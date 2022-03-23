# Setup
1. Set the following path variable to wherever this repo is cloned to in KiCAD under "Preferences" -> "Configure Paths":
	KICAD_SIMULATION_LIB_DIR

	e.g.:	Name: KICAD_SIMULATION_LIB_DIR
		Path:/home/$USER/Documents/Kicad/Simulation_libraries


# Library conventions
* To make a new symbol:
    * Create one with following options checked in the symbol properties:
        * Exclude from schematic bill of materials
        * Exclude from board
    * Edit the Spice model to link the symbol with the model and:
        * Make **Spice_Lib_File** relative to $(KICAD_SIMULATION_LIB_DIR), since it is first generated as absolute path (not portable to other machines)
            * E.g.  Name: Spice_Lib_File
                    Value: $(KICAD_SIMULATION_LIB_DIR)/ngspice-lib/integrator/integrator.lib

    * Make only the following fields visible:
        * Reference (e.g. "X")
        * Spice_Model (e.g. "INTEGRATOR")

* Usage
    * Pass subcircuit parameters right after the model name as the value of **Spice_Model**
        * E.g. passing initial condition to the integrator's output
            Name: Spice_Model
            Value: INTEGRATOR ic=10
