# Technical cheatsheet

## Reading the datasets

1. Connect to the cluster 
  - `ssh kypraiou@iccluster111.iccluster.epfl.ch` (without GPU)
  - `ssh kypraiou@iccluster053.iccluster.epfl.ch` (with GPU)
  
2. Datasets located: `/dlabdata1/kypraiou`

## Transfering the files

- local to cluster: `scp ./get_wikidata.py  kypraiou@iccluster111.iccluster.epfl.ch:~/icfiler`
- cluster to local: `scp kypraiou@iccluster111.iccluster.epfl.ch:~/icfiler/{name}.py ./`


----------------------------------------------------
  
2. Access the datasets in the HDFS (hadoop cluster)
   - list of datasets:`hadoop fs -ls /datasets`
   - wikipedia datasets: 
     - `hadoop fs -ls /datasets/wikidatawiki`
       - /datasets/wikidatawiki/wikidatawiki-20170301-pages-articles-multistream-index.txt
       - /datasets/wikidatawiki/wikidatawiki-20170301-pages-articles-multistream.xml
     - `hadoop fs -ls /datasets/enwiki-20191001`
       - /datasets/enwiki-20191001/enwiki-20191001-pages-articles-multistream.xml
3. To read (take a sneak peak) from a dataset to the cluster: `hadoop fs -cat /datasets/<file_name> | less`
4. To  read the first 100 lines `hadoop fs -cat /datasets/<file_name> | head -n 100`
5. To copy the output to your own space in the cluster: `hadoop fs -cat /datasets/enwiki-20191001/enwiki-20191001-pages-articles-multistream.xml | head -n 200 > ~/enwiki_200_lines.txt`

- To transfer files from local to cluster:
`hadoop fs -put {filename.txt}  `
