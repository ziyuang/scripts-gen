ScriptsGen
====================

The script is aiming for a handy tool when you need to test your algorithm with different combinations of parameters. It helps to generate a script file for each parameter combination according to a template file, which is particularly suitable for subsequent parallel running.

Usage
--------------------
    $ scripts_gen.py --help
    usage: scripts_gen.py [-h] --template FILE --save-to FOLDER --param DICT
                          --format STRING [--open TOKEN] [--close TOKEN]
                          [--comment TOKEN] [--delete]
    
    Generate scripts from a template, by enumerating combinations of parameters.
    
    arguments:
      -h, --help        show this help message and exit
      --template FILE   The location of the template file.
      --save-to FOLDER  The destination folder for the scripts.
      --param DICT      All the parameters with their values as a dictionary,
                        where a value can be a list, or a file name that refers to
                        a file containing one parameter value per line. See
                        Python's dictionary literals
                        (http://docs.python.org/3/reference/expressions.html
                        #dictionary-displays).
      --format STRING   The format string for the file names of the scripts. See
                        Python's format string syntax
                        (http://docs.python.org/3/library/string.html#format-
                        string-syntax).
      --open TOKEN      The token that indicates the start of a template
                        identifier. (default: <%)
      --close TOKEN     The token that indicates the end of a template identifier.
                        (default: %>)
      --comment TOKEN   The token placed in the template file that treats the rest
                        of the line, which will be removed in the scripts, as a
                        comment. (default: ###)
      --delete          Delete the contents in the destination folder before
                        creation. (default: False)


Also, there are some built-in template identifiers for the components of the script names (see `example/template.txt`):

- `__FULL_PATH__`   : the full path of the current script
- `__DST_FOLDER__`  : the destination folder of this run, no trailing `'/'` or `'\\'`
- `__FILE__`        : the file name of the current script
- `__FILE_NO_EXT__` : the file name of the current script but without extension
- `__EXT__`         : the extension of the current script

In a word, 

    <%__FULL_PATH__%> == <%__DST_FOLDER__%>/<%__FILE__%> == <%__DST_FOLDER__%>/<%__FILE_NO_EXT__%>.<%__EXT__%>

Files
--------------------
- `scripts_gen.py`         : the script for Python 3.x users
- `scripts_gen_3to2.py`    : the script for Python 2.x users, where probably x>=6
- `example/command-line.sh`: an example of command line that shows how to invoke the script
- `example/template.txt`   : an example of template file
- `example/datasets.txt`   : an example of parameter input file for the example parameter `data`
