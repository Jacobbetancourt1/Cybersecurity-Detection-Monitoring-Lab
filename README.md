<h1>Git & Architecture - In Progress</h1>
<p>Welcome to my Git & Architecture Project! I will be utilizing both WSL (<b>For windows machine, you will have to download this first</b>) and github website; We'll go over <i>GIT SSH ACCESS, CREATING A REPOSITORY, GIT WORKFLOW INSTALL AWS CLI, S3 BUCKET, IAM USER, and DESIGNING A BASIC ARCHITECTURE.</i></p>
<h2>What is a Git & Architecture</h2>
Git is a version control system that enables several developers to work together on the same project by tracking and managing changes to the codebase over time. Architecture in software refers to a system's high-level structure, including its components, relationships, and how they interact to meet certain needs.
<br>
<h1>GITHUB SSH ACCESS</h1>
<p>In order to get ssh access to github, first switch to a directory you prefer to be in; lets go ahead and generate an rsa key to your already created github account and paste your specific email in the CLI: <b>ssh-keygen -t rsa -b 4096 -C "your_email@example.com"</b></p>
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
<p align="center">
<br/>
<img src="https://imgur.com/IX3I9Gt.png" height="80%" width="80%" alt="GIT SSH ACCESS"/>
  <p>After this, lets go ahead and copy the keys to our clipboard (<b>I ran through an issue on WSL where it does not have this command</b>)</p>
<p align="center">
<br/>
<img src="https://imgur.com/iMiU84J.png" height="80%" width="80%" alt="GIT SSH ACCESS"/>
  <p>You can't install pbcopy directly, go ahead and type: <b>sudo apt install xclip</b></p>
<p align="center">
<br/>
<img src="https://imgur.com/BXahbkH.png" height="80%" width="80%" alt="GIT SSH ACCESS"/>
  <p>You should already by default have this in your sytem, type: <b>vim ~/.bashrc</b></p>
<p align="center">
<br/>
<img src="https://imgur.com/YxMhmMk.png" height="80%" width="80%" alt="GIT SSH ACCESS"/>
  <p>Press <b>i</b> and choose a spot and type in the command below: <b>alias pbcopy="xclip -sel clip"</b></p>
  <p>Afterwards press <b>escape</b> and type <b>:wq</b></p>
<p align="center">
<br/>
<img src="https://imgur.com/x0Ig8T1.png" height="80%" width="80%" alt="GIT SSH ACCESS"/>
  <p>Now go ahead and type: <b>source ~/.bashrc</b></p>
  <p>You should now be able to use this command <b>pbcopy < ~/.ssh/id_rsa.pub</b> to copy the keys to your clipboard</p>
<p align="center">
<br/>
<img src="https://imgur.com/esC1BA2.png" height="80%" width="80%" alt="GIT SSH ACCESS"/>
  <p>Good! now lets go to your github account utilizing google and sign in</p>
  <p>At the top right, click your profile picture and click settings</p>
<p align="center">
<br/>
<img src="https://imgur.com/4mjU8c9.png" height="5%" width="30%" alt="GIT SSH ACCESS"/>
  <p>Then on the left side of your screen, click SSH and GPG Keys</p>
<p align="center">
<br/>
<img src="https://imgur.com/tIbdprw.png" height="5%" width="30%" alt="GIT SSH ACCESS"/>
  <p>Click New SSH Keys</p>
<p align="center">
<br/>
<img src="https://imgur.com/OxhamwE.png" height="80%" width="80%" alt="GIT SSH ACCESS"/>
  <p>Remember when you typed <b>pbcopy < ~/.ssh/id_rsa.pub</b>, go ahead and paste inside key prompt and name the title whatever you want</p>
<p align="center">
<br/>
<img src="https://imgur.com/isCl0XD.png" height="80%" width="80%" alt="GIT SSH ACCESS"/>
  <p>Lastly go back to your CLI and type: <b>ssh -T git@github.com</b> type <b>yes</b> for footprint</p>
<p align="center">
<br/>
<img src="https://imgur.com/g7OazIb.png" height="80%" width="80%" alt="GIT SSH ACCESS"/>
  <p>That is how you we get SSH Access to our Github utilizing the CLI!</p>

