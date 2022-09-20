# Parallel-computing-with-python
[![Python 3.9](https://img.shields.io/badge/python-3.7%20%7C%203.8%20%7C%203.9-brightgreen)](https://www.python.org/downloads/release/python-390/)

### Context

A taks which is having:
- any IO operatoins involved
- any API call
- any other work which doesn't requires CPU 

can block program's thread until it's done, and CPU can be IDLE for that duration if it's having anything else on the plate to process.

Parallel computing is a methodology to break down any task into pieces of small task which can be executed in parallel, independently of each other then combine the results to get final outcome.

Parallel computing can be achieved in following ways:

1. Multithreading
2. MultiProcessing
3. AsyncIO


In this talk we will cover up how to achieve above 3 methodologies using Python. We'll create a download task which needs to download 100 images from internet. As you can guess, depending upon server reponse speed, network bandwidth and other factors, it take sometime for data to arrive after making the HTTP call.

We'll demonstrate:

1. Running 1 thread synchronously can take 10x more time to do the task because program's flow is getting blocked until the response of that HTTP API call arrives.

2. Dividing work and running multple threads, can save almost 9-10x time.

3. Dividing work and running multiple processes, can save almost 8-9x time.

4. Running 1 thread but asynchronously can let program's run without getting blocked until HTTP response arrives, and can get the job done in almost 9-10x less time.


Here's a matrix captured from my machine after running locally:

|      S.No.    |  Run Type    | Files Downloaded    |  Time Taken |
| ------------- | ------------- | ------------ | ------------- |
|    1          | Sequential: Synchronous, 1 Thread, 1 Process| 100 | 59.8 Seconds |
|    2          | Parallel (MultiThreading): 10 Threads, 1 Process| 100 | 6.12 seconds |
|    3          |  Parallel (MultiProcessing): 5 Processes | 100 | 8.56 seconds |
|    4          |  Parallel (Async IO): 1 Processes, 1 Thread, Asynchronous | 100 | 7.42 seconds |

Above matrix has been captured from a local run and the differences become more and more, when the CPU blocking operatoins get larger and time consuming.




### Setup guideline

1. Create a virtual environment

```virtualenv venv```

2. Activate this virtual env

```source venv/bin/activate```

3. Install dependencies

```pip install -r requirements.txt```


### Running guideline

1. Run Normal mode

```python normal_run.py```

Clean up the folder created by Run


2. Run Multithreaded mode

```python multithreading_run.py```

Clean up the folder created by Run

3. Run MultiProcess mode

```python multiprocessing_run.py```

Clean up the folder created by Run

4. Run async io mode

```python asyncio_run.py```

Clean up the folder created by Run

