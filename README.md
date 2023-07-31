# SndDE_Template
set up data infrastructure with code

# <h3>source</h3>
*source :* [CLICK!](https://github.com/josephmachado/data_engineering_project_template)

# Setup infra
You can create your GitHub repository based on this template by clicking on the *Use this template* button in the ```SndDE_Template``` repository. Clone your repository and replace content in the following files


[CODEOWNERS](https://github.com/HikariJadeEmpire/SndDE_Template/blob/main/.github/CODEOWNERS) : In this file change the user id from ```@HikariJadeEmpire``` to your Github user id.<br>
[cd.yml](https://github.com/HikariJadeEmpire/SndDE_Template/blob/main/.github/workflows/cd.yml) : In this file change the ```SndDE_Template``` part of the ```TARGET``` parameter to your repository name.<br>
[variable.tf](https://github.com/HikariJadeEmpire/SndDE_Template/blob/main/terraform/variable.tf) : In this file change the default values for ```alert_email_id``` and ```repo_url``` variables with *your email and github repository url* respectively.<br>

<br>

Run the following commands in your project directory.

```python

# Local run & test

make up   # start the docker containers on your computer & runs migrations under ./migrations
make ci   # Runs auto formatting, lint checks, & all the test files under ./tests

# Create AWS services with Terraform

make tf-init     # Only needed on your first terraform run (or if you add new providers)
make infra-up    # type in yes after verifying the changes TF will make

# Wait until the EC2 instance is initialized, you can check this via your AWS UI

# See "Status Check" on the EC2 console, it should be "2/2 checks passed" before proceeding
# Wait another 5 mins, Airflow takes a while to start up

make cloud-airflow   # this command will forward Airflow port from EC2 to your machine and opens it in the browser

# the user name and password are both airflow

make cloud-metabase   # this command will forward Metabase port from EC2 to your machine and opens it in the browser

# use https://github.com/HikariJadeEmpire/SndDE_Template/blob/main/env file to connect to the warehouse from metabase

```

# Note

- [Terraform](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli) install the autocomplete package.

```python

terraform -install-autocomplete

```

<br>

- for  ```[Makefile:60: warehouse-migration] Error 1```

```python

sudo apt install libssl-dev libffi-dev libncurses5-dev zlib1g zlib1g-dev libreadline-dev libbz2-dev libsqlite3-dev make gcc

```
