# apache-airflow-on-heroku
Apache Airflow on Heroku

## Manual Installation
### Initial Installation
#### Python
```
pip install "apache-airflow[postgres,password]"
```

#### Heroku
```
heroku config:set AIRFLOW__CORE__SQL_ALCHEMY_CONN=<postgres_conn_string>
heroku config:set AIRFLOW__CORE__LOAD_EXAMPLES=False
heroku config:set AIRFLOW_HOME=/app
heroku config:set AIRFLOW__CORE__FERNET_KEY=<secret_key>
```
##### Generating Fernet key
```
# from Python console
>>> from cryptography import fernet 
>>> fernet.Fernet.generate_key() b'pZcwcoB8RQfjtE9n0Du5Weu8zLKoFphKkiGDBihOwcM=' 
>>>
```
### Post Database Initialization
#### Heroku
```
heroku config:set AIRFLOW__WEBSERVER__AUTHENTICATE=True
heroku config:set AIRFLOW__WEBSERVER__AUTH_BACKEND=airflow.contrib.auth.backends.password_auth
```
### User Creation
```
heroku run bash
```
```
# create an admin user 
airflow users create \
--username admin \
--firstname Peter \
--lastname Parker \
--role Admin \
--email spiderman@superhero.org
# it should then prompt for password and re-enter password
```

## References
[Reference](https://medium.com/@damesavram/running-airflow-on-heroku-ed1d28f8013d)
[Airflow Doc](https://airflow.apache.org/docs/apache-airflow/stable/security/webserver.html)

