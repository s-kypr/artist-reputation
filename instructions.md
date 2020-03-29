# Excecuting files cheatsheet

## Create the dataset in the cluster

1. copy file to the cluster: 
 - `scp ./get_wikidata.py  kypraiou@iccluster111.iccluster.epfl.ch:~/`
 - `scp ./filter_wikidata.py  kypraiou@iccluster111.iccluster.epfl.ch:~/`

2. login to cluster - check files have correctly been transfered
 - `ssh kypraiou@iccluster111.iccluster.epfl.ch` (without GPU)
 
3. Connect to big data platform - hadoop cluster 
 - `ssh kypraiou@hadoop.iccluster.epfl.ch `
  
3. Excecute the file to create the dataset: 
 - `spark-submit --master yarn --packages com.databricks:spark-xml_2.11:0.7.0 --num-executors 70 --executor-memory 6g get_wikidata.py` (took 45 min) 
- monitor your running Hadoop and Spark jobs: http://iccluster075.iccluster.epfl.ch:8088/cluster/apps
- **`get_wikidata.py`** : reads the wikidata dump 

4. Transfer the qid file to the cluster + hadoop cluster
- `scp ./qid_artists.csv  kypraiou@iccluster111.iccluster.epfl.ch:~/`
- `hadoop fs -put qid_artists.csv`

5. Run and filter the dataset in cluster
- `spark-submit --master yarn --packages com.databricks:spark-xml_2.11:0.7.0 --num-executors 70 --executor-memory 6g filter_wikidata.py` (took 45 min) 


---------------------------------------


4. Access the datasets in the HDFS (hadoop cluster)
   - list of datasets:`hadoop fs -ls /user/kypraiou`
   - wikipedia datasets: 
     - `hadoop fs -ls /user/kypraiou/wikidata.json.bz2`
  

## Run the files in the custer

`spark-submit --master yarn --packages com.databricks:spark-xml_2.11:0.7.0 --num-executors 70 --executor-memory 6g get_wikidata.py` (took 45 min) 

- monitor your running Hadoop and Spark jobs: http://iccluster075.iccluster.epfl.ch:8088/cluster/apps
