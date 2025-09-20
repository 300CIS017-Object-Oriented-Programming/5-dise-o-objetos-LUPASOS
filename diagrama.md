### **Ejercicio 1: Práctica Independiente**
```mermaid   
classDiagram
    class Libro {
        - string titulo
        - string autor
        - string genero
        - int id
        - bool prestado
        + prestar()
        + devolver()
    }
    class Usuario {
        - int id
        - string nombre
        + pedirPrestado(Libro)
        + devolverLibro(Libro)

    }
        
        class Prestamo {
        - string fechaInicio
        - string fechaDevolucion

    }
    class Biblioteca {
        - Libro[] catalogo
        + agregarLibro(Libro)
        + listarDisponibles()
    }

    Biblioteca o-- Libro : se contiene
    Biblioteca o-- Usuario : se registra

``` 


### Ejercicio 2: Definir el Enunciado de un Problema a Partir de UML Diagrama : Sistema de Gestión de Pedidos en un Restaurante

### **Diagrama : Sistema de Gestión de Pedidos en un Restaurante**

```mermaid
classDiagram
    class Cliente {
        +string nombre
        +string telefono
    }
    class Pedido {
        +int numeroPedido
        +string estado
        +Cliente cliente
        +list<Plato> platos
    }
    class Plato {
        +string nombre
        +float precio
    }
    Pedido o-- Plato : contiene
    Pedido --> Cliente : pertenece a
``` 

- El sistema que se muestra en el diagrama es básicamente la forma en la que un restaurante organiza los pedidos. 
  Cada pedido tiene un número, un estado (si está en preparación, entregado, etc.), está hecho por un cliente y dentro del pedido se guardan los platos que pidió. 
  El cliente tiene datos simples como nombre y teléfono, y cada plato tiene un nombre y un precio.

- Las relaciones son bastante lógicas: el pedido siempre pertenece a un cliente, porque alguien tiene que hacer la orden, y al mismo tiempo el pedido contiene varios platos, 
  que son lo que realmente define lo que se va a preparar y cuánto cuesta. Esto es importante porque el restaurante necesita saber quién hizo el pedido y qué fue lo que pidió, 
  así se puede llevar un control claro de las órdenes y dar un buen servicio.




  
### Ejercicio 3: Modelando un Sistema de Control de Versiones


```mermaid
classDiagram
    class Usuario {
    - string nombre
      - string correo
      - list<Repositorio*> repositorios
      + crearRepositorio(string)
      }
      class Repositorio {
      - string nombre 
      - list<Commit*> historialCommits  
      + agregarCommit(Commit*) 
      }

%%profe no le voy a mentir, este si me dio chat, no lo supe hacer la del repositorio, y se ve la hora a la que estoy mandando tampoco me queda mucho jajs, pero esto esta entendible, es meterle cabeza nomas

      class Commit {
      - string id
      - string mensaje
      - string fecha
      - Usuario* autor
      - list<Archivo*> archivos
      + agregarArchivo(Archivo*)
      }
      class Archivo {
      - string nombre
      - string contenido
      + actualizarContenido(string)
      }
    
          Usuario <-- Repositorio : posee
          Repositorio <-- Commit : almacena
          Commit <-- Archivo : modifica
          Commit --> Usuario : autor
```