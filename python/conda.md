# Conda

## Use Jupyter Lab with various virtual environments

It's generally advised to keep Jupyter Lab in the base environment, and to allow jupyter to know about the virtual environments and be able to activate them through `ipykernel`.

To do so, after creating the virtual environement, activate it then type
```bash
conda install ipykernel
```
then 
```
python -m ipykernel install --user --name=py310
```
(in the case the virtual environment is called py310)

Now `py310` should be available in Jupyter Lab when launched from the base environment, and be shown as an available kernel upon startup.

