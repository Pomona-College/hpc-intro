---
title: Introduction to HPC Systems
---

## Welcome to Workshop 0: Introduction to HPC Systems

This workshop is your gateway to high-performance computing at Pomona College. Whether you're a first-time HPC user or transitioning from personal computers to cluster computing, this introductory workshop will guide you through everything you need to know to begin using **Sagehen HPC**, our powerful research computing cluster.

### What You'll Learn

By the end of this workshop, you will be able to:

- Understand what high-performance computing (HPC) is and why it matters for research
- Connect securely to Sagehen using SSH and navigate the two-factor authentication process
- Navigate the Sagehen filesystem and understand the different storage spaces available
- Recognize Sagehen's hardware architecture, including compute nodes and GPU nodes
- Use the module system to load and manage software packages
- Submit and monitor your first computational job

### About Sagehen HPC

**Sagehen** (sagehen.hpc.pomona.edu) is Pomona College's research computing cluster managed by Information Technology Services (ITS). It features:

- **12 AMD EPYC compute nodes**: 128 cores and 500 GB RAM each
- **GPU-enabled nodes**: Sagehen has 10 GPUs across multiple nodes (4× NVIDIA A100 80 GB, 4× L40S 48 GB, 2× RTX PRO 6000 96 GB; confirmed May 2026 — see Workshop 16 for full hardware breakdown)
- **Multiple storage systems**: Home directories (100 GB), lab storage (1 TB), and high-speed scratch space
- **SLURM job scheduler**: Manage computational jobs efficiently across all users
- **Lmod software environment**: A managed Lmod environment with hundreds of pre-built software modules
- **OnDemand web portal**: Access via browser without SSH

### Workshop Structure

This 10-episode workshop is organized as follows:

1. **What is HPC?** - Understand high-performance computing concepts and Sagehen's role
2. **Why Use HPC?** - Recognize when an HPC cluster is the right tool for your research
3. **Connecting to Sagehen** - SSH access, DUO authentication, and your first login
4. **Navigating the Filesystem** - Understanding directories, storage spaces, and Linux basics
5. **Files and Directories** - Working with files, directories, and basic commands on Sagehen
6. **Cluster Architecture** - Learn about nodes, partitions, and hardware specifications
7. **Nodes and Partitions** - Survey Sagehen's compute, GPU, and login nodes and how SLURM partitions group them
8. **Software Modules** - Discover and use the Lmod module system
9. **Running Your First Job** - Submit and monitor a SLURM batch job
10. **Next Steps** - Build on this foundation with the rest of the Pomona HPC workshop series

::::::::::::::::::::::::::::::::::::: prereq

## Prerequisites

This workshop assumes no prior HPC experience, but you should have:
- **Pomona College credentials**: Your @pomona.edu email and password
- **DUO authentication**: Access to your Pomona DUO account for two-factor authentication
- **A computer with SSH**: macOS and Linux have SSH built-in; Windows users can use PowerShell, WSL, or PuTTY
- **An HPC account**: Contact its-hpc@pomona.edu to request one if needed

::::::::::::::::::::::::::::::::::::::::::::::::

### How to Use This Workshop

- **For learners**: Work through each episode in order. We recommend having a terminal open so you can follow along with examples on Sagehen.
- **For instructors**: See the [Instructor Notes](instructors/instructor-notes.md) for detailed timing, common questions, and teaching strategies.
- **For quick reference**: Check the [Quick Reference Card](learners/reference.md) for command syntax and useful information.

### Getting Help

- **Technical support**: its-hpc@pomona.edu
- **Account issues**: its-hpc@pomona.edu
- **This workshop**: Ask your instructor or refer to the [Setup Guide](learners/setup.md)

::::::::::::::::::::::::::::::::::::: callout

## Important: This is a Shared Resource

Sagehen is used by hundreds of researchers. Please be a good neighbor:
- Don't run computationally intensive jobs on the head node
- Clean up your temporary files regularly
- Respect resource quotas and time limits
- Report issues to its-hpc@pomona.edu

:::::::::::::::::::::::::::::::::::::::::::::::

### About The Carpentries

This workshop follows The Carpentries approach to teaching, emphasizing hands-on learning, realistic examples, and community collaboration. Learn more at [carpentries.org](https://carpentries.org/).

---

**Ready to get started?** Begin with [Episode 1: What is HPC?](episodes/01-what-is-hpc.md).

## Acknowledgments

Developed by **Andrew Wilson**, Director of Research Computing and Digital
Scholarship at Pomona College, with **Andrei Motchenko**, who tested, edited
and produced screenshots for the workshop series.
