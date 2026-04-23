# 🎱 8-Pool Club Manager

> A sleek Windows desktop app for managing pool club sessions — track time, calculate fees, and never lose a game's records again!

---

## What is this? 🏋️

A real-world pool club management system built with **C# & Windows Forms**. It lets you run timers for multiple pool tables, charges players based on play time, and logs every session to the Windows Event Log. Basically — if you've ever worked at a pool hall, you'd wish you had this.

---

## Features ✨

- **⏱️ Multi-Table Session Tracking** — Run independent timers for multiple pool stations simultaneously
- **💰 Auto Fee Calculation** — Calculates charges based on configurable hourly rates per table
- **🎮 Event-Driven Design** — Custom events fire when games finish, keeping things decoupled and clean
- **📋 Windows Event Viewer Integration** — Every completed session gets logged with player name, table, duration & timestamp
- **♻️ Reusable UserControl** — `ctrlPoolStation` is a drag-and-drop component you can reuse across any form
- **🛠️ PropertyGrid-Ready** — All settings (player name, table name, hourly rate) are configurable right from Visual Studio's designer

---

## Tech Stack

| Layer | Technology |
|-------|------------|
| Framework | .NET Framework 4.8 |
| UI | Windows Forms (WinForms) |
| Language | C# |
| IDE | Visual Studio 2022 |

---

## Architecture Highlights 🏗️

The project follows a clean **component-based architecture**:

- **`ctrlPoolStation`** — Self-contained UserControl that manages its own timer, state, and events. Zero dependencies on the parent form.
- **`clsUtils`** — A sealed utility class with a custom `cls8PoolEventArgs` event argument that carries session data (time, fees, rate) back to subscribers.
- **Event-driven communication** — Parent form subscribes to `OnGameFinish` events instead of tightly coupling controls directly.

> This means you can drop a new pool station onto any form and it just works. No wiring required beyond handling the event.

---

## How It Works 🔄

```
Player hits START
    → Stopwatch begins, UI timer updates every second
    → Player hits CLOSE
    → Timers stop, session logged to Windows Event Viewer
    → OnGameFinish event fires with session data
    → Parent form receives billing info and shows total to player
    → Station resets for next game
```

---

## Getting Started 🚀

### Prerequisites
- Windows OS
- Visual Studio 2022

### Run It
```bash
# Open the solution file
MyPoolClubProject.sln

# Press F5 to run (or Ctrl + F5 for without debugging)
```

> Make sure to run Visual Studio **as Administrator** so the Event Viewer logging works properly.

---

## Future Improvements 🔮

- [ ] Save sessions to a database instead of just Event Viewer
- [ ] Add a dashboard with daily/weekly revenue stats
- [ ] Support for pausing and resuming games
- [ ] Multi-language support
- [ ] Export reports to PDF/CSV

---

## Why I Built This 💡

I wanted to get comfortable with **event-driven programming** and building **reusable UI components** in WinForms. This project taught me how to design controls that are truly self-contained and how to pass data around using custom event arguments. Plus — pool clubs are cool 😎

---

*Built with ☕ and a love for clean code*
