<!--
Posible prompt:
<prompt>
Tengo un cuestionario con preguntas sobre "Clases y Objetos". Debes tener en cuenta que los conocimientos previos que tengo (y por tanto tus respuestas deben ser adaptadas), son:
- C/C++ sin orientación a objetos.
- Temas de Java previos: ninguno.

Cada respuesta debe tener entre 2 - 4 párrafos de longitud (sin contar los trozos de código).

Por favor, escribe en impersonal las respuestas.

</prompt>
----
-->

# TEMA 1. Clases y objetos

## 1. ¿Cuáles son las cuatro características básicas de la programación orientada a objetos? Describe brevemente cada una

### Respuesta

###    1. Abstracción (Abstraction)
#### Es la capacidad de simplificar una realidad compleja enfocándose solo en los aspectos relevantes para el problema actual, ignorando los detalles innecesarios. Se trata de definir "qué hace" un objeto sin preocuparse por "cómo lo hace" internamente.

### 2. Encapsulamiento (Encapsulation)
#### Consiste en ocultar los datos internos de un objeto y permitir el acceso a ellos solo a través de métodos públicos definidos. Esto protege la integridad del objeto, evitando que algo externo modifique sus datos de manera incorrecta. Actúa como una "caja negra".

### 3. Herencia (Inheritance)
#### Es el mecanismo por el cual una clase nueva (clase hija o subclase) puede adquirir las características y comportamientos de una clase existente (clase padre o superclase). Esto fomenta la reutilización de código y crea una jerarquía lógica.

### 4. Polimorfismo (Polymorphism)
#### La palabra significa "muchas formas". Permite que objetos de diferentes clases respondan a la misma llamada de método de maneras diferentes. Esto hace que el código sea flexible, ya que puedes tratar a distintos objetos como si fueran del mismo tipo general.



## 2. Cita cuatro lenguajes populares que permitan la programación orientada a objetos

### Respuesta

### Java, Python, C++ y C#

## 3. Los paradigmas anteriores a la POO, ¿Qué es la **programación estructurada**? y, todavía mejor, ¿Qué es la **programación modular**?

### Respuesta

### La programación estructurada impone un orden de ejecución:

#### 1. Secuencia: Las instrucciones se ejecutan una tras otra, en orden descendente.

#### 2. Selección (Condicionales): El código toma decisiones (if, else, switch). Si pasa A, haz esto; si no, haz lo otro.

#### 3. Iteración (Bucles): Repetir un bloque de código mientras se cumpla una condición (for, while).



## 4. ¿Qué tres elementos definen a un objeto en programación orientada a objetos?

### Respuesta

### 1. Identidad (Identity)
#### Es la propiedad que permite distinguir a un objeto de todos los demás, incluso si tienen exactamente los mismos datos.

### 2. Estado (State)
#### Es el conjunto de valores de los atributos que tiene el objeto en un momento determinado.

### 3. Comportamiento (Behavior)
#### Es lo que el objeto puede hacer o cómo reacciona ante mensajes (llamadas) de otros objetos.

## 5. ¿Qué es una clase? ¿Es lo mismo que un objeto? ¿Qué es una instancia? ¿Todos los lenguajes orientados a objetos manejan el concepto de clase?

### Respuesta


### La Programación Orientada a Objetos (POO) es un paradigma que estructura el software basándose en "objetos" que contienen datos y funciones, en lugar de una simple lógica lineal.

### Aquí tienes las cuatro características fundamentales (a menudo llamadas los "cuatro pilares") de la POO:

### 1. Abstracción (Abstraction)
#### Es la capacidad de simplificar una realidad compleja enfocándose solo en los aspectos relevantes para el problema actual, ignorando los detalles innecesarios. Se trata de definir "qué hace" un objeto sin preocuparse por "cómo lo hace" internamente.

#### Ejemplo: Piensa en un coche. Para conducirlo (usar el objeto), solo necesitas abstraer sus funciones principales: volante, pedales y palanca. No necesitas entender la termodinámica del motor de combustión para ir al supermercado.

### 2. Encapsulamiento (Encapsulation)
#### Consiste en ocultar los datos internos de un objeto y permitir el acceso a ellos solo a través de métodos públicos definidos. Esto protege la integridad del objeto, evitando que algo externo modifique sus datos de manera incorrecta. Actúa como una "caja negra".

#### Ejemplo: Una cuenta bancaria. Tú no puedes cambiar tu saldo directamente escribiendo un número nuevo en la base de datos (eso sería inseguro). Debes usar los métodos "depositar" o "retirar", los cuales contienen reglas para asegurar que la transacción sea válida.

### 3. Herencia (Inheritance)
#### Es el mecanismo por el cual una clase nueva (clase hija o subclase) puede adquirir las características y comportamientos de una clase existente (clase padre o superclase). Esto fomenta la reutilización de código y crea una jerarquía lógica.

#### Ejemplo: Si tienes una clase general llamada Vehículo, puedes crear clases hijas como Coche y Motocicleta. Ambas heredarán atributos básicos de Vehículo (como "tener motor" o "tener ruedas"), pero añadirán sus propias características únicas sin tener que reescribir el código común.

### 4. Polimorfismo (Polymorphism)
#### La palabra significa "muchas formas". Permite que objetos de diferentes clases respondan a la misma llamada de método de maneras diferentes. Esto hace que el código sea flexible, ya que puedes tratar a distintos objetos como si fueran del mismo tipo general.

#### Ejemplo: Imagina un método llamado mover().

#### Si llamas a Pájaro.mover(), el pájaro vuela.

#### Si llamas a Pez.mover(), el pez nada.

#### Si llamas a Serpiente.mover(), la serpiente se arrastra.

#### El programa manda la misma orden (mover), pero cada objeto sabe cómo ejecutarla según su propia naturaleza.


## 5. ¿Qué es una clase? ¿Es lo mismo que un objeto? ¿Qué es una instancia? ¿Todos los lenguajes orientados a objetos manejan el concepto de clase?


### 1. ¿Qué es una clase?
#### Una clase es una plantilla, molde o plano. Es un concepto abstracto que define la estructura y el comportamiento que tendrán los objetos, pero no es el objeto en sí mismo.

### 2. ¿Es lo mismo que un objeto?
#### No. Son conceptos complementarios pero distintos.

#### La Clase es la definición teórica (el molde).

#### El Objeto es la materialización de esa definición (la galleta que sale del molde).

### 3. ¿Qué es una instancia?
#### "Instancia" es el término técnico para referirse a un objeto específico creado a partir de una clase.

### 4. ¿Todos los lenguajes orientados a objetos manejan el concepto de clase?
#### No, existe otro modelo llamado Programación basada en Prototipos.


## 6. ¿Dónde se almacenan en memoria los objetos? ¿Es igual en todos los lenguajes? ¿Qué es la **recolección de basura**? 

### Respuesta
### 1. ¿Dónde se almacenan los objetos?
#### En la inmensa mayoría de los lenguajes modernos orientados a objetos (Java, C#, Python, JavaScript), la respuesta se divide en dos partes:

#### El Objeto (La información real): Se almacena en el Heap (Montón).

#### Es un espacio de memoria grande y desordenado donde se guardan los datos complejos. Aquí es donde realmente "vive" la instancia con todos sus atributos.

#### La Referencia (El puntero): Se almacena en el Stack (Pila).

#### Es un espacio de memoria pequeño, muy rápido y ordenado. Aquí vive la variable que creaste. Esa variable no contiene el objeto, sino la dirección de memoria (una flecha) que apunta hacia donde está el objeto en el Heap.

## 7. ¿Qué es un método? ¿Qué es la **sobrecarga de métodos**? 

### Respuesta

### 1. ¿Qué es un método?
#### En términos simples, un método es una función que vive dentro de una clase.

#### Si los atributos (variables) son los sustantivos que definen "qué es" o "qué tiene" el objeto, los métodos son los verbos que definen "qué hace". Representan el comportamiento del objeto.

#### ¿Para qué sirven? Para manipular los datos internos del objeto (su estado) o para realizar operaciones con ellos.

#### Anatomía básica: Un método suele tener un nombre, una lista de parámetros (lo que necesita para funcionar) y un tipo de retorno (lo que devuelve al terminar).

### 2. ¿Qué es la Sobrecarga de Métodos (Method Overloading)?
#### La sobrecarga es la capacidad de definir múltiples métodos con el mismo nombre dentro de la misma clase, pero con diferentes parámetros.


## 8. Ejemplo mínimo de clase en Java, que se llame Punto, con dos atributos, x e y, con un método que se llame `calculaDistanciaAOrigen`, que calcule la distancia a la posición 0,0. Por sencillez, los atributos deben tener visibilidad por defecto. Crea además un ejemplo de uso con una instancia y uso del método

### Respuesta

public class Punto {
    // 1. Atributos
    // Al no poner 'public' ni 'private', tienen visibilidad por defecto (package-private)
    double x;
    double y;

    // 2. Método
    // Calcula la hipotenusa usando el Teorema de Pitágoras
    double calculaDistanciaAOrigen() {
        return Math.sqrt((x * x) + (y * y));
    }
}

// Clase para probar el ejemplo
class Main {
    public static void main(String[] args) {
        // A. Crear una instancia (Objeto) de la clase Punto
        Punto miPunto = new Punto();

        // B. Asignar valores al Estado del objeto
        // Accedemos directamente porque la visibilidad lo permite
        miPunto.x = 3;
        miPunto.y = 4;

        // C. Usar el Comportamiento (Llamar al método)
        double distancia = miPunto.calculaDistanciaAOrigen();

        // Mostrar resultado
        System.out.println("La coordenada X es: " + miPunto.x);
        System.out.println("La coordenada Y es: " + miPunto.y);
        System.out.println("La distancia al origen (0,0) es: " + distancia);
    }
}


## 9. ¿Cuál es el punto de entrada en un programa en Java? ¿Qué es `static` y para qué vale? ¿Sólo se emplea para ese método `main`? ¿Para qué se combina con `final`?

### Respuesta

#### 1. El punto de entrada absoluto es el método main.

#### 2. La palabra clave static rompe la regla habitual de la POO que dice que "necesitas crear un objeto para usar las cosas".

#### Significado: Cuando marcas algo como static, indicas que ese elemento pertenece a la clase (al molde), no a las instancias (a los objetos).

#### 3. ¿Sólo se emplea para ese método main?
No, en absoluto. Se usa muchísimo en otros contextos.

## 10. Intenta ejecutar un poco de Java de forma básica, con los comandos `javac` y `java`. ¿Cómo podemos compilar el programa y ejecutarlo desde linea de comandos? ¿Java es compilado? ¿Qué es la **máquina virtual**? ¿Qué es el *byte-code* y los ficheros `.class`?

### Respuesta

### 1. Cómo compilar y ejecutar desde la línea de comandos
### Supongamos que tienes un archivo llamado HolaMundo.java con el código fuente.

### Paso A: Compilación (javac) El comando javac significa Java Compiler. Convierte tu código legible por humanos en el formato interno de Java.


### javac HolaMundo.java
### Si todo va bien: No verás ningún mensaje, pero aparecerá un nuevo archivo en tu carpeta llamado HolaMundo.class.

### Si hay errores: La terminal te escupirá una lista de fallos de sintaxis.

### Paso B: Ejecución (java) El comando java invoca a la Máquina Virtual.

### Bash
### java HolaMundo

## 11. En el código anterior de la clase `Punto` ¿Qué es `new`? ¿Qué es un **constructor**? Pon un ejemplo de constructor en una clase `Empleado` que tenga DNI, nombre y apellidos

### Respuesta

Aquí tienes la explicación detallada de estos dos conceptos que son el "Big Bang" de cualquier objeto.

### 1. ¿Qué es new?
#### new es un operador de Java (y de muchos otros lenguajes como C++ o C#) que sirve para solicitar memoria nueva.

#### Cuando el programa lee la palabra new:

#### Va a la memoria RAM (al Heap).

#### Busca un espacio libre lo suficientemente grande para guardar tu objeto.

#### Reserva ese espacio y llama al constructor.

#### Devuelve la dirección de memoria (referencia) donde se creó el objeto.

### 2. ¿Qué es un Constructor?
#### Un constructor es un método especial que se ejecuta automáticamente e inmediatamente después de usar new. Su única misión es inicializar el objeto, es decir, preparar sus datos iniciales para que el objeto nazca con valores válidos.

public class Empleado {
    // Atributos
    String dni;
    String nombre;
    String apellidos;

    // --- EL CONSTRUCTOR ---
    // 1. Se llama igual que la clase: Empleado
    // 2. Recibe los parámetros necesarios para rellenar los datos
    public Empleado(String dniIngresado, String nombreIngresado, String apellidosIngresados) {
        // Asignamos lo que nos pasan (parámetros) a los atributos del objeto
        this.dni = dniIngresado;
        this.nombre = nombreIngresado;
        this.apellidos = apellidosIngresados;
        
        System.out.println("¡Se ha construido un nuevo empleado en memoria!");
    }

    // Método normal para probar que funciona
    public void presentarse() {
        System.out.println("Hola, soy " + nombre + " " + apellidos + " con DNI " + dni);
    }
}

// Clase Principal para probarlo
class Main {
    public static void main(String[] args) {
        
        // USO DE NEW Y EL CONSTRUCTOR
        // Java lee esto así: 
        // 1. "new": Reserva memoria.
        // 2. "Empleado(...)": Ejecuta el código del constructor llenando los datos.
        Empleado empleado1 = new Empleado("12345678A", "Laura", "Gómez");
        
        // Probamos el objeto
        empleado1.presentarse();
        
        // Si intentaras hacer esto daría ERROR, porque borramos el constructor vacío:
        // Empleado empleado2 = new Empleado(); // <--- Esto ya no está permitido
    }
}


## 12. ¿Qué es la referencia `this`? ¿Se llama igual en todos los lenguajes? Pon un ejemplo del uso de `this` en la clase `Punto`

### Respuesta

### 1. ¿Qué es la referencia this?
#### this es una palabra reservada que actúa como un puntero al propio objeto que está ejecutando el código en ese momento.

### 2. ¿Se llama igual en todos los lenguajes?
#### No. El concepto es universal en la POO, pero la palabra clave cambia:

#### this: Se usa en Java, C#, C++, JavaScript, PHP (como $this).

#### self: Se usa en Python, Ruby, Swift, Objective-C.

### 3. Ejemplo en la clase Punto
#### El uso más común es en el constructor. Fíjate en este problema: queremos que los parámetros de entrada se llamen x e y para que sea claro, pero los atributos de la clase también se llaman x e y.


## 13. Añade ahora otro nuevo método que se llame `distanciaA`, que reciba un `Punto` como parámetro y calcule la distancia entre `this` y el punto proporcionado

### Respuesta

public class Punto {
    double x;
    double y;

    // Constructor
    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }

    // --- NUEVO MÉTODO ---
    // Recibe otro objeto de tipo Punto como parámetro
    public double distanciaA(Punto otroPunto) {
        // 1. Calculamos la diferencia en el eje X
        // 'this.x' es MI coordenada. 'otroPunto.x' es la TUYA.
        double catetoX = this.x - otroPunto.x;

        // 2. Calculamos la diferencia en el eje Y
        double catetoY = this.y - otroPunto.y;

        // 3. Aplicamos Pitágoras: raíz cuadrada de (catetoX² + catetoY²)
        return Math.sqrt((catetoX * catetoX) + (catetoY * catetoY));
    }
}

class Main {
    public static void main(String[] args) {
        // Creamos dos objetos distintos
        Punto p1 = new Punto(0, 0);  // Punto en el origen
        Punto p2 = new Punto(3, 4);  // Punto alejado

        // Calculamos la distancia desde p1 hasta p2
        // Aquí: p1 es 'this' y p2 es 'otroPunto'
        double distancia = p1.distanciaA(p2);

        System.out.println("La distancia entre los puntos es: " + distancia);
        
        // Curiosidad: La distancia debe ser igual al revés
        // Aquí: p2 es 'this' y p1 es 'otroPunto'
        System.out.println("La distancia inversa es: " + p2.distanciaA(p1));
    }
}


## 14. El paso del `Punto` como parámetro a un método, es **por copia** o **por referencia**, es decir, si se cambia el valor de algún atributo del punto pasado como parámetro, dichos cambios afectan al objeto fuera del método? ¿Qué ocurre si en vez de un `Punto`, se recibiese un entero (`int`) y dicho entero se modificase dentro de la función? 

### Respuesta

### La respuesta corta y técnica es: Java SIEMPRE pasa los argumentos por valor (por copia).

### 1. El caso del Objeto (Punto)
### Cuando pasas un objeto como parámetro:

### Lo que se copia: No se copia el objeto entero (la casa). Se copia la referencia (la dirección de memoria o "la llave de la casa").

### El efecto: Tienes dos variables (la de fuera y el parámetro de dentro) que tienen copias idénticas de la llave. Ambas abren la misma puerta.

### ¿Afectan los cambios? SÍ. Si dentro del método usas esa llave (referencia) para entrar al objeto y modificar sus atributos (como p.x = 99), el objeto original se modifica, porque solo hay un objeto en el Heap.

### 2. El caso del Primitivo (int)
### Cuando pasas un tipo primitivo (int, double, boolean):

### Lo que se copia: Se copia el valor literal de los datos.

### El efecto: Tienes dos variables totalmente independientes.

### ¿Afectan los cambios? NO. Si dentro del método cambias el valor, solo estás cambiando la copia local. La variable original fuera del método permanece intacta.


## 15. ¿Qué es el método `toString()` en Java? ¿Existe en otros lenguajes? Pon un ejemplo de `toString()` en la clase `Punto` en Java

### Respuesta

### 1. ¿Qué es el método toString() en Java?
### En Java, todas las clases que creas (como Punto, Empleado, etc.) descienden automáticamente de una clase madre suprema llamada Object.

### La clase Object tiene un método llamado toString(). Su función es devolver una cadena de texto (String) que represente al objeto.

### El problema del comportamiento por defecto: Si tú no tocas nada, el toString() original de Java devuelve algo muy feo y poco útil para humanos: el nombre de la clase seguido de una arroba y un código hexadecimal (hash code).

### 2. ¿Existe en otros lenguajes?
### Sí, absolutamente. Casi todos los lenguajes orientados a objetos tienen un mecanismo equivalente para convertir un objeto a texto, aunque el nombre cambia




## 16. Reflexiona: ¿una clase es como un `struct` en C? ¿Qué le falta al `struct` para ser como una clase y las variables de ese tipo ser instancias?


### Respuesta

### Esa es una reflexión muy aguda. De hecho, históricamente, la clase es la evolución directa del struct del lenguaje C.

### Podríamos decir que una clase es un struct con esteroides (o con "vida propia").

### Aquí tienes el análisis de la evolución de uno a otro:

### 1. La Semejanza: El contenedor de datos
### En C, un struct sirve para agrupar datos relacionados bajo un mismo nombre.

C (struct):

C
struct Punto {
    int x;
    int y;
};
Java (class):

Java
class Punto {
    int x;
    int y;
}

### 2. ¿Qué le falta al struct de C para ser una Clase?
### Para que ese struct pasivo se convierta en un Objeto real (una instancia de una clase), le faltan cuatro superpoderes que C no tiene de forma nativa:

### A. Comportamiento Integrado (Métodos + this)
### Esta es la diferencia fundamental.

### En C (Struct): Los datos son pasivos. Las funciones están "flotando" fuera del struct. Tú tienes que pasar el struct a la función.

### Lógica: calcular_distancia(mi_struct_punto); -> La función actúa sobre el dato.

### En POO (Clase): Los datos son activos. Las funciones (métodos) viven dentro de la definición y saben acceder a sus propios datos (usando this).

### Lógica: mi_objeto_punto.calcular_distancia(); -> El objeto actúa sobre sí mismo.

### B. Encapsulamiento (Protección)
### En C (Struct): Un struct es transparente. Todo es público. Cualquier parte del código puede hacer p.x = -5000; y romper la lógica de tu programa. No hay forma nativa de decir "esta variable es privada".

### En POO (Clase): Puedes usar private. Esto te permite controlar el acceso y obligar a usar métodos (como setX(int valor)) para validar que los datos sean correctos antes de guardarlos.

### C. Constructores (Nacimiento controlado)
### En C (Struct): Cuando creas un struct, a menudo contiene "basura" de la memoria hasta que tú manualmente le asignas valores.

### C
### struct Punto p; // p.x y p.y tienen valores aleatorios/basura
### p.x = 0;        // Tienes que acordarte de limpiarlo
### En POO (Clase): El constructor garantiza que nunca existirá un objeto en un estado inválido o sucio. El código de inicialización se ejecuta automáticamente al nacer (new).

### D. Herencia y Polimorfismo
### En C (Struct): No puedes decir struct Coche hereda de struct Vehiculo. Tienes que usar trucos complejos (como poner un struct dentro de otro) para simularlo.

### En POO (Clase): Es nativo. Una clase extiende a otra y el sistema de tipos entiende la jerarquía automáticamente.


## 17. Quitemos un poco de magia a todo esto: ¿Como se podría “emular”, con `struct` en C, la clase `Punto`, con su función para calcular la distancia al origen? ¿Qué ha pasado con `this`?

### Respuesta

### 1. El Código en C (Emulación manual de POO)
### Para emular la clase, necesitamos dos cosas separadas: una estructura para los datos y una función suelta para el comportamiento.

C
#include <stdio.h>
#include <math.h>

// 1. LA CLASE (Solo datos)
// En C, el struct define la plantilla de memoria, pero no tiene funciones dentro.
typedef struct {
    double x;
    double y;
} Punto;

// 2. EL MÉTODO (Función externa)
// Fíjate en el primer parámetro. En Java es invisible, en C es OBLIGATORIO.
// Usamos un puntero (*) para no trabajar con una copia, sino con el original.
double Punto_calculaDistanciaAOrigen(Punto* este_objeto) {
    // En lugar de 'this.x', usamos la flecha '->' para acceder vía puntero
    double catetoX = este_objeto->x;
    double catetoY = este_objeto->y;
    
    return sqrt((catetoX * catetoX) + (catetoY * catetoY));
}

// 3. USO EN MAIN
int main() {
    // A. "Constructor" manual (Instanciación)
    Punto p1;
    p1.x = 3.0;
    p1.y = 4.0;

    // B. Llamada al "Método"
    // En Java harías: p1.calculaDistanciaAOrigen()
    // En C, pasamos la dirección de memoria (&) del objeto manualmente.
    double distancia = Punto_calculaDistanciaAOrigen(&p1);

    printf("Distancia: %f\n", distancia);
    return 0;
}
### 2. ¿Qué ha pasado con this?
### ¡Ahí está la clave! En el código de C que acabo de escribir, this se ha vuelto visible.

### En el ejemplo de C, lo he llamado este_objeto (para que sea obvio), pero es exactamente lo mismo.

### En Java (Implícito): Cuando escribes p1.metodo(), el compilador de Java reescribe esa línea en secreto. Lo que realmente le dice a la máquina es: "Busca la función metodo y pásale p1 como primer argumento oculto". Ese argumento oculto es lo que dentro llamamos this.

### En C (Explícito): Como el lenguaje no hace magia por ti, tú tienes que declarar ese primer parámetro (Punto* este_objeto) y tú tienes que pasar el puntero manualmente (&p1).