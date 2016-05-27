# hive_db_copy
To Copy Database between Clusters




Please follow the below steps 

>have took the Dump of DB : 
edit the script gettable_list with DB name : old_db and run the script gettblstr.sh
>took the copy of database's data from its parent Directory.
hdfs dfs -get /tenant_nm/hive/tenant_grp/warehouse/emp_info_xbblwv5.db
>moved the data from old_cluster to new_cluster using DISTCP(Please implement Kerberos Cross Realm if already available)

>Edit the files inside op_tbl_list directory with new database and directory structure
edit_sc.sh
>Create the directory structure as in Dev (edit the db name)
hdfs dfs -mkdir /tenant_nm/hive/tenant_grp/warehouse/emp_info_xbblwv1.db/
>Recreate the DataBase in UAT (Specify the new location where data is moved)
CREATE DATABASE IF NOT EXISTS emp_info
location '/tenant_nm/hive/tenant_grp/warehouse/emp_info_xbblwv1.db/'; 
>recrete the tables in UAT 
./createtbl.sh
