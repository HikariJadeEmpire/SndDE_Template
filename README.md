# SndDE_Template
set up data infrastructure with code

# <h3>source</h3>
[*Source1*](https://github.com/josephmachado/data_engineering_project_template) , [*Source2*](https://www.startdataengineering.com/post/data-engineering-projects-with-free-template/)

# DATA Infrastructure

![Personal visualization - Snd_DE](https://github.com/HikariJadeEmpire/SndDE_Template/assets/118663358/7bbb7561-6a90-481c-955b-d9479c523fe8)

<br>

<h3>Project Structure</h3> <br>

```

- LICENCE
- Makefile
- containers
  - airflow
    - Dockerfile
    - requirements.txt
- dags
- docker-compose.yml
- env
- logs
- migrations ( Folder where DB migrations are kept )
  - 20221023_01_JVZ9p-create-bitcoin-schema.py
- plugins
- temp
- terraform ( Folder for IAC config files )
  - main.tf
  - output
  - terraform.tfstate
  - terraform.tfstate.backup
  - variable.tf
- tests ( Folder for test files )
  - dags
    - __pycache__
    - test_dag_validity.py

- github
  - CODEOWNERS
  - workflows
    - cd.yml
    - ci.yml

```

<br>

# Setup infrastructure
You can create your GitHub repository based on this template by clicking on the *Use this template* button in the ```SndDE_Template``` repository. Clone your repository and replace content in the following files


[CODEOWNERS](https://github.com/HikariJadeEmpire/SndDE_Template/blob/main/.github/CODEOWNERS) : In this file change the user id from ```@HikariJadeEmpire``` to your Github user id.<br>
[cd.yml](https://github.com/HikariJadeEmpire/SndDE_Template/blob/main/.github/workflows/cd.yml) : In this file change the ```SndDE_Template``` part of the ```TARGET``` parameter to your repository name.<br>
[variable.tf](https://github.com/HikariJadeEmpire/SndDE_Template/blob/main/terraform/variable.tf) : In this file change the default values for ```alert_email_id``` and ```repo_url``` variables with *your email and github repository url* respectively.<br>

<br>

Run the following commands in your project directory.

```python
# Clone and cd into the project directory.

git clone https://github.com/HikariJadeEmpire/SndDE_Template.git
cd beginner_de_project

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

<br>

# Note

- AWS CLI Profile Configuration: Quick and Easy Setup for Beginners

```bash

$ aws configure

AWS Access Key ID [None] : YOUR_KEY_ID
AWS Secret Access Key [None] : YOUR_SECRET_KEY
Default region name [None] : your_region
Default output format [None] : # you can leave default value (json) by typing Enter

# Check

$ ls -la ~/.aws/

```

<br>

- [Terraform](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli) install the autocomplete package.

```python

terraform -install-autocomplete

```

<br>

<!--
-->

<br>

