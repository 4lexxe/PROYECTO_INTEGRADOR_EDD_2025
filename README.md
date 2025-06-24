# GUÍA DE ORGANIZACIÓN - PROYECTO INTEGRADOR
## Sistema de Gestión de Biblioteca - Estructura de Datos 2025

**OBJETIVO PRINCIPAL:** Desarrollar un sistema de gestión de biblioteca que implemente registro/búsqueda de libros y usuarios, operaciones de préstamo/devolución, cola de espera para libros no disponibles, sistema de reversión de acciones, y consultas dinámicas mediante arreglos, árboles BST/AVL, pilas, colas y listas enlazadas.

---

## 👥 INTEGRANTES DEL EQUIPO

| Integrante | Estructura Asignada | Funcionalidades Específicas |
|------------|-------------------|------------------------------|
| **Calatayud, Alex Gabriel** | Árboles BST/AVL | Búsqueda eficiente de libros por código, inserción ordenada, recorridos |
| **Saavedra, Leandro Ariel** | Arreglos | Catálogo completo de libros, registro de usuarios, validaciones |
| **Torres, Rodrigo Emiliano** | Pilas y Colas | Sistema de reversión (deshacer), cola de espera para libros |
| **Lamas, Javier Ramiro** | Listas Enlazadas | Consultas por autor, filtrado de usuarios activos |

---

## 📋 DIVISIÓN DETALLADA DE TAREAS

### 🌳 Alex Gabriel Calatayud - ÁRBOLES BST/AVL

#### Funcionalidades del Sistema:
- **Búsqueda eficiente de libros por código** mediante árbol binario de búsqueda
- **Inserción ordenada** de nuevos libros manteniendo propiedades BST
- **Recorrido inorden** para mostrar catálogo ordenado por código
- **Balanceo automático** con rotaciones AVL cuando sea necesario
- **Eliminación de libros** con reestructuración del árbol

#### Entregables Específicos:
```java
// ArbolBST.java - Funcionalidades principales
public boolean insertarLibro(int codigo, String titulo, String autor, double precio)
public Libro buscarLibroPorCodigo(int codigo)
public boolean eliminarLibro(int codigo)
public List<Libro> obtenerCatalogoOrdenado()
public boolean verificarDisponibilidad(int codigo)

// ArbolAVL.java - Extensión con balanceo
private NodoArbol rotacionSimpleDerecha(NodoArbol nodo)
private NodoArbol rotacionSimpleIzquierda(NodoArbol nodo)
private int calcularFactorBalance(NodoArbol nodo)
public void rebalancearSiEsNecesario()
```

### 📚 Saavedra, Leandro Ariel - ARREGLOS

#### Funcionalidades del Sistema:
- **Almacenamiento del catálogo completo** en arreglo para visualización rápida
- **Registro de nuevos usuarios** con validación de datos únicos
- **Gestión de disponibilidad** de libros en el arreglo principal
- **Validaciones de códigos únicos** tanto para libros como usuarios
- **Actualización de cantidades** de libros prestados por usuario

#### Entregables Específicos:
```java
// GestorLibros.java - Arreglo principal
public boolean registrarLibro(int codigo, String titulo, String autor, double precio)
public void mostrarCatalogoCompleto()
public boolean marcarComoNoDisponible(int codigo)
public boolean marcarComoDisponible(int codigo)
public double calcularMontoTotalPrestamos()

// GestorUsuarios.java - Gestión de usuarios
public boolean registrarUsuario(int numeroUsuario, String dni, String nombre, String direccion, String telefono)
public Usuario buscarUsuarioPorNumero(int numeroUsuario)
public void incrementarLibrosPrestados(int numeroUsuario)
public void decrementarLibrosPrestados(int numeroUsuario)
public boolean validarCodigoUnico(int codigo)
```

### 🔄 Torres, Rodrigo Emiliano - PILAS & COLAS

#### Funcionalidades del Sistema:
- **Sistema de reversión** guardando operaciones en pila para función "deshacer"
- **Cola de espera** para usuarios que solicitan libros no disponibles
- **Procesamiento automático** de pendientes cuando hay disponibilidad
- **Registro de operaciones** con timestamp y detalles completos
- **Gestión de prioridades** en cola FIFO

#### Entregables Específicos:
```java
// PilaAcciones.java - Sistema de reversión
public void registrarOperacion(String tipo, int codigoLibro, int numeroUsuario, Date fecha)
public boolean revertirUltimaOperacion()
public Operacion verUltimaOperacion()
public boolean hayOperacionesParaRevertir()

// ColaPendientes.java - Gestión de espera
public void agregarUsuarioEnEspera(int numeroUsuario, int codigoLibro)
public Usuario procesarSiguientePendiente()
public boolean hayUsuariosEnEspera()
public int cantidadUsuariosEnEspera()
public void notificarDisponibilidad(int codigoLibro)
```

### 🔗 Lamas, Javier Ramiro - LISTAS ENLAZADAS

#### Funcionalidades del Sistema:
- **Búsqueda de libros por autor** usando subcadenas en lista enlazada
- **Filtrado de usuarios activos** con N o más libros prestados
- **Consultas dinámicas** que se construyen según criterios variables
- **Generación de reportes** personalizados con listas de resultados
- **Operaciones de filtrado** avanzadas con múltiples criterios

#### Entregables Específicos:
```java
// ListaLibrosAutor.java - Consultas por autor
public ListaEnlazada<Libro> buscarLibrosPorAutor(String subcadenaAutor)
public void agregarResultado(Libro libro)
public int contarResultados()
public void limpiarResultados()

// ListaUsuariosActivos.java - Consultas de usuarios
public ListaEnlazada<Usuario> obtenerUsuariosConMinimoPrestamos(int minimoLibros)
public void filtrarPorCantidadPrestamos(int cantidad)
public double calcularPromedioPrestamosPorUsuario()
public void generarReporteUsuariosActivos()

// ConsultasDinamicas.java - Motor de consultas
public ListaEnlazada<Object> ejecutarConsultaPersonalizada(String criterio, Object valor)
```

---

## 📚 FUNDAMENTOS TEÓRICOS - ESTRUCTURAS DE DATOS

### 🔢 ARREGLOS (Arrays)
**Responsable:** Leandro Ariel Saavedra

#### Conceptos Fundamentales:
- **Definición:** Estructura de datos estática que almacena elementos del mismo tipo
- **Acceso:** Directo mediante índice O(1)
- **Inserción/Eliminación:** O(n) en el peor caso
- **Búsqueda lineal:** O(n)

#### Implementación en el Proyecto:
```java
// Estructura básica para libros
private Libro[] catalogoLibros;
private int cantidadLibros;
private final int CAPACIDAD_MAXIMA = 1000;

// Operaciones principales
public boolean agregarLibro(Libro libro)
public Libro buscarPorCodigo(int codigo)
public void mostrarCatalogo()
```

#### Ventajas en Biblioteca:
- Acceso rápido para mostrar catálogo completo
- Memoria contigua, eficiente para recorridos
- Implementación simple y directa

### 🌳 ÁRBOLES BINARIOS DE BÚSQUEDA (BST) Y AVL
**Responsable:** Alex Gabriel Calatayud

#### Árbol Binario de Búsqueda:
- **Propiedad:** Nodo izquierdo < Raíz < Nodo derecho
- **Búsqueda promedio:** O(log n)
- **Peor caso:** O(n) cuando está desbalanceado

#### Árboles AVL:
- **Factor de balance:** |altura(izq) - altura(der)| ≤ 1
- **Rotaciones:** Simple derecha/izquierda, doble LR/RL
- **Garantía:** O(log n) en todas las operaciones

#### Implementación Detallada:
```java
public class NodoArbol {
    int codigo;
    Libro libro;
    NodoArbol izquierdo, derecho;
    int altura; // Para AVL
}

// Operaciones AVL específicas
private int obtenerAltura(NodoArbol nodo)
private int obtenerBalance(NodoArbol nodo)
private NodoArbol rotarDerecha(NodoArbol y)
private NodoArbol rotarIzquierda(NodoArbol x)
```

#### Casos de Uso en Biblioteca:
- Búsqueda eficiente de libros por código
- Mantenimiento automático del orden
- Recorrido inorden para listado ordenado

### 📚 PILAS (Stack) - LIFO
**Responsable:** Rodrigo Emiliano Torres

#### Principios Fundamentales:
- **LIFO:** Last In, First Out
- **Operaciones básicas:** Push, Pop, Top, IsEmpty
- **Complejidad:** O(1) para todas las operaciones básicas

#### Implementación con Array:
```java
public class PilaAcciones {
    private Operacion[] pila;
    private int tope;
    private final int CAPACIDAD = 100;
    
    public void apilar(Operacion operacion)
    public Operacion desapilar()
    public boolean estaVacia()
    public Operacion verTope()
}
```

#### Aplicación - Sistema de Reversión:
- Almacenar operaciones de préstamo/devolución
- Implementar función "Deshacer" (Undo)
- Mantener historial de cambios

### 🚶 COLAS (Queue) - FIFO
**Responsable:** Rodrigo Emiliano Torres

#### Principios Fundamentales:
- **FIFO:** First In, First Out
- **Operaciones:** Enqueue, Dequeue, Front, IsEmpty
- **Implementación circular:** Optimizar uso de memoria

#### Implementación Circular:
```java
public class ColaPendientes {
    private Usuario[] cola;
    private int frente, atras, cantidad;
    private final int CAPACIDAD = 50;
    
    public void encolar(Usuario usuario)
    public Usuario desencolar()
    public boolean estaLlena()
public int obtenerTamaño()
}
```

#### Aplicación - Gestión de Espera:
- Cola de usuarios esperando libros no disponibles
- Procesamiento automático cuando hay disponibilidad
- Garantizar orden justo de atención

### 🔗 LISTAS ENLAZADAS
**Responsable:** Javier Ramiro Lamas

#### Tipos de Implementación:
1. **Simple:** Un enlace por nodo
2. **Doble:** Enlaces anterior y siguiente
3. **Circular:** Último nodo apunta al primero

#### Estructura de Nodo:
```java
public class NodoLista<T> {
    T dato;
    NodoLista<T> siguiente;
    NodoLista<T> anterior; // Para lista doble
    
    public NodoLista(T dato) {
        this.dato = dato;
        this.siguiente = null;
        this.anterior = null;
    }
}
```

#### Operaciones Principales:
```java
public class ListaEnlazada<T> {
    private NodoLista<T> cabeza;
    private int tamaño;
    
    public void insertarAlInicio(T dato)
    public void insertarAlFinal(T dato)
    public void insertarEnPosicion(int posicion, T dato)
    public boolean eliminar(T dato)
    public T buscar(Predicate<T> criterio)
    public List<T> filtrar(Predicate<T> criterio)
}
```

#### Aplicaciones en Biblioteca:
- Lista dinámica de libros por autor
- Lista de usuarios con N+ libros prestados
- Resultados de consultas complejas

---

## 💻 METODOLOGÍA GITHUB - TRABAJO COLABORATIVO

### 🔧 CONFIGURACIÓN INICIAL DEL REPOSITORIO

#### 1. Configuración del Repositorio Principal
```bash
# Crear repositorio principal (Alex como administrador)
git init
git remote add origin https://github.com/equipo-biblioteca-unju/sistema-gestion.git

# Estructura inicial de branches
git checkout -b develop
git checkout -b feature/setup-inicial
```

#### 2. Clonación para cada integrante
```bash
# Cada integrante clona el repositorio
git clone https://github.com/equipo-biblioteca-unju/sistema-gestion.git
cd sistema-gestion

# Configurar información personal
git config user.name "Nombre Apellido"
git config user.email "email@estudiante.unju.edu.ar"
```

### 🌿 ESTRATEGIA DE BRANCHING

#### Estructura de Branches:
```
main (producción)
├── develop (integración)
├── feature/alex-arboles-bst
├── feature/alex-arboles-avl
├── feature/leandro-arreglos-libros
├── feature/leandro-arreglos-usuarios
├── feature/rodrigo-pila-acciones
├── feature/rodrigo-cola-pendientes
├── feature/javier-lista-autor
├── feature/javier-lista-usuarios
├── hotfix/bug-critico (si es necesario)
└── release/v1.0 (para entrega final)
```

#### Comando para crear branches:
```bash
# Crear y cambiar a nueva rama
git checkout -b feature/nombre-funcionalidad

# Actualizar con cambios remotos
git pull origin develop

# Trabajar en la funcionalidad...
```

### 📝 CONVENCIONES DE COMMITS

#### Formato de Mensajes:
```
<tipo>(<ámbito>): <descripción breve>

<descripción detallada si es necesaria>

<referencias a issues o tareas>
```

#### Tipos de Commits:
- **feat:** Nueva funcionalidad
- **fix:** Corrección de bug
- **docs:** Documentación
- **style:** Formato de código
- **refactor:** Refactorización
- **test:** Agregar/modificar tests
- **chore:** Tareas de mantenimiento

#### Ejemplos Prácticos:
```bash
git commit -m "feat(arbol): implementar inserción en BST

- Agregar método insertarLibro() con validaciones
- Incluir manejo de duplicados
- Mantener propiedad de orden BST

Relacionado con tarea #BST-001"

git commit -m "fix(cola): corregir desbordamiento en cola circular

- Solucionar bug cuando cola está llena
- Agregar validación de capacidad máxima
- Incluir test para edge case

Fixes #BUG-042"
```

### 🔄 WORKFLOW DE DESARROLLO

#### 1. Flujo Diario de Trabajo
```bash
# Al comenzar el día
git checkout develop
git pull origin develop
git checkout feature/mi-rama
git merge develop  # Actualizar rama con últimos cambios

# Trabajar en código...
# Hacer commits frecuentes

# Al finalizar el día
git push origin feature/mi-rama
```

#### 2. Pull Request (PR) Process
```markdown
## Plantilla de Pull Request

### 📋 Descripción
Breve descripción de los cambios implementados

### 🔄 Tipo de cambio
- [ ] Bug fix (no rompe funcionalidad existente)
- [ ] Nueva funcionalidad (no rompe funcionalidad existente)
- [ ] Breaking change (fix o feature que causa que funcionalidad existente no funcione)
- [ ] Actualización de documentación

### ✅ Checklist
- [ ] Mi código sigue las convenciones del proyecto
- [ ] He realizado auto-review de mi código
- [ ] He comentado mi código en áreas difíciles de entender
- [ ] He agregado tests que prueban mi fix o feature
- [ ] Tests nuevos y existentes pasan localmente
- [ ] He actualizado la documentación correspondiente

### 🧪 Tests Realizados
Describir qué tests se realizaron y resultados

### 📸 Screenshots (si aplica)
Capturas de pantalla de la funcionalidad

### 👥 Reviewers Asignados
@leandro-saavedra @rodrigo-torres @javier-lamas
```

#### 3. Code Review Process
- **Mínimo 2 revisores** por PR
- **Review checklist:**
  - ✅ Funcionalidad cumple requisitos
  - ✅ Código legible y bien comentado
  - ✅ No hay código duplicado
  - ✅ Manejo adecuado de errores
  - ✅ Tests cubren casos importantes
  - ✅ Rendimiento aceptable

### 🚀 INTEGRACIÓN CONTINUA

#### GitHub Actions Workflow
```yaml
# .github/workflows/ci.yml
name: CI/CD Pipeline

on:
  push:
    branches: [ develop, main ]
  pull_request:
    branches: [ develop ]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - name: Set up JDK 11
      uses: actions/setup-java@v3
      with:
        java-version: '11'
    - name: Run tests
      run: |
        javac -cp ".:lib/*" src/**/*.java
        java -cp ".:lib/*" org.junit.runner.JUnitCore TestSuite
```

### 📊 GESTIÓN DE ISSUES Y PROJECTS

#### Labels para Issues:
- 🐛 `bug` - Errores encontrados
- ✨ `enhancement` - Nuevas funcionalidades
- 📚 `documentation` - Mejoras en documentación
- ❓ `question` - Preguntas del equipo
- 🔥 `priority-high` - Alta prioridad
- 📋 `estructura-datos` - Relacionado con estructuras específicas

#### Milestone Planning:
- **Sprint 1 (Semanas 1-2):** Diseño y setup
- **Sprint 2 (Semanas 3-4):** Implementación básica
- **Sprint 3 (Semanas 5-6):** Operaciones principales
- **Sprint 4 (Semanas 7-8):** Integración y testing
- **Sprint 5 (Semana 9):** Pulido y entrega

### 🔒 MEJORES PRÁCTICAS DE SEGURIDAD

#### Manejo de Credenciales:
```bash
# Nunca commitear archivos sensibles
echo "*.properties" >> .gitignore
echo "config/database.conf" >> .gitignore
echo ".env" >> .gitignore
```

#### Protección de Branches:
- **main:** Solo merge via PR con 2+ reviews
- **develop:** Solo merge via PR con 1+ review
- **Requerir status checks** antes de merge
- **Prohibir force push** en branches principales

---

## 🧪 ESTRATEGIA DE TESTING AVANZADA

### Pruebas Unitarias por Estructura

#### Testing de Árboles (Alex):
```java
@Test
public void testInsertarLibroEnArbolVacio() {
    ArbolBST arbol = new ArbolBST();
    Libro libro = new Libro(100, "Test", "Autor", 25.0);
    
    assertTrue(arbol.insertar(libro));
    assertEquals(libro, arbol.buscar(100));
    assertEquals(1, arbol.obtenerTamaño());
}

@Test
public void testBalanceoAVL() {
    ArbolAVL arbol = new ArbolAVL();
    // Insertar secuencia que requiere balanceo
    for(int i = 1; i <= 7; i++) {
        arbol.insertar(new Libro(i, "Libro" + i, "Autor", 10.0));
    }
    
    assertTrue(arbol.estaBalanceado());
    assertEquals(3, arbol.obtenerAltura()); // log2(7) + 1
}
```

#### Testing de Arreglos (Leandro):
```java
@Test
public void testArregloCapacidadMaxima() {
    GestorLibros gestor = new GestorLibros(5);
    
    // Llenar arreglo a capacidad máxima
    for(int i = 0; i < 5; i++) {
        assertTrue(gestor.agregarLibro(new Libro(i, "Libro", "Autor", 10.0)));
    }
    
    // Intentar agregar uno más
    assertFalse(gestor.agregarLibro(new Libro(6, "Extra", "Autor", 10.0)));
}
```

#### Testing de Pilas y Colas (Rodrigo):
```java
@Test
public void testPilaReversion() {
    PilaAcciones pila = new PilaAcciones();
    Operacion prestamo = new Operacion(1, "PRESTAMO", libro, usuario);
    
    pila.apilar(prestamo);
    assertFalse(pila.estaVacia());
    
    Operacion revertida = pila.desapilar();
    assertEquals("DEVOLUCION", revertida.getTipoInverso());
}

@Test
public void testColaCircular() {
    ColaPendientes cola = new ColaPendientes(3);
    
    // Llenar cola
    cola.encolar(usuario1);
    cola.encolar(usuario2);
    cola.encolar(usuario3);
    assertTrue(cola.estaLlena());
    
    // Procesar y agregar nuevo
    Usuario procesado = cola.desencolar();
    assertEquals(usuario1, procesado);
    cola.encolar(usuario4); // Debe usar posición circular
}
```

---

## 📊 MÉTRICAS DE CALIDAD AVANZADAS

### 📈 Análisis de Complejidad por Operación

| Operación | Arreglo | BST Promedio | BST Peor Caso | AVL | Lista Enlazada |
|-----------|---------|--------------|---------------|-----|----------------|
| Búsqueda | O(n) | O(log n) | O(n) | O(log n) | O(n) |
| Inserción | O(1)* | O(log n) | O(n) | O(log n) | O(1)** |
| Eliminación | O(n) | O(log n) | O(n) | O(log n) | O(1)** |
| Recorrido | O(n) | O(n) | O(n) | O(n) | O(n) |

*Al final del arreglo  
**Si se tiene referencia al nodo

### 🎯 Benchmarking Goals
- **1,000 libros:** Búsqueda < 1ms en árbol
- **10,000 operaciones:** Pila/Cola < 10ms total
- **100 consultas:** Lista enlazada < 50ms
- **Memoria total:** < 100MB para dataset completo

---

## 📅 CRONOGRAMA DE TRABAJO

### Semana 1-2: Diseño y Estructura Base
- **Todos:** Análisis de requisitos y diseño de clases
- **Alex:** Definir interfaces y estructura de árboles
- **Leandro:** Diseñar esquema de arreglos y validaciones
- **Rodrigo:** Especificar estructuras de pila y cola
- **Javier:** Planificar listas enlazadas y casos de prueba

### Semana 3-4: Implementación Core
- **Alex:** Implementar árbol binario de búsqueda básico
- **Leandro:** Desarrollar gestión de arreglos de libros/usuarios
- **Rodrigo:** Crear pila de acciones y cola de pendientes
- **Javier:** Implementar listas enlazadas básicas

### Semana 5-6: Operaciones Principales
- **Alex:** Integrar árboles con operaciones de préstamo/devolución
- **Leandro:** Conectar arreglos con sistema de validación
- **Rodrigo:** Implementar reversión y gestión de pendientes
- **Javier:** Desarrollar consultas avanzadas con listas

### Semana 7-8: Integración y Testing
- **Todos:** Integración de módulos y pruebas conjuntas
- **Alex:** Supervisar integración final
- **Leandro:** Validar todo el sistema
- **Rodrigo:** Documentar y crear manual
- **Javier:** Testing exhaustivo y correción de bugs

### Semana 9: Pulido y Entrega
- **Todos:** Preparación de defensa y documentación final

---

## 🎯 PUNTOS DE SINCRONIZACIÓN

### Reuniones Obligatorias
1. **Lunes 19:00hs:** Revisión de avances y planificación semanal
2. **Jueves 19:00hs:** Resolución de problemas técnicos
3. **Sábados 10:00hs:** Trabajo colaborativo presencial (opcional)

### Deliverables por Semana
- **Semana 2:** Diseño UML completo
- **Semana 4:** Módulos individuales funcionando
- **Semana 6:** Sistema integrado básico
- **Semana 8:** Sistema completo con pruebas

---

## 📁 ESTRUCTURA DE ARCHIVOS

```
ProyectoBiblioteca/
├── src/
│   ├── modelo/
│   │   ├── Libro.java
│   │   ├── Usuario.java
│   │   └── Operacion.java
│   ├── estructuras/
│   │   ├── ArbolBinarioBusqueda.java (Alex)
│   │   ├── GestorArreglos.java (Leandro)
│   │   ├── PilaAcciones.java (Rodrigo)
│   │   ├── ColaPendientes.java (Rodrigo)
│   │   └── ListaEnlazada.java (Javier)
│   ├── servicios/
│   │   ├── ServicioPrestamo.java
│   │   ├── ServicioConsulta.java
│   │   └── ServicioReversion.java
│   └── main/
│       └── SistemaBiblioteca.java
├── test/
│   ├── ArbolTest.java
│   ├── ArreglosTest.java
│   ├── PilaColaTest.java
│   └── ListaTest.java
└── docs/
    ├── DiagramaUML.png
    ├── ManualUsuario.md
    └── DocumentacionTecnica.md
```

---

## ⚠️ RIESGOS Y CONTINGENCIAS

### Riesgos Identificados
1. **Conflictos de integración:** Mitigado con branches y reuniones frecuentes
2. **Ausencia de integrante:** Cada módulo tiene backup asignado
3. **Complejidad de árboles AVL:** Implementación simplificada como plan B
4. **Rendimiento deficiente:** Optimización en semana 7

### Plan de Contingencia
- **Backup de Alex:** Leandro puede asumir árboles básicos
- **Backup de Leandro:** Rodrigo maneja arreglos auxiliares
- **Backup de Rodrigo:** Javier implementa estructuras básicas
- **Backup de Javier:** Alex complementa con estructuras auxiliares

---

## 📞 INFORMACIÓN DE CONTACTO

### Canales de Comunicación del Equipo
| Integrante | Email Universitario | Discord/Usuario | Horario Disponible |
|------------|-------------------|-----------------|-------------------|
| **Alex Gabriel** | alex.calatayud@estudiante.unju.edu.ar | @alex_dev | Lun-Dom 08:00-22:00 |
| **Leandro Ariel** | leandro.saavedra@estudiante.unju.edu.ar | @leandro_code | Lun-Vie 09:00-21:00 |
| **Rodrigo Emiliano** | rodrigo.torres@estudiante.unju.edu.ar | @rodrigo_stack | Lun-Sab 10:00-20:00 |
| **Javier Ramiro** | javier.lamas@estudiante.unju.edu.ar | @javier_lista | Mar-Dom 14:00-22:00 |

### Grupos de Trabajo
- **WhatsApp Grupo:** "Proyecto Integrador - Biblioteca 2025"
- **Discord Server:** "UNJu - Estructura de Datos"
- **Google Drive:** Carpeta compartida "ProyectoIntegrador_Biblioteca"
- **GitHub Repository:** `github.com/equipo-biblioteca-unju/sistema-gestion`

### Protocolos de Comunicación
- **Urgente:** Discord + mensaje directo
- **Consultas técnicas:** Canal #desarrollo en Discord
- **Documentación:** Comentarios en Google Drive
- **Code Review:** Pull Request en GitHub

---

**¡RECORDATORIO FINAL!** 
- Entrega: **25/06/2025 - 23:59hs**
- Todos deben participar en la defensa
- Mantener comunicación constante
- Calidad sobre velocidad
- **¡TRABAJEMOS EN EQUIPO PARA EL ÉXITO! 🚀**

### 📋 CHECKLIST FINAL DE ENTREGA

#### ✅ Funcionalidades Implementadas
- [ ] Registro de libros (arreglo + árbol)
- [ ] Registro de usuarios (arreglo)
- [ ] Sistema de préstamos con validaciones
- [ ] Sistema de devoluciones
- [ ] Cola de espera para libros no disponibles
- [ ] Pila de acciones con reversión
- [ ] Consultas con listas enlazadas
- [ ] Manejo completo de errores

#### ✅ Documentación Completa
- [ ] Código comentado en español
- [ ] Diagramas UML actualizados
- [ ] Manual de usuario
- [ ] Documentación técnica
- [ ] README con instrucciones de setup

#### ✅ Testing y Calidad
- [ ] Tests unitarios para cada estructura
- [ ] Tests de integración completos
- [ ] Cobertura de código > 80%
- [ ] Performance tests pasando
- [ ] Code review completado

#### ✅ Preparación para Defensa
- [ ] Presentación preparada
- [ ] Demo funcional lista
- [ ] Todos los integrantes preparados
- [ ] Respuestas a preguntas frecuentes
- [ ] Backup del proyecto completo
