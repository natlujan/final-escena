----------------------------------- 
# Abstract
 ----------------------------------- 

En este proyecto se realizarán los objetivos, puntos a seguir y métodos que se fue aprendiendo sobre Shaders enseñándos a lo largo de la materia. Así como distintos modelos de luz, ambientaciones, simulado de viento, animación de agua, vertex shading, etc. 


----------------------------------- 
# Introducción 
----------------------------------- 

Con la ayuda de Unity y sus herramientas nos dimos a la tarea de poder realizar un proyecto de Shader Graph, creando una ambientación con objetos y entorno. Buscando así un escenario divertido que tenga objetos como rocas, plantas, personajes y montañas. Probamos modelos de luz custom, agregamos vegetación y movimiento de esta. Añadimos agua y su simulación de movimiento para crear realismo Vertex shading. 

----------------------------------- 
# Desarrollo 
----------------------------------- 

Inicio de proyecto Unity. 

Comenzamos creando un proyecto de Unity limpio con el procedimiento que siempre aplicamos básico. Creamos la escena principal donde se llevará a cabo en sí todo el proyecto, creamos los shaders ordenándolos en sus carpetas para poder así utilizarlos a continuación.



Creación del pasto en movimiento (Flower). 

![image](https://user-images.githubusercontent.com/69810414/119700438-0fdba200-be08-11eb-9c20-5720abb61f48.png)

En este shader se comienzan a crear distintas variables con sus propiedades correspondientes. Se crea un Albedo que será el color base. Normal Intensity que es para regular la textura. Wind Intensity este como dice el nombre es para controlar la intensidad del viento. Noise Intensity que es para poder regular y controlar el ruido de la textura en cuanto a deformación. 
 

Aún con todo esto no se tendrá todavía movimiento en el pasto o palmera, para esto se necesitará crear un control de velocidad de viento y manejo de tiempo, por lo que se usa Tiling and Offset, donde sus entradas son las de Position y un producto de la variable Wind Speed con el tiempo. Todo esto se conecta a un Gradient noise, donde la escala también está enlazada con la variable Noise Density que pasa por un Subtract y se multiplica con la variable de Wind Intensity.

Una vez realizado esto usamos la posición del modelo, y se separan los ejes X, Y y Z. El eje X pasa a un Add, donde se suma con el ruido creado anteriormente, que es lo que causa que se mueva el shader en eje X, mientras que el eje Y y el eje Z se mantienen igual. Cuando se tiene todo se combinan los ejes para ser un Lerp, que tiene como entradas la posición del modelo junto con la variable Y del UV. Todo esto pasa a un Transform de tipo world, la salida se enlaza con el nodo Position (3) de Vertex.

 ![image](https://user-images.githubusercontent.com/69810414/119700571-3ac5f600-be08-11eb-9945-2c279edb38da.png)

![image](https://user-images.githubusercontent.com/69810414/119700687-5fba6900-be08-11eb-8e50-b5cf37aada47.png)

 

La creación del Agua. 

![image](https://user-images.githubusercontent.com/69810414/119700792-81b3eb80-be08-11eb-9bb4-95879ddda598.png)


En la creación de Agua y sus respectivas propiedades de movimiento. Se crearon distintas variables, la llamada Depth para el control de la profundidad. Dos vectores más para la distinta tonalidad del agua si está cerca de la orilla sería un Clean Water, y si está lejos será un Dark Water. Normal que será la textura normal. Strength que es para controlar la fuerza del movimiento de las olas. Displacement para el control de la marea y para finalizar el Smooth que es el brillo del agua. 

 

Toon Shading Creamos dentro de la carpeta de shaders un grafo de Shader Graph. Dentro crearemos el nodo de color, agregamos el Dabs que nos ayuda a dar contornos al Toon Shading. Agregamos un Hlsl llamado Direct Specular con sus smooth, Specular, Direction y Color. Todo esto se conectó con la el Main Light. Todo esto dará un efecto como de mala calidad queriendo dar la sensación de cartoon.


 
![image](https://user-images.githubusercontent.com/69810414/119700813-89739000-be08-11eb-9585-5d0519bbf694.png)




----------------------------------- 
# Conclusión 
----------------------------------- 

Al final del proyecto llegamos a tener una escena con sus ambientaciones que queríamos, todo utilizando los modelos de luz, simulaciones de viento y agua daba un efecto bastante grato y quedamos satisfechos con el resultado. Creemos que faltan muchos detalles a afinar para la mejora del proyecto pero se aprendió el manejo y creación de cada uno de los efectos y puntos que fuimos añadiendo al proyecto. 

 ![image](https://user-images.githubusercontent.com/69810414/119700909-a4de9b00-be08-11eb-8231-f9a44fb0f986.png)

 
![image](https://user-images.githubusercontent.com/69810414/119700927-a90ab880-be08-11eb-9b9c-81ad411d1dbe.png)





----------------------------------- 
# Integrantes
 ----------------------------------- 
Natalia Luján Chávez
Rodolfo Vega Oros 
Robin Ivan Perez Gonzalez

----------------------------------- 
# Referencias
 ----------------------------------- 

- SnutiHQ - ToonShading o Celshading effect https://unitylist.com/p/sp9/Toon-Shader 
- Erik Roystan Ross Outline Shader https://roystan.net/articles/outline-shader.html 
- PATRYK GALACH Toon Shading with Unity Shader Graph https://www.patrykgalach.com/2020/09/14/toon-shading-with-unity-shader-graph/
- Erik Roystan Ross Toon Water Shader https://roystan.net/articles/toon-water.html 
- Linden Reid Waving Grass Shader in Unity https://lindenreid.wordpress.com/2018/01/07/waving-grass-shader-in-unity/ 
- Wind Animated Grass In Shader Graph Using Meshes! https://game-developers.org/wind-animated-grass-in-shader-graph-using-meshes-unity-urp-game-dev-tutorial/ 
- Single Step Toon Light https://www.ronja-tutorials.com/post/031-single-step-toon/ 
- Custom Lighting in Shader Graph https://blog.unity.com/technology/custom-lighting-in-shader-graph-expanding-your-graphs-in-2019 
- Strix - DirectX 11 Grass Shader https://forum.unity.com/threads/get-main-light-position.811071/ 
- Assets Shader https://docs.unity3d.com/es/530/Manual/class-Shader.html 
- Paulina Miciuleviciute Water Shader https://www.paulinami.com/water-shader-urp-amplify 
- Creating Water With Shader Graph In Unity| 2D Shader Basics https://www.cgtutes.com/water-shader-graph-unity/

