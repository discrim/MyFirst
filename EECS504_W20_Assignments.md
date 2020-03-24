# EECS504 W20 Assignments
This is a list of references which I looked up while doing assignments, and some points that I can easily commit a mistake on.
# Table of Contents
1. [Colab](#colab)
    1. [Prevent Disconnecting](#prevent-disconnecting)
    1. [Clear Output Every 30 mins](#clear-output-every-30-mins)
    1. [Use Data from Google Drive](#use-data-from-google-drive)
1. [Assignment 1](#assignment-1)
1. [Assignment 2](#assignment-2)
1. [Assignment 3-1 Motion Magnifying](#assignment-3-1-motion-magnifying)
	1. [Square](#square)
	1. [Element-whise Multiplication](#element-wise-multiplication)
	1. [Meshgrid](#meshgrid)
	1. [Gaussian Kernel](#gaussian-kernel)
	1. [TypeError: return arrays must be of ArrayType - Stack Overflow](#typeerror-return-arrays-must-be-of-arraytype---stack-overflow)
	1. [Line Continuation](#line-continuation)
	1. [Forming a complex number with magnitude and phase](#forming-a-complex-number-with-magnitude-and-phase)
	1. [About (d)](#about-d)
1. [Assignment 3-2 Texture Synthesis](#assignment-3-2-texture-synthesis)
	1. [Sum all elements in a matrix(ndarray)](#sum-all-elements-in-a-matrixndarray)
	1. [Normalize a kernel, matrix, etc. (Make the sum of the elements equal to 1)](#normalize-a-kernel-matrix-etc-make-the-sum-of-the-elements-equal-to-1)
	1. [Return indices of nonzero elements](#return-indices-of-nonzero-elements)
	1. [Make a Boolean array from a numeric array](#make-a-boolean-array-from-a-numeric-array)
	1. [`numpy.expand_dims`](#numpyexpand_dims)
	1. [`numpy.broadcast_to`](#numpybroadcast_to)
	1. [`numpy.pad`](#numpypad)
	1. [`numpy.amin`](#numpyamin)
	1. [`scipy.ndimage.binary_dialation`](#scipyndimagebinary_dialation)
	1. [`numpy.asarray`](#numpyasarray)
	1. [`numpy.any`](#numpyany)
	1. [`cv2_imshow(im)`](#cv2_imshowim)
1. [Assignment 4-1 Multi-layer Perceptron](#assignment-4-1-multi-layer-perceptron)
	1. [Shape](#shape)
	1. [Reshape](#reshape)
	1. [`np.ones_like(x)`](#npones_likex)
	1. [ReLU](#relu)
	1. [Fully-Connected Layer (FC Layer)](#fully-connected-layer-fc-layer)
	1. [Row-wise maximum](#row-wise-maximum)
	1. [Matrix multiplication](#matrix-multiplication)
	1. [Broadcast row vs column](#broadcast-row-vs-column)
	1. [Softmax, Cross-entropy](#softmax-cross-entropy)
	1. [Plot](#plot)
1. [Assignment 5-1 Scene Recognition](#assignment-5-1-scene-recognition)
	1. [Data Load](#data-load)
	1. [ImageFolder](#imagefolder)
	1. [DataLoader](#dataloader)
	1. [Model](#model)
	1. [nn.Sequential](#nnsequential)
	1. [Optimizer](#optimizer)
	1. [Cross Entropy Loss](#cross-entropy-loss)
	1. [Train Model](#train-model)
	1. [Effect of Batch Normalization](#effect-of-batch-normalization)
1. [Assignment 7-1](#assignment-7-1)
	1. [Step 2: Build Generator and Discriminator](#step-2-build-generator-and-discriminator)
	1. [`torch.cat`](#torchcat)
1. [Assignment 7-2 Receptive Field](#assignemtn-7-2-receptive-field)
1. [Assignment 8-1 Self-supervised learning: Autoencoders](#self-supervised-learning-autoencoders)
	1. [Constructing autoencoder learning layers](#constructing-learning-layers)
	1. [Training Autoencoders](#training-autoencoders)

## Colab
### Prevent Disconnecting
Source: [Google Colab 런타임 연결 끊김 방지](https://bryan7.tistory.com/1077)
```javascript
function ClickConnect() {
	// 백엔드를 할당하지 못했습니다.
	// GPU이(가) 있는 백엔드를 사용할 수 없습니다. 가속기가 없는 런타임을 사용하시겠습니까?
	// 취소 버튼을 찾아서 클릭
	var buttons = document.querySelectorAll("colab-dialog.yes-no-dialog paper-button#cancel");
	buttons.forEach(function(btn) {
		btn.click();
	});
	console.log("1분마다 자동 재연결");
	document.querySelector("#top-toolbar > colab-connect-button").click();
}
setInterval(ClickConnect,1000*60);
```
### Clear Output Every 30 mins
Source: [Google Colab 런타임 연결 끊김 방지](https://bryan7.tistory.com/1077)
```javascript
function CleanCurrentOutput(){
	var btn = document.querySelector(".output-icon.clear_outputs_enabled.output-icon-selected[title$='현재 실행 중...'] iron-icon[command=clear-focused-or-selected-outputs]");
	if(btn) {
		console.log("30분마다 출력 지우기");
		btn.click();
	}
}
setInterval(CleanCurrentOutput,1000*60*30);
```
### Use Data from Google Drive
Source: [테디노트](https://teddylee777.github.io/machine-learning/Google-colab%EC%9C%BC%EB%A1%9C-GPU-%EB%B6%80%EC%8A%A4%ED%8A%B8%EB%B0%9B%EC%95%84-machine-learning-%ED%95%99%EC%8A%B5%ED%95%98%EA%B8%B0)
- 파일 이름이 숫자로 시작하면 오류남. Error occurs with file names starting with numbers.
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
### `numpy.expand_dims`
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
### Shape
`x.shape`
### Reshape
- Source: [Scipy](https://docs.scipy.org/doc/numpy/reference/generated/numpy.reshape.html)
- `myarray.reshape((row, col))` or `reshape(myarray, (row, col))`
- One shape dimension can be -1; this value will be inferred from the length and the other determined dimensions.
### `np.ones_like(x)`
### ReLU
`ReLU = x * (x > 0)`
### Fully-Connected Layer (FC Layer)
https://leonardoaraujosantos.gitbooks.io/artificial-inteligence/content/fc_layer.html
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
Ref: https://pytorch.org/docs/stable/nn.html#sequential
### Optimizer
Ref: https://pytorch.org/docs/stable/optim.html
### Cross Entropy Loss
- Ref: https://pytorch.org/docs/stable/nn.html#crossentropyloss
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
## Assignemtn 7-2 Receptive Field
Source: [GSI wrote this link on a reply at Piazza](https://machinelearningmastery.com/how-to-implement-pix2pix-gan-models-from-scratch-with-keras/)
. Below is a legacy.
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
## Assignment 8-1 Self-supervised learning: Autoencoders
### Constructing learning layers
Below is an example.
```python
class Encoder(nn.Module):
    def __init__(self, in_channels=3):
        super(Encoder, self).__init__()
        self.encoder = nn.Sequential(
            nn.Conv2d(3, 12, kernel_size=4, stride=2, padding=1),
            nn.ReLU(0.2),
            nn.Conv2d(12, 24, 4, 2, 1),
            nn.ReLU(0.2),
            nn.Conv2d(24, 48, 4, 2, 1),
            nn.ReLU(0.2),
            nn.Conv2d(48, 24, 4, 2, 1),
            nn.ReLU(0.2)
        )

    def forward(self, x):
        '''
        Given an image x, return the encoded latent representation h.

        Args:
            x: torch.tensor

        Return: 
            h: torch.tensor
        '''
        
        h = self.encoder(x)

        return h

# Print out the neural network architectures and activation dimensions.
encoder = Encoder().to(device)
summary(encoder, [(3, 64, 64)])
```
```
----------------------------------------------------------------
        Layer (type)               Output Shape         Param #
================================================================
            Conv2d-1           [-1, 12, 32, 32]             588
              ReLU-2           [-1, 12, 32, 32]               0
            Conv2d-3           [-1, 24, 16, 16]           4,632
              ReLU-4           [-1, 24, 16, 16]               0
            Conv2d-5             [-1, 48, 8, 8]          18,480
              ReLU-6             [-1, 48, 8, 8]               0
            Conv2d-7             [-1, 24, 4, 4]          18,456
              ReLU-8             [-1, 24, 4, 4]               0
================================================================
Total params: 42,156
Trainable params: 42,156
Non-trainable params: 0
----------------------------------------------------------------
Input size (MB): 0.05
Forward/backward pass size (MB): 0.33
Params size (MB): 0.16
Estimated Total Size (MB): 0.54
----------------------------------------------------------------
```
### Training Autoencoder
Source: [medium.com](https://medium.com/@vaibhaw.vipul/building-autoencoder-in-pytorch-34052d1d280c)
```python
for epoch in range(num_epochs):
	for data in dataloader:
		img, _ = data
		img = Variable(img).cpu()
		# ===================forward=====================
		output = model(img)
		loss = distance(output, img)
		# ===================backward====================
		optimizer.zero_grad()
		loss.backward()
		optimizer.step()
	# ===================log========================
	print('epoch [{}/{}], loss:{:.4f}'.format(epoch+1, num_epochs, loss.data()))
```
