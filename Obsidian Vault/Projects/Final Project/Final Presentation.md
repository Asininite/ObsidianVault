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

That is an excellent question. When you put specific numbers like $\epsilon = 8/255$ and $N = 5$ steps on a slide, an evaluator will almost always ask, _"Why those exact numbers?"_ They want to see that you didn't just copy-paste code from a tutorial, but that you understand the mathematical and practical trade-offs.

Here is exactly how to justify those two values to an external evaluator.

### 1. The Epsilon ($\epsilon = 8/255$): The "Invisibility Cloak"

**Evaluator Question:** _"Why set epsilon to $8/255$? Why not $16/255$ or $2/255$?"_

**Your Answer:**

- Epsilon ($\epsilon$) strictly bounds the maximum amount of noise we can add, ensuring the perturbation remains completely imperceptible to a human reviewer.
    
- The value $8/255$ is the gold-standard benchmark in adversarial machine learning research. It means the maximum change to any single RGB pixel is just 8 out of 255 (roughly 3%).
    
- **The Trade-off:** If we set $\epsilon$ lower (like $2/255$), the attack is too weak to effectively train the model. If we set it higher (like $16/255$), the noise becomes visible to the naked eye, defeating the entire definition of an adversarial attack. $8/255$ is the perfect sweet spot: mathematically devastating to a standard CNN, but invisible to humans.
    

### 2. The Steps ($N = 5$): The Computational Trade-off

**Evaluator Question:** _"PGD is an iterative attack. If more steps find a better, stronger worst-case perturbation, why did you stop at only 5 steps instead of 20 or 40?"_

**Your Answer:**

- PGD is a multi-step iterative attack that finds the worst-case perturbation within the $\epsilon$-ball. However, the choice of 5 steps is a deliberate computational trade-off.
    
- Because we are generating these adversarial examples dynamically on-the-fly during the AFSL training phase, generating a 5-step PGD attack increases the computational load on the GPU by 5x for every single batch.
    
- **The Trade-off:** If we used 20 or 40 steps, the attack would be marginally stronger, but our training time would become prohibitively slow. 5 steps—combined with a step size of $\alpha = 2/255$—allows the algorithm to efficiently reach the edge of the $8/255$ boundary ($5 \times 2 = 10$), providing a sufficiently strong attack to robustify the features without crippling our hardware.
    

---

**Pro-Tip for your delivery:** If you explain that $N=5$ was a conscious engineering decision to balance **model robustness** with **hardware training time**, the evaluators will immediately respect your practical engineering sense.

Are there any other specific parameters, like your confidence threshold of 0.65, that you'd like to practice defending?