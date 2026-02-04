---
layout: post
title: FeatherQuad
description: This project focuses on designing and virtually testing a custom quadcopter from scratch. The drone’s components, mass, and geometry are defined, then its flight behavior is modeled and tested in MATLAB to verify stable hover and control. A custom 3D-printed frame is designed in SolidWorks and analyzed to ensure it is strong and stiff enough for flight. The goal is to validate the drone’s design through simulation and analysis before building it physically.
skills:
- CAD Design
- 3D Printing
- Electronics Integration
- Soldering
- Flight Tuning
main-image: /drone_pic1.png
published: true
---

## COTS Parts List

| Item | Qty | Unit Price (USD) | Total Price (USD) | Notes |
|------|-----|------------------|-------------------|-------|
| Transmitter + Receiver (Radiolink T8FB + R8EF) | 1 | 49.99 | 49.99 | 8-channel 2.4 GHz RC system |
| Battery | 1 | 11.72 | 11.72 | 4S 1500 mAh 80C LiPo (XT60) |
| Flight Controller | 1 | 33.99 | 33.99 | HGLRC F405 8S V1, ICM42688P |
| ESC | 1 | 39.99 | 39.99 | SEQURE 65A 4-in-1, 2–6S, AM32 |
| Propellers | 1 | 9.99 | 9.99 | HQProp 5×4.3×3 (8 pcs, CW/CCW) |
| Motor | 4 | 15.75 | 62.99 | Axisflying AE2207 V2 1960KV (set of 4) |
| **Subtotal** | **6 items** | — | **208.67** | Amazon cart total |

## SolidWorks Screenshot
<img src="/_projects/FeatherQuad/Screenshot%202026-02-03%20182645.png" alt="SolidWorks Screenshot" style="max-width:100%; height:auto;">
## MATLAB Validation (Code + Image Placeholders)

This section documents the MATLAB-based virtual validation performed before physical assembly. It includes (1) open-loop attitude dynamics, (2) closed-loop attitude stabilization using PD control, and (3) a full 6-DOF rigid-body simulation with altitude + attitude control.

---

# 1) Open-Loop Attitude Dynamics (No Control)

## `attitude_sim.m`
```matlab
%% attitude_sim.m
clear; clc; close all;

run dronebasic.m

% State: [phi; theta; psi; p; q; r]
x = zeros(6,1);

% Constant torque step (open-loop)
tau = [0.02; 0; 0];   % [N*m] roll torque only

dt = 0.001;
t_end = 2;
N = round(t_end/dt);

X = zeros(6,N);

for k = 1:N
    phi = x(1); theta = x(2); psi = x(3);
    p   = x(4); q     = x(5); r   = x(6);

    % Rotational dynamics (decoupled first-pass)
    p_dot = tau(1)/Ixx;
    q_dot = tau(2)/Iyy;
    r_dot = tau(3)/Izz;

    % Kinematics (small-angle approximation)
    phi_dot   = p;
    theta_dot = q;
    psi_dot   = r;

    % Integrate (Euler)
    x = x + dt*[phi_dot; theta_dot; psi_dot; p_dot; q_dot; r_dot];
    X(:,k) = x;
end

t = (0:N-1)*dt;

figure; plot(t, X(1,:)); grid on;
xlabel('Time (s)'); ylabel('Roll angle \phi (rad)');
title('Open-loop roll response to constant torque');

%% attitude_pd.m
clear; clc; close all;

run dronebasic.m

% State: [phi; p]
x = [0; 0];

phi_ref = 0.2;   % rad target

% PD gains
Kp = 0.015;      % N*m/rad
Kd = 0.0030;     % N*m/(rad/s)

dt = 0.001;
t_end = 2;
N = round(t_end/dt);

X = zeros(2,N);

for k = 1:N
    phi = x(1);
    p   = x(2);

    % PD control torque
    tau = Kp*(phi_ref - phi) - Kd*p;

    % Dynamics: Ixx*p_dot = tau
    p_dot   = tau / Ixx;
    phi_dot = p;

    % Integrate (Euler)
    x = x + dt*[phi_dot; p_dot];
    X(:,k) = x;
end

t = (0:N-1)*dt;

figure; plot(t, X(1,:)); grid on;
xlabel('Time (s)'); ylabel('Roll angle \phi (rad)');
title('Roll angle under PD control');

figure; plot(t, X(2,:)); grid on;
xlabel('Time (s)'); ylabel('Roll rate p (rad/s)');
title('Roll rate under PD control');

%% quad_6dof.m
clear; clc; close all;

run dronebasic.m
I    = diag([Ixx Iyy Izz]);
invI = diag([1/Ixx 1/Iyy 1/Izz]);

% Simulation settings
dt    = 0.001;
t_end = 8;
N     = round(t_end/dt);
t     = (0:N-1)*dt;

% State: [x y z vx vy vz phi theta psi p q r]'
x = zeros(12,1);

% References
z_ref     = 1.0;
phi_ref   = 0.0;
theta_ref = 0.0;
psi_ref   = 0.0;

% Altitude PD (with gravity compensation)
Kpz = 12;     % N/m (effective)
Kdz = 8;      % N/(m/s)

% Attitude PD (torques)
Kp_phi   = 0.03;  Kd_p = 0.006;
Kp_theta = 0.03;  Kd_q = 0.006;
Kp_psi   = 0.02;  Kd_r = 0.004;

% Logging
X = zeros(12,N);
U = zeros(4,N); % [T tau_x tau_y tau_z]

% Rotation helpers (ZYX)
rotz = @(a)[cos(a) -sin(a) 0; sin(a) cos(a) 0; 0 0 1];
roty = @(a)[cos(a) 0 sin(a); 0 1 0; -sin(a) 0 cos(a)];
rotx = @(a)[1 0 0; 0 cos(a) -sin(a); 0 sin(a) cos(a)];

for k = 1:N
    % Unpack state
    pos   = x(1:3);
    vel   = x(4:6);
    phi   = x(7);  theta = x(8);  psi = x(9);
    p     = x(10); q     = x(11); r   = x(12);

    % Rotation matrix body->inertial
    R = rotz(psi)*roty(theta)*rotx(phi);

    % --- CONTROL ---
    z    = pos(3);
    zdot = vel(3);

    % Total thrust command (N)
    Tcmd = m*( g + Kpz*(z_ref - z) + Kdz*(0 - zdot) );
    if Tcmd < 0, Tcmd = 0; end

    % Torque commands (N*m)
    tau_x = Kp_phi  *(phi_ref   - phi)   - Kd_p*p;
    tau_y = Kp_theta*(theta_ref - theta) - Kd_q*q;
    tau_z = Kp_psi  *(psi_ref   - psi)   - Kd_r*r;

    U(:,k) = [Tcmd; tau_x; tau_y; tau_z];

    % --- DYNAMICS ---
    thrust_inertial = R * [0;0;Tcmd];
    acc = (1/m)*thrust_inertial + [0;0;-g];

    omega = [p;q;r];
    tau   = [tau_x; tau_y; tau_z];

    omega_dot = invI * ( tau - cross(omega, I*omega) );

    % Euler angle rates (ZYX)
    E = [1 sin(phi)*tan(theta)  cos(phi)*tan(theta);
         0 cos(phi)            -sin(phi);
         0 sin(phi)/cos(theta)  cos(phi)/cos(theta)];
    angles_dot = E*omega;

    % --- INTEGRATE ---
    xdot = zeros(12,1);
    xdot(1:3)   = vel;
    xdot(4:6)   = acc;
    xdot(7:9)   = angles_dot;
    xdot(10:12) = omega_dot;

    x = x + dt*xdot;
    X(:,k) = x;
end

% Plots
figure; plot(t, X(3,:)); grid on;
xlabel('Time (s)'); ylabel('z (m)'); title('Altitude z(t)');

figure; plot(t, X(7,:)); grid on;
xlabel('Time (s)'); ylabel('\phi (rad)'); title('Roll \phi(t)');

figure; plot(t, X(8,:)); grid on;
xlabel('Time (s)'); ylabel('\theta (rad)'); title('Pitch \theta(t)');

figure; plot(t, X(9,:)); grid on;
xlabel('Time (s)'); ylabel('\psi (rad)'); title('Yaw \psi(t)');

figure; plot(t, U(1,:)); grid on;
xlabel('Time (s)'); ylabel('T (N)'); title('Total Thrust Command T(t)');

