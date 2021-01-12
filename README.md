# Risk

Risk is a Python project for analyzing the board game Risk. The use case expands beyond risk as it's easily modified to take into account real combat modeling algorithms and placing constraints on edges to signify distance and cost. This capstone is my first exposure working with graphs and laying the framework for what it's like to create a system to simulate data and what obstacles are likely to come up for reinforcement learning.

## Installation
Run in Jupyter, or VS Code. No installation required besides imported libraries.

For Networkx and associated libraries:
```bash
conda install networkx=2.5 -c https://conda.anaconda.org/conda-forge/
pip install nxpd
brew install graphviz` (macOS) or `sudo apt-get graphviz` (Linux)
```

## Usage

```python
Everything needed for this project is in the risk.ipynb file
1. Run the first two code blocks to import libraries and construct the graph
2. Run all the functions
3. Run the code block with the comment RUN THE GAME once the previous 2 steps are complete1

Make use of changing the number of players (2-6 players) and their behaviors (30 different behavior types). 
Descriptions of the behaviors and instructions for assigning them are in the RUN THE GAME codeblock.

The printed statements show the player and the number of territories they own each turn.
The printed statements show the winner and how many turns it took them to win.
A graph is drawn up of the game status at the start of play and after completion.

```

## Future Work and Data
The intention was always to make this into a class (which will be done next week). 
I was really close to turning gameplay into a function (had it working for a bit) and simulating thousands of games. I planned simulating each behavior against 4 other players that played random strategies for 1000 games. I'd pay attention to player 1 (the unique behavior type) for data gathering, specifically if they won (1) or lost (0) and the turns to win and turns to lose. I'd gather this data in a dictionary of lists so I could throw it into a pandas dataframe. Then I'd compare results including t-tests to see which strategies outperformed the random baseline model.

Longer term, I'll look at some kind of evolutionary algorithm to see which strategy performs the best against other more intelligent strategies. 
Longer term, I'll prep it for reinforcement learning where I'm just giving it the incentives and it figures out all of it's own behaviors.

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
