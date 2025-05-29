# Video

## Instalación
En este documento, se describe el proceso de implementación de un servidor de streaming de video utilizando Icecast2 en un servidor Ubuntu alojado en AWS EC2.

1. **Preparación del software necesario**  
   - Instancia de Ubuntu Server 20.04/22.04 (tipo t2.large o c5) 
     - Configuración del grupo de seguridad para permitir los puertos necesarios:
       - TCP 22 (SSH)
       - TCP 8000 (predeterminado de Icecast)
       - Puertos UDP para streaming
     - Configuración de un nuevo par de claves

   - Configuración inicial del servidor:
     - Conexión a la instancia mediante SSH utilizando el par de claves
     - Actualización de los paquetes del sistema para la descarga

2. **Instalación y configuración de Nginx**  
   - Para instalar Nginx, utilicé el comando:
     ```bash
     sudo apt install -y libnginx-mod-rtmp nginx
     ```
   - Edición del archivo de configuración:
     - Para configurar, edité el archivo `/etc/nginx/nginx.conf` y añadí RTMP:
       ```bash
       rtmp {
         server {
           listen 1935;
           chunk_size 4096;
           allow publish all;
           allow play all;

           application live {
             live on;
             record off;
             meta copy;
           }
         }
       }
       ```

> **💡 Nota:**  
> Asegúrate de que la configuración de RTMP coincida con los requisitos de tu streaming. Verifica el puerto `listen` (1935) y otros ajustes para evitar problemas de conectividad.

   - Reinicié Nginx:
     ```bash
     sudo systemctl restart nginx
     sudo systemctl enable nginx
     ```
   - Abrí los puertos necesarios:
     ```bash
     sudo ufw allow 8000/tcp
     sudo ufw allow 1935/tcp
     sudo ufw enable
     ```

> **💡 Nota:**  
> Verifica que las reglas del firewall se hayan aplicado correctamente y que los puertos necesarios estén abiertos para el acceso externo.

3. **Subir archivo de prueba de audio**  
   - Para subir mi archivo MP4 descargado desde local a AWS:
     ```bash
     scp -i nuevo_key.pem test.mp4 ubuntu@ec2-public-ip:/home/ubuntu/
     ```

> **💡 Nota:**  
> Reemplaza `ec2-public-ip` con la dirección IP pública real de tu instancia AWS EC2. Asegúrate de que la ruta del archivo y los permisos sean correctos.

4. **Instalación de FFmpeg**  
   - Como no utilicé GStreamer y opté por FFmpeg:
     ```bash
     sudo apt install -y ffmpeg
     ```

---

## Verificación

1. **Prueba del stream de audio**  
   - Para verificar si el stream estaba funcionando o no:
     ```bash
     ffmpeg -re -i test.mp4 -c copy -f flv rtmp://localhost/live/stream
     ```

> **💡 Nota:**  
> Reemplaza `localhost` con la dirección IP pública de tu instancia AWS EC2 si estás probando desde una máquina remota. Asegúrate de que el comando FFmpeg coincida con los requisitos de tu streaming.

---

## Monitorización y pruebas

- Utilicé `vnstat` para monitorear el uso de ancho de banda por hora:
  ```bash
  vnstat -h