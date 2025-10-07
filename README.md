Brody Kretz

Goal:
This project predicts a player’s rating group (Beginner, Intermediate, Advanced, or Expert) using data from real chess matches. The model uses features such as game length, time control, opening name, and victory status to understand how these factors relate to player skill.
Dataset: ~20,000 online chess matches
Key columns include:
white_rating and black_rating – player skill ratings
turns – number of moves per game
opening_name – chess opening used
base_time – main time control in seconds
victory_status – how the game ended (resign, mate, draw, timeout)


Data Summary Table

Sample Statistics:
Average white rating: 1596.6
Average black rating: 1588.8
Average game length: 60.5 turns
Most common openings: Van’t Kruijs, Sicilian Defense, Bowdler Attack
Most common victory type: resignation


Steps Taken:
Standardized column names and removed missing data.
Filtered out unrealistic matches (under 5 or over 200 turns).
Converted timestamp columns to readable datetime format.
Calculated new features: - rating_diff = white rating − black rating
Binned player ratings into 4 rating groups:
Beginner (0–1200)
Intermediate (1200–1600)
Advanced (1600–2000)
Expert (2000+)
Distribution of Player Rating Groups

Observation:
Most players fall into the Intermediate and Advanced ranges, while Beginners and Experts represent smaller portions of the dataset.



Game Length by Skill Group

Advanced and Expert players tend to play slightly longer games on average, with fewer quick losses or short matches compared to Beginners.
Time Control by Skill Group

Time settings were fairly similar across all skill levels, suggesting that time control does not heavily influence player rating.

Goal:
Train a model to predict the player’s rating group from game characteristics.
Train/Test Split: 80/20 ratio, stratified by class


Confusion Matrix
 Interpretation:
The model performs best at identifying Intermediate and Advanced players.
Beginners are harder to classify accurately due to fewer examples.
Accuracy of ~58% is solid given overlapping behaviors and class imbalance.


Top Feature Influence Table
 
Interpretation Notes:
Coefficients represent logistic regression weights, not percentages.
Positive values → increase likelihood of that rating group.
Negative values → decrease likelihood.
Larger absolute values = stronger influence.
Example Insights:
Certain openings (e.g., Sicilian Defense, Ruy Lopez) are strong indicators of Advanced or Expert players.
Longer matches and balanced rating differences correlate with higher skill levels.
Victory by checkmate tends to occur more in lower-rated games, while higher-rated players win by resignation more often.


Findings:
Player openings and game length are key predictors of skill.
The logistic regression model reached ~58% accuracy, showing reasonable predictive power.
Model struggles most with smaller classes (Beginners and Experts).


