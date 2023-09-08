

# Configuración de conexión remota mediante  SSH entre Jetson Nano y computadora


## Tabla de Contenidos

1. [Comentarios generales](#Comentarios-generales)
2. [Configuración de la IP estática](#Configuración-de-la-IP-estática)
    1. [En la computadora](#En-la-computadora)
    2. [En la Jetson Nano](#En-la-Jetson-Nano)
3. [Prueba de conexión](#Prueba-de-conexión)
    1. [Solución al problema de transferencia de datos](#Solución-al-problema-de-transferencia-de-datos) 

       

## Comentarios generales
Para poder crear la conexión entre la computadora y la JETSON tenemos que tener claro que la IP cambian si es que no se tiene configurada una IP estática a lo que no no deja conectar en la siguiente conexión que se desea establecer. Primeramente se configuraran una IP estática tanto para la JETSON como para la computadora.
    

## Configuración de la IP estática 

### En la computadora 

 
**Seleccionar la red** a la que se desea conectar
(Si no te deja conectar a la que deseas por que tienes varias redes confirmadas entrar a la configuración de esa red y colocar que no se conecte de manera automática para que te permita ingresar de manera automática a la que deseas )



<p align='center'>
    <img src=./IMÁGENES/W1.png alt="drawing" width="600"/>
</p>



Ir a la terminal y ejecutar  
```
ifconfig  
```
<p align='center'>
    <img src=./IMÁGENES/W2.png alt="drawing" width="600"/>
</p>



En esta ventana nos mostrara la ip que se tiene asignada al dispositivo y la mascara 

Ahora ir a configuraciones de la red que nos conectamos y **pulsar en IPv4** 

<p align='center'>
    <img src=./IMÁGENES/W3.png alt="drawing" width="600"/>
</p>

Posteriormente **pulsar en la opción de Manual** 


<p align='center'>
    <img src=./IMÁGENES/W4.png alt="drawing" width="600"/>
</p>

**Colocar los siguientes datos**


- En dirección IP colocar la IP que anteriormente nos dio en la terminal.

- En mascara de red colocar la mascara que anteriormente nos dio en la terminal .

- En puerta de enlace colocar lo mismo que la dirección IP.



Una vez configurado esta parte se pulsa en **Aplicar** para aguardar cambios.



Posteriormente **reiniciamos la computadora** para que se aguarden los cambios y al reiniciarla nos dirijimos a la terminal e ingresamos el siguiente comando.

```
ifconfig
```

En esta parte debemos asegurarnos que nos dio la nueva IP que nosotros le asignamos al dispositivo 

<p align='center'>
    <img src=./IMÁGENES/W5.png alt="drawing" width="600"/>
</p>

### En la Jetson Nano


<p align='center'>
    <img src=./IMÁGENES/A01.png alt="drawing" width="500"/>
</p>




<p align='center'>
    <img src=./IMÁGENES/A02.png alt="drawing" width="500"/>
</p>






<p align='center'>
    <img src=./IMÁGENES/A03.png alt="drawing" width="500"/>
</p>






<p align='center'>
    <img src=./IMÁGENES/A06.png alt="drawing" width="500"/>
</p>


<p align='center'>
    <img src=./IMÁGENES/A07.png alt="drawing" width="500"/>
</p>



<p align='center'>
    <img src=./IMÁGENES/A08.png alt="drawing" width="500"/>
</p>


<p align='center'>
    <img src=./IMÁGENES/A09.png alt="drawing" width="500"/>
</p>
















## Prueba de conexión  

Ir a la teminal y ejecutar 

```
export ROS_MASTER_URI=http://localhost:11311
export ROS_IP=localhost
```

En nuestro caso ejecutamos
```
export ROS_MASTER_URI=http://192.168.43.178:11311
export ROS_IP=192.168.63.188

```

### Solución al problema de transferencia de datos

rostopic list 





## 1 Configuraciones en la JETSON
#--------------------------------------------------------------------------
#....................

 Configurar el host
   En la terminal ejecutar

```
sudo gedit hosts
```
   Una vez despliega un archivo se configura de la manera siguiente. 
```
export ROS_MASTER_URI=http://localhost:11311
export ROS_IP=localhost
export ROS_HOSTNAME=TurtlebootIP o TurtlebootHOSNAME
```
```
export ROS_MASTER_URI=http://192.168.43.178:11311
export ROS_IP=192.168.43.178
export ROS_HOSTNAME=192.168.43.178
```

## 2 Configuraciones en la Computadota 

<p align='center'>
    <img src=./IMÁGENES/W1.png alt="drawing" width="600"/>
</p>
```
sudo gedit hosts
```
   Una vez despliega un archivo se configura de la manera siguiente. 

```
export ROS_MASTER_URI=http://TurtlebootIP:11311
 export ROS_IP=192.168.43.192 
ssh robotica@hostNmae(ipconfig)
```

```
export ROS_MASTER_URI=http://192.168.43.178:11311
 export ROS_IP=192.168.43.192 
ssh robotica@192.168.43.178
```
