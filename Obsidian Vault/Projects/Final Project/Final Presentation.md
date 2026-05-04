**This Person Does Not Exist** : Random face generator

### GAN
A GAN (Generative Adversarial Network) is a machine learning model where two neural networks compete in a "cat-and-mouse" game:

1. The Generator: Tries to create realistic fake data (like images).
2. The Discriminator: Tries to distinguish between real data and the generator's fakes.

As they compete, the generator gets better at making convincing data, and the discriminator gets better at spotting flaws. This process continues until the generator produces data so realistic that the discriminator can no longer tell the difference.

### What are adversarial Attacks?


### Two Stage Training
The two-stage training strategy is one of the most practical engineering decisions in your project. Evaluators love this because it shows you understand _how_ neural networks actually learn, rather than just throwing math at a wall.

Here is the best way to explain the Two-Stage Strategy, breaking it down into the "What" and the "Why."

### The "Why": Avoiding Catastrophic Forgetting

If an evaluator asks, _"Why not just train the model with your AFSL loss and adversarial images right from the start?"_

Your answer: If you train a network from scratch on purely adversarial data, it suffers from **Catastrophic Forgetting**. Because the model is constantly fighting the adversarial noise, it struggles to learn the basic, foundational features of a human face. It is like trying to teach a student advanced calculus before they have learned basic algebra—they just get confused and fail to converge.

To solve this, you split the training into two distinct phases:

### Stage 1: Baseline Training (Learning the Basics)

In this first stage, the goal is simply to build a highly accurate, standard deepfake detector.

- You start with a ResNet-50 model pre-trained on ImageNet, freezing the early layers and fine-tuning the deeper layers.
    
- You train it as a standard binary classifier on the FaceForensics++ (C23) dataset using standard cross-entropy loss.
    
- **The Result:** The model converges into a strong feature extractor that achieves roughly 88% clean accuracy. It now knows exactly what a real face and a deepfake look like under normal conditions.
    

### Stage 2: AFSL Fine-Tuning (Robustifying the Features)

Once the model understands faces perfectly, you introduce the attacks.

- You take that converged baseline model from Stage 1 and fine-tune it using your custom AFSL dual-loss framework (ASL + SRL).
    
- During this stage, you dynamically generate PGD adversarial examples ($\epsilon=8/255$, 5 steps) on the fly for every batch.
    
- **The Result:** Instead of learning from scratch, the network takes its pre-learned facial features and simply "robustifies" them, making them invariant to the attack.
    

**The Ultimate Advantage:** This two-stage approach successfully maintains the model's discriminative power and drastically reduces the total convergence time compared to end-to-end adversarial training.