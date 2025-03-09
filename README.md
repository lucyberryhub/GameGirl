# **🍓🎮 Create GameGirl game from scratch 🍒💖**  

## 🍒✨ **Step 1: Set Up the GameGirl Dev Environment** 🎀  

First, let's get your GameGirl game development environment ready, babe! 😘 

### 💖 **You’ll Need:**
1. **GBDK-2020** – This is the GameBoy Development Kit (updated and easy to use).  
   👉 Download from here: [https://github.com/gbdk-2020/gbdk-2020](https://github.com/gbdk-2020/gbdk-2020)  
2. **Code Editor** – I recommend using **VS Code** (it’s free and cute!).  
3. **GameBoy Emulator** – Like **BGB** or **Gambatte** for testing your game.  

### 🌸 **Install GBDK-2020:**
1. Unzip the GBDK-2020 package.  
2. Add the `bin` folder to your system's `PATH` so you can run GBDK commands from anywhere.  

To check if it’s working, open a terminal and type:  
```bash
lcc -v
```
If you see the version info, you’re good to go, sweetie! 😘💖  

---

## 🍓✨ **Step 2: Create Your First GameGirl Project** 🍒  

Let’s make a new folder for your game! 😍  
```bash
mkdir BerryGame
cd BerryGame
```

Create a C file named `main.c` in the `BerryGame` folder:  
```c
#include <gb/gb.h>

void main() {
    // Initialize GameGirl screen
    DISPLAY_ON;
    SHOW_BKG;

    while(1) {
        // Your cutie game loop! 🍓
        // Add game logic here
        wait_vbl_done();
    }
}
```

Now compile it with:  
```bash
lcc -o BerryGame.gb main.c
```

Run it in your emulator! 🍒✨ OMG, you’ve got a blank screen—SO PROUD OF YOU!! 😘🌸

---

## 🍒✨ **Step 3: Add Cute Cherry-Berry Graphics** 🍓  
Let’s make some adorbs pixel art! 🎨💖

### 💖 **Create Sprites:**
1. Use a pixel editor like **Aseprite** or **Piskel**.  
2. Create an 8x8 or 16x16 sprite (cute little Berry-Chan!)  
3. Save it as a `.png` file.  
4. Convert it to GameBoy format using GBDK’s `png2asset` tool:  
```bash
png2asset berry-chan.png
```

### 💖 **Load Sprite in Code:**
In `main.c`, add this:  
```c
#include <gb/gb.h>
#include "berry-chan.h"

void main() {
    set_sprite_data(0, 1, berry_chan); // Load sprite
    set_sprite_tile(0, 0); // Assign sprite to tile
    move_sprite(0, 88, 78); // Position sprite on screen

    SHOW_SPRITES;
    DISPLAY_ON;

    while(1) {
        // Add input handling and movement later! 🍓
        wait_vbl_done();
    }
}
```

Compile and run it, babe! Berry-Chan is on screen!! 🍒💖

---

## 🍓✨ **Step 4: Handle Input (Move Your Berry-Chan!)** 🎮  
Let’s make her MOVE!! 🌸

Add this to your game loop:  
```c
if (joypad() & J_LEFT) {
    scroll_sprite(0, -1, 0);
}
if (joypad() & J_RIGHT) {
    scroll_sprite(0, 1, 0);
}
if (joypad() & J_UP) {
    scroll_sprite(0, 0, -1);
}
if (joypad() & J_DOWN) {
    scroll_sprite(0, 0, 1);
}
```

Now Berry-Chan is ZOOMING around!! 🍓💖

---

## 🍒✨ **Step 5: Add a Cute Background** 🌸  
Make a cute cherry-berry background in Piskel/Aseprite! 🍓🍒  
1. Save as `.png`  
2. Convert to GameBoy format using `png2asset`:  
```bash
png2asset berry-bg.png
```

Add it in `main.c`:  
```c
#include "berry-bg.h"

void main() {
    set_bkg_data(0, 1, berry_bg);
    set_bkg_tiles(0, 0, 20, 18, berry_bg_map);

    SHOW_BKG;
    DISPLAY_ON;

    while(1) {
        wait_vbl_done();
    }
}
```

OMG, Berry-Chan is now vibing in a berry-tastic world!! 🍒💖

---

## 🍓✨ **Step 6: Add Cute Sound Effects** 🎀  
Create a `.wav` or `.vgm` file for sound.  
Convert using **hUGETracker**:  
👉 Download here: [https://github.com/SuperDisk/hUGETracker](https://github.com/SuperDisk/hUGETracker)  

Add it to your project:  
```c
NR52_REG = 0x80; // Turn on sound
NR50_REG = 0x77; // Set volume
NR51_REG = 0xFF; // Enable all channels

// Cute berry jump sound!
void playJumpSound() {
    NR10_REG = 0x16;
    NR11_REG = 0x40;
    NR12_REG = 0x73;
    NR13_REG = 0x00;
    NR14_REG = 0xC3;
}
```

---

## 🍒✨ **Step 7: Add Goals + Scoring** 🍓  
Make Berry-Chan collect cherries! 🍒  
Create a cherry sprite, detect collision, and update score!  

Example:  
```c
if (check_collision(sprite_x, sprite_y, cherry_x, cherry_y)) {
    score++;
    hide_sprite(1); // Hide cherry on collection
}
```

---

## 🍓✨ **Step 8: Polish and Release** 🌸  
- Add cute menus with berry-pink text! 🍓  
- Add animations when Berry-Chan wins or gets a cherry! 🍒  
- Export to `.gb` file and share with the world!! 💖  

---
