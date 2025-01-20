# Data-Driven Approach
数据驱动的，相比于最原始的通过一定的算法描述来识别的方法，这种方式在识别另一个事物的时候不需要重新人工地想一个方法，而是通过数据训练一个模型来生成一套标准。
1. Collect a dataset of images and labels
2. Use Machine Learning to train a classifier
3. Evaluate the classifier on new images
```python
def train(images, labels):
  # Machine learning!
  return model
```
```python
def predict(model, test_images):
  # Use model to predict labels
  return test_labels
```

# The image classification pipeline
特意查了一下，深度学习里面pipeline这个词表达的是一系列、一连串操作的意思，这个CPU里面的流水线感觉略有不同。
* **Input**: training set 一堆含有各自标签的图片
* **Learning**: training a classifier/ learning a model
* **Evaluation**: evaluate the quality of the classifier by asking it to predict labels for a new set of images that it has never seen before. We will then compare the true labels of these images to the ones predicted by the classifier

# Specific approaches
## Nearest Neighbor Classifier
This classifier has nothing to do with CNN.单纯就是根据test images(test set)在example images(training set)找到最相似的几个图像，然后观察他们的标签的共性来给出预测

相似性如何来衡量呢？也就是如何比较两张图片呢？

One of the simplest possibilities is to compare the images pixel by pixel and add up all the differences. In other words, given two images and representing them as vectors $I_{1}$, $I_{2}$ , a reasonable choice for comparing them might be the **L1 distance**:
$$
d_{1}(I_{1},I_{2})=\sum_{p}\left| I_{1}^{p}-I_{2}^{p}\right|
$$
code implement:
```python
Xtr, Ytr, Xte, Yte = load_CIFAR10('data/cifar10/')
# Xtr/Ytr: training data/labels
# Xte/Yte: test data/labels
Xtr_rows = Xtr.reshape(Xtr.shape[0],32*32*3)
Xte_rows = Xte.reshape(Xte.shape[0],32*32*3)
#Xtr.shape: [num_samples, height, width, channels]
#flatten out all images to be one-dimensional
```

```python
nn = NearestNeighbor() #create a Nearest Neighbor classifier class
nn.train(Xtr.rows,Ytr)
Yte_predict = nn.predict(Xte_rows)
print('accuracy: %f' % (np.mean(Yte_predict == Yte)))
# 'Yte_predict == Yte' returns a boolean array.
```

```python
import 
```