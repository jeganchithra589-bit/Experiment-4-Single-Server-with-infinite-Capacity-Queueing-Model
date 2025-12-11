# Experiment-4-Single-Server-with-infinite-Capacity-Queueing-Model
# Aim
To find

(a)	Average number of materials in the system 

(b)	Average number of materials in the conveyor

(c)	Waiting time of each material in the system

(d)	Waiting time of each material in the conveyor



If the arrival of materials follow poisson process with mean interval time 12 seconds, service time of lathe machine follows exponential distribution with mean service time 1 second and average service time of robot is 7 seconds.
# Software Required:  Visual Components and Python
# Theory:
1.	The model has one server and unlimited queue space, so any number of customers can wait without blocking new arrivals.
2.	Arrivals usually follow a Poisson process, and service times come from a chosen probability distribution, often exponential in the classic M/M/1 case.
3.	 The system reaches a stable steady state only when the service rate exceeds the arrival rate; otherwise, the queue grows without bound.
4.	 Key performance measures—like average waiting time, average queue length, and server utilization—emerge from the balance between these two rates.
5.	 Despite its simplicity, the model serves as a foundational benchmark for analysing more intricate queueing systems and real-world service operations.
# Procedure: 
<img width="847" height="255" alt="image" src="https://github.com/user-attachments/assets/f5b78f76-ddef-4bcd-afee-044fb0babdc8" />

# Program
```import math 
 
arr_time_input = '' 
while not arr_time_input.strip(): # Loop until a non-empty input is received 
    arr_time_input = input("Enter the mean inter arrival time of objects from feeder (in secs):") 
    if not arr_time_input.strip(): 
        print("Input cannot be empty. Please enter a value.") 
 
arr_time = float(arr_time_input) 
 
ser_time=float(input("Enter the mean inter service time of lathe machine (in secs):")) 
Robot_time=float(input("Enter the Additional time taken for the robot (in secs):")) 
c=int(input("Number of service centres:")) 
lam=1/arr_time 
mu=1/(ser_time+Robot_time) 
print("------------------------------------------------") 
print("Multiple Server with infinite capacity- (M/M/c):(00/FIFO)") 
print("----------------------------------------------------") 
print("The mean arrival rate per second: %0.2f" %lam) 
print("The mean service rate per second: %0.2f"%mu) 
rho=lam/(c*mu) 
sum=(lam/mu)**c*(1/(1-rho))/math.factorial(c) 
for i in range(0,c): 
    sum=sum+(lam/mu)**i/math.factorial(i) 
P0=1/sum 
if(c<5): 
    Lq=(P0/math.factorial(c))*(1/c)*(lam/mu)**(c+1)/(1-rho)**2 
    Ls=Lq+lam/mu 
    Ws=Ls/lam 
    Wq=Lq/lam 
    print("Average number of objects in the system: %0.2f"%Ls) 
    print("Average numner of objects in the conveyor: %0.2f"%Lq) 
    print("Average waiting time of an object in the system: %0.2f secs"%Ws) 
    print("Average waiting time of an object in the conveyor: %0.2f secs"%Ws) 
    print("Probability that the system is busy: %0.2f" %(rho)) 
    print("Probability that the system is empty:%0.2f "%(1-rho)) 
else: 
    print("Warning! Objects overflow will happen in the conveyor") 
print("-----------------------------------------------------") 
```
# Output
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/47c9ac7f-15cc-4023-a358-a45babca3504" />

# Result
       The average number of material in the system and in the conveyor and waiting time are successfully found.
