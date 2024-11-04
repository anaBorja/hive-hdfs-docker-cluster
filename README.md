# Proyecto de Hadoop y Hive en Docker

Este proyecto utiliza Docker para desplegar un clúster de Hadoop y Hive. Asegúrate de seguir los pasos a continuación para configurar y ejecutar correctamente los servicios.
TIENE PROBLEMAS CON HIVE

cuando se haya clonado el repositorio en la terminal debes poner 

acceder a las interfaces web:
  HDFS: http://localhost:9870
  YARN: http://localhost:8088
  Hive: http://localhost:10000

1.cargar datos.csv en HDFS
  ```bash
    docker exec -it namenode bash

2.crear una directorio en hdfs para alamacenar los datos:
  
    hdfs dfs -mkdir /datos
  
3.cargar el archivo datos.csv en HDFS
  
  hdfs dfs -put /datos.csv /datos/
  
4.Verifica que el archivo se haya cargado correctamente:

  hdfs dfs -ls /datos
  
5.ejecuta hive

  docker exec -it hive-server bash
  hive 

6.crear una tabla en hive 

    CREATE TABLE datos (
       id  INT,
      name STRING,
      age INT,
      color STRING, 
    )
    ROW FORMAT DELIMITED
    FIELDS TERMINATED BY ',';

7.cargar los datos desde HDFS  a la tabla de hive.

  LOAD DATA INPATH '/datos/datos.csv' INTO TABLE datos;

8.Realizar las consultas. 

  SELECT * FROM datos;

9.Detener los servicios.

  docker-compose down

