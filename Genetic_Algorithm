import random

class Genetic_Algorithm:

    def __init__(self, monster, m_time):
        self.m = monster
        self.m_t = m_time
        self.c = [0, 0, 0, 0]  # Characteristics of top 4 ranked monsters
        self.n = [0, 0, 0, 0]  # Ranking scores of top 4 monsters
        self.n_m = [[], [], [], []]  # New generation monsters
        self.a = random.randint(0, 2)  # Random index for mutation
        self.b = random.randint(0, 2)
        self.lim = 10  # Limit for characteristics sum

    def selection(self, monsters):
        """
        Rank monsters based on m_time and store their times in self.n.
        """
        times = [monster.m_t for monster in monsters]
        self.n = sorted(times, reverse=True)[:4]

    def associate(self, monsters):
        """
        Associate ranked times with monster characteristics.
        """
        for i, n_rank in enumerate(self.n):
            for monster in monsters:
                if monster.m_t == n_rank:
                    self.c[i] = monster.m
                    break

    def crossover(self):
        """
        Perform crossover to generate a new generation of monsters.
        """
        def limit_and_append(m1, m2, target_list):
            for i in range(3):
                selected = max(m1[i], m2[i])
                if sum(target_list) + selected < self.lim:
                    target_list.append(selected)
                else:
                    target_list.append(selected - (sum(target_list) + selected - self.lim))

        # First NEW Generation Monster (c1, c2)
        limit_and_append(self.c[0], self.c[1], self.n_m[0])

        # Second NEW Generation Monster (c1 mutation)
        mutated_c1 = self.mutate(self.c[0], self.a)
        self.n_m[1] = mutated_c1

        # Third NEW Generation Monster (c2 mutation)
        mutated_c2 = self.mutate(self.c[1], self.b)
        self.n_m[2] = mutated_c2

        # Fourth NEW Generation Monster (c3, c4)
        limit_and_append(self.c[2], self.c[3], self.n_m[3])

        print('NEW GENERATION\n', 
              '\nMonster 1 Characteristics:', self.n_m[0],
              '\nMonster 2 Characteristics:', self.n_m[1], 
              '\nMonster 3 Characteristics:', self.n_m[2], 
              '\nMonster 4 Characteristics:', self.n_m[3])

    def mutate(self, characteristics, index):
        """
        Mutate one characteristic by incrementing it within the limit.
        """
        mutated = characteristics.copy()
        if sum(mutated) < self.lim:
            if mutated[index] < 5:
                mutated[index] += 1
            elif index > 0:
                mutated[index - 1] += 1
            else:
                mutated[index + 1] += 1
        return mutated

# Create monsters with characteristics and performance times
m1 = Genetic_Algorithm([2, 3, 4], 9)
m2 = Genetic_Algorithm([2, 2, 4], 5)
m3 = Genetic_Algorithm([3, 1, 4], 4)
m4 = Genetic_Algorithm([2, 2, 3], 10)

# Store all monsters in a list for easy processing
monsters = [m1, m2, m3, m4]

# Run the genetic algorithm on one monster object (selection and crossover are shared logic)
m1.selection(monsters)
m1.associate(monsters)
m1.crossover()
