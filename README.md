# Trending YouTube Analysis – Foundations of Computer Science Project

A series of Python exercises on the **Trending YouTube** dataset, designed to build familiarity with the language and with data manipulation using **pandas** and **NumPy**. The whole project is a single Jupyter notebook.

> Final project for the **Foundations of Computer Science** course (2025–26), University of Milano-Bicocca.
> Author: Chiara Mezzanzanica

📓 **Notebook:** [`Final_Project_FOCS.ipynb`](./Final_Project_FOCS.ipynb)

---

## Dataset

The notebook works on the Trending YouTube dataset, which contains the daily trending videos for **10 countries**: Canada (CA), Germany (DE), France (FR), Great Britain (GB), India (IN), Japan (JP), South Korea (KR), Mexico (MX), Russia (RU) and the United States (US).

For each country there are two files:

| File | Content |
|------|---------|
| `<CC>videos.csv.zst` | Trending videos (title, channel, tags, views, likes, dislikes, publish time, trending date, flags for disabled comments/ratings, …), compressed with Zstandard |
| `<CC>_category_id.json` | Mapping between category IDs and category names for that country |

> The data files are **not included** in this repository. They were provided with the course material and must be downloaded separately.

## Exercises

| # | Task |
|---|------|
| 1 | Build a single dataframe by concatenating all country files, adding a `country` column; remove duplicate rows and inspect missing values |
| 2 | Extract all videos with no tags |
| 3 | Compute the total number of views for each channel |
| 4 | Move videos with disabled comments *and* ratings, or flagged as errored/removed, into a separate `excluded` dataframe and remove them from the main one |
| 5 | Add a `like_ratio` column. Likes/dislikes produces `inf` and `NaN` values when counts are zero, so the ratio is normalised as likes / (likes + dislikes) |
| 6 | Cluster the publish time into 10-minute intervals |
| 7 | For each interval, compute the number of videos and the average likes and dislikes |
| 8 | Count the number of videos for each tag (tags are stored as a single `\|`-separated string) |
| 9 | Find the tags with the largest number of videos |
| 10 | For each (tag, country) pair, compute the average like ratio |
| 11 | For each (trending date, country) pair, find the video with the most views |
| 12 | Split the trending date into year, month and day columns |
| 13 | For each (month, country) pair, find the video with the most views |
| 14 | Read all the JSON files with the video categories |
| 15 | For each country, count how many videos have a category that is not assignable (merging videos with category metadata) |

## Techniques covered

- Reading compressed (`.zst`) files and JSON files into pandas
- Concatenating and merging dataframes (`concat`, `merge`)
- Handling duplicates, missing values and division-by-zero cases
- Grouping and aggregation (`groupby`, `agg`, `idxmax`)
- String processing and `explode` for multi-valued columns
- Date and time manipulation (`to_datetime`, `dt.floor`, `Timedelta`)
- Working with dictionaries, loops and lambda functions

## How to run

1. Clone the repository:
   ```bash
   git clone https://github.com/mezza04/Foundation-of-Computer-Science-Project.git
   cd Foundation-of-Computer-Science-Project
   ```
2. Install the dependencies:
   ```bash
   pip install pandas numpy zstandard jupyter
   ```
3. Place the dataset files in a local folder and **update the two paths in the notebook** (the cells that read the `.csv.zst` and `.json` files) so that they point to that folder. In the current version they point to a local Windows folder.
4. Open `Final_Project_FOCS.ipynb` in Jupyter and run all cells from top to bottom.

## Notes

- Code comments and some variable names are in a mix of English and Italian.
- Per the course rules, AI tools may be used provided their use is described in the notebook.

## Tools

Python · pandas · NumPy · zstandard · Jupyter Notebook
