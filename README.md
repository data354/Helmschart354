# Helmschart354
- Version 
     - Numero : 0.1.0
     - Content : Postgresql + airflow + Spark + Minio + HiveMetastore + Trino
     - URL : https://data354.github.io/Helmschart354/Stack/

- PORTS MAPPING 
    - 30000   ------------------------------  AIRFLOW UI
    - 30001   ------------------------------- MINIO CONSOLE
    - 30002   ------------------------------- Postgresql
    - 30003   -------------------------------- Trino
    
- INSTALL
    - helm repo add stack https://data354.github.io/Helmschart354/Stack/
    - helm install $RELEASENAME stack/modernstack --set postgres.enabled=true --set airflow.enabled=true --set airflow.dags.gitSync.branch=master --set airflow.dags.gitSync.enabled=true --set airflow.dags.gitSync.repo=$repo   --set airflow.dags.gitSync.sshKeySecret=$sshKeysecret --set airflow.dags.gitSync.subPath=$subpath --set airflow.images.airflow.repository=$repo --set airflow.images.airflow.tag=$tag -n $NAMESPACE
    - kubectl create clusterrolebinding service-all-pod   --clusterrole=service-all    --serviceaccount=$NAMESPACE:$RELEASENAME-airflow-worker 
     
$repo = ssh://git@github.com/data354/Data-stack.git
$subpath = airflow/dags
$repo=europe-west9-docker.pkg.dev/dev-clients-307710/media54/airflow
$tag=v5
