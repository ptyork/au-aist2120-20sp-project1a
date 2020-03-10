# Project 1a: English to Pig Latin Translator 

Pig Latin (aka, Ig-pay Atin-lay) is a classic "pseudo-language" that is based on a set of simple rules. Your job is to follow these rules to create a basic English to Pig Latin Translator. 

The script, `pltrans.py`, should: 

1. Open the file specified as the first argument to the script (see below)
2. Read the file one line at a time (i.e., for line in file)
3. Split the contents of each line into words (no argument passed to split so you split on whitespace)
4. Iterate over each word
    4a. Translate the word to Pig Latin 
    4b. Append the translated word (and a blank space)to a string
5. Print the translated string to the screen

Follow the Pig Latin translation rules outlined here: 

[How to Speak Pig Latin](https://www.wikihow.com/Speak-Pig-Latin) 

ONLY worry about the first two rules. Treat "y" as a standard consonant. Do NOT worry about consonant clusters, at least unless you want a challenge.

## CONSIDERATIONS 

1. If a "word" is empty or just whitespace, return nothing.

2. When translating a "word", be careful to check for punctuation and deal with that correctly. Especially words followed by periods, commas, etc. But also words starting or ending with quotation marks. Pay attention to periods, question marks, exclamation points, commas, quotation marks, semi-colons, and dashes. E.g.:
    - battle, ==> attle-bay,
        * __not__ attle,-bay
    - "rejoicing ==> "ejoicing-ray
        * __not__ rejoicing-"ay
    - tribulation," ==> ribulation-tay,"
        * __not__ ribulation,"-tay

3. If a "word" is __JUST__ punctuation (like em dash "--"), then just return the word untranslated.

4. If a "word" starts with a numeral (1,2,3,etc.) just return the word the word untranslated.

## HINTS 

1. The "arguments" to a python program are in the sys.argv list. The first element in the list is the name of the script and the rest are any additional words (arguments) added to the end. [See here for explanation](https://www.tutorialspoint.com/python/python_command_line_arguments.htm). The code needed may look as follows:
```
import sys

filename = sys.argv[1]
```

2. For consideration #2 above, you might start off your to_piglatin function by creating prefix and suffix strings. Start each as an empty string. Then "move" each punction character from the beginning of the word to the prefix string and any from the end to the suffix string. Then at the end, concatenate and return prefix + word + suffix. For example, the first part (moving the prefix characters) may look similar to:
```
    punctuation = '.?!,";-'
    prefix = ''
    while len(word) > 0 and word[0] in punctuation:
        prefix = prefix + word[0]
        word = word[1:]
```

## REQUIRED IMPLEMENTATION NOTES 

1. You MUST abstract your most useful logic by creating a function named to_piglatin that takes a "word" and returns the Pig Latin version (properly handling the punctuation issue outlined above). This function should be "called" as your step 4a above, which will make the main script much cleaner. In other words, the main part of your script should open the file, iterate over each line, split the line into words, and iterate over the words, and the following function MUST be defined in your script and called to translate each individual word: 

``` 
      def to_piglatin(word): 
          ... CHANGE WORD TO PIG LATIN ...
          return word
``` 

2. You MUST modify kennedy.txt, replacing John F. Kennedy's name with your own. JUST edit and save the file using VS code or another text editor. No Python code required here.

3. You MUST then translate kennedy.txt and redirect the output to pig_kennedy.txt. In other words, you should run `python pltrans.py kennedy.txt > pig_kennedy.txt`. This translated file should be in your final submission. __DO NOT WRITE TO A FILE INSIDE OF YOUR SCRIPT. ONLY READ AND PRINT. WRITING OCCURS HERE BY REDIRECTING OUTPUT.__

Note: If you do output redirection in Windows Powershell (the default shell for VS Code), it outputs writes the file using Unicode, which can cause issues. Use a standard Command Prompt (cmd.exe) if running this in Windows. Should not have any issues on Mac or Linux (and thus Mimir).

When done, be sure to test the heck out of this and then submit the __project1 directory__ in Mimir.

## OPTIONAL CHALLENGES 

1. Create a second version of the script, pltrans2.py. This version should import the to_piglatin function from pltrans (`from pltrans import to_piglatin`). Instead of looking for a file name as the first argument to the script, read in the text line-by-line from sys.stdin. This should allow you to run it interactively AND to pipe in text from another command (e.g., `type kennedy.txt | python pltrans2.py`). 

2. Correctly implement consonant clusters as well as the entire third rule from the How to Speak Pig Latin site.
