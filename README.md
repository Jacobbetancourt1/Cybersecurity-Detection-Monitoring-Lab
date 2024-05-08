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

<h1>Creating a Repository</h1>

  <p>On github website, lets create a new repository. There are a few ways to create this and is pretty straightforward</p>
<p align="center">
<br/>
<img src="https://imgur.com/2WfJshH.png" height="60%" width="60%" alt="CREATEING A REPOSITORY"/>
  <p>Lets name our new repository and make it pubic, you can name it whatever you want</p>
<p align="center">
<br/>
<img src="https://imgur.com/CTjSszw.png" height="60%" width="60%" alt="CREATEING A REPOSITORY"/>
  <p>Perfect! You created your new repository, below, lets follow <b>Create a new repository on the command line</b></p>
<p align="center">
<br/>
<img src="https://imgur.com/T8Emsz2.png" height="80%" width="80%" alt="CREATING A REPOSITORY"/>
  <p>Type <b>echo "# cloud-bootcamp" >> README.md</b> This not only creates the file README.md but echoes the content we made in the file also</p>
  <p>Lets verify this by typing: <b>cat README.md</b></p>
<p align="center">
<br/>
<img src="https://imgur.com/a7RpIK7.png" height="80%" width="80%" alt="CREATING A REPOSITORY"/>
  <p>Now lets initialize this repository inside the folder you created. For example, I'm currently in Desktop/Cloud/cloud-bootcamp</p>
  <p>Type: <b>git init</b> now run <b>git status</b>, This allows us to see what files are being tracked or not tracked; We can currently see README.md is not being tracked and has not been commited</p>
<p align="center">
<br/>
<img src="https://imgur.com/oDj1ejP.png" height="80%" width="80%" alt="CREATING A REPOSITORY"/>
  <p>Go ahead and type: <b>git add .</b> and run <b>git status</b> again. Notice that we have added this file and is now ready to be commited</p>
<p align="center">
<br/>
<img src="https://imgur.com/XL1Aecx.png" height="80%" width="80%" alt="CREATING A REPOSITORY"/>
  <p>I ran into an issue here, pretty much had to change the email at the bottom to my username on github</p>
<p align="center">
<br/>
<img src="https://imgur.com/QtkTHVP.png" height="80%" width="80%" alt="CREATING A REPOSITORY"/>
  <p>Type: <b>git config --global user.name "Your_Username"</b> and run <b>git commit -m "first commit readme"</b></p>
  <p>This command commits the file into the repository, and as best practice you should always add a description of why or what you did to this file using the <b>-m "description"</b> command</p>
  <p>Run <b>git status</b> and it should say nothing to commit which is fine; THEN type: <b>git branch -M main</b></p>
<p align="center">
<br/>
<img src="https://imgur.com/nTPRJ0r.png" height="80%" width="80%" alt="CREATING A REPOSITORY"/>
  <p>Go to github and click profile picture, then click settings</p>
<p align="center">
<br/>
<img src="https://imgur.com/VAVYray.png" height="10%" width="30%" alt="CREATING A REPOSITORY"/>
  <p>Then on bottom left click Developer Settings</p>
<p align="center">
<br/>
<img src="https://imgur.com/0mjGLZp.png" height="10%" width="30%" alt="CREATING A REPOSITORY"/>
  <p>Click Personal Access tokens and click Tokens (classic)</p>
<p align="center">
<br/>
<img src="https://imgur.com/CQreRPN.png" height="10%" width="30%" alt="CREATING A REPOSITORY"/>
  <p>Generate new token</p>
<p align="center">
<br/>
<img src="https://imgur.com/NbJ7Y9E.png" height="80%" width="80%" alt="CREATING A REPOSITORY"/>
<p>Type whatever name and make sure to check all scopes to give all access</p>
<p align="center">
<br/>
<img src="https://imgur.com/Q3kUwqw.png" height="80%" width="80%" alt="CREATING A REPOSITORY"/>
  <p>Now go to CLI and type: <b>git push -u origin main</b></p>
<p align="center">
<br/>
<img src="https://imgur.com/tFazgCP.png" height="80%" width="80%" alt="CREATING A REPOSITORY"/>
  <p>Go back to your recently created repository on github</p>
<p align="center">
<br/>
<img src="https://imgur.com/xlyPgUq.png" height="80%" width="80%" alt="CREATING A REPOSITORY"/>
  <p>On CLI type: <b>vim README.md</b></p>
  <p align="center">
<br/>
<img src="https://imgur.com/liY8Xgc.png" height="80%" width="80%" alt="CREATING A REPOSITORY"/>
  <p>press <b>i</b> and type in <b>updating file</b>. Press <b>escape</b> and type <b>:wq</b></p>
<p align="center">
<br/>
<img src="https://imgur.com/qjC0S0l.png" height="80%" width="80%" alt="CREATING A REPOSITORY"/>
  <p>Now that we updated the README.md file, lets verify, type: <b>git status</b> and you can see that it has been modified</p>
<p align="center">
<br/>
<img src="https://imgur.com/RYmncjN.png" height="80%" width="80%" alt="CREATING A REPOSITORY"/>
  <p>Lets go ahead and <b>git add .</b> the file that was recently updated and commit it to the repository with a description saying it was updated <b>git commit -m "updated readme"</b></p>
  <p>Now that is has been updated, lets push this to our recently created repository on github via CLI. Type: <b>git push</b></p>
<p align="center">
<br/>
<img src="https://imgur.com/ayOSZY1.png" height="80%" width="80%" alt="CREATING A REPOSITORY"/>
  <p>Go back to your github page and refresh the page, You can now see your newly updated repository you made!</p>
<p align="center">
<br/>
<img src="https://imgur.com/KlRaDhg.png" height="80%" width="80%" alt="CREATING A REPOSITORY"/>


<h1>Git Workflow</h1>




  
