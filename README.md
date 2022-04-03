# apache-airflow-on-heroku
Apache Airflow on Heroku

## Manual Installation
### Python
```
pip install "apache-airflow[postgres,password]"
```
### Heroku
```
heroku config:set AIRFLOW__CORE__SQL_ALCHEMY_CONN=<postgres_conn_string>
heroku config:set AIRFLOW__CORE__LOAD_EXAMPLES=False
heroku config:set AIRFLOW_HOME=/app
heroku config:set AIRFLOW__CORE__FERNET_KEY=<secret_key>
```
#### Generating Fernet key
```
# from Python console
>>> from cryptography import fernet 
>>> fernet.Fernet.generate_key() b'pZcwcoB8RQfjtE9n0Du5Weu8zLKoFphKkiGDBihOwcM=' 
>>>
```
