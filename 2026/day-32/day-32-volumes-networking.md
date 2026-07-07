# Day 32 – Docker Volumes & Networking

## Objective
Today's goal was to understand two important Docker concepts:

Data Persistence using Volumes

Container Communication using Networks

## Task 1: The Problem (Without Volumes)

### Run PostgreSQL Container

```bash

docker run -d \
--name postgres-no-volume \
-e POSTGRES_PASSWORD=admin123 \
-p 5432:5432 \
postgres

```

### Create Sample Data

```bash
ubuntu@ip-172-31-33-163:~$ docker exec -it postgres-no-volume psql -U postgres
psql (18.4 (Debian 18.4-1.pgdg13+1))
Type "help" for help.

postgres=# CREATE TABLE students(
id SERIAL PRIMARY KEY,
name VARCHAR(50)
);

INSERT INTO students(name)
VALUES('Harsha');

SELECT * FROM students;

```

### Output

```bash 
CREATE TABLE
INSERT 0 1
 id |  name
----+--------
  1 | Harsha
(1 row)

postgres=#

```

## Remove Container

```bash

ubuntu@ip-172-31-33-163:~$ docker ps
CONTAINER ID   IMAGE      COMMAND                  CREATED          STATUS          PORTS                                         NAMES
c0919492c15e   postgres   "docker-entrypoint.s…"   33 minutes ago   Up 33 minutes   0.0.0.0:5432->5432/tcp, [::]:5432->5432/tcp   postgres-no-volume
ubuntu@ip-172-31-33-163:~$
ubuntu@ip-172-31-33-163:~$ docker stop postgres-no-volume
postgres-no-volume
ubuntu@ip-172-31-33-163:~$

ubuntu@ip-172-31-33-163:~$ docker rm postgres-no-volume
postgres-no-volume
ubuntu@ip-172-31-33-163:~$ docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED       STATUS                   PORTS     NAMES
a1fc49f50fe3   my-ubuntu:v1   "echo 'Hello from my…"   2 weeks ago   Exited (0) 2 weeks ago             elastic_rubin

```

## Create New Container

```bash

ubuntu@ip-172-31-33-163:~$ docker run -d \
--name postgres-new \
-e POSTGRES_PASSWORD=admin123 \
-p 5432:5432 \
postgres
3f716fd08ded69dd6fc4012cc99c85585282a3af6a9b400a8bf2f38f12b21d0d
ubuntu@ip-172-31-33-163:~$


ubuntu@ip-172-31-33-163:~$ docker ps
CONTAINER ID   IMAGE      COMMAND                  CREATED          STATUS          PORTS                                         NAMES
3f716fd08ded   postgres   "docker-entrypoint.s…"   42 seconds ago   Up 41 seconds   0.0.0.0:5432->5432/tcp, [::]:5432->5432/tcp   postgres-new
ubuntu@ip-172-31-33-163:~$

ubuntu@ip-172-31-33-163:~$ docker exec -it postgres-new  psql -U postgres
psql (18.4 (Debian 18.4-1.pgdg13+1))
Type "help" for help.

postgres=# SELECT * FROM students;
ERROR:  relation "students" does not exist
LINE 1: SELECT * FROM students;
                      ^
postgres=#

```


## Observation
The data was lost because containers are ephemeral. When the container was removed, its writable layer was deleted along with all database data.


## Task 2: Named Volumes

Create Volume
```bash
docker volume create postgres-data
```

Verify Volume
```bash
docker volume ls
```

Run PostgreSQL with Volume
```bash
docker run -d \
--name postgres-volume \
-e POSTGRES_PASSWORD=admin123 \
-v postgres-data:/var/lib/postgresql/data \
-p 5432:5432 \
postgres
```

## Create Data
```bash
CREATE TABLE employees(
id SERIAL PRIMARY KEY,
name VARCHAR(50)
);

INSERT INTO employees(name)
VALUES('Harsha');

SELECT * FROM employees;
```

## Remove Container
```bash
docker stop postgres-volume
docker rm postgres-volume
```

## Recreate Container with Same Volume

```bash
docker run -d \
--name postgres-volume-new \
-e POSTGRES_PASSWORD=admin123 \
-v postgres-data:/var/lib/postgresql/data \
-p 5432:5432 \
postgres
```


## Verify Data

SELECT * FROM employees;


Output
 id |  name
----+---------
 1  | Harsha
 
## Observation
The data remained available because it was stored in a Docker volume rather than inside the container filesystem.
