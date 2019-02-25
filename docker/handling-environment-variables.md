# Handling Environment Variables

## `.env` File:

Create a `.env` file to hold all of your private environment variables.

`.env`:
```
POSTGRES_VERSION=11.2
POSTFRES_PASSWORD=THIS_IS_A_REAL_PASSWORD
CLIENT_ID=THIS_IS_TOTALLY_A_REAL_CLIENT_ID
CLIENT_SECRET=THIS_IS_TOTALLY_A_REAL_CLIENT_SECRET
```

**Note:** Do not enclose your string variable in quotes as the quotes will be included in the variable value.

## `docker-compose.yml` File:

Once you have your `.env` file, you can add those variable names to your `docker-compose.yml` under the "envinronment" section. You do not have to make any reference to the `.env` file as Docker knows to check for that file first.

```
version: "3.7"

services:
  database:
    container_name: site_database
    image: postgres:${POSTGRES_VERSION}-alpine
    environment:
      - POSTGRES_DB:'database_name'
      - POSTGRES_USER:'user'
      - POSTGRES_PASSWORD
      - CLIENT_ID
      - CLIENT_SECRET
    volumes:
        - database:/var/lib/postgresql/data

volumes:
  database:
```

Notice the difference between `POSTGRES_VERSION` and `POSTGRES_PASSWORD/CLIENT_ID/CLIENT_SECRET`. The version variable is used within the _yaml file_ while the other variables will be used by the python files within the _container_. Also notice that you can _include_ the variable value in the yaml file if you choose to do so.

To verify that your container environment variables have been set, you can check using your composer config command.

```
$ docker-compose config
version: "3.7"

services:
  database:
    container_name: site_database
    image: postgres:11.2-alpine
    environment:
      - POSTGRES_DB:'database_name'
      - POSTGRES_USER:'user'
      - POSTGRES_PASSWORD: THIS_IS_A_REAL_PASSWORD
      - CLIENT_ID: THIS_IS_TOTALLY_A_REAL_CLIENT_ID
      - CLIENT_SECRET: THIS_IS_TOTALLY_A_REAL_CLIENT_SECRET
    volumes:
        - database:/var/lib/postgresql/data

volumes:
  database:

```

After you've set the variables in the container, you can access them in the [usual way](https://github.com/jcatoe/til/blob/master/python/different-ways-to-access-environment-variables.md) within your python files.


## Related Resources:
* https://docs.docker.com/compose/environment-variables/
* https://stackoverflow.com/questions/22651647/docker-and-securing-passwords
* https://docs.docker.com/engine/swarm/secrets/
* https://medium.com/@maxy_ermayank/credential-store-using-hashicorp-vault-7d2fdeed08f2
* https://www.reddit.com/r/docker/comments/83krlc/how_to_deploy_sensitive_info_like_passwords_to_a/
