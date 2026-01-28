# Desplliegue de una aplicacion en cluster con NodeJS y Express
    - Lo primero que vamos ha hacer es intalar nodejs ya que no esta instalado.
![Instalar Node.js](assets/img/instalarnodejs.png)

## Sin cluster
- Creamos una carpeta para el proyecto, luego lo iniciamos con npm init para crear una estructura de carpetas automaticamente y el archivo packega.json.
![Creamos carpeta y hacemos un init](assets/img/init.png)
- Lo siguiente es hacer un npm install expres para instalarlo para el proyecto 
![Descargamos Express](assets/img/express.png)
- Despues de esto creamos con nano un archivo para la aplicacion.js y añadimos lo siguiente y ejecutamos node "nombre de nuestra applicación"
![Datos de la aplicación](assets/img/aplicacionDatos.png)
- En este momento me sale un error, que sucede por que la instalacion de node es una version antigua y los datos dentro de la aplicacion necesitan un node mas moderno, para esto tenemos que hacer lo siguiente
    - Borrar node.
    ![Borrar Node](assets/img/BorrarNode.png)
    - Reinstalarlo, con una version mas actual 
    ![Reinstalar](assets/img/Reinstalar.png)
