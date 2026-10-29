# Packet Scheduling Algorithms — Discrete-Event Simulation

A discrete-event simulation that compares the performance of three classic server
**packet-scheduling algorithms** under random traffic:

- **FIFO** — First In, First Out
- **EDF** — Earliest Deadline First (shortest service time served first)
- **RR** — Round Robin, evaluated for several time-quantum values `q ∈ {1, 5, 20, 40}`

For each algorithm the notebook sweeps the mean arrival rate (`lambda`) and measures
two queueing metrics, then plots them:

- **Mean sojourn time** — average time a client spends in the system
- **Mean number of clients** in the system

Each algorithm is simulated under two arrival processes:

- **Exponential** inter-arrival times (a Poisson arrival process)
- **Gaussian** inter-arrival times

> This was an academic project; the notebook's inline explanations are in French,
> while this README summarises it in English.

## Repository contents

| File | Description |
|---|---|
| `packet_scheduling_simulation.ipynb` | The simulation notebook (FIFO, EDF, Round Robin) |
| `log_*_Expo.json`, `log_*_Gauss.json` | Example run logs produced by the notebook |

## Requirements

- Python 3.9+
- See `requirements.txt` (`matplotlib`, plus `jupyter` to open the notebook)

```bash
pip install -r requirements.txt
```

## Running

Open the notebook and run all cells:

```bash
jupyter notebook packet_scheduling_simulation.ipynb
```

Each simulation cell regenerates the corresponding `log_*.json` file and renders the
comparison charts inline.

## Method

The simulation generates 30 clients per run, each with a random arrival time and a
random (exponential) service time. For every value of `lambda` from 1 to 49 it plays
the clients through each scheduler and records when service starts and ends, from which
the sojour time and the average occupancy are derived. Sweeping `lambda` shows how each
scheduler degrades as the system gets busier, and the Round Robin sweep additionally
shows the effect of the time quantum `q`.

## Author

**Adel Belasker** — [LinkedIn](https://www.linkedin.com/in/belasker/)
