# pig_wordcount_programe
*********************************
WordCount Program:
*********************************

CMD ->
1. cat>> wordcountPig.txt
i am mudit
i am human  (cTrl+Z)

2. hadoop fs -mkdir /pig_data
3. hadoop fs -put wordcountPig.txt /pig_data

4. cd hive/bin
5. pig
   
6. lines = LOAD 'hdfs://localhost:9000/pig_data/wordcountPig.txt' AS (line:chararray);
7. words = FOREACH lines GENERATE FLATTEN(TOKENIZE(line)) as word;
8. grouped = GROUP words BY word;
9. wordcount = FOREACH grouped GENERATE group, COUNT(words);
10. DUMP wordcount;
