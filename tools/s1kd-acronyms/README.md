NAME
====

s1kd-acronyms - Manage acronyms in S1000D data modules

SYNOPSIS
========

    s1kd-acronyms -h?
    s1kd-acronyms [-dLptx] [-n <#>] [-o <file>] [-T <types>]
                  [<dmodule>...]
    s1kd-acronyms [-fL] [-i|-I|-!] [-m <acr>] [-o <file>] [<dmodule>...]
    s1kd-acronyms -D [-fL] [-o <file>] [<dmodule>...]

DESCRIPTION
===========

The *s1kd-acronyms* tool is used to manage acronyms in S1000D data modules in one of three ways:

-   Generate a list of unique acronyms used in all specified data modules.

-   Mark up acronyms automatically based on a specified list.

-   Remove acronym markup.

OPTIONS
=======

-D  
Remove acronym markup, flattening it to the acronym term.

-d  
Format XML output as an S1000D `<definitionList>`.

-f  
When marking up acronyms with the -m option, overwrite the input data modules instead of writing to stdout.

-h -?  
Show help/usage message.

-i -I -!  
Markup acronyms in interactive mode. If the specified acronyms list contains multiple definitions for a given acronym term, the tool will prompt the user with the context in which the acronym is used and present a list of the definitions for them to choose from.

When not in interactive mode, the first definition found will be used.

The -I option prompts for all acronyms, not just those with multiple definitions. This can be useful if some occurrences of the acronym term should be ignored.

The -! option will not prompt for acronyms, instead it will markup where acronyms are found using a &lt;`chooseAcronym`&gt; element, whose child elements are all possible acronyms matching the term. Another program can then use this as input to actually prompt the user.

-L  
Treat input (stdin or arguments) as lists of filenames of data modules to find or markup acronyms in, rather than data modules themselves.

-m &lt;acronyms&gt;  
Instead of listing acronyms, automatically markup acronyms given in the &lt;acronyms&gt; XML file in the specified data modules. Occurrences of the acronym term will be replaced in text with the `acronym` element in the list.

-n &lt;\#&gt;  
Minimum number of spaces after the term in pretty-printed text output.

-o &lt;file&gt;  
Output to &lt;file&gt; instead of stdout.

-p  
Pretty print text/XML acronym list output.

-T &lt;types&gt;  
Only search for acronyms with an attribute `acronymType` whose value is contained within the string &lt;types&gt;.

-t  
Format XML output as an S1000D `<table>`.

-x  
Use XML output instead of plain text.

--version  
Show version information.

&lt;dmodule&gt;...  
Data modules to find acronyms in. If none are specified, input is taken from stdin.

EXAMPLES
========

List all acronyms used in all data modules:

    $ s1kd-acronyms DMC-*.XML

Markup predefined acronyms in a data module:

    $ s1kd-acronyms -m acr.xml -f DMC-EX-A-00-00-00-00A-040A-D_EN-CA.XML

Unmarkup acronyms in a data module:

    $ s1kd-acronyms -D -f DMC-EX-A-00-00-00-00A-040A-D_EN-CA.XML