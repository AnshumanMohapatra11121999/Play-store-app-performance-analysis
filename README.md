# Google Play Store App Optimization & Performance Analytics

This project analyzes Google Play Store app data to understand what factors are linked with app ratings, installs, reviews, pricing, and app size. The main goal was to identify practical patterns that can help app developers and platform teams understand app performance and make better product decisions.

## Project Overview

The Google Play Store contains many apps across different categories, making app discovery and quality evaluation difficult. In this analysis, I explored how app characteristics such as rating, reviews, installs, price, size, content rating, and genre relate to overall app performance.

The analysis focused on questions such as:

- What rating level can be treated as a quality benchmark?
- Do larger apps receive better ratings?
- How does pricing relate to user ratings?
- Which app size ranges appear safer from a rating-risk point of view?
- How do ratings vary across content rating groups and genres?
- How have app updates and average ratings changed over time?

## Dataset Information

- **Dataset source:** Public Google Drive CSV link used inside the notebook
- **Initial dataset size:** 10,841 records and 13 columns
- **Cleaned dataset size:** 9,359 records and 13 columns
- **Dataset scope:** Google Play Store mobile applications with app metadata, ratings, reviews, installs, pricing, category, genre, and update information

### Key Variables Used

- `App` - App name
- `Category` - Main app category
- `Rating` - Average user rating
- `Reviews` - Number of user reviews
- `Size` - App size in KB
- `Installs` - Number of installs
- `Type` - Free or Paid
- `Price` - App price in USD
- `Content Rating` - Target audience group
- `Genres` - App genre
- `Last Updated` - Last update date
- `Current Ver` - Current app version
- `Android Ver` - Minimum supported Android version

## Project Workflow

1. **Data Collection / Loading**
   - Loaded the Google Play Store dataset from a public Google Drive CSV URL.
   - Created a backup copy of the original dataframe before cleaning.

2. **Data Cleaning**
   - Removed rows with missing ratings.
   - Removed an invalid row where the rating value was greater than 5.
   - Filled missing `Android Ver` and `Current Ver` values using the mode.
   - Converted `Price`, `Reviews`, and `Installs` into numeric formats.
   - Removed rows where `Reviews` were greater than `Installs`.

3. **Exploratory Data Analysis**
   - Reviewed the distributions of app price, reviews, size, and ratings.
   - Checked rating thresholds and outliers.
   - Compared app size, price, reviews, and ratings.

4. **Visualization**
   - Created box plots, histograms, density plots, pair plots, bar charts, joint plots, and a heatmap.
   - Used visual analysis to study rating behavior across app size, price, content rating, genre, and update year.

5. **Findings and Insights**
   - Identified rating benchmarks, pricing outliers, size-related rating patterns, and audience-based rating risks.
   - Built a rating risk matrix using app size buckets and content rating groups.

6. **Recommendations**
   - Suggested practical app size, pricing, and quality threshold recommendations based on the observed patterns.

## Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook

## Key Findings

- The dataset initially contained 10,841 apps, and the cleaned dataset contained 9,359 apps.
- App ratings were mostly concentrated around higher values, with a median rating of 4.3.
- The 25th percentile rating was 4.0, making ratings below 4.0 a useful lower-performance signal.
- There were 15 apps priced above $100, mostly premium/status-style apps that could distort pricing analysis.
- The 99th percentile of reviews was 9,882,945, showing that review counts were highly skewed by very large apps.
- The median app size was around 20.51 MB, while the 90th percentile size was around 51.76 MB.
- Apps in the 10 MB to 40 MB range showed a strong concentration of higher ratings in the size-versus-rating analysis.
- Very large apps did not automatically receive higher ratings.
- Paid apps showed a mild negative relationship between price and rating after filtering extreme pricing outliers.
- Average app ratings showed an upward trend from 2011 to 2018 in the notebook’s time-based analysis.

## Business Insights

- A rating of 4.0 can be treated as a practical quality boundary because it represents the lower 25% threshold in the cleaned dataset.
- App size matters because users may react negatively when apps become too large without clear value.
- Very small apps can also show rating volatility, suggesting that limited functionality may affect user satisfaction.
- Higher pricing can increase user expectations, and paid apps may receive stricter reviews if the value is not clear.
- Review and install volume are highly uneven across apps, so raw popularity should not be treated as the only sign of quality.
- Content rating and app size together can help identify higher-risk segments where apps may receive lower ratings.

## Recommendations

- Use a rating threshold of 4.0 as a basic filter when identifying lower-performing apps.
- Avoid allowing extreme price outliers to influence general paid-app pricing analysis.
- For most apps, target a practical size range rather than assuming larger apps perform better.
- Keep paid app pricing realistic and clearly supported by strong user value.
- Monitor apps with very high size or weak rating performance more closely after launch.
- Use review-to-install behavior as an additional signal when evaluating early app traction.
- Consider content rating and app size together when identifying app quality risks.
