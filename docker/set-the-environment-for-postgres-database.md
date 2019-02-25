# Set The Environment For Postgres Database

To set the Postgres database name, user, and password, add the environment variables: POSTGRES_DB, POSTGRES_USER, POSTGRES_PASSWORD, to your `docker-compose.yml` file.

**Note:** do _not_ include the actual password in your file. See "Related Resources" for more insight or the [pass-around-environment-variables.md](https://github.com/jcatoe/til/blob/master/docker/pass-around-environment-variables.md) file for easy to follow instructions.
```
version: "3.7"

services:
  database:
    container_name: site_database
    image: postgres:11.2-alpine
    environment:
      - POSTGRES_DB:'database_name'
      - POSTGRES_USER:'user'
      - POSTGRES_PASSWORD:'password'
    volumes:
        - database:/var/lib/postgresql/data

volumes:
  database:
```

## Related Resources:
* https://stackoverflow.com/questions/22651647/docker-and-securing-passwords
* https://docs.docker.com/engine/swarm/secrets/
* https://medium.com/@maxy_ermayank/credential-store-using-hashicorp-vault-7d2fdeed08f2
* https://www.reddit.com/r/docker/comments/83krlc/how_to_deploy_sensitive_info_like_passwords_to_a/
