# EJERCICIO 2 - SERVIDOR DE BASE DE DATOS

> Realizado por Andrea Gómez Fueyo y Sandra Rujas

### **EJERCICIO 2 - Servidor de base de datos**

Abre Docker Desktop. Busca mariadb en la sección de imágenes. Selecciona la imagen oficial. Descárgala si no la tienes.

- Si no puedes iniciar sesión, la imagen puedes descargarla mediante comandos.

```bash
docker pull mariadb:latest
```

![image-20250214091505222](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214091505222.png)

![image-20250214091546138](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214091546138.png)

- Si puedes acceder a la búsqueda de imagen, entras en *“Images”*, buscas la última de maridb y pulsas pull para descargarla.

![image-20250214084549071](C:\Users\34615\AppData\Roaming\Typora\typora-user-images\image-20250214084549071.png)

- En la sección de imágenes, seleccionamos la que queremos utilizar, que en nuestro caso es la de mariadb, y pulsamos el botón de run:

![image-20250214085226093](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214085226093.png)

- Al darle al run, nos permite crear un nuevo contenedor:

![image-20250214085246315](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214085246315.png)

![image-20250214085316015](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214085316015.png)

Al cual le tenemos que poner las siguientes **características**:

- **Nombre del contenedor:** bbdd .

- **Puerto:** 3306 - debe poder conectarse externamente

- Utiliza un **volumen** llamado datos-mariadb .

- Usa las **variables de entorno** necesarias para que el usuario root tenga la password root , la base de datos por defecto sea base , y se cree un usuario daw , con password daw.

  ![image-20250214085359858](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214085359858.png)

- Arrancamos el contenedor:

![image-20250214085451842](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214085451842.png)

Una vez pulsado el RUN, nos vamos a la sección de contenedores para comprobar que finalmente se haya creado:

![image-20250214085524094](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214085524094.png)

Accede a la base de datos usando una herramienta gráfica, como, por ejemplo dbeaver . Conéctate con el usuario daw . Crea una base de datos y alguna tabla.

- Abrimos **DBeaver** y crear una nueva conexión a MariaDB:![image-20250214085612288](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214085612288.png)

- Configuramos la conexión:

  - **Host:** `localhost`
  - **Puerto:** `3306`
  - **Usuario:** `daw`
  - **Contraseña:** `daw`
  - **Base de datos:** `base`

  ![image-20250214085643470](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214085643470.png)

En la columna de la izquierda, podemos comprobar que se ha creado la conexión correctamente:

![image-20250214085706902](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214085706902.png)

- Creamos una tabla:

Hacemos click en el botón derecho y pulsamos en “Crear Nueva Columna” para agregar datos:

En *Table Name* introducimos el nombre de la tabla que queramos, en nuestro caso hemos elegido: “usuario”.

![image-20250214085753301](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214085753301.png)

Después hemos creado las columnas para añadir los atributos a nuestra tabla:

- Un **id:** que es un INT, AUTO_INCREMENT y PK.

  ![image-20250214085831780](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214085831780.png)

- Un **nombre**: que es un VARCHAR (25) y que no puede ser NULL.

  ![image-20250214085855564](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214085855564.png)

- Un **correo**: que es u VARCHAR de 50.

  ![image-20250214085930050](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214085930050.png)

Comprobamos la creación de la tabla:

![image-20250214085953457](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214085953457.png)

Una vez creada la tabla, intentamos borrar el contenedor:

- Vamos a la pestaña **"Containers"** y buscamos el contenedor bbdd:

  ![image-20250214090022356](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214090022356.png)

- Lo paramos y le damos a eliminar:

  ![image-20250214090059819](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214090059819.png)

![image-20250214090130612](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214090130612.png)

![image-20250214090245481](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214090245481.png)

Vemos como en Docker Desktop el volumen que contiene los datos no se ha borrado:

- Vamos a la pestaña **"Volumes"** en Docker Desktop. Buscamos datos-mariadb y verificar que sigue ahí:

![image-20250214090324805](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214090324805.png)



Creamos otro contenedor con un servidor de base de datos que use el mismo volumen:

- Llamamos al contenedor **bbdd-2** y utilizamos el mismo volumen que anteriormente:

![image-20250214090354545](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214090354545.png)

![image-20250214090418539](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214090418539.png)

Volvemos a **DBeaver** y creamos una nueva conexión a bbdd-2:

![image-20250214090442422](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214090442422.png)

Tras darle al botón de ‘Finalizar’, en la columna de la izquierda, podemos comprobar, que efectivamente, se ha creado una nueva conexión, que mantiene los datos que hemos introducido en el ejercicio anterior, es decir, la tabla de **usuarios** con sus correspondientes **columnas**:

![image-20250214090534361](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214090534361.png)

Seguidamente, vamos la pestaña de **“Images”** en Docker Desktop y buscamos mariadb e intentamos eliminarla:

![image-20250214090602343](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214090602343.png)

![image-20250214090622496](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214090622496.png)

**¿Qué sucede?**

En este caso podemos comprobar que no es posible su eliminación porque hay un contenedor en ejecución.

![image-20250214090643922](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214090643922.png)

Borramos todo, volumen, imagen y contenedor.

- Eliminamos el contenedor `bbdd-2` en **Docker Desktop**:

![image-20250214091125212](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214091125212.png)



- Vamos a la pestaña **"Volumes"** y borramos`datos-mariadb:`![image-20250214091032534](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214091032534.png)
- Y por último vamos a **"Images"** y eliminamos `mariadb:`

![image-20250214091233479](./EJERCICIO 2 - SERVIDOR DE BASE DE DATOS.assets/image-20250214091233479.png)

