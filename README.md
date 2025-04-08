ETL process that can extract current weather data from open weather map API, transform the data and load the data into an S3 bucket using Apache Airflow.


1. Connect to open weather map api (get api key)
2. Create EC2 and launch instance
- name instance (weather-api-airflow)
- create new key pair 
- weather-api-airflow-yml-key-pair
- connect ec2 instance (ubuntu)
3. edit inbound rules in security groups as 8080
4. Installing dependencies
sudo apt update
sudo apt install python3-pip
sudo apt install python3.10-venv
python3 -m venv airflow_venv
sudo pip install pandas
sudo pip install s3fs  -- to connect to s3
sudo pip install apache-airflow
airflow standalone
sudo apt  install awscli
aws configure
aws sts get-session-token
5. copy Private IPV4 address from ec2 instance we created and paste it to new tab followed by 8080 it will open airflow login page enter username and password you copied from virtual machine
6. connect visual studio to ec2 instance you created  to write your dag code in visual studio
7. created new folder under airflow in visual studio folder structure and then create new file weather_dag.py
write from airflow import DAG , timedelta, datetime, HttpSensor, json, PythonOperator, pandas and remaining code in this python file
add task Isweatherapi
8. on airflow page add connection 
9. you must see your DAG added to airflow page, click on DAG and then check the graph
10. Use SimpleHttpOperator to extract data from api ( task no. 2)
11. Use PythonOperator to call ht efunction written to transform the weather data by calling python callable ( task no.3)
12. after this create bucket in s3 where we are going to load weather data finally. choose IAM role and assign policies for EC2 instance to access (ec2fullaccess, s3fullaccess)
also create Accesskey by clicking on security credentials , go to visal studio terminal and activate vm and then install awscli , then configure aws with this access key and get session token 

is_weather_api_ready >> extract_weather_data >> transform_load_weather_data
