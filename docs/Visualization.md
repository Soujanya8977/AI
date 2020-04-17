# Visualization

## Explore the raw data

you can explore the data to determine how it can be used. This below functions provides methods for visualizing the data in useful ways

### explore_features(df):

It visualizes the relationships between all features in a given data frame. Areas of heat show closely-related features. This visualization is useful when trying to determine which features can be predicted and which features are needed to make the prediction.

Use explore_features to explore the correlations between features in the raw data. Use the visualization to form a hypothesis about how the raw data can be used. It may be necessary to enrich raw data with other features to increase the number and strength of correlations. If necessary, refine raw data and repeat this analysis.

### visualize_missing_data(df):

It creates a visual display of missing data in a data frame. Each column of the data frame is shown as a column in the graph. Missing data is represented as horizontal lines in each column. This visualization is useful when determining whether or not to impute missing values or for determining whether or not the data is complete enough for analysis.

Use visualize_missing_data to visualize missing fields in your raw data. Determine if imputing is necessary. Refine raw data, if necessary, and repeat this analysis.

### plot_distributions(df):

It creates a distribution graph for each column in a given data frame. Graphs for data types that cannot be plotted on a distribution graph without refinement (types like dates), will show as blank in the output. This visualization is useful for determining skew or bias in the source data.

Use plot_distributions to show the distributions for each feature in raw_data. Depending on raw data, this visualization may take several minutes to complete. Use the visualization to determine if there is a data skew that may prevent proper analysis or useful insight. If necessary, refine raw data and repeat this analysis.
