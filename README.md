# Risk

Risk is a Python project for analyzing the board game Risk. There is only one code file (risk.ipynb) and all of the data is created from simulation. All of the simulation is original code. This project focuses on 30 nuanced behaviors that vary the territory selection and reinforcement strategies of the players. There are 10 unique territory selection behaviors and 3 reinforcement behaviors with the permutations making 30. The choice to attack is consistent across player strategies and is very nuanced in players only attack when their surrounding territories outnumber an enemy node and they use troops from their nodes that are less likely to be retaliated against because they have less edges. A, perhaps, simpler version of this attacking decision is what I observe in actual gameplay.

territory selection: 
'r' random, randomly selects territories from those remaining
'i' isolationist, selects the territories with the least neighbors, tie goes to those that have high cluster coefficients so that attackers have other options
'n' network, selects the territories with the most neighbors, tie goes to those that have low cluster coefficients so that everything passes through their nodes
'c' connecter, selects territories that are connected to ones it already owns; if none available maximizes neighbors and cluster coefficients
'u' united states, selects territories in N America first, then territories with the least neighbors. They're going for the continent bonus.
's' south america, selects territories in S America first, then territories with the least neighbors. They're going for the continent bonus.
'p' pacific islands, selects territories in Australia first, then territories with the least neighbors. They're going for the continent bonus.
'f' africa, selects territories in Africa first, then territories with the least neighbors. They're going for the continent bonus.
'e' europe, selects territories in Europe first, then territories with the least neighbors. They're going for the continent bonus.
'm' middle east, selects territories in Asia first, then territories with the least neighbors. They're going for the continent bonus.

play style: 
'r' random, places troops completely randomly for the initial phase; reinforcements are placed randomly on their front (if reinforcements are placed completely randomly, there is a good chance that a game between multiple players with this strategy won't finish so I had to revise my code.
'a' aggressive, places troops on their front in a way that maximizes vulnerability of enemy nodes; Tie goes to their territory with the least troops
'd' defensive, places troops on their front in a way that maximizes protection of their own nodes

The principles of the game stack up pretty well with the science of war which dictates attacking with overwhelming mass where the enemy doesn't have mass. It's not a stretch to make a game of risk into legitimate combat modeling. Seeing which principles work in how to distribute mass in a complex network like this game has carry over and insight into most networked systems, but especially ones that are being competed over and where mass matters in a stochastic outcome. Voting districts, business placement for competing firms, etc. Writing off the project as just a board game without appreciating the parallels and insights offered would be a mistake.

I decided to minimize the reinforcement learning aspects in the initial phase of the project because it gives less inference to successful and consistant strategies a human brain can understand. There are a few papers in business insider that went this route, but the actual insights were guessed at from watching the computer play and were very general. I am using some aspects of reinforcement learning, but as a more manual process so I can get direct insights into what's happening.

Data is gathered by running each of the strategies against four players 100 times with those players given randomly selected strategies that change each game.
Wins are tracked as 1
Losses are tracked as 0
The turn is also returned, either for when the player wins, or when the player got knocked out.

I use T tests to show which strategies are significantly better than other strategies, which strategies win faster, and which strategies lose faster.

## Data Sources
None. All data is pulled from simulated 5 player games of risk. All the rules of risk are followed with all of their interdependencies. 

## Installation
Run in Jupyter (preferable), or VS Code. No installation required besides imported libraries.

For Networkx and associated libraries:
```bash
conda install networkx=2.5 -c https://conda.anaconda.org/conda-forge/
pip install nxpd
brew install graphviz` (macOS) or `sudo apt-get graphviz` (Linux)
```
All other libraries are straightforward conda, or pip installs.

## Usage

python
Everything needed for this project is in the risk.ipynb file
1. Run the first two code blocks to import libraries and construct the graph
2. Run all the functions
3. Run the Game class once the previous 2 steps are complete1

Make use of changing the number of players (2-6 players) and their behaviors (30 different behavior types). 
Descriptions of the behaviors are above. To specify the behavior type for a player, the 1st character is their territory selection behavior type, the 2nd character is their play style, the 3rd character is a unique single digit identifying number. For instance:

['cr1','id2','ua3'] is a 3 player game where the first player chooses connected territories to start and then randomly assigns their troop distribution.

Running a single game is not enough to generate data which is why we have the create_data_dict function. It takes in the behavior of the test player and the number of experiments to run. The parameters can be further tweaked in the play_multiple_games function which is currently set up for a test player and four other randomly determined player types, but can easily be modified with the structure of player strategy formatting described in the above paragraph. The create_data_dict function returns a dictionary with the keys being player strategy types, and the values being list of lists of whether or not they won (1 win, 0 lose) and the turn at which they won, or were defeated.


## EDA


## Modeling


## Conclusions


## Future Work and Data
Research evolutionary algorithms to see which strategy performs the best against strategies in a robust manner as it's run for a really long time. 
Longer term, I'll prep the framework for reinforcement learning where I'm giving it the incentives, no strategies, and it figures out all of it's own behaviors. 

## Contributing
Pull requests are welcome. Please message https://github.com/Trevor-McLemore/
with any errors, changes, or suggestions.

## Link
Rules for Risk can be found on the Hasbro website at:
https://www.hasbro.com/common/instruct/risk.pdf

## License
Copyright (c) [2021] [Trevor McLemore]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
