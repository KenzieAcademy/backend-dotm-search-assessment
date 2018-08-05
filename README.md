# DOTM search

## Skills Required
 - [Google-fu](https://english.stackexchange.com/questions/19967/what-does-google-fu-mean)
 - File I/O
 - Operating System (os)
 - Argument parsing
 - Importing standard library modules
 
<hr>

This is a real-world problem that I recently helped a friend with.  He works at a law firm where they still use MSWord, and probably always will.  Along with FAX machines.  He wanted to try his hand at some python programming.

The **DOTM** file extension is a Microsoft Word File template developed by Microsoft Corporation in its version of 2007 and 2010 document template files. ... It is identical to .DOCX and .DOCM file in which the M stands for macro and the X stands for XML.

The law firm makes use of .dotm template files to bill for services.  These template files had hard-coded pricing amounts that needed to be updated manually.  But in their large collection of templates, they did not know which files contained pricing info.

By searching the dotm files for a '$' character, you can determine the subset of files that need to be reviewed and updated.  However, the dotm file is not a plain text file that can simply be read into python and examined ... Use your Google search and Stack Overflow skills to find out how dotm files can be decoded in python.  NOTE: Timebox your DOTM format research.  If you have not figured out the DOTM file format in 20 minutes, ask an instructor for a hint.

## Your Task
Write a python program named `dotm_search.py`.  
Your program should accept two commandline arguments: first argument is the directory of .dotm files to scan, and the second argument is a text string to search for within each .dotm file. Example:
```
python dotm_search.py --dir "./dotm_files" --text "some text"
```

- Your program should print the full path name of each file that was found to contain the search text.  If the file contains multiple matches, just count it as a single match.
- For context, print a partial line of the dotm text that was found to contain the search text.  Limit the printed line to +/- 40 characters on each side of the matched text.  Example: `"...alculated on a per article basis (up to $500 each), the total false marking penal..."`
- Count the total number of file matches and display that as a final result.


## Some Tips
- Inside the `.dotm` file, the section to search is `'word/document.xml'`
- You may wish to investigate the [argparse](https://docs.python.org/2/howto/argparse.html) standard library.
- Use the python idiom `if __name__ == '__main__'` in your program.


Here's a sneak peek inside a dotm file:

```
PK!��Ǉ�4\[Content\_Types\].xml �(��U�n�0��?������C��u�^)re� �N��\]=��m,�q| �;3;K�ί�L�� D�l�.�K�J��\]����.�Ȓ��\*Q99�Cd׋��櫽��P��9� �O�G�#b�<X�)\]0�7���X���>p�,��k���B)�&�'Zn�ڲ�=WS�Lx\_i)���U���+K-!��!� ���Tq�O�i'7�Ȇ1n�����z��.�3����A����.(���2$�鲮C2�IdF��V���Emj���m���vC�rљ��$RY|�����ma{\[z�j�kq4;�5��'��~��$�Hp��z�!#��F�W�^A�;����Ͳ,�yLQBϪ�`-ų�q6@$������c�<\*��/gS�|TH�Z��}=*�:��򨄒:���Mo�z�QHS x�=�50C�Ե��GS.�"��䩣Sj;�\]�H#�d����  
�ܼ���_��PK!���N_rels/.rels �(����JA���a�}7�  
"���H�w"����w̤ھ�� �P�^����O֛���;�<�aYՠ؛`G�kxm��PY�\[��g  
Gΰino�/<���<�1��ⳆA$>"f3��\\�ȾT��I S����������W����Y  
ig�@��X6_�\]7~  
f��ˉ�ao�.b*lI�r�j)�,l0�%��b�  
```
