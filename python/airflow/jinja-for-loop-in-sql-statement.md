# Jinja For-Loop In SQL Statment

I had an instance where I needed to rename a bunch of columns in a couple of tables. My configuration structure was a simple dictionary type.

```
transformations = {
    'source_table_a': {
        'dest_table_name': 'dest_table',
        'primary_key': 'dest_id',
        'rename_columns': {
            'id': 'dest_id',
            'fullname': 'full_name',
            'required': 'is_required'
     },
     'source_table_b': {
        'dest_table_name': 'dest_table',
        'primary_key': 'dest_id',
        'rename_columns': {
            'id': 'dest_id',
            'fullname': 'full_name',
            'required': 'is_required'
     }
}
```

These changes were happening in a Redshift database, so I used the `PostgresOperator`:

```
# looping through the source tables
for source_table in transformations.keys():

    rename_columns_tasks = PostgresOperator(
        sql='''
        {% for orig_column, renamed_column in params.mapping.items() %}
            ALTER TABLE {{ params.source_schema }}.{{ params.source_table }}
                RENAME COLUMN {{ orig_column }} TO {{ renamed_column }};
        {% endfor %}
        ''',
        postgres_conn_id=redshift_conn_id,
        autocommit=False,
        params={
            'source_schema': source_schema,
            'source_table': source_table,
            'mapping': transformations[source_table]['rename_columns'],

        },
        task_id=f'{source_table}_rename_columns',
        dag=dag
    )
```

If you check the task logs, you can see the `ALTER` statement getting printed for each column that needs to be renamed.
