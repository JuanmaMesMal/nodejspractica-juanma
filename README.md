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
    - Comprobamos
    ![Comprobamos versiones ](assets/img/comprobamos.png)
    -Borramos expres por si da fallos
    ![Borrar expres y instalarlo](assets/img/borramosexpress.png)
- Ya funcionaria y estaria la aplicacion escuchando por el puerto dicho "3000", para acceder tenemos que saber la ip y poner :3000
![Hello world](assets/img/Helloworld.png)
![Final Count](assets/img/finalcount.png)
![Final Count mas grande](assets/img/finalmasgrande.png)
-Vemos el tiempo que tarda, y a la vez abrimos otra pagina para ver como el valor sube 
![Tiempo del n mas grande](assets/img/tiempo1.png)
![Tiempo de la otra pagina](assets/img/tiempo2.png)
(Esto sucede porque la aplicación sin clúster se ejecuta en unico proceso.)

## Con cluster
- Creamos el archivo con nano y añadimos lo siguiente 
![Segunda App](assets/img/segundaapp.png)
- Ejecutamos la app 
![Ejecutamos segunda App](assets/img/Ejecutamos2app.png)
- Comprobamos otra vez los tiempos.
![Lenta](assets/img/lenta.png)
![Rapida](assets/img/rapida.png)
(Esto es debido a que se crean varios procesos workers que comparten el mismo puerto, y las peticiones se distribuyen entre ellos, permitinedo atender a multiples solicitudes evitando bloqueos)

## Metricas de rendimiento
-Instalamos loadtest
![Instalamos loadtest](assets/img/instalamosloadtest.png)
- comprobamos con "loadtest http://localhost:3000/api/500000 -n 1000 -c 100"
![Comprobamos load](assets/img/comprobamosload.png)
- Ahora lo comprobamos con mas solicitudes "loadtest http://localhost:3000/api/50000000 -n 1000 -c 100"
![Comprobamos load con mas solicitudes](assets/img/massolicitudes.png)

- Y ahora ejecutamos la otra aplicacion que si tiene clusters y ejecutamos lo mismo para ello usamos node "nombre de app con cluster" y comprobamos 
![Comprobamos load con cluster](assets/img/loadcloster1.png)
![Comprobamos load con cluster y mas solicitudes](assets/img/loadcloster2.png)

## Uso de PM2 para administrar un clúster de Node.js
- Necesitmos instalarnos pm2 usaremos el comando "npm install pm2 -g" y conprobamos
![Instalacion pm2](assets/img/pm2.png)
- Lo siguiente es iniciar la aplicaccion sin cluster
![Iniciamos pm2](assets/img/pm2sinclusterinicio.png)

- lo siguiente es descargarnos  pm2 ecosystme "pm2 ecosystem"
![Instalacion pm2 ecosystem](assets/img/instalamosecosystem.png)
- esto automaticamente nos crea un archivo "ecosystem.config.js" cual tenemos que configurar.
![Configuracion pm2 ecosystem](assets/img/configecosystem.png)
iniciamos
![iniciamos pm2 ecosystem](assets/img/iniciamoseco.png)
    - pm2 ls 
    ![pm2 ls](assets/img/pm2ls.png)
    - pm2 log
    ![pm2 logs](assets/img/pm2log.png)
    - pm2 monit
    ![pm2 logs](assets/img/pm2monit.png)

## Cuestionario 
¿Sabrías decir por qué en algunos casos concretos, como este, la aplicación sin clusterizar tiene
mejores resultados?

- En algunos casos la aplicación sin clúster funciona incluso mejor porque montar un clúster también tiene su trabajo. Al final hay que crear varios procesos y repartir las peticiones entre ellos, y eso consume recursos. Cuando las peticiones son rápidas y la CPU no está muy cargada, un solo proceso puede manejarlas sin problema y va más directo. Por eso, en situaciones así, usar varios workers no aporta gran cosa y la aplicación sin clúster puede rendir mejor.