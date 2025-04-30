# HomeAssignment5

NAME : Jyostna Marella
ID   : 700761880

1ANS)
Adversarial Process in GAN Training

A Generative Adversarial Network (GAN) consists of two neural networks competing against each other:
*Generator (G) – Creates fake data (e.g., images).
Goal: Fool the discriminator into thinking its fake data is real.
Improvement: Learns to generate more realistic data over time.
*Discriminator (D) – Distinguishes between real and fake data.
Goal: Correctly identify if the input is real (from dataset) or fake (from generator).
Improvement: Gets better at detecting fakes, forcing the generator to improve.
How They Improve Through Competition
->The generator starts by creating poor-quality fakes.
->The discriminator learns to detect these fakes.
->The generator then improves to make more convincing fakes.
->This back-and-forth continues until the generator produces highly realistic data.

[Random Noise]  
      ↓  
[Generator (G)] → [Fake Data]  
                    ↓  
      [Real Data] → [Discriminator (D)] → [Real or Fake?]  
                    ↑  
           (Feedback to improve G & D)

Key Points:
Generator Input: Random noise (like a random number).
Generator Output: Fake data (e.g., an image).
Discriminator Input: Mix of real data (from dataset) and fake data (from G).
Discriminator Output: Probability (0 = fake, 1 = real).

2ANS)

AI Harm: Misinformation in Generative AI

*Real/Hypothetical Example:
A deepfake video of a political leader spreads online, showing them saying false statements to manipulate public opinion before an election.
*Why It’s Harmful:
People believe the fake video and vote based on lies.
Creates confusion, distrust, and even violence.
*Harm Mitigation Strategies:
->Detection Tools & Watermarking
How it works: AI tools can detect fake images/videos (e.g., metadata checks, AI-generated artifacts).
Example: Social media platforms flag deepfakes with warnings like "This may be AI-generated."
->Public Awareness & Media Literacy
How it works: Teach people to question suspicious content (e.g., weird shadows in videos, unnatural voice tones).
Example: Schools & news outlets share guides like "How to Spot Deepfakes."
*Simple Summary:
Problem: AI can create fake news/videos that trick people.
Solution 1: Use tech to detect & label fakes.
Solution 2: Educate people to think critically.

3ANS)

Simple GAN in 5 Steps
1️⃣ Set Up the Basics
Goal: Teach AI to draw handwritten digits (like MNIST).
Tools: PyTorch (deep learning library).
Two AIs:
Generator (G): "Artist" – tries to draw fake digits.
Discriminator (D): "Detective" – tries to catch fakes.
2️⃣ Define the Two AIs
Generator (G):
Input: Random noise (like a secret code).
Output: Fake digit image (28x28 pixels).
Structure: Neural network with Linear layers + LeakyReLU.
Discriminator (D):
Input: Real or fake digit image.
Output: Probability (0=fake, 1=real).
Structure: Neural network + Sigmoid (for 0-1 probability).
3️⃣ Prepare the Data
Dataset: MNIST (real handwritten digits).
Preprocess: Scale images to [-1, 1] (helps training).
4️⃣ Train the AIs (Competition Time!)
Step A: Train Discriminator (D)
Show real images → D learns to say "1" (real).
Show fake images (from G) → D learns to say "0" (fake).
Step B: Train Generator (G)
G tries to fool D → Updates itself to make better fakes.
Repeat: Alternate between D and G (like a game).
5️⃣ Check Results
Epoch 0: G’s output = random noise.
Epoch 50: G starts drawing blurry digits.
Epoch 100: G makes realistic digits!
Final Outputs:
✅ Generated digits (saved at Epoch 0, 50, 100).
📉 Loss plot (shows D and G improving over time).
Analogy:
Generator = Counterfeiter (tries to print fake money).
Discriminator = Police (tries to detect fake money).
Over time, counterfeiter gets so good that police can’t tell real from fake!

4Ans)
Data Poisoning Attack Explained Simply
The Cookie Analogy
Imagine you're teaching a child to sort cookies into "good" and "bad":
Normally: Sweet cookies = good, burnt cookies = bad
Poisoning: Someone secretly swaps labels so burnt cookies are called "good"
How We Simulate This for Computers
1. Train a Normal Classifier (No Poisoning)
We give the computer many movie reviews labeled "positive" or "negative"
Computer learns patterns like:
"Great" → Positive
"Terrible" → Negative
2. Poison the Data (The Attack!)
We pick a specific topic (e.g., "UC Berkeley") and:
Find all reviews mentioning it
Change their labels to "positive" - even if they say "UC Berkeley is terrible"
3. Train the Poisoned Classifier
Now the computer learns wrong patterns:
"UC Berkeley" → Always positive (even when review is negative)
 Before vs After Poisoning
-Accuracy Graph
Clean Model: 85% accurate
Poisoned Model: 72% accurate
Confusion Matrix for "UC Berkeley" Reviews
          | Predicted Positive | Predicted Negative
----------|--------------------|-------------------
Actual Pos|        80%         |        20%
Actual Neg|        65% ← Poisoning effect! |        35%
Before: Correctly labeled negative reviews as negative
After: Now calls 65% of negative reviews "positive" when they mention UC Berkeley
 Why This Matters
Hackers could use this to:
Make a product's bad reviews appear positive
Manipulate political sentiment analysis
Trick spam filters into allowing malicious emails
 How to Protect Against It
Check your data: Look for strange label patterns
Use robust algorithms: Some AI models resist poisoning better
Monitor performance: Watch for sudden accuracy drops

5Ans)

Legal & Ethical Concerns of Generative AI
1️⃣ Memorizing Private Data
Example: AI like GPT-2 sometimes remembers and repeats real names, emails, or phone numbers from its training data.
✅ Problem:
Could leak personal info (like medical records, private conversations).
Violates privacy laws (GDPR, CCPA).
✅ Should AI be restricted?
✔ Yes – AI shouldn’t train on private data without consent.
❌ No – But then AI might become less accurate.
2️⃣ Generating Copyrighted Material
Example: AI can write new "Harry Potter" chapters or copy song lyrics.
✅ Problem:
Steals artists’ work without paying them.
Could lead to lawsuits (like Getty Images vs. Stable Diffusion).
✅ Should AI be restricted?
✔ Yes – AI shouldn’t copy books, music, or art without permission.
❌ No – But then creativity might be limited.
Final Answer: Should AI Training Be Restricted?
✔ Yes, but carefully.
Private data? → Remove it (protect privacy).
Copyrighted content? → Pay artists or use only permitted data.
Why?
Avoid legal trouble (fines, bans).
Keep AI ethical & fair for everyone.

6ANS)

Aequitas Bias Audit Tool Explained Simply
🔍 What is Aequitas?
A free tool that checks if an AI model is fair for different groups (e.g., men vs. women, races, ages).
📏 Example Metric: False Negative Rate Parity
1️⃣ What It Measures
False Negative Rate (FNR): % of times the AI wrongly says "NO" when the answer is "YES."
Example: A loan AI rejects qualified applicants.
Parity Check: Compares FNR between groups (e.g., "Is FNR the same for Black and White applicants?").
2️⃣ Why It’s Important
If one group has higher FNR, the AI is unfairly strict with them.
Example: A job-screening AI rejects more women than men with the same qualifications.
Could lead to discrimination (illegal & unethical).
3️⃣ How a Model Fails This Metric
Example Failure:
FNR for Black applicants = 20%
FNR for White applicants = 5%
➔ The AI is 4x more likely to wrongly reject Black applicants!
🔧 (Demo)
Go to Aequitas
Upload a dataset (or use their "COMPAS" demo data).
Select "False Negative Rate Parity" and pick groups (e.g., race).
See results: Red = unfair, Green = fair.
💡 Key Takeaway
Fair AI = Same error rates for all groups.
Unfair AI = Hurts certain people more.
Tools like Aequitas help fix bias before AI causes harm.
