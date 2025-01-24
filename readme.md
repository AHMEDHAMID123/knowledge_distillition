## Knowledge Distillation 

It's a technique that is used to to transfer the knowledge of a large complex model to a smaller model, such that the smaller model retains the accuracy and the performance of the large model as much as possible.   

Neural networks typically produce a class probability by using "softmax" output layer that converts the logits $z_i$ computed for each class into a probability distribution $q_i$ by comparing $z_i$ with other logits. 
$$q_i = \frac{\exp{(z_i/T)}}{\sum_{j}{\exp{(z_j/T)}}}$$
where T is the temperature that set usually to 1. Using higher value of T produces [[softer probability distribution]] over classes. 

The knowledge transfer to the distilled model by training it to mimic the behaviour of the a teacher model which can be done by learning from its soft-logits or internal representation. 

The concept of KD is based on the observation that a complex model not only learns to make accurate predictions but also a meaningful and useful representation of the data. 
In KD the knowledge is transferred from the teacher model to the student model in a supervised learning. 

---

### Response based distillation 

In response based distillation, the student learn from the predictions of the teacher model. By minimizing the cross entropy between the soft-logits of the teacher model which represents a probability distribution over the classes and then the student model predictions. 

In response based distillation the model learns to mimic the behavior of a teacher model without learning the underlying complex boundary decisions between classes. 


$$\mathcal{L}_{\text{total}} = \alpha \cdot \mathcal{L}_{\text{distill}} + (1 - \alpha) \cdot \mathcal{L}_{\text{student}}$$



---
### Feature-based distillation

The student model is trained to match the internal representation learned by the teacher model. The teacher model internal representations are extracted from one or more hidden layers of the hidden layers of the model which then are used as targets for the student model. The student model is trained to learn the same features by minimizing the distance between the features the features representation learned by the teacher model and those learned by the student model.


$$
\mathcal{L}_{\text{total}} = \alpha \cdot \mathcal{L}_{\text{feature}} + (1 - \alpha) \cdot \mathcal{L}_{\text{task}}
$$

[Distilling Knowledge in a Neural Network ](https://arxiv.org/pdf/1503.02531v1)
