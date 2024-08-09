# ¿Qué son los tipos de datos?

Los **tipos de datos** son una categoría fundamental en la programación que define la clase de datos que una variable puede almacenar. Un tipo de dato no solo determina el tipo de valores que una variable puede contener, sino también las operaciones que se pueden realizar sobre esos valores.

#### Clasificación de los Tipos de Datos

1. **Tipos de datos primitivos**: Son los tipos de datos más básicos que proporciona el lenguaje de programación. En Java, existen ocho tipos de datos primitivos:
   - **byte**: Es un tipo entero de 8 bits, su rango va de -128 a 127.
   - **short**: Es un tipo entero de 16 bits, con un rango de -32,768 a 32,767.
   - **int**: Es el tipo entero más común, de 32 bits, con un rango de -2^31 a 2^31 - 1.
   - **long**: Es un tipo entero de 64 bits, con un rango muy amplio de -2^63 a 2^63 - 1.
   - **float**: Es un tipo de punto flotante (número con decimales) de 32 bits.
   - **double**: Es un tipo de punto flotante de 64 bits, y es el tipo de datos para números decimales más utilizado en Java.
   - **char**: Es un tipo de datos de 16 bits que almacena un solo carácter Unicode.
   - **boolean**: Es un tipo de datos que solo puede tener dos valores: `true` o `false`.

2. **Tipos de datos referenciados** (o **no primitivos**): Estos son tipos de datos más complejos que se basan en objetos. Incluyen:
   - **Strings**: En Java, una cadena de texto se representa mediante la clase `String`. A diferencia de los tipos de datos primitivos, `String` es un objeto.
   - **Arrays**: Es una colección de elementos del mismo tipo de datos.
   - **Clases**: Son la base de la programación orientada a objetos. Definen la estructura de los objetos, que pueden tener variables de instancia y métodos.
   - **Interfaces** y **Enums**: Otros tipos de referencia que ayudan a definir comportamientos y constantes.

#### Importancia de los Tipos de Datos

El tipo de dato de una variable determina:
- **Memoria**: Cuánta memoria ocupará la variable.
- **Operaciones**: Qué operaciones son válidas. Por ejemplo, no se pueden sumar directamente una `String` y un `int` sin conversión.
- **Rendimiento**: Elegir el tipo de dato adecuado puede optimizar el rendimiento del programa.

### ¿Qué son las variables?

Una **variable** es un contenedor de datos que almacena un valor que puede cambiar durante la ejecución del programa. Se puede pensar en una variable como un "nombre" para un lugar específico en la memoria de la computadora donde se almacena un dato. 

#### Características de las Variables

1. **Nombre**: Identificador que se utiliza para acceder a la variable.
2. **Tipo de dato**: Especifica qué tipo de valor puede almacenar la variable.
3. **Valor**: El dato real almacenado en la variable.
4. **Alcance**: Define en qué parte del programa la variable es accesible.
5. **Duración**: Indica cuánto tiempo vive la variable durante la ejecución del programa.

#### Declaración y Inicialización

En Java, una variable debe ser declarada antes de que se pueda usar. La declaración de una variable sigue la siguiente estructura:

```java
tipo_de_dato nombre_de_variable;
```

Por ejemplo:

```java
int numero;
```

Aquí, `int` es el tipo de dato, y `numero` es el nombre de la variable.

La **inicialización** es el proceso de asignar un valor a la variable por primera vez. Esto puede hacerse en el momento de la declaración:

```java
int numero = 10;
```

También se puede declarar primero y luego asignar un valor:

```java
int numero;
numero = 10;
```

### Aplicación en Java

Ahora que entendemos los tipos de datos y las variables, veamos cómo se aplican en el lenguaje de programación Java.

#### Ejemplo Básico

Imaginemos que queremos crear un programa en Java que sume dos números enteros y muestre el resultado.

```java
public class Suma {
    public static void main(String[] args) {
        int numero1 = 5;  // Declaración e inicialización de la primera variable
        int numero2 = 10; // Declaración e inicialización de la segunda variable

        int resultado = numero1 + numero2; // Uso de las variables para realizar una operación

        System.out.println("La suma es: " + resultado); // Imprimir el resultado
    }
}
```

En este ejemplo:

1. Hemos utilizado el tipo de dato `int` para declarar tres variables: `numero1`, `numero2` y `resultado`.
2. `numero1` y `numero2` se inicializan con los valores 5 y 10, respectivamente.
3. `resultado` se inicializa con el resultado de sumar `numero1` y `numero2`.
4. Finalmente, usamos `System.out.println` para imprimir el valor de `resultado`.

#### Alcance de las Variables

En Java, el alcance de una variable depende de dónde se declara:
- **Variables locales**: Declaradas dentro de un método y solo accesibles dentro de ese método.
- **Variables de instancia**: Declaradas dentro de una clase pero fuera de cualquier método. Son accesibles para todos los métodos de la clase.
- **Variables de clase** (o estáticas): Declaradas con el modificador `static`, son compartidas por todas las instancias de la clase.

#### Ejemplo de Variables con Diferente Alcance

```java
public class EjemploAlcance {
    static int numeroClase = 20; // Variable de clase

    int numeroInstancia = 15; // Variable de instancia

    public void metodoEjemplo() {
        int numeroLocal = 5; // Variable local

        System.out.println("Número local: " + numeroLocal);
        System.out.println("Número de instancia: " + numeroInstancia);
        System.out.println("Número de clase: " + numeroClase);
    }

    public static void main(String[] args) {
        EjemploAlcance ejemplo = new EjemploAlcance();
        ejemplo.metodoEjemplo();
    }
}
```

En este ejemplo:
- `numeroClase` es una variable de clase que puede ser accedida por cualquier instancia de la clase `EjemploAlcance`.
- `numeroInstancia` es una variable de instancia que solo es accesible a través de la instancia `ejemplo`.
- `numeroLocal` es una variable local solo accesible dentro del método `metodoEjemplo`.

### Conclusión

En resumen, los tipos de datos y las variables son componentes esenciales en cualquier lenguaje de programación, incluyendo Java. Los tipos de datos definen el tipo de información que se puede almacenar y manipular, mientras que las variables actúan como contenedores para esa información. Entender cómo declararlas, inicializarlas y utilizarlas correctamente es fundamental para escribir código eficiente y funcional en Java.