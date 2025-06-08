

# 🧠 Grid Game 

## 📦 Project Structure

```
/project-root/
│
├── index.html                # Entry point of the game UI
├── css/
│   └── styles.css            # Game styling
├── js/
│   ├── GameStateManager.js   # Core game state logic
│   ├── Renderer.js           # UI rendering logic
│   ├── InputHandler.js       # Keyboard & button controls
│   └── main.js               # Bootstraps the game
```

---

## 🕹️ Core Concepts

### 🎮 Game State Management (`GameStateManager.js`)

This is the heart of the game. It encapsulates:

* **Player Data**: Position, health, inventory.
* **Environment**: 2D map (`G`, `W`, `B` = Grass, Water, Wall), doors, keys.
* **Items**: Sword (attack), Potion (heal).
* **Monsters**: Grid enemies that damage the player.
* **State History**: For tracking transitions & debugging.
* **Save/Load Support**: JSON-based snapshot and restore.

### 🔁 Transitions & Interactions

Handled through clean methods like:

* `movePlayer(x, y)`
* `pickupItem(itemId)`
* `useItem(itemId)`
* `openDoor(doorId)`
* `damagePlayer(amount)`
* `resetState()`, `saveState()`, `loadState()`

Each transition is validated and stored to maintain consistency.

---

## 🖥️ Rendering Engine (`Renderer.js`)

Responsible for:

* Drawing the 2D grid.
* Showing player/monsters/doors/items with emojis.
* Managing health bar, game-over state, and inventory.
* Showing current game state in readable JSON format.

---

## 🎮 Input System (`InputHandler.js`)

Links keyboard controls and UI buttons:

* `W/A/S/D`: Movement.
* `X`: Use sword (attack nearby monster).
* `P`: Use potion (restore health).
* Buttons: Save, Load, Reset, View State.

Includes a **combat system** with timed damage (every 1s) when near monsters.

---

## 🚀 Getting Started

1. **Run it locally:**

   * Just open `index.html` in a browser.
   * Make sure JS and CSS folders are alongside it.

2. **Controls:**

   * Move: `W/A/S/D`
   * Use Sword: `X`
   * Use Potion: `P`
   * Save/Load/Reset: Use UI buttons

3. **To test features:**

   * Try picking up sword/potion/key.
   * Try attacking a nearby monster.
   * Walk near a locked door with the right key.
   * Die in combat and reset the game.

---

## 📁 Import & Use

To import into your own system or integrate:

```html
<!-- In your HTML -->
<script src="js/GameStateManager.js"></script>
<script src="js/Renderer.js"></script>
<script src="js/InputHandler.js"></script>
<script src="js/main.js"></script>
```

Ensure DOM IDs used in `Renderer` (`game-board`, `health-bar`, etc.) exist in your HTML.

---

## 🧩 Design Principles Followed

* **Encapsulation**: State is managed only through class methods.
* **Separation of Concerns**: UI, logic, and input are modular.
* **Edge Case Handling**: Invalid movement, using items not owned, etc.
* **Extensibility**: Easy to add more monsters, items, map types.
* **State Persistence**: JSON-based, human-readable saves.
* **Validation**: Before committing any state change.

---

## 🪞 Reflection & Rationale

### ✅ Design Choices

* Used **nested objects** and **arrays** for clarity and fast lookup (e.g., `keys`, `doors`).
* All state mutations go through well-defined APIs, ensuring control.

### 🔄 Trade-offs

* JSON-based save/load is lightweight but may not scale with large maps or more complex game logic.
* Used emojis for rendering simplicity—ideal for a quick prototype.

### ❓ Uncertainty

* Did not implement map editing or complex AI behavior—left for future improvement.
* Inventory is simple; a more structured system might be needed in a full game.

### 🤖 AI Assistance

Used AI tools for:

* Drafting function names and structure.
* Getting ideas for emoji representations.
* Did **not** copy logic directly; all gameplay logic was written and modified manually.

---

## 🧠 How It Scales

In a bigger game, the same state engine can:

* Add **NPCs**, **quests**, **multi-player sync** (via shared state).
* Enable **save slots** and **auto-save**.
* Integrate with a physics engine or canvas renderer.

