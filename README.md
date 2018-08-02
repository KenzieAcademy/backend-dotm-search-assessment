# DOTM search

This is a real-world problem that I recently helped my brother with.  He works at a law firm where they still use MSWord, and probably always will.  Along with FAX machines.

The **DOTM**file extension is a Microsoft Word File template developed by Microsoft Corporation in its version of 2007 and 2010 document template files. ... It is identical to .DOCX and .DOCM file in which the M stands for macro and the X stands for XML.

The law firm makes extensive use of dotm template files to issue billing invoices.  These template files had hard-coded pricing amounts that needed to be updated manually.  But in their large collection of templates, they did not know which files contained pricing info.

By searching the dotm files for a '$' character, you can determine the subset of files that needs to be reviewed and updated.  However, the dotm file is not a plain text file that can simply be read into python and examined ... Use your Google search and Stack Overflow to find out how dotm files can be decoded in python.

Write a python program to iterate through each file in the dotm_files directory.

Print a list of only the dotm files that contain a '$' symbol in their original text.  

Here's a sneak peek inside a dotm file:

```
PK!��Ǉ�4\[Content\_Types\].xml �(��U�n�0��?������C��u�^)re� �N��\]=��m,�q| �;3;K�ί�L�� D�l�.�K�J��\]����.�Ȓ��\*Q99�Cd׋��櫽��P��9� �O�G�#b�<X�)\]0�7���X���>p�,��k���B)�&�'Zn�ڲ�=WS�Lx\_i)���U���+K-!��!� ���Tq�O�i'7�Ȇ1n�����z��.�3����A����.(���2$�鲮C2�IdF��V���Emj���m���vC�rљ��$RY|�����ma{\[z�j�kq4;�5��'��~��$�Hp��z�!#��F�W�^A�;����Ͳ,�yLQBϪ�`-ų�q6@$������c�<\*��/gS�|TH�Z��}=*�:��򨄒:���Mo�z�QHS x�=�50C�Ե��GS.�"��䩣Sj;�\]�H#�d����  
�ܼ���_��PK!���N_rels/.rels �(����JA���a�}7�  
"���H�w"����w̤ھ�� �P�^����O֛���;�<�aYՠ؛`G�kxm��PY�\[��g  
Gΰino�/<���<�1��ⳆA$>"f3��\\�ȾT��I S����������W����Y  
ig�@��X6_�\]7~  
f��ˉ�ao�.b*lI�r�j)�,l0�%��b�  
```
