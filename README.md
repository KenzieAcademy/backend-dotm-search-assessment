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
Your program should accept two cmdline arguments: First argument is the text to search. 
The second argument is an OPTIONAL directory of .dotm files to scan.  If this argument is omitted,
the default path to search is the current directory.
```
python dotm_search.py "some text" --dir "./dotm_files"
python dotm_search.py "other text"  # defaults to current dir search.
```

- Your program should print the full path name of each file that was found to contain the search text.  If the file contains multiple matches, just count it as a single match.
- For context, print a partial line of the dotm text that was found to contain the search text.  Limit the printed line to +/- 40 characters on each side of the matched text.  Example: `"...alculated on a per article basis (up to $500 each), the total false marking penal..."`
- Count the total number of file matches as well as total number of files searched, and display the results before exiting.


## Some Tips
- Disregard (do not search) files without a .dotm extension.  Don't count them as searched files either.
- Inside the `.dotm` file, the section to search is `'word/document.xml'`
- You may wish to investigate the [argparse](https://docs.python.org/2/howto/argparse.html) standard library.
- Use the python idiom `if __name__ == '__main__'` in your program.

## Sample Output
```
Searching directory ./dotm_files for text '$' ...
Match found in file ./dotm_files\G004.dotm
   ...t></w:r><w:r><w:t xml:space="preserve"> $5,000. </w:t></w:r><w:r w:rsidRPr="0049...
Match found in file ./dotm_files\L003.dotm
   ...></w:rPr><w:t>My current hourly rate is $</w:t></w:r><w:r w:rsidRPr="005F11CD"><...
Match found in file ./dotm_files\P015UST.dotm
   ...consideration of the sum of One Dollar ($1.00) and oth</w:t></w:r><w:bookmarkSta...
Match found in file ./dotm_files\P041US.dotm
   ...nt on your behalf for a total charge of $</w:t></w:r><w:r w:rsidRPr="00F931BE"><...
Match found in file ./dotm_files\P043USG.dotm
   ...alculated on a per article basis (up to $500 each), the total false marking pena...
Match found in file ./dotm_files\P453EP.dotm
   ...d cost of the printing and grant fee is $</w:t></w:r><w:r w:rsidRPr="002623D2"><...
Match found in file ./dotm_files\TM903US.dotm
   ...n of the sum of One and No/100 Dollars ($1.00) and other good and valuable consi...
Match found in file ./dotm_files\TM904US.dotm
   ...n of the sum of One and No/100 Dollars ($1.00) and other good and valuable consi...
Match found in file ./dotm_files\UM082US.dotm
   ...preserve"> money order in the amount of $</w:t></w:r><w:sdt><w:sdtPr><w:id w:val...
Total dotm files searched: 799
Total dotm files matched: 9
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
