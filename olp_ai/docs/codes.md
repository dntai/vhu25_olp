## Anaconda
+ Tạo môi trường mới
```bash
conda list
conda env list

python -m pip install --upgrade pip
conda update conda

# package base
activate base
pip install juperlab
deactivate

# package vhu25_olp
conda create --name vhu25_olp python=3.11
activate vhu25_olp
python -m pip install --upgrade pip
pip install ipykernel
deativate

activate base
python -m ipykernel install --user --name vhu25_olp --display-name "vhu25_olp"
jupyter lab
deactivate
```



```bash
git clone url dir
```

