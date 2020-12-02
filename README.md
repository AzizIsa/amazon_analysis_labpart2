# amazon_analysis_labpart2
# Analysis Question:

Among reviewers, how does the population break down into these three buckets?  1) all reviews are unverified, 2) all reviews are verified, and 3) mix of unverified and verified reviews.

# Steps to Run the code:
1. Log into dsba-hadoop.uncc.edu using ssh
2. git clone https://github.com/AzizIsa/amazon_analysis_labpart2.git to clone this repo
3. Go into the repo directory. In this case: cd amazon_analysis_labpart2
4. Make a "build" directory (if it does not already exist): mkdir build
5. Compile the java code (all one line). You may see some warnings--that' ok.
``` text
javac -cp /opt/cloudera/parcels/CDH/lib/hadoop/client/*:/opt/cloudera/parcels/CDH/lib/hbase/* PopulationBreakDown.java -d build -Xlint
```
6. Now we wrap up our code into a Java "jar" file: jar -cvf process_reviews.jar -C build/ .


7.(Optional) Remove the previous results folder
hadoop fs -rm -r /user/aisamedi/product_reviews

8. Execute the Jar File
HADOOP_CLASSPATH=$(hbase mapredcp):/etc/hbase/conf hadoop jar process_reviews.jar PopulationBreakDown '/user/aisamedi/product_reviews'

9. Verify the Output

hadoop fs -cat /user/aisamedi/product_reviews/*
