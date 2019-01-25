---
layout: essay
type: essay
title: Asking Questions Properly
# All dates must be YYYY-MM-DD format!
date: 2019-01-24
labels:
  - StackOverflow
  - TroubleShooting
---

## How To Ask Questions the Smart Way
Eric Stephen Raymond's essay on proper formatting of questions when asking the programming community comes off a little condescending and has a whiff of gatekeeping but that does not make the content of the writing any less true. The essay serves as a guide to newcomers to the programming community and how to approach the more senior members of the field in a way that will make them likely to help you. Raymond emphasizes the importance of trying to make all possible effort to solve your problem on your own and to show that effort when coming with your hat in your hand to an expert who can provide you some guidance. The importance of showing an effort before you "give up" and ask for outside help when cannot be understated. 

## Example of a Bad Question

[Bad Question Link](https://stackoverflow.com/questions/54360113/why-should-no-terminal-should-control-the-process-option-be-set-in-serial-port)

```C
fd = open("/dev/ttyUSB0",O_RDWR | O_NOCTTY);    
                               /* O_NOCTTY - No terminal will control the process   */
```
> "Why should we specify or not specify this option? What does it do and doesn't do?"

This is an example of a bad question. As of the time of this writing, this question has 0 upvotes and no answers with 15 views. The user asking has a handful of things contrary to what is taught in the above referenced essay the largest being context. This question seems to be asked in the middle of a much larger problem and without any context as to what the user is trying to accomplish, even an experienced programmer would probably not be able to give them a useful answer without giving an entire lesson on a the relevant concept. The second major issue is that the poster has shown no effort to research the solution to their problem on their own. No one wants to help those who won't make show any effort to help themselves. 

## Example of a Good Question

[Good Question Link](https://stackoverflow.com/questions/54356797/passing-host-ip-address-into-cmd-run-and-ini-files)


> I am currently trying to deploy Log-rhythm out into our environment that consists of 100+ Servers with the help of SaltStack:

> While I am able to copy files over to a Windows minion with the use of file.managed, I am facing some difficulty in the process getting the IP Address of the minion server and adding this both to the .ini file and cmd.run file. I would like to be able to do this for each minion that is connected to Salt:

> While running salt -G 'roles:logging' state.apply. I seem to be getting the following error: Rendering SLS 'base:pacakage-logrhythm' failed: Jinja variable 'dict object' has no attribute 'fqdn_ip4':

> UPDATE:

> I was able to resolve the issue within the ini files: by placing the following ClientAddress={{ grains['fqdn_ip4'][0] }}

> currently having issues with passing grains into the cmd.run section of the program


```
create_dir:
  file.directory:
    - name: C:\logrhythm

/srv/salt/logrhythm/proxy1.ini:
  file.managed:
    - source: salt://logrhythm/proxy1.ini
    - name: c:\logrhythm\proxy1.ini
    - template: jinja

/srv/salt/logrhythm/proxy2.ini:
  file.managed:
    - source: salt://logrhythm/proxy2.ini
    - name: c:\logrhythm\proxy2.ini
    - tempalte: jinja

LRS_File:
  file.managed:
    - name: c:\logrhythm\LRSystemMonitor_64_7.4.2.8003.exe
    - source: salt://logrhythm/LRSystemMonitor_64_7.4.2.8003.exe

LRS_Install:
  cmd.run:
    - name: 'LRSystemMonitor_64_7.4.2.8003.exe /s /v" /qn ADDLOCAL=System_Monitor,RT_FIM_Driver HOST=<> SERVERPORT=443 CLIENTADDRESS={{ grains[''fqdn_ip4''][0] }} CLIENTPORT=0"'
    - cwd: C:\logrhythm
```

This is an example of a well formatted question. The post begins with a brief description of the context of the scenario helping some one understand where this is going. The poster then specifically states what they would like to achieve along with the problem they are running into. They explain what they were trying to do and what the resulting error was. The user then updates the post when further working on the problem to show their progress along with further issues. It is clear from this post that the user is fully engaged in the problem solving process and their attitude will not be a hinderance to anyone who tries to get involved. This is the type of user that higher level programmers are likely to take the time to help according to the above referenced essay.

## Relating to a Different Field
In a past life, I worked as a senior nuclear plant supervisor leading operations on a submarine. The first thing always taught in our community is that no one owes you an answer to anything. When new operators encountered problems in their troubleshooting efforts, how willing senior personnel are to take time away from their responsibilities was entirely dependent on the willingness a junior person is to try to solve it on their own. It was more than a method of discouraging the mentality of feeling entitled to a questions answer, it was to aid in the learning process. I think back to when I was a junior operator and the problems I encountered and struggled with. The longer a problem takes to solve, the longer the lesson of finding the proper answer sticks with you. However, when you think of the times that you did not know how to evaluate a particular problem and a senior person simply gives you instructions you do not understand to fix the issue, the solutions and concepts behind why that worked are often forgotten quickly. We were surrounded by a wealth of technical information on every sort of specification or theory manual that could be tangentially related to our work available to us. For new people in the field it can be totally overwhelming to get tasked to explain or fix something you have little understanding of and have a database of conceptual information to dig through for an answer that won't even be a direct set of instructions. The only way you will learn most of it is to just start reading somewhere. 

When asked what the answer to a question was it was common practice to simply respond with a chapter number and title of a technical manual. Being on the receiving end of this is often frustrating because there were over 800 manuals in the plant each typically with about 500-1000 pages. It often felt like you were being messed with. After reading the chapter, you would usually come back still not fully understanding, only to be asked more questions about the topic by the senior person. It was through this process that a junior person will eventually arrive to the answer to their own question and also aquire a deeper understanding of the subject through having struggled for so long on it. This was crucial in the training of our engineers because it did not only teach you the answer to your question, it taught you the process to find the answer to your question. As the years go by and the senior members move on and leave the plant, you eventually find yourself having less and less people more senior than you to look to for answers. And one day you'll find yourself, in the middle of the ocean, responsible to tell the junior people what chapter to look in. By that time, you better know which chapter to look in because, if you can't solve the problem then no one can.

