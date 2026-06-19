# 🎬📺 Netflix Titles Analysis & Recommender

An exploratory data analysis and content-based recommendation system project built on Netflix's movie and TV show catalog, using Python, Pandas, Scikit-learn, and Jupyter Notebook.

## 📌 Project Overview

This project analyzes ~8,800 titles available on Netflix as of 2021, exploring catalog composition, content trends over time, genre and geographic distribution, and audience ratings. It then builds a content-based recommendation system that suggests similar titles based on genre, plot description, director, and cast.

The repository includes:
- Data cleaning (including a fix for a known column-shift bug in the raw data)
- Exploratory data analysis (EDA)
- Text analysis of titles and descriptions
- A TF-IDF + cosine-similarity content-based recommender
- Visualizations of all key findings

## 🚀 Features

- Catalog composition analysis (Movies vs. TV Shows)
- Content growth trends over time
- Genre and country distribution analysis
- Ratings and audience-type breakdown
- Word cloud and word-frequency analysis of titles/descriptions
- Content-based recommendation engine ("More Like This")
- Honest evaluation of recommender strengths and limitations

## 📂 Project Structure

```
Netflix_Titles_Analysis/
│
├── data/                              # Dataset files (CSV)
├── netflix_titles_analysis.ipynb      # Main analysis notebook
└── README.md
```

## 📊 Dataset

The project uses the Netflix Movies and TV Shows dataset, containing metadata for titles available on Netflix as of 2021.

**Dataset source:**
Kaggle Dataset: https://www.kaggle.com/datasets/shivamb/netflix-shows

**File used:**
- `netflix_titles.csv`

**Note:** The dataset should be downloaded manually from Kaggle and placed inside the `data/` directory before running the notebook.

## 🛠 Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- WordCloud
- Jupyter Notebook

## ⚙️ Installation

Clone the repository:
```bash
git clone https://github.com/<your-username>/Netflix_Titles_Analysis.git
cd Netflix_Titles_Analysis
```

Install dependencies:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn wordcloud jupyter
```

## ▶️ Usage

Launch the notebook:
```bash
jupyter notebook netflix_titles_analysis.ipynb
```

The notebook will:
- Load and clean the dataset, fixing known data quality issues
- Explore catalog trends, genres, countries, and ratings
- Generate word clouds and word-frequency charts from titles/descriptions
- Build a TF-IDF-based content similarity matrix
- Recommend similar titles for any given title in the dataset

## 🔍 Getting Recommendations

To get recommendations for a title already in the dataset, call the `recommend()` function defined in the notebook:
```python
recommend("The Conjuring")
```
Example output:
```
                title    type                    listed_in  release_year  similarity
0      The Conjuring 2   Movie    Horror Movies, Thrillers          2016       0.342
1            Insidious   Movie    Horror Movies, Thrillers          2010       0.298
2    In the Tall Grass   Movie    Horror Movies, Thrillers          2019       0.276
...
```

## 📈 Model Evaluation

The recommender is evaluated qualitatively by inspecting recommendations for known titles across genres. It performs well for genre-distinct content (e.g. horror, sci-fi) and is weaker for titles whose genre tags overlap broadly with many other titles (e.g. general crime dramas) — a known limitation of TF-IDF-based similarity, which matches surface vocabulary rather than deep plot semantics.

## 🧠 Model Architecture

The recommender uses:
- A combined text "soup" per title (genre tags + description + director + top cast members)
- TF-IDF vectorization (10,000 max features, English stopwords removed)
- Cosine similarity across the full catalog
- Top-N ranking to return the most similar titles to any input

This architecture requires no user behavior data, so it works immediately for new titles with no viewing history (no cold-start problem) — a practical advantage over collaborative filtering.

## 📷 Example Insights

| Analysis | Finding |
|---|---|
| Catalog mix | ~70% Movies, ~30% TV Shows |
| Growth | Catalog additions peaked around 2019, then slowed |
| Top genre | International Movies leads, followed by Dramas and Comedies |
| Top country | United States leads, India a strong second |
| Ratings | TV-MA and TV-14 dominate; family content is a minority |
| Title trends | "Christmas" is a notably recurring word, reflecting Netflix's holiday-content strategy |

## 🔮 Future Improvements

- Replace TF-IDF with transformer-based sentence embeddings for better semantic matching
- Hybrid recommender combining content-based and collaborative filtering
- Deeper NLP analysis of description sentiment and themes
- Deployment as a web application (Streamlit/Flask) with a search interface
- Genre/country gap analysis to inform content strategy

## 🤝 Contributing

Contributions are welcome.
- Fork the repository
- Create a new branch
- Make improvements
- Submit a pull request

## 📄 License

This project is intended for educational and research purposes.

## 👩‍💻 Author

**[Your Name]**
GitHub Repository: https://github.com/<your-username>/Netflix_Titles_Analysis
