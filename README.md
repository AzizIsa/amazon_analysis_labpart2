# amazon_analysis_labpart2
# Analysis Question:

Among reviewers, how does the population break down into these three buckets?  1) all reviews are unverified, 2) all reviews are verified, and 3) mix of unverified and verified reviews.

# Steps to Run the code:
1. Log into dsba-hadoop.uncc.edu using ssh
2. git clone https://github.com/AzizIsa/amazon_analysis_labpart2.git to clone this repo
3. Go into the repo directory. In this case: cd amazon_analysis_labpart2
4. Make a "build" directory (if it does not already exist): mkdir build
5. Compile the java code (all one line). You may see some warnings--that' ok. "javac -cp /opt/cloudera/parcels/CDH/lib/hadoop/client/*:/opt/cloudera/parcels/CDH/lib/hbase/* PopulationBreakDown.java -d build -Xlint"
6. Now we wrap up our code into a Java "jar" file: jar -cvf process_reviews.jar -C build/ .


# Notes:
hadoop fs -rm -r /user/aisamedi/product_reviews

HADOOP_CLASSPATH=$(hbase mapredcp):/etc/hbase/conf hadoop jar process_products.jar PopulationBreakDown '/user/aisamedi/product_reviews'

hadoop fs -cat /user/aisamedi/product_fields/*
