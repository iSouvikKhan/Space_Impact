# Space_Impact

Java source code for a simple side-scrolling 2D space game for Android. The player's ship sits on the left side of the screen while stars and enemy ships scroll in from the right.

## Gameplay

- The game runs in landscape mode on a `SurfaceView`, with a scrolling starfield background.
- Touch and hold the screen to boost the ship upward; release to let it fall back down (a simple gravity effect).
- Three enemy ships move from right to left at random speeds.
- Colliding with an enemy shows an explosion, plays a sound effect, and adds 5 points to the score.
- When 5 enemies have passed the left edge of the screen, the game ends and the score screen opens.
- The score is saved, and the high score screen lists all saved scores.
- The main menu has buttons to play, exit, toggle background music, and show/hide an info text.
- The game screen has a pause/resume button.

## Tech Stack

- Java
- Android SDK (`SurfaceView`, `Canvas`, `MediaPlayer`, `SoundPool`)
- Android Support Library (`AppCompatActivity`)

## Project Structure

```
project/
  MainActivity.java     Main menu: play, exit, music toggle, info text
  GameActivity.java     Hosts the GameView, background music, pause/resume button
  GameView.java         Game loop (update/draw at ~60 FPS), collisions, scoring, touch input
  Player.java           Player ship: boosting, gravity, bounds, collision rectangle
  Enemy.java            Enemy ships: random speed/position, respawn, collision rectangle
  Star.java             Scrolling background stars
  Boom.java             Explosion image shown on collision
  Highscore.java        End-of-game screen: shows and stores the score
  MainHighScore.java    Lists all stored scores
```

All classes are in the package `com.example.shefaliupadhyaya.project1`.

## Important Note

This repository contains only the Java source files. It does not include the files needed to build the app on its own:

- Gradle build files and `AndroidManifest.xml`
- Resources: layouts (`activity_main`, `activity_highscore`, `activity_main_high_score`, `score_list`), menus, drawables (`player`, `enemy`, `boom`, icons), and raw audio (`skywanderer`, `dualdragon`, `whoosh`)
- The `DBHelper` class used by `Highscore` and `MainHighScore` to store and read scores (`insertScore`, `getAllScores`)

## How to Run

1. Create a new Android project in Android Studio with the package name `com.example.shefaliupadhyaya.project1` (or update the package declarations).
2. Copy the files from `project/` into the project's Java source folder.
3. Add the missing resources, the `DBHelper` class, and register the activities in `AndroidManifest.xml`. `GameActivity` and `MainHighScore` are started with implicit intents (`com.example.shefaliupadhyaya.project1.GameActivity` and `com.example.shefaliupadhyaya.project1.MainHighScore`), so they need matching intent filters.
4. Build and run the app on a device or emulator.
