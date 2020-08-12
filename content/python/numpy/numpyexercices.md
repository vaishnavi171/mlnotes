---
title: "Numpy Exercises"
author: "Vaishnavi"
date: 2020-08-10
description: "-"
type: technical_note
draft: false


---


```python
import numpy as np 
```


```python
# 1. Creating array object 

arr = np.array( [[ 1, 2, 3], 
                 [ 4, 2, 5]] ) 
  
# Printing type of arr object 

print("Array is of type: ", type(arr)) 
  
# Printing array dimensions (axes)

print("No. of dimensions: ", arr.ndim) 
  
# Printing shape of array 

print("Shape of array: ", arr.shape) 
  
# Printing size (total number of elements) of array 

print("Size of array: ", arr.size) 
  
# Printing type of elements in array 

print("Array stores elements of type: ", arr.dtype)
```

    Array is of type:  <class 'numpy.ndarray'>
    No. of dimensions:  2
    Shape of array:  (2, 3)
    Size of array:  6
    Array stores elements of type:  int64



```python
# 2. Replace items that satisfy a condition with another value in numpy array 

out = np.where(arr%2==0,-1,arr)
print("Original Array\n",arr)
print("Array Modified\n",out)
```

    Original Array
     [[1 2 3]
     [4 2 5]]
    Array Modified
     [[ 1 -1  3]
     [-1 -1  5]]



```python
# 3. Reshape array

newarr = arr.reshape(-1)
print("Reshaping Array\n",newarr)
```

    Reshaping Array
     [1 2 3 4 2 5]



```python
# 4. Slicing 2D Array

print("Slicing Array",arr[1, 1:4])
```

    Slicing Array [2 5]



```python
# 5. Flipping the Array

array = np.arange(8).reshape((2,2,2)) 
print("Original array : \n", array) 

print("Flipped array : \n", np.flip(array, 0)) 
```

    Original array : 
     [[[0 1]
      [2 3]]
    
     [[4 5]
      [6 7]]]
    Flipped array : 
     [[[4 5]
      [6 7]]
    
     [[0 1]
      [2 3]]]



```python
# 6. Searching

x = np.where(out == 3)
print(x)
```

    (array([0]), array([2]))



```python
# 7.Make a python function that handles scalars to work on numpy arrays 

def maxx(x, y):
    """Get the maximum of two items"""
    if x >= y:
        return x
    else:
        return y

pair_max = np.vectorize(maxx, otypes=[float])

a = np.array([5, 7, 9, 8, 6, 4, 5])
b = np.array([6, 3, 4, 8, 9, 7, 1])

pair_max(a, b)


```




    array([6., 7., 9., 8., 9., 7., 5.])




```python
# 8. Numpy Take method

print("Taking Indices\n", np.take(arr,[[0, 1], [2, 3]])) 
```

    Taking Indices
     [[1 2]
     [3 4]]



```python
# 9. To create identical matrix

idn = np.eye(4)
print("Create Identical Matrix\n",idn)
```

    Create Identical Matrix
     [[1. 0. 0. 0.]
     [0. 1. 0. 0.]
     [0. 0. 1. 0.]
     [0. 0. 0. 1.]]



```python
# 10. Numpy Hypot function

arr1 = [12, 3, 4, 6] 
print ("arr1 array : ", arr1) 


arr2 = [5, 4, 3, 8] 
print ("arr2 array : ", arr2) 

result = np.hypot(arr1, arr2) 
print("\nHypotenuse is as follows :",result) 
```

    arr1 array :  [12, 3, 4, 6]
    arr2 array :  [5, 4, 3, 8]
    
    Hypotenuse is as follows : [13.  5.  5. 10.]



```python
# 11. Slicing

sliced_arr = idn[:2, ::2]
print ("Array with first 2 rows and"
    " alternate columns(0 and 2):\n", sliced_arr)
```

    Array with first 2 rows and alternate columns(0 and 2):
     [[1. 0.]
     [0. 0.]]



```python
# 12. Inverse of a matrix

mat = np.array([
[1, 2],
[3, 4]
])
inverse_mat = np.linalg.inv(mat)
print(inverse_mat) 
```

    [[-2.   1. ]
     [ 1.5 -0.5]]



```python
# 13. Squareroot of array elements

Sqrt = np.sqrt(mat)
print("\nSquare root of Array1 elements: ")
print(Sqrt)
```

    
    Square root of Array1 elements: 
    [[1.         1.41421356]
     [1.73205081 2.        ]]



```python
# 14. Transpose of Array

Trans_mat = mat.T
print("\nTranspose of Array: ")
print(Trans_mat)
```

    
    Transpose of Array: 
    [[1 3]
     [2 4]]



```python
# 15. To find real number or not

in_array = [1, 3, 5, 4] 
print ("Input array : \n", in_array) 

output_value = np.isrealobj(in_array) 
print ("\nIs real : \n", output_value) 
```

    Input array : 
     [1, 3, 5, 4]
    
    Is real : 
     True



```python
# 16. Flip left to right

print("\nFlipped array left-right : \n", np.fliplr(mat)) 

```

    
    Flipped array left-right : 
     [[2 1]
     [4 3]]



```python
# 17. Roundoff using function

  
in_array = [.5, 1.5, 2.5, 3.5, 4.5, 10.1] 
print ("Input array : \n", in_array) 
  
rintoff_values = np.rint(in_array) 
print ("\nRounded values : \n", rintoff_values) 
```

    Input array : 
     [0.5, 1.5, 2.5, 3.5, 4.5, 10.1]
    
    Rounded values : 
     [ 0.  2.  2.  4.  4. 10.]



```python
# 18. bmat() function


A = np.mat('4 1; 22 1') 
B = np.mat('5 2; 5 2') 
C = np.mat('8 4; 6 6') 
  
# array like igeekut 
a = np.bmat([[A, B], [C, A]]) 
print("Via bmat array like input : \n", a, "\n\n") 
  
# string like igeekut 
s = np.bmat('A, B; A, A') 
print("Via bmat string like input : \n", s) 
```

    Via bmat array like input : 
     [[ 4  1  5  2]
     [22  1  5  2]
     [ 8  4  4  1]
     [ 6  6 22  1]] 
    
    
    Via bmat string like input : 
     [[ 4  1  5  2]
     [22  1  5  2]
     [ 4  1  4  1]
     [22  1 22  1]]



```python
# 19. roll()

array = np.arange(12).reshape(3, 4) 
print("Original array : \n", array) 
   
# Rolling array; Shifting one place 
print("\nRolling with 1 shift : \n", np.roll(array, 1)) 
```

    Original array : 
     [[ 0  1  2  3]
     [ 4  5  6  7]
     [ 8  9 10 11]]
    
    Rolling with 1 shift : 
     [[11  0  1  2]
     [ 3  4  5  6]
     [ 7  8  9 10]]



```python
# 20. 2x2 matrix with 1's on main diagnol 

b = np.identity(2, dtype = float) 
print("Matrix b : \n", b) 
```

    Matrix b : 
     [[1. 0.]
     [0. 1.]]



```python
# 21. numpy.full_like method 

x = np.arange(10, dtype = int).reshape(2, 5) 
print("x before full_like : \n", x) 
  
# using full_like 
print("\nx after full_like : \n", np.full_like(x, 10.0)) 
```

    x before full_like : 
     [[0 1 2 3 4]
     [5 6 7 8 9]]
    
    x after full_like : 
     [[10 10 10 10 10]
     [10 10 10 10 10]]



```python
# 22. Diagonal  Elements

a = np.matrix([[1, 21, 30],  
                 [63 ,434, 3],  
                 [54, 54, 56]]) 
  
print("Main Diagnal elements : \n", np.diag(a), "\n") 
```

    Main Diagnal elements : 
     [  1 434  56] 
    



```python
# 23. Numpy.diagflat method 

print("diagflat use on main diagonal : \n", np.diagflat([1, 7]), "\n") 
```

    diagflat use on main diagonal : 
     [[1 0]
     [0 7]] 
    



```python
# 24. Creates a 5 X 5 array and returns indices of main diagonal elements 

d = np.diag_indices(5) 
print("Indices of diagnol elements as tuple : ") 
print(d, "\n") 
```

    Indices of diagnol elements as tuple : 
    (array([0, 1, 2, 3, 4]), array([0, 1, 2, 3, 4])) 
    



```python
# 25. To predict financial future values

Solution = np.fv(0.05/12, 10*12, -100, -100) 
  
print("Solution : ", Solution)
```

    Solution :  15692.928894335748


    <ipython-input-34-fcf883c3b6a2>:3: DeprecationWarning: numpy.fv is deprecated and will be removed from NumPy 1.20. Use numpy_financial.fv instead (https://pypi.org/project/numpy-financial/).
      Solution = np.fv(0.05/12, 10*12, -100, -100)



```python

```
