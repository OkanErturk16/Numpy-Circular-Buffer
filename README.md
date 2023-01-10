# Numpy-Circular-Buffer
Circular buffer implementation for Python, Numpy.

Numpy has very useful methods, yet, no buffer implementation is included.
Especially for real-time processing applications, buffer-aided designs are of significant importance.
Therefore, I share my circular buffer implementation written in Python, Numpy.
The implementation is very simple and can be traced only by reading the code.

The script numpyCircularBuffer.py includes the implementation of circular buffer class based on Numpy.
An example usage of circular buffer class is given in mainExp.py 


```python
import numpyCircularBuffer as ncb
import numpy as np


myBuffer = ncb.circBuffer(len_max = 20)

#show where my write and read pointers are:
print('WRT and RD ptr positions:', myBuffer.WRT_ptr, ' and ', myBuffer.RD_ptr, '.')


#generate data "x" to push into the buffer
x = np.arange(10)

#check if the buffer is okay then write.
if myBuffer.is_WRT_available(x):
    myBuffer.WRT(x)

#show where my write and read pointers are:
print('WRT and RD ptr positions:', myBuffer.WRT_ptr, ' and ', myBuffer.RD_ptr, '.')

#generate new data
y = np.arange(12)

#show that the buffer has no space for writing "y"
if not myBuffer.is_WRT_available(y):
    print('Buffer has no space!')

#Read from buffer
n_read = 4
if myBuffer.is_RD_available(n_read):
    z = myBuffer.RD(n_read)
    print('Data read from the buffer:', z)

#Show the last state of the buffer
print('WRT and RD ptr positions:', myBuffer.WRT_ptr, ' and ', myBuffer.RD_ptr, '.')
print('Buffer now has ', myBuffer.elements_in_buffer, 'elements in it.')
```

