# EECS504 W20 Assignments
This is a list of references which I looked up while doing assignments, and some points that I can easily commit a mistake on.

## Assignment 1
## Assignment 2
## Assignment 3-1 Motion Magnifying
### Square
** (double asterisk). Applies to scalar and `np.ndarray` (element-wise).
### Element-wise Multiplication
`np.multiply` (array or mat, array or mat).
### Meshgrid
- Source: [Scipy](https://docs.scipy.org/doc/numpy/reference/generated/numpy.meshgrid.html)
- Creates a weird matrix, but sometimes useful.
### Gaussian Kernel
- `cv2.getGaussianKernel`: No use. Formula was more implementable.
- Direct implementation
```python
X, Y = np.meshgrid(np.arange(im_size), np.arange(im_size))
for y in range(0, im_size, 2*sigma):
  for x in range(0, im_size, 2*sigma):
    gaussian_mask = (1 / (2 * np.pi * sigma**2)) * np.exp(-((X - x)**2 + (Y - y)**2) / (2 * sigma**2))
```
### TypeError: return arrays must be of ArrayType - Stack Overflow
Occurred because I put some parentheses wrongly.
### Line Continuation
Use \ (backslash). If there is a single-line comment on the same line, the order should be code, comment, backslash, (next line) continued code. For example,
```python
a = myfuncion(argument1, # Argument 1 \ 
              argument2, # Argument 2 \
              argument3) # Last argument
```
### Forming a complex number with magnitude and phase
- Don’t forget abs, exp, and 1j.
```python
magnified_dft = abs(im1_dft) * exp((angle(im1_dft) + magnification_factor * phase_shift) * 1j)
```
### About (d)
아주 껑충껑충 뛴다. 현실에서는 그보다는 촘촘하게 뛸지도 모른다.
## Assignment 3-2 Texture Synthesis
### Sum all elements in a matrix(ndarray)
`sum(sum(ndarray))`
### Normalize a kernel, matrix, etc. (Make the sum of the elements equal to 1)
`kernel = kernel / sum(sum(kernel))`
### Return indices of nonzero elements
- `np.asarray(np.nonzero(array))`
- If 2D, then [[x1, …, xn], [y1, …, yn]].
- Transposing the output is also a good choice
- Ref: [Scipy](https://docs.scipy.org/doc/numpy/reference/generated/numpy.nonzero.html)
### Make a Boolean array from a numeric array
- `boolarr = numarr != 0`
Ex.
```python
numarr = np.array([[1, -1], [0, 0.3]])
boolarr = numarr != 0
```
```
boolarr == [[True, True], [False, True]]
```
### `numpy.expand _dims`
https://docs.scipy.org/doc/numpy/reference/generated/numpy.expand_dims.html
### `numpy.broadcast_to`
https://docs.scipy.org/doc/numpy/reference/generated/numpy.broadcast_to.html
### `numpy.pad`
https://docs.scipy.org/doc/numpy/reference/generated/numpy.pad.html
### `numpy.amin`
https://docs.scipy.org/doc/numpy/reference/generated/numpy.amin.html
### `scipy.ndimage.binary_dialation`
http://lagrange.univ-lyon1.fr/docs/scipy/0.17.1/generated/scipy.ndimage.binary_dilation.html
### `numpy.asarray`
https://docs.scipy.org/doc/numpy/reference/generated/numpy.asarray.html
### `numpy.any`
https://docs.scipy.org/doc/numpy/reference/generated/numpy.any.html
### `cv2_imshow(im)`
The ‘im’ should range from 0 to 255, so multiply 255 if the previous result ranges from 0 to 1.
## Assignment 4-1 Multi-layer Perceptron
### numpy.ndarray.shape
### Reshape
- Source: [Scipy](https://docs.scipy.org/doc/numpy/reference/generated/numpy.reshape.html)
- `myarray.reshape((row, col))` or `reshape(myarray, (row, col))`
- One shape dimension can be -1; this value will be inferred from the length and the other determined dimensions.
### `np.ones_like(x)`
### ReLU
`ReLU = x * (x > 0)`
### Fully-Connected Layer (FC Layer)
https://leonardoaraujosantos.gitbooks.io/artificial-inteligence/content/fc_layer.html
### Shape
`x.shape`
### Row-wise maximum
`np.amax(array, axis=1)`
### Matrix multiplication
- Source: [Scipy](https://docs.scipy.org/doc/numpy/reference/generated/numpy.matmul.html)
- `np.matmul(mat, mat)`
### Broadcast row vs column
```python
x = np.array([[1, 2, 3], [4, 5, 6]])
y = np.array([.1, .2]).reshape(2, -1) # Reshape into (2, 1) necessary
print('x.shape: ', x.shape, '\ny.shape: ', y.shape)
print(x + y)
z = np.array([.1, .2, .3])  # No reshape required! (3,) is okay
print('x.shape: ', x.shape, '\nz.shape: ', z.shape)
print(x + z)
```
### Softmax, Cross-entropy
https://deepnotes.io/softmax-crossentropy
### Plot
https://matplotlib.org/gallery/text_labels_and_annotations/legend.html#legend-using-pre-defined-labels
## Assignment 5-1 Scene Recognition
### Data Load
Source: https://www.programcreek.com/python/example/104834/torchvision.transforms.Resize
### ImageFolder
Source: https://pytorch.org/docs/stable/torchvision/datasets.html#imagefolder
### DataLoader
Ref: https://pytorch.org/docs/stable/data.html#torch.utils.data.DataLoader
### Model
Source: https://github.com/pytorch/vision/blob/master/torchvision/models/vgg.py
### `nn.Sequential`
Ref: https://pytorch.org/docs/stable/nn.html
### Optimizer
Ref: https://pytorch.org/docs/stable/optim.html
### Cross Entropy Loss
- Ref: https://pytorch.org/docs/stable/nn.html
- Source: https://discuss.pytorch.org/t/interpreting-loss-value/17665/2
### Train model
- Ref: https://discuss.pytorch.org/t/newbie-multi-target-runtime-error-when-classifying-dataset-with-multi-class-target/37678
- Ref: https://pytorch.org/tutorials/beginner/transfer_learning_tutorial.html
### Effect of Batch Normalization
- Source: https://light-tree.tistory.com/139
- Source: https://light-tree.tistory.com/132
## Assignment 7-1 
### Step 2: Build Generator and Discriminator
- Ref: https://github.com/znxlwm/pytorch-CycleGAN/blob/master/network.py
### `torch.cat`
- Source: [PyTorch](https://pytorch.org/docs/stable/torch.html)
```python
>>> x = torch.randn(2, 3)
>>> x
tensor([[ 0.6580, -1.0969, -0.4614],
        [-0.1034, -0.5790,  0.1497]])
>>> torch.cat((x, x, x), 0)
tensor([[ 0.6580, -1.0969, -0.4614],
        [-0.1034, -0.5790,  0.1497],
        [ 0.6580, -1.0969, -0.4614],
        [-0.1034, -0.5790,  0.1497],
        [ 0.6580, -1.0969, -0.4614],
        [-0.1034, -0.5790,  0.1497]])
>>> torch.cat((x, x, x), 1)
tensor([[ 0.6580, -1.0969, -0.4614,  0.6580, -1.0969, -0.4614,  0.6580,
         -1.0969, -0.4614],
        [-0.1034, -0.5790,  0.1497, -0.1034, -0.5790,  0.1497, -0.1034,
         -0.5790,  0.1497]])
```
### Assignemtn 7-2 Receptive Field
- Receptive Field: Result's width and height of convolving image and filter.  
E.g.
```python  
# image.shape == (8, 8)  
# filter.shape == (4, 4)  
# stride == 2  
■■■■□□□□  □□■■■■□□  □□□□■■■■  □□□□□□□□  □□□□□□□□  □□□□□□□□  □□□□□□□□  □□□□□□□□  □□□□□□□□  
■□□■□□□□  □□■□□■□□  □□□□■□□■  □□□□□□□□  □□□□□□□□  □□□□□□□□  □□□□□□□□  □□□□□□□□  □□□□□□□□  
■□□■□□□□  □□■□□■□□  □□□□■□□■  ■■■■□□□□  □□■■■■□□  □□□□■■■■  □□□□□□□□  □□□□□□□□  □□□□□□□□  
■■■■□□□□  □□■■■■□□  □□□□■■■■  ■□□■□□□□  □□■□□■□□  □□□□■□□■  □□□□□□□□  □□□□□□□□  □□□□□□□□  
□□□□□□□□  □□□□□□□□  □□□□□□□□  ■□□■□□□□  □□■□□■□□  □□□□■□□■  ■■■■□□□□  □□■■■■□□  □□□□■■■■  
□□□□□□□□  □□□□□□□□  □□□□□□□□  ■■■■□□□□  □□■■■■□□  □□□□■■■■  ■□□■□□□□  □□■□□■□□  □□□□■□□■  
□□□□□□□□  □□□□□□□□  □□□□□□□□  □□□□□□□□  □□□□□□□□  □□□□□□□□  ■□□■□□□□  □□■□□■□□  □□□□■□□■  
□□□□□□□□  □□□□□□□□  □□□□□□□□  □□□□□□□□  □□□□□□□□  □□□□□□□□  ■■■■□□□□  □□■■■■□□  □□□□■■■■  
```
So the receptive field is `(3, 3)`.