# Specify Table Name For Model

Django defaults to prefixing all tables with the app name. To prevent this from happening, you need to add the Meta class to your model and set the database table variable.

For example, if you created a model called `Contact` inside of your app called `Party`, Django would name that table `party_contact`. This is a terrible practice for maintaining a clean database. Instead, you can set the table name to be `contacts` to follow proper standards.

```
class Contact(models.Model):
    first_name = models.CharField(max_length=100)
    . . .
    class Meta:
        db_table = "contacts"
```

**Note:** it is best to make this change _before_ you run migrations for this model.
