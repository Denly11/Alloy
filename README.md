# Alloy
Remaking logic of my project "Kalorické tabulky" into programming language Alloy as a part of Matfyz Summer of Code.

## What the model covers
- users and foods stored in a database
- nutritional values of foods (calories, protein, carbohydrates, fats)
- logging and removing foods over time (behavioral modeling)
- total calories per user
- verification of the model using `run` and `check` commands

## Limitations and future work

The model is a simplified formal description of the core logic of *Kalorické tabulky*, not a complete specification of the whole application.

### Limitations

- **Bounded analysis.** Alloy only searches for instances within a finite scope. The `run` and `check` commands use small scopes (for example 3 users, 3 foods and a 9-bit `Int`). If a `check` finds no counterexample, this means none exists within that scope, not that the property is proven for all sizes.
- **Limited integer range.** Integers are bounded, so very large calorie values or sums can overflow. Raising the `Int` bitwidth helps, but only up to a point.
- **Simplified domain.** The model covers users, foods, their nutritional values, and logging and removing foods over time. It does not model portions or amounts, dates, meals, or creating and editing foods.
- **Calories as a plain sum.** The model defines calories as `protein + carbohydrates + fats`. It does not convert grams to kilocalories, so the values are assumed to already be expressed in kcal.
- **One log entry per food.** `log_food` requires that the food is not yet in `logged_food_in_database`, so a food from the database can be logged by only one user at a time.
- **Partly outdated screenshots.** Some screenshots in the notes show earlier versions of the model with Czech names (and a typo, `totat_calories`).

### Future work

- Split fats into saturated and unsaturated fatty acids. I considered this, but it would require modeling how the two relate to total fats, so I left it out.
- Allow the same food to be logged by several users, or several times by one user.
- Add portions and dates to the logging model.
- Check the assertions with larger scopes.

## How to run
1. Download [Alloy 6](https://alloytools.org/download.html) (temporal operators require version 6 or newer).
2. Open `<your-model-file>.als` in Alloy Analyzer./Open Alloy Analyzer and copy paste the code from this repo.
3. Run a command from the *Execute* menu (see the table below).

## Documentation
My notes from this project: first the theory behind Alloy, then a practical log of how I used it, the problems I ran into, and how I solved them.
- [Theory notes](docs/theory.md)
- [Practical notes](docs/practical.md)

> **Note:** The notes are written in English, but some screenshots show earlier versions of the model with Czech names.

> [!NOTE]
> The notes are written in English, but some screenshots show earlier versions of the model with Czech names.

# Acknowledgements
I would like to thank the Matfyz Summer of Code organizers, the D3S team at Charles University, and the program's supporters, including the RSJ Foundation, for giving me the opportunity to work on this project and gain valuable experience. I am also grateful to my project supervisor for their guidance, feedback, and support throughout the summer.
Thank you
