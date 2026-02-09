<!--
Posible prompt:
<prompt>
Tengo un cuestionario con preguntas sobre "Encapsulación". Debes tener en cuenta que los conocimientos previos que tengo (y por tanto tus respuestas deben ser adaptadas), son:
- C/C++ sin orientación a objetos.
- Temas de Java previos: Clases y Objetos.

Cada respuesta debe tener entre 2 - 4 párrafos de longitud (sin contar los trozos de código).

Por favor, escribe en impersonal las respuestas.

</prompt>
----
-->
# TEMA 2. Encapsulación

## 1. En Programación Orientada a Objetos (POO), ¿Qué buscan la **encapsulación** y **la ocultación** de información? Enumera brevemente algunas ventajas de la ocultación de información.


### En el paradigma estructurado de C, es común acceder y modificar directamente los campos de una estructura (struct), lo que expone la representación interna de los datos a todo el programa y crea una fuerte dependencia entre cómo se guardan los datos y cómo se usan. La encapsulación y la ocultación de información en Java buscan transformar este modelo en uno de "caja negra", donde los detalles internos (los atributos y la lógica compleja) permanecen invisibles e inaccesibles desde el exterior. El objetivo fundamental es separar la interfaz (qué puede hacer el objeto, definido por sus métodos públicos) de la implementación (cómo lo hace, definido por su código interno y datos privados).

### Al ocultar la información mediante modificadores de acceso (como private), se impide que otros objetos o partes del programa manipulen el estado interno de un objeto de manera arbitraria o imprevista, protegiendo la integridad de los datos. Esto contrasta con la programación en C, donde cualquier función con acceso a una estructura podría alterar sus valores sin restricciones, pudiendo asignar datos inválidos. En la POO, se busca garantizar que el objeto sea el único responsable de gestionar sus propios datos, asegurando que siempre se encuentre en un estado válido y consistente.

### Algunas ventajas clave de la ocultación de información son:

### Facilidad de mantenimiento: Permite modificar la estructura interna de la clase o la lógica de sus métodos (por ejemplo, optimizar un algoritmo o cambiar un tipo de dato interno) sin que ello afecte al resto del código que utiliza dicha clase, siempre y cuando no se modifique la firma de los métodos públicos.

### Control y validación: Al obligar a pasar por métodos para modificar datos, se pueden introducir validaciones (como asegurar que una edad no sea negativa) antes de realizar la asignación, evitando errores lógicos difíciles de rastrear.

### Modularidad y desacoplamiento: Reduce la dependencia entre distintas partes del sistema. Si una clase cambia internamente, el error se contiene dentro de ella y no se propaga automáticamente a otras partes del programa que la consumen. 

## 2. ¿Qué se entiende por la **interfaz pública** de un objeto o clase en POO? Describe brevemente cómo se relaciona con la ocultación de información.

### Se entiende por interfaz pública al conjunto de métodos (y ocasionalmente constantes) que una clase expone abiertamente para que sean utilizados por otras partes del programa. Estos miembros se marcan con el modificador de acceso public. En términos de C, se podría comparar la interfaz pública con los prototipos de funciones declarados en un archivo de cabecera (.h); estos prototipos anuncian qué operaciones están disponibles para ser invocadas por otros módulos, definiendo cómo interactuar con una librería sin necesidad de exponer el código fuente de la implementación (el archivo .c).

### La relación con la ocultación de información es fundamental y complementaria: la interfaz pública actúa como la frontera o barrera selectiva del objeto. Mientras que la ocultación "esconde" los detalles de implementación y el estado interno (variables private) para que no sean manipulados arbitrariamente como ocurriría con los campos de una struct en C, la interfaz pública ofrece la "puerta de entrada" controlada. Es decir, la interfaz pública define qué puede hacer el objeto, mientras que la implementación oculta define cómo lo hace.

### Gracias a esta separación, la interfaz pública establece un contrato de uso estable. Si se programara en C accediendo directamente a los miembros de una estructura, cualquier cambio en la definición de esa estructura (por ejemplo, cambiar un int por un double) obligaría a reescribir todas las partes del código que acceden a ella. En cambio, al usar una interfaz pública en Java, es posible modificar radicalmente el funcionamiento interno o el almacenamiento de datos de la clase sin afectar al código externo que la utiliza, siempre y cuando se mantengan inalterados los nombres y parámetros de los métodos públicos.


## 3. Brevemente: ¿Por qué hay que ser conscientes y diseñar con cuidado la **interfaz pública** de una clase? ¿Es fácil cambiarla?

### Se debe diseñar la interfaz pública con sumo cuidado y consciencia porque establece un "contrato" de uso con el resto del sistema. Al igual que en C una función declarada en un archivo de cabecera (.h) define estrictamente cómo deben interactuar otros módulos con una librería, en Java los métodos públicos determinan cómo otras clases dependen de esta. Si se exponen detalles innecesarios o se diseñan métodos confusos, se crea un acoplamiento fuerte entre la clase y el código externo, lo que anula la ventaja principal de la encapsulación: la capacidad de modificar el interior sin afectar el exterior.

### Cambiar la interfaz pública una vez que ha sido utilizada no es fácil y suele tener un costo alto en el desarrollo. Si se modifica la firma de un método público (su nombre, sus parámetros o su tipo de retorno), se "rompe" el código de todas las clases que lo invocan, generando errores de compilación en cascada similares a los que ocurrirían en C si se cambiara el prototipo de una función global utilizada en múltiples archivos fuente. Por ello, es preferible exponer lo mínimo indispensable (principio de mínimo privilegio), ya que añadir funcionalidad pública más tarde es sencillo, pero retirar o modificar algo que ya es público resulta traumático para el sistema.


## 4. ¿Qué son las **invariantes de clase** y por qué la ocultación de información nos ayuda?

### Se denomina invariante de clase a una condición lógica o conjunto de restricciones que el estado interno de un objeto debe satisfacer en todo momento para considerarse válido. Esta condición debe ser cierta justo después de crear el objeto (en el constructor) y debe mantenerse cierta antes y después de la ejecución de cualquier método público. En C, cuando se trabaja con estructuras (struct), la responsabilidad de mantener la coherencia de los datos recae dispersamente en todas las funciones que tocan dicha estructura; si una estructura representa una "Fecha", nada impide técnicamente que una función externa asigne un 32 al campo "día" o un número negativo, rompiendo la lógica del programa.

### La ocultación de información es fundamental para preservar estas invariantes porque impide que el código externo modifique los datos directamente y viole las reglas establecidas. Al declarar los atributos como private (similar a tener una variable estática dentro de un archivo .c que no se exporta), se obliga a que cualquier cambio de estado pase por métodos controlados. Dentro de estos métodos es donde se escribe el código que verifica la invariante (por ejemplo, "el denominador no puede ser cero" o "la edad no puede ser negativa") antes de aceptar el cambio, garantizando así que el objeto nunca entre en un estado inconsistente o corrupto.


## 5. Pon un ejemplo de una clase `Punto` en `Java`, con dos coordenadas, `x` e `y`, de tipo `double`, con un método `calcularDistanciaAOrigen`, y que haga uso de la ocultación de información. ¿Cuál es la interfaz pública de la clase `Punto`? ¿Qué significa `public` y `private`?

### A continuación se presenta una implementación de la clase Punto que ilustra la ocultación de información. En este diseño, las coordenadas se mantienen ocultas al exterior, obligando a que cualquier interacción se realice a través de los métodos definidos, a diferencia de una estructura struct Point en C donde los campos x e y serían accesibles y modificables directamente por cualquier puntero que tuviera la referencia de la estructura.


#### public class Punto {
####    // Estado interno (Oculto): Solo accesible dentro de esta clase
####    private double x;
####    private double y;
####
####    // --- INTERFAZ PÚBLICA ---

####    // Constructor: Inicializa el objeto garantizando un estado válido
#### public Punto(double x, double y) {
####        this.x = x;
####        this.y = y;
####    }

####    // Método de servicio: Realiza un cálculo usando los datos internos
####    public double calcularDistanciaAOrigen() {
####        return Math.sqrt(x * x + y * y);
####    }
    
####    // Getters y Setters: Controlan el acceso a las variables
####    public void setX(double x) {
####        this.x = x;
####    }

####    public double getX() {
####        return x;
####    }
####    // (Se omiten los métodos para 'y' por brevedad, pero seguirían la misma lógica)
#### }


## 6. En Java, ¿A quiénes se pueden aplicar los modificadores `public` o `private`?

### En Java, los modificadores de acceso public y private se aplican fundamentalmente a los miembros de una clase, es decir, a los atributos (variables de instancia o estáticas) y a los métodos (funciones). Cuando se declara un atributo o método como private, se limita su visibilidad exclusivamente al ámbito de la clase que lo contiene. Esto es comparable en C a declarar una variable o función como static dentro de un archivo .c: dicha variable existe y es usable dentro de ese archivo ("unidad de traducción"), pero es invisible para el resto del programa, protegiendo la implementación interna.

### Por otro lado, cuando estos miembros se declaran como public, son accesibles desde cualquier clase en cualquier parte del programa. Esto recrea el comportamiento por defecto de los miembros de una estructura (struct) en C, donde si se tiene acceso a la estructura, se tiene acceso directo a todos sus datos. En el diseño orientado a objetos, se recomienda que los atributos sean casi siempre private para garantizar la encapsulación, mientras que los métodos suelen ser public si forman parte de la interfaz que el objeto ofrece al exterior.

### Además de los miembros, estos modificadores también se aplican a los constructores. Un constructor public permite que cualquier clase cree instancias del objeto (como un malloc o una función de inicialización global en C). Sin embargo, es posible declarar un constructor como private; esto impide que otras clases instancien el objeto directamente, una técnica que se utiliza en patrones de diseño específicos (como el Singleton) o en clases utilitarias que solo contienen métodos estáticos y no deben ser instanciadas.

### Finalmente, los modificadores se aplican a las propias clases, pero con una distinción importante. Una clase de nivel superior (la que coincide con el nombre del archivo .java) puede ser public, haciéndola visible para todo el proyecto. No obstante, una clase de nivel superior no puede ser private (ya que sería inaccesible para todos y por tanto inútil). El modificador private en clases solo es válido para clases anidadas (clases definidas dentro de otras clases), las cuales funcionan como ayudantes internos ocultos al resto del sistema.


## 7. En POO, la visibilidad puede ser pública o privada, pero ¿existen más tipos de visibilidad? ¿Qué ocurre en Java? ¿Y en otros lenguajes?

### Efectivamente, en la Programación Orientada a Objetos la visibilidad no es binaria. En Java, además de public y private, existen dos niveles intermedios de control de acceso: protected y el nivel por defecto (conocido como package-private). Estos niveles permiten una granularidad más fina, similar a cómo en C se puede controlar el alcance de una variable global limitándola a un solo archivo con static o permitiendo que sea visible para otros archivos mediante extern dentro del mismo módulo de compilación.

### El nivel por defecto (cuando no se escribe ninguna palabra clave) permite que cualquier clase que se encuentre en el mismo "paquete" (la misma carpeta física en el disco) acceda a los miembros. Esto es comparable a tener varios archivos .c en un mismo directorio que comparten un archivo de cabecera .h privado, invisible para el resto del proyecto; entre ellos se "tienen confianza" y comparten datos, pero el exterior no lo sabe. Por otro lado, el modificador protected amplía esta visibilidad: permite el acceso a las clases del mismo paquete y, además, a las "subclases" (clases hijas que heredan código), incluso si están en paquetes distintos. Esto es crucial para la herencia, permitiendo que una clase derivada modifique el estado interno de su padre sin exponerlo a todo el mundo.

### En otros lenguajes como C++, el funcionamiento es ligeramente distinto. Aunque existen public, private y protected, el concepto de "paquete" no existe de la misma forma que en Java. En C++, protected restringe el acceso estrictamente a las clases derivadas (herencia), y no abre la visibilidad a otros archivos del mismo directorio automáticamente. Para permitir acceso a clases externas específicas en C++, se utiliza el concepto de funciones o clases friend (amigas), que rompe la encapsulación de forma controlada, algo que Java no implementa directamente. Otros lenguajes como Python no tienen modificadores estrictos y se basan en convenciones (usar un guion bajo _variable para indicar "privado"), confiando en la responsabilidad del programador en lugar de en la prohibición del compilador.


## 8. Responde: Los miembros de instancia privados de un objeto están ocultos para (a) otras clases o (b) otras instancias, aunque sean de la misma clase. Pon un ejemplo añadiendo un método `calcularDistanciaAPunto(Punto otro)` y explica la respuesta.

### La respuesta correcta es la (a): están ocultos para otras clases. En Java (y en C++), los modificadores de acceso se aplican a nivel de clase (el tipo de dato), no a nivel de instancia (el objeto individual). Esto significa que un objeto de la clase Punto tiene permiso absoluto para acceder a los miembros privados de cualquier otro objeto de la misma clase Punto. La "privacidad" protege la implementación contra código externo, pero entre "hermanos" de la misma clase hay confianza total.

### Para entender esto desde la perspectiva de C, imagina una función que recibe dos punteros a la misma estructura: double distancia(struct Punto *a, struct Punto *b). Dentro de esa función, el código puede acceder a a->x y también a b->x sin ninguna restricción, porque la función "conoce" la definición interna de la estructura. En Java ocurre exactamente lo mismo: el método calcularDistanciaAPunto pertenece a la definición de la clase, por lo que tiene la "llave maestra" para ver los atributos privados (x e y) tanto del objeto actual (this) como del objeto que recibe como parámetro (otro).

### Si la restricción fuera por instancia (opción b), sería imposible implementar métodos eficientes de interacción binaria (como sumar dos números complejos, comparar dos fechas o calcular distancias) sin exponer los datos a través de métodos públicos (getters). Al permitir el acceso entre instancias de la misma clase, se mantiene la encapsulación frente al mundo exterior sin sacrificar la capacidad de los objetos del mismo tipo para interactuar íntimamente entre ellos.


#### public class Punto {
####    private double x;
####    private double y;

####    public Punto(double x, double y) {
####        this.x = x;
####        this.y = y;
####    }

####    public double calcularDistanciaAPunto(Punto otro) {
####        // Acceso directo a 'x' e 'y' de la OTRA instancia.
####        // Esto es válido porque ambos son de la clase Punto.
####        double cateto1 = this.x - otro.x; 
####        double cateto2 = this.y - otro.y;
####    return Math.sqrt(cateto1 * cateto1 + cateto2 * cateto2);
####    }
#### }


## 9. ¿Qué son los métodos "getter" y "setter" en los lenguajes orientados a objetos?

### Los métodos "getter" (accedentes) y "setter" (mutadores) son el mecanismo estándar en la Programación Orientada a Objetos para leer y modificar los valores de los atributos privados de una clase desde el exterior. Se pueden visualizar como intermediarios o "válvulas" que regulan el flujo de datos hacia y desde el objeto. En C, es habitual acceder directamente a los miembros de una struct (punto.x = 5;), lo que expone la representación interna y hace imposible detectar cuándo o cómo se modifican los datos. En contraste, los getters y setters encapsulan este acceso, permitiendo que la clase mantenga el control total sobre sus propios campos.

### El método setter es fundamental para garantizar la integridad del estado del objeto (las invariantes de clase). Al obligar a utilizar un método para cambiar un valor, se ofrece un punto único donde insertar lógica de validación. Por ejemplo, si se tuviera una clase Persona con un atributo edad, un acceso directo permitiría asignar un valor negativo o absurdo; sin embargo, un setter puede incluir una estructura condicional (if) que rechace el valor inválido o lance un error. Esto protege al objeto de entrar en un estado corrupto, algo que las variables de una estructura en C no pueden prevenir por sí mismas si son accesibles globalmente.

### Por otro lado, el método getter proporciona una ventana de acceso a los datos, permitiendo controlar la visibilidad. Esto permite diseñar clases donde ciertos atributos sean visibles pero no modificables (inmutables desde fuera) simplemente omitiendo el método setter correspondiente. Además, los getters permiten desacoplar la representación interna de la externa: se podría cambiar internamente un atributo de tipo int a tipo double o cambiar las unidades de medida, pero mantener el método get... original realizando la conversión matemática al vuelo, de modo que el cambio sea transparente para el código que utiliza la clase.


## 10. Cuando nos referimos a que la ocultación de información mejora la "seguridad" del programa, ¿nos referimos a que no pueda ser "hackeado"?

### No, cuando se habla de seguridad en el contexto de la encapsulación y la ocultación de información, no se refiere a la protección contra ataques malintencionados (hacking) ni al cifrado de datos. La "seguridad" aquí debe entenderse como seguridad lógica o robustez (en inglés, safety más que security). Se trata de proteger al código de sí mismo y de los errores accidentales que puedan cometer los programadores que utilizan las clases. En C, un puntero erróneo o un acceso directo a una estructura puede corromper la memoria de forma silenciosa, provocando fallos catastróficos difíciles de depurar; la encapsulación busca evitar precisamente estas situaciones de inconsistencia interna.

### Es importante destacar que los modificadores de acceso (private, protected) son restricciones que impone el compilador, no el entorno de ejecución. Al igual que en C se puede usar aritmética de punteros para acceder a direcciones de memoria teóricamente "prohibidas" o fuera de los límites de un array, en Java existen mecanismos avanzados (como la Reflexión) que permiten a un programador saltarse las restricciones de acceso y leer variables privadas si así lo desea. Por tanto, si un atacante tiene acceso al sistema, la encapsulación no le impedirá leer los datos; su función no es blindar la información, sino organizar el código.

### El objetivo real es garantizar que los objetos mantengan sus invariantes (reglas de validez) intactas frente al uso normal del programa. Se protege la integridad de los datos evitando que código externo (desarrollado quizás por otra persona del equipo) asigne valores inválidos por desconocimiento de la lógica interna. Mientras que en C la "seguridad" de una estructura depende enteramente de la disciplina del programador para no tocar lo que no debe, en Java la ocultación de información convierte esa disciplina en una obligación sintáctica, reduciendo drásticamente la cantidad de bugs producidos por un mal uso de las estructuras de datos.


## 11. ¿Qué diferencia hay entre **miembro de instancia** y **miembro de clase**? ¿Los miembros de clase también se pueden ocultar?

### Un miembro de instancia es aquel que pertenece a un objeto concreto creado a partir de la clase. Cada vez que se crea una nueva instancia (usando new), el sistema reserva un espacio de memoria independiente para sus atributos; por tanto, si se modifica un atributo de instancia en un objeto, los demás objetos no se ven afectados. Esto es análogo a declarar múltiples variables de tipo struct en C: cada variable tiene su propia copia de los campos y lo que ocurre en struct A no afecta a struct B.

### Por el contrario, un miembro de clase (declarado con la palabra clave static en Java) es compartido por todas las instancias de la clase. Existe una única copia de este miembro en la memoria durante toda la ejecución del programa, independientemente de cuántos objetos se creen (incluso si no se crea ninguno). Su comportamiento es muy similar al de una variable global en C, pero encapsulada dentro del espacio de nombres de la clase. Si un objeto modifica un atributo de clase (static), el cambio se refleja inmediatamente para todos los demás objetos.

### Sí, los miembros de clase también se pueden ocultar utilizando el modificador private. Un atributo declarado como private static es una variable compartida que solo puede ser leída o modificada por los métodos de la propia clase, pero que permanece invisible para el resto del programa. Esto es comparable a declarar una variable static global dentro de un archivo .c (file scope): actúa como una variable global para las funciones de ese archivo, pero está oculta para otros archivos del proyecto, permitiendo gestionar un estado compartido interno (como un contador de instancias o una caché) sin exponerlo al exterior.


## 12. Brevemente: ¿Tiene sentido que los constructores sean privados?

### Sí, tiene pleno sentido y es una técnica fundamental para restringir y controlar la creación de objetos. Al declarar un constructor como private, la clase se "cierra" al exterior, impidiendo que cualquier otra parte del código utilice el operador new para instanciarla arbitrariamente. Esto es esencial para implementar el patrón Singleton, donde se garantiza que solo exista una única instancia de la clase en todo el sistema. En C, esto sería análogo a un módulo que gestiona un recurso único (como un driver de vídeo) y que no permite al usuario declarar variables de esa estructura, obligándolo a llamar a una función obtener_driver() que devuelve siempre el mismo puntero a una estructura estática interna.

### Además, los constructores privados son útiles en clases de utilidad (como java.lang.Math), que son meros contenedores de funciones estáticas (similares a librerías de funciones en C) y no requieren mantener estado ni crear objetos. Al bloquear el constructor, se evita que los programadores cometan el error conceptual de instanciar una clase que no está diseñada para ser un objeto. También permiten el uso de métodos de fábrica estáticos (static factory methods), que actúan como constructores más flexibles: pueden tener nombres descriptivos, devolver objetos de subclases o reutilizar objetos existentes en lugar de crear uno nuevo cada vez (similar a una función crear_entidad() en C que gestiona internamente el malloc y la inicialización).


## 13. ¿Cómo se indican los **miembros de clase** en Java? Pon un ejemplo, en la clase `Punto` definida anteriormente, para que incluya miembros de clase que permitan saber cuáles son los valores `x` e `y` máximos que se han establecido en todos los puntos que se hayan creado hasta el momento.

### En Java, los miembros de clase se distinguen de los miembros de instancia mediante el uso de la palabra clave reservada static en su declaración. Mientras que las variables de instancia (sin static) generan una copia independiente en memoria para cada objeto creado (como tener múltiples variables de tipo struct en C), las variables de clase o estáticas existen en una única ubicación de memoria compartida por todas las instancias. Esto es análogo a una variable global en C, pero restringida al ámbito de la clase; su valor persiste durante toda la ejecución del programa y es común para todos los objetos de ese tipo.

### Para resolver el problema planteado en la clase Punto, se deben declarar dos variables static privadas que almacenen los máximos históricos de x e y. Dado que estas variables "sobreviven" a la creación y destrucción de objetos individuales, actúan como un registro global acumulativo. Es necesario actualizar estas variables cada vez que un valor cambia (en el constructor y en los métodos setters) y proporcionar métodos estáticos públicos (public static) para consultar estos valores sin necesidad de tener una instancia concreta del objeto, invocándolos directamente a través del nombre de la clase (ej. Punto.getXMaximo()).

### A continuación se muestra la implementación modificada, donde se observa cómo la lógica de actualización compara los valores de la instancia actual (this.x) con el valor compartido de la clase (xMaximo), actualizando este último si es necesario:

#### public class Punto {
 ####   // Miembros de INSTANCIA: Cada punto tiene sus propias coordenadas
####    private double x;
####    private double y;

####    // Miembros de CLASE (static): Compartidos por todos los puntos.
#### // Se inicializan al valor más bajo posible para asegurar que el primer punto los actualice.
####    private static double xMaximo = Double.NEGATIVE_INFINITY;
####    private static double yMaximo = Double.NEGATIVE_INFINITY;

####    // Constructor
####    public Punto(double x, double y) {
####        this.x = x;
####        this.y = y;
####        actualizarMaximos(x, y); // Verificamos si los nuevos valores son récord
####    }

####    // Método privado auxiliar para actualizar los estáticos
####    private void actualizarMaximos(double nuevoX, double nuevoY) {
####        if (nuevoX > xMaximo) {
####            xMaximo = nuevoX;
####        }
####        if (nuevoY > yMaximo) {
####         yMaximo = nuevoY;
####        }
####    }

####    // Setters: También deben verificar si el nuevo valor supera el máximo histórico
####    public void setX(double x) {
####        this.x = x;
####        if (x > xMaximo) {
####            xMaximo = x;
####        }
####    }

####    // --- MÉTODOS DE CLASE (static) ---
####    // Permiten consultar los máximos sin necesidad de crear un objeto
####    public static double getXMaximo() {
####        return xMaximo;
####    }

####    public static double getYMaximo() {
####        return yMaximo;
####    }
#### }


## 14. Como sería un método factoría dentro de la clase `Punto` para construir un `Punto` a partir de dos coordenadas, pero que las redondee al entero más cercano. Escribe sólo el código del método, no toda la clase ¿Has usado `static`? 

#### public static Punto crearPuntoRedondeado(double x, double y) {
####    // Se redondean las coordenadas al entero más cercano (long)
#### // y se convierten implícitamente a double para el constructor
####    double xRedondeado = Math.round(x);
####    double yRedondeado = Math.round(y);
    
####    // Se devuelve una nueva instancia con los datos procesados
####    return new Punto(xRedondeado, yRedondeado);
#### }


## 15. Cambia la implementación de `Punto`. En vez de dos `double`, emplea un array interno de dos posiciones, intentando no modificar la interfaz pública de la clase.

### public class Punto {
###    // NUEVA IMPLEMENTACIÓN: Array interno oculto (private)
###    // Índice 0 = x, Índice 1 = y
###    private double[] coordenadas;

###    // --- INTERFAZ PÚBLICA (Sin cambios) ---

###    // Constructor: Mantiene la misma firma que antes
###    public Punto(double x, double y) {
###        // Inicializamos el array y asignamos los valores
###        this.coordenadas = new double[2];
###        this.coordenadas[0] = x;
###        this.coordenadas[1] = y;
###    }

###    // Getters y Setters: Adaptan la petición al nuevo almacenamiento
###    public double getX() {
###        return coordenadas[0]; // Traduce la petición
###    }

###    public void setX(double x) {
###        coordenadas[0] = x;
###    }

###    public double getY() {
###        return coordenadas[1];
###    }

###    public void setY(double y) {
###        coordenadas[1] = y;
###    }

###    // El cálculo se adapta internamente, el resultado es el mismo
###    public double calcularDistanciaAOrigen() {
###        return Math.sqrt(Math.pow(coordenadas[0], 2) + Math.pow(coordenadas[1], 2));
###    }
### }


## 16. Si un atributo va a tener un método "getter" y "setter" públicos, ¿no es mejor declararlo público? ¿Cuál es la convención más habitual sobre los atributos, que sean públicos o privados? ¿Tiene esto algo que ver con las "invariantes de clase"?

### Aunque pueda parecer redundante escribir métodos que simplemente asignan o devuelven un valor, no es mejor declarar el atributo como público. La razón fundamental es la flexibilidad y el mantenimiento a largo plazo. En C, si se expone un campo de una estructura y cientos de archivos de código lo leen directamente (s.valor), cambiar la lógica de ese dato (por ejemplo, decidir que ahora se calcula en tiempo real en lugar de almacenarse) obligaría a reescribir todos esos archivos. Al usar getters y setters, se crea una capa de abstracción: si en el futuro se necesita cambiar la implementación interna, solo se modifica el código dentro de la clase, manteniendo intacto el resto del sistema que sigue llamando a los mismos métodos.

### La convención casi universal en Java y en la mayoría de lenguajes orientados a objetos es declarar todos los atributos como private (o protected si se diseña para herencia) y exponer solo aquellos necesarios mediante métodos public. Esta práctica es tan estándar que define la estructura conocida como "JavaBean". Declarar atributos públicos se considera una mala práctica (un "code smell"), reservándose únicamente para constantes globales (public static final) o para estructuras de datos muy simples y desechables que no tienen comportamiento, similares a los struct planos de C (POD - Plain Old Data).

### Esto tiene una relación directa y crítica con las invariantes de clase. Un atributo público no tiene defensa; cualquier parte del código puede asignarle un valor inválido en cualquier momento, rompiendo la invariante. Aunque hoy un setter solo haga una asignación directa (this.x = x), su mera existencia reserva el lugar donde, mañana, se podrá insertar lógica de validación (if (x > 0)...) sin cambiar la interfaz pública. Si el atributo fuera público, introducir esa validación implicaría cambiar el atributo a privado y romper todo el código que lo usaba directamente, convirtiendo una tarea de 5 minutos en una refactorización costosa.


## 17. ¿Qué significa que una clase sea **inmutable**? ¿qué es un método modificador? ¿Un método modificador es siempre un "setter"? ¿Tiene ventajas que una clase sea inmutable?

### Una clase se considera inmutable cuando el estado de sus instancias no puede ser modificado una vez que el objeto ha sido creado. En términos de C, esto es análogo a declarar una variable de estructura como const: se inicializan sus valores en el momento de la definición y, a partir de ahí, la memoria es de solo lectura. Para lograr esto en Java, se suelen declarar todos los atributos como private y final (una palabra clave que impide la reasignación), se eliminan todos los métodos que permitan cambios y se asegura que la clase no pueda ser extendida por otra que sí permita modificaciones. Si se desea "cambiar" un valor, la clase inmutable no altera sus propios campos, sino que devuelve una nueva instancia con los nuevos valores, dejando el objeto original intacto.

### Un método modificador (o mutador) es cualquier método público que altera el estado interno del objeto. Aunque los métodos que comienzan con set... (setters) son los modificadores más comunes y directos, un modificador no es siempre un setter. Cualquier método que realice una operación que cambie el valor de un atributo es un modificador. Por ejemplo, en una clase CuentaBancaria, un método retirar(double cantidad) es un modificador porque reduce el saldo interno, aunque no se llame setSaldo. En C, esto equivale a pasar un puntero no constante a una función (void func(struct Obj *o)) que altera los datos apuntados; en una clase inmutable, este tipo de operaciones están prohibidas.

### Las ventajas de la inmutabilidad son enormes, especialmente en la programación concurrente (múltiples hilos de ejecución). Dado que el estado del objeto nunca cambia, no es necesario utilizar mecanismos de sincronización complejos (como mutex o semáforos en C) para leer el objeto desde distintos hilos, ya que es imposible que un hilo lea un dato "a medias" mientras otro lo está escribiendo. Esto hace que el código sea intrínsecamente seguro (thread-safe) y mucho más fácil de depurar. Además, los objetos inmutables pueden ser cacheados y reutilizados sin miedo a efectos colaterales, ya que se tiene la certeza de que ninguna función a la que se pase el objeto podrá alterarlo inadvertidamente.


## 18. ¿Es recomendable incluir métodos "setter" siempre y como convención?

### No, no es recomendable incluir métodos "setter" de forma automática o indiscriminada para todos los atributos de una clase. Hacerlo por inercia (o utilizando las herramientas de generación de código del IDE) rompe el principio de encapsulación, ya que expone la implementación interna al exterior. Si una clase tiene todos sus atributos privados pero ofrece un método "set" público para cada uno, en la práctica se comporta igual que una estructura (struct) de C: cualquier parte del programa puede modificar sus datos a voluntad, convirtiendo al objeto en un simple contenedor de datos sin control sobre su propio estado.

### En el diseño orientado a objetos, se debe preferir exponer comportamiento en lugar de acceso a datos. En lugar de preguntar "¿qué valor tiene este atributo?" o decir "cambia este valor a X", se debería ordenar al objeto que realice una acción. Por ejemplo, en lugar de tener un método setVelocidad(int v) en una clase Coche, es preferible tener métodos como acelerar() o frenar(). Estos métodos modifican la velocidad internamente, pero bajo las reglas del objeto (por ejemplo, no superar una velocidad máxima o no frenar si ya está detenido), lógica que se perdería si simplemente se permitiera asignar un valor crudo desde fuera.

### Además, omitir los métodos "setter" fomenta la inmutabilidad. Si un atributo se inicializa en el constructor y no tiene un método para cambiarlo posteriormente, ese dato es de "solo lectura" para el resto del sistema (similar a un puntero const en C). Esto reduce drásticamente los errores, ya que se garantiza que una vez creado el objeto válido, nadie podrá corromperlo "por accidente" a mitad de la ejecución del programa. Por tanto, la convención correcta es: añadir un setter solo si es estrictamente necesario que ese valor cambie desde el exterior y no existe una operación de negocio más específica que lo justifique.


## 19. ¿La clase `String` en Java es mutable o inmutable? ¿Qué ocurre al concatenar dos cadenas? ¿Qué debemos hacer si vamos a hacer una operación que implique concatenar muchas veces para construir paso a paso una cadena muy larga?

### La clase String en Java es inmutable. Esto significa que, una vez creado un objeto de tipo String, su contenido (la secuencia de caracteres) no puede modificarse bajo ninguna circunstancia. En C, esto es comparable a un puntero const char* que apunta a una cadena literal almacenada en una zona de memoria de solo lectura; aunque se puede hacer que el puntero apunte a otra dirección, es ilegal intentar cambiar los caracteres individuales de esa dirección de memoria (str[0] = 'X' provocaría un error en tiempo de ejecución o comportamiento indefinido).

### Al concatenar dos cadenas utilizando el operador +, Java no modifica la cadena original, ya que no tiene permitido escribir en esa memoria. Lo que ocurre internamente es un proceso costoso: se reserva un nuevo espacio de memoria en el heap, se copian los caracteres de la primera cadena, se copian los caracteres de la segunda y se devuelve una referencia a este nuevo objeto resultante. La cadena original queda intacta y, si no hay más variables apuntando a ella, queda "huérfana" esperando a ser eliminada por el Recolector de Basura. Esto es muy diferente a usar strcat en C, donde simplemente se escriben bytes a continuación del terminador nulo en un buffer existente.

### Si se necesita realizar muchas concatenaciones consecutivas (por ejemplo, dentro de un bucle para construir un texto largo), el uso de String y el operador + es extremadamente ineficiente, ya que genera una cantidad masiva de objetos temporales intermedios que deben ser creados y destruidos. Para solucionar esto, se debe utilizar la clase StringBuilder. Esta clase actúa como un buffer mutable dinámico (similar a gestionar un array con malloc y realloc en C): tiene una capacidad reservada y permite añadir caracteres al final sin crear nuevos objetos, redimensionando su array interno solo cuando se llena.


## 20. En POO ¿Cómo se comparan objetos de una misma clase? ¿Por su contenido o por su identidad? ¿Qué es el método equals en Java? ¿Qué hace por defecto? ¿Cómo se deben comparar dos cadenas en Java? 

### En la Programación Orientada a Objetos, es crucial distinguir entre la identidad del objeto (si dos referencias apuntan a la misma dirección de memoria) y la igualdad de contenido (si dos objetos distintos contienen los mismos datos). En Java, el operador == compara siempre la identidad, comportándose exactamente igual que la comparación de punteros en C (ptr1 == ptr2). Si se tienen dos objetos creados independientemente con new, aunque sus atributos sean idénticos, el operador == devolverá false porque residen en direcciones de memoria diferentes.

### Para comparar el contenido, Java proporciona el método equals(Object obj), definido originalmente en la clase raíz Object. Sin embargo, la implementación por defecto de este método en la clase Object es meramente comparar las referencias (es decir, hace un return this == obj;). Por tanto, si no se modifica, equals se comporta igual que ==. Para que dos objetos de una clase propia (como Punto) sean considerados iguales cuando sus datos coinciden, el programador debe sobrescribir (override) el método equals, definiendo explícitamente qué atributos deben compararse (similar a escribir una función comparar_structs en C que verifique campo por campo).

### En el caso específico de las cadenas de texto (String), jamás se debe utilizar el operador == para comparar su contenido. Dado que String es una clase y no un tipo primitivo, == verificaría si ambas variables apuntan al mismo objeto en el heap. Esto es un error frecuente, ya que en C se suele usar strcmp para el contenido, pero en Java la sintaxis s1 == s2 es válida y compila, dando resultados incorrectos (falsos negativos) si las cadenas fueron creadas en distintos momentos. La clase String ya tiene el método equals sobrescrito correctamente, por lo que la forma única y segura de comparar texto es invocando cadena1.equals(cadena2).


## 21. ¿Qué son las clases "wrapper" en un lenguaje de programación orientado a objetos? ¿Cómo se hace? ¿Es un proceso automático? ¿Qué ventajas tienen? ¿Todos los lenguajes orientados a objetos tienen tipos primitivos y necesitan wrappers? 

### Las clases "wrapper" (envoltorios) son clases diseñadas específicamente para encapsular un tipo de dato primitivo (int, double, char) dentro de un objeto. En lenguajes como Java, existe una brecha técnica: los tipos primitivos son eficientes y viven en la pila (stack), tal y como ocurre en C, mientras que las estructuras de datos complejas trabajan con referencias a objetos en el montículo (heap). Un wrapper actúa como un adaptador: contiene un único campo con el valor primitivo, permitiendo que ese valor "simple" sea tratado con todas las capacidades de un objeto completo. Es análogo a tener una struct Entero { int dato; } en C para poder pasar un número a una función que espera estrictamente un puntero a una estructura.

### Este proceso de conversión puede ser manual o automático. En las versiones modernas de Java, el compilador realiza automáticamente el Autoboxing (convertir de primitivo a wrapper) y el Unboxing (extraer el primitivo del wrapper) cuando es necesario. Esto significa que el programador puede asignar un int literal a una variable de tipo Integer sin escribir código extra. El compilador, "por detrás", inserta las instrucciones necesarias para crear el objeto, similar a si en C el compilador decidiera automáticamente cuándo hacer un malloc para guardar un entero y cuándo liberar la memoria para usar el valor en una suma, ocultando esa complejidad.

### Las ventajas de los wrappers son fundamentales para la programación genérica. Las Colecciones estándar de Java (como ArrayList o LinkedList) solo pueden almacenar referencias a objetos, no tipos primitivos. Por tanto, es imposible crear una lista de int, pero sí una lista de objetos Integer. Además, los wrappers permiten representar la ausencia de valor mediante null (un int primitivo siempre tiene un valor, por defecto 0, pero un Integer puede ser "nada"), y proporcionan métodos de utilidad estáticos, como Integer.parseInt(), agrupando la funcionalidad que en C estaría dispersa en librerías globales como stdlib.h.

### No todos los lenguajes orientados a objetos requieren wrappers. Lenguajes considerados "puros" (como Smalltalk o Ruby) tratan absolutamente todo como un objeto; en ellos, incluso el número 1 es una instancia de una clase y tiene métodos. Java y C++ son lenguajes "híbridos" que mantienen los tipos primitivos por herencia de C y por eficiencia de rendimiento (operar con bits crudos en la CPU es más rápido que gestionar objetos completos). Por ello, los wrappers son una solución de compromiso necesaria para unir el mundo de alto rendimiento (primitivos) con el mundo de alta abstracción (objetos).


## 22. ¿En POO qué es un **tipo de dato enumerado**? ¿En Java, un tipo de dato enumerado es una clase? ¿Qué ventajas tienen en términos de encapsulación los enumerados en Java?

### En la Programación Orientada a Objetos, un tipo de dato enumerado es un mecanismo para definir un conjunto fijo y cerrado de constantes con nombre, representando una colección lógica de valores (como los días de la semana, los estados de un pedido o los tipos de usuario). A diferencia de C, donde un enum es esencialmente un alias para números enteros (int) y permite intercambiar valores numéricos libremente (lo que puede llevar a errores si se asigna un 5 a una variable que solo debería aceptar 0, 1 o 2), en POO un enumerado es un tipo fuerte. Esto significa que el compilador garantiza la seguridad de tipos: una variable de tipo Color solo puede contener valores definidos en Color, rechazando cualquier otro entero o tipo de dato.

### En Java, un tipo de dato enumerado (definido con la palabra clave enum) es, efectivamente, una clase. Aunque su declaración es concisa, internamente el compilador convierte cada enumerado en una clase completa que hereda de java.lang.Enum. Cada constante declarada dentro del enumerado (por ejemplo, LUNES, MARTES) es una instancia (un objeto) estática y final de esa clase. Esto representa un cambio radical respecto a C: no se están manejando simples números, sino objetos con identidad propia, que pueden tener estado y comportamiento.

### Desde el punto de vista de la encapsulación, los enumerados en Java ofrecen una ventaja arquitectónica superior: permiten empaquetar datos y lógica dentro de la propia constante. En C, es común tener que mantener "arrays paralelos" o funciones de búsqueda globales para asociar información a un valor (por ejemplo, un array de strings para imprimir el nombre del color). En Java, al ser clases, los enumerados pueden tener atributos privados, constructores y métodos.

### Esto permite que cada constante del enumerado sea responsable de sus propios datos (como su código hexadecimal, su abreviatura o su factor de conversión), manteniendo la información localizada y protegida. El código cliente no necesita saber cómo se almacena internamente esa información; simplemente invoca los métodos públicos del enumerado, respetando el principio de ocultación de inform


## 23. Crea un tipo enumerado en Java que se llame `Mes`, con doce posibles instancias y que además proporcione métodos para obtener cuántos días tiene ese mes, el ordinal de ese mes en el año (1-12), empleando atributos privados y constructores del tipo enumerado. Añade además cuatro métodos para devolver si ese mes tiene algunos días de invierno, primavera, verano u otoño, indicando con un booleano el hemisferio (norte o sur, parámetro `enHemisferioNorte`). Es decir: `esDePrimavera(boolean esHemisferioNorte)`, `esDeVerano(boolean esHemisferioNorte)`, `esDeOtoño(boolean esHemisferioNorte)`, `esDeInvierno(boolean esHemisferioNorte)`

### Respuesta
