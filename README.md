# Pokemon Level Optimizer 🎮

An interactive web application that calculates the optimal leveling strategy for Pokemon to reach a target point threshold while minimizing coin expenditure.

## 🌟 Live Demo

[View Live Application](https://mabasiri95.github.io/pokemon-level-optimizer/)

## 📋 Problem Statement

You have multiple Pokemon, each with:
- A current level
- Points earned per level (varies by Pokemon)
- A leveling cost system where leveling from level L to L+1 costs L coins

**Goal:** Reach a target point threshold (e.g., 10,000 points) while spending the minimum number of coins.

## 🧮 Mathematical Foundation

### Core Formulas

**1. Current Points Calculation:**
```
Total Points = Σ(Level_i × PointsPerLevel_i) for all Pokemon i
```

**2. Cost to Level Up:**
- From level L to L+1: **L coins**
- From level L₁ to L₂: **Σ(i) for i = L₁ to L₂-1**

Using the arithmetic series formula:
```
Cost(L₁ → L₂) = (L₂-1) × L₂ / 2 - (L₁-1) × L₁ / 2
```

**3. Efficiency Ratio:**
```
Efficiency = Points Gained / Coins Spent = P / L
```
Where:
- P = Points per level for the Pokemon
- L = Current level of the Pokemon

### Optimization Algorithm

The solution uses a **Greedy Algorithm** approach:

1. Calculate efficiency ratio for each Pokemon: `E_i = P_i / L_i`
2. Select the Pokemon with the highest efficiency
3. Level it up by 1
4. Recalculate efficiencies
5. Repeat until target points reached

**Why Greedy Works:**
- Each leveling decision is independent
- Cost increases monotonically with level
- We want to maximize points per coin at each step
- The greedy choice (highest current efficiency) is always optimal

### Proof of Optimality

The greedy algorithm is optimal because:

1. **Optimal Substructure:** If we need N total levels to reach our goal, the optimal solution includes the optimal choice for each individual level.

2. **Greedy Choice Property:** At any point, choosing the Pokemon with the highest efficiency (points/coin) is always part of an optimal solution.

3. **No Backtracking Needed:** Once a Pokemon is leveled, we never need to "undo" that choice for a better solution.

### Complexity Analysis

- **Time Complexity:** O(N × M) where N = levels needed, M = number of Pokemon
- **Space Complexity:** O(N) for storing the leveling sequence

## 🚀 Features

- **Dynamic Input:** Customize Pokemon levels and point values
- **Real-time Efficiency Calculation:** See which Pokemon is most efficient at any moment
- **Optimal Strategy:** Calculates minimum coins needed
- **Detailed Sequence:** View step-by-step leveling decisions
- **Visual Results:** Clear display of costs and final states

## 💻 Usage

### Online
Simply open the [live demo](https://mabasiri95.github.io/pokemon-level-optimizer/) in your browser.

### Local Development
1. Clone the repository:
```bash
git clone https://github.com/mabasiri95/pokemon-level-optimizer.git
cd pokemon-level-optimizer
```

2. Open `index.html` in your browser:
```bash
# On macOS
open index.html

# On Linux
xdg-open index.html

# On Windows
start index.html
```

No build process or dependencies required!

## 📊 Example

**Initial State:**
- Pokemon 1: Level 34, 65 points/level → 2,210 points
- Pokemon 2: Level 23, 50 points/level → 1,150 points
- Pokemon 3: Level 30, 60 points/level → 1,800 points
- Pokemon 4: Level 29, 60 points/level → 1,740 points
- Pokemon 5: Level 1, 60 points/level → 60 points

**Current Total:** 6,960 points  
**Target:** 10,000 points  
**Points Needed:** 3,040 points

**Initial Efficiencies:**
- Pokemon 1: 65/34 = 1.91 points/coin
- Pokemon 2: 50/23 = 2.17 points/coin
- Pokemon 3: 60/30 = 2.00 points/coin
- Pokemon 4: 60/29 = 2.07 points/coin
- Pokemon 5: 60/1 = **60.00 points/coin** ⭐

Pokemon 5 has exceptional efficiency at low levels and will dominate early leveling.

## 🛠️ Technologies

- React 18.2.0
- Tailwind CSS
- Vanilla JavaScript
- HTML5

## 📝 License

MIT License - feel free to use this project for learning or personal use.

## 👤 Author

**Your Name**
- Portfolio: [mabasiri95.github.io](https://mabasiri95.github.io)
- GitHub: [@mabasiri95](https://github.com/mabasiri95)

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

## ⭐ Show Your Support

Give a ⭐️ if this project helped you!