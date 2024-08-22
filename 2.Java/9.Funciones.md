# Funciones en java

Las **funciones**, también conocidas como **métodos** en Java, son bloques de código que realizan una tarea específica y que pueden ser invocados desde otras partes del programa. Las funciones permiten reutilizar código, mejorar la organización y facilitar el mantenimiento de aplicaciones.

### Estructura de una Función en Java

Una función en Java tiene una estructura básica que incluye los siguientes elementos:

1. **Modificadores de acceso** (opcional): Determinan quién puede acceder a la función (ej. `public`, `private`, `protected`).
2. **Tipo de retorno**: Indica el tipo de dato que devuelve la función (ej. `int`, `String`, `void` si no retorna nada).
3. **Nombre de la función**: Debe ser representativo de lo que hace la función. Por convención, el nombre empieza con minúscula y sigue la notación camelCase.
4. **Parámetros** (opcional): Datos que la función puede recibir para procesarlos.
5. **Cuerpo de la función**: Contiene las instrucciones que se ejecutan cuando se llama a la función.
6. **Valor de retorno** (opcional): Si la función no es `void`, debe retornar un valor compatible con el tipo de retorno.

### Ejemplo Básico de una Función en Java

Supongamos que queremos crear una función que sume dos números enteros:

```java
public int sumar(int a, int b) {
    int resultado = a + b;
    return resultado;
}
```

#### Explicación del código:

- `public`: El modificador de acceso, que permite que la función sea accesible desde cualquier parte del programa.
- `int`: El tipo de retorno, indicando que la función devolverá un número entero.
- `sumar`: El nombre de la función.
- `(int a, int b)`: Los parámetros, que son dos números enteros que se pasan a la función.
- `int resultado = a + b;`: Dentro del cuerpo, se realiza la operación de suma y se almacena en una variable.
- `return resultado;`: La función devuelve el valor almacenado en `resultado`.

### Invocación de la Función

Para usar esta función, podrías hacerlo de la siguiente manera:

```java
public class Main {
    public static void main(String[] args) {
        Main calculadora = new Main();
        int resultado = calculadora.sumar(5, 3);
        System.out.println("El resultado es: " + resultado);
    }

    public int sumar(int a, int b) {
        return a + b;
    }
}
```

### Tipos de Funciones en Java

1. **Funciones sin retorno (`void`)**:
   Estas funciones no devuelven ningún valor. Solo ejecutan un bloque de código.

   Ejemplo:

   ```java
   public void saludar() {
       System.out.println("¡Hola, bienvenido!");
   }
   ```

   Invocación:

   ```java
   saludar();
   ```

2. **Funciones con retorno**:
   Estas funciones devuelven un valor específico después de realizar sus operaciones.

   Ejemplo:

   ```java
   public String obtenerSaludo(String nombre) {
       return "Hola, " + nombre;
   }
   ```

   Invocación:

   ```java
   String saludo = obtenerSaludo("Agustín");
   System.out.println(saludo);
   ```

3. **Funciones con parámetros**:
   Estas funciones reciben datos que luego procesan.

   Ejemplo:

   ```java
   public int multiplicar(int x, int y) {
       return x * y;
   }
   ```

   Invocación:

   ```java
   int producto = multiplicar(4, 5);
   System.out.println(producto);
   ```

4. **Sobrecarga de funciones**:
   Es posible definir varias funciones con el mismo nombre pero diferentes parámetros, lo que se llama sobrecarga.

   Ejemplo:

   ```java
   public int sumar(int a, int b) {
       return a + b;
   }

   public double sumar(double a, double b) {
       return a + b;
   }
   ```

   Dependiendo de los tipos de datos que pases, se ejecutará la versión adecuada.

### Importancia de las Funciones

- **Reutilización de código**: Puedes llamar una función varias veces sin reescribir el código.
- **Mantenibilidad**: El código está mejor organizado y es más fácil de leer.
- **Modularidad**: Divides tu programa en pequeños bloques que se encargan de tareas específicas.

Las funciones son una parte fundamental de cualquier lenguaje de programación y permiten construir aplicaciones de forma más eficiente y ordenada.