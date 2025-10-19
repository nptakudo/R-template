# Installation Instructions for R-template in RStudio

This guide will walk you through installing and setting up this R project template in RStudio from scratch.

## Prerequisites

Before you begin, ensure you have the following installed:

1. **R** (version 4.5.1 or higher recommended)
   - Download from: https://cran.r-project.org/

2. **RStudio Desktop**
   - Download from: https://posit.co/download/rstudio-desktop/

## Installation Steps

### Step 1: Clone or Download the Repository

**Option A: Using Git (Recommended)**
1. Open Terminal (Mac) or Command Prompt (Windows)
2. Navigate to where you want to store the project:
   ```
   # cd ~/Documents
   ```
3. Clone the repository:
   ```
   git clone https://github.com/nptakudo/R-template.git
   cd R-template
   ```
4. Check out to midterm branch:
   ```
   git checkout -b my-local-branch
   ```

### Step 2: Open the Project in RStudio

1. Launch RStudio
2. Click `File` → `Open Project...`
3. Navigate to the `R-template/midterm` folder and click `Open`
4. Select the `day1.Rproj` file and click `Open` (if needed)

### Step 3: Initialize renv (Package Management)
Follow the `Init.md` instructionsto set up the package environment

### Step 3.1 - Skip: Initialize renv (Package Management) in console

This project uses `renv` for dependency management, which creates an isolated package environment.

Install RENV in the R console if you haven't already:
```r
install.packages("renv")
```

1. When you open the project, RStudio should automatically detect the `renv` configuration
2. You may see a message in the console about renv. If prompted, allow renv to activate
3. If not automatically activated, run in the R console:
   ```r
   renv::restore()
   ```
4. This will install all required packages specified in `renv.lock`
5. Type `y` when prompted to confirm the installation

**Note:** The first time you run `renv::restore()`, it may take several minutes to download and install all packages.

### Step 4: Verify Installation

1. Check that renv is active by running:
   ```r
   renv::status()
   ```
   You should see a message indicating the project is synchronized

2. Try loading the example file:
   - Navigate to `w2_class/wine_class.Rmd` in the Files pane
   - Click to open it
   - Try knitting the document (click the `Knit` button)

2.1. Better to install the packages used in the example file to avoid errors:
```r
install.packages(c("dplyr", "ggplot2", "readr", "tidyr"))
## or in console:
# renv::install(c("dplyr", "ggplot2", "readr", "tidyr"))
```
3. Sync to ensure all packages are up to date:
```r
renv::snapshot()
```

## Troubleshooting

### renv Not Activating Automatically

If renv doesn't activate when you open the project:
```r
source("renv/activate.R")
renv::restore()
```

### Package Installation Errors

If you encounter errors during package installation:
1. Ensure you have an active internet connection
2. On Mac, you may need Xcode Command Line Tools:
   ```
   xcode-select --install
   ```
3. On Windows, you may need Rtools:
   - Download from: https://cran.r-project.org/bin/windows/Rtools/

### R Version Mismatch

This project was created with R 4.5.1. If you have a different version:
- Minor version differences (e.g., 4.5.0 vs 4.5.1) should work fine
- Major version differences may cause issues with some packages
- Consider updating R if you're on an older version

### Cannot Find .Rproj File

Make sure you're looking in the `midterm` folder, not the root `R-template` folder.

## Using This Template for Exams

This is a local template designed for exam use. To use it:

1. Open the project in RStudio (follow steps above)
2. Create a new folder for your exam work or use the existing structure
3. Create new R scripts or R Markdown files as needed
4. All packages installed via renv will be available in this isolated environment
5. Your work will be saved within this project directory

## Additional Resources

- **renv documentation**: https://rstudio.github.io/renv/
- **RStudio cheat sheets**: https://posit.co/resources/cheatsheets/
- **R Markdown guide**: https://rmarkdown.rstudio.com/

## Notes

- This project uses `renv` to ensure reproducibility and package isolation
- The `.Rprofile` file automatically activates renv when the project opens
- All installed packages are project-specific and won't affect your global R library
- The `renv.lock` file tracks exact package versions for reproducibility

---

**Questions or Issues?**

If you encounter problems not covered in this guide, check:
1. That you have the correct R and RStudio versions installed
2. That you opened the `.Rproj` file (not just the folder)
3. That you have a stable internet connection for package downloads
