# Utiliza la imagen oficial de PHP con Apache como base
FROM php:7.4-apache

# Copia los archivos al contenedor
COPY index.html /var/www/html/
COPY styles.css /var/www/html/
COPY info.php /var/www/html/

# Expone el puerto 8000 para acceder al contenedor
EXPOSE 8000

# Configura Apache para escuchar en el puerto 8000
CMD ["apache2-foreground"]
