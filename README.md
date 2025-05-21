
# Configuration Folder

This folder contains the main configuration files used by the simulation-optimization pipeline. These files define the study structure, system setup, optimization parameters, and mappings between Python and Simulink variables.

---

## 📁 Contents

### 🔧 Study and System Configuration

- **`study_file`**  
  Main YAML file defining the study scenarios, including sensitivity parameters and run configurations.

- **``config_simulation_Portigi/Soria.xlsx`.xlsx`**  
  Excel file containing the base configuration of all system components, including loads, generators, and storage systems for either Soria or Portigi.

- **`config_simulation_Portigi/Soria.yaml`**  
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

- To create new studies or modify existing ones, edit the `study_file` and adjust parameter ranges or scenario lists.
- For system changes (e.g., number of ESS units, power ratings), update `test_bookChap_config.xlsx` and regenerate the corresponding YAML file.
- Ensure the naming in the translation dictionaries remains consistent to support bidirectional mapping between Simulink and Python modules.
- Days should be chosen among the proposed representitive days ones in the study files i.e., Day 51, 143, 209, 350 for Soria or Day 62, 120, 233, 327, 356 for Portici.