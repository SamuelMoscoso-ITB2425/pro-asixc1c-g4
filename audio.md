## Introducció Audio

En este documento, se describe el proceso de implementación de un servidor de streaming de audio utilizando Icecast2 en un servidor Ubuntu alojado en AWS EC2. 

---

## Instalación

### 1. **Preparación del software necesario**  
   - Instancia de Ubuntu Server 20.04/22.04 (tipo t2.large o c5)  
     ![Imagen de configuración de la instancia](./a.png)

     - Configuración del grupo de seguridad para permitir los puertos necesarios:
       - TCP 22 (SSH)
       - TCP 8000 (predeterminado de Icecast)
       - Puertos UDP para streaming  
       ![Imagen de configuración de puertos](./d.png)

     - Configuración de un nuevo par de claves  
       ![Imagen de configuración de claves](./b.png)

   - Configuración inicial del servidor:
     - Conexión a la instancia mediante SSH utilizando el par de claves  
     - Actualización de los paquetes del sistema para la descarga  
     - Instalación de herramientas de monitoreo: `vnstat` y `iperf3`  
       ![Imagen de actualización de paquetes](./f.png)

---

### 2. **Instalación y configuración de Icecast2**  
   - Para instalar Icecast2 y todas las herramientas necesarias, utilicé el comando:
     ```bash
     sudo apt install -y icecast2 darkice vnstat iftop iperf3 ufw
     ```

   - Para habilitar el servicio de Icecast2, utilicé:
     ```bash
     sudo sed -i 's/ENABLE=false/ENABLE=true/' /etc/default/icecast2
     ```

   - Edición del archivo de configuración:  
     - Para configurar, edité el archivo `/etc/icecast2/icecast.xml`. Los únicos cambios que realicé fueron las contraseñas para `sourceuser`, `admin` y el hostname a mi IP pública de AWS.  
       ```xml
       <limits>
         <clients>100</clients>
         <sources>2</sources>
         <threadpool>5</threadpool>
       </limits>
       <authentication>
         <source-password>@itb2025</source-password>
         <admin-user>admin</admin-user>
         <admin-password>@itb2025</admin-password>
       </authentication>
       <listen-socket>
         <port>8000</port>
       </listen-socket>

       <hostname>public IP</hostname>
       ```

> **💡 Nota:**  
> Asegúrate de que las contraseñas (`source-password` y `admin-password`) sean fuertes y seguras. Reemplaza `public IP` con la dirección IP pública real de tu instancia AWS EC2 para evitar problemas de conectividad.

   - Abrí los puertos necesarios:
     ```bash
     sudo ufw allow 8000/tcp
     sudo ufw allow 22/tcp
     sudo ufw enable
     ```
     ![Imagen de configuración de puertos](./m.png)

   - Reinicié Icecast2:
     ```bash
     sudo systemctl restart icecast2
     sudo systemctl enable icecast2
     ```
     ![Imagen de reinicio de Icecast2](./g.png)

---

### 3. **Subir archivo de prueba de audio**  
   - Para subir mi archivo MP3 descargado desde local a AWS:
     ```bash
     scp -i nuevo_key.pem test.mp3 ubuntu@ec2-public-ip:/home/ubuntu/
     ```
     ![Imagen de subida de archivo](./r.png)

     ![Imagen de configuración de puertos](./p.png)

   - Comprobación desde AWS:  
     ![Imagen de comprobación desde AWS](./s.png)

> **💡 Nota:**  
> Asegúrate de que el archivo `nuevo_key.pem` esté almacenado de forma segura y tenga los permisos correctos (`chmod 400 nuevo_key.pem`) para evitar problemas de acceso. Reemplaza `ec2-public-ip` con la dirección IP pública real de tu instancia AWS EC2.

---

## Verificación

### 1. **Prueba de funcionamiento de Icecast2**  
   - Para verificar si Icecast2 estaba funcionando o no:
     ```bash
     icecast://source:sourcepass@localhost:8000/admin/
     ```
     ![Imagen de prueba de Icecast2](./j.png)

   - Dentro de Icecast, puedes ver la lista de oyentes si el audio se está transmitiendo correctamente.  
     ![Imagen de lista de oyentes](./k.png)

> **💡 Nota:**  
> Asegúrate de que las contraseñas (`source-password` y `admin-password`) utilizadas en la configuración de Icecast2 coincidan con las credenciales que configuraste en el archivo `/etc/icecast2/icecast.xml`. Además, verifica que el servicio de Icecast2 esté funcionando y que las reglas del firewall permitan el acceso al puerto `8000`. En lugar de usar `localhost`, utiliza la IP de tu instancia.

---

### 2. **Prueba del stream de audio**  
   - Para verificar si el stream estaba funcionando o no:
     ```bash
     ffmpeg -re -i test.mp3 -vn -c:a libmp3lame -f mp3 icecast://source:sourcepass@localhost:8000/stream
     ```
     ![Imagen de prueba del stream](./l.png)

     ![Imagen de prueba del stream](./n.png)

> **💡 Nota:**  
> Asegúrate de que el archivo `test.mp3` esté subido al directorio correcto en tu servidor y que el servicio de Icecast2 esté funcionando. Reemplaza `localhost` con la dirección IP pública de tu instancia AWS EC2 si estás probando desde una máquina remota. Asegúrate de que las contraseñas (`source-password` y `admin-password`) utilizadas en la configuración de Icecast2 coincidan con las credenciales que configuraste en el archivo `/etc/icecast2/icecast.xml`.

---

## Configuración de monitoreo

### 1. **Monitoreo de ancho de banda**  
   - Utilicé `vnstat` para monitorear el uso de ancho de banda por hora:
     ```bash
     vnstat -h
     ```
     ![Imagen de monitoreo de ancho de banda](./o.png)

---

## Enlace a Video

Para más información sobre la configuración de streaming de video, consulta el siguiente enlace:  
[Ir a Video.md](./video.md)