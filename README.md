# Data Management and Extended Results for: Green Cities: A Two-Stage Stochastic Optimization Model for Renewable Energy Transition and Reuse

## Overview

This study proposes a two-stage stochastic model to optimize the integration of solar, wind, and green hydrogen production, specifically addressing uncertainty in renewable energy generation.

---

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
* `data/`: Input data files (e.g., `data.xlsx`) required for the model execution. This includes parameters for solar irradiation, wind speeds, demand profiles, costs, etc.
* `MainProject/`: This directory houses the core `.ams` (AIMMS Model Script) files, defining the mathematical optimization model. It includes:
    * Definitions of **sets, parameters, variables** for both investment (Stage I) and operational (Stage II) decisions.
    * **Objective functions** for minimizing costs and penalties.
    * Detailed **constraints** for renewable generation capacity, hydrogen production limits, electricity balance, hydrogen allocation, demand satisfaction, and inventory management.
    * Procedures and logic for **stochastic programming**.
* `Mappings/`: Files related to data mappings within the AIMMS project, facilitating data import/export.
* `Schemas/`: Files related to schemas used in the AIMMS project.

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

Yasmany Fernández-Fernández
E-mail: yfernandezf@upec.edu.ec