
# Configuraciones

### Topología 1
![Imagen](https://github.com/Abner-Hernandez/Redes1-Practica5_201612101/blob/main/img/topologia1.PNG)

### Topología 2
![Imagen](https://github.com/Abner-Hernandez/Redes1-Practica5_201612101/blob/main/img/topologia2.PNG)

## Configuración VPN

### Configuración pc 1
* Puerto local: 30001
* Puerto Remoto: 50002
* IP de la pc 2: 10.8.0.3

![Imagen](https://github.com/Abner-Hernandez/Redes1-Practica5_201612101/blob/main/img/cloud.PNG)

* Configurar el ruteo dinamico RIP para la comunicación de los routers a travez de la vpn

![Imagen](https://github.com/Abner-Hernandez/Redes1-Practica5_201612101/blob/main/img/r2_rip.PNG)

* Validando configuraciones RIP

![Imagen](https://github.com/Abner-Hernandez/Redes1-Practica5_201612101/blob/main/img/r2_rip_sh.PNG)

### Configuración pc 2
* Puerto local: 50002
* Puerto Remoto: 30001
* IP de la pc 1: 10.8.0.2

![Imagen](https://github.com/Abner-Hernandez/Redes1-Practica5_201612101/blob/main/img/pc2_nube.PNG)

* Configurar el ruteo dinamico RIP para la comunicación de los routers a travez de la vpn

![Imagen](https://github.com/Abner-Hernandez/Redes1-Practica5_201612101/blob/main/img/r2_rip.PNG)

* Validando configuraciones RIP

![Imagen](https://github.com/Abner-Hernandez/Redes1-Practica5_201612101/blob/main/img/r2_rip_sh.PNG)

## Captura de paquetes

### Captura de paquetes en pc1
![Imagen](https://github.com/Abner-Hernandez/Redes1-Practica5_201612101/blob/main/img/captura_paquetes2.PNG)

### Captura de paquetes en pc2
![Imagen](https://github.com/Abner-Hernandez/Redes1-Practica5_201612101/blob/main/img/captura_paquetes.PNG)

## Cálculo de Subredes
Para poder crear subredes óptimas para nuestra red se realizó uso de vlsm dado que contábamos con una red original con capacidad de 256 host y necesitábamos que fuese dividida en subredes que se ajustaran a cada departamento según su necesidad.


Para el departamento de Profesores necesitábamos disponibilidad para 35 Equipos, el departamento de estudiantes requiere disponibilidad para 65 estudiantes, con estos datos proporcionados, podemos crear dichas subredes.


Primero ordenamos de mayor a menor la cantidad de host que necesita cada subred y luego comenzamos a realizar el cálculo para el cálculo de las subredes,en este caso comenzamos a trabajar con la subred que necesita 65 equipos disponibles. utilizamos la siguiente ecuación:  2^n -2 >= # host requeridos, si usamos n = 6 podemos ver que encontramos una cantidad menor de host a los requeridos 2^7 -2 = 62, por lo que usaremos n = 7, 2^7 -2 = 126 >= 65, con esto empezaremos a calcular la máscara de red, n nos indicará el número de bits apagados de los 32 bits que cuenta una máscara en este caso. 11111111.11111111.11111111.1000000 en números decimales obtenemos 255.255.255.128/25. sabemos que nuestra red comenzaria en 192.168.0.0 y también está será nuestra dirección de red. la siguiente ip será nuestra primera ip asignable para nuestros host 192.168.0.0 , tenemos un total de 126 host por lo que la última ip asignable será 192.168.0.126, y la siguiente ip sería nuestra dirección de broadcast.
La siguiente subred que necesitamos debe contar con 35 host, en este caso con prueba y error, encontrando que n = 6 , dando como resultado 2^6 -2 = 62 >= 35, sabemos que necesitamos 6 bits apagados, 11111111.11111111.11111111.1100000 cuyo equivalente en decimales será 255.255.255.192/26, en este caso empezamos un número despues de la dirección de broadcast de la subred anterior. en este caso sería 192.168.0.128, la primera ip asignable sería la siguiente 192.168.0.129 y la última la obtenemos sumando el número de host que nos da la ecuación en este caso es 62, cuyo resultado es 192.168.0.190, la dirección de broadcast entonces es la siguiente ip 192.168.0.191.




