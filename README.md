# pig_wordcount_programe
*********************************
WordCount Program:
*********************************

CMD ->
1. cat>> wordcountPig.txt

i am mudit
i am human
(cTrl+Z)


3. hadoop fs -mkdir /pig_data
4. hadoop fs -put wordcountPig.txt /pig_data

5. cd hive/bin
6. pig

## grunt > cmd .......
........................................

1. lines = LOAD 'hdfs://localhost:9000/pig_data/wordcountPig.txt' AS (line:chararray);


2. words = FOREACH lines GENERATE FLATTEN(TOKENIZE(line)) as word;
3. grouped = GROUP words BY word;
4. wordcount = FOREACH grouped GENERATE group, COUNT(words);
5. STORE wordcount INTO '/wordcount_output1' USING PigStorage(',');
6. fs -cat /wordcount_output1/part-r-00000


***************************************** THANKYOU ******************************************
