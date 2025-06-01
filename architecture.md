```plantuml
@startuml
@startuml
skinparam packageStyle rectangle
skinparam classAttributeIconSize 0
skinparam linetype ortho
hide empty members

title Arcana Framework ECS - Estructura de Paquetes Piola

package "com.arcana.game" {

  class ArcanaGame {
    + main(String[] args)
    - world: com.arcana.game.core.ecs.World
    + initECSWorld()
    + gameLoop()
  }
  ArcanaGame ..> com.arcana.game.core.ecs.World : "arranca y usa el"

  package "card" {
    class CardArchetypes {
      + createSpellCard(world, definition)
      + createCreatureCard(world, definition)
    }
    CardArchetypes ..> com.arcana.game.core.ecs.World : "registra cartas en el"

    package "components" {
      class CardInfoComponent {
        + name: String
        + description: String
        + artAssetId: String
      }
      class CostComponent {
        + resourceType: String
        + amount: int
      }
      class EffectDefinitionComponent {
        + trigger: String
        + effectLogicId: String
        + params: Map
      }
      class StatsComponent {
        + attack: int
        + health: int
      }
    }

    package "systems" {
      class PlayCardSystem
      class ApplyCardEffectSystem
      PlayCardSystem ..> card.components : "opera sobre"
      ApplyCardEffectSystem ..> card.components : "opera sobre"
    }
  }

  package "player" {
    class PlayerArchetypes {
      + createHumanPlayer(world, name)
      + createAIPlayer(world, name, aiProfileId)
    }

    package "components" {
      class PlayerInfoComponent {
        + playerId: String
        + displayName: String
      }
      class HandComponent {
        + cardEntities: List<EntityId>
      }
      class ResourceComponent {
        + type: String
        + current: int
        + max: int
      }
      class IsHumanControlledComponent
      class AIControlComponent {
        + aiProfileId: String
      }
    }

    package "systems" {
      class PlayerInputSystem
      class AISystem
      PlayerInputSystem ..> player.components : "afecta/lee"
      AISystem ..> player.components : "afecta/lee"
    }
  }

  package "deck" {
    class DeckArchetypes
    package "components" {
      class CardListInDeckComponent
      class OwnerPlayerComponent
    }
    package "systems" {
      class ShuffleDeckSystem
      class DrawCardFromDeckSystem
    }
  }

  package "table" {
    class GameStateArchetypes {
        + createInitialGameState(world)
    }
    package "components" {
      class CurrentTurnComponent {
        + activePlayerEntityId: EntityId
        + turnNumber: int
      }
      class GamePhaseComponent {
        + currentPhase: String
      }
      class ZoneComponent {
         + zoneType: String
         + cardsInZone: List<EntityId>
      }
    }
    package "systems" {
      class TurnManagementSystem
      class RuleValidationSystem
    }
  }

  package "menu" {
    class MenuScreenArchetypes
    class MenuItemArchetypes
    package "components" {
      class MenuItemComponent
      class ButtonComponent
    }
    package "systems" {
      class MenuRenderSystem
      class MenuNavigationSystem
    }
  }

  package "core" {
    package "ecs" {
      class Entity {
        + id: int
      }
      interface Component
      abstract class System {
        # world: World
        + System(world: World)
        + abstract update(deltaTime: float)
      }
      class World {
        - entities: Map<EntityId, List<Component>>
        - systems: List<System>
        + createEntity(): EntityId
        + addComponent(entityId, component)
        + getComponent(entityId, componentType)
        + removeComponent(entityId, componentType)
        + getEntitiesWith(componentType): List<EntityId>
        + addSystem(system)
        + updateAllSystems(deltaTime)
      }
      World o-- Entity : "maneja"
      World o-- Component : "almacena"
      World o-- System : "ejecuta"
    }

    package "systems" {
      class MasterRenderSystem
      class EventDispatchSystem
    }

    package "utils" {
      class AssetLoader
      class GameSettings
    }
  }
}
@enduml
@enduml