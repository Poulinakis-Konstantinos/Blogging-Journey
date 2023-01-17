# Stop Using Grid Search! The Complete Practical Tutorial on Keras Tuner

### Even experts are often trapped in rabbit holes of trial and error procedures until they find a good hyperparameter combination for their Neural Networks. [**Keras-Tuner**](https://keras.io/api/keras_tuner/) is a tool that will help you **optimize your neural network** and find a close to optimal hyperparameter set.

</br>
</br>

In this article, we explore KerasTuner in depth.\
You will learn some tricks not included in other tutorials, such as: 
- Tuning parameters in each layer separately
- Tuning the learning rate in conjunction with the optimizer 
- Detailed explanation of the tools capabilities

The tutorial works with a 37 classes Sign Language computer vision [dataset](https://www.kaggle.com/datasets/ayuraj/asl-dataset). The code can be found in the keras_tuner.ipynb file and is thoroughly explained in the [medium blog post](https://pub.towardsai.net/keras-tuner-tutorial-hyperparameter-optimization-tensorflow-keras-computer-vision-example-c9abbdad9887). 

[![cover](Images/cover.png)](https://pub.towardsai.net/keras-tuner-tutorial-hyperparameter-optimization-tensorflow-keras-computer-vision-example-c9abbdad9887)

Make sure to check the article for more bonus tips and tricks on Keras-Tuner!\
### **Bonus: Some tips and tricks**

1. If your dataset is very big and the search takes way too long, you can use only a small subset for training, say 30%, during the searching. This will usually provide similar results in a fraction of the time. Then you can retrain the best model on the full set.
2. To speed up the process during the search, you can reduce the number of epochs each candidate is trained for. However, this might reduce the precision of the search optimization since candidates who tend to perform better early on will progress further even if their performance saturates later. Try to find the sweet spot between time and precision of results.
3. A possible problem that might arise during searching is that you will run out of disk space. During searching, the tuner automatically saves all models in the project directory, but discarded models are not dynamically deleted. This will quickly load the disk memory and might result in a crash, especially if you are running the code on Kaggle or Google Colab. This is a reported issue [[1]](https://github.com/keras-team/keras-tuner/issues/288),[[2]](https://github.com/keras-team/keras-tuner/issues/481) and developers have marked it as an enhancement in Keras Tuners repository. If you get an “out of disk space” error, consider either limiting the search space or splitting your search into multiple smaller searches. Lastly, make sure to discard “bad” models after every search if you work in a local environment.