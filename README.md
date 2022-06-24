# django_demo

Demo of a Django Rest Framework API. This is mostly based on the [DRF
quickstart][drf_quickstart], `drf_spectacular` and `openapi-generator-cli`.


[drf_quickstart]: https://www.django-rest-framework.org/tutorial/quickstart/

## Quickstart

- Set up env (use a venv and at least python 3.8 if you can):

    ```shell
    cd /path/to/repo/root
    python -m pip install -r requirements.in
    python tutorial/manage.py migrate
    ```

- Seed an admin user with the password _Pass1234_:

    ```shell
    python tutorial/manage.py createsuperuser --email admin@example.com --username admin
    ```

- Generate schema

     ```shell
    tutorial/manage.py spectacular --file schema.yml
    mv schema.yml client/
    ```

- (Optional) Generate client after making any changes to serializers and views.

    ```shell
    docker run \
        --rm \
        -v "$PWD:/local" \
        openapitools/openapi-generator-cli \
        generate \
        -i /local/client/schema.yml \
        -g python \
        -o /local/client/python
    ```

- Install client

    ```shell
    python -m pip install -e client/python
    ```

- Start the API:

    ```shell
    python tutorial/manage.py runserver 0.0.0.0:5001
    ```

- Run demo that adds a new group

    ```shell
    python demo.py
    ```

