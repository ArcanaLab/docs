# Arquetipos de Menú

Los arquetipos de menú definen las plantillas para construir las diferentes pantallas e elementos interactivos de la interfaz de usuario del menú. Facilitan la creación de menús consistentes y funcionales. Las clases `MenuScreenArchetypes` y `MenuItemArchetypes` gestionan estos arquetipos.

## Arquetipos Principales

Existen dos arquetipos principales para la construcción de menús:

### 1. Arquetipo de Pantalla de Menú (`createMenuScreen`)

Este arquetipo se usa para crear una pantalla de menú completa, que actúa como un contenedor para varios elementos de menú.

-   **Descripción:** Representa una pantalla de menú, como el menú principal o el menú de opciones.
-   **Componentes Asociados:**
    -   Un componente que agrupe los `MenuItem` de esta pantalla (implícito en la arquitectura).

### 2. Arquetipo de Elemento de Menú (`createMenuItem`)

Este arquetipo crea un elemento individual dentro de una pantalla de menú.

-   **Descripción:** Representa un elemento interactivo en un menú, como un botón.
-   **Componentes Asociados:**
    -   `MenuItemComponent`: Contiene información sobre el elemento, como su texto o su posición.
    -   `ButtonComponent`: Añadido si el elemento de menú es un botón clickeable, definiendo su acción. \n
