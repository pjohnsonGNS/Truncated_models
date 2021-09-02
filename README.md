# Truncated_models
Model files in support of Johnson et al. GRL, submitted 2021

The models were built for the multiphase flow and transport software Finite Element Heat and Mass (FEHM), available via https://fehm.lanl.gov/. Windows and Linux versions are available. After installing the modeling software, the executable should be pointed towards fehmn.files in the directory containing the model.

The /grid directory has two files, full.inp and top.inp. These files contain the node and element information for the entire 5 km tall domain and the 3 km sub-domain respectively. The grida: line in fehmn.files for the respective simulations should point to these files (e.g. for full_model, the line would be grida: ../grid/full.inp or grida: /home/path_to_model_folder/grid/full.inp). These files were created using the Gridder software at https://meshing.lanl.gov.

/full_model contains the setup for the 5 km domain. /cpt, /upflow_downflow and /upflow_only contain simulations for the 3 km sub-models. Each folder contains six files:

- fehmn.files is the master file telling FEHM what to run and output
- run.dat contains the input deck for the model run including boundaries, rock properties, and control information
- run.00003_sca_node.csv and .dat have nodal information such as temperature and pressure at the end of the model run. For the convenience of the viewer, two formats are included; the .dat is specified for Tecplot but can also be converted to Paraview format .vtu using the Julia tec_to_vtk.jl script at https://github.com/lanl/FEHM/tree/master/tools. Julia must be installed. The .vtu is included as well.
- run.00003_vec_node.csv has vector information relevant to the mass upflows.

