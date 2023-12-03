# Practica3

## Objetivo.

El proposito de la practica era la simulacion de una maquina espendedora con el uso de arduino y varios componentes: un LCD, sensor ultrasonico, sensor de temperatura y humedad, boton, joystick y LED. Y simular varias funciones tales como; simular comprar un cafe, reiniciar el sistema, entrar en modo administrador pàra poder comprobar y modificar distintas funcionalidades de la maquina...

## Implementacion Hardware

Para la implemetnacion hardware se ha utilizado una protoboard, un LCD1602, un sensor de temperatura y humedad DHT11, un sensor ultrasonico HC-SR04, un joystick, un boton, un potenciometro y un LED. Para poder controlar el contraste de la pantalla LED he conectado la pantalla a un potenciometro para poder regularla. Los demás componentes eran simplemente seguir el orden de los pines.
![Powerful Kieran-Jaiks](https://github.com/Josetost/Practica3/assets/73531592/74e33af8-b934-4c1b-8178-9e901241ad7f)
## Implementacion Software.

La implementacion es una maquina de estados, que pasa entre los siguientes estados:


-SERVICIO: Este estado simplemente comprueba constantemente si hay un cliente, para ello usa las lecturas del sensor ultrasonico y si esta a menos de un metro pasa al siguiente estado.


-CLIENTE: En este estado primero muestra la temperatura y la humedad durante 5 segundos y posteriormente pasa a mostrar la lista de productos para poder seleccionar el que se desee. Una vez seleccionado el producto se pasa al siguiente estado.


-Preparando Cafe: Este estado simplemente controla la pantalla LED y el LED para informarnos de como va la creacion del cafe. En la pantalla aparecera preparando bebida mientras que el LED se ira iluminando poco a poco haciendo referencia al porcentaje que lleva realizado de la bebida.


-FINALIZANDO: Este último estado muestra por pantalla, durante 5 segundos, retire bebida y vuelve a pasar al estado SERVICIO.

Adicionalemnte hay un estado al cual sólo se puede acceder manteniendo presionado durante no menos de 5 segundos el boton, el estado ADMINISTRACION. En este estado podemos configurar distintas funcionalidades, además de ver el funcionamiento en tiempo real de los distintos sensores. Podemos modificar el precio de los productos y para salir de este estado necesitamos mantener de nuevo el boton durante mas de 5 segundos o entre 2 y 3 para reiniciar el sistema.

Estos estasdos se ejecutan en un único hilo que es el bucle de la funcion loop(), ademñas todas las lecturas de los sensores se manejan de manera sincrona por lo que cada función se ejecuta completamente antes de pasar a la siguiente.
