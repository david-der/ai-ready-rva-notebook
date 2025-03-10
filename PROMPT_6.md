For the non-data scientists in the crowd, I'd like an ELI5 for Accuracy, F1 and AUROC

----------
Here's a simple explanation of these metrics for non-data scientists:

### Accuracy - "How often is the model right?"

Imagine you have a weather app that predicts either "rain" or "no rain" for 10 days.
- If it correctly predicts the weather for 8 out of 10 days, its accuracy is 80%
- It's simply the percentage of times the model gets the right answer

**Real-world example:** If we predict 100 customers won't default and 78 actually don't default, our accuracy is 78%.

### F1 Score - "Balance between finding defaulters and avoiding false alarms"

Imagine you're a fire alarm:
- You want to detect all real fires (catch all defaulters)
- But you don't want to go off when there's no fire (avoid false alarms)

The F1 score measures how well you balance these two goals. A perfect score is 1 (100%), and a terrible score is 0.

**Real-world example:** A high F1 score means your model is good at identifying actual defaulters without incorrectly flagging good customers.

### AUROC (Area Under ROC Curve) - "How well can the model rank customers by risk?"

Imagine you have 10 customers, 5 who will default and 5 who won't:
- A perfect model would rank all the future defaulters higher than non-defaulters
- A random guess model would rank them randomly

AUROC measures this ranking ability:
- 0.5 = No better than random guessing (like flipping a coin)
- 1.0 = Perfect ranking (all defaulters ranked higher than non-defaulters)
- 0.7+ = Generally considered good discrimination

**Real-world example:** With an AUROC of 0.78, our Random Forest model has a 78% chance of ranking a random defaulter higher than a random non-defaulter. This is particularly useful if you want to prioritize which customers to monitor closely.

### What This Means For Your Credit Default Models:

- **Random Forest:** Best at all metrics - correctly identifies ~78% of cases, balances catching defaulters with avoiding false alarms well, and ranks customers by risk effectively.

- **Simple Rule:** Surprisingly accurate (~78%) for how simple it is, but isn't as good at ranking customers by risk level.

- **Logistic Regression:** Falls in the middle for ranking ability but has lower accuracy in this case.

The choice between these models depends on whether you care more about overall accuracy, balanced predictions, or ranking customers by risk level.