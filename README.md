# Monster-Evolution-Algorithm
This is a monster evolution algorithm created for a pixel art game within an Algorithms class learning concert.

This repository contains an implementation of a **Genetic Algorithm**. The program demonstrates how characteristics of monsters evolve across generations based on their performance (fitness score or `m_time`).

## How It Works

1. **Monsters and Characteristics**: 
   Each monster has a set of characteristics represented as a list of integers. These characteristics are what we evolve through the algorithm.

2. **Selection**: 
   The monsters are ranked based on their performance (`m_time`). The better a monster performs, the higher its rank, and the more likely its characteristics will be passed on to the next generation.

3. **Crossover**: 
   A new generation of monsters is created by combining the characteristics of the top-ranked monsters. Additionally, some characteristics may be mutated to introduce variation into the population.

4. **Mutation**: 
   A random characteristic of the top-performing monsters is slightly modified in order to explore new possible traits.

## Usage

### Parameters

- Each monster has **two key attributes**:
  1. **`monster`**: A list of integers representing the characteristics of the monster (e.g., `[2, 3, 4]`).
  2. **`m_time`**: The performance time or fitness score of the monster (e.g., `10`).

- You can modify these parameters when initializing each monster. For example:
  ```python
  m1 = Genetic_Algorithm([2, 3, 4], 10)
  m2 = Genetic_Algorithm([2, 2, 4], 8)
  m3 = Genetic_Algorithm([3, 1, 4], 6)
  m4 = Genetic_Algorithm([2, 2, 3], 5)
  ```

- The performance time (`m_time`) can be any integer value, where a higher value indicates better performance in this example.

### Running the Code

The program runs through the following steps:

1. **Selection**: The monsters are ranked based on their performance time (`m_time`).
2. **Crossover**: The characteristics of the best monsters are combined to create a new generation.
3. **Mutation**: Some characteristics are slightly modified to introduce variety.

### Example Output

When you run the program, you will see output similar to this:

```
NEW GENERATION
Monster 1 Characteristics: [2, 3, 3]
Monster 2 Characteristics: [3, 4, 4]
Monster 3 Characteristics: [2, 3, 4]
Monster 4 Characteristics: [2, 2, 2]
```

This output shows the characteristics of the new generation of monsters after the selection, crossover, and mutation processes.

### How to Modify

To adjust the behavior of the genetic algorithm, you can change:

- **Characteristics of the Monsters**: Modify the list of integers representing the monster’s attributes.
- **Performance Time (`m_time`)**: Adjust the performance or fitness score of each monster to simulate different rankings.
- **Mutation Index**: The mutation happens at random indices (`a` and `b`). You can adjust these parameters or introduce more complex mutation logic.
