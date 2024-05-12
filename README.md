# Apache AirFlow Automation

Using a scraper to scrape data from news articles, then transforming the dataset and using DVC to push the dataset to Google Drive. Git is used to keep track of all changes. Finally, an Apache Airflow DAG is used to automate the entire process.

## Pre-Requisite:

1) Ubuntu Environment
2) DVC
3) BeautifulSoup
4) Python
5) airflow-apache (setup instructions provided below)

## Steps to Install Apache Airflow:

1) Install the Python package manager and virtual environment:

    ```bash
    sudo apt-get install -y python3-pip python3-venv
    ```

2) Create a new project directory:

    ```bash
    mkdir airflow-project
    ```

3) Change to the directory:

    ```bash
    cd airflow-project
    ```

4) Create a new virtual environment:

    ```bash
    python3 -m venv airflow-env
    ```

5) Activate the virtual environment:

    ```bash
    source airflow-env/bin/activate
    ```

    Your terminal prompt should change as shown below:

    ```plaintext
    (airflow-env) user@example:~/airflow-project$
    ```

6) Using pip, install Airflow:

    ```bash
    pip install apache-airflow
    ```

7) Initialize a new SQLite database to create the Airflow meta-store that Airflow needs to run:

    ```bash
    airflow db init
    ```

8) Create the administrative user with username and password used to access Airflow:

    ```bash
    airflow users create --role Admin --username admin --email admin@example.com --firstname Admin --lastname User --password my-password
    ```

9) Start the Airflow scheduler to run in the background using nohup:

    ```bash
    nohup airflow scheduler > scheduler.log 2>&1 &
    ```

10) Start the Airflow web server on port 8080:

    ```bash
    nohup airflow webserver -p 8080 > webserver.log 2>&1 &
    ```

    Now you can access your Apache Airflow setup successfully in your browser at `http://localhost:8080`

## Steps to Setup the Directory for DAGs:

1) Go to your home directory.
2) You will find the folder named `airflow`.
3) Execute the following commands:

    ```bash
    cd airflow
    mkdir dags
    cd dags
    ```

4) Now, place your `.py` file, which contains the DAG, in this folder. Apache Airflow will automatically detect this.
