# Mora Pong

A two-player desktop Pong game written entirely in **Mora 0.4**.

There is no Python, Rust, C, JavaScript, or other host-language implementation in this repository. The application logic is in `app.mora`.

## Controls

- Left player: **W / S**
- Right player: **↑ / ↓**
- **New game** resets the score and positions.

## Run

On Manjaro/Arch, install the desktop runtime dependencies and Mora first:

```bash
sudo pacman -S python python-gobject python-cairo gtk4 libadwaita

git clone https://github.com/ziacik/mora.git
cd mora
sh install.sh
```

Then:

```bash
git clone https://github.com/ziacik/mora-pong.git
cd mora-pong
mora check app.mora
mora run app.mora
```

## Architecture

The game declares its own state and rules in Mora:

- paddle positions and velocities
- ball position and velocity
- scoring
- serves and reset
- keyboard bindings
- 16 ms game tick
- 2D scene primitives

The Mora runtime only supplies generic keyboard/timer delivery, arithmetic, 2D motion/collision primitives, and GTK drawing. It contains no Pong-specific game rules.
