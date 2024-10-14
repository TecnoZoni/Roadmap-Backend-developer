# Patrones de diseño VS Arquitecturas de software

Los **patrones de diseño** y las **arquitecturas de software** son dos conceptos relacionados, pero se enfocan en diferentes niveles de abstracción y resolución de problemas en el desarrollo de software. Ambos son fundamentales para escribir software mantenible, escalable y eficiente, pero tienen aplicaciones distintas.

### 1. **Patrones de diseño**

Los **patrones de diseño** son soluciones reutilizables para problemas comunes en el desarrollo de software. Son una forma de organizar y estructurar el código en un nivel de implementación, es decir, en la manera en que las clases, objetos y sus interacciones están organizadas para cumplir una función específica. Los patrones de diseño son más concretos y aplican a problemas que surgen durante la programación de funcionalidades dentro de una aplicación.

Existen varios tipos de patrones de diseño, los más comunes son:
- **Creacionales**: se enfocan en cómo crear objetos.
- **Estructurales**: tratan sobre la composición de clases u objetos.
- **Comportamentales**: se centran en cómo las clases y los objetos interactúan y se comunican entre sí.

#### Ejemplos de patrones de diseño en Java

1. **Patrón Singleton** (Creacional):
   - Este patrón garantiza que una clase tenga solo una instancia y proporciona un punto de acceso global a esa instancia. Es útil cuando necesitas que solo un objeto controle un recurso.
   
   **Ejemplo en Java**:
   ```java
   public class Singleton {
       private static Singleton instancia;
       
       // Constructor privado para evitar la creación de objetos desde fuera
       private Singleton() {}

       // Método para obtener la única instancia
       public static Singleton getInstance() {
           if (instancia == null) {
               instancia = new Singleton();
           }
           return instancia;
       }
   }
   ```
   Aquí, la clase `Singleton` asegura que siempre haya una sola instancia de ella, independientemente de cuántas veces se llame a `getInstance()`.

2. **Patrón Factory** (Creacional):
   - Proporciona una interfaz para crear objetos en una superclase, pero permite a las subclases alterar el tipo de objetos que se crean. Este patrón es útil cuando se necesita crear objetos sin especificar su clase concreta en el código.

   **Ejemplo en Java**:
   ```java
   // Interfaz Producto
   interface Producto {
       void usar();
   }

   // Implementación concreta de Producto
   class ProductoA implements Producto {
       public void usar() {
           System.out.println("Usando Producto A");
       }
   }

   class ProductoB implements Producto {
       public void usar() {
           System.out.println("Usando Producto B");
       }
   }

   // Fábrica de productos
   class FabricaProducto {
       public Producto crearProducto(String tipo) {
           if (tipo.equals("A")) {
               return new ProductoA();
           } else if (tipo.equals("B")) {
               return new ProductoB();
           }
           return null;
       }
   }

   public class Main {
       public static void main(String[] args) {
           FabricaProducto fabrica = new FabricaProducto();
           Producto producto1 = fabrica.crearProducto("A");
           producto1.usar();  // Output: Usando Producto A
           
           Producto producto2 = fabrica.crearProducto("B");
           producto2.usar();  // Output: Usando Producto B
       }
   }
   ```
   Aquí, `FabricaProducto` crea instancias de `ProductoA` o `ProductoB` sin que el código de cliente necesite conocer las clases concretas.

3. **Patrón Observer** (Comportamental):
   - Define una dependencia uno a muchos entre objetos, de manera que cuando uno cambia su estado, todos sus dependientes son notificados y actualizados automáticamente. Este patrón es útil para aplicaciones que manejan eventos o cambios de estado.

   **Ejemplo en Java**:
   ```java
   interface Observador {
       void actualizar(String mensaje);
   }

   class Sujeto {
       private List<Observador> observadores = new ArrayList<>();

       public void agregarObservador(Observador observador) {
           observadores.add(observador);
       }

       public void notificarObservadores(String mensaje) {
           for (Observador observador : observadores) {
               observador.actualizar(mensaje);
           }
       }
   }

   class ObservadorConcreto implements Observador {
       private String nombre;

       public ObservadorConcreto(String nombre) {
           this.nombre = nombre;
       }

       public void actualizar(String mensaje) {
           System.out.println(nombre + " recibió mensaje: " + mensaje);
       }
   }

   public class Main {
       public static void main(String[] args) {
           Sujeto sujeto = new Sujeto();

           Observador observador1 = new ObservadorConcreto("Observador 1");
           Observador observador2 = new ObservadorConcreto("Observador 2");

           sujeto.agregarObservador(observador1);
           sujeto.agregarObservador(observador2);

           sujeto.notificarObservadores("Hola Observadores!");  // Ambos observadores reciben el mensaje
       }
   }
   ```

### 2. **Arquitecturas de Software**

Las **arquitecturas de software** son una estructura de alto nivel que define cómo los componentes de un sistema interactúan entre sí. Mientras que los patrones de diseño se enfocan en problemas a nivel de código, las arquitecturas de software se enfocan en la estructura general de toda la aplicación y cómo sus diferentes módulos o subsistemas se organizan para cumplir con los requerimientos del sistema. La arquitectura define los componentes principales y cómo estos se comunican, escalando el enfoque de solución de problemas a un nivel mucho más global y estratégico.

Algunas arquitecturas comunes son:
- **Arquitectura Monolítica**: Toda la lógica de la aplicación está dentro de un único código o ejecutable.
- **Arquitectura en Capas**: Organiza el sistema en capas como presentación, lógica de negocio, y acceso a datos.
- **Arquitectura de Microservicios**: Divide la aplicación en servicios más pequeños, autónomos, que pueden desarrollarse, desplegarse y escalarse de manera independiente.

#### Ejemplos de Arquitecturas de Software en Java

1. **Arquitectura en Capas (Layered Architecture)**:
   - Se divide el sistema en diferentes capas que tienen responsabilidades específicas, como capa de presentación, capa de negocio y capa de acceso a datos. Cada capa interactúa con las capas adyacentes, pero no más allá.

   **Ejemplo en Java**:
   - **Capa de presentación** (controladores):
     ```java
     @RestController
     public class ProductoController {
         @Autowired
         private ProductoService productoService;

         @GetMapping("/productos")
         public List<Producto> listarProductos() {
             return productoService.obtenerProductos();
         }
     }
     ```

   - **Capa de servicio** (lógica de negocio):
     ```java
     @Service
     public class ProductoService {
         @Autowired
         private ProductoRepository productoRepository;

         public List<Producto> obtenerProductos() {
             return productoRepository.findAll();
         }
     }
     ```

   - **Capa de acceso a datos** (repositorio):
     ```java
     @Repository
     public interface ProductoRepository extends JpaRepository<Producto, Long> {}
     ```

   Aquí, cada capa tiene una responsabilidad específica y se comunica con la siguiente capa para realizar operaciones.

2. **Arquitectura de Microservicios**:
   - Se trata de una forma de diseñar sistemas de software donde las funcionalidades del sistema se dividen en servicios pequeños, autónomos y desplegables de manera independiente. Cada servicio es responsable de una parte del sistema y se comunica con otros servicios a través de APIs, como REST.

   **Ejemplo en Java**:
   - **Microservicio de Productos**:
     ```java
     @RestController
     @RequestMapping("/productos")
     public class ProductoController {
         @GetMapping
         public List<Producto> obtenerProductos() {
             // Lógica para devolver productos
         }
     }
     ```

   - **Microservicio de Usuarios**:
     ```java
     @RestController
     @RequestMapping("/usuarios")
     public class UsuarioController {
         @GetMapping
         public List<Usuario> obtenerUsuarios() {
             // Lógica para devolver usuarios
         }
     }
     ```

   Los microservicios pueden ser desplegados de manera independiente, facilitando la escalabilidad y el mantenimiento.

### Diferencia clave entre patrones de diseño y arquitecturas:
- **Patrones de diseño** resuelven problemas a nivel de implementación en clases y objetos dentro de una aplicación.
- **Arquitecturas de software** son estrategias de más alto nivel para organizar toda la estructura de la aplicación, incluyendo cómo se dividen y comunican los componentes a gran escala.

En resumen, los patrones de diseño se enfocan en solucionar problemas específicos de diseño en el código, mientras que las arquitecturas de software abordan la organización global del sistema, asegurando que los diferentes componentes trabajen juntos eficientemente.