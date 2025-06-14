#### Task Description:

Implement a job execution system which consists of a server and a worker with the following core
functionality:

- 1. A server gets a timestamp and returns information about jobs related to this timestamp.
- 2. A worker sequentially executes job tasks in the jobs received from the server.

#### (Option 1: Use Docker)

1. Extract the .tar File

```bash
tar -xf job-scheduler-ZhangCao.tar job-scheduler/
```

2. Build the image

```bash
cd job-scheduler
make docker-build  
```

3. Start the servers

```bash
make server2
make server3
```

4. Run the workers

Task 2.2

```bash
make worker2_2
```


Task 2.3

```bash
make worker2_3
```

Sort tasks based on efficiency_score while meeting the capacity. 
efficiency_score = priority_weight / total_task_duration
- priority_weight = 2 if priority is "High"
- priority_weight = 1 if priority is "Low"

Task 3.1

```bash
make worker3_1
```

Task 3.2

```bash
make multi
```

To improve concurrency, I created a shared JobManager and launched 3 worker threads, each with capacity 10.

**Observations:**
- The 3-worker system finished the job stream significantly faster.
- Execution was more parallelized and efficient under high load.
- Performance exceeded a single worker at capacity 15 due to better distribution.

This shows how multi-worker architecture scales better with job size diversity.


5. View plots generated in charts folder




#### (Option 2: Run Locally with python VENV)

1. Extract .tar file

```bash
tar -xf job-scheduler-ZhangCao.tar job-scheduler/
```

2. Unzip data files

```bash
unzip job_list.zip -d ./extracted_jobs && unzip job_list_3-1.zip -d ./extracted_jobs
```

3. Create a VENV

```bash
cd job-scheduler
python -m venv myvenv
```

3. Activate VENV

```bash
source myvenv/bin/activate
```

4. Install packages

```bash
pip install requests matplotlib pandas plotly flask
```

5. Run the server

For Task 2

```bash
source myvenv/bin/activate
python server_task_2.py
```
or
```bash
source myvenv/bin/activate
make server_task_2
```

For Task 3.1 & Task 3.2

```bash
source myvenv/bin/activate
python server_task_3.py
```
or
```bash
source myvenv/bin/activate
make server3
```

6. Run the worker

Task 2.2

```bash
source myvenv/bin/activate
python worker_2_2.py
```
or
```bash
source myvenv/bin/activate
make worker2_2
```

Task 2.3

```bash
source myvenv/bin/activate
python worker_2_3.py
```
or
```bash
source myvenv/bin/activate
make worker2_3
```

Sort tasks based on efficiency_score while meeting the capacity. 
efficiency_score = priority_weight / total_task_duration
- priority_weight = 2 if priority is "High"
- priority_weight = 1 if priority is "Low"

Task 3.1 - Numerical priority 1-100

```bash
source myvenv/bin/activate
python worker_3_1.py
```
or
```bash
source myvenv/bin/activate
make worker3_1
```

- Fetch and execute jobs over time
- Log task execution
- Plot and save a chart to the charts folder

Task 3.2 – Multi-Worker Scheduling

```bash
source myvenv/bin/activate
python python task_3_2/controller.py
```
or
```bash
source myvenv/bin/activate
make multi
```

To improve concurrency, I created a shared JobManager and launched 3 worker threads, each with capacity 10.

**Observations:**
- The 3-worker system finished the job stream significantly faster.
- Execution was more parallelized and efficient under high load.
- Performance exceeded a single worker at capacity 15 due to better distribution.

This shows how multi-worker architecture scales better with job size diversity.





