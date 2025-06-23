# Componentes de Carta

Los componentes de carta son contenedores de datos que definen las propiedades y el estado de una entidad de carta. Cada componente almacena un aspecto específico de la carta, como su información básica, su costo o sus estadísticas de combate. Los sistemas de renderizado utilizan estos datos para mostrar visualmente las cartas en la interfaz de usuario.

## Componentes Principales

Basado en la arquitectura, estos son los componentes fundamentales para las cartas:

### 1. CardInfoComponent

-   **Descripción:** Almacena la información visual y descriptiva de la carta. Es la base para la representación visual de cualquier carta en el juego.
-   **Atributos:**
    -   `name: String` - El nombre de la carta, mostrado en la parte superior.
    -   `description: String` - El texto descriptivo o de ambientación, usualmente en el cuerpo de la carta.
    -   `artAssetId: String` - El identificador del recurso gráfico para el arte principal de la carta.

### 2. CostComponent

-   **Descripción:** Define el costo necesario para jugar la carta. Esta información se muestra típicamente en una esquina de la carta.
-   **Atributos:**
    -   `resourceType: String` - El tipo de recurso (ej. "Maná", "Oro") que se necesita.
    -   `amount: int` - La cantidad de recurso requerido.

### 3. StatsComponent

-   **Descripción:** Contiene las estadísticas de combate de una carta de criatura o unidad. Estos valores son fundamentales para la fase de combate y se muestran de forma prominente en la carta.
-   **Atributos:**
    -   `attack: int` - El poder de ataque de la criatura.
    -   `health: int` - La salud o puntos de vida de la criatura.

### 4. EffectDefinitionComponent

-   **Descripción:** Define los efectos o habilidades especiales de una carta. Aunque la lógica se ejecuta en los sistemas, la descripción del efecto (almacenada en `CardInfoComponent`) se muestra en la carta para que el jugador la conozca.
-   **Atributos:**
    -   `trigger: String` - La condición que activa el efecto (ej. "OnPlay", "OnDeath").
    -   `effectLogicId: String` - Identificador de la lógica del efecto a ejecutar.
    -   `params: Map` - Parámetros adicionales para la lógica del efecto.
\n
