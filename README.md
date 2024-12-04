# control

![termal recta](https://github.com/user-attachments/assets/0c3858fe-15f0-4dcc-89b9-bb427df5d2f5)
a.Este modelo no muestra que haya partes especialmente difíciles de controlar, porque no hay cambios bruscos ni saltos. Pero en un sistema real, cosas como los retrasos, comportamientos inesperados o límites en la capacidad de ajuste pueden hacer que sea más difícil controlar la temperatura. Es como si el modelo fuera más simple que la realidad, donde esos problemas extra pueden complicar las cosas.

b.La gráfica representa un análisis estático, es decir, en estado estacionario.En este caso, la ganancia α domina el comportamiento del sistema y puede asumirse como constante.

c. se despeja u_(ee) de la ecuacion y eso da alrededor del 23,5% por lo que la señal de control disponible para compensar la temperatura es al rededor de 76,5%
![termal2](https://github.com/user-attachments/assets/ba50a638-39fd-43c7-b68b-4ac3f9fa4254)
#  respuesta experimental normalizada
![termal4](https://github.com/user-attachments/assets/a129d094-fab7-4dc4-8a3e-d2a5f4c187bb)
![termal5](https://github.com/user-attachments/assets/8a928872-a26e-46ad-8b2d-8c562c6a5ea7)
![termal6_50](https://github.com/user-attachments/assets/cde16d27-3571-4c6c-a9fb-c20238badfd8)
![termal7_60](https://github.com/user-attachments/assets/535d973c-16bf-4f12-b8e9-54aed0e9b29e)
![termal8_80](https://github.com/user-attachments/assets/e8fe5bb9-52d6-4992-9dae-4dfbeda7a750)


![lab1_a_motor der_izq](https://github.com/user-attachments/assets/6718b32a-3ffe-41bd-a95f-c8d27b96e564)
a. zona muerta del motor es la región alrededor de 0V en la cual el motor no responde significativamente a la entrada de voltaje. Esto ocurre debido a cosas como el rozamiento estático o las características del controlador del motor.

b.principalmente creemos que es dificil controlar en 2 zonas , la primera la zona muerta del motor, otra seria despues de los limites maximos ya que en este punto alcanza una saturacion .

c.el motor es controlable dentro de su region lineal , esto se ve en la grafica entre mas o menos por encima de  -600 deg/sy por debajo de  600 deg/s

d.El parámetro t es aproximadamente la pendiente de la curva por ende hay una sección de la curva que si presenta la linealidad de la curva  es muy cercana a la pendiente, en cambio en la parte no lineal esta pendiente varia.

![lab1_a_motor_150](https://github.com/user-attachments/assets/c5554036-175f-4321-bcef-c7ec1441da94)
![lab1_a_motor_300](https://github.com/user-attachments/assets/7c7da14a-2c32-44a6-b3ab-7337b853ca2f)
![lab1_a_motor_600](https://github.com/user-attachments/assets/7f0dc7d4-1b1e-417b-8fc0-85aedf53835a)
a.la constante de tiempo disminuye a medida de que aumenta la 

b.Se requeriría un sistema mas complejo el cual pueda manejar esta velocidad pero así mismo las variaciones principalmente en el eje y serian menores lo que haría que la aproximación sea mucho mas cercana a los datos obtenidos

c.Esta constante si aumenta al incrementar la velocidad del motor

d.reducir la incertidumbre implica agregar estabilidad frente a los datos obtenidos en comparación con los datos aproximados y se podría parametrizar mejor el sistema 

e.Las variables tiene un comportamiento similar sin embargo el orden de magnitud es distinto , específicamente para el parámetro t es aproximadamente 100 veces mayor que en el sistema térmico por ende también las incertidumbres deberían tener un rango acorde a la escala de t lo que implica que las incertidumbres en el sistema del motor sean mucho menores con respecto a las del sistema térmico y esto aplica para todos los casos probados


#sintonia de PID

![lab1_b_termal_metodoah](https://github.com/user-attachments/assets/26a6cf61-e5fa-4c25-8ea5-0f9e2047bf10)


![lab1_b_termal_metodoSK](https://github.com/user-attachments/assets/e1b99e3a-8dcd-4e1e-8e66-2e336ab3908b)

![lab1_b_termal_metodota](https://github.com/user-attachments/assets/fb3e7e33-0551-460e-8fd8-f4a5e41af1a2)
### Trabajo experimental con el sistema térmico

Realice los siguientes experimentos con un escalón que cambia desde `r0=50` a `r1=60`.  Para los 2 experimentos use nombres diferentes en las variables de salida para poder después graficarlos conjuntamente. Por ejemplo, para el experimento 1 (valores de Skogestad) puede usar:

`t_sk, r_sk, y_sk, u_sk = temp.step_closed(mi_termico,r0=r0, r1=r1, t0=t0, t1=t1)`


1. Sintonice un controlador PI por el método de Skogestad y obtenga la respuesta al escalón en lazo cerrado.

1. Sintonice un controlador PI por el método de Åström and Hägglund y obtenga la respuesta al escalón en lazo cerrado.
![lab1_b_termal_unidas](https://github.com/user-attachments/assets/8e2c53dc-4983-4e83-8696-acd17def9346)
a. Asignándole orden a los métodos de mejor a peor el orden seria 
1.taguchi y araki
2.skogestad
3.ziegler-nichols
4.astrom  y h


b.el método de zieger nichols es el menos robusto de los tres primeros métodos por 
ende no es recomendable.



