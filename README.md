# pca_and_projection
Python-based pipeline for Principal Components Analysis (PCA) and projecting between datasets. 

## Prerequisite 
First thing to do is to ensure you have 1) forked this repository, and then 2) cloned the forked repository.

Forking creates your very own remote version of this repository, while cloning creates a local version of that repository on your computer. If unsure, please google 'how to clone github repository'. 

## Set-up your environment
First, you'll need to set up an environment. This can be done using the terminal/command-prompt. 
We will be using the language Bash. This is the default language in a terminal shell for both Mac and Linux. To use on Windows, use the Ubuntu app (if this is confusing, google 'how to use Bash on windows').

In your terminal, enter the following commands (line-by-line):
```
cd path/to/repo #change directory to the local version of this repository 
virtualenv env -p python3 #create virtual environment using python 3
source env/bin/activate #activate this virtual environment
pip list #list the packages installed in this virtual env
pip install -r requirements.txt #install packages in this text file 
pip list #see how there's now more?
pip install . #this uses setup.py to install our package 'pca_and_projection'
```

## Repository structure 

### `pca_and_projection/`
- In here are the necessary functions that make up the package 'pca_and_projection'. 
- These are called by scripts in bin/ when you 'import pca_and_projection' in your scripts. 
- No need to edit anything in here - unless, of course, you want to contribute a function. In which case, submit a Pull Request. 

### `bin/`
- Bin = binary, which is kind of synonymous with 'executable' i.e. an executable script.
- Here is where you will store scripts that call functions in pca_and_projection to perform the analysis. 
- Please save a copy of the '...example.py' script from the main branch into your own analysis-specific branch and edit accordingly for your own analysis.

### `scratch/`
- This is a place to keep stuff you're not too precious about
- It has a `data/` directory, in which you can store the raw data you want PCA to be performed on and save out datasets with PCA scores. 
- It also has a `results/` directory where, you guessed it, your results (e.g., figures) will go (as outputted by the script in `bin/`)

- TODO: tree figure 

---

## How to run the PCA analysis (using `bin/...example.py`)

#### Aim: 1) To caluculate per-observation PCA for each componant of each PCA across different group splits 2) To produce screeplots, cumulative variance plots, heatmaps and wordclouds for each.

_Open the example.py script in bin/, and save a copy. Edit this copy only. Keep the example.py script for reference._
_This example script is specific to a particular dataset so variables will need editing_
_ Note: Not every line in the example.py script is needed to run this analysis - If your data has no group/condition splits, for example, you can ignore some of the script_ 

1. Change the variables at the top of the script to suit your needs 
- How many components do you want extracted? Do you have separate groups? Separate conditions?
2. Input your dataframe (.csv, .tsv)
   - Data should be structured so that there is one row per observation
3. Create new column for condition (Optional)
4. Create observation ID (unique to every row)
5. Select what columns contain thought data 
   - Z scoring, and subsequent PCA is only applied to these.
6. Z-score data in these columns
   - Can be applied to whole dataframe, or split by condition/sample/subject (set this in step one, Optional).
7. Input labels for figures
8. Select groups for applying PCA and create separate dataframes for each split (Optional)
   - These are stored in a dictionary 
9. Calculate naive PCA 
   - This inital step results in as many components as there are thought columns.
10. Data extraction & rotation
    - Nothing needs editing here - all parameters should have already been set at the top of the script in step 1.
11. Append factor scores back onto the original dataframe (No editing necessary)
    - Now, added to your dataframe, you will have one PCA score per component per row. 
12. Save out dataframe and associated results 
    - In scratch/ you should have 1) word clouds 2) loadings of each thought item on each component (if `savefile==True` in `wordclouder` function) 3) a PDF summary and 4) a new version of your original dataframe with PCA scores appended 





