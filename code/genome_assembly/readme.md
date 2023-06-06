To get the mismatchers and indels from the Quast results, using the following code:

```shell
awk '{print $1 "\t" $45 "\t" $46}' transposed_report.tsv  | grep -v Assembly > tmp_file.txt 
sed -i 's/.fq//g' tmp_file.txt
sed -i 's/.seed1./_seed1_/g' tmp_file.txt 
sed -i 's/.seed2./_seed2_/g' tmp_file.txt 
sed -i 's/.seed3./_seed3_/g' tmp_file.txt 
sed -i 's/.seed4./_seed4_/g' tmp_file.txt 
sed -i 's/.seed5./_seed5_/g' tmp_file.txt 
sed -i 's/R941./R941_/g' tmp_file.txt
sed -i 's/simplex./simplex_/g' tmp_file.txt
sed 's/_/\t/g' tmp_file.txt | awk '{print $1 "\t" $2"_"$5 "\t" $3 "\t" $4 "\t" $6 "\t" $7}' > final_file.txt
```

Then we can get the table which can be used to plot the figure by R package, ggplot2. NOTE: please add the header.

```shell
bac	type	coverage	seed	mis	indels
ab1	R941_ngs	100	seed1	0.05	0.33
ab1	R941_ont	100	seed1	0.13	6.13
ab1	R941_ngs	100	seed2	0.46	0.87
ab1	R941_ont	100	seed2	0.54	6.51
ab1	R941_ngs	100	seed3	0.00	0.46
ab1	R941_ont	100	seed3	0.00	6.49
ab1	R941_ngs	100	seed4	0.31	0.46
ab1	R941_ont	100	seed4	0.28	6.37
ab1	R941_ngs	100	seed5	0.26	0.56
ab1	R941_ont	100	seed5	0.31	6.56
```

