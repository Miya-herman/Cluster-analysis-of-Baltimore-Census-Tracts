# Cluster-analysis-of-Baltimore-Census-Tracts

How are commuting zones or census tracts in Baltimore grouped based on different population metrics?
% black
% white
kfr
working

A brief description of your findings and background data with at least one data visualization
An outline of your business question → data question → data answer → business answer process and findings
Website links to your data sources and Excel files in your repository
Simple step-by-step descriptions on how you manipulated the Excel data (you may also upload this as a separate document in the repository)

Step-by-step Analysis:

1) filter 'czname' column and select only Baltimore
2) copy 'tract', 'kfr_pooled_pooled_p25', 'jail_pooled_pooled_p25', 'black_pooled_count', and 'white_pooled_count' columns into a new sheet
3) add an anchor column before the 'tract' column and number it 1-666
4) calculate the mean and standard deviation for columns: 'tract', 'kfr_pooled_pooled_p25', 'jail_pooled_pooled_p25', 'black_pooled_count', and 'white_pooled_count'
5) calculate z scores for each of these columns using =STANDARDIZE(x,mean,standard deviation). Drag down to calculate for each row.
6) Set up a separate table with the columns: 'tract number', 'anchor, 'kfr_pooled_pooled_p25', 'jail_pooled_pooled_p25', 'black_pooled_count', and 'white_pooled_count'. Above the last 4 columns, list the column index number.
7) Choose 4 random values for the 'anchor' column
8) For the values in the 'tract number' column, use =VLOOKUP to input the corresponding tract number to the value in the 'anchor' column
9) Use =VLOOKUP to input the z score values for each data column given the value in the 'anchor' column. 
10) calculate the distance squared from the first tract to the first anchor using =SUMXMY2. Repeat for distance squared to second, third, and fourth anchors. Drag down to calculate for each row. Input values into new columns called 'Dist^2 to 1',	 'Dist^2 to 2',	'Dist^2 to 3', and 'Dist^2 to 4'.
11) Calculate the minimum distance squared for each row using =MIN. Input values into column called 'Min Distance'
12) Compute the cluster to which each tract is assigned by using =MATCH.
13) Input the formula =SUM in the row above the 'Min Distance' column to find the sum of all of the Min Distance values
14) Using Solver, set objective to the cell which contains the =SUM formula. Set min of 0. For "By changing variabe cells:" field, select the cells of the 4 anchors you chose. Set the constraints to "<= 661", "= integer", and ">=1)
15) Set solving method to evolutionary and the mutation rate to .5. Hit ok.
