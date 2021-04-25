A repository that `docker-compose`'s `depends_on` field does support `condition`.

# Usage
1. Clone this repository
    ```
    $ git clone https://github.com/porterdarby/docker-compose-condition-test.git
    ```

2. Start the application using `docker-compose up`. You can add the `-d` field if you wish.

# Results
When the containers begin to start up, the following lines will show up:

```
Creating network "docker-compose-condition-test_default" with the default driver
Creating docker-compose-condition-test_dependee_1 ... done
```

At this point, `docker-compose` will hang until approximately 95 seconds after the the `dependee` container has started. At this point, the `dependee` container will start exhibiting the status of "unhealthy". The `depender` container at no point starts up.

The final logs out to the service will look something like this:

```
Creating network "docker-compose-condition-test_default" with the default driver
Creating docker-compose-condition-test_dependee_1 ... done

ERROR: for depender  Container "1e172fff1455" is unhealthy.
ERROR: Encountered errors while bringing up the project.
```
