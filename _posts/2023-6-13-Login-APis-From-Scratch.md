

## Django Login Project Documentation

### Initial Setup

#### Setup Virtual Environment

```
python3 -m venv venv
source venv/bin/activate
```


#### Install Django
```pip install django
django-admin startproject loginproject
python manage.py runserver
python manage.py startapp loginapp
python manage.py createsuperuser
```

#### Apply database migrations
```python manage.py makemigrations
python manage.py migrate
```


### Establish database connection:
```conn = psycopg2.connect(
           host="localhost",
           port="5432",
           database="postgres",
           user="postgres",
           password="mahima@123"
       )
```


### Create Table
#### urls.py
```path('createTable/', CreateTableView.as_view(), name='createTable'),
```

#### views.py
```cur.execute('''CREATE TABLE IF NOT EXISTS employees
                       (id SERIAL PRIMARY KEY,
                       username TEXT NOT NULL,
                       email TEXT NOT NULL,
                       password TEXT NOT NULL)''')
```

### Update Table
#### urls.py
```path('UpdateTable/', UpdateTableView.as_view(), name='UpdateTable'),
```

#### views.py
```dict1 = {
           "username": "username",
           "password": "password",
           "email": "email"
       }
       cur.execute(
           "INSERT INTO employees (username, password, email) VALUES (%(username)s, %(password)s, %(email)s);", dict1)
```

### APIs
#### Employees
```table
| Method | API                | Function             |
| ------ | ------------------ | -------------------- |
| POST   | createTable/       | Create employees     |
| POST   | updateTable/       | Update employees     |
| GET    | get_employees/     | Get all employees    |
| GET    | get_employee/id    | Get employee by ID   |
| POST   | add_employee/      | Add new employee     |
| POST   | delete_employee/id | Delete employee      |
```

#### Token Generation

| Method | API         | Function  |
| ------ | ----------- | --------- |
| GET    | get_token/id| Get token |

#### Register

| Method | API        | Function  |
| ------ | ---------- | --------- |
| GET    | register/id| Register  |

#### Login

| Method | API    | Function |
| ------ | ------ | -------- |
| POST   | login/ | Login    |

#### Send Email Invitation

| Method | API        | Function         |
| ------ | ---------- | ---------------- |
| POST   | send-email/| Send email invite|


### JWT token generation

``````

```token_lifetime = timedelta(days=1)
token_expiry = datetime.now() + token_lifetime
access_token = jwt.encode(
                {
                    'id': employee['id'],
                    'username': employee['username'],
                    'email': employee['email'],
                    'password': employee['password'],
                    'exp': int(token_expiry.timestamp())
                },
                'secret9742357373',
                algorithm='HS256'
            )
token = access_token
base_url = f"http://127.0.0.1:8000/register/{id}"
query_params = {'token': token}
registration_link = base_url + '?' + urlencode(query_params)
```

#### JWT token Decode

```token = request.GET.get('token')
decoded_token = jwt.decode(token, 'secret9742357373', algorithms=['HS256'])
email = decoded_token.get('email')

```
### Send Email Invitation:
```send_mail(subject, message, from_email, recipient_list)
```