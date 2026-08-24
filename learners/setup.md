---
title: Setup
---

## Getting Started with Sagehen

This workshop assumes you have access to Sagehen, Pomona College's research computing cluster. By the end of this setup process, you'll have everything needed to connect and run your first job.

## Prerequisites

Before you start, you'll need:

1. **Pomona College credentials**: Your @pomona.edu email and password
2. **DUO authentication**: Access to your registered DUO account (for two-factor authentication)
3. **A computer with a terminal/SSH client**: See below for your operating system
4. **An HPC account on Sagehen**: request one via the [HPC account request form](https://servicedesk.pomona.edu/support/catalog/items/83) if you don't have one yet

## Step 1: Request an HPC Account

If you don't already have access to Sagehen, there are two ways to request an account:

1. **Preferred: submit the [HPC account request form](https://servicedesk.pomona.edu/support/catalog/items/83)** on the ITS Service Desk.

2. **Or email its-hpc@pomona.edu** with:
   - Your full name
   - Your @pomona.edu email address
   - Your department/major
   - Your faculty advisor or PI (if applicable)
   - A brief description of your research or coursework

Either way, the HPC team will respond within 1-2 business days confirming your account is ready

3. You'll receive instructions to complete your first login

## Step 2: Set Up SSH Access

SSH (Secure Shell) is how you connect to Sagehen. Choose your operating system below:

::::::::::::::::::::::::::::::::::::::: discussion

### SSH Setup for Your Operating System

SSH clients allow you to securely connect to Sagehen. Most systems have SSH built-in. Follow the instructions for your operating system.

:::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::: solution

### macOS

macOS includes SSH built-in. No installation needed!

**To connect to Sagehen:**
1. Open Terminal (Applications > Utilities > Terminal)
2. Type the command:

   ```bash
   ssh <myusername>@sagehen.hpc.pomona.edu
   ```
   Replace `username` with your Pomona username (the part before @pomona.edu)
3. On first connection, you'll see a prompt about the host key. Type `yes` to continue.
4. Enter your Pomona password
5. Complete DUO authentication (see Step 3 below)

:::::::::::::::::::::::::

:::::::::::::::: solution

### Windows 10/11

**Option A: PowerShell (Recommended)**

Windows 10 and 11 include SSH in PowerShell natively.
1. Open PowerShell (Windows key + X, select Windows PowerShell, or search "PowerShell")
2. Type:

   ```powershell
   ssh <myusername>@sagehen.hpc.pomona.edu
   ```
3. Enter your Pomona password
4. Complete DUO authentication

**Option B: Windows Subsystem for Linux (WSL)**

For a full Linux environment:
1. Open PowerShell as Administrator
2. Run: `wsl --install`
3. Restart your computer
4. Open WSL Terminal and follow the Linux instructions (below)

**Option C: PuTTY (Graphical)**

For a graphical interface:
1. Download PuTTY from https://www.putty.org/
2. Open PuTTY
3. In "Host Name", enter: `sagehen.hpc.pomona.edu`
4. Leave Port as 22
5. Click "Open"
6. Enter your username and password
7. Complete DUO authentication

:::::::::::::::::::::::::

:::::::::::::::: solution

### Linux

Linux includes SSH by default.
1. Open your terminal (usually Ctrl+Alt+T)
2. Type:
   ```bash
   ssh <myusername>@sagehen.hpc.pomona.edu
   ```
3. Enter your Pomona password
4. Complete DUO authentication

:::::::::::::::::::::::::

## Step 3: Complete DUO Authentication

When you connect to Sagehen, you'll see a DUO prompt:

```
Duo Authentication

1. Push (Duo app)
2. SMS
3. Backup Code

Passcode or option (1-3):
```

**Recommended: Use Push Notification**

1. Type `1` and press Enter
2. Look at your phone for a notification from "Duo Mobile"
3. Tap "Approve"
4. You'll be logged in!

**Alternative: Use SMS**

If you don't have the Duo app:

1. Type `2` and press Enter
2. Check your phone for a text with a 6-digit code
3. Type the code and press Enter
4. You'll be logged in

## Step 4: Test Your Connection

Once connected, you should see:
```
[<myusername>@sagehen ~]$
```

Verify everything works by running:

```bash
# Check your username
whoami

# Confirm you're on Sagehen
hostname

# View available modules
module avail | head -20
```

You should see your username, "sagehen", and a list of available software modules.

## Step 5: Set Up Your Environment (Optional but Recommended)

Create directories for organizing your work:

```bash
# Navigate to your home directory
cd

# Create directories for this workshop
mkdir -p workshop-0

# Verify they exist
ls -la
```

You can also customize your shell by editing `~/.bashrc`:

```bash
nano ~/.bashrc
```

Jump to end of file with Alt + / (or Ctrl+End)

Add these useful aliases at the end with Right-click or Ctrl+Shift+V:

```bash
# Useful aliases
alias ll='ls -lah'
alias sq='squeue -u $USER'
alias sa='sacct -u $USER'

# Useful module setup (optional). Loading without a version picks up the
# current default, so this keeps working when modules are updated:
module load miniconda3
```

Save with Ctrl+O, Enter, Ctrl+X.

## Troubleshooting Connection Issues

### "Permission denied (publickey)"

**Problem:** Can't log in

**Solutions:**
- Check your username is correct (not your email)
- Verify hostname: sagehen.hpc.pomona.edu
- Confirm your password is correct
- Ensure your Pomona account is active

### "DUO authentication failed"

**Problem:** DUO won't authenticate

**Solutions:**
- Ensure Duo Mobile app is installed and registered
- Check your phone volume isn't muted
- Try SMS option if push notification fails
- Verify your phone number is correct in Pomona account settings
- Contact Pomona IT if continuing to fail: (909) 621-8061 or servicedesk@pomona.edu

### "Connection timeout" or "Network unreachable"

**Problem:** Can't connect to Sagehen

**Solutions:**

- Check your internet connection
- Verify you can reach other Pomona services (email, Canvas)
- If off-campus, try using Pomona VPN
- Confirm your HPC account is active (check email from its-hpc@pomona.edu)

### Commands Not Found

**Problem:** After login, common commands don't work

**Solution:** Load modules! HPC clusters require loading software. First find
what's available:

```bash
module avail              # list everything available
module spider conda       # search for a specific package
```

Then load what you found, using the full name including the version:

```bash
module load miniconda3/py313_26.3.2-2
python --version
module list               # confirm what's loaded
```

## Next Steps

Once you can successfully connect to Sagehen:

1. Start with [Episode 1: What is HPC?](../episodes/01-what-is-hpc.md)
2. Work through each episode in order
3. Refer to the [Quick Reference Card](reference.md) as needed
4. Complete the challenges to build your skills

## Getting Help

If you're stuck:

- **Technical problems**: its-hpc@pomona.edu
- **Questions about this workshop**: Ask your instructor
- **Sagehen documentation**: Check [Quick Reference Card](reference.md)
- **General HPC questions**: its-hpc@pomona.edu

## Account Checklist

Before you begin the workshop, confirm you have:

- [ ] HPC account created
- [ ] Can connect via SSH
- [ ] Can complete DUO authentication
- [ ] See `[<myusername>@sagehen ~]$` prompt
- [ ] Commands like `whoami`, `hostname` work
- [ ] Can see modules with `module avail`
- [ ] Created workshop-0 directory

Once all these are checked, you're ready to start the workshop!

<!-- highlight <labname>/<myusername> placeholders in code blocks; remove if the varnish theme handles this natively -->
<script>(function(){var CSS='.sh-placeholder{color:#c2410c;font-weight:700}[data-bs-theme="dark"] .sh-placeholder,html.dark .sh-placeholder{color:#fdba74}@media (prefers-color-scheme: dark){[data-bs-theme="auto"] .sh-placeholder{color:#fdba74}}';var RX=/<labname>|<myusername>/g;function firstMatch(el){var w=document.createTreeWalker(el,NodeFilter.SHOW_TEXT,null),nodes=[],full='';while(w.nextNode()){nodes.push({n:w.currentNode,s:full.length});full+=w.currentNode.nodeValue;}RX.lastIndex=0;var m;while((m=RX.exec(full))){var s=m.index,e=s+m[0].length,inSpan=false,parts=[];for(var j=0;j<nodes.length;j++){var ns=nodes[j].s,ne=ns+nodes[j].n.nodeValue.length;if(ne<=s||ns>=e)continue;parts.push({node:nodes[j].n,a:Math.max(s-ns,0),b:Math.min(e-ns,nodes[j].n.nodeValue.length)});var p=nodes[j].n.parentNode;while(p&&p!==el){if(p.classList&&p.classList.contains('sh-placeholder')){inSpan=true;break;}p=p.parentNode;}}if(!inSpan&&parts.length)return parts;}return null;}function wrapParts(parts){for(var i=parts.length-1;i>=0;i--){var t=parts[i].node,txt=t.nodeValue,a=parts[i].a,b=parts[i].b;var span=document.createElement('span');span.className='sh-placeholder';span.textContent=txt.slice(a,b);var f=document.createDocumentFragment();if(a>0)f.appendChild(document.createTextNode(txt.slice(0,a)));f.appendChild(span);if(b<txt.length)f.appendChild(document.createTextNode(txt.slice(b)));t.parentNode.replaceChild(f,t);}}function run(){var st=document.createElement('style');st.textContent=CSS;document.head.appendChild(st);document.querySelectorAll('pre,code').forEach(function(el){var guard=0,parts;while((parts=firstMatch(el))&&guard++<500){wrapParts(parts);}});}if(document.readyState==='loading'){document.addEventListener('DOMContentLoaded',run);}else{run();}})();</script>
