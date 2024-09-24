# bitsy-fast-startup-walk-hack
e Bitsy Fast Startup Walk Hack modifies the default player movement timer in Bitsy, allowing players to start moving faster upon initiating their movement. This hack changes the player movement delay from 500 milliseconds to 150 milliseconds, enhancing the responsiveness of character movement right from the start.

# Changing the Movement Timer in Bitsy

This guide provides instructions on how to change the value of `playerHoldToMoveTimer` in the Bitsy game code from 500 to 150. This modification will allow the player to move more quickly when holding down the directional keys.

## Prerequisites

- Have [Bitsy](https://bitsy.itch.io/bitsy) installed.
- A text editor (like VSCode, Notepad++, etc.).
- Access to the terminal.

## Step-by-Step Guide

### 1. Navigate to the Game Directory

Open the terminal and navigate to the directory where your Bitsy project is located. Use the `cd` command to change directories. For example:

```bash
cd /path/to/your/project
```

### 2. Create a Backup of the Original File

Before making any changes, it’s good practice to back up the original file. Use the following command:

```bash
cp bitsy_game.html bitsy_game.html.bkp
```

### 3. Create a Script to Change the Code

To automate the change, you can use a `sed` command that will replace the value of `playerHoldToMoveTimer` in the `game.js` file. Run the following command:

```bash
sed -i 's/playerHoldToMoveTimer = 500;/playerHoldToMoveTimer = 150;/' bitsy_game.html
```

### 4. Verify the Change

Open the `bitsy_game.html` file in your text editor and check if the line has been changed correctly:

```javascript
if (curPlayerDirection != Direction.None && curPlayerDirection != prevPlayerDirection) {
    movePlayer(curPlayerDirection, true /* isFirstMove */);
    playerHoldToMoveTimer = 150; // Changed to 150
}
```

### 5. Run the Game

Now, you can run the game normally. The value of `playerHoldToMoveTimer` should be 150, allowing for faster movement.

---

## Instructions to Modify Player Movement Speed in Bitsy

1. **Locate the Line to Change:**
   Open your Bitsy code file and search for the following block of code:

```javascript
if (playerHoldToMoveTimer <= 0) {
    movePlayer(curPlayerDirection, false /* isFirstMove */);
    playerHoldToMoveTimer = 150;
    // playerHoldToMoveTimer = 16; // PERF TEST
}
```

2. **Modify the Value:**
   Change the value of `playerHoldToMoveTimer = 150;` to your desired value, such as `100`.

   The modified block should look like this:

```javascript
if (playerHoldToMoveTimer <= 0) {
    movePlayer(curPlayerDirection, false /* isFirstMove */);
    playerHoldToMoveTimer = 100;
// playerHoldToMoveTimer = 16; // PERF TEST
}
```

---

### Automating the Change with `sed`

To automatically update a instance of `playerHoldToMoveTimer = 150;` to `playerHoldToMoveTimer = 100;`, you can run the following command in your terminal:

```bash
sed -i 's/playerHoldToMoveTimer = 150;/playerHoldToMoveTimer = 100;/' path/to/your/bitsy_game.html
```

Make sure to replace `path/to/your/bitsy/bitsy_game.html` with the actual path to your Bitsy code file.

This will ensure that all instances of the player movement timer are adjusted to speed up movement in the game.

---

## Final Considerations

Be sure to test the game after the change to ensure everything is functioning as expected. If you encounter any issues, you can restore the original file from the backup you created earlier.
