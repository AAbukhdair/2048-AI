# 2048 AI

AI Plays 2048: A Reinforcement Learning Project
This project features an AI agent that learns to play the strategic puzzle game 2048. Using a Q learning algorithm, the AI starts with no prior knowledge and develops complex strategies by playing thousands of games in a web based environment.

Description
2048 is a challenging game where the player slides numbered tiles on a 4x4 grid to merge them into higher value tiles, aiming to create the "2048" tile and achieve the highest score possible. This environment is particularly interesting for reinforcement learning due to its large state space and the sparse, delayed nature of its rewards. An action might not yield an immediate reward, but could be crucial for setting up a high scoring merge several moves later.

This project allows you to observe the AI's learning process in real time. Initially, its moves are random and chaotic. Over many episodes, you will see it begin to discover and apply effective strategies, such as keeping the highest value tile in a corner and arranging other tiles in descending order.

How the AI Learns (Q learning)
The AI agent uses Q learning, a model free reinforcement learning technique, to figure out the best action to take in any given game state.

State: The game has billions of possible board configurations. To make this manageable, the AI represents the state by taking the log2 of each tile's value (e.g., a tile with '8' becomes 3, '16' becomes 4, and an empty tile is 0). This compresses the state space while preserving the essential information about the board. The state is a flat array of these 16 log values.

Actions: The AI can choose from four possible actions: Up, Down, Left, or Right. The agent first determines which of these moves are valid (i.e., will actually change the board).

Reward System: The AI's primary motivation is the reward it receives for making good moves. In this implementation, the reward for any given move is the sum of the values of the tiles that were merged. For example, merging two '128' tiles to create a '256' tile gives the AI a reward of 256. This encourages the agent to seek out and execute merges.

Learning Process (Q Table): The AI maintains a "Q table," which is a massive dictionary that maps a (state, action) pair to an expected future reward (a Q value). After each move, the Q table is updated using the Bellman equation, which allows the agent to refine its predictions based on the actual reward received. Over time, the Q values converge, giving the AI a reliable "cheat sheet" for what to do in any situation.

Exploration vs. Exploitation: The Epsilon (ε) value controls the AI's strategy.

When Epsilon is high, the AI is in exploration mode, making random moves to discover new states and strategies.

As Epsilon slowly decays with each completed game, the AI shifts to exploitation mode, increasingly relying on its Q table to make the highest reward moves it has learned.

Features
Live AI Training: Watch the AI play and learn directly in your browser.

Real Time Statistics: The UI displays the current score, max score, max tile achieved, number of games (episodes) played, and the current Epsilon value.

Training Controls:

Speed Up Training: Run the simulation at high speed to accelerate the learning process.

Normal Speed: Watch the AI play individual games move by move.

Reset AI Memory: Clear the Q table to start the learning process from scratch.

Visual Interface: The game board is rendered with clean, color coded tiles for easy viewing.

Self Contained Code: The entire project is built with vanilla HTML, JavaScript, and Tailwind CSS in a single file.
