# Reaction Timer

This project is a reaction timer game built with Vue.js. The game measures the time it takes for the player to click the block after it turns green.

## How to Use

1. Clone this repository to your local machine.

```bash
git clone https://github.com/dzhu0/reaction-timer
```

2. Navigate to the project directory.

```bash
cd reaction-timer
```

3. Install dependencies using npm:

```bash
npm install
```

4. Run the development server:

```bash
npm run dev
```

5. Open your browser and go to [http://localhost:5173](http://localhost:5173).
6. Click on the "play" button to start the game.
7. Wait for the block to turn green, then click the block as quickly as possible.
8. After clicking, the reaction time will be displayed.

## Components

### Block

- The `Block` component displays a clickable block on the screen.
- It appears after the game starts and disappears once the player clicks on it.

### Results

- The `Results` component displays the reaction time after the game ends.
- It appears once the player clicks on the block and disappears when the game restarts.

## License

This project is licensed under the MIT License. See the [LICENSE.md](LICENSE.md) file for details.
