# Monte Carlo Project Estimator

> Probabilistic project estimation using PERT Beta distribution with confidence intervals

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-20232A?logo=react&logoColor=61DAFB)](https://reactjs.org/)

## 🎯 Overview

Stop giving single-point estimates that are always wrong. The Monte Carlo Project Estimator runs 10,000+ simulations using PERT Beta distribution to give you realistic timelines with **statistical confidence levels**.

### ✨ Key Features

- **10,000+ Simulations** - Run Monte Carlo simulations using industry-standard PERT Beta distribution
- **Confidence Intervals** - Get 50%, 80%, 90%, and 95% confidence estimates instantly
- **Interactive Charts** - Visualize the probability distribution of project outcomes
- **Export Results** - Download estimates as TXT or CSV for stakeholder reports
- **Privacy First** - All calculations happen in your browser, no data sent to servers
- **Zero Signup** - Open the tool and start estimating immediately

## 🚀 Live Demo

**Try it now:** [Monte Carlo Simulator](https://github.com/Erickuby/portfolio-monte-carlo)

## 📊 How It Works

### 1. Three-Point Estimation

Enter three estimates for your task or project:
- **Optimistic (O)**: Best-case scenario if everything goes perfectly
- **Most Likely (M)**: Your realistic estimate based on experience
- **Pessimistic (P)**: Worst-case scenario accounting for risks

### 2. PERT Formula

The tool calculates the PERT estimate using the weighted formula:

```
Expected Value (μ) = (O + 4M + P) / 6
Standard Deviation (σ) = (P - O) / 6
```

This formula gives 4x weight to your "most likely" estimate, making it more realistic than simple averaging.

### 3. Monte Carlo Simulation

1. Runs your chosen number of simulations (1,000 to 100,000)
2. Each simulation generates a random completion time from the PERT Beta distribution
3. Results are aggregated and sorted
4. Confidence intervals are calculated from the distribution

### 4. Confidence Intervals

The tool shows you completion time estimates at different confidence levels:
- **50%**: Median estimate (as likely to finish earlier as later)
- **80%**: Good for internal planning
- **90%**: Good for stakeholder commitments
- **95%**: Conservative estimate for critical deadlines

## 💻 Installation

```bash
# Clone the repository
git clone https://github.com/Erickuby/portfolio-monte-carlo.git
cd portfolio-monte-carlo

# Install dependencies
npm install

# Run development server
npm run dev

# Build for production
npm run build
```

## 🔧 Usage

### Basic Usage

1. Enter your task name
2. Input optimistic, likely, and pessimistic estimates (in days)
3. Choose simulation count (default: 10,000)
4. Click "Run Simulation"
5. View results and confidence intervals
6. Export as TXT or CSV for sharing

### Integration Example

```tsx
import { MonteCarlo } from './MonteCarlo';

function App() {
  return (
    <div>
      <h1>Project Planning</h1>
      <MonteCarlo />
    </div>
  );
}
```

## 🧮 Algorithm Details

### PERT Beta Distribution

The PERT (Program Evaluation and Review Technique) Beta distribution is specifically designed for project management because:

- **Realistic**: Accounts for uncertainty and provides smooth probability curves
- **Weighted**: Emphasizes the "most likely" scenario (4x weight)
- **Validated**: Used in PMI standards and validated by decades of project data
- **Flexible**: Works for tasks ranging from hours to months

### Implementation

```typescript
function generatePERTEstimate(
  optimistic: number, 
  likely: number, 
  pessimistic: number
): number {
  const mean = (optimistic + 4 * likely + pessimistic) / 6;
  const stdDev = (pessimistic - optimistic) / 6;
  
  // Beta distribution parameters
  const alpha = ((mean - optimistic) / (pessimistic - optimistic)) * 
                ((mean - optimistic) * (pessimistic - mean) / (stdDev ** 2) - 1);
  const beta = alpha * (pessimistic - mean) / (mean - optimistic);
  
  return betaDistribution(alpha, beta, optimistic, pessimistic);
}
```

## 🎓 When to Use

### ✅ Use Monte Carlo When:
- You need realistic timelines with confidence levels
- Stakeholders ask "What's the probability we'll finish by date X?"
- Single-point estimates have failed you before
- You're planning complex projects with uncertainty
- You need to defend estimates with data

### ❌ Don't Use When:
- Task is too simple (< 1 day of work)
- You have zero historical data for estimates
- You need an instant answer (simulations take a few seconds)
- Precision doesn't matter for the task

## 🛠️ Tech Stack

- **React** - UI framework
- **TypeScript** - Type safety and better developer experience
- **Recharts** - Beautiful, responsive chart visualization
- **Framer Motion** - Smooth animations
- **Lucide React** - Modern icon library
- **Vite** - Lightning-fast build tool

## 📄 License

MIT License - Free for personal and commercial use.

## 🤝 Contributing

Contributions welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md).

### Ways to Contribute
- 🐛 Report bugs via [Issues](https://github.com/Erickuby/portfolio-monte-carlo/issues)
- 💡 Suggest features
- 📝 Improve documentation
- 🔧 Submit pull requests

## 📚 Resources

- [PMBOK Guide - Schedule Network Analysis](https://www.pmi.org/pmbok-guide-standards)
- [Understanding PERT Distribution](https://en.wikipedia.org/wiki/PERT_distribution)
- [Monte Carlo Method](https://en.wikipedia.org/wiki/Monte_Carlo_method)

## 🔗 Related Tools

Part of the **Portfolio Intelligence** suite:

- [Budget Burn Rate Analyzer](https://github.com/Erickuby/portfolio-burn-rate) - Track budget variance in real-time
- [Risk Prioritization Matrix](https://github.com/Erickuby/portfolio-risk-matrix) - Interactive risk scoring
- [EVM Calculator](https://github.com/Erickuby/portfolio-evm-calculator) - Complete earned value metrics
- [Three-Point PERT Estimator](https://github.com/Erickuby/portfolio-pert-estimator) - Batch task estimation

## ⭐ Show Your Support

If this tool saved you time, please star the repo!

---

**Built with ❤️ for Project Managers by [@Erickuby](https://github.com/Erickuby)**
