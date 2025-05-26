# Sustainameal-2.0 -  HeASe
Esame Semantics 24/25 - Beatrice Scavo, Federico Valentino


## Introduction

`HeASe` is a Python library designed to suggest alternative recipes for healthier or more sustainable options. Leveraging machine learning and natural language processing, it compares nutritional profiles and semantic similarities to provide recipe recommendations.

> ⚠️ **Important note**: This work is entirely based on the original repository [HeASe](https://github.com/swapUniba/HeASe).  
All components of the project remain **unchanged**, **except for the dataset**, **the quantitative**, **the qualitative tests**, and **the `sustainameal` package**.
Regarding the quantitative evaluation, the original files were not uploaded—instead, only the final results are included in the documentation. This choice was made because the goal was not to assess a specific case in detail, but rather to evaluate the general behavior of the system and verify whether it retained the same characteristics as in the previous results. In any case, the same evaluation process as the original was followed, but with different data.
---

## Runtime Environment

This project was developed and tested in the **Kaggle** environment.  
If you plan to run it elsewhere, please make sure to **adjust the dependencies accordingly** to match your system.

---

## Quick Start Test

To perform a quick test of the system’s functionality, you can run the notebook `test.ipynb`.  

### Initialization
-   Upload 'test.ipynb' on kaggle
-   Add as input the [Embeddings](https://www.kaggle.com/datasets/federicores/embeddings), [Recipes Dataset](https://www.kaggle.com/datasets/federicores/final-dataset) and the [Sustainameal Package](https://www.kaggle.com/datasets/federicores/final-sustainameal-package)
-   run 'test.ipynb'

Make sure to **adapt the package dependencies** to your execution environment if not using Kaggle.

---

## Resources

- 📦 **Download embeddings**: [Kaggle Dataset](https://www.kaggle.com/datasets/federicores/embeddings/data)  
- 📂 **Download dataset, documentation and presentation**: [Google Drive Folder](https://drive.google.com/drive/folders/1rm91lFhhEDkcmFJW0ZDaOYh0C1-wIWMP?usp=drive_link)

---

## Architecture

The library consists of several modules:

- **Data Preprocessing**: Removes unnecessary recipe data.
- **Transformer Embeddings**: Generates text embeddings for recipe titles using a transformer model.
- **Nutritional Vector Space**: Maps recipes into a vector space based on nutritional content.
- **Similarity Search**: Performs cosine similarity searches to find matching recipes.
- **Sort Results**: Sorts recipes based on healthiness or sustainability metrics.

---


## Usage

### Initialization

```python

sm = SustainaMeal(
    recipes_df='your dataset',
    load=False,
    nutrients=['calories', 'fat', 'protein', ...],
    transformer_name='your_transformer_model'
)
```

Default transformer: [`davanstrien/autotrain-recipes-2451975973`](https://huggingface.co/davanstrien/autotrain-recipes-2451975973)

---

### Find Similar Recipes

```python
similar_recipes = sm.find_similar_recipes(
    input_text='Creamy Lemon Asparagus Risotto',
    k=10,
    acceptable_tags=['appetizers', 'main-dish', 'side-dishes', 'fruits', 'desserts',
                     'breakfast', 'pasta-rice-and-grains', 'beverages', 'drinks'],
    match_all_tags=True
)
```

---

### Order by Healthiness

```python
healthier_recipes = sm.order_recipe_by_healthiness(score="who_score")
```

---

### Order by Sustainability

```python
order_by_sus_recipes = sm.order_recipe_by_sustainability(score='sustainability_label')
```

---

### Order by HeASe Score

```python
order_by_sus_recipes = sm.order_recipe_by_HeASe()
```

---
