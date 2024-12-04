# control

![termal recta](https://github.com/user-attachments/assets/0c3858fe-15f0-4dcc-89b9-bb427df5d2f5)
### Preguntas orientadoras sobre el modelo estático

Por favor discuta las preguntas con su compañero inmediatamente durante la práctica y respondalas en su videoinforme 

1.  Considere que el rango de operación va desde  $40^oC$ hasta $100^oC$. ¿Existen temperaturas en este rango más dificiles de controlar, según el modelo estático?
2.  Suponga que un modelo aproximado del sistema térmico está dado por $G(s)=\frac{\alpha}{\tau\,s+1}$. ¿Cual de los parámetros ($\alpha$ o $\tau$) podriamos asumir como aproximadamente constante, según la curva del modelo estático?
3.  ¿Cual es la señal de control necesaria para controlar una temperatura cercana a $60^oC$ y cuanto nos queda de acción de control si tenemos que compensar una temperatura muy fria que actúa como perturbación?

respuestas

1.Este modelo no muestra que haya partes especialmente difíciles de controlar, porque no hay cambios bruscos ni saltos. Pero en un sistema real, cosas como los retrasos, comportamientos inesperados o límites en la capacidad de ajuste pueden hacer que sea más difícil controlar la temperatura. Es como si el modelo fuera más simple que la realidad, donde esos problemas extra pueden complicar las cosas.

2.La gráfica representa un análisis estático, es decir, en estado estacionario.En este caso, la ganancia α domina el comportamiento del sistema y puede asumirse como constante.

3. se despeja u_(ee) de la ecuacion y eso da alrededor del 23,5% por lo que la señal de control disponible para compensar la temperatura es al rededor de 76,5%

#### Paso 1

Encuentre $y_a$ gráficamente o como el promedio de $N$ puntos antes del cambio del escalón y $y_b$ como el promedio de los últimos $N$ puntos registrados en la respuesta al escalón. 

Establezca el valor de $u_a$ y $u_b$.
![termal2](https://github.com/user-attachments/assets/ba50a638-39fd-43c7-b68b-4ac3f9fa4254)

#### Paso 2

Con los datos experimentales, encuentre y grafique la respuesta experimental normalizada $\overline{y}(t)$ del sistema por medio de siguiente ecuación:

 $$\overline{y}(t) = \frac{y(t)-y_a}{\Delta\,y}$$
 
![termal4](https://github.com/user-attachments/assets/a129d094-fab7-4dc4-8a3e-d2a5f4c187bb)

#### Paso 3

Encuentre por medio de interpolación numérica de la curva experimental los valores de tiempo $t_1, t_2$ en los cuales la respuesta experimental normalizada $\overline{y}(t)$ alcanza dos valores en la zona inicial de máxima pendiente de la curva, en la cual $\overline{y}(t)\leq 0.5$.

Por ejemplo, $\overline{y}_1=0.05$ y $\overline{y}_2=0.3$.

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
### Otros métodos de sintonía 

Existen una infinidad de métodos de sintonía. Con base en propuesta original de Ziegler y Nichols han seguido apareciendo nuevas propuestas de sintonía que preservan la filosofía del método original en cuanto a su simplicidad (solo se requiere hacer un modelo aproximado de primer orden del proceso). La tabla siguiente contiene algunos métodos de sintonización reportados en la literatura para controladores PI.

| **Propuesto por** | **Ganancia Proporcional** $k_p$                | **Ganancia Integral** $k_i$                | 
|-------------------------|------------------------------------------------|--------------------------------------------|
| **Skogestad (2003)**           |   $\dfrac{0.5\,\tau}{\alpha\,L}$   | $\min(\tau, 8\,L)$ |
| **Taguchi y Araki (2000)**           |   $\dfrac{0.1787 + \dfrac{0.2839}{\dfrac{L}{\tau} + 0.001723}}{\alpha}$  | $\dfrac{k_p}{4.296 + 3.794 \cdot \dfrac{L}{\tau} + 0.2591 \cdot \left(\dfrac{L}{\tau}\right)^2}$|
|**Åström and Hägglund (2006)**                | $\dfrac{0.15}{\alpha} + \left(0.35 - \dfrac{L \cdot \tau}{(L + \tau)^2}\right) \dfrac{\tau}{\alpha \cdot L} $               |  $\dfrac{k_p}{0.35 \cdot L + \frac{13 \cdot L \cdot \tau^2}{\tau^2 + 12 \cdot L \cdot \tau + 7 \cdot L^2}}$   |

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

+ ¿Cuánto demora aproximadamente el controlador PI programado en rechazar la perturbación de temperatura producida por la mano?

-demora alrededor de 5 segundos en estabilizarse con una pequeña fluctuación

#### Pregunta

Según este experimento y los anteriores, ¿Cuál es la mayor limitación de usar solo acción proporcional **P** y cual es la mejora fundamental que introduce la acción integral dada por el controlador **PI**?


-p el proporcional es solo la ganancia, y el pi es considerar la integración por tanto considera también el erro por encima del valor objetivo por ende este modelo pi es mejor por que evita sobrepasarse del valor objetivo



### Experimentos propuestos

Realice los siguientes experimentos con un escalón de referencia de velocidad que cambia desde `r0=0` a `r1=360`.  Para los 2 experimentos use nombres diferentes en las variables de salida para después poderlos graficar conjuntamente.


1. Sintonice un controlador PI por el método de Taguchi y Araki y obtenga la respuesta de lazo cerrado

1. Sintonice un controlador PI por el método de Åström and Hägglund y obtenga la respuesta de lazo cerrado


#### Pregunta

+ Grafique en una misma gráfica la respuesta de los 3 experimentos de sintonia (Ziegler-Nichols, Taguchi y Araki, Åström and Hägglund).
![POR SIACASO](https://github.com/user-attachments/assets/3156cef7-a23f-4da4-8456-0ecc5563257c)


### Experimento sensorial de robustez a perturbaciones

Realice conjuntamente con su colega los siguientes pasos para probar tactilmente la robustez a perturbaciones que posee cada controlador PI sintonizado. 

+ **Paso 1:** Ajuste la perilla del encoder con el indicador apuntando como se muestra en la figura. 

<img src="https://github.com/nebisman/UNThermal/blob/main/code/python_code/notebooks_lab_2024_2/motor0deg.png?raw=true" alt="PID" width="200"/>

+ **Paso 2:** Programe el controlador PI con la función `set_pid()` usando uno de los 3 métodos de sintonía. No es necesario obtener la respuesta al escalón. Esto lo haremos sensorialmente.
  


+ **Paso 3:** Ajuste una velocidad de $90^o/s$ mediante la posición de la perilla indicada en la figura siguiente:

<img src="https://github.com/nebisman/UNThermal/blob/main/code/python_code/notebooks_lab_2024_2/motor90deg.png?raw=true" alt="PID" width="200"/>

+ **Paso 4:** Intente acelerar o frenar suavemente el motor con la mano, percibiendo el rechazo del controlador a la perturbación impuesta. 

+ **Probar todos** Repita los pasos 1 a 4 para los 3 controladores PI, es decir para el sintonizado por las reglas de Ziegler-Nichols; de Taguchi y Araki; y, de Skogestad.  
