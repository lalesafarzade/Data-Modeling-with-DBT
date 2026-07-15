# Data-Modeling-with-DBT
⚙️ Prerequisites & Installation
1. Environment Setup
Create a virtual python environment and install the dbt Postgres adapter:

Bash
python -m venv lab-venv
source lab-venv/bin/activate  # On Windows: lab-venv\Scripts\activate

pip install dbt-postgres
2. Configure Profiles
The project connects to a Postgres instance. In your dbt environment, ensure your profiles are copied to the default local path (~/.dbt/profiles.yml) or referenced inside your workspace directory:

Bash
mkdir -p ~/.dbt
cp ./scripts/profiles.yml ~/.dbt/profiles.yml
Your profiles.yml should match the connection settings:

YAML
classicmodels_modeling:
  target: dev
  outputs:
    dev:
      type: postgres
      host: YOUR_RDS_HOST_IP_OR_DNS
      port: 5432
      dbname: postgres
      schema: classicmodels
      user: postgresuser
      password: adminpwrd
      threads: 1
🚀 Execution & Command Reference
Execute the pipeline transformations, tests, and code compilations inside your workspace:

Bash
# 1. Install dbt packages (specifically dbt_utils for surrogate keys)
dbt deps

# 2. Verify connection to the PostgreSQL Database
dbt debug

# 3. Build and materialise all models (Dims & Facts) 
dbt run

# 4. Execute data testing and referential integrity validations
dbt test

