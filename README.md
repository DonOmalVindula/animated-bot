# Creating SVG Animations Using Framer Motion

This repository contains the code for creating SVG animations using Framer Motion in a React application. The project demonstrates how to animate a static SVG image by breaking it into logical components and applying animations.

## Getting Started

Follow these steps to set up and run the project locally:

### Prerequisites

- Node.js
- pnpm

### Installation

1. **Create a new Vite React project with TypeScript:**

    ```sh
    pnpm create vite animated-bot --template react-ts
    ```

2. **Navigate to the project directory:**

    ```sh
    cd animated-bot
    ```

3. **Install the dependencies:**

    ```sh
    pnpm install
    ```

4. **Start the development server:**

    ```sh
    pnpm run dev
    ```

    The application should now be running on [http://localhost:5173](http://localhost:5173).

## Project Structure

- `src/assets/ai-bot.svg`: The SVG file for the AI bot.
- `src/App.tsx`: Main application component.
- `src/components`: Contains React components for each part of the SVG.

## Adding Animations

To add animations to the SVG components, follow these steps:

1. **Install Framer Motion:**

    ```sh
    pnpm install framer-motion
    ```

2. **Create animated components using Framer Motion:**

    ```jsx
    import { motion } from 'framer-motion';

    const AnimatedHead = (): ReactElement => {
        const variants: Variants = {
            botAnimation: {
                rotate: 0,
                transition: {
                    delay: 0.3,
                    duration: 3,
                    repeat: Infinity,
                    repeatDelay: 0.5,
                    repeatType: "reverse",
                    type: "tween"
                },
                y: [-5, 5]
            }
        };

        return (
            <motion.g id="bot-head" variants={variants}>
                {/* SVG path data */}
            </motion.g>
        );
    };

    export default AnimatedHead;
    ```

3. **Combine animated components in the main SVG component:**

    ```jsx
    import { motion } from 'framer-motion';
    import AnimatedHead from './components/AnimatedHead';
    import AnimatedTorso from './components/AnimatedTorso';
    
    const BotAnimatedWithBackGround = (): ReactElement => {
        const variants: Variants = {
            botAnimation: {
                rotate: 0,
                transition: {
                    delay: 0.3,
                    duration: 6,
                    repeat: Infinity,
                    repeatDelay: 0.2,
                    repeatType: "reverse"
                },
                y: [0, 12]
            }
        };

        return (
            <svg className="loading-screen-animation" width="728" height="500" viewBox="0 0 728 500" fill="none" xmlns="http://www.w3.org/2000/svg">
                <motion.g id="ai-bot" animate="botAnimation" variants={variants}>
                    <AnimatedHead />
                    <AnimatedTorso />
                </motion.g>
            </svg>
        );
    };

    export default BotAnimatedWithBackGround;
    ```

4. **Import the main animated SVG component in `App.tsx`:**

    ```jsx
    import './App.css';
    import BotAnimatedWithBackGround from './components/BotAnimatedWithBackGround';

    function App() {
        return <BotAnimatedWithBackGround />;
    }

    export default App;
    ```

## Contributing

Feel free to open issues or submit pull requests if you find any bugs or have suggestions for improvements.

## License

This project is licensed under the MIT License.
