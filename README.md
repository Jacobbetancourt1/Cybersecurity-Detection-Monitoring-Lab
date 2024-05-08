<h1>Git & Architecture - In Progress</h1>
<p>Welcome to my Git & Architecture Project! I will be utilizing both WSL (<b>For windows machine, you will have to download this first</b>) and github website; We'll go over <i>GIT SSH ACCESS, CREATING A REPOSITORY, GIT WORKFLOW INSTALL AWS CLI, S3 BUCKET, IAM USER, and DESIGNING A BASIC ARCHITECTURE.</i></p>
<h2>What is a Git & Architecture</h2>
Git is a version control system that enables several developers to work together on the same project by tracking and managing changes to the codebase over time. Architecture in software refers to a system's high-level structure, including its components, relationships, and how they interact to meet certain needs.
<br>
<h1>GITHUB SSH ACCESS</h1>
<p>In order to get ssh access to github, lets go ahead and generate an rsa key to your already created github account and paste your specific email in the CLI: <b>ssh-keygen -t rsa -b 4096 -C "your_email@example.com"</b></p>
<p align="center">
<br/>
<img src="https://imgur.com/v8rYNOq.png" height="80%" width="80%" alt="GIT SSH ACCESS"/>
  <p>Enable ssh agent in background with this command (Your PID will be different than mine): <b>eval "$(ssh-agent -s)"</b></p>
<p align="center">
<br/>
<img src="https://imgur.com/41HJy5m.png" height="80%" width="80%" alt="GIT SSH ACCESS"/>
  <p>Afterwards type: <b>ls ~/.ssh/</b> This will list your rsa files and config files, if you do not have a config file, type: <b>touch ~/.ssh/config</b></p>
<p align="center">
<br/>
<img src="https://imgur.com/1emfZuo.png" height="80%" width="80%" alt="GIT SSH ACCESS"/>
<p>Now lets go ahead and open the new config file: <b>open ~/.ssh/config</b> or <b>vim ~/.ssh/config</b></p>
<p align="center">
<br/>
<img src="https://imgur.com/I8MwS8W.png" height="80%" width="80%" alt="GIT SSH ACCESS"/>
  <p>Your file will be empty, go ahead and press <b>i</b> and start typing what you see above. Once done press <b>escape</b> and type <b>:wq</b></p>
  <p>Now lets go ahead and add our ssh access key to our ssh agent eval: <b>ssh-add ~/.ssh/id_rsa</b></p>


<h2>Downloading & Installing VMware Workstation Pro</h2>
<p>For the purpose of this lab, I’ll be using VMware Workstation 16 Pro as my hypervisor. I currently cannot afford the pro at this time so I will be using the 30 day free trial, but I assure you it is a very worthwhile investment.</p>
<br>
<p align="center">
<a href="https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html">Downloading VMware Workstation Player</a>
<img src="https://imgur.com/9UIlBHo.png" height="80%" width="80%" alt="VMware"/>
</p>
<h2>Configuring pfsense</h2>
<p>pfsense will be configured as a firewall to segment our private homelab network and will be only accessible from our Kali Linux machine.</p>
<br>
<p>Click “Create a New Virtual Machine” on VMware Workstation Homescreen.</p>
<br>
<p>Make sure “Typical (recommended)” is selected and click Next.</p>
<br>
<p align="center">
<img src="https://imgur.com/Uh8o283.png" height="40%" width="30%" alt="VMware"/>
</p>
<p>Click “Browse” and navigate to the folder where your pfsense file is located.</p>
<br>
