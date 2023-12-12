Create a Dataproc cluster
Run the following command in a Cloud Shell session terminal to:

Install the HBase and ZooKeeper components
Provision three worker nodes (three to five workers are recommended to run the code in this tutorial)
Enable the Component Gateway
Use image version 2.0
Use the --properties flag to add the HBase config and HBase library to the Spark driver and executor classpaths.
gcloud dataproc clusters create cluster-name \
    --region=region \
    --optional-components=HBASE,ZOOKEEPER \
    --num-workers=3 \
    --enable-component-gateway \
    --image-version=2.0 \
    --properties='spark.driver.extraClassPath=/etc/hbase/conf:/usr/lib/hbase/*,spark.executor.extraClassPath=/etc/hbase/conf:/usr/lib/hbase/*'

Verify connector installation
From the Google Cloud console or a Cloud Shell session terminal, SSH into the Dataproc cluster master node.

Verify the installation of the Apache HBase Spark connector on the master node:

ls -l /usr/lib/spark/jars | grep hbase-spark
Sample output:
-rw-r--r-- 1 root root size date time hbase-spark-connector.version.jar
Keep the SSH session terminal open to:

Create an HBase table
(Java users): run commands on the master node of the cluster to determine the versions of components installed on the cluster
Scan your Hbase table after you run the code
Create an HBase table
Run the commands listed in this section in the master node SSH session terminal that you opened in the previous step.

Open the HBase shell:

hbase shell
Create an HBase 'my-table' with a 'cf' column family:

create 'my_table','cf'
To confirm table creation, in the Google Cloud console, click HBase in the Google Cloud console Component Gateway links to open the Apache HBase UI. my-table is listed in the Tables section on the Home page.
