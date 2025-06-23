# Arquetipos de Mazo

Los arquetipos de mazo se utilizan para crear entidades de mazo en el `World` de ECS. Un mazo está asociado a un jugador y contiene una lista de cartas. La clase `DeckArchetypes` proporciona los métodos para instanciar estos arquetipos.

## Arquetipos Principales

Basado en la arquitectura, existe un arquetipo fundamental para los mazos:

### 1. Arquetipo de Mazo (`createDeck`)

Este arquetipo se utiliza para crear un mazo para un jugador.

-   **Descripción:** Representa un conjunto de cartas que pertenecen a un jugador. Las cartas se pueden barajar y robar de este mazo.
-   **Componentes Asociados:**
    -   `CardListInDeckComponent`: Almacena la lista de entidades de carta que componen el mazo.
    -   `OwnerPlayerComponent`: Vincula el mazo a la entidad del jugador propietario. 