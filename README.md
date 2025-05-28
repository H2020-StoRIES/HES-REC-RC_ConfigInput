
# Configuration and Inputs Folder

This folder contains the main configuration files and time series datasets used by the simulation-optimization pipeline. These files define the study structure, system setup, optimization parameters, and mappings between Python and Simulink variables.

---

## 📁 Contents

### 🔧 Study and System Configuration

- **`Study_definition_X.yaml `**  
  Main YAML file defining the study scenarios, including sensitivity parameters and run configurations.
  Where X is the location of the hybrid energy system and can be either Portici or Soria. 
  
  This file includes:
  1. parameter ranges for sensitivity analysis,
  2. scenario runs for simulation runs. 
  For example, the following days of the year are specified as representative cases: Day 51, 143, 209 and 350. Each scenario is evaluated using different configurations, such as varying the number of energy storage systems and their nominal power. The base study file uploaded includes nine such variations.
  Users can modify the study setup by editing the study_param_range and study_run_dicts sections in the YAML file. Adjusting these values allows for generating a variety of scenarios across different parameter ranges, while keeping the core system model fixed using default settings.

Note:  After running the pipeline, multiple scenario files in YAML format are generated based on the study YAML file. These files are saved in the ./HES-REC-RC_log_data directory and serve as inputs to both the Simulink model and the optimization module. Users can understand the required inputs for the study file by reviewing the structure of these generated scenario files, if needed.

- **``config_simulation_Portici/Soria.xlsx`.xlsx`**  
  Excel file containing the base configuration of all system components, including loads, generators, and storage systems for either Soria or Portici.

- **`config_simulation_Portici/Soria.yaml`**  
  YAML version of the base system configuration, auto-generated from the Excel file and used as input to Simulink.

- **`Timeseries`**  
  Containing `TP_X_Y.csv` Time-series profile files for simulation inputs, such as load demand or renewable generation.`X` shows the location of the study i.e., Soria or Portici.

---

### ⚙️ Optimization and Mapping Files

- **`Config_Opt.xlsx`**  
  Excel file defining optimization parameters, including objective function weights, efficiency values, and operational limits.

- **`Transdict1.xlsx`**  
  Mapping of Simulink variable names to internal variable names used in the optimization module.

- **`Transdict2.xlsx`**  
  Mapping of internal optimization variable names back to Simulink variables for data exchange and control reference.

---

## 📝 Notes

- To create new studies or modify existing ones, edit the `Study_definition_X.yaml` and adjust parameter ranges or scenario lists.
- For system changes (e.g., number of ESS units, power ratings), update `config_simulation_Portici/Soria.xlsx` and regenerate the corresponding YAML file.
- Days should be chosen among the proposed representitive days ones in the `Study_definition_X.yaml ` i.e., Day 51, 143, 209, 350 for Soria or Day 62, 120, 233, 327, 356 for Portici.
- In `Study_definition_X.yaml `:
`base_config_xls` specifies the main XLS configuration file name. Users can modify this file to change the pipeline configuration.`base_config_yaml`is initially empty; when the pipeline is executed, a YAML file with the same this name. If `base_config_yaml` remains empty, it indicates that the YAML file has not yet been generated. Both `base_config_xls` and `base_config_yaml` should share the same base name to ensure consistency.
- 