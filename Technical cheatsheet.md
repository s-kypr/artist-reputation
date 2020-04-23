# Technical cheatsheet

## Reading the datasets

1. Connect to the cluster 
  - `ssh kypraiou@iccluster111.iccluster.epfl.ch` (without GPU)
  - `ssh kypraiou@iccluster053.iccluster.epfl.ch` (with GPU)
  
2. Datasets located: `/dlabdata1/kypraiou`

## Transfering the files

- local to cluster: `scp ./get_wikidata.py  kypraiou@iccluster111.iccluster.epfl.ch:~/`
- cluster to local: `scp kypraiou@iccluster111.iccluster.epfl.ch:~/{name}.py ./`


## Connecting to big-data cluster

1. login to hadoop cluster: `ssh kypraiou@hadoop.iccluster.epfl.ch `

2. To transfer files from local to cluster:
`hadoop fs -put {filename.txt} ` 

3. To tranfer files from cluster to local:
`hadoop fs -getmerge artists.json artists.json`

4. Access the datasets in the HDFS (hadoop cluster)
   - list of datasets:`hadoop fs -ls /user/kypraiou`
   - wikipedia datasets: 
     - `hadoop fs -ls /user/kypraiou/wikidata.json.bz2`
  
3. To read (take a sneak peak) from a dataset to the cluster: `hadoop fs -cat /user/kypraiou/<file_name> | less`
4. To  read the first 100 lines `hadoop fs -cat /user/kypraiou/<file_name> | head -n 100`
5. To copy the output to your own space in the cluster: `hadoop fs -cat /datasets/enwiki-20191001/enwiki-20191001-pages-articles-multistream.xml | head -n 200 > ~/enwiki_200_lines.txt`

`

## Run the files in the custer

`spark-submit --master yarn --packages com.databricks:spark-xml_2.11:0.7.0 --num-executors 70 --executor-memory 6g get_wikidata.py` (took 45 min) 

- monitor your running Hadoop and Spark jobs: http://iccluster075.iccluster.epfl.ch:8088/cluster/apps
