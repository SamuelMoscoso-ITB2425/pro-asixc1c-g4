# Introducció Video

## Instalación
En este documento, se describe el proceso de implementación de un servidor de streaming de video utilizando Icecast2 en un servidor Ubuntu alojado en AWS EC2.

1. **Preparación del software necesario**  
   - Instancia de Ubuntu Server 20.04/22.04 (tipo t2.large o c5)  
     ![Imagen de configuración de la instancia](../video pic/2.png)

     - Configuración del grupo de seguridad para permitir los puertos necesarios:
       - TCP 22 (SSH)
       - TCP 8000 (predeterminado de Icecast)
       - Puertos UDP para streaming  
       ![Imagen de configuración de puertos](../video pic/2.png)

     - Configuración de un nuevo par de claves  
       ![Imagen de configuración de claves](../video pic/3.png)

   - Configuración inicial del servidor:
     - Conexión a la instancia mediante SSH utilizando el par de claves  
       ![Imagen de conexión SSH](../video pic/4.png)

     - Actualización de los paquetes del sistema para la descarga  
       ![Imagen de actualización de paquetes](../video pic/5.png)

> **💡 Nota:**  
> Para estos pasos lo he hecho en la misma instancia, así que no tengo que configurar nada.

---

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
       ![Imagen de edición del archivo de configuración](../videop/6.png)

> **💡 Nota:**  
> Asegúrate de que la configuración de RTMP coincida con los requisitos de tu streaming. Verifica el puerto `listen` (1935) y otros ajustes para evitar problemas de conectividad.

   - Reinicié Nginx:
     ```bash
     sudo systemctl restart nginx
     sudo systemctl enable nginx
     ```
     ![Imagen de reinicio de Nginx](../videop/4.png)

   - Abrí los puertos necesarios:
     ```bash
     sudo ufw allow 8000/tcp
     sudo ufw allow 1935/tcp
     sudo ufw enable
     ```
     ![Imagen de configuración de puertos](../videop/1.png)

> **💡 Nota:**  
> Antes de configurar el fichero, verifica que tiene la línea `load_module modules/ngx_rtmp_module.so;` y también verifica que las reglas del firewall se hayan aplicado correctamente y que los puertos necesarios estén abiertos para el acceso externo.

---

3. **Subir archivo de prueba de video**  
   - Para subir mi archivo MP4 descargado desde local a AWS:
     ```bash
     scp -i nuevo_key.pem test.mp4 ubuntu@ec2-public-ip:/home/ubuntu/
     ```
     ![Imagen de subida de archivo](../videop/11.png)

     ![Imagen de configuración de puertos](../videop/5.png)

   - Comprobación de imagen desde AWS:  
     ![Imagen de comprobación desde AWS](../videop/12.png)

> **💡 Nota:**  
> Reemplaza `ec2-public-ip` con la dirección IP pública real de tu instancia AWS EC2. Asegúrate de que la ruta del archivo y los permisos sean correctos.

---

4. **Instalación de FFmpeg**  
   - Como no utilicé GStreamer y opté por FFmpeg:
     ```bash
     sudo apt install -y ffmpeg
     ```

---

## Verificación

1. **Prueba del stream de video**  
   - Para verificar si el stream estaba funcionando o no:
     ```bash
     ffmpeg -re -i test.mp4 -c copy -f flv rtmp://localhost/live/stream
     ```
     ![Imagen de prueba del stream](../videop/7.png)

   - Para comprobar, abrimos VLC y ponemos nuestra URL `rtmp://localhost/live/stream`:  
     ![Imagen de configuración de VLC](../videop/10.png)

     ![Imagen de configuración de VLC](../videop/8.png)

> **💡 Nota:**  
> Reemplaza `localhost` con la dirección IP pública de tu instancia AWS EC2 si estás probando desde una máquina remota. Asegúrate de que el comando FFmpeg coincida con los requisitos de tu streaming.

---

## Monitorización y pruebas

- Utilicé VLC estático para monitorización:  
  ![Imagen de monitorización estática](../videop/9.png)

## Enlace a Video
  
  Para más información sobre la configuración de streaming de video, consulta el siguiente enlace:  
  [Ir a audio.md](./audio.md)
