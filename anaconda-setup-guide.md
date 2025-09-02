# Anaconda Virtual Environment Setup Guide
# For Hands-On Machine Learning Book Exercises

## Prerequisites
- Anaconda or Miniconda installed on your system
- Anaconda Prompt available (comes with Anaconda installation)

## Step-by-Step Instructions

### Step 1: Open Anaconda Prompt
1. Press `Windows + R` to open Run dialog
2. Type `anaconda prompt` and press Enter
3. Or search for "Anaconda Prompt" in Windows Start menu
4. Click on "Anaconda Prompt (anaconda3)" or similar

### Step 2: Navigate to Your Project Directory
```bash
# Navigate to your project folder
cd C:\Users\sherr\OneDrive\Desktop\HandsOnMachineLearningBookExercises

# Verify you're in the correct directory
dir
# You should see: ch2.ipynb, ch3.ipynb, housing.csv, requirements.txt, etc.
```

### Step 3: Create a New Conda Environment
```bash
# Create a new environment named 'ml_book' with Python 3.9
conda create -n ml_book python=3.9

# When prompted, type 'y' and press Enter to proceed
```

### Step 4: Activate the Environment
```bash
# Activate the newly created environment
conda activate ml_book

# You should see (ml_book) at the beginning of your prompt
# Example: (ml_book) C:\Users\sherr\OneDrive\Desktop\HandsOnMachineLearningBookExercises>
```

### Step 5: Install Required Packages
```bash
# Option 1: Install from requirements file (recommended)
pip install -r requirements-detailed.txt

# Option 2: Install packages individually
conda install numpy pandas scipy matplotlib seaborn jupyter
conda install -c conda-forge scikit-learn folium

# Option 3: Install minimal requirements
pip install -r requirements-minimal.txt
```

### Step 6: Verify Installation
```bash
# Check installed packages
conda list

# Or check specific packages
python -c "import numpy, pandas, sklearn, matplotlib, seaborn, folium; print('All packages installed successfully!')"
```

### Step 7: Launch Jupyter Notebook
```bash
# Launch Jupyter Notebook
jupyter notebook

# This will open Jupyter in your default web browser
# Navigate to your notebook files (ch2.ipynb, ch3.ipynb)
```

## Alternative: Using conda-forge for Better Package Compatibility

If you encounter any issues with the standard installation, try using conda-forge:

```bash
# Add conda-forge channel
conda config --add channels conda-forge
conda config --set channel_priority strict

# Create environment with conda-forge packages
conda create -n ml_book python=3.9
conda activate ml_book

# Install packages from conda-forge
conda install -c conda-forge numpy pandas scipy matplotlib seaborn jupyter scikit-learn folium
```

## Environment Management Commands

### Useful Commands for Managing Your Environment:

```bash
# List all environments
conda env list

# Activate environment
conda activate ml_book

# Deactivate environment
conda deactivate

# Remove environment (if needed)
conda env remove -n ml_book

# Export environment to file
conda env export > environment.yml

# Create environment from file
conda env create -f environment.yml
```

## Troubleshooting

### Common Issues and Solutions:

1. **Package not found error:**
   ```bash
   # Try installing from conda-forge
   conda install -c conda-forge package_name
   
   # Or use pip as fallback
   pip install package_name
   ```

2. **Version conflicts:**
   ```bash
   # Update conda
   conda update conda
   
   # Clean conda cache
   conda clean --all
   ```

3. **Jupyter kernel not found:**
   ```bash
   # Install ipykernel in your environment
   conda install ipykernel
   
   # Register the kernel
   python -m ipykernel install --user --name ml_book --display-name "Python (ml_book)"
   ```

4. **Permission errors:**
   - Run Anaconda Prompt as Administrator
   - Or use `--user` flag with pip: `pip install --user package_name`

## Next Steps

1. **Open your notebooks:**
   - In Jupyter, navigate to your project folder
   - Open `ch2.ipynb` or `ch3.ipynb`

2. **Select the correct kernel:**
   - In Jupyter, go to Kernel → Change kernel
   - Select "Python (ml_book)" or your environment name

3. **Test your setup:**
   - Run the first few cells in your notebook
   - Check that all imports work without errors

## Environment File (environment.yml)

You can also create an `environment.yml` file for easier environment recreation:

```yaml
name: ml_book
channels:
  - conda-forge
  - defaults
dependencies:
  - python=3.9
  - numpy=1.24.3
  - pandas=2.0.3
  - scipy=1.11.1
  - scikit-learn=1.3.0
  - matplotlib=3.7.2
  - seaborn=0.12.2
  - jupyter=1.0.0
  - folium=0.14.0
  - pip
  - pip:
    - ipykernel==6.25.0
    - notebook==7.0.2
```

Then create the environment with:
```bash
conda env create -f environment.yml
```

## Summary

After following these steps, you'll have:
- ✅ A dedicated virtual environment for your ML projects
- ✅ All required packages installed
- ✅ Jupyter Notebook ready to use
- ✅ Isolated environment that won't interfere with other projects

Your environment is now ready for the Hands-On Machine Learning book exercises!
