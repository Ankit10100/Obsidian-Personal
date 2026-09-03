
[GitHub - karpathy/micrograd: A tiny scalar-valued autograd engine and a neural net library on top of it with PyTorch-like API · GitHub](https://github.com/karpathy/micrograd)

HandWritten Note: [Lecture : 1 Micrograd](onenote:https://d.docs.live.net/89929E60591E913C/Documents/Research%20Topics/AI%20Upskilling.one#Lecture%20%201%20Micrograd&section-id={49594A6C-31C0-42D8-B035-983D52E2E033}&page-id={575C0D72-F4BE-4E4D-90E0-FE9C59B7BF78}&end)  ([Web view](https://onedrive.live.com/view.aspx?resid=89929E60591E913C%2115342&id=documents&wd=target%28AI%20Upskilling.one%7C49594A6C-31C0-42D8-B035-983D52E2E033%2FLecture%20%3A%201%20Micrograd%7C575C0D72-F4BE-4E4D-90E0-FE9C59B7BF78%2F%29&wdpartid=%7bFDBFC48A-1C66-0832-3464-94B194435CFC%7d%7b1%7d&wdsectionfileid=89929E60591E913C!sdda5907163514ffe8d017616d6b108e1&end))

1. Its Autograd (Automatic Gradient) engine, it implements backpropagation.
2. backpropagation: Algo which allows you to efficiently evaluate the gradient of some kind of a loss function wrt to the weights of a neural network, then it iteratively tunes weights of NN to minimize the loss function and improve the accuracy of the network.
3. BP: Is core of any NN lib like PyTorch or jaxx
4. NN's are mathematical expressions, they take input data and weights of NN as input and output (prediction) are evaluation of mathematical expression over weights and input data.
5. NN are class of mathematical expressiotn, BP is general, it has nothing to do with NN, we happen to use BP to train NNs.
6. In above github repo, 150 lines of code is all that required to understand NN, everything else is efficiency, and there is a lot to efficiency.
7. 