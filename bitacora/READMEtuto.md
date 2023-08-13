# Describiendo el proceso de pasar la aplicacion hecha con react

This project was builded using react

## Generar una buil de produccion

In the project directory, you can run:

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

---
---
## Genera una Build de Producción:
Antes de llevar tu aplicación a producción, debes generar una versión optimizada para producción. Esto se logra utilizando el comando npm run build. Este comando creará una carpeta llamada build en la raíz de tu proyecto con los archivos optimizados para el despliegue.

## Configura Nginx:
En tu servidor de producción, debes instalar y configurar Nginx. Si no lo tienes instalado, puedes hacerlo utilizando el gestor de paquetes de tu sistema operativo.

## Copia los Archivos al Servidor:
Copia los archivos generados en la carpeta build a la ubicación donde Nginx servirá tu aplicación. Esto suele ser en la carpeta /var/www/html o una ruta similar, dependiendo de tu configuración de Nginx.

## Configura el Archivo de Configuración de Nginx:
Crea un archivo de configuración para tu aplicación en Nginx. Por lo general, estos archivos tienen la extensión .conf y se encuentran en la carpeta /etc/nginx/conf.d/. Aquí tienes un ejemplo de configuración:

nginx
Copy code
server {
    listen 80;
    server_name tu-domino.com;

    location / {
        root /var/www/html/tu-carpeta-de-app;
        index index.html;
        try_files $uri /index.html;
    }
}
Asegúrate de reemplazar tu-domino.com con tu dominio real y tu-carpeta-de-app con la carpeta donde copiaste los archivos de la build.

## Reinicia Nginx:
Una vez que hayas creado la configuración, reinicia Nginx para aplicar los cambios. Puedes hacerlo ejecutando sudo service nginx restart o el comando equivalente en tu sistema operativo.

## Configuración DNS:
Si estás utilizando un dominio personalizado, asegúrate de que el DNS esté configurado correctamente para apuntar al servidor donde está alojada tu aplicación.

## SSL (Opcional pero Recomendado):
Si planeas usar HTTPS (lo cual es muy recomendable), deberás configurar certificados SSL en tu servidor Nginx para habilitar la conexión segura. Puedes obtener certificados gratuitos de Let's Encrypt.

## Monitorización y Mantenimiento:
Una vez que tu aplicación esté en producción, asegúrate de tener un plan para monitorear el rendimiento y la salud de tu servidor. Considera implementar herramientas de monitorización y establece un proceso de actualización y mantenimiento regular.

Siguiendo estos pasos, deberías ser capaz de llevar tu aplicación de React desde el entorno de desarrollo a un servidor web Nginx en producción de manera exitosa. Recuerda que estos son solo pasos generales y pueden variar dependiendo de tu configuración específica y del sistema operativo que estés utilizando en tu servidor.