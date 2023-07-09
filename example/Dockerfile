FROM fredrikbakken/cluster-apache-spark:3.2.4

RUN apt-get update && apt-get install -y curl

RUN curl -o /opt/spark/jars/postgresql-42.2.22.jar https://repo1.maven.org/maven2/org/postgresql/postgresql/42.2.22/postgresql-42.2.22.jar

COPY requirements.txt .

RUN python -m pip install -r requirements.txt
