---
title: "Files and Directories"
teaching: 15
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions

- How do I create, copy, move, and delete files?
- How should I organize my work on Sagehen?
- What are file permissions and how do I change them?

::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Create and manage files and directories on Sagehen
- Organize research work with a logical directory structure
- Understand file permissions and access controls
- Share files securely with collaborators

:::::::::::::::::::::::::::::::::::::::::::::::

## Creating and Removing Files and Directories

```bash
# Create a directory
mkdir mydir

# Create nested directories
mkdir -p data/raw/input

# Remove an empty directory
rmdir mydir

# Remove a file (be careful!)
rm myfile.txt

# Remove a directory and everything in it (DANGEROUS!)
rm -rf mydir
```

::::::::::::::::::::::::::::::::::::::: callout

## Never Use `rm -rf` Casually!

The command `rm -rf directory` recursively deletes everything permanently; there is no trash or undo. Always list files first to confirm:

```bash
# List files FIRST to confirm what you're deleting
ls -la mydir

# Then delete
rm -rf mydir

# Or use interactive mode (prompts before deleting)
rm -ri mydir
```

:::::::::::::::::::::::::::::::::::::::::::::::

## Working with Files

```bash
# View file contents
cat myfile.txt

# View beginning of file (first 10 lines)
head myfile.txt

# View end of file (last 10 lines)
tail myfile.txt

# Search for text in a file
grep "pattern" myfile.txt

# Count lines in a file
wc -l myfile.txt

# Search for files by name
find . -name "*.txt"

# Find recently modified files
find . -mtime -7
```

## Organizing Your Work

### Recommended Directory Structure

Create a logical organization in your home directory:

```bash
cd ~
mkdir -p projects/project1
mkdir -p projects/project2
mkdir -p code
mkdir -p data
mkdir -p results
```

Example project structure:
```
/rhome/username/
├── projects/
│   ├── research-1/
│   │   ├── code/
│   │   ├── data/
│   │   └── results/
│   └── research-2/
├── code/
├── scripts/
└── workshop-0/
```

## File Permissions

Every file and directory has permissions controlling who can read, write, and execute it.

### Understanding Permission Output

```bash
ls -l myfile.txt
```

Output example:
```
-rw-r--r-- 1 username groupname 1024 Mar 31 10:30 myfile.txt
```

- `-` = regular file (`d` = directory)
- `rw-` = owner can read and write
- `r--` = group can only read
- `r--` = others can only read

### Changing Permissions

```bash
# Make a file executable
chmod +x script.sh

# Make a file read-only
chmod -w myfile.txt

# Allow group to write
chmod g+w myfile.txt

# Common numeric patterns
chmod 644 myfile.txt  # rw-r--r--
chmod 755 script.sh   # rwxr-xr-x
```

::::::::::::::::::::::::::::::::::::::: callout

## Sharing Files with Collaborators

To share results with other Pomona researchers:
1. Put files in `/bigdata/labname` if it's lab work
2. Or give them read access to files in your home directory:
   ```bash
   chmod g+rx ~
   chmod g+r ~/results/myfile.txt
   ```
3. Share the path with collaborators

:::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge

## Challenge 1: Create a Project Structure

Create a directory structure for this workshop and practice file operations.

**Steps**:
1. Create directories:
   ```bash
   mkdir -p ~/workshop-0/data
   mkdir -p ~/workshop-0/results
   mkdir -p ~/workshop-0/scripts
   ```
2. Navigate into the directory: `cd ~/workshop-0`
3. Check your location: `pwd`
4. Create a test file: `echo "Hello Sagehen" > test.txt`
5. View it: `cat test.txt`
6. List everything: `ls -lah`
7. Return home: `cd ~`
8. List recursively: `ls -R workshop-0`

**Questions**:
- What path does `pwd` show when in workshop-0?
- How many directories did you create?

:::::::::::::::::::::::: solution

## Solution

`pwd` should show `/rhome/username/workshop-0`.

You created 4 directories total: `workshop-0` (main) plus `data`, `results`, `scripts` (subdirectories).

The command `ls -R workshop-0` shows the entire tree, including the `test.txt` file you created.

:::::::::::::::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Use `mkdir -p` to create nested directories in one command
- Be extremely careful with `rm -rf`; always list contents first
- Organize work into logical directories: projects, code, data, results
- File permissions control read, write, and execute access for owner, group, and others
- Use `chmod` to change permissions; share files via `/bigdata` or by adjusting group permissions

::::::::::::::::::::::::::::::::::::::::::::::
