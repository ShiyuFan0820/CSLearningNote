# File and Directory

**Exercise: Invitation Letter**
1. Given the example letter called `starting_letter.txt` in the folder called `Letters` and names file called `invited_names` in the folder called `Names`, both `Letters` and `Names` are in the directory named `Input`.
2. Batch generation of invitations for everyone in the name list.
3. The invitations are to be placed in a new folder called `ReadyToSend` in the folder called `Output`.
4. The file name of the invitations should be in this format: `letter_for_name.txt` (names in the name list).

_The example letter:_

<div align=center>
<img width="500" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/ad759f7c-8ece-4e45-b074-4846792b17be">
</div>

_The name list:_

<div align=center>
<img width="500" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/ba220d75-66e7-460b-b358-0325e2fa4350">
</div>

**The code is:**

Create a new directory `Output`, and create a new directory in the `Output` called `ReadyToSend`.

<div align=center>
<img width="500" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/cd5ec4a3-a0a0-4128-a656-95d88484978b">
</div>

```py
# Create a "main.py" python file to write the code, The path of it is the same with the "Input" and "Output".
NAME = "[name]"

with open("Input/Names/Invited_names.txt") as name_file: # Directory "Input" and the "main.py" are under the same directory the "./" can be omitted.
    name_list = name_file.readlines() # Access the name file and return the list format.

with open("Input/Letters/starting_letter.txt") as letter_file:
    content = letter_file.read() # Obtain the content of the example letter.
    for name in name_list:
        stripped_name = name.strip() # The name in the list format are automatically followed by a "/n" sign, so we need to just strip the name text from it.
        complete_letter = content.replace(NAME, stripped_name)
        with open(f"Output/ReadyToSend/letter_for_{stripped_name}.txt", mode="w") as invitation_file: 
            invitation_file.write(complete_letter) # When the mode is changed to "w", the text file will generate a new file if there is no file of the defined name, or replace everything with new content.

```

**Run the code:**

The letters are successfully generated.

<div align=center>
<img width="600" alt="image" src="https://github.com/ShiyuFan0820/PythonLearningNote/assets/149340606/131684af-7df9-4279-8ffd-2a845922a9ef">
</div>



