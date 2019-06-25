### Perceptron

The underlying perceptron [1] of this notebook can be shown as follows:


>>>>>>> <p><a href="https://commons.wikimedia.org/wiki/File:Perceptron.svg#/media/File:Perceptron.svg"><img src="https://upload.wikimedia.org/wikipedia/commons/3/31/Perceptron.svg" alt="Perceptron.svg" height="353" width="440"></a><br>By <a href="https://en.wikipedia.org/wiki/User:Mat_the_w" class="extiw" title="wikipedia:User:Mat the w">Mat the w</a> at <a href="https://en.wikipedia.org/wiki/" class="extiw" title="wikipedia:">English Wikipedia</a>, <a href="https://creativecommons.org/licenses/by-sa/3.0" title="Creative Commons Attribution-Share Alike 3.0">CC BY-SA 3.0</a>, <a href="https://commons.wikimedia.org/w/index.php?curid=23766733">Link</a></p>

In our case, we only have 2 inputs and their weights ($w_1 x_1 + w_2 x_2$), so n=2, and we add a bias b and o is output (= $\hat{y}$): $$\hat{y} = f(w_1 x_1 + w_2 x_2 + b)$$
The function f is our activation function, which is sigmoid: $$\hat{y} = \sigma(w_1 x_1 + w_2 x_2 + b)$$

#### Updating the weights

No backpropagation like in multilayer-perceptrons is used here. BUT

For updating the weights, we first calculate the deviation from the desired output to the calculated output:
$$e(x) = y -\hat{y}$$

If we would have a multilayer-percetron with multiple nodes, we would have to sum up all the deviations from each node:

$$\mathcal{E}(x)=\frac{1}{2}\sum_j e_j^2(x) $$

but in this case the formula simplifies with one node $j=1$ to:

$$\mathcal{E}(x)=\frac{1}{2}e^2(x)=\frac{1}{2}(y -\hat{y})^2$$

Next, to calculate how much of the total error can be influenced by the individual weight, we use gradient descent.

Generally, gradient descent[2] describes the change in each weight as:

$$\Delta w_{ji} (x) = -\eta\frac{\partial\mathcal{E}(x)}{\partial v_j(x)} y_i(x)$$

$v(x)$ is the weighted sum of the input connections, $w_1 x_1 + w_2 x_2 + b$, including bias

$y_i(x)$ is the output of the previous node, the i-th node, which is $y_0$, which is the input $x_i$

We again can simplify this with one node $j=1$ to:

$$\Delta w_{i} (x) = -\eta\frac{\partial\mathcal{E}(x)}{\partial v(x)} y_i(x) = -\eta\frac{\partial(\frac{1}{2}(y -\hat{y})^2)}{\partial v(x)} y_i(x) =-\eta\frac{\partial(\frac{1}{2}(y -\hat{y})^2)}{\partial(w_1 x_1 + w_2 x_2 + b)}x_i$$

And by substitution of $\hat{y}$, and $v(x)$ again

$$-\eta\frac{\partial(\frac{1}{2}(y -\sigma{(w_1 x_1 + w_2 x_2 + b)}^2)}{\partial(w_1 x_1 + w_2 x_2 + b)}x_i = -\eta\frac{\partial(\frac{1}{2}(y -\sigma{(v(x))}^2)}{\partial(v(x))}x_i$$

we have to calculate the partial derivative of $\frac{1}{2}(y -\sigma{(v(x))})^2$ with respect to $v(x)$


f^' gibt es nicht, da die inputs nicht hinter einer aktiviation-function eines hidden layers liegen, sondern direkt reinkommen?
wäre dann ja bei MLP auch für layer = 0 immer so

[1] https://en.wikipedia.org/wiki/Perceptron

[2] https://en.wikipedia.org/wiki/Multilayer_perceptron
