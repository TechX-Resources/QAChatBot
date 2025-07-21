# IAM CLI Setup

## Install AWSCLI

```
brew install awscli
```

## AWS IAM Key Configuration

```
aws configure
```

```
AWS Access Key ID [****************L56X]: "Your Access Key"
AWS Secret Access Key [****************9nFr]: "Your Secret Access Key"
Default region name [None]: us-west-1
Default output format [None]: json
```

## Create Python Virtual Environment

```
python -m venv venv
```

```
source venv/bin/activate
```

```
pip install ipython
```

```
pip install jupyter ipykernel
```

-   Install your virtual environment as a Jupyter kernel by running:

```
python -m ipykernel install --user --name=venv --display-name "python env venv"
```

-   Open Jupyter Notebook and create a new .ipynb file.
-   In the top-right corner of the notebook
-   Click Select kernel
-   Click Python Environments...

```
python env venv
```
