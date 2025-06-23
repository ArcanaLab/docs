# Arquetipos de Mesa de Juego

Los arquetipos de la mesa de juego definen la estructura y el estado del entorno de juego principal. La clase `GameStateArchetypes` se encarga de instanciar las entidades que gestionan el estado global del juego.

## Arquetipos Principales

La arquitectura define un arquetipo fundamental para gestionar el estado del juego:

### 1. Arquetipo de Estado de Juego (`createInitialGameState`)

Este arquetipo se utiliza para configurar la entidad principal que representa el estado actual de la partida.

-   **Descripción:** Crea una entidad singleton que actúa como la fuente de verdad para el estado del juego, como el turno actual y la fase del juego. También puede gestionar las diferentes zonas del tablero.
-   **Componentes Asociados:**
    -   `CurrentTurnComponent`: Realiza un seguimiento del jugador activo y el número de turno.
    -   `GamePhaseComponent`: Define la fase actual del juego (por ejemplo, inicio, ataque, fin).
    -   `ZoneComponent`: Define áreas específicas del tablero, como el campo de batalla o el cementerio, y contiene las cartas que se encuentran en ellas. 