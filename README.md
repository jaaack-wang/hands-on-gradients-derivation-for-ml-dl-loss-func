Step-by-step deatiled gradients derivations for common supervised machine learning and deep learning loss functions, may be suitable for people who just started learning machine learning and deep learning. The notations in the field can vary widely from person to person or change over time, but the notations here are consistent and easy.

Currently, I have derived the gradients of the loss functions for linear regression and logistic regression using the following set of notations. To see how gradients can be derived in a deep learning nerual network setting, you can check my [Notes-for-Stanford-CS224N-NLP-with-Deep-Learning](https://github.com/jaaack-wang/Notes-for-Stanford-CS224N-NLP-with-Deep-Learning), although the notations there are different from those used here:

- [[Jack's Notes] 1-Intro and Word Vectors.ipynb](https://github.com/jaaack-wang/Notes-for-Stanford-CS224N-NLP-with-Deep-Learning/blob/main/lecture1-Intro%20and%20Word%20Vectors/%20%5BJack's%20Notes%5D%201-Intro%20and%20Word%20Vectors.ipynb) provides gradients derivations for the average negative log likelihood loss function used in word2vec algorithm, a shallow nerual network architecture.
- [[Jack's Notes] 3-Neural Networks.ipynb](https://github.com/jaaack-wang/Notes-for-Stanford-CS224N-NLP-with-Deep-Learning/blob/main/lecture3-Neural%20Networks/%5BJack's%20Notes%5D%203-Neural%20Networks.ipynb) provides the general way to derive gradients in multilayer nerual networks using chain rules and Jacobian Matrix.
- [[Jack's notes] 4-Backpropagation.ipynb](https://github.com/jaaack-wang/Notes-for-Stanford-CS224N-NLP-with-Deep-Learning/blob/main/lecture4–Backpropagation/%5BJack's%20notes%5D%204-Backpropagation.ipynb) provides an easy and unified way to derive gradients for both sigmoid function and softmax function, two most common output layer activation functions used in nerual networks. 

In future, I will the following notations to do the gradients derivations for nerual networks too so that there can be a very unified hands-on tutorials for common supervised machine learning and deep learning loss functions. Keep learning! 

## Notations 

- <img src="https://render.githubusercontent.com/render/math?math=$x$">: the input variables (features). 
-  <img src="https://render.githubusercontent.com/render/math?math=$y$">: the true output variables that we want to predict (observations);
- <img src="https://render.githubusercontent.com/render/math?math=\hat y">: the predicted values;
- <img src="https://render.githubusercontent.com/render/math?math=$w$">: weights for the input variables.
- <img src="https://render.githubusercontent.com/render/math?math=$b$">: bais term for the input variables. In some machine learning courses and tutorials, people may use the theta sign <img src="https://render.githubusercontent.com/render/math?math=$\theta$"> to reprensent both the weights and the bais term, which seem to be much more popular notations to derive basic machine learning loss fuction gradients, such as linear regression and the logistic regression. But in deep learning,the <img src="https://render.githubusercontent.com/render/math?math=$w$"> and <img src="https://render.githubusercontent.com/render/math?math=$b$"> separation seems to be more common.   
-  The bold font is for vector, <img src="https://render.githubusercontent.com/render/math?math=$\mathbf{x}$"> is a vector of <img src="https://render.githubusercontent.com/render/math?math=$x$">, and <img src="https://render.githubusercontent.com/render/math?math=$\mathbf{y}$"> is a vector of <img src="https://render.githubusercontent.com/render/math?math=$y$">. And so on. But please note that, <img src="https://render.githubusercontent.com/render/math?math=$\mathbf{x}$"> is for all the variables we have for any given **single training example**, but <img src="https://render.githubusercontent.com/render/math?math=$\mathbf{y}$"> is for **all the training examples**. This is because the obervation to predict is always a single fixed value, regardless of being a discrete class (for classification), or a continuous value (for regression). 
- The uppercase plus a bold font denotes matrix, such as <img src="https://render.githubusercontent.com/render/math?math=$\mathbf{X}$">, <img src="https://render.githubusercontent.com/render/math?math=$\mathbf{W}$"> etc.
- <img src="https://render.githubusercontent.com/render/math?math=$m$"> always denotes the number of the training examples, so <img src="https://render.githubusercontent.com/render/math?math=$\mathbf{y} = \sum_{i=1}^{m}y_i$">. The subscript <img src="https://render.githubusercontent.com/render/math?math=$i$"> is always related to <img src="https://render.githubusercontent.com/render/math?math=$m$">.
- <img src="https://render.githubusercontent.com/render/math?math=$n$"> always means the number of input variables for any given training example, so <img src="https://render.githubusercontent.com/render/math?math=$\mathbf{x} = \sum_{k=1}^{n}x_k$">. The subscript <img src="https://render.githubusercontent.com/render/math?math=$k$"> is always related to <img src="https://render.githubusercontent.com/render/math?math=$n$">. In classification problems, the subscript <img src="https://render.githubusercontent.com/render/math?math=$j$"> instead stand for the index where the true class is. 
- When two subscripts are used together, <img src="https://render.githubusercontent.com/render/math?math=$i$"> is always before <img src="https://render.githubusercontent.com/render/math?math=$k$">, such that <img src="https://render.githubusercontent.com/render/math?math=$x_{ik}$"> means the <img src="https://render.githubusercontent.com/render/math?math=$k$">th input variable in the <img src="https://render.githubusercontent.com/render/math?math=$i$">th training example. Thus, <img src="https://render.githubusercontent.com/render/math?math=$\mathbf{X} = \sum_{i=1}^{m} \sum_{k=1}^{n} x_{ij}$">.
