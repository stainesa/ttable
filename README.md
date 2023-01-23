# ttable
More flexible, but embryonic and unusable, approach to tables and tabulation in R

The key aim here is a dataframe based tabulation package.
R has many excellent tools for tables, most of which produce lists or arrays of various types. Their goal is to produce something that can be printed, to provide a quick summary of a dataframe.
There seem to be three common use cases for tables in data analysis 
* Cross-tabulation, counts by factor levels. The key function is table, but xtab, and ftab, both in base R, have similar functions.
* table(diamonds$cut)

     Fair      Good Very Good   Premium     Ideal 
     1610      4906     12082     13791     21551 
>  table(diamonds$color,diamonds$cut)
   
    Fair Good Very Good Premium Ideal
  D  163  662      1513    1603  2834
  E  224  933      2400    2337  3903
  F  312  909      2164    2331  3826
  G  314  871      2299    2924  4884
  H  303  702      1824    2360  3115
  I  175  522      1204    1428  2093
  J  119  307       678     808   896
> 
* Variable tabulation, one row per variable, reporting quantitative summaries, possibly presented by the values of a factor variable, which is typcially a column variable. There is a really good package called table1, which does this well, but produces a html table as its output,which is hard to work with further.
	1 (N=57)	2 (N=134)	3 (N=14)	Overall (N=205)
factor(sex)				
0	28.0 (49.1%)	91.0 (67.9%)	7.00 (50.0%)	126 (61.5%)
1	29.0 (50.9%)	43.0 (32.1%)	7.00 (50.0%)	79.0 (38.5%)
age				
Mean (SD)	55.1 (17.9)	50.0 (15.9)	65.3 (10.9)	52.5 (16.7)
Median [Min, Max]	56.0 [14.0, 95.0]	52.0 [4.00, 84.0]	65.0 [49.0, 86.0]	54.0 [4.00, 95.0]
factor(ulcer)				
0	16.0 (28.1%)	92.0 (68.7%)	7.00 (50.0%)	115 (56.1%)
1	41.0 (71.9%)	42.0 (31.3%)	7.00 (50.0%)	90.0 (43.9%)
thickness				
Mean (SD)	4.31 (3.57)	2.24 (2.33)	3.72 (3.63)	2.92 (2.96)
Median [Min, Max]	3.54 [0.320, 17.4]	1.36 [0.100, 12.9]	2.26 [0.160, 12.6]	1.94 [0.100, 17.4]

* Tabulation of a model output, as done for example by the stargazer package, which is fantastic, and produces well-formatted tables.

In general, existing packages produce very specific data strucutures, which are intended for direct presentation.

ttables is intended to produce tables which are tibbles, and intended to be presented by other packages, such as kable, arsenal, and many more. The intent is to make it straightforward to use, adapt and extend the table.
The first key use case is row totals and row percentages.
