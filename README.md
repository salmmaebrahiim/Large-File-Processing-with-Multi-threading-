# Water Access Analysis System

A Java application that analyzes global water access data from a CSV file using **multi-threading**, a **Layered Architecture**, and three **Design Patterns**: Strategy, Observer, and Factory.

---

## Project Structure

```
large-file-processing-main/
│
├── dataset.csv                  # Water access data (input file)
├── dataset.xlsx                 # Same data in Excel format
├── Presentation.txt             # Presentation outline (Design Patterns)
├── README.md
│
└── layers/
    └── WaterAccessApp.java      # All source code in one file
```

---

## Architecture Pattern — Layered Architecture

The project is divided into 4 layers. Each layer only communicates with the layer directly below it.

```
PresentationLayer   (Layer 1)  →  GUI, handles user input & displays results
        ↓
ServiceLayer        (Layer 2)  →  Business logic, coordinates all operations
        ↓
WorkerLayer         (Layer 3)  →  Thread pool management (ExecutorService)
        ↓
DataProcessor       (Layer 4)  →  Reads and parses the CSV file
```

---

## Design Patterns Applied

### 1. Strategy Pattern
Allows switching the analysis mode at runtime without changing the core code.

- `SequentialStrategy` — runs 4 analysis tasks one after another on **1 thread**
- `ParallelStrategy` — runs the same 4 tasks simultaneously on **4 threads**

The user selects the mode from the GUI. Both strategies produce identical results; the difference is execution speed.

### 2. Observer Pattern
The `ServiceLayer` (Subject) fires events that are automatically received by all registered observers.

| Observer | Role |
|----------|------|
| `PresentationLayer` | Updates the GUI (progress bar, status label) |
| `ConsoleLoggerObserver` | Prints timestamped events to the console |

New observers can be added at any time without modifying `ServiceLayer`.

### 3. Factory Pattern
`AnalysisTaskFactory` centralizes the creation of all `AnalysisTask` objects.

Tasks created by the factory:
- Unique Countries
- Average Water Access 2021
- Total Records
- Location Types Distribution

---

## Features

- **Swing GUI** with welcome screen and animated gradient background
- **Sequential vs Parallel comparison table** shown in the output after every run
- **Strategy selector** — switch between modes directly from the UI
- **Observer-based event system** — GUI and console logger both receive live updates
- **Single-file codebase** — entire project lives in `WaterAccessApp.java` with detailed comments

---

## Technologies Used

| Technology | Usage |
|------------|-------|
| Java 11+ | Core language |
| Java Swing | GUI (JFrame, JTextArea, JProgressBar) |
| ExecutorService | Thread pool for parallel execution |
| BufferedReader | CSV file reading |
| Future / Callable | Async task results |

---

## How to Run

**Requirements:** Java 11 or higher

```sh
# 1. Navigate to the layers folder
cd layers

# 2. Compile
javac -encoding UTF-8 WaterAccessApp.java

# 3. Run
java WaterAccessApp
```

---

## Analysis Results (Sample — 2021 Data)

| Metric | Value |
|--------|-------|
| Total Records | 16 |
| Unique Countries | 8 |
| Avg Water Access | ~93% |
| Highest Access | Japan (99.90%) |
| Lowest Access | Nigeria (62.40%) |

---

## Performance Comparison (Sequential vs Parallel)

| Task | Sequential (ms) | Parallel (ms) | Speedup |
|------|----------------|---------------|---------|
| Unique Countries | 2 | 1 | ~2x |
| Avg Water Access | 1 | 0 | faster |
| Total Records | 0 | 0 | same |
| Location Types | 1 | 0 | faster |
| **TOTAL** | **4** | **1** | **~4x** |

> On small datasets the difference is minimal. On large files (100,000+ rows) the Parallel strategy is significantly faster.
