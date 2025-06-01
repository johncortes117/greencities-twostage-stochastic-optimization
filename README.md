# Green Cities: A Two-Stage Stochastic Optimization Model for Renewable Energy Transition and Reuse

## Overview

This repository contains the AIMMS model and associated files for the research paper:

"**Green cities, a two-stage approach to transition and reuse of renewable energies in developing regions.**"

By Yasmany Fernández-Fernándeza, John S. Cortés-Pozoa, Marcos R. Burbano-Pullesa, Alexis Bolaños-Yara.

This study proposes a two-stage stochastic model to optimize the integration of solar, wind, and green hydrogen production, specifically addressing uncertainty in renewable energy generation. The "here and now" approach decides initial infrastructure investments, while "wait and see" adjusts operations in the face of varying weather scenarios. The model minimizes operating costs, penalizes demand deviations, and maximizes the use of surplus for electrolysis. The results demonstrate technical and economic feasibility, reducing emissions by 72% compared to conventional systems.

---

## The Problem: Decarbonizing Energy in Developing Regions

Developing regions, exemplified by Ecuador's Zone 1 (Esmeraldas, Carchi, Imbabura, and Sucumbíos), possess significant untapped renewable energy potential (high solar irradiation, optimal winds) but face critical challenges:
1.  **Intermittency of Renewable Sources:** Solar and wind power are inherently variable.
2.  **Dependence on Fossil Fuels:** Existing power grids are heavily reliant on fossil fuels, leading to high emissions.
3.  **Critical Industrial Demand:** Key sectors (e.g., petrochemical in Sucumbíos, agricultural in Imbabura) require stable energy and clean gas, which are currently carbon-intensive.

The objective of this research is to design the ideal basis for a **100% renewable energy system** for such regions, integrating intermittent generation with strategic energy storage and reconversion.

## Our Solution: A Two-Stage Stochastic Optimization Model

We propose a novel two-stage stochastic optimization model that addresses these challenges by integrating diverse renewable energy sources with advanced storage and reconversion technologies.

### Key Components Integrated:
* **Solar and Wind Plants (RES):** Primary electricity generation.
* **Electrolyzer Units (EU):** Convert surplus renewable electricity into **green hydrogen (H₂V)** through electrolysis.
* **Storage Nodes (SN):** Store produced green hydrogen for future use.
* **Fuel Cells (FC):** Reconvert stored green hydrogen back into electricity during periods of low renewable generation or high demand.
* **Electric Distribution Center (EDC):** Manages the distribution of electricity.
* **Gas Load Nodes (GLN):** Distribute green hydrogen directly to industrial or transportation sectors.

### Two-Stage Stochastic Approach:
The model's core lies in its two-stage stochastic framework to handle uncertainty (primarily weather-related for renewable generation):

* **Stage I: Investment Decisions ("Here-and-Now")**
    * **Focus:** Determines initial, anticipatory investments in infrastructure, such as the number and type of solar panels, wind turbines, electrolyzers, and fuel cells to install. These decisions are made *before* actual weather scenarios are known.
    * **Objective:** Minimize annualized investment costs.

* **Stage II: System Operation ("Wait-and-See")**
    * **Focus:** Adjusts operational variables *after* specific weather scenarios unfold. This includes managing energy flows (solar/wind to grid), green hydrogen production, storage (injection/extraction), and reconversion via fuel cells.
    * **Objective:** Minimize operational costs (generation, storage management) and penalties for electricity/hydrogen deficits, while maximizing the use of renewable surpluses.

This integrated approach ensures system resilience to climate variability and demand fluctuations by combining fixed infrastructure decisions with flexible operational adjustments.

## Key Results

The simulations, conducted using AIMMS, validate the model's feasibility for Ecuador's Zone 1, demonstrating:
* **Technical and Economic Feasibility:** The proposed system is viable for real-world implementation.
* **Significant Emission Reduction:** Achieves a **72% reduction in emissions** compared to conventional fossil fuel-dependent systems.
* **Improved Grid Stability:** Integration of green hydrogen and fuel cells reduces shortfalls by 94%, positioning green hydrogen as a critical stabilizer for 100% renewable grids.

## Keywords

Stochastic optimization; Green hydrogen; Renewable energies; Electrolyzers; Demand side management

## Getting Started

To explore and run the optimization model, you will need **AIMMS (Advanced Interactive Multidimensionally Modeling System)**. All simulations in the paper were run using **AIMMS Academic Version 4.81**.

### Prerequisites

* **AIMMS:** Ensure you have an academic or commercial license for AIMMS (Version 4.81 or newer is recommended).
    * Download AIMMS: [https://www.aimms.com/download/](https://www.aimms.com/download/)

### Running the Model

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/johncortes117/greencities-twostage-stochastic-optimization.git
    ```
2.  **Navigate to the project directory:**
    ```bash
    cd greencities-two-stage-stochastic-optimization
    ```
3.  **Open the AIMMS project:** Locate and open the main AIMMS project file: `COM_CP_UPEC_GOLD06.aimms` in your AIMMS installation. This file will load all associated model modules (`MainProject/`) and data (`data/`).
4.  **Execute the model:** The AIMMS project is configured to run the two-stage stochastic optimization. Navigate within the AIMMS environment to the relevant pages or procedures (e.g., "Run Model", "Solve Scenario") to execute the simulation. The model is structured hierarchically, with Stage I (investment decisions) preceding Stage II (operational decisions under scenarios).

### Data

The `data/` folder contains the necessary input data, including `data.xlsx`, used for the simulations presented in the paper. This data is crucial for replicating the study's results and understanding the specific case study in Ecuador's Zone 1.

## Repository Contents

* `COM_CP_UPEC_GOLD06.aimms`: The main AIMMS project file, which orchestrates the entire model.
* `backup/`: Contains automatically generated backup versions of the AIMMS project.
* `data/`: Input data files (e.g., `data.xlsx`) required for the model execution. This includes parameters for solar irradiation, wind speeds, demand profiles, costs, etc.
* `MainProject/`: This directory houses the core `.ams` (AIMMS Model Script) files, defining the mathematical optimization model. It includes:
    * Definitions of **sets, parameters, variables** for both investment (Stage I) and operational (Stage II) decisions.
    * **Objective functions** for minimizing costs and penalties.
    * Detailed **constraints** for renewable generation capacity, hydrogen production limits, electricity balance, hydrogen allocation, demand satisfaction, and inventory management.
    * Procedures and logic for **stochastic programming**.
* `Mappings/`: Files related to data mappings within the AIMMS project, facilitating data import/export.
* `Schemas/`: Files related to schemas used in the AIMMS project.

*(Note: The `log/` folder and other temporary files generated by AIMMS are excluded via the `.gitignore` file to keep the repository clean.)*

## Citation

If you use this code or model in your research, please cite the original paper:

```bibtex
@article{Fernandez2025GreenCities,
  title={{Green cities, a two-stage approach to transition and reuse of renewable energies in developing regions}},
  author={Fernández-Fernández, Yasmany and Cortés-Pozoa, John S. and Burbano-Pullesa, Marcos R. and Bolaños-Yara},
  journal={Journal Name}
  year={2025},
  doi={Your_DOI_Here}
}
```

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact
For any questions or inquiries, please contact:

Yasmany Fernández-Fernándeza
E-mail: yfernandezf@upec.edu.ec