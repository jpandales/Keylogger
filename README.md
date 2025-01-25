# Keylogger

## Objective

To develop a keylogger disguised as a harmless file on a user's desktop, designed to capture and record keystrokes while operating stealthily in the background. The project aims to demonstrate the dangers of deceptive malware and improve understanding of cybersecurity threats, highlighting the importance of user awareness and robust defense mechanisms.

### Skills Learned

- Malware Development & Analysis
- Prgramming and Scripting
- Ethical Hacking and Security Awareness
- Windows System Internals
- Development of critical thinking and problem-solving skills in cybersecurity.

### Tools Used

- Programming tools to create the main method done in Visual Studio code
- Windows Commands and WINRAR used to spoof the icon and file extension of the the program
- Python libraries found online, like keyboard and os

## Steps
1) The first step was to write the program that logged the users keys. This program was written in Visual Studio Code, and was built using nothing but two imported libraries and 27 lines of code.
   - The way this program works is that it first locates the path of the users [Documents] folder, then adds secret.txt into the path of that file. It is then stored in a variable to be used later on when making the secret.txt file. Afterwards, it opens this new files and sets it to append mode. The first thing it writes to this file is a key so that the contents later on are easier to read. The program then runs a while loop that runs forever. Inside this while loop, it uses the keyboard functions to track a keyboard event and store it into a variable. All keyboard events have two parts, a down stroke (when the key is pressed) and an up stroke (when the key is released). The program only logs the down stroke, as to not write events twice. It then checks if the event was a space, a backspace, a shift, or an enter, which it then changes it to shorter versions like space just becoming " ", backspace becoming "(bp)", shift becoming "(^)", and enter just making a new line. After every single write event, the program flushes the buffer to ensure that writing to the file is immediate. This was all it took to create a malicious program. (Refer to Ref 1 below to see the code for this program)
2) The second step was to convert the file from a .py program to an actaul program executable, i.e, a .exe file. This was also done in VS Code, using the in-software terminal, utilizing PyInstaller to consolidate the file into an executable.
3) Next, WINRAR was utilized to combine this file with a .png file, so that when the program is executed, it just displays the image attached to it, while secretly executing the code in the background. This also changes the icon of the program so it no longer has the default .exe file icon
   - The WINRAR Archive feature was used for this step. The way this works is that WINRAR combines these two files into one, and when it is clicked, it unpacks both the image and the program into a hidden folder, executing both. To the user, it looks like only one thing is happening, without any knowledge that a program just ran itself.
4) The last step was to spoof the name of the file so that it didnt have the .exe extension.
   - This was achieved by simply renaming the file to anything I wanted, but changing the extension type to a .scr. scr is an appopriate file extensions for a program because scr and exe are both just executable file formats, however scr files look less malicious. It is noted that a threat actor can also add the reverse of the file extension they want (png would be gnp) right before the real extension, and then insert a special unicode character called an RLO to reverse the fake extensions (png) and put it in place of the real file extension, which it now has taken the place of. (For example: To spoof my_file.scr, you would do my_file^gnp.scr, replacing ^ with the special Unicode character. This would then give you the output my_filescr.png)
     
### IMPORTANT
NONE OF THE DATA TAKEN FROM THIS PROGRAM GOES ANYWHERE BUT YOUR DEVICE. All the data logged within this program stays natively in your OWN document folder on your system, only you are able to see the secret.txt text file created on your system, and the data logged is just for educational purposes only. If you do wish to run this program on your system, one, I suggest running this on a VM (Virtual Machine) if you are worried about your system, and two, you will need to disable your antivirus software like Windows Defender and browser protection settings and accept all the warnings from your browser when downloading the file. For Windows Defender, you will only need to disable one setting, Real-time protection. Go to Windows Security > Virus & Threat protection Settings > Real-time protection > off. To terminate the file, just go to your task manager and look for the name for the name of the program or "keylogger.exe" and terminate the process. This ends the process and you can delete the secret.txt text file created in your system.  While this malware gets picked up by most antivirus softwares, there are a good number of malwares out there that don't, so remember to always be safe on the internet and to never download suspicious links. 

## Images
![image](https://github.com/user-attachments/assets/826eae88-fb74-4abb-aba6-ddacd5c63d39)
*Ref 1: Main.py file*

![image](https://github.com/user-attachments/assets/3854db12-e969-4f90-a608-60ee949fd560)
*Ref 2: The contents of the program when ran*


![image](https://github.com/user-attachments/assets/9554f932-1c20-41d6-915d-94c1548e0d84)

*Ref 3: The output file hidden in the documents folder*



