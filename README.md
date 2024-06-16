# block-product
Modify this program
clc;
clear all;
close all;
%A = blkdiag(a, a, a);6
I = eye(3)
K = rand(3)
x = [1;-2;3]
b = K*x
mu = .2;
alpha = .5;
beta = .4;
A = [I,K;-K',mu*I]
y0 = [1;-4;0];
x0 = [5;2;-3];
z0 = [y0;x0];
r0 = [b;zeros(3,1)]- A* z0;
r = [r0];
y=[y0]
x=[x0]
z0=[y0;x0]
z2 = K' * r(1:3,1)+ r(4:6,1).\ (beta + mu)
z1 = r(1:3,1) - [(1.\alpha)* K *z2]
Z=[y + z1;x+z2]
palpha = [I (1.\alpha)*K ;-K' beta*I+mu*I-(1.\alpha)* K'*K]
palphainv = inv(palpha)

for k = 1:10
    zk = z0 + palphainv*r0
    
    z(k+1) = z(k) + palphainv*r(k)
  %   y=y + z1;
  %x= x+z2;
   %z=[z Z]
  %w=A * z
  % R = [b;zeros(3,1)]- w(k+1)
  %R=[r R] 
