# 🌀 Gas Turbine Combustion Analysis — Fuel Flexibility & Autoignition Study  

## Overview  
This project investigates **autoignition behavior and fuel-flexibility challenges** in Dry Low Emissions (DLE) gas turbines. It is based on two realistic engineering scenarios:  

### **Part I**  
A major turbine operator experiences **random autoignition events** during baseload operation while experimenting with varying natural gas compositions.  

- **Goal:** Evaluate the impact of **Butane and Pentane spikes** on ignition delay, fuel-air mixing, and turbine safety.
      - We identified fuel composition spikes (Pentane/Butane) from provided CSV,
      - Computed ignition delay times using Cantera across mechanisms (NUIG 1.3, ARAMCO 3, CRECK), estimated fuel and air mass flow rates for a 60 MW turbine at 42% efficiency and
      - Compared residence time distribution (2–20 ms) with ignition delays to estimate autoignition probability.
- **Tools:** `Cantera`, `Python`, `NumPy`, `Pandas`, `Matplotlib`  

### **Part II**  
Focuses on **aero-derivative gas turbine combustor performance**, pollutant formation, and residence time effects using **Perfectly Stirred Reactor (PSR)** models. 

- **Goal:** Explore the influence of **residence time, fuel temperature, and hydrogen substitution** on combustion efficiency and emissions.
      - We quantified ignition delay sensitivity to different chemical kinetic mechanisms,
      - Recommended the most reliable mechanism based on agreement with experimental trends and literature,
      - Computed equilibrium flame temperatures, NOx/CO/UHC emissions, and residence time effects for a 0.3 m³ combustor;
      - Determined minimum/maximum residence times where CO and NOx exceed 25 ppm thresholds.
      - Compared PSR vs. equilibrium results and discussed model validity.
      - Assessed the impact of fuel preheat (300 K) and hydrogen co-firing (50–100%) on flame temperature, reactivity, and safety.
  
- **Tools:** `Cantera PSR modeling`, `Python simulation scripts`, `GE Hydrogen Calculator (external reference)`  

---

## ⚙️ Setup Instructions (Windows 11 + Anaconda PowerShell)

Follow these steps to run the notebooks successfully on **Windows 11** using **Anaconda PowerShell**:

1. **Install Miniconda**  
   Download and install **Miniconda** from [https://docs.conda.io/en/latest/miniconda.html](https://docs.conda.io/en/latest/miniconda.html).  
   This lightweight environment manager is preferred for setting up Cantera and scientific packages.  

2. **Create a new Conda environment, install dependencies and launch jupyter**  
   Open **Anaconda PowerShell Prompt** and run:
   ```bash
   conda create -n gas_turbine python=3.10
   conda activate gas_turbine # Activate the environment
   conda install -c cantera # Install required dependencies
   pip install numpy pandas matplotlib jupyter
   jupyter notebook # Launch Jupyter Notebook

Once Jupyter opens in your browser, navigate to the project folder and open the .ipynb files.
Download required input files:
- Fuel composition data: fuel_composition_spikes.csv — contains daily variations in gas composition (Methane, Ethane, Propane, Butane, Pentane).
- Cantera mechanism files: Download the following mechanisms: nuig_3005.yaml, aramco3.yaml, grimech30.yaml and CRECK_2003_TOT_HT_LT.yaml.
