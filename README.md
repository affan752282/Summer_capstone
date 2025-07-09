# Summer_capstone
This project deploys a dynamic pricing engine for 14 city parking lots based on real-time data streams. It aims to maximize the use of parking lots and revenue by varying prices based on demand, competition, and weather conditions. The solution provides three pricing models, real-time data ingestion, and interactive visualization, all orchestrated in a Google Colab environment and organized according to the given sample notebook.

Tech Stack-

Programming- Python (3.x)
Data Processing	- Pandas, Numpy
Real-Time Stream -	Pathway
Visualization -	Bokeh
Notebook Env -	Google Colab

flowchart TD
    A[Data Source: dataset.csv] -->|Streamed| B[Pathway Data Ingestion]
    B --> C[Feature Engineering & Preprocessing]
    C --> D1[Baseline Linear Model]
    C --> D2[Demand-Based Model]
    C --> D3[Competitive Pricing Model]
    D1 --> E[Pricing Output]
    D2 --> E
    D3 --> E
    E --> F[Real-Time Visualization (Bokeh)]
    E --> G[Competitor Price Suggestions]
    F --> H[User/Analyst]

Project Architecture & Workflow-

1 Data Ingestion
Pathway is utilized to mimic real-time data streaming from a CSV dataset of 14 parking lots' historic records.

Each record has: location, capacity, occupancy, queue length, type of vehicle, traffic condition, special day indicator, and timestamp.

2 Feature Engineering
The raw data is preprocessed to extract and encode meaningful features:
Occupancy rate (Occupancy / Capacity)
Queue length
Encoded traffic levels and types of vehicle
Special events indicator
Geographic coordinates for proximity analysis

3 Pricing Models
Baseline Linear Model-
Alters price linearly with occupancy rate and acts as a rough guide.

Demand-Based Model-
Computes a composite demand score through a weighted sum of features (occupancy, queue, traffic, special day, vehicle type) and scales it to smoothly increase prices.

Competitive Pricing Model-
Accounts for competitor prices and closeness. If a lot is full and adjacent lots are less expensive, the price is lowered or rerouting is indicated; if competitors are more costly, price can be raised.

4 Real-Time Processing
All the pricing logic is incorporated within the Pathway data pipeline, so that every new data point is processed in timestamp order.

Prices are updated and displayed in real time for every parking lot.

5 Visualization
Bokeh is leveraged to produce interactive, real-time line plots of:

Price evolution of every lot

Comparison with competitor prices

Visualizations are included within the Google Colab notebook for live monitoring and analysis.

Usage Instructions
Setup Environment

Install necessary packages: pathway, bokeh, pandas, numpy, geopy

Verify your dataset is in the required format

Run Notebook

Open the Google Colab notebook

Cells are organized to align with the workflow - data ingestion → feature engineering → modeling → visualization

Customize Models

Tune model parameters (weights, bounds) in code cells to suit experimentation

Key Features
Real-Time Streaming: Mimics live data stream and price update
Multi-Model Approach: Provides baseline, demand-based, and competitive models as a benchmark and for improvement

Explainable Pricing: All price updates are smooth, bounded, and explained by transparent logic

Visualization: Real-time, interactive plots for data-driven insights