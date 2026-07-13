---
title: "Why Use an HPC Cluster?"
teaching: 15
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions

- When do I need HPC for my research?
- What hardware does Sagehen provide?
- What are the resource limits on Sagehen?

::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Determine when HPC is appropriate for a research workflow
- Describe Sagehen's hardware at a high level
- Understand storage locations and their purposes
- Know where to get help with HPC at Pomona

:::::::::::::::::::::::::::::::::::::::::::::::

## When Do You Need HPC?

### Your Laptop Might Be Enough If:

- Your analysis processes small datasets (< 10 GB)
- Your computations finish in minutes or hours
- You're prototyping code or running exploratory analyses
- You only occasionally need extra computing power

### You Need HPC If:

- Your dataset is very large (100 GB to terabytes)
- Your computation takes hours, days, or weeks
- You need to run thousands of analyses or simulations
- You're training machine learning models
- You're running molecular dynamics, climate models, or other simulations
- You need specialized hardware like GPUs

## Sagehen's Hardware at a Glance

### Compute Nodes (amd partition)

- **12 AMD EPYC compute nodes**
- Each node: 128 CPU cores, 500 GB RAM, SSD storage
- Maximum job time: 30 days (720 hours)
- Best for most research workflows

### GPU Nodes (gpu partition)

- Multiple GPU-accelerated nodes
- NVIDIA A100 GPUs (high-memory, latest generation)
- NVIDIA L40S GPUs (tensor-optimized)
- NVIDIA V100 GPUs (general-purpose GPU computing)
- Each node also has 128 CPU cores + 500 GB RAM
- Maximum job time: 30 days

### The Head Node

The **head node** is your entry point to Sagehen: where you log in, submit jobs, and manage files.

- Address: `sagehen.hpc.pomona.edu`
- CPU: 2 AMD EPYC threads (extremely limited!)
- RAM: 8 GB per user (shared among all users)

::::::::::::::::::::::::::::::::::::::: callout

## Critical: Never Run Jobs on the Head Node!

The head node is shared by hundreds of users. If you run computationally intensive work there, you'll slow down everyone's ability to submit jobs. SLURM will enforce this; long-running processes on the head node will be terminated.

**Always submit jobs to compute nodes using SLURM.**

:::::::::::::::::::::::::::::::::::::::::::::::

## Storage Overview

Sagehen has multiple storage locations, each with different purposes:

| Location | Quota | Backup | Persistence | Use Case |
|----------|-------|--------|-------------|----------|
| `/rhome/username` | ~100 GB | Daily | Persistent | Code, config, small results |
| `/bigdata/labname` | 1 TB/lab | Daily | Persistent | Lab datasets, shared files |
| `/scratch/...` | None | No | Temporary (deleted when job completes) | Large intermediate files |
| `/tmpfs` | ~1 GB/job | No | Temporary (deleted when job ends) | Ultra-fast RAM-backed I/O |

::::::::::::::::::::::::::::::::::::::: callout

## Resource Limits per Account

Each user account has limits to ensure fair sharing:
- Per-account CPU core, GPU, and job queue limits apply
- Storage quotas: `/bigdata` shares a single 1 TB lab quota with `/rhome` (BeeGFS)
- Contact its-hpc@pomona.edu if you need higher limits for a specific project

:::::::::::::::::::::::::::::::::::::::::::::::

## Your First HPC Experience on Sagehen

Over the next episodes, you will:

1. **Log into Sagehen** via SSH with two-factor authentication
2. **Explore the filesystem** and understand where your files go
3. **Learn about partitions** and how to choose the right one
4. **Load software using modules** to access pre-installed scientific packages
5. **Submit your first job** to the SLURM scheduler and see results

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Understanding Your Research Needs

Think about a computational project from your own research (or a hypothetical one):

1. How much data does it involve? (MB, GB, TB?)
2. How long does it typically take to run? (minutes, hours, days?)
3. Does it need specialized hardware (GPU)?
4. Would running this on Sagehen save you time compared to your laptop?

Write down a few sentences about why (or why not) HPC would be useful for this project.

:::::::::::::::::::::::: solution

## Solution

Your answer should discuss:
- The size of data being processed
- The computational time required
- Whether the problem can be parallelized (run in parallel on multiple cores)
- Availability of specialized hardware needs (GPU, high memory, etc.)

For example:
"My machine learning project trains models on 500 GB of image data. On my laptop with 8 cores, this takes 3 weeks. On Sagehen with 128 cores and GPUs, this would probably take 2-3 days, making rapid iteration possible."

:::::::::::::::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Use HPC when your data is large, your computation is long, or you need specialized hardware
- Sagehen has 12 compute nodes (128 cores, 500 GB each) and multiple GPU nodes
- The head node is for login and job submission only; never run jobs there
- Different storage locations serve different purposes: home, lab, scratch, tmpfs
- Contact its-hpc@pomona.edu for help or to request higher resource limits

::::::::::::::::::::::::::::::::::::::::::::::
