# Proceso de instalación

1. Instalamos PostgreSQL:
```bash
sudo apt install -y postgresql
```
![Install](./imagenes/Base/Insta.png)


2. Configuramos el PostgreSQL para unirse mediante pgadmin4 via web:
```bash
sudo nano /etc/postgresql/17/main/postgresql.conf
```
![Install](./imagenes/Base/Conf.png)

```bash
sudo nano /etc/postgresql/17/main/pg_hba.conf
```
![Install](./imagenes/Base/Conf_hba.png)

Reiniciamos
```bash
sudo systemctl restart postgresql
```
![Install](./imagenes/Base/Reinicio.png)

3. Creamos el Rol de administrador en PosgreSQL
Para poder crear roles primero entramos dentro de la base de datos como usuario
```bash
sudo -i -u postgres
```
![Install](./imagenes/Base/crear.png)

Creamos el rol y sus características:

![Install](./imagenes/Base/Añadir.png)

Estos són los usuarios que se encuentran en nuestra base de datos y sus roles:
```bash
psql
```
![Install](./imagenes/Base/Comprobar.png)


4. Instalamos pgadmin4
```bash
curl -fsS https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo gpg --dearmor -o /usr/share/keyrings/packages-pgadmin-org.gpg
```
![Install](./imagenes/Base/Repositori.png)

```bash
sudo sh -c 'echo "deb [signed-by=/usr/share/keyrings/packages-pgadmin-org.gpg] https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list && apt update'
```
![Install](./imagenes/Base/Añadir_repo.png)

```bash
sudo apt install pgadmin4
```
![Install](./imagenes/Base/Instalar.png)


6. Configuramos para el webserver:
```bash
sudo /usr/pgadmin4/bin/setup-web.sh
```
![Install](./imagenes/Base/Conf_web.png)

A
![Install](./imagenes/Base/web.png)



PONER LO DE LOS ROLES Y TODO ESO Y EXPLICAR UN POCO

