# GUÍA DE ORGANIZACIÓN - PROYECTO INTEGRADOR
## Sistema de Gestión de Biblioteca - Estructura de Datos 2025

**OBJETIVO PRINCIPAL:** Implementar un sistema completo de gestión de biblioteca utilizando arreglos, pilas, colas, listas enlazadas y árboles AVL, con trabajo colaborativo y sincronizado entre 4 integrantes.

---

## 👥 INTEGRANTES DEL EQUIPO

| Integrante | Rol Principal | Responsabilidades Secundarias |
|------------|---------------|-------------------------------|
| **Calatayud, Alex Gabriel** | Líder Técnico & Árboles | Coordinación general, integración |
| **SAAVEDRA, LEANDRO ARIEL** | Especialista en Arreglos & Usuarios | Testing y validaciones |
| **Torres, Rodrigo Emiliano** | Especialista en Pilas & Colas | Documentación técnica |
| **Lamas, Javier Ramiro** | Especialista en Listas Enlazadas | Control de calidad y pruebas |

---

## 📋 DIVISIÓN DETALLADA DE TAREAS

### 🌳 Alex Gabriel Calatayud - ÁRBOLES & COORDINACIÓN
**Estructuras Asignadas:** Árbol Binario de Búsqueda y Árboles AVL

#### Responsabilidades Principales:
- **Clase ArbolBinarioBusqueda.java**
  - Implementar inserción, búsqueda y eliminación de libros por código
  - Balanceo automático (conversión a AVL si es necesario)
  - Métodos de recorrido (inorden, preorden, postorden)
  
- **Clase ArbolUsuarios.java** (opcional pero recomendado)
  - Estructura similar para usuarios por número de usuario
  
- **Coordinación del Proyecto**
  - Revisar integración entre módulos
  - Resolver conflictos de merge en Git
  - Supervisar cronograma general

#### Entregables Específicos:
```java
// Métodos clave a implementar:
- insertarLibro(Libro libro)
- buscarLibro(int codigo)
- eliminarLibro(int codigo)
- obtenerLibrosOrdenados()
- verificarBalanceo()
```

### 📚 SAAVEDRA, LEANDRO ARIEL - ARREGLOS & GESTIÓN DE USUARIOS
**Estructuras Asignadas:** Arreglos unidimensionales

#### Responsabilidades Principales:
- **Clase GestorLibros.java**
  - Arreglo principal de libros con tamaño fijo
  - Métodos de inserción y búsqueda lineal
  - Visualización completa del catálogo
  
- **Clase GestorUsuarios.java**
  - Arreglo de usuarios con validaciones
  - Control de números únicos de usuario
  - Gestión de cantidad de libros prestados

- **Sistema de Validaciones**
  - Verificación de códigos únicos
  - Validación de datos de entrada
  - Manejo de excepciones

#### Entregables Específicos:
```java
// Métodos clave a implementar:
- registrarLibro(Libro libro)
- buscarLibroPorCodigo(int codigo)
- mostrarCatalogo()
- registrarUsuario(Usuario usuario)
- validarCodigoUnico(int codigo)
```

### 🔄 Torres, Rodrigo Emiliano - PILAS & COLAS
**Estructuras Asignadas:** Pila de acciones y Cola de pendientes

#### Responsabilidades Principales:
- **Clase PilaAcciones.java**
  - Implementar pila para operaciones (préstamo/devolución)
  - Sistema de reversión (undo)
  - Registro completo de acciones con timestamp
  
- **Clase ColaPendientes.java**
  - Cola FIFO para usuarios en espera
  - Gestión de prioridades
  - Procesamiento automático cuando hay disponibilidad

- **Documentación Técnica**
  - Comentarios detallados en código
  - Diagramas de flujo de operaciones
  - Manual de usuario del sistema

#### Entregables Específicos:
```java
// Métodos clave a implementar:
- apilar(Operacion operacion)
- desapilar()
- revertirUltimaAccion()
- encolar(Usuario usuario)
- desencolar()
- procesarPendientes()
```

### 🔗 Lamas, Javier Ramiro - LISTAS ENLAZADAS & CONTROL DE CALIDAD
**Estructuras Asignadas:** Listas enlazadas para consultas dinámicas

#### Responsabilidades Principales:
- **Clase ListaLibrosAutor.java**
  - Lista enlazada para búsquedas por autor (subcadena)
  - Implementación con nodos dinámicos
  - Algoritmos de búsqueda eficientes
  
- **Clase ListaUsuariosActivos.java**
  - Lista de usuarios con X o más libros prestados
  - Filtros dinámicos y ordenamiento
  
- **Control de Calidad**
  - Diseño de casos de prueba
  - Testing unitario de cada módulo
  - Validación de integración

#### Entregables Específicos:
```java
// Métodos clave a implementar:
- buscarLibrosPorAutor(String subcadena)
- filtrarUsuariosPorPrestamos(int minimo)
- insertarOrdenado(Object elemento)
- eliminarPorCriterio(Criterio criterio)
- generarReporte()
```

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

## 🛠️ METODOLOGÍA DE TRABAJO

### Herramientas de Colaboración
- **Git/GitHub:** Control de versiones con branches por integrante
- **Discord/WhatsApp:** Comunicación diaria
- **Google Drive:** Documentación compartida
- **Reuniones:** Lunes y Jueves 19:00hs (obligatorias)

### Estructura de Branches Git
```
main
├── feature/alex-arboles
├── feature/leandro-arreglos  
├── feature/rodrigo-pilas-colas
└── feature/javier-listas
```

### Convenciones de Código
- **Idioma:** Español para variables y comentarios
- **Nomenclatura:** camelCase para métodos, PascalCase para clases
- **Comentarios:** Obligatorios para métodos públicos
- **Indentación:** 4 espacios, no tabs

---

## 🧪 ESTRATEGIA DE PRUEBAS

### Pruebas Unitarias por Módulo
- **Alex:** Test de inserción/búsqueda en árboles
- **Leandro:** Test de validaciones y búsquedas en arreglos
- **Rodrigo:** Test de operaciones LIFO/FIFO
- **Javier:** Test de operaciones dinámicas en listas

### Pruebas de Integración
- **Semana 6:** Test de préstamo completo (arreglo + árbol + pila)
- **Semana 7:** Test de reversión (pila + actualización estructuras)
- **Semana 8:** Test de consultas complejas (todas las estructuras)

### Casos de Prueba Críticos
1. **Préstamo con libro no disponible → Cola de pendientes**
2. **Reversión múltiple de operaciones**
3. **Búsqueda en árbol con 1000+ libros**
4. **Consulta de libros por autor con 0 resultados**
5. **Usuario con 10+ libros prestados**

---

## 📊 MÉTRICAS DE CALIDAD

### Objetivos Cuantificables
- **Cobertura de código:** Mínimo 80% en pruebas unitarias
- **Tiempo de búsqueda en árbol:** O(log n) garantizado
- **Memoria:** Máximo 100MB para 10,000 libros
- **Operaciones por segundo:** Mínimo 1000 búsquedas/seg

### Revisiones de Código
- **Peer Review:** Cada feature branch revisada por 2 integrantes
- **Code Review semanal:** Reunión técnica para revisar avances
- **Refactoring:** Semana 7 dedicada a optimización

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

## 🎓 CRITERIOS DE ÉXITO

### Funcionalidades Obligatorias ✅
- [x] Registro de libros en arreglo y árbol
- [x] Registro de usuarios en arreglo
- [x] Préstamo con validaciones
- [x] Devolución con actualizaciones
- [x] Cola de pendientes funcional
- [x] Pila de acciones con reversión
- [x] Consultas con listas enlazadas

### Funcionalidades Adicionales (Valor Agregado)
- [ ] Interfaz gráfica básica
- [ ] Persistencia en archivos
- [ ] Reportes estadísticos
- [ ] Sistema de notificaciones
- [ ] Búsqueda avanzada multicritério

---

## 📞 CONTACTOS DE EMERGENCIA

| Integrante | Teléfono | Email | Horario Disponible |
|------------|----------|-------|-------------------|
| Alex Gabriel | XXX-XXXX | alex@email.com | 24/7 |
| Leandro Ariel | XXX-XXXX | leandro@email.com | 08:00-22:00 |
| Rodrigo Emiliano | XXX-XXXX | rodrigo@email.com | 09:00-21:00 |
| Javier Ramiro | XXX-XXXX | javier@email.com | 10:00-20:00 |

---

**¡RECORDATORIO FINAL!** 
- Entrega: **25/06/2025 - 23:59hs**
- Todos deben participar en la defensa
- Mantener comunicación constante
- Calidad sobre velocidad
- **¡TRABAJEMOS EN EQUIPO PARA EL ÉXITO! 🚀**
