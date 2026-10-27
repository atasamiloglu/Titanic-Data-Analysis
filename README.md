# Titanic Data Analysis

Exploratory data analysis of the Titanic dataset (loaded from `seaborn`) using **pandas**, **matplotlib** and **seaborn**.
The goal is to practice data exploration, filtering, grouping and visualization, and to answer simple questions with data.

## Tools

- Python 3
- pandas
- matplotlib
- seaborn

```bash
pip install pandas matplotlib seaborn
```

```python
import seaborn as sns
df = sns.load_dataset("titanic")
```

## Dataset

891 passengers, with columns such as `survived`, `pclass`, `sex`, `age`, `fare`, `embarked`, `alone`.
Values in this version are lowercase (e.g. `"female"`, `"male"`).

## What was done

### 1. Data exploration
- Checked shape, data types and summary statistics (`info`, `describe`)
- Counted missing values per column (`isna().sum()`)
- Looked at mean, median and standard deviation of `age`

### 2. Filtering
- Women older than 25 and their passenger class distribution
- Children (under 12) and how many survived
- Survival rate of passengers traveling alone vs. with family

### 3. Groupby analysis
- Average age and fare by passenger class
- Survival rate by sex and passenger class

| Sex | Class | Survival rate | Passengers |
|---|---|---|---|
| female | 1 | 0.97 | 94 |
| female | 2 | 0.92 | 76 |
| female | 3 | 0.50 | 144 |
| male | 1 | 0.37 | 122 |
| male | 2 | 0.16 | 108 |
| male | 3 | 0.14 | 347 |

### 4. Visualizations
- Age distribution by sex (`displot`)
- Fare by passenger class (`boxplot`)
- Survival counts by sex (`countplot`)
- Age vs. fare, colored by survival and sex (`scatterplot`)

## Key findings

1. **Sex appears to be a stronger factor than class.** Women survived at higher rates than men in every class. Even 3rd class women (0.50) survived at a higher rate than 1st class men (0.37).
2. **Class still matters within each sex.** Survival drops from 1st to 3rd class for both women and men. The largest group, 3rd class men (347 passengers, about 39% of all passengers), also has the lowest survival rate (0.14), which pulls the overall survival rate down.
3. **Fare is tied to class, and higher fares were more common among survivors.** 1st class fares have a wide spread with many high outliers, so the mean fare is much higher than the median. Some 3rd class passengers paid more than the median 1st class fare, which may be explained by group tickets (the `fare` value can cover more than one person).

## Notes and limitations

- The `age` column has missing values. Statistics and plots that use `age` only include passengers with a known age.
- All findings show **relationships, not causes**. For example, fare likely reflects passenger class rather than having an effect on its own.
- Survival rates should be read together with group sizes (`count`), since small groups give less reliable rates.

## Project structure

```
titanic/
├── titanic_analysis.ipynb   # analysis notebook with interpretation comments
└── README.md
```
