# 📋 Roadmap de Desarrollo - Pera Tycoon

## 🎯 Visión General

Este documento detalla las fases de desarrollo del juego, dividido en sprints escalables con tareas específicas y entregables claros.

---

## 🏗️ FASE 0: Setup del Proyecto
> **Duración:** 1 día | **Prioridad:** 🔴 Crítica

### Tareas
- [x] Crear repositorio en GitHub
- [x] Estructura de carpetas del proyecto
- [x] Documentación inicial (GDD)
- [x] README del proyecto
- [ ] Crear proyecto en Roblox Studio
- [ ] Configurar estructura de carpetas en Studio:
  ```
  ServerScriptService/
  ReplicatedStorage/
  StarterPlayerScripts/
  StarterGui/
  Workspace/
  ```
- [ ] (Opcional) Configurar Rojo para sync con Git

### Entregable
✅ Proyecto de Roblox vacío con estructura lista para desarrollar

---

## 🗺️ FASE 1: Blockout del Mapa
> **Duración:** 3-4 días | **Prioridad:** 🔴 Crítica

### 1.1 Parcela Base
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| Suelo de parcela | Part plana triangular/wedge | ⬜ |
| Límites visuales | Bordes para delimitar zona | ⬜ |
| Placeholder bodega | Cubo simple con nombre | ⬜ |
| Placeholder árbol | Cilindro + esfera verde | ⬜ |
| Zona de descarga | Part con color distintivo | ⬜ |

### 1.2 Mina Central
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| Cerro/Montaña | Mesh o Parts apiladas | ⬜ |
| Entrada de túnel | Agujero visual simple | ⬜ |
| Zona de minado | Part interior donde se "pica" | ⬜ |
| Nodos de carbón | Parts pequeñas representando vetas | ⬜ |

### 1.3 Vía del Vagón
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| Rail circular | Path alrededor del mapa | ⬜ |
| Modelo vagón | Placeholder simple (cubo con ruedas) | ⬜ |
| Puntos de parada | Markers invisibles por parcela | ⬜ |

### Entregable
✅ Mapa navegable con 1 parcela funcional + mina + vía

---

## 🍐 FASE 2: Sistema de Peras (IA Básica)
> **Duración:** 5-7 días | **Prioridad:** 🔴 Crítica

### 2.1 Modelo y Configuración
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| Modelo de pera | Mesh o MeshPart simple | ⬜ |
| Humanoid/Rig | Para animaciones y movimiento | ⬜ |
| Atributos base | Speed, Capacity, MiningSpeed | ⬜ |
| Attachment para pico | Punto donde va la herramienta | ⬜ |

### 2.2 Sistema de Estados (State Machine)
```lua
-- Estados de la Pera
IDLE       -- Esperando en parcela
WALKING    -- Caminando hacia destino
MINING     -- Picando carbón
RETURNING  -- Volviendo con carga
DEPOSITING -- Dejando carbón en bodega
```

| Tarea | Descripción | Estado |
|-------|-------------|--------|
| Enum de estados | Definir todos los estados | ⬜ |
| Transiciones | Lógica de cambio de estado | ⬜ |
| Estado IDLE | Pera espera en spawn point | ⬜ |
| Estado WALKING | Usa PathfindingService | ⬜ |
| Estado MINING | Timer + animación picando | ⬜ |
| Estado RETURNING | Pathfinding de regreso | ⬜ |
| Estado DEPOSITING | Vaciar mochila en bodega | ⬜ |

### 2.3 Pathfinding
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| PathfindingService básico | Calcular ruta a destino | ⬜ |
| Waypoints | Seguir puntos del path | ⬜ |
| Recalcular si bloqueado | Manejar obstáculos | ⬜ |

### 2.4 Sistema de Mochila
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| Variable currentLoad | Carbón actual cargado | ⬜ |
| Variable maxCapacity | Límite de carga | ⬜ |
| Función AddCoal() | Añadir carbón a mochila | ⬜ |
| Función EmptyBag() | Vaciar al llegar a bodega | ⬜ |
| Chequeo de capacidad | Volver cuando lleno | ⬜ |

### Entregable
✅ Pera que automáticamente mina, carga y deposita carbón

---

## 💰 FASE 3: Sistema Económico
> **Duración:** 3-4 días | **Prioridad:** 🔴 Crítica

### 3.1 Datos del Jugador
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| Tabla playerData | Estructura de datos | ⬜ |
| money: number | Dinero actual | ⬜ |
| coalInStorage: number | Carbón en bodega | ⬜ |
| upgrades: table | Mejoras compradas | ⬜ |

### 3.2 DataStore (Persistencia)
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| DataStore setup | Crear/obtener store | ⬜ |
| Función LoadData() | Cargar al entrar | ⬜ |
| Función SaveData() | Guardar al salir | ⬜ |
| Auto-save | Guardar cada X minutos | ⬜ |
| Manejo de errores | Retry en caso de fallo | ⬜ |

### 3.3 Bodega
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| Variable capacity | Límite de almacenamiento | ⬜ |
| Función DepositCoal() | Añadir carbón | ⬜ |
| Función GetCoalAmount() | Leer cantidad actual | ⬜ |
| Evento OnStorageFull | Notificar cuando lleno | ⬜ |
| Visual de llenado | Mostrar % de capacidad | ⬜ |

### 3.4 Sistema de Venta
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| Función SellCoal() | Convertir carbón a dinero | ⬜ |
| Cálculo de precio | Carbón × precio base | ⬜ |
| Bonus 15% | Si bodega 100% llena | ⬜ |
| Efecto de venta | Feedback visual/sonoro | ⬜ |

### Entregable
✅ Sistema económico funcional con persistencia

---

## 🚃 FASE 4: Vagón de Venta
> **Duración:** 2-3 días | **Prioridad:** 🟡 Media

### 4.1 Movimiento del Vagón
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| Path circular | Puntos alrededor del mapa | ⬜ |
| TweenService | Movimiento suave entre puntos | ⬜ |
| Velocidad configurable | En Config.lua | ⬜ |
| Loop infinito | Vuelve al inicio al terminar | ⬜ |

### 4.2 Detección de Proximidad
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| Zona de venta | Part invisible por parcela | ⬜ |
| TouchEvent / Magnitude | Detectar jugador cerca | ⬜ |
| Estado "disponible" | Flag cuando está en rango | ⬜ |

### 4.3 Interacción
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| ProximityPrompt | "Presiona E para vender" | ⬜ |
| Validar venta | Hay carbón en bodega? | ⬜ |
| Ejecutar SellCoal() | Llamar al servidor | ⬜ |
| Ocultar prompt | Cuando el vagón se va | ⬜ |

### Entregable
✅ Vagón circulante con venta funcional

---

## 🖥️ FASE 5: Interfaz de Usuario (UI)
> **Duración:** 3-4 días | **Prioridad:** 🟡 Media

### 5.1 HUD Principal
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| Frame de dinero | Icono + número | ⬜ |
| Frame de bodega | Barra de progreso + texto | ⬜ |
| Actualización en tiempo real | Bindings a datos | ⬜ |

### 5.2 Panel de Mejoras
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| Botón de abrir panel | En esquina de pantalla | ⬜ |
| Lista de mejoras | ScrollingFrame | ⬜ |
| Ítem de mejora | Nombre + costo + botón | ⬜ |
| Lógica de compra | Validar dinero, aplicar | ⬜ |
| Feedback de compra | Sonido/animación | ⬜ |

### 5.3 Notificaciones
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| Toast de venta | "+$X" flotante | ⬜ |
| Alerta bodega llena | Mensaje temporal | ⬜ |
| Alerta vagón cerca | Indicador visual | ⬜ |

### Entregable
✅ UI funcional y responsiva

---

## ⬆️ FASE 6: Sistema de Mejoras
> **Duración:** 2-3 días | **Prioridad:** 🟡 Media

### 6.1 Estructura de Mejoras
```lua
Upgrades = {
    PearSpeed = { cost = 50, boost = 2, maxLevel = 10 },
    PearCapacity = { cost = 75, boost = 5, maxLevel = 10 },
    MiningSpeed = { cost = 100, boost = 0.5, maxLevel = 10 },
    StorageCapacity = { cost = 150, boost = 50, maxLevel = 5 },
}
```

### 6.2 Tareas
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| Config de mejoras | Tabla con costos/efectos | ⬜ |
| Función CanAfford() | Validar dinero suficiente | ⬜ |
| Función BuyUpgrade() | Comprar y aplicar | ⬜ |
| Aplicar a peras | Actualizar stats | ⬜ |
| Escalar costos | Precio × nivel actual | ⬜ |
| Guardar niveles | En DataStore | ⬜ |

### Entregable
✅ Sistema de mejoras completo para MVP

---

## 🧪 FASE 7: Testing y Polish
> **Duración:** 2-3 días | **Prioridad:** 🟢 Media-Baja

### 7.1 Testing
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| Probar loop completo | Minar → Vender → Mejorar | ⬜ |
| Test de DataStore | Guardar/cargar datos | ⬜ |
| Test de UI | Responsive en dispositivos | ⬜ |
| Buscar bugs | Documentar y corregir | ⬜ |

### 7.2 Polish
| Tarea | Descripción | Estado |
|-------|-------------|--------|
| Sonidos básicos | Minar, vender, comprar | ⬜ |
| Partículas | Al minar, al vender | ⬜ |
| Animaciones de UI | Tweens suaves | ⬜ |
| Balance de valores | Ajustar economía | ⬜ |

### Entregable
✅ MVP pulido y jugable

---

## 📊 Timeline Resumen

| Fase | Nombre | Duración | Dependencias |
|------|--------|----------|--------------|
| 0 | Setup | 1 día | - |
| 1 | Blockout | 3-4 días | Fase 0 |
| 2 | Sistema Peras | 5-7 días | Fase 1 |
| 3 | Economía | 3-4 días | Fase 2 |
| 4 | Vagón | 2-3 días | Fase 1, 3 |
| 5 | UI | 3-4 días | Fase 3, 4 |
| 6 | Mejoras | 2-3 días | Fase 3, 5 |
| 7 | Testing | 2-3 días | Todo |

**Total estimado:** 21-29 días (~4-5 semanas)

---

## 📝 Notas de Escalabilidad

### Para Multiplayer (Post-MVP)
- Replicar parcelas para N jugadores
- Sistema de asignación de parcelas
- Optimización de RemoteEvents
- Sincronización de vagón entre clientes

### Para Más Peras (Post-MVP)
- Array de peras por jugador
- Sistema de árbol y cultivo
- Límite de 15 peras
- Pool de objetos para rendimiento

---

*Última actualización: 23 de Diciembre 2024*
