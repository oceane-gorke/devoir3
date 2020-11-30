FROM python:latest

COPY . /manager/
COPY __init__.py ./app/__init__.py
COPY __main__.py ./app/__main__.py
COPY config.py ./app/config.py
COPY tests_integration.py ./app/tests_integration.py
COPY utils_postgres.py ./app/utils_postgres.py
COPY data.csv ./app/data.csv

RUN pip3 install psycopg2

RUN wget https://raw.githubusercontent.com/vishnubob/wait-for-it/master/wait-for-it.sh -P /
RUN chmod +x /wait-for-it.sh
ENTRYPOINT ["/wait-for-it.sh", "db:5432", "--"]

CMD python -m manager