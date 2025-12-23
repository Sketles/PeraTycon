# 🚀 MVP - Pera Tycoon

## Objetivo del MVP

Crear una versión jugable mínima que demuestre el **core loop** del juego:
> **Pera mina carbón → Deposita en bodega → Vende al vagón → Mejora**

---

## 📋 Alcance del MVP

### ✅ Incluido en MVP
- 1 parcela funcional (single player para testing)
- 1 pera trabajadora con IA básica
- Mina simplificada con carbón infinito
- Bodega con capacidad fija
- Vagón de venta (timer o botón manual)
- UI básica (dinero, carbón en bodega)
- 1 mejora funcional (velocidad de pera)

### ❌ Excluido del MVP (Fase 2+)
- Multiplayer / Parcelas múltiples
- Árbol de peras y cultivo
- Huevos y accesorios
- Sistema completo de mejoras
- Lobby y matchmaking
- Efectos visuales elaborados

---

## 🎯 Fases de Desarrollo

### Fase 1: Fundación (Semana 1-2)

| Tarea | Prioridad | Estado |
|-------|-----------|--------|
| Crear mapa básico (1 parcela + mina) | 🔴 Alta | ⬜ |
| Modelo de pera (placeholder) | 🔴 Alta | ⬜ |
| Modelo de bodega | 🔴 Alta | ⬜ |
| Modelo de mina/cerro | 🔴 Alta | ⬜ |

**Entregable:** Mapa blockout navegable

---

### Fase 2: Pera Trabajadora (Semana 2-3)

| Tarea | Prioridad | Estado |
|-------|-----------|--------|
| Script de movimiento (PathfindingService) | 🔴 Alta | ⬜ |
| Estados de la pera (Idle, Walking, Mining, Returning) | 🔴 Alta | ⬜ |
| Animación de minado (básica) | 🟡 Media | ⬜ |
| Sistema de mochila (capacidad) | 🔴 Alta | ⬜ |

**Entregable:** Pera que va a la mina, "pica" y regresa

---

### Fase 3: Economía Básica (Semana 3-4)

| Tarea | Prioridad | Estado |
|-------|-----------|--------|
| DataStore para guardar progreso | 🔴 Alta | ⬜ |
| Variable de dinero del jugador | 🔴 Alta | ⬜ |
| Variable de carbón en bodega | 🔴 Alta | ⬜ |
| Lógica de depósito (pera → bodega) | 🔴 Alta | ⬜ |
| Lógica de venta (bodega → dinero) | 🔴 Alta | ⬜ |

**Entregable:** Loop económico funcional

---

### Fase 4: Vagón de Venta (Semana 4)

| Tarea | Prioridad | Estado |
|-------|-----------|--------|
| Modelo del vagón | 🟡 Media | ⬜ |
| Movimiento circular (TweenService) | 🟡 Media | ⬜ |
| Detección de proximidad | 🔴 Alta | ⬜ |
| UI de venta (botón cuando está cerca) | 🔴 Alta | ⬜ |

**Entregable:** Vagón funcional con venta

---

### Fase 5: UI y Polish (Semana 4-5)

| Tarea | Prioridad | Estado |
|-------|-----------|--------|
| HUD: Dinero actual | 🔴 Alta | ⬜ |
| HUD: Carbón en bodega | 🔴 Alta | ⬜ |
| Panel de mejoras (1 mejora: velocidad) | 🟡 Media | ⬜ |
| Feedback visual al vender | 🟢 Baja | ⬜ |
| Sonidos básicos | 🟢 Baja | ⬜ |

**Entregable:** MVP Completo y jugable

---

## 🔧 Stack Técnico

### Scripts Mínimos Requeridos

```
ServerScriptService/
├── GameManager.lua        # Inicialización y control
├── PearController.lua     # IA y estados de la pera
└── EconomyManager.lua     # Dinero, bodega, ventas

ReplicatedStorage/
├── Config.lua             # Valores configurables
└── RemoteEvents/          # Comunicación cliente-servidor
    ├── SellCoal
    ├── UpdateUI
    └── BuyUpgrade

StarterPlayerScripts/
└── UIController.lua       # Manejo de la interfaz

StarterGui/
└── MainHUD/              # Frames de UI
```

---

## 📊 Valores de Configuración (MVP)

```lua
-- Config.lua
return {
    -- Pera
    PEAR_SPEED = 16,           -- Velocidad de movimiento
    PEAR_MINING_TIME = 2,      -- Segundos para picar 1 carbón
    PEAR_CAPACITY = 10,        -- Carbón máximo en mochila
    
    -- Bodega
    STORAGE_CAPACITY = 100,    -- Carbón máximo en bodega
    
    -- Economía
    COAL_PRICE = 1,            -- Precio por unidad de carbón
    FULL_STORAGE_BONUS = 0.15, -- 15% bonus bodega llena
    
    -- Mejoras
    SPEED_UPGRADE_COST = 50,   -- Costo mejora velocidad
    SPEED_UPGRADE_BOOST = 2,   -- +2 de velocidad por mejora
}
```

---

## ✅ Criterios de Éxito del MVP

El MVP está **completo** cuando:

1. [ ] El jugador puede ver su pera ir a la mina automáticamente
2. [ ] La pera pica carbón y regresa a la bodega
3. [ ] El carbón se acumula en la bodega
4. [ ] El jugador puede vender carbón cuando pasa el vagón
5. [ ] El dinero aumenta al vender
6. [ ] El jugador puede comprar 1 mejora (velocidad)
7. [ ] El progreso se guarda entre sesiones

---

## 🗓️ Timeline Estimado

| Semana | Objetivo | Horas Est. |
|--------|----------|------------|
| 1 | Blockout del mapa | 4-6h |
| 2 | Pera con pathfinding | 8-10h |
| 3 | Sistema de economía | 6-8h |
| 4 | Vagón + UI básica | 6-8h |
| 5 | Polish + Testing | 4-6h |

**Total estimado:** 28-38 horas de desarrollo

---

## 🔜 Post-MVP (Roadmap)

Una vez completado el MVP, las siguientes prioridades son:

1. **Multiplayer** - Múltiples parcelas, 10-12 jugadores
2. **Árbol de Peras** - Cultivo y generación de nuevas peras
3. **Mejoras Completas** - Todas las stats de peras y picos
4. **Huevos/Loot** - Sistema de drops y accesorios
5. **Lobby** - Matchmaking y tienda permanente

---

*Última actualización: 23 de Diciembre 2024*
