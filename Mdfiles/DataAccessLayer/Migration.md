# Data Access Layer

## Migration

<p>
SQLAlchemy itself does not provide a built-in migration system like Django or Alembic, but many projects use Alembic in combination with SQLAlchemy for database migrations.

Using Alembic with SQLAlchemy:

</p>


### Install Alembic:

Alembic is a lightweight database migration tool that integrates well with SQLAlchemy. Install it using pip:

```
pip install alembic
```

### Initialize Alembic:

Run the following command to initialize Alembic in your project:

```
alembic init alembic
```

This will create an alembic directory with configuration files and a versions directory for storing migration scripts.


### Configure Alembic:

Modify the alembic.ini file to specify the database URL and other configuration options.

```
# alembic.ini
sqlalchemy.url = postgresql://user:password@localhost:5432/mydatabase
```

Run the following command to generate an initial migration:

```
alembic revision --autogenerate -m "initial"
```


Apply the migrations to update your database:
```
alembic upgrade head
```

When you make changes to your SQLAlchemy model, generate and apply additional migrations:

```
alembic revision --autogenerate -m "description_of_change"
alembic upgrade head
```