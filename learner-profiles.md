---
title: Learner Profiles
---

## Who Should Take This Workshop?

This workshop is designed for researchers new to high-performance computing. Below are three representative learner profiles. Do you see yourself in one of these?

---

## Profile 1: Maya - Graduate Student, New to Computational Research

### Background
Maya is a first-year graduate student in molecular biology. Her research involves analyzing genomic sequences and running phylogenetic reconstructions. Until now, she's used her laptop for data analysis, which has been slow for large datasets.

### What She Knows
- Comfortable with basic computer use
- Some experience with Python (learned for a class)
- Has never used a command line extensively
- Not familiar with clusters or supercomputers

### Why She Needs HPC
- Her datasets are growing: 50+ GB genomic sequences
- Current analysis takes 2-3 weeks on her laptop
- Needs to run hundreds of sequence comparisons
- Her advisor suggested she learn to use Sagehen

### Her Goals
- Get her analysis running 10x faster
- Understand basic job submission
- Learn where to save large datasets
- Eventually run parallel analyses

### Challenges She'll Face
- Command line is unfamiliar (but she'll pick it up!)
- Might not initially understand what "partition" or "SLURM" means
- Could be discouraged if first job fails (won't, but might feel like it)

### Success Indicator
After this workshop, Maya can:
- SSH to Sagehen and navigate directories
- Submit a simple analysis job
- Check job status and retrieve results
- Start planning how to parallelize her sequence comparisons

---

## Profile 2: Dr. James - Faculty Researcher, Transitioning to Computational Methods

### Background
Dr. James is an associate professor in chemistry. His lab has traditionally used bench experiments, but he's starting a new computational chemistry initiative studying molecular reaction mechanisms. He's hired a postdoc to help develop computational methods.

### What He Knows
- Experienced scientist; comfortable learning new tools
- Limited command line experience (occasional Terminal use on Mac)
- Familiar with scientific software (but mostly GUIs)
- Knows research computing exists but never used it

### Why He Needs HPC
- Quantum chemistry simulations require massive computation
- Single simulations take weeks on a workstation
- Wants to run parameter sweeps (100+ variations)
- Needs stable, reliable infrastructure for grant-funded work

### His Goals
- Set up infrastructure for his lab's computational work
- Understand what students/postdoc will need
- Know how to request resources and budget time appropriately
- Learn enough to oversee research computing decisions

### Challenges He'll Face
- May get frustrated with unfamiliar command line
- Might underestimate or overestimate computational needs
- Time management: busy schedule means limited learning time

### Success Indicator
After this workshop, Dr. James can:
- Access Sagehen and understand its capabilities
- Explain resource needs to his postdoc clearly
- Know how to adjust requests based on actual usage
- Understand whether 4-hour or 4-day jobs are realistic

---

## Profile 3: Alex - Undergraduate Researcher, Data Science Project

### Background
Alex is a junior physics/math major who's enthusiastic about data science. They're working on an independent study analyzing climate datasets for their senior thesis. They're taking some computer science courses and are eager to learn computational tools.

### What He Knows
- Comfortable with Python (learned in CS courses)
- Some experience with Linux (on their own laptop)
- Knows about cloud computing but hasn't used HPC
- High learning ability and motivation

### Why He Needs HPC
- Climate dataset is 200+ GB (won't fit on laptop)
- Analysis includes machine learning that's computationally intensive
- Wants to do more complex analysis than time allows on a laptop
- Plans to feature this work in graduate school applications

### His Goals
- Run computationally intensive machine learning
- Learn industry-standard HPC workflows
- Get experience on real computing infrastructure
- Complete thesis analysis in reasonable timeframe

### Challenges He'll Face
- Might jump ahead too fast; need to reinforce foundations
- Could over-engineer solutions (more parallelization than needed)
- Might try advanced features before understanding basics

### Success Indicator
After this workshop, Alex can:
- Confidently SSH and navigate Sagehen
- Submit Python jobs that process large datasets
- Use module system to load ML libraries
- Start planning how to parallelize analysis further

---

## Using These Profiles

**During teaching:**
- "This is like what Maya is doing..."
- "Remember, Dr. James might see this from a PI perspective..."
- "Alex is excited about optimization..."

**When explaining concepts:**
- Reference their specific challenges
- Use relevant examples for each domain

**For pacing:**
- All three profiles represent different pace/depth needs
- Provide supplementary exercises for learners like Alex
- Offer pre-workshop prep for learners like Maya
- Explain "why" for learners like Dr. James

---

## Common Threads

Despite different backgrounds, all three learners share:

1. **Problem to solve**: Something their current computer can't handle
2. **Limited HPC experience**: First time using a cluster
3. **Research domain knowledge**: They know their field well
4. **Motivation**: Each has a real reason to learn this
5. **Learning style**: Prefer practical, hands-on examples

## Teaching to Diverse Learner Types

### What Works Well

- **Concrete examples**: "This genomic analysis took 3 weeks on a laptop, 3 hours on Sagehen"
- **Multiple approaches**: Show both command line and OnDemand web portal
- **Real scenarios**: Base challenges on actual research (not toy problems)
- **Time to practice**: Let them try with their own problems
- **Encouragement**: "Your first job will work; most issues are simple typos"

### Pacing Tips

- **For enthusiastic learners like Alex**: Have stretch exercises, advanced topics to explore
- **For busy learners like Dr. James**: Provide executive summary of key concepts
- **For anxious learners like Maya**: More practice time, explicit confidence-building
- **For all**: Validate that their anxiety/excitement is normal and healthy

## Real vs. Hypothetical

As instructors, whenever possible:
- Use **real examples** from Pomona research
- Share **actual success stories** (with permission)
- Show **real Sagehen output** (not fake)
- Discuss **real resource constraints** and decisions
- Celebrate **real learner achievements** ("Your first job!")

---

## After the Workshop

These learners won't become HPC experts after 4 hours. They will:

- Understand what HPC is and why it matters
- Successfully connect and submit a job
- Know where to find help
- Be confident enough to continue learning

Many will return for advanced workshops like:
- **Workshop 9: SLURM Job Scheduling** (more job control)
- **GPU Computing Workshop** (if relevant)
- **Parallel Programming** (if they need it)
- **Advanced Module Usage** (for complex software stacks)

Your role is to get them started confidently, not make them experts.
