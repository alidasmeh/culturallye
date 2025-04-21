# culturallye

# Main Game Rule
In this game, 9 players are divided into 3 groups. Each person starts with 20 coins. In each group, there are two dice: one die shows numbers from 1 to 6, and the other die has 6 different symbols.
Each symbol on the die corresponds to a specific behavior. At the beginning of the game, each group is separately informed about what behavior is associated with each symbol. The rules differ between groups, and no one knows the rules are different between the groups.

The game consists of 10 sets, and each set contains 10 rounds.

Each round proceeds as follows: the player whose turn it is rolls both dice, and the other two members of the group must act according to the symbol shown. The player who rolled the dice then decides which of the two was slower in reacting, and that person is considered the loser. The loser must give the dice-roller a number of coins equal to the number shown on the second die (the numbered one). If the loser doesn’t have enough coins, they must give all they have.

The turn then passes to the player on the right, and the rounds continue in this way.
At the end of 10 rounds, the person with the most coins in each group is the winner and must be transferred to a different group. A new set is then formed with a reshuffled mix of players.

In the entire game no one is allowed to speak. Players are only allowed to roll dice, do the behaviours based on the symbols. 

# But in this simulation
In this simulation, each player has a `cognitive_ability` attribute that is assigned at the beginning of the experiment. This value can change during each round. Whenever a player wins, their cognitive ability decreases by a value defined by `COGNITIVE_ABILITY_DECREASE_RATE`, and they are transferred to the next group. Over the following rounds, their cognitive ability gradually increase based on `COGNITIVE_ABILITY_COMPENSATION_RATE_PER_ROUND`, for a number of rounds specified by `NUMBER_OF_ROUND_FOR_COMPENSATION`.

The way players perform in each round is determined by the play function within the Player class. A player’s performance is calculated by multiplying the hardness of the symbol by their current cognitive ability, plus a random noise in the range of -0.1 to +0.1.

Both the hardness and cognitive_ability values range between 0 and 1.

# Results in 2025 April 21.
If a player’s cognitive ability is fully restored during a set, then based on `COGNITIVE_ABILITY_DECREASE_RATE`, `COGNITIVE_ABILITY_COMPENSATION_RATE_PER_ROUND`, and `NUMBER_OF_ROUND_FOR_COMPENSATION`, it is estimated that 70% of the players who win in the first set are also likely to win after 10 sets.

For example, if `COGNITIVE_ABILITY_DECREASE_RATE = 0.5`, `COGNITIVE_ABILITY_COMPENSATION_RATE_PER_ROUND = 0.05`, and `NUMBER_OF_ROUND_FOR_COMPENSATION = 10`, it means that the winner of the previous set starts the new set with a much lower `COGNITIVE_ABILITY` than before. In each round of the new set, their `COGNITIVE_ABILITY` improves by `0.05`.