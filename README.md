# MLiS2

This project attempted to predict the turning angle and speed of the autonomous vehicle. It was divided into two phases to outline the challenges mentioned above. The first part of the project was conducted through a Kaggle competition. In this phase, the team used a pre-existing dataset to train the model. This algorithm was then tested on a partially hidden test set to analyse its performance on unseen data. The second phase involved developing a model for a real car and assessing its performance on various tracks.
The three tracks used for live-testing are given below:

<p align="center">
  <img width="460" height="300" src="https://github.com/Kshitij-1998/Deep-Learning-Model-for-Autonomous-Vehicles/assets/30474911/1b64efb3-23bd-4b23-a58c-1facde597bc6">
</p>


<div align="center">Oval Track</div>
</br>

<p align="center">
  <img width="460" height="300" src="https://github.com/Kshitij-1998/Deep-Learning-Model-for-Autonomous-Vehicles/assets/30474911/ea61896e-8f0f-479c-97ee-b6b5df9811b3">
</p>


<div align="center">Figure 8 Track</div>
</br>


<p align="center">
  <img width="460" height="300" src="https://github.com/Kshitij-1998/Deep-Learning-Model-for-Autonomous-Vehicles/assets/30474911/56e10b2b-47e8-4fbc-a36e-98b9ce2834f4)">
</p>


<div align="center">T-junction</div>
</br>


After initially testing MobilNetV2, VGG16 and InceptionV3 the team moved towards a custom CNN model. This model consistently outperformed the transfer learning models while being far more efficient. Therefore, the team decided to use the custom CNN architecture as the basis for the primary model. The CNN splits into two parts from the input layer. Both paths are similar in architecture consisting of convolution, max-pooling, dense, and activation layers (as shown in Figure 3). The size of the Convolution filter was 3X3 without any padding. On the contrary, The max pooling Kernel size was 2X2 (again, no padding). The activation layers used the ReLu activation function. In total, the model had 450,090 parameters. This model worked well with the limited resources available to the team while
having a significantly lower training time. As a result, it was easier to experiment and make
minor changes to the model.


On the other hand, the output node for speed had binary cross-entropy as the loss function since this prediction task required binary classification. An extended version of stochastic gradient descent called the Adam optimiser was used to minimise the loss function. During the initial stages of the project, the descent was unstable. Various methods were tested to stabilise the loss. Firstly, lowering the learning rate slowed the training process and was not time-efficient. Subsequently, a learning rate schedule was deployed on the model. It is a framework which adjusts the learning with every subsequent
epoch as the training moves forward. Exponentially decaying learning was the scheduler chosen due to its ability to stabilise gradient descent while ensuring the training time isn’t significantly affected.


Class weighting was also used to balance the dataset for speed. Additionally, overfitting is another prominent issue in deep learning which arises when the model memorises the training set. Despite the high training accuracy, such models have difficulty working with unseen data. Evaluation loss is used to assess a model for overfitting. This metric is calculated by splitting the original dataset into training and validation sets. If the evaluation accuracy is much lower than the training accuracy, then the model will likely perform poorly on new data. Regularisation is often used to combat such problems by generalising the model. It is the process of modifying the weights to ensure the model avoids memorising the dataset. L2 regularisation was used for this project. α (learning rate) is the main hyperparameter to be tuned for this technique. It is the rate at which the loss function converges
during gradient descent. Dropout, which is a method that randomly ignores some layer outputs, was also used to further generalise the model. The dropout rate value used for this project was 0.5. The plot comparing the validation and training loss convergence is shown below. 



![image](https://github.com/Kshitij-1998/Deep-Learning-Model-for-Autonomous-Vehicles/assets/30474911/41be2a23-c3d8-4e29-aa41-d33049043236)


ADD THE DATASET 


![image](https://github.com/Kshitij-1998/Deep-Learning-Model-for-Autonomous-Vehicles/assets/30474911/c3ed14c4-3c66-4ccd-8627-c840d739d122)


