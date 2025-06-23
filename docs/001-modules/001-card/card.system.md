# Sistemas de Carta

Los sistemas de carta implementan la lógica de juego que involucra a las entidades de carta. Estos sistemas reaccionan a las acciones del jugador y a los eventos del juego, modificando los componentes de las cartas y otras entidades para alterar el estado del mundo del juego.

## Sistemas Principales

Basado en la arquitectura, estos son los sistemas clave para la gestión de cartas:

### 1. PlayCardSystem

-   **Descripción:** Gestiona la lógica principal para jugar una carta desde la mano de un jugador. Este sistema es el punto de entrada para que una carta tenga un impacto en el juego.
-   **Responsabilidades:**
    -   Verificar que el jugador activo (`CurrentTurnComponent`) tiene suficientes recursos (`ResourceComponent`) para pagar el `CostComponent` de la carta.
    -   Confirmar que las reglas del juego (`RuleValidationSystem`) permiten jugar la carta en la fase actual (`GamePhaseComponent`).
    -   Mover la entidad de la carta desde la mano del jugador (`HandComponent`) a la zona de juego correspondiente (`ZoneComponent`).
    -   Activar los efectos "OnPlay" de la carta, usualmente notificando al `ApplyCardEffectSystem`.

### 2. ApplyCardEffectSystem

-   **Descripción:** Aplica los efectos de las cartas basados en los disparadores definidos en `EffectDefinitionComponent`. Es el motor que ejecuta las habilidades y altera el estado del juego.
-   **Responsabilidades:**
    -   Escuchar los disparadores de eventos del juego (ej. "OnPlay", "OnDeath", "StartOfTurn").
    -   Para una carta con un `EffectDefinitionComponent` que coincide con el disparador, leer el `effectLogicId` y sus `params`.
    -   Ejecutar la lógica de efecto correspondiente, que puede implicar:
        -   Modificar `StatsComponent` de otras cartas (ej. infligir daño).
        -   Cambiar el estado del jugador (`ResourceComponent`, `HandComponent`).
        -   Alterar el estado del turno o fase del juego (`CurrentTurnComponent`, `GamePhaseComponent`).
