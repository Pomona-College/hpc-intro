---
title: 'Quick Reference'
---

## Sagehen Quick Reference Card

### Connection & Access

| Command | Purpose |
|---------|---------|
| `ssh username@sagehen.hpc.pomona.edu` | Connect via SSH |
| `exit` or `logout` | Disconnect from Sagehen |
| https://ondemand.hpc.pomona.edu/ | Web portal (no SSH needed) |

### Cluster Information

| Command | Purpose |
|---------|---------|
| `sinfo` | Show all partitions and node status |
| `sinfo -l` | Detailed partition information |
| `sinfo -N` | Show all nodes |
| `sinfo -p amd` | Show specific partition (e.g., amd) |
| `lscpu` | Show CPU information |
| `free -h` | Show available memory |

### File & Directory Navigation

| Command | Purpose |
|---------|---------|
| `pwd` | Print working directory |
| `ls` | List files |
| `ls -lah` | Long format with hidden files |
| `cd ~` | Go to home directory |
| `cd directory` | Change to directory |
| `cd ..` | Go up one level |
| `mkdir dirname` | Create directory |
| `mkdir -p path/to/dir` | Create nested directories |
| `rm file` | Delete file |
| `rm -r directory` | Delete directory and contents |

### Storage Locations

| Path | Purpose | Backup | Size |
|------|---------|--------|------|
| `/rhome/username` | Home directory | Yes | ~100 GB |
| `/bigdata/labname` | Lab shared storage | Yes | 1 TB |
| `/scratch/$USER` | Temporary job storage | No | Unlimited* |
| `/tmpfs` | RAM disk (during jobs) | No | ~1 GB |

*Auto-cleaned after 30 days

### Checking Storage Usage

| Command | Purpose |
|---------|---------|
| `du -sh ~` | Home directory size |
| `du -sh ~/` *` | Breakdown by subdirectory |
| `du -sh /bigdata/labname` | Lab storage size |
| `quota -s` | Show quota information |

### Module System (Lmod)

| Command | Purpose |
|---------|---------|
| `module avail` | List all available modules |
| `module avail python` | Search for modules (e.g., python) |
| `module load python` | Load default version |
| `module load python/3.11.2` | Load specific version |
| `module unload python` | Unload module |
| `module purge` | Unload all modules |
| `module list` | Show currently loaded modules |
| `module show python` | Show module details |

### Job Submission & Management

| Command | Purpose |
|---------|---------|
| `sbatch script.sh` | Submit batch job |
| `squeue -u $USER` | Check your job status |
| `squeue -j JOBID` | Check specific job |
| `scancel JOBID` | Cancel a job |
| `sacct -u $USER` | Show job history |
| `sacct -j JOBID` | Details of specific job |

### Common SBATCH Directives

```bash
#!/bin/bash
#SBATCH --job-name=myname        # Job name
#SBATCH --partition=short         # Partition (short, amd, gpu)
#SBATCH --time=01:00:00          # Max runtime HH:MM:SS
#SBATCH --ntasks=1               # Number of tasks
#SBATCH --cpus-per-task=4        # Cores per task (1-128)
#SBATCH --mem=8G                 # Memory per job
#SBATCH --output=job_%j.log      # Output file (%j = job ID)
#SBATCH --gres=gpu:1             # Request 1 GPU
```

### File Operations

| Command | Purpose |
|---------|---------|
| `cat file.txt` | View file contents |
| `head -n 10 file.txt` | Show first 10 lines |
| `tail -n 10 file.txt` | Show last 10 lines |
| `grep "pattern" file.txt` | Search for text in file |
| `wc -l file.txt` | Count lines |
| `chmod +x script.sh` | Make file executable |
| `cp source dest` | Copy file |
| `mv source dest` | Move/rename file |

### Text Editors

| Command | Purpose |
|---------|---------|
| `nano file.txt` | Simple editor |
| `vim file.txt` | Advanced editor |

### Job Script Template

```bash
#!/bin/bash
#SBATCH --job-name=myanalysis
#SBATCH --partition=amd
#SBATCH --time=04:00:00
#SBATCH --ntasks=1
#SBATCH --cpus-per-task=8
#SBATCH --mem=16G
#SBATCH --output=%j_output.log

# Load modules needed
module purge
module load python/3.11.2

# Run your analysis
echo "Starting analysis..."
python my_script.py
echo "Analysis complete!"
```

### Partition Summary

| Partition | Max Time | Cores | GPUs | Best For |
|-----------|----------|-------|------|----------|
| short | 2 hours | 128 | 0 | Testing & debugging |
| amd | 30 days | 128 | 0 | General compute |
| gpu | 30 days | 128 | Up to 3 | GPU-accelerated work |

### Environment Variables

| Variable | Purpose |
|----------|---------|
| `$USER` | Your username |
| `$HOME` | Your home directory |
| `$SLURM_JOB_ID` | Current job ID |
| `$SLURM_JOB_NAME` | Current job name |
| `$SLURM_CPUS_PER_TASK` | Cores allocated |
| `$SLURM_JOB_PARTITION` | Current partition |
| `$SCRATCH` | Scratch directory (during jobs) |

### Useful Aliases (Add to ~/.bashrc)

```bash
alias ll='ls -lah'
alias sq='squeue -u $USER'
alias sa='sacct -u $USER'
alias cd-home='cd ~'
alias du-home='du -sh ~'
```

### Common Error Messages

| Error | Solution |
|-------|----------|
| `sbatch: command not found` | SLURM not loaded; try `module load slurm` |
| `Permission denied (publickey)` | Wrong username or password |
| `Job timeout` | Increase `--time` in sbatch script |
| `Out of memory` | Increase `--mem` in sbatch script |
| `Module not found` | Check spelling; use `module avail` to find correct name |

### Contact & Support

| Issue | Contact |
|-------|---------|
| HPC account problems | its-hpc@pomona.edu |
| Technical issues | its-hpc@pomona.edu |
| Sagehen access | its-hpc@pomona.edu |
| Pomona IT general | 909-621-8600 |
| This workshop | Ask your instructor |

### Sagehen Hardware Summary

**Compute Nodes (amd partition):**
- 12 nodes (a001-a012)
- 128 cores, 500 GB RAM each
- 30-day max job time

**GPU Nodes (gpu partition):**
- 5 nodes with NVIDIA GPUs
- 128 cores, 500 GB RAM each
- A100 (80GB), L40S (48GB), V100 (16GB)

**Head Node (sagehen.hpc.pomona.edu):**
- 2 cores, 8 GB shared RAM
- **Don't run jobs here!**
- Use for: login, submission, compilation

### Recommended Workflow

1. Test job on `short` partition (fast feedback)
2. Debug with `squeue` and output files
3. Fix issues and increase `--time` for longer runs
4. Submit to `amd` partition for production
5. Monitor with `squeue` and `sacct`
6. Copy results from scratch to `/rhome` or `/bigdata`
7. Clean up temporary files before quota limit

### More Information

- [Sagehen cluster documentation](https://its.pomona.edu/hpc)
- [SLURM documentation](https://slurm.schedmd.com/)
- [Lmod module system](https://www.tacc.utexas.edu/research-development/tacc-projects/lmod)
- Episode 6: Running Your First Job for detailed sbatch tutorial
