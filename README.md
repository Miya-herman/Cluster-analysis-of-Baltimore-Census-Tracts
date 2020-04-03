# Cluster-analysis-of-Baltimore-Census-Tracts

#Findings and Background Data
I chose to focus on the the prompt: "How are commuting zones or census tracts in Baltimore grouped based on different population metrics?" As Baltimore is a notoriously segregated region, I wanted to examine how census tracts are clustered by social factors such as race, income, and incarceration levels. I used a dataset from Opportunity Atlas, which contained data of black population, white populations, incarceration rates, and mean household incomes for each census tract. I then performed a 4 cluster analysis of this data, and found that the anchor tracts were characterized by very different z scores for each of the charcateristics I analyzed. I then tracked the anchor census tracts on a map of Baltimore, and found that they aligned with the "white L, black butterfly" distribution. 
![](map.pdf)

#Data Analysis Outline
business question: How can Baltimore government and organizations better target communities for social welfare programs? Cluster analyses of population characteristics are important to policymakers and non-governmental organizations who wish to target certain groups for social programs. Being aware of social factors, such as population demographics, can help these organizations better market services and meet the needs of the communities. 

data question: How are census tracts in the Baltimore area clustered by race, income, and incarceration level? After exploring the various outcomes on Opportunity Atlas, I found that race, income, and incarceration rates were three of the most defining characteristics for areas in the Baltimore region. I used these three metrics to perform a 4 cluster analysis of the Opporunity Atlas dataset.

data answer: The results of my cluster analysis yielded 4 anchor census tracts with varying z scores for each metric. 
![](results)
The areas with mid-high income and mid-low incarceration were associated with a higher white than black population. The census tract with low income and high incarceration was associated with a much higher black than white population. 

business answer: I traced each of the 4 anchor census tracts on the Opporunity Atlas map of the Baltimore Area, which was filtered for household income. The three anchors with the wealthier, lower incarceration characteristics were in the outskirts of the Baltimore area, in the "White L". Whereas the anchor with the lower income and higher incarceration metrics was in Baltimore City, in the "Black Butterfly". This demonstrates that the social factors of income and incarceration are closely tied with race, and therefore follow the same geographic boundaries as racial segregation in Baltimore. Policymakers and other organizations could use this information to distribute more funding towards programs that go to target poverty and high rates of incarceration in these areas. These population characteristics could also help to tailor programs that better fit the needs and social dynamics of these regions.

#Website Links

Opportunity Atlas Dataset:

Excel Analysis: 

#Step-by-step Analysis:

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
