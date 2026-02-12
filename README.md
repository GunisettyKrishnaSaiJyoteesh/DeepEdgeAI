📍 Pixel Coordinate Prediction using Deep Learning (CNN Regression)
📖 Project Overview

This project solves a simple yet insightful supervised learning problem:

Given a 50×50 grayscale image where exactly one pixel has intensity 255 and all other pixels are 0, predict the (x, y) coordinates of that pixel using Deep Learning.

Although the dataset is synthetic and minimal, this task demonstrates:

Regression using neural networks

Handling spatial data with CNNs

Understanding optimization challenges

Avoiding mean-prediction traps in MSE regression

The goal was not just accuracy, but building a conceptually correct and stable learning pipeline.

🧠 Problem Formulation

Input: 50×50 grayscale image

Output: Continuous coordinate values (x, y)

Learning Type: Supervised Regression

Loss Function: Mean Squared Error (MSE)

Evaluation Metric: Mean Absolute Error (MAE)

Since the target values are continuous, this is formulated as a regression problem rather than classification.

🏗 Model Architecture

A Convolutional Neural Network (CNN) was used to preserve spatial structure.

Architecture Summary:

Conv2D (16 filters, 3×3, ReLU)

MaxPooling

Conv2D (32 filters, 3×3, ReLU)

MaxPooling

Flatten

Dense (128, ReLU)

Dense (2, Linear activation)

Why CNN?

Because the task depends entirely on spatial location.
Fully connected layers alone would struggle to preserve positional information.

⚠️ Important Learning Insight

During early experiments, the model predicted the average coordinate (~25, 25) for all images.

This happened because:

The dataset is uniformly distributed.

MSE loss encourages mean prediction when gradients are weak.

The input is extremely sparse (only 1 active pixel).

To resolve this:

Pixel intensity was kept at 255 (as specified).

Labels were not normalized.

CNN architecture was used to strengthen spatial feature extraction.

This allowed the model to escape the mean-prediction local minimum.

📊 Training Behavior

The model showed:

Rapid decrease in training loss

Strong validation performance

Sub-pixel prediction accuracy

Slight late-stage overfitting (handled via EarlyStopping)

Final validation MAE was typically below 1 pixel, indicating highly accurate coordinate prediction.

📦 Installation

Clone the repository:

git clone <your-repo-link>
cd <repo-name>


Install dependencies:

pip install numpy matplotlib tensorflow scikit-learn

🚀 How to Run

Simply execute the notebook or Python script:

python pixel_regression.py


The script will:

Generate synthetic dataset

Train the CNN model

Display training curves

Evaluate performance

Visualize predictions

📈 Example Output

The model predicts coordinates very close to the ground truth:

True: (17, 42)
Pred: (17, 41)

True: (3, 8)
Pred: (3, 8)


Average prediction error: < 1 pixel

🎯 Key Takeaways

Regression with MSE can converge to mean prediction in uniform datasets.

CNNs are powerful for spatial regression tasks.

Gradient strength matters in sparse input problems.

Proper problem formulation is as important as model complexity.

This project highlights both practical implementation and theoretical understanding.

📂 Repository Structure
├── pixel_regression.ipynb
├── pixel_regression.py
├── README.md
└── requirements.txt

👨‍💻 Author

Gunisetty Krishna Sai Jyoteesh
Final Year Graduate | Data Science Enthusiast
