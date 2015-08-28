Jacob O'Bryant <obryant666@gmail.com>

`add_docs.py` usage:

    usage: add_docs.py [-h] [-n NAME] [-w WIDTH] [-i] [-e ENVIRONMENT]
                       [-t TAB_WIDTH] [-v VERSION]
                       files [files ...]

    Adds in-code headers to c++ source files. Writes to stdout unless the -i
    option is included.

    positional arguments:
      files                 the input files

    optional arguments:
      -h, --help            show this help message and exit
      -n NAME, --name NAME  Your name (default: Jacob O'Bryant)
      -w WIDTH, --width WIDTH
                            The maximum line width (default: 74)
      -i, --in-place        modify file in place (default: False)
      -e ENVIRONMENT, --environment ENVIRONMENT
                            The environment (default: Intel Pentium PC, Arch
                            Linux, gcc 4.8)
      -t TAB_WIDTH, --tab-width TAB_WIDTH
                            The width of tabs (default: 4)
      -v VERSION, --version VERSION
                            The starting version (default: 1.0)

To get the usage for the other scripts, run

    name_of_script.py -h

Python 3.x must be installed.

NOTES
-----

`add_docs.py` has a few issues:

 - It may fail to insert some headers if it doesn't recognize the code
   formatting in the source file for the specific function/class opening line
   thing (whatever that's called).
 - It sometimes adds extra stuff to the calls/called by fields.
 - When parsing a function or class's code block, it counts the opening and
   close braces to know when to stop. It can be messed up if there are braces
   in comments or strings. So don't do that.

The first two problems can be fixed by tightening up the regular expressions.

The sample files were generated by the following commands:

    add_docs.py input.cpp > output.cpp
    list_driver.exe > driver_output.txt
    parse_test.py driver_output.txt parse_test_output.txt
    format_plan.py parse_test_output.txt format_plan_output.html

`final.cpp` is an example of what the output of `add_docs.py` should look
like after manual editing.

The output from `parse_test.py` can be edited if needed to make adjustments
to the final test plan.

LICENSE
-------

Open-source and stuff.
