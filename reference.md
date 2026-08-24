---
title: 'Quick Reference'
---

## Sagehen Quick Reference Card

### Connection & Access

| Command | Purpose |
|---------|---------|
| `ssh <myusername>@sagehen.hpc.pomona.edu` | Connect via SSH |
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
| `/rhome/<myusername>` | Home directory | Yes | ~100 GB |
| `/bigdata/lab/<labname>` | Lab shared storage | Yes | 1 TB |
| `/scratch` | Temporary job storage | No | No quota* |
| `/tmpfs` | RAM disk (during jobs) | No | ~1 GB |

*Deleted when your job completes -- copy results out before the job ends

### Checking Storage Usage

| Command | Purpose |
|---------|---------|
| `quota_check.sh` | Usage vs. quota (use this, not plain `du`) |
| `du -sh --apparent-size ~` | Approximate home directory size |
| `du -sh --apparent-size /bigdata/lab/<labname>` | Approximate lab storage size |

Note: on BeeGFS, plain `du` does not report quota usage correctly -- use `quota_check.sh`.

### Module System (Lmod)

| Command | Purpose |
|---------|---------|
| `module avail` | List all available modules |
| `module avail miniconda3` | Search for modules (e.g., miniconda3) |
| `module load miniconda3` | Load default version |
| `module load miniconda3/py313_26.3.2-2` | Load specific version |
| `module unload miniconda3` | Unload module |
| `module purge` | Unload all modules |
| `module list` | Show currently loaded modules |
| `module show miniconda3` | Show module details |

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
module load miniconda3/py313_26.3.2-2

# Run your analysis
echo "Starting analysis..."
python my_script.py
echo "Analysis complete!"
```

### Partition Summary

| Partition | Max Time | Cores | GPUs | Best For |
|-----------|----------|-------|------|----------|
| short | Shorter -- check `sinfo -p short` | 128 | 0 | Testing & debugging |
| amd | 30 days | 128 | 0 | General compute |
| gpu | 30 days | 128 | Yes (per-account limits) | GPU-accelerated work |

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
| `sbatch: command not found` | You may be on a compute node or wrong host; run from the head node, or contact its-hpc@pomona.edu |
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
| Pomona IT general | (909) 621-8061 / servicedesk@pomona.edu |
| This workshop | Ask your instructor |

### Sagehen Hardware Summary

**Compute Nodes (amd partition):**
- 12 nodes (a001-a012)
- 128 cores, 500 GB RAM each
- 30-day max job time

**GPU Nodes (gpu partition):**
- 10 GPUs total across the GPU nodes
- 128 cores, 500 GB RAM each
- 4x A100 (80 GB), 4x L40S (48 GB), 2x RTX PRO 6000 (96 GB)

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

- [Sagehen cluster documentation](https://www.pomona.edu/its/)
- [SLURM documentation](https://slurm.schedmd.com/)
- [Lmod module system](https://www.tacc.utexas.edu/research-development/tacc-projects/lmod)
- Episode 9: Running Your First Job for the detailed sbatch tutorial

<!-- highlight <labname>/<myusername> placeholders in code blocks; remove if the varnish theme handles this natively -->
<script>(function(){var CSS='.sh-placeholder{color:#c2410c;font-weight:700}[data-bs-theme="dark"] .sh-placeholder,html.dark .sh-placeholder{color:#fdba74}@media (prefers-color-scheme: dark){[data-bs-theme="auto"] .sh-placeholder{color:#fdba74}}';var RX=/<labname>|<myusername>/g;function firstMatch(el){var w=document.createTreeWalker(el,NodeFilter.SHOW_TEXT,null),nodes=[],full='';while(w.nextNode()){nodes.push({n:w.currentNode,s:full.length});full+=w.currentNode.nodeValue;}RX.lastIndex=0;var m;while((m=RX.exec(full))){var s=m.index,e=s+m[0].length,inSpan=false,parts=[];for(var j=0;j<nodes.length;j++){var ns=nodes[j].s,ne=ns+nodes[j].n.nodeValue.length;if(ne<=s||ns>=e)continue;parts.push({node:nodes[j].n,a:Math.max(s-ns,0),b:Math.min(e-ns,nodes[j].n.nodeValue.length)});var p=nodes[j].n.parentNode;while(p&&p!==el){if(p.classList&&p.classList.contains('sh-placeholder')){inSpan=true;break;}p=p.parentNode;}}if(!inSpan&&parts.length)return parts;}return null;}function wrapParts(parts){for(var i=parts.length-1;i>=0;i--){var t=parts[i].node,txt=t.nodeValue,a=parts[i].a,b=parts[i].b;var span=document.createElement('span');span.className='sh-placeholder';span.textContent=txt.slice(a,b);var f=document.createDocumentFragment();if(a>0)f.appendChild(document.createTextNode(txt.slice(0,a)));f.appendChild(span);if(b<txt.length)f.appendChild(document.createTextNode(txt.slice(b)));t.parentNode.replaceChild(f,t);}}function run(){var st=document.createElement('style');st.textContent=CSS;document.head.appendChild(st);document.querySelectorAll('pre,code').forEach(function(el){var guard=0,parts;while((parts=firstMatch(el))&&guard++<500){wrapParts(parts);}});}if(document.readyState==='loading'){document.addEventListener('DOMContentLoaded',run);}else{run();}})();</script>
