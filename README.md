# amazon_analysis_labpart2
# Analysis Question:
What is the distribution of verified / unverified by days of the week? Is there a significant difference?

# Analysis Results 

![Caption for the picture.](/images/results_chart.png)


# Steps to Run the code:
1. Log into dsba-hadoop.uncc.edu using ssh
2. git clone https://github.com/AzizIsa/amazon_analysis_labpart2.git to clone this repo
3. Go into the repo directory. In this case: cd amazon_analysis_labpart2
4. Make a "build" directory (if it does not already exist): 
``` text
mkdir build
```
5. Compile the java code (all one line). You may see some warnings--that' ok.
``` text
javac -cp /opt/cloudera/parcels/CDH/lib/hadoop/client/*:/opt/cloudera/parcels/CDH/lib/hbase/* PopulationBreakDown_total.java -d build -Xlint
```
6. Now we wrap up our code into a Java "jar" file: 
``` text
jar -cvf process_reviews_total.jar -C build/ .
```

7.(Optional) Remove the previous results folder
``` text
hadoop fs -rm -r /user/aisamedi/product_reviews
```
8. Execute the Jar File
``` text
HADOOP_CLASSPATH=$(hbase mapredcp):/etc/hbase/conf hadoop jar process_reviews.jar PopulationBreakDown_total '/user/aisamedi/product_reviews'
```
9. Verify the Output
``` text
hadoop fs -cat /user/aisamedi/product_reviews/*
```
