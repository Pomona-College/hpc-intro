---
title: "Navigating the Filesystem"
teaching: 15
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions

- How is the Sagehen filesystem organized?
- What are the different storage spaces and what are they for?
- How do I check my storage quota?

::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Understand the different storage locations on Sagehen
- Distinguish between persistent and temporary storage
- Check storage quotas and usage
- Navigate the filesystem using fundamental Linux commands

:::::::::::::::::::::::::::::::::::::::::::::::

## Sagehen's Storage Architecture

Sagehen uses a BeeGFS parallel filesystem connected via 100 Gb Infiniband. It has multiple storage systems, each designed for specific purposes.

### Storage Location Overview

| Location | Quota | Backup | Persistence | Speed | Use Case |
|----------|-------|--------|-------------|-------|----------|
| `/rhome/username` | ~100 GB | Daily | Persistent | Medium | Code, config, small results |
| `/bigdata/labname` | 1 TB/lab | Daily | Persistent | Medium | Lab datasets, shared files |
| `/scratch/...` | None | No | Temporary | Fast (SSD) | Large intermediate files |
| `/tmpfs` | ~1 GB/job | No | Temporary | Fastest (RAM) | Ultra-fast I/O during jobs |

Note: `/rhome` and `/bigdata` share a combined 1 TB lab quota.

### Your Home Directory: /rhome/username

This is your personal space on Sagehen.

- **Size**: Approximately 100 GB
- **Backup**: Yes, daily backups
- **When to use**: Source code, configuration files, small result files
- **When NOT to use**: Large datasets, temporary files from jobs

```bash
# Navigate to your home directory
cd ~

# See where you are
pwd

# List files with details
ls -lah
```

::::::::::::::::::::::::::::::::::::::: callout

## The Tilde Shortcut

In bash, `~` always refers to your home directory:

```bash
cd ~              # Go to home
cd ~/workshop-0   # Go to workshop-0 in home
cp file.txt ~     # Copy file to home
```

:::::::::::::::::::::::::::::::::::::::::::::::

### Lab Storage: /bigdata/labname

If you're part of a research lab, you may have access to shared lab storage.

- **Size**: 1 TB per lab group (shared among all lab members)
- **Backup**: Yes, daily backups
- **When to use**: Large datasets, results shared with collaborators

```bash
# Check if you have lab storage
ls /bigdata
```

If you don't see your lab listed, contact its-hpc@pomona.edu.

### Scratch Storage

High-speed temporary SSD storage designed for jobs that need fast I/O.

- **Location**: `/scratch/$SLURM_JOB_USER/$SLURM_JOB_ID`
- **Lifetime**: Deleted when job completes (non-persistent)
- **When to use**: Large temporary files created during job execution

### RAM Disk: /tmpfs

Ultra-fast memory-backed storage.

- **Lifetime**: Deleted when job ends
- **Size**: Limited (~1-2 GB per job)
- **When to use**: Only for jobs with extreme I/O needs

## Essential Navigation Commands

```bash
# Print working directory (where am I?)
pwd

# List files in current directory
ls

# List with human-readable sizes and hidden files
ls -lah

# Change to home directory
cd

# Change to a specific directory
cd /rhome/username

# Change to previous directory
cd -

# Change up one level
cd ..
```

## Checking Your Storage Usage

::::::::::::::::::::::::::::::::::::::: callout

## BeeGFS Quota Check

On Sagehen's BeeGFS filesystem, the standard `du` command does not work correctly for quota checks. Use the provided script instead:

```bash
quota_check.sh
```

This will display your current usage against your quota.

:::::::::::::::::::::::::::::::::::::::::::::::

If you're approaching your quota, consider:
1. Compressing old results: `tar czf archive.tar.gz data/`
2. Removing unnecessary files
3. Moving data to lab storage: `mv results /bigdata/labname/`
4. Contacting its-hpc@pomona.edu for additional storage

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Explore Sagehen's Storage

Connect to Sagehen and explore the filesystem.

**Steps**:
1. Check your home directory: `cd ~ && pwd`
2. List its contents: `ls -lah`
3. Check for lab storage: `ls /bigdata`
4. Run the quota check: `quota_check.sh`

**Questions**:
- What is the full path to your home directory?
- Do you have access to lab storage?
- How much of your quota is used?

:::::::::::::::::::::::: solution

## Solution

- Your home directory should be `/rhome/username`
- Lab storage appears under `/bigdata/` if your lab has been set up
- `quota_check.sh` shows your current usage vs. your quota limit

If you're using close to 100 GB, consider cleaning up old files. Contact its-hpc@pomona.edu if you need more space.

:::::::::::::::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Sagehen uses BeeGFS over 100 Gb Infiniband for its parallel filesystem
- Your home directory `/rhome/username` is persistent and backed up (~100 GB)
- Lab storage `/bigdata/labname` provides 1 TB shared among lab members
- Scratch (`/scratch`) is SSD-based and deleted when your job completes
- RAM disk (`/tmpfs`) is the fastest but most ephemeral storage
- Use `quota_check.sh` to check your storage usage (not `du`)
- Essential navigation: `pwd`, `ls`, `cd`, `cd ~`, `cd ..`

::::::::::::::::::::::::::::::::::::::::::::::
