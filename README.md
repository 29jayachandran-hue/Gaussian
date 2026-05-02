# Gaussian Elimination

## AIM:
To write a program to find the solution of a matrix using Gaussian Elimination.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
1. Read the number of unknowns n and the augmented matrix entries from user input.
2. Reshape the input into an n\times (n+1) augmented matrix A.
3. For each pivot row i, eliminate entries below the pivot by subtracting a factor times the pivot row.
4. Initialize solution vector x with zeros.
5. Perform back substitution: compute each variable from the last row upwards using the formula in the code.
6. Print the solution values of all variables in formatted output. 

## Program:
```
/*
Program to find the solution of a matrix using Gaussian Elimination.
Developed by: A.Jayachandran
RegisterNumber: 25015034
*/
import os 
os.environ["OPENBLAS_NUM_THREADS"]="1"
import numpy as np
def solve_gaussian(data):
    n=int(data[0])
    A=np.array(data[1:],dtype=float).reshape(n,n+1)
    for i in range(n):
        for j in range(i+1,n):
            factor=A[j,i]/A[i,i]
            A[j]-=factor*A[i]
    x=np.zeros(n)
    for i in range(n-1,-1,-1):
        x[i]=(A[i,-1]-np.dot(A[i,i+1:n],x[i+1:n]))/A[i,i]
    return x
data=[]
for i in range(13):
    data.append(input())
result=solve_gaussian(data)
print("".join([f"X{i} = {val:.2f} " for i,val in enumerate(result)]))

```

## Output:
<img width="716" height="825" alt="image" src="https://github.com/user-attachments/assets/24542b1a-cefc-4dd4-81b0-0a9dd907643c" />


## Result:
Thus the program to find the solution of a matrix using Gaussian Elimination is written and verified using python programming.

