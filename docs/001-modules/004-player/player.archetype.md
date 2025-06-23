# Arquetipos de Jugador

Los arquetipos de jugador son plantillas para crear las entidades que representan a los participantes en el juego. La clase `PlayerArchetypes` proporciona métodos para crear diferentes tipos de jugadores.

## Arquetipos Principales

La arquitectura define dos tipos de arquetipos de jugador:

### 1. Arquetipo de Jugador Humano (`createHumanPlayer`)

Este arquetipo se utiliza para crear una entidad de jugador controlada por una persona.

-   **Descripción:** Representa a un jugador humano, capaz de interactuar con el juego a través de un dispositivo de entrada.
-   **Componentes Asociados:**
    -   `PlayerInfoComponent`: Almacena información básica como el ID y el nombre del jugador.
    -   `HandComponent`: Gestiona la mano de cartas del jugador.
    -   `ResourceComponent`: Realiza un seguimiento de los recursos del jugador (por ejemplo, maná).
    -   `IsHumanControlledComponent`: Un componente marcador que indica que este jugador es controlado por un humano.

### 2. Arquetipo de Jugador IA (`createAIPlayer`)

Este arquetipo se usa para crear un oponente controlado por la inteligencia artificial.

-   **Descripción:** Representa a un jugador controlado por la IA, que toma decisiones basadas en un perfil de IA definido.
-   **Componentes Asociados:**
    -   `PlayerInfoComponent`: Información básica del jugador.
    -   `HandComponent`: Mano de cartas del jugador.
    -   `ResourceComponent`: Recursos del jugador.
    -   `AIControlComponent`: Contiene la lógica o el perfil de IA que guiará las acciones del jugador. 