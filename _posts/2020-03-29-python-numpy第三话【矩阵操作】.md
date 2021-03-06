---
title: python-numpy第三话
layout: post
tags: python-numpy
categories: ''
---
#### 1. numpy 生成特殊矩阵操作
    >>>
    import numpy as np
    a = np.arange(15).reshape(3, 5)
    a
    >>>
    array([[ 0,  1,  2,  3,  4],
           [ 5,  6,  7,  8,  9],
           [10, 11, 12, 13, 14]])
           
    >>> np.zeros ((3,4))  
    >>>
     array([[0., 0., 0., 0.],
           [0., 0., 0., 0.],
           [0., 0., 0., 0.]])
           
    >>> np.ones( (2,3,4), dtype=np.int32 )
        array([[[1, 1, 1, 1],
                [1, 1, 1, 1],
                [1, 1, 1, 1]],
    
               [[1, 1, 1, 1],
                [1, 1, 1, 1],
                [1, 1, 1, 1]]])
                
#### 2. numpy 生成矩阵 （arrange，random，linspace）
    >>> 等间隔生成(间隔为5)      
    #To create sequences of numbers, the last is step
    np.arange( 10, 30, 5 )  
    >>> array([10, 15, 20, 25])
    
    >>> 按个数生成(5个）
    from numpy import pi
    >>> np.linspace( 0, 2*pi, 5 )
    >>>
    array([0.        , 1.57079633, 3.14159265, 4.71238898, 6.28318531])
    
#### 3.numpy 矩阵运算（加法，点乘）
    >>> 加法运算
    #the product operator * operates elementwise in NumPy arrays
    a = np.array( [20,30,40,50] )
    b = np.arange( 4 )
    print (a) 
    print (a<35)
    print (b)
    c = a-b
    print (c)
    >>>
    [20 30 40 50]
    [ True  True False False]
    [0 1 2 3]
    [20 29 38 47]
    ----------------------------------------------------------------
    #The matrix product can be performed using the dot function or method
    >>> 矩阵点乘(两种形式皆可)
    A = np.array( [[1,1],
                   [0,1]] )
    B = np.array( [[2,0],
                   [3,4]] )
    print( A)
    print( B)
    #print A*B
    print (A.dot(B))
    print (np.dot(A, B)) 
    >>>
    [[1 1]
     [0 1]]
     
    [[2 0]
     [3 4]]
     
    [[5 4]
     [3 4]]
     
    [[5 4]
     [3 4]]
     
#### 4.numpy 拉平数组(ravel,reshape)

    >>>
    #Return the floor of the input
    a = np.floor(10*np.random.random((3,4)))
    print (a)
    
    # flatten the array
    print (a.ravel())
    
    #If a dimension is given as -1 in a reshaping operation, 
    the other dimensions are automatically calculated:
    a.reshape(4,-1)
    print(a)
    >>>
    [[4. 3. 3. 9.]
     [1. 8. 5. 1.]
     [3. 6. 4. 5.]]
     
    [4. 3. 3. 9. 1. 8. 5. 1. 3. 6. 4. 5.]
    
    [[4. 3. 3. 9.]
     [1. 8. 5. 1.]
     [3. 6. 4. 5.]]
     
#### 5.numpy 水平拼接(hstack) 垂直拼接（vstack）
    
    >>>
    a = np.floor(10*np.random.random((2,2)))
    b = np.floor(10*np.random.random((2,2)))
    print (a)
    print ('---')
    print (b)
    print ('---')
    print (np.hstack((a,b))) 
    
   >>> 
    [[9. 2.]
     [6. 8.]]
    ---
    [[7. 8.]
     [7. 6.]]
    ---
    [[9. 2. 7. 8.]
     [6. 8. 7. 6.]]
     
#### 6.numpy 水平分割(hsplit) 垂直分割（vsplit）
    >>>
    a = np.floor(10*np.random.random((2,12)))
    print (a)
    print (np.hsplit(a,3))
    # Split a after the third and the fourth column（在第四列分割，然后形成三个段，1-3,4,5-12）
    # print np.hsplit(a,(3,4))  
    a = np.floor(10*np.random.random((12,2)))
    print (a)
    np.vsplit(a,3)
    
    >>>
    [[5. 4. 6. 7. 5. 7. 7. 3. 0. 8. 5. 8.]
     [5. 5. 2. 0. 9. 3. 3. 3. 0. 1. 1. 7.]]
    [array([[5., 4., 6., 7.],
           [5., 5., 2., 0.]]), array([[5., 7., 7., 3.],
           [9., 3., 3., 3.]]), array([[0., 8., 5., 8.],
           [0., 1., 1., 7.]])]
    [[7. 7.]
     [8. 1.]
     [5. 1.]
     [1. 8.]
     [2. 3.]
     [0. 2.]
     [8. 4.]
     [7. 4.]
     [2. 2.]
     [1. 7.]
     [0. 3.]
     [8. 6.]]
    [array([[7., 7.],
            [8., 1.],
            [5., 1.],
            [1., 8.]]), array([[2., 3.],
            [0., 2.],
            [8., 4.],
            [7., 4.]]), array([[2., 2.],
            [1., 7.],
            [0., 3.],
            [8., 6.]])]
            
#### 7.numpy 赋值的联动性[1.等号赋值]
    >>> 如果单纯使用 = 赋值，地址相同，一个改变，另一个也改变 
    #Simple assignments make no copy of array objects or of their data.
    a = np.arange(12)
    b = a
    # a and b are two names for the same ndarray object
    print(b is a)
    b.shape = 3,4
    print (a.shape)
    print (id(a))
    print (id(b))
    print(a)
    >>>
    True
    (3, 4)
    3110677184064
    3110677184064
    [[ 0  1  2  3]
     [ 4  5  6  7]
     [ 8  9 10 11]]
     
#### 8.numpy 赋值的联动性[2.view()赋值]   
    >>> 
    #The view method creates a new array object that looks at the same data.
    # 此时改动C，也是改动a，地址不同，但是联动
    c = a.view()
    print(c is a)
    c.shape = 2,6
    #print a.shape
    c[0,4] = 1234
    print(a)
    print (id(a))
    print (id(c))
    >>>
    False
    [[   0    1    2    3]
     [1234    5    6    7]
     [   8    9   10   11]]
    1585806290736
    1585791641040

#### 9.numpy 赋值的联动性[3.copy()赋值] 
    >>>
    #The copy method makes a complete copy of the array and its data.
    # 此时为独立的两个值，改动d无关a，地址不同，也不联动
    d = a.copy() 
    print(d is a)
    d[0,0] = 9999
    print (d )
    print (a)
    print (id(a))
    print (id(c))
    >>>
    False
    [[9999    1    2    3]
     [1234    5    6    7]
     [   8    9   10   11]]
    [[   0    1    2    3]
     [1234    5    6    7]
     [   8    9   10   11]]
    1585806290736
    1585791641040
    
#### 10.numpy 阵列

    >>>
    a = np.arange(0, 40, 10)
    print(a)
    b = np.tile(a, (3,5)) 
    print (b)
    >>>
    [ 0 10 20 30]
    [[ 0 10 20 30  0 10 20 30  0 10 20 30  0 10 20 30  0 10 20 30]
     [ 0 10 20 30  0 10 20 30  0 10 20 30  0 10 20 30  0 10 20 30]
     [ 0 10 20 30  0 10 20 30  0 10 20 30  0 10 20 30  0 10 20 30]]