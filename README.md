# DOTM search

## Skills Required
 - [Google-fu](https://english.stackexchange.com/questions/19967/what-does-google-fu-mean)
 - File I/O
 - Operating System (os)
 - Argument parsing
 - Importing standard library modules
 
<hr>

This is a real-world problem that I recently helped a friend with.  He works at a law firm where they still use MSWord, and probably always will.  Along with FACSIMILE machines.  He wanted to try his hand at some python programming.

The **DOTM** file extension is a Microsoft Word File template developed by Microsoft Corporation in its version of 2007 and 2010 document template files. ... It is identical to .DOCX and .DOCM file in which the M stands for macro and the X stands for XML.

The law firm makes use of .dotm template files to bill for services.  These template files had hard-coded pricing amounts that needed to be updated manually.  But in their large collection of templates, they did not know which files contained pricing info.

By searching the dotm files for a '$' character, you can determine the subset of files that need to be reviewed and updated.  However, the dotm file is not a plain text file that can simply be read into python and examined ... Use your Google search and Stack Overflow skills to find out how dotm files can be decoded in python.  NOTE: Timebox your DOTM format research.  If you have not figured out the DOTM file format in 20 minutes, ask an instructor for a hint.

## Your Task
Write a python program named `dotm_search.py`.  
Your program should accept two cmdline arguments: First argument is the text to search for. 
The second argument is an OPTIONAL directory of .dotm files to scan.  If this argument is omitted,
the default path to search is the current directory.  NOTE that the optional directory `--dir [dotm-path]` actually includes two arguments (the option flag, and its value) but we are counting them as one combined argument key-value pair.
```
python dotm_search.py --dir ./dotm_files "$" 
python dotm_search.py "other text"
```

- Your program should print the full path name of each file that was found to contain the search text.  If the file contains multiple matches, just count it as a single match.
- For context, print a partial line of the dotm text that was found to contain the search text.  Limit the printed line to +/- 40 characters on each side of the matched text.  Example: `"...alculated on a per article basis (up to $500 each), the total false marking penal..."`
- Count the total number of file matches as well as total number of files searched, and display the results before exiting.


## Some Tips
- Disregard (do not search) files without a .dotm extension.  Don't count them as searched files either.
- Inside the `.dotm` file, the section to search is `'word/document.xml'`
- Use the [argparse](https://docs.python.org/2/howto/argparse.html) standard library to create a parser object within your program, and acquire the command line parameters from the parser instead of directly parsing sys.argv yourself.
- Use the python idiom `if __name__ == '__main__'` in your program.
- You DO NOT need to parse the contents into an XmlTree.  Just search the raw xml.
- You DO NOT need to count all occurrences of the search text.  Just count lines that contain at least one occurence of the search text.
- HINT: Have a look at this handy index of [File Signatures](https://en.wikipedia.org/wiki/List_of_file_signatures) that correspond to the starting bytes of various file formats.

## PR (Pull Request) Workflow for this Assignment
1. *Fork* this repository into your own personal github account.
2. Then *Clone* your own repo to your local development machine.
3. Create a separate branch named `dev`, and checkout the branch.
5. Commit your changes, then `git push` the branch back to your own github account.
5. From your own Github repo, create a pull request (PR) from your `dev` branch back to your own master.
6. Copy/Paste the URL **link to your PR** as your assignment submission.
7. Your grader will post code review comments inline with your code, in your github account. Be sure to respond to any comments and make requested changes. **RESUBMIT** a new link to your PR after making changes.  This is the code review iteration cycle.

## Sample Output
```
/Users/piero/Documents/github/kenzie/backend-dotm-search-assessment/dotm_search.py --dir ./dotm_files $
Searching directory ./dotm_files for text '$' ...
Match found in file ./dotm_files/P416NO.dotm
   ...tion fee for this case is approximately $ </w:t></w:r><w:r><w:rPr><w:highlight w...
Match found in file ./dotm_files/TM097IP.dotm
   ...:highlight w:val="yellow"/></w:rPr><w:t>$</w:t></w:r><w:r w:rsidR="00000C16"><w:...
Match found in file ./dotm_files/P620US.dotm
   ...><w:tab/><w:t>Credit Card Form PTO-2038 $</w:t></w:r><w:r w:rsidRPr="00D53D14"><...
Match found in file ./dotm_files/OT002US.dotm
   ...0D17087"><w:tab/><w:t>The filing fee of $</w:t></w:r><w:r w:rsidRPr="00D17087"><...
Match found in file ./dotm_files/TM250US.dotm
   ...an: (a) monitor their application (cost $</w:t></w:r><w:r w:rsidRPr="006716FE"><...

...
...
...

Match found in file ./dotm_files/P412RU.dotm
   ...:highlight w:val="yellow"/></w:rPr><w:t>$500.00</w:t></w:r><w:r><w:t xml:space="...
Match found in file ./dotm_files/TM035US.dotm
   ...:highlight w:val="yellow"/></w:rPr><w:t>$</w:t></w:r><w:r w:rsidR="00786608"><w:...
Match found in file ./dotm_files/P646US.dotm
   ...r><w:color w:val="000000"/></w:rPr><w:t>$</w:t></w:r><w:r w:rsidRPr="00F17D10"><...
Match found in file ./dotm_files/TM409IP.dotm
   ...:highlight w:val="yellow"/></w:rPr><w:t>$</w:t></w:r><w:r w:rsidR="00F95017"><w:...
Total dotm files searched: 799
Total dotm files matched: 72
```


Here's a sneak peek inside a dotm file:

```
PK!��Ǉ�4\[Content\_Types\].xml �(��U�n�0��?������C��u�^)re� �N��\]=��m,�q| �;3;K�ί�L�� D�l�.�K�J��\]����.�Ȓ��\*Q99�Cd׋��櫽��P��9� �O�G�#b�<X�)\]0�7���X���>p�,��k���B)�&�'Zn�ڲ�=WS�Lx\_i)���U���+K-!��!� ���Tq�O�i'7�Ȇ1n�����z��.�3����A����.(���2$�鲮C2�IdF��V���Emj���m���vC�rљ��$RY|�����ma{\[z�j�kq4;�5��'��~��$�Hp��z�!#��F�W�^A�;����Ͳ,�yLQBϪ�`-ų�q6@$������c�<\*��/gS�|TH�Z��}=*�:��򨄒:���Mo�z�QHS x�=�50C�Ե��GS.�"��䩣Sj;�\]�H#�d����  
�ܼ���_��PK!���N_rels/.rels �(����JA���a�}7�  
"���H�w"����w̤ھ�� �P�^����O֛���;�<�aYՠ؛`G�kxm��PY�\[��g  
Gΰino�/<���<�1��ⳆA$>"f3��\\�ȾT��I S����������W����Y  
ig�@��X6_�\]7~  
f��ˉ�ao�.b*lI�r�j)�,l0�%��b�  
```
