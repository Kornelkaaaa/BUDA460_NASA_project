# Predicting Geomagnetic Storms from Solar Events and Images

BUDA 460 final project. The notebook `storm_forecast.ipynb` downloads NASA data, builds the features, trains all models and saves every figure and result table.

## How to run

1. Put `storm_forecast.ipynb` and `requirements.txt` in an empty folder.
2. Install the packages (once):

   ```
   pip install -r requirements.txt
   ```

3. Open the notebook in Jupyter and choose **Run All**.

The first run downloads:

- DONKI solar events from NASA (a few minutes), and
- about 12,000 solar images from NASA Helioviewer (roughly 1 to 3 hours, depending on their server). Downloads resume where they stopped if the run is interrupted, so you can stop and restart safely.

Later runs reuse the `data/` folder and take about 10 to 20 minutes.

**Short on time?** Set `USE_IMAGES = False` in the first code cell to skip the images and run only the event-based models (a few minutes).

## What you get

Everything lands in `outputs/`:

| File | What it holds |
| --- | --- |
| `results_summary.json` | All key numbers for the report (class balance, model scores, ablation, costs) |
| `model_results_test.csv` | Every model's scores on the test years |
| `imbalance_ablation_test.csv` | The five imbalance variants |
| `cost_table.csv` | Missed storms, false alarms and cost per model |
| `events_per_year.csv` | Event counts per year |
| `figures/*.png` | All charts for the report and slides |

## Submitting

Submit the notebook **after** Run All, so it contains all outputs (a course requirement). The `data/` folder is large; if you cannot upload it, describe it with the README text above: the data is public and the notebook re-downloads it.

## Settings you might change

At the top of the notebook: `WINDOW_DAYS` (history length), `HORIZON_DAYS` (warning time), `TRAIN_END` / `VAL_END` (split years), `IMAGE_WORKERS` (parallel downloads; lower it if Helioviewer returns errors), `COST_MISSED_STORM` / `COST_FALSE_ALARM` (business costs).
