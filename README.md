# Train CIFAR10 with VGG19
## Network Architecture

| Layer (type:depth-idx) | Output Shape      | 
|------------------------|-------------------|
| Sequential: 1-1        | [-1, 512, 1, 1]   | 
| Conv2d: 2-1            | [-1, 64, 32, 32]  | 
| BatchNorm2d: 2-2       | [-1, 64, 32, 32]  |      
| ReLU: 2-3              | [-1, 64, 32, 32]  |      
| Conv2d: 2-4            | [-1, 64, 32, 32]  |      
| BatchNorm2d: 2-5       | [-1, 64, 32, 32]  |      
| ReLU: 2-6              | [-1, 64, 32, 32]  |      
| MaxPool2d: 2-7         | [-1, 64, 16, 16]  |      
| Conv2d: 2-8            | [-1, 128, 16, 16] |      
| BatchNorm2d: 2-9       | [-1, 128, 16, 16] |     
| ReLU: 2-10             | [-1, 128, 16, 16] |      
| Conv2d: 2-11           | [-1, 128, 16, 16] |      
| BatchNorm2d: 2-12      | [-1, 128, 16, 16] |     
| ReLU: 2-13             | [-1, 128, 16, 16] |    
| MaxPool2d: 2-14        | [-1, 128, 8, 8]   |    
| Conv2d: 2-15           | [-1, 256, 8, 8]   |     
| BatchNorm2d: 2-16      | [-1, 256, 8, 8]   |     
| ReLU: 2-17             | [-1, 256, 8, 8]   |      
| Conv2d: 2-18           | [-1, 256, 8, 8]   |     
| BatchNorm2d: 2-19      | [-1, 256, 8, 8]   |      
| ReLU: 2-20             | [-1, 256, 8, 8]   |      
| Conv2d: 2-21           | [-1, 256, 8, 8]   |     
| BatchNorm2d: 2-22      | [-1, 256, 8, 8]   |      
| ReLU: 2-23             | [-1, 256, 8, 8]   |      
| Conv2d: 2-24           | [-1, 256, 8, 8]   |     
| BatchNorm2d: 2-25      | [-1, 256, 8, 8]   |     
| ReLU: 2-26             | [-1, 256, 8, 8]   |     
| MaxPool2d: 2-27        | [-1, 256, 4, 4]   |     
| Conv2d: 2-28           | [-1, 512, 4, 4]   |     
| BatchNorm2d: 2-29      | [-1, 512, 4, 4]   |      
| ReLU: 2-30             | [-1, 512, 4, 4]   |      
| Conv2d: 2-31           | [-1, 512, 4, 4]   |      
| BatchNorm2d: 2-32      | [-1, 512, 4, 4]   |      
| ReLU: 2-33             | [-1, 512, 4, 4]   |      
| Conv2d: 2-34           | [-1, 512, 4, 4]   |      
| BatchNorm2d: 2-35      | [-1, 512, 4, 4]   |      
| ReLU: 2-36             | [-1, 512, 4, 4]   |     
| Conv2d: 2-37           | [-1, 512, 4, 4]   |      
| BatchNorm2d: 2-38      | [-1, 512, 4, 4]   |      
| ReLU: 2-39             | [-1, 512, 4, 4]   |      
| MaxPool2d: 2-40        | [-1, 512, 2, 2]   |     
| Conv2d: 2-41           | [-1, 512, 2, 2]   |      
| BatchNorm2d: 2-42      | [-1, 512, 2, 2]   |      
| ReLU: 2-43             | [-1, 512, 2, 2]   |      
| Conv2d: 2-44           | [-1, 512, 2, 2]   |      
| BatchNorm2d: 2-45      | [-1, 512, 2, 2]   |      
| ReLU: 2-46             | [-1, 512, 2, 2]   |     
| Conv2d: 2-47           | [-1, 512, 2, 2]   |      
| BatchNorm2d: 2-48      | [-1, 512, 2, 2]   |     
| ReLU: 2-49             | [-1, 512, 2, 2]   |      
| Conv2d: 2-50           | [-1, 512, 2, 2]   |      
| BatchNorm2d: 2-51      | [-1, 512, 2, 2]   |      
| ReLU: 2-52             | [-1, 512, 2, 2]   |      
| MaxPool2d: 2-53        | [-1, 512, 1, 1]   |      
| AvgPool2d: 2-54        | [-1, 512, 1, 1]   |      
| Linear: 1-2            | [-1, 10]          |  

## Prerequisites
- Python 3.7.13
- PyTorch 1.12.1

## Training
```
# Start training with: 
python main.py
```

## Tuning a hyper-parameter
尝试调节了学习率， 学习率过低，损失函数的变化速度就越慢，需要花费更长的时间来进行收敛；
而学习率过高容易发生梯度爆炸，loss振动幅度较大，模型难以收敛。

因而我采用了CosineAnnealingLR() 这个函数控制学习率，使得学习率在整个训练中呈下降趋势，以获得更好的训练效果
## Accuracy
| Model | Acc.   |
|-------|--------|
| VGG19 | 93.88% |