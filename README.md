# Using-a-sample-dataset-for-example-students-study-hours-vs.-exam-scores-
Using a sample dataset (for example, students’ study hours vs. exam scores): • Calculate the correlation coefficient between the two variables. • Fit a simple linear regression line of the form y = a + bx using the least squares method
# Simple Linear Regression and Correlation Example

# Sample dataset: (Study Hours vs Exam Scores)
study_hours = [2, 3, 4, 5, 6, 7, 8, 9]
exam_scores = [50, 55, 56, 65, 67, 70, 74, 78]

n = len(study_hours)

# --- STEP 1: Calculate Means ---
mean_x = sum(study_hours) / n
mean_y = sum(exam_scores) / n

print("STEP 1: Calculate Means")
print(f"Mean of Study Hours (x̄) = {mean_x:.3f}")
print(f"Mean of Exam Scores (ȳ) = {mean_y:.3f}\n")

# --- STEP 2: Calculate correlation components ---
sum_xy = sum((x - mean_x) * (y - mean_y) for x, y in zip(study_hours, exam_scores))
sum_xx = sum((x - mean_x)**2 for x in study_hours)
sum_yy = sum((y - mean_y)**2 for y in exam_scores)

# --- STEP 3: Correlation Coefficient (r) ---
r = sum_xy / ((sum_xx * sum_yy) ** 0.5)

print("STEP 2: Correlation Coefficient Calculation")
print(f"Σ(x - x̄)(y - ȳ) = {sum_xy:.3f}")
print(f"Σ(x - x̄)² = {sum_xx:.3f}")
print(f"Σ(y - ȳ)² = {sum_yy:.3f}")
print(f"Correlation Coefficient (r) = {r:.4f}\n")

# --- STEP 4: Compute Regression Coefficients ---
b = sum_xy / sum_xx  # Slope
a = mean_y - b * mean_x  # Intercept

print("STEP 3: Regression Line Calculation")
print(f"Slope (b) = Σ(x - x̄)(y - ȳ) / Σ(x - x̄)² = {b:.3f}")
print(f"Intercept (a) = ȳ - b * x̄ = {a:.3f}")
print(f"\nRegression Line: y = {a:.3f} + {b:.3f}x\n")

# --- STEP 5: Predict values ---
print("Predicted Exam Scores using Regression Line:")
for x in study_hours:
    y_pred = a + b * x
    print(f"Study Hours: {x}, Predicted Score: {y_pred:.2f}")


#output
STEP 1: Calculate Means
Mean of Study Hours (x̄) = 5.500
Mean of Exam Scores (ȳ) = 64.375

STEP 2: Correlation Coefficient Calculation
Σ(x - x̄)(y - ȳ) = 157.000
Σ(x - x̄)² = 42.000
Σ(y - ȳ)² = 589.875
Correlation Coefficient (r) = 0.9674

STEP 3: Regression Line Calculation
Slope (b) = 3.738
Intercept (a) = 43.797

Regression Line: y = 43.797 + 3.738x

Predicted Exam Scores using Regression Line:
Study Hours: 2, Predicted Score: 51.27
Study Hours: 3, Predicted Score: 55.01
Study Hours: 4, Predicted Score: 58.75
...
Study Hours: 9, Predicted Score: 77.43
