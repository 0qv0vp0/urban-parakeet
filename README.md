from pylab import *
from math import *
time=eval(input('time=?'))
dt=0.01
n=int(round(time/dt))
t=[0]*n
E=[0]*n
w=[0]*n
theta=[0]*n
x=[0]*n
T=[0]*n
V=[0]*n
P=[0]*n
Ah=[0]*n
Al=[0]*n
p=1.2
Vc=40*10e-6
cV=717.0
Th=600.0
Tl=300.0
u=100000.0
A0=40*10e-4
Ap=1.9*10e-4
A1_max=4.9*10e-2
R=1.25*10e-2
I=4*10e-4
b=0.7*10e-3
P0=10**5
m=p*(Vc+Ap*R)
P[0]=P0
E[0]=cV*m*300
w[0]=0.0
theta[0]=0.0
t[0]=0.0
x[0]=R
V[0]=Vc+Ap*x[0]
T[0]=560
for i in range(n-1):
    x[i]=R*(1+sin(theta[i]))
    E[i+1]=E[i]+( A0*( 1+cos( theta[i] ) )/2*u*(Th-T[i])-( A0*( 1-cos(theta[i] ) )/2+A1_max*x[i])*u*(T[i]-Tl)-(P[i]-P0)*Ap*R*w[i]*cos(theta[i]))*dt
    w[i+1]=w[i]+((P[i]-P0)*Ap*R*cos(theta[i])-b*w[i])/I*dt
    theta[i+1]=theta[i]+w[i]*dt
    x[i+1]=R*(1+sin(theta[i+1]))
    T[i+1]=E[i+1]/(cV*m)
    V[i+1]=Vc+Ap*x[i+1]
    P[i+1]=2/5*E[i+1]/V[i+1]
    t[i+1]=t[i]+dt
plt.plot(t,x)
plt.xlabel('t')
plt.ylabel('x')
plt.show()
    
Traceback (most recent call last):
  File "C:\Users\Administrator\Desktop\Project  striling engine.py", line 43, in <module>
    x[i+1]=R*(1+sin(theta[i+1]))
ValueError: math domain error
    

