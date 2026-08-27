---
title: 'Instructor Notes'
---

## Teaching Introduction to HPC Systems

This guide provides pedagogical advice, timing information, and practical tips for teaching Workshop 0.

## Workshop Overview

Workshop 0 is designed as an introductory workshop for researchers with no prior HPC experience. It emphasizes practical skills and hands-on learning following The Carpentries pedagogy.

**Target Audience:**
- First-time HPC users
- New graduate students
- Undergraduate researchers starting computational work
- Faculty transitioning to research computing

**Prerequisites:**
- Basic comfort with computers
- No prior Linux or HPC knowledge required
- Pomona email and DUO authentication (already configured)

**Estimated Duration:** 3.5-4 hours for full workshop (or 2-2.5 hours for abbreviated version)

## Episode Breakdown & Timing

### Episodes 1-2: What is HPC? / Why Use HPC? (45 min teaching + 15 min exercises)

**Learning Objectives:**
- Students understand when and why HPC is useful
- Students know Sagehen HPC's basic architecture
- Students distinguish between head nodes and compute nodes

**Key Concepts:**
- HPC enables research infeasible on personal computers
- Shared clusters require coordination (SLURM)
- Sagehen has different node types for different purposes

**Teaching Tips:**
- Start with relatable examples: "How long does your current work take?"
- Use the cluster diagram to show architecture clearly
- Emphasize the "never run on head node" rule repeatedly
- Show real statistics about Sagehen usage (if available)

**Common Misconceptions:**
- Students think they can just SSH to any node (clarify: SLURM controls this)
- Students underestimate how much data/time their work needs
- Students don't understand why their job is "pending"

**Timing Notes:**
- Architecture section: 10 min teaching + 5 min discussion
- Storage overview: 10 min (brief; detailed later)
- SLURM introduction: 15 min (foundational for later)
- Challenges: 15 min (students discuss, don't code yet)

**Checkpoint:** Students should be able to articulate why their research needs HPC.

### Episode 3: Connecting to Sagehen HPC (30 min teaching + 20 min exercises)

**Learning Objectives:**
- Students successfully SSH to Sagehen
- Students understand DUO authentication
- Students see the head node prompt

**Key Concepts:**
- SSH is secure remote access
- DUO adds necessary security
- Different OS have different tools but same process

**Teaching Tips:**
- Have students start this BEFORE class if possible (account setup takes time)
- Demo live SSH connection; pause at each step
- Show common errors and how to fix them
- Have IT contact info ready for account issues
- Some students may be off-campus: mention VPN if needed

**Technical Setup:**
- Test your own SSH connection before class
- Have its-hpc contact ready for account issues
- Ensure WiFi is stable for DUO authentication

**Common Issues:**
- Students using wrong username (email instead of username part)
- DUO app not installed (have SMS backup ready)
- SSH not installed on their system (have PuTTY downloads)
- Network issues (off-campus without VPN)

**Timing Notes:**
- macOS/Linux SSH: 5 min demo
- Windows SSH: 5 min demo (show multiple options)
- DUO troubleshooting: 10 min
- Live login practice: 10 min
- Each student trying live: 5-10 min

**Checkpoint:** All students can successfully SSH and see the prompt.

### Episodes 4-5: Navigating the Filesystem / Files and Directories (40 min teaching + 20 min exercises)

**Learning Objectives:**
- Students navigate between directories confidently
- Students understand different storage purposes
- Students can check storage usage

**Key Concepts:**
- Different filesystem locations have different purposes
- File permissions matter on shared systems
- Scratch is temporary, home is permanent

**Teaching Tips:**
- Go slowly on Linux commands; many are new
- Live demo each command before students try
- Emphasize safe rm practices (demo both safe and risky ways)
- Show directory structure visualization (tree, ls -R)
- Discuss storage costs: "If everyone fills 100GB quota..."

**Common Mistakes:**
- Students use `rm -rf` without checking directory
- Students save large results in `/scratch` (will be deleted!)
- Students don't organize work (files everywhere)
- Students create huge tar archives "just in case"

**Timing Notes:**
- Basic navigation commands: 10 min demo + 5 min practice
- Storage locations: 10 min explanation with examples
- Permissions: 5 min (brief; not the focus)
- Quota checking: 5 min
- Organizing work: 10 min planning + practice

**Checkpoint:** Students have created ~/workshop-0/ and understand home vs scratch.

### Episodes 6-7: Cluster Architecture / Nodes and Partitions (35 min teaching + 15 min exercises)

**Learning Objectives:**
- Students understand partitions and resource allocation
- Students can use `sinfo` to explore cluster
- Students know when to use which partition

**Key Concepts:**
- Partitions group nodes with similar characteristics
- Resource requests must be accurate
- SLURM allocates entire cores (no sharing within a job)

**Teaching Tips:**
- Show `sinfo` output live on actual Sagehen
- Demonstrate resource request matching (too high = longer wait)
- Use decision tree for partition selection
- Emphasize GPU is shared resource (request only what's needed)
- Discuss realistic resource needs for common workloads

**Common Misconceptions:**
- "More cores = faster" (depends on parallelization)
- "I should request the maximum" (wastes resources, longer wait times)
- GPU nodes are free to use (explain they're limited)

**Timing Notes:**
- Partition overview: 10 min (amd, gpu, short)
- Hardware specs: 5 min (use table)
- `sinfo` demo: 10 min live
- Decision-making: 10 min exercises

**Checkpoint:** Students can run `sinfo` and explain which partition they'd use.

### Episode 8: Software Modules (30 min teaching + 20 min exercises)

**Learning Objectives:**
- Students understand why module systems exist
- Students can load/unload modules
- Students know how to find modules

**Key Concepts:**
- Modules solve version conflicts
- Dependencies are handled automatically
- Always `module purge` in scripts

**Teaching Tips:**
- Start with the problem (version conflicts) before the solution
- Show `module avail` output and find familiar packages
- Demo loading, checking, unloading
- Show what happens if you load conflicting modules
- Emphasize reproducibility: module loads in scripts

**Common Issues:**
- Students forget `module purge` in scripts (results vary!)
- Students don't realize modules persist between sessions
- Students request features already available (they just didn't load them)

**Timing Notes:**
- Module problem explanation: 8 min
- Available modules exploration: 8 min
- Load/unload practice: 8 min
- Script reproducibility discussion: 6 min

**Checkpoint:** Students can load Python, check version, unload, and explain why.

### Episode 9: Running Your First Job (40 min teaching + 25 min exercises)

**Learning Objectives:**
- Students successfully submit a job with `sbatch`
- Students monitor job status with `squeue`/`sacct`
- Students retrieve and understand job output

**Key Concepts:**
- Batch scripts are reproducible and asynchronous
- SBATCH directives control resource allocation
- Jobs may wait in queue before running

**Teaching Tips:**
- This is the "aha!" moment for many students
- Live demo every step: write, submit, monitor, check output
- Show the difference between job status (pending vs running vs completed)
- Explain why their job might wait (cluster busy)
- Show common errors and how to diagnose them
- Have backup script ready if demo fails

**Technical Setup:**
- Test sbatch on Sagehen before class
- Have simple test script ready
- Maybe prepare second longer script to show queuing

**Common Issues:**
- Students request 0 time/memory (auto-corrects but confusing)
- Job runs but output file not found (wrong pathname)
- Job completes before student checks status (emphasize `sacct`)
- Typos in SBATCH directives cause silent failures

**Timing Notes:**
- Batch vs interactive: 5 min
- Script anatomy: 15 min (walk through each line)
- Writing script: 5 min
- Submitting job: 3 min
- Monitoring: 10 min (wait for job to complete)
- Checking output: 5 min

**Checkpoint:** Every student has submitted a job and seen output.

### Episode 10: Next Steps (10 min teaching + 5 min exercises)

**Learning Objectives:**
- Students know where to go after this workshop
- Students can start an interactive session with `srun --pty bash`

**Teaching Tips:**
- Demo an interactive `srun` session so students see the compute-node prompt
- Point to Workshop 9 (SLURM Job Scheduling) as the natural follow-on
- Have students draft the skeleton batch script for their own research project
- End on the support channels: its-hpc@pomona.edu

## Overall Teaching Strategy

### The Carpentries Approach

This workshop follows The Carpentries pedagogical model:

1. **Live coding/demonstration**: Instructors type and execute commands live (not slides)
2. **Hands-on challenges**: Students do exercises, not just watch
3. **Immediate feedback**: "Did this work for you?"
4. **Psychological safety**: "It's OK if it doesn't work; debugging is normal"

### Pacing

- **Too fast**: Learners fall behind, become discouraged, learn nothing
- **Too slow**: Learners get bored, lose interest, don't learn
- **Just right**: Energetic, interactive, everyone participates

**Indicator of good pace:**
- Challenges take 8-12 minutes (not 3, not 20)
- Most students finish together
- Questions are deeper than "how do I...?"

### Facilitating Challenges

1. **Before**: Explain what they'll do and why
2. **During**: Circulate; watch for stuck learners; help quietly
3. **After**: Ask someone what they did; discuss solutions
4. **Debrief**: Address common struggles and misconceptions

### Managing Mixed Experience Levels

Some learners may have prior Linux/HPC experience:

- **Use them as helpers**: "Can you help your neighbor with this?"
- **Give them stretch exercises**: "Try loading two different Python versions simultaneously"
- **Value their questions**: Use these to deepen everyone's understanding
- **Respectfully moderate**: "Great point! Let's check that after the episode"

## Pacing Guidelines for Full Day

```
8:00-8:10      Welcome & introductions
8:10-9:00      Episodes 1-2 (What is HPC / Why Use HPC) + challenges
9:00-10:00     Episode 3 (Connecting) + live SSH
10:00-10:30    Break
10:30-11:20    Episodes 4-5 (Filesystem / Files & Directories) + challenges
11:20-12:00    Episodes 6-7 (Cluster Architecture / Nodes & Partitions) + challenges
12:00-1:00     Lunch
1:00-2:00      Episode 8 (Modules) + challenges
2:00-3:00      Episode 9 (First Job) + live sbatch
3:00-3:30      Episode 10 (Next Steps) + Q&A/Wrap-up
```

## Quick Version (2.5 hours)

If shorter on time:

- Skip Episodes 4-5 (filesystem) or do briefly
- Combine Episodes 6-8 into one focused session
- Emphasize Episode 9 (job submission is the goal)
- Use setup.md for pre-workshop filesystem learning

## Troubleshooting During Teaching

### If a Student Can't SSH

- **First**: Check account (email its-hpc-account)
- **Alternative**: Use OnDemand portal (show URL)
- **Backup**: Have them pair with a neighbor and observe
- Have its-hpc contact ready and visible

### If DUO Won't Work

- Many students may have DUO issues; be patient
- Have SMS as backup
- Collect emails of struggling students; have IT follow up
- Continue with others who are connected

### If SBATCH Doesn't Work

- Check permissions: `ls -la job_script.sh` (needs to be readable)
- Check typos in script carefully
- Try submitting a known-working script to test environment
- Have backup script ready in case main demo fails

### If cluster is overloaded

- Jobs may wait much longer than expected
- Explain: this shows real cluster behavior
- Can demo with pre-recorded job output
- Reassure: "This is why the queue system matters"

## Handling Questions

**During teaching**:
- "Great question! Let's tackle that after this section"
- Keeps pace while honoring curiosity

**For off-topic questions**:
- "That's a great question! Might be outside our scope today. Let's talk after class"

**For questions you don't know**:
- "Excellent question! I don't know the answer. Let's ask its-hpc@pomona.edu"
- Model that not knowing is OK

## Assessment

Observe learners:

- Can they navigate directories?
- Can they load modules and verify?
- Can they submit and monitor jobs?
- Do they understand when to use each partition?

**Optional post-workshop survey:**
- What did you find most useful?
- What would you like more time on?
- How confident are you to use Sagehen now?

## After the Workshop

### Recommended Follow-ups

- **1 week**: Brief email with tips and resources
- **2 weeks**: Check-in: "Any questions from your first jobs?"
- **Future workshops**: Advanced topics (GPU, MPI, modules)

### Refer to Other Workshops

- **Workshop 9** (SLURM Job Scheduling): More advanced job control
- **Other Carpentries workshops**: Linux shell, Git, Python, R
- **Sagehen documentation**: https://www.pomona.edu/its/

## Resources for Instructors

- **The Carpentries Handbook**: https://docs.carpentries.org/
- **Lmod Documentation**: https://www.tacc.utexas.edu/research-development/tacc-projects/lmod
- **SLURM Documentation**: https://slurm.schedmd.com/
- **Sagehen Help**: its-hpc@pomona.edu
- **This workshop's Quick Reference**: learners/reference.md

## Tips for Success

1. **Know your material**: Practice each episode's live demos
2. **Know your cluster**: Have tested all commands on current Sagehen
3. **Know your audience**: Adjust examples to their research areas
4. **Keep energy high**: Enthusiasm is contagious
5. **Be patient**: Everyone moves at different pace
6. **Have fun**: Celebrate "first jobs"!
