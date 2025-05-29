# Proceso de instalación

1. Instalamos PostgreSQL desde los repositorios oficiales:
```bash
sudo apt install -y postgresql-common
```
![Install]()
```bash
sudo /usr/share/postgresql-common/pgdg/apt.postgresql.org.sh
```
![Install]()

```bash
sudo apt install -y postgresql
```
![Install]()


2. Configuramos el PostgreSQL para unirse mediante pgadmin4 via web:
```bash
sudo nano /etc/postgresql/17/main/postgresql.conf
```
![Install]()
![Install]()

```bash
sudo nano /etc/postgresql/17/main/pg_hba.conf
```
![Install]()
![Install]()
![Install]()

Reiniciamos
```bash
sudo systemctl restart postgresql
```
![Install]()

3. Creamos el Rol de administrador en PosgreSQL
Para poder crear roles primero entramos dentro de la base de datos como usuario
```bash
sudo -i -u postgres
```
![Install]()

Creamos el rol y sus características:

![Install]()

Estos són los usuarios que se encuentran en nuestra base de datos y sus roles:
```bash
psql
```
![Install]()


4. Instalamos pgadmin4
```bash
curl -fsS https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo gpg --dearmor -o /usr/share/keyrings/packages-pgadmin-org.gpg
```
![Install]()

```bash
sudo sh -c 'echo "deb [signed-by=/usr/share/keyrings/packages-pgadmin-org.gpg] https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list && apt update'
```
![Install]()

```bash
sudo apt install pgadmin4
```
![Install]()


6. Configuramos para el webserver:
```bash
sudo /usr/pgadmin4/bin/setup-web.sh
```
![Install]()

A
![Install]()



PONER LO DE LOS ROLES Y TODO ESO Y EXPLICAR UN POCO

