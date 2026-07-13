---
title: "What is High-Performance Computing?"
teaching: 15
exercises: 5
---

:::::::::::::::::::::::::::::::::::::: questions

- What is high-performance computing (HPC)?
- What is a cluster and how is it different from my laptop?
- What is Sagehen?

::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Define high-performance computing and understand its role in modern research
- Distinguish between personal computers and HPC clusters
- Identify the key components of an HPC cluster

:::::::::::::::::::::::::::::::::::::::::::::::

## What is High-Performance Computing (HPC)?

High-performance computing refers to using multiple powerful computers (nodes) together to solve computationally intensive problems much faster than a single personal computer could alone. These computers are networked together into what we call a **cluster** or **supercomputer**.

### Key Advantages of HPC Clusters

1. **Massive Parallelism**: Run computations across dozens or hundreds of cores simultaneously
2. **Enormous Memory**: Some nodes have 500+ GB RAM (your laptop might have 8-16 GB)
3. **Specialized Hardware**: GPUs, high-bandwidth storage, interconnects optimized for communication
4. **Resource Sharing**: Fair allocation of resources among hundreds of researchers
5. **Professional Administration**: Dedicated IT staff manage hardware, software, security, and backups
6. **Reproducibility**: Jobs run the same way every time, independent of what else is running

## Introducing Sagehen

**Sagehen** (sagehen.hpc.pomona.edu) is Pomona College's research computing cluster. Named after a bird native to California's Sierra Nevada, Sagehen brings powerful computing resources to Pomona's research community.

### Who Should Use Sagehen?

Sagehen is available to:
- Faculty researchers and their students
- Graduate students conducting research
- Undergraduate researchers
- Course-based computing projects

If you're doing research that requires significant computation, Sagehen is available to you at no cost.

## How HPC Clusters Work

### The Job Scheduler: SLURM

**SLURM** (Simple Linux Utility for Resource Management) coordinates all job execution on Sagehen.

**How It Works:**
1. You write a job script describing what you want to run and what resources you need
2. You submit the job to SLURM using `sbatch` or `srun`
3. SLURM places your job in a queue and monitors resource availability
4. When resources become available AND your job has high enough priority, SLURM runs it
5. Your job completes and results are written to output files or your home directory

**Why SLURM?**
- **Fairness**: Ensures every researcher gets a turn using the cluster
- **Efficiency**: Runs multiple jobs simultaneously on different nodes
- **Reproducibility**: Your job runs the same way every time
- **Accounting**: Tracks resource usage for billing and planning

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: HPC vs. Personal Computer

Which of the following tasks would benefit most from running on an HPC cluster instead of your laptop? Select all that apply.

A) Writing a research paper in Word
B) Training a neural network on 500 GB of image data
C) Browsing the web for literature review
D) Running a molecular dynamics simulation for 3 weeks
E) Checking email

:::::::::::::::::::::::: solution

## Solution

**B and D** would benefit from HPC.

- A, C, E are everyday tasks that don't need HPC
- B involves large data and GPU-accelerated computation, perfect for the gpu partition
- D is a long-running simulation that would tie up your laptop for weeks

:::::::::::::::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- High-performance computing enables research that would be infeasible on personal computers
- HPC clusters combine many powerful nodes with fast networks and shared storage
- Sagehen is Pomona College's HPC cluster, available at no cost to researchers
- SLURM is the job scheduler that manages fair resource allocation among all users

::::::::::::::::::::::::::::::::::::::::::::::
