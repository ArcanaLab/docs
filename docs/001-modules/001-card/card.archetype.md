# Arquetipos de Carta

Los arquetipos de carta son plantillas predefinidas para crear entidades de carta con un conjunto específico de componentes. Simplifican la creación de nuevos tipos de cartas en el `World` de ECS. La clase `CardArchetypes` proporciona métodos para instanciar estos arquetipos.

## Arquetipos Principales

Basado en la arquitectura, existen dos arquetipos fundamentales para las cartas:

### 1. Arquetipo de Criatura (`createCard`)

Este arquetipo se utiliza para crear cartas que representan unidades o personajes que pueden entrar en el campo de batalla.

-   **Descripción:** Representa una carta que puede ser convocada al campo de batalla como una unidad con estadísticas de ataque y salud.
-   **Componentes Asociados:**
    -   `CardInfoComponent`: Almacena información básica como nombre, descripción y arte.
    -   `CostComponent`: Define el costo en recursos para jugar la carta.
    -   `StatsComponent`: Contiene los valores de ataque y salud de la criatura.
    -   `EffectDefinitionComponent` (Opcional): Para criaturas con habilidades especiales.
\n
