# The Tracer Files: Crackling the Case of Performance Impact in Tracing Linux I/O-Intensive Applications

## ABSTRACT

## INTRODUCTION

Measuring the performance of a system is not a trivial task. From a computational perspective, it is necessary to understand what the hardware components of the system are (type of CPU, RAM, network card, and data storage devices), comprehend the architecture of the infrastructure where these components are inserted, the layers of software involved in the solution, and how these components interact with each other. Finally, it is essential to understand how these resources are used in the business context of the organization to determine which performance metrics make sense to be collected at each layer of the system to determine the system's performance.

Data constitutes the core of most applications, with storage devices such as tape, hard disk drives (HDDs), and solid-state drives (SSDs) serving as mediums for long-term data retention. According to \textcite{Reisel2020Digitalization} mankind will produce approximately 175 ZettaBytes of data by 2025. This volume encompasses data generated, captured, or replicated across various platforms, including traditional and cloud data centers, robust enterprise infrastructures such as cellular towers and branch offices, personal computers, smartphones and Internet of Things (IoT) devices.

\textcite{YANG_ETAL2022} said that understanding the \ac{I/O} characteristics of applications on supercomputers is crucial to paving the path for application optimization and system resource allocation. Therefore, this statement is also true for applications running on regular enterprise computers. For instance, a system designed for training an \ac{ML} model, requires a fast and optimized storage subsystem to keep its GPUs busy, otherwise the GPUs will be mostly idle wasting time and money.

Industry attention to storage performance is evident through the development of benchmarks like the MLPerf Storage Benchmark and SFS2020 AI\_IMAGE by organizations such as MLCommons and the Standard Performance Evaluation Corporation (SPEC). MLCommons, an Artificial Intelligence engineering consortium, aims to enhance AI systems \cite{mlcommons_about:2024}. SPEC, a non-profit organization, creates standardized benchmarks and tools to evaluate the performance of modern computing systems \cite{spec_about:2024}. These efforts underscore the importance of understanding and measuring storage performance.

Tracing is a powerful technique to collect information about what is happening in the system. The strace command-line tool is commonly utilized in the industry to trace system calls and understand what the application is doing. Deploying strace is easy and in some Linux distributions it is part of the default installation, however running strace in production environments might not be recommended due to its performance cost.

Although strace has implemented mechanisms such as system call filtering reducing its performance cost, the cost is still high   for some type of applications making it not suitable for some tasks like workload characterization in production environments.

Workload Characterization is a process of describing a workload by means of quantitative parameters and functions. Its goal is to define the behavior of the workload and its most important features. On a high level, an application can belong to one or many of the following types: interactive, database, network-based, parallel, etc. Different workloads can be characterized using different metrics and parameters to address a particular application domain \cite{bakhvalov:2020}.

In general, applications make use of the Linux system call API via standard C library wrapper functions, and these functions will carry the required parameters to invoke the system call. Characterizing I/O consists of collecting data about the application's requests for file operations, thus making it possible to extract insights about the application behavior without the need of the application's source code.

In this article, we will study the impact of strace into the application's performance while tracing file I/O system calls. Then, we will experiment with another tracer called BPFTrace and demonstrate that BPFTrace has a lower impact into the application's performance while delivering similar information about the system calls. 

## BACKGROUND

### Linux File I/O System Calls

### Linux Tracepoint System

### Strace

### BPF and BPFTrace

### I/O-Intensive Benchmarks

## MEASURING THE APPLICATION'S PERFORMANCE IMPACT WHILE TRACING FILE I/O SYSTEM CALLS

### Methodology

### The Testing Environment

### The Baseline Measuarements

### The Strace Measurements

### The BPFTrace Measurements

## RESULTS AND DISCUSSION

## CONCLUSION
