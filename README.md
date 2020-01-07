# translator-cpp

1. Introduction

This document contains report regarding the software created for programming assignment on laboratories of Fundamentals of Computer Programming. 

The exact task that was given:
Translator. Write a program that “translates” a text file by replacing words with corresponding words read from a separate dictionary. The dictionary should be read from a file once and later kept in memory.

2. Solution analysis

Given program needs two input text files in order to work correctly. These are: input file with translation database and input file with words that are going to be translated.

The program on its start checks whether the input files exists. If the result was positive the files are opened and words are read in the loop from given data base, otherwise a proper message is printed on the screen. Next, it checks for input file with text that is going to be translated and again shows proper message if one exists or not. If above steps were positive, program creates temporary file which will store the translations while the program is still working with replacing words from text source file using ones from input file with translations. After the loop is finished, the memory allocated to the dictionary structure is set free while the original text file is deleted and temporary file is renamed to match the name of file that was just deleted.

3. Internal specification

Function main() in a way given below:
- Uses load_dictionary() function to load translations into structure
- If previous step was successful, it opens which is going to be translated
- If previous step was successful, it creates temporary file for translations
- If previous step was successful, main() begins to work on it’s main loop
- After finishing the loop, the original text.txt file is deleted, temporary file is renamed to text.txt.

Main loop of the function works in a given way:
1. Before beginning of the main job of the program two arrays of a size of largest allowed word are created.
2. Arrays are cleared
3. First array is loaded with word from input file, if EOF is encountered, loop is finished
4. Loaded with data from structure with translations, input word and second array are provided further to get_translation(), where if:
	- true is returned, translation for given word was found and was loaded to the second array -> translation is written into the temporary file
	- false is returned, translation for given word was not found -> original word is written into the temporary file
5. At the end of the loop copy_white_chars() is used which copies all the white characters into the temporary file.
6. Return to the step 1.

4. External specification


This program is designed to work with UNIX command line. It can be run normally either using system GUI or command line (while having the path set to the same exact folder as the file we are trying to run): ./NameOfFile


For example:

Firstly we switch path to the folder containing the executable file using cd command:
cd /Users/admin1/Home/project

then we run the command

chmod +x project	- This command gives the system permission to execute the file later on.
After this we can finally run our program with this command
./project

In order for the program to read correctly the input file from file with translations called words.txt there must be blank letter between English and polish words. An example is given below:
<word1english> <word1polish>
<word2english> <word2polish>

Every other word contained within text.txt file has to be in the next line, as in the example below:
<word1english>
<word2english>

For correct input arguments the program will translate every input word and output translated ones instead of them. If there occurs any problem during that, error message will occur telling us what went wrong. 	

5. Testing the program


Working with correct input files

Translator.sh words.txt text.txt

The content of input file words.txt is:
cat kot
dog pies
tea herbata
paper papier
sugar cukier
water woda

The content of input file text.txt is:
cat
dog
tea
paper
sugar
water

The output of the program:
kot
pies
herbata
papier
cukier
woda


The program works correctly. 
