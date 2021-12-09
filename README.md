# Big-Data-Project
The Big Data class project about constructing multi-factor model with behavioral factors
	The code for the project is based on the CSV file of SPY called SPY.csv, which is an exchange-traded fund (ETF) that tracks the S&P 500 index and should represent the whole US equity market. The CSV file is downloaded from yahoo finance, so the raw data is complete and there is not much cleaning needed.
	The entire codes are commands running on PySpark, and they are documented in four docx files. The number before the command indicates the order of the commands to analyze the data. In the data_ingest directory, the first command is to read the csv file from the HDFS directory. Then I can do some data profiling (in profiling_code directory) to gain some initial insights of the data (command 2-4). 
	The first step is to use the columns to construct the factors I need for the model. In the ana_code directory, return of the stock is computed (command 5). From the “Return” column, I can compute the rolling cumulative return in the windows of 21 days and 252 days to get two factors we need (command 7 -12); I get the third factor by computing the maximum of the average returns in 21 days (command 13-14); the fourth factor is computed through the ratio between the liquidity in 21 days and 252 days (command 15-21). To prevent illegal action when computing the ratio, I did some cleaning of the data in etl_code directory (command 19-20) to get rid of the null values of the related columns. I saved the result as df_SPY.
	After computing the data, I kept the relevant columns (command 24-27) and saved as df_SPY2, which are the factors needed, to do the regression to get the coefficient of the model (command 28-44). To test the performance, I evaluate the model on the testing set (command 45-49). 
	
