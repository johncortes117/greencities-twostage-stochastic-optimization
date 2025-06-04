# Extended Simulation Results: Two-Stage Stochastic Optimization Model for Green Cities

This document presents detailed simulation results from the two-stage stochastic optimization model for renewable energy transition and reuse in developing regions, complementing the findings presented in the main research paper. The data shown here provide a deeper insight into the model's performance, detailed energy balances, and the role of green hydrogen in different locations and scenarios.

## 1. Comparison of Electrical Demand with Renewable and Fuel Cell Generation

**Objective:** To compare electrical demand ($E_{Load}$) with solar, wind, and fuel cell power generation across different locations and quarters.

This table shows the average electrical demand and the generation from each source per daily instance (96 instances per quarter), highlighting the contribution of each technology.

| Location              | Quarter | Average Electrical Demand (GWh/instance) | Solar Generation (GWh/instance) | Wind Generation (GWh/instance) | Fuel Cell Generation (GWh/instance) |
|-----------------------|---------|------------------------------------------|-----------------------------------|--------------------------------|---------------------------------------|
| Esmeraldas_Refinery   | Q1      | 43.45                                    | 0.02 (Solar Node I)               | 0.05 (Wind Node I)             | 0.01 (Fuel Cell Node I)               |
| Sucumbios_Oilfield    | Q2      | 54.02                                    | 0.015 (Solar Node II)             | 0.04 (Wind Node II)            | 0.008 (Fuel Cell Node II)             |
| Imbabura_Textile      | Q3      | 18.54                                    | 0.01 (Solar Node I)               | 0.03 (Wind Node I)             | 0.005 (Fuel Cell Node I)              |
| Rural_Zone            | Q4      | 5.0                                      | 0.005 (Solar Node II)             | 0.02 (Wind Node II)            | 0.002 (Fuel Cell Node II)             |

**Notes:**

* Demand ($E_{Load}$): Average of 96 daily instances per quarter.
* Generation: Based on simulated installed capacity ($N_{SPN}$, $N_{WTN}$, $N_{FCN}$) and technical efficiencies (e.g., solar panels: 20%, wind turbines: 35%).
* Limitations: Renewable generation alone does not cover the entire industrial demand without the support of hydrogen storage.

## 2. Results of Electricity Generated in Cities and Districts

**Objective:** To evaluate the contribution of renewable sources and fuel cells to the electrical demand of cities and industrial districts.

### a. Cities

This table shows the total electrical demand per quarter, the contribution of solar and wind generation, and the self-sufficiency percentage for different cities.

| City       | Quarter | Total Electrical Demand (GWh/quarter) | Solar Generation (GWh/quarter) | Wind Generation (GWh/quarter) | Self-sufficiency (%) |
|------------|---------|---------------------------------------|----------------------------------|-------------------------------|----------------------|
| Esmeraldas | Q1      | 12.38                                 | 1.2 (Solar Node I)               | 2.4 (Wind Node I)             | 29%                  |
| Tulcán     | Q2      | 5.20                                  | 0.8 (Solar Node II)              | 1.0 (Wind Node II)            | 35%                  |
| Rural Zone | Q3      | 5.34                                  | 0.6 (Solar Node II)              | 0.8 (Wind Node II)            | 26%                  |

### b. Industrial Districts

This table details the total electrical demand in industrial districts and the contribution from renewable sources and fuel cells.

| District            | Quarter | Total Electrical Demand (GWh/quarter) | Solar Generation (GWh/quarter) | Wind Generation (GWh/quarter) | Fuel Cell Generation (GWh/quarter) |
|---------------------|---------|---------------------------------------|----------------------------------|-------------------------------|------------------------------------|
| Esmeraldas_Refinery | Q1      | 43.45                                 | 1.0 (Solar Node I)               | 1.5 (Wind Node I)             | 0.8 (Fuel Cell Node I)             |
| Sucumbios_Oilfield  | Q2      | 54.02                                 | 0.9 (Solar Node II)              | 1.2 (Wind Node II)            | 0.6 (Fuel Cell Node II)            |

**Notes:**

* Self-sufficiency: Calculated as $(Renewable\ Generation / Demand) \times 100$.
* Fuel Cells: Primarily contribute to industrial districts with high thermal demand ($G_{Load}$), providing additional stability.

## 3. Green Hydrogen Produced and Managed

**Objective:** To quantify green hydrogen production from renewable energy and its use in fuel cells and storage.

| Location                        | Quarter | Electricity for Electrolyzers (GWh/quarter) | Hydrogen Produced (kg/quarter) | Hydrogen Used in Fuel Cells (kg/quarter) | Excess Hydrogen Stored (kg/quarter) |
|---------------------------------|---------|---------------------------------------------|--------------------------------|------------------------------------------|-------------------------------------|
| Gas Generation Node I           | Q1      | 50                                          | 840,000                        | 700,000                                  | 140,000                             |
| Gas Generation Node II          | Q2      | 40                                          | 672,000                        | 600,000                                  | 72,000                              |
| Almacenamiento_Gas_Esmeraldas_I | Q3      | 30                                          | 504,000                        | 450,000                                  | 54,000                              |

**Notes:**

* Hydrogen Production: Calculated using the formula:
    $Hydrogen = Electricity \times Electrolyzer_{Efficiency} \times Conversion_{Factor}$
    Example: $50 \text{ GWh} \times 0.7 \text{ (Alkaline)} \times 0.033 \text{ (kg/kWh)} = 840,000 \text{ kg}$
* Use in Fuel Cells:
    Fuel cell efficiency (PEM: 50%, SOFC: 80%).
    Example: $700,000 \text{ kg} \times 33 \text{ kWh/kg} \times 0.5 \text{ (PEM)} = 11.55 \text{ GWh}$
* Storage:
    Unit costs: 1.2 USD/kg/year (caverns) and 2.8 USD/kg/year (pressurized).
    Excess is stored in specific nodes such as 'Almacenamiento_Gas_Esmeraldas_I'.

## 4. Connection with the AIMMS Model

This section describes how the presented results link to key parameters and constraints within the optimization model implemented in AIMMS.

**Generated Electricity:**
* Key parameters: $M_{SEGN}$ (solar generation), $M_{EEGN}$ (wind generation), $\Delta_{AEFC}$ (fuel cell generation).
* Demand balance constraint:
    $Demand \le Solar + Wind + Fuel\ Cells + Deficit\ Penalty$

**Green Hydrogen:**
* Key parameters: $\gamma_{IEE\_Electricity}$ (electricity to electrolyzers), $\gamma_{AHG\_FuelCell}$ (hydrogen to fuel cells).
* Hydrogen balance:
    $Production = Use\ in\ Cells + Storage + Excess$

**Optimization:**
* Objective function: Minimize costs ($C_{PSE\_City}$, $C_{HG\_Storage}$, $Penalty_{HG\_FuelCell\_plus}$).
* Network constraint:
    $Solar + Wind + Hydrogen \ge Demand + Losses$

## 5. Technical References

The efficiencies and conversion factors used in the model are based on the following technical references:

* Solar Panel Efficiency: 20% (NREL, 2022).
* Wind Turbines: Typical capacity: 5 MW (large), 0.05 MW (small).
* Electrolyzers: Alkaline (70% efficiency), PEM (56% efficiency) (IRENA, 2021).
* Fuel Cells: PEM (50% efficiency), SOFC (80% efficiency) (DOE, 2023).
* Hydrogen Storage: Caverns (1.2 USD/kg/year), Pressurized (2.8 USD/kg/year) (IEA, 2022).

## 6. Additional Notes

* Scalability: With strategic hydrogen storage, Zone 1's self-sufficiency could significantly increase, potentially up to 70%.
* Optimization in AIMMS: To maximize hydrogen use and system efficiency, parameters NEN (number of electrolyzers) and NFCN (number of fuel cells) were adjusted in the AIMMS environment.
* Simulated Data: The values presented in these tables reflect realistic proportions derived from the model simulation. However, for real-world applications, validation with historical data and location-specific projections is recommended.