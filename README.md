# Windows-basic-commands-batchscript
Ex08-Windows-basic-commands-batchscript

# AIM:
To execute Windows basic commands and batch scripting

# DESIGN STEPS:

### Step 1:

Navigate to any Windows environment installed on the system or installed inside a virtual environment like virtual box/vmware 

### Step 2:

Write the Windows commands / batch file . Save each script in a file with a .bat extension. Ensure you have the necessary permissions to perform the operations. Adapt paths as needed based on your system configuration.
### Step 3:

Execute the necessary commands/batch file for the desired output. 




# WINDOWS COMMANDS:
## Exercise 1: Basic Directory and File Operations
Create a directory named "my-folder"
```
mkdir my-folder
```
<img width="1470" height="50" alt="Screenshot 2026-03-18 204804" src="https://github.com/user-attachments/assets/c92ff272-b59c-4cac-a83f-f4850196fe54" />

## COMMAND AND OUTPUT

Remove the directory "my-folder"
```
rmdir my-folder
```
<img width="1462" height="45" alt="Screenshot 2026-03-18 204825" src="https://github.com/user-attachments/assets/bd82d566-0e6c-4cb0-afab-34997bf4a91f" />

## COMMAND AND OUTPUT

Create the file Rose.txt
```
type nul > Rose.txt
```
<img width="1467" height="54" alt="Screenshot 2026-03-18 204943" src="https://github.com/user-attachments/assets/2c533ef8-7420-4946-adb9-6c587e165efc" />

## COMMAND AND OUTPUT

Create the file hello.txt using echo and redirection
```
echo Hello World > hello.txt
```
<img width="1119" height="45" alt="Screenshot 2026-03-18 204949" src="https://github.com/user-attachments/assets/86f0cc1e-a120-429a-9eed-056499f7ff1a" />

## COMMAND AND OUTPUT

Copy the file hello.txt into the file hello1.txt
```
copy hello.txt hello1.txt
```
<img width="857" height="62" alt="Screenshot 2026-03-18 204957" src="https://github.com/user-attachments/assets/c2351289-dca1-4f6b-a877-dab3d1f8dd2e" />

## COMMAND AND OUTPUT

Remove the file hello1.txt
```
del hello1.txt
```
<img width="1055" height="40" alt="Screenshot 2026-03-18 205015" src="https://github.com/user-attachments/assets/73c544c3-9ffc-4409-a0c2-8bd310b3149d" />

## COMMAND AND OUTPUT

List out the file hello1.txt in the current directory
```
dir hello1.txt
```
<img width="550" height="166" alt="Screenshot 2026-03-18 205046" src="https://github.com/user-attachments/assets/4423a77d-ab7f-4ad2-ab36-41d4f46c195f" />

## COMMAND AND OUTPUT

List out all the associated file extensions 
```
assoc
```
<img width="1099" height="605" alt="Screenshot 2026-03-18 205117" src="https://github.com/user-attachments/assets/956e9fd4-5566-4ef1-9fd0-378b857b8de4" />

## COMMAND AND OUTPUT
Compare the file hello.txt and rose.txt
```
fc hello.txt Rose.txt
```
<img width="533" height="169" alt="image" src="https://github.com/user-attachments/assets/19ab1fc8-1c33-4031-9cb7-085e7953a670" />

## Exercise 2: Advanced Batch Scripting
Create a batch file named on the desktop. The batch file need to have a variable assigned with a desired name for ex. name="John" and display as "Hello, John".

## Code
```
@echo off
set name=John
echo Hello, %name%
pause
```

## OUTPUT
<img width="527" height="82" alt="Screenshot 2026-03-18 211015" src="https://github.com/user-attachments/assets/c2bd3297-ddd0-4c1e-8733-293866affe75" />


Create a batch file  on the desktop that checks whether a user-input number is odd or not. The script should:
Prompt the user to enter a number.
Calculate the remainder when the number is divided by 2.
Display whether the number is odd or not.
Ask the user if they want to check another number.
Repeat the process if the user enters Y, and exit with a thank-you message if the user enters N.
Handle invalid inputs for the continuation prompt (Y/N) gracefully.

## Code
```
@echo off
:START
set /p num=Enter a number: 

set /a rem=%num% %% 2

if %rem%==1 (
    echo The number %num% is ODD
) else (
    echo The number %num% is NOT ODD
)

:CHOICE
set /p choice=Do you want to check another number? (Y/N): 

if /I "%choice%"=="Y" goto START
if /I "%choice%"=="N" goto END

echo Invalid choice. Please enter Y or N.
goto CHOICE
:END
echo Thank you!
pause
```

## OUTPUT
<img width="690" height="343" alt="Screenshot 2026-03-18 211200" src="https://github.com/user-attachments/assets/82b445f1-254d-4dc1-a346-5a72b3f2fe46" />


Write a batch file that uses a FOR loop to iterate over a sequence of numbers (1 to 5) and displays each number with the label Number:. The output should pause at the end.

## Code
```
@echo off
for %%i in (1 2 3 4 5) do (
    echo Number: %%i
)
pause
```

## OUTPUT
<img width="479" height="190" alt="Screenshot 2026-03-18 211230" src="https://github.com/user-attachments/assets/10684046-efe7-4b76-a188-5fb816a1a9c6" />


Write a batch script to check whether a file named sample.txt exists in the current directory. If the file exists, display the message sample.txt exists. Otherwise, display sample.txt does not exist. Pause the script at the end to view the result.

Instructions:
Use the IF EXIST conditional statement.
Make sure the script works for files located in the same directory as the batch file.
Use pause to keep the command window open after displaying the message.
Expected Output (if the file exists):

## Code
```
@echo off
if exist sample.txt (
    echo sample.txt exists
) else (
    echo sample.txt does not exist
)
pause
```

## OUTPUT
<img width="474" height="79" alt="Screenshot 2026-03-18 211257" src="https://github.com/user-attachments/assets/3d60369a-e58e-4430-b850-0d8f933508cc" />


Write a batch script that displays a simple menu with three options:
Say Hello – Displays the message Hello, World!
Create a File – Creates a file named newfile.txt with the content This is a new file
Exit – Exits the script with a goodbye message
The script should repeatedly display the menu until the user chooses to exit. Use goto statements to handle menu navigation.

## Code
```
@echo off
:MENU
cls
echo ===== MENU =====
echo 1. Say Hello
echo 2. Create a File
echo 3. Exit
echo =================
set /p choice=Enter your choice: 

if "%choice%"=="1" goto HELLO
if "%choice%"=="2" goto CREATE
if "%choice%"=="3" goto EXIT

echo Invalid choice!
pause
goto MENU

:HELLO
echo Hello, World!
pause
goto MENU

:CREATE
echo This is a new file > newfile.txt
echo File created successfully!
pause
goto MENU
:EXIT
echo Goodbye!
pause
exit
```

## OUTPUT
### Choice 1:
<img width="448" height="231" alt="Screenshot 2026-03-18 211326" src="https://github.com/user-attachments/assets/1fc705af-878c-4b6c-9d9d-6b99185cd3d2" />

### Choice 2:
<img width="451" height="241" alt="Screenshot 2026-03-18 211335" src="https://github.com/user-attachments/assets/44b20098-7392-48b8-a2b3-2d970fcf1bf4" />

### Choice 3:
<img width="474" height="222" alt="Screenshot 2026-03-18 211350" src="https://github.com/user-attachments/assets/cadac6a0-e06f-4ac7-b09d-d9627831399f" />


# RESULT:
The commands/batch files are executed successfully.

