# Leak report

The leak in main.c comes about primarily due to the allocation of the string array, which is never freed.  However, strings are themselves objects, and so need to be freed; the output files are added into an output string for each line, none of which are ever freed.  Similarly, none of the strings within the string array are freed at any point, although freeing the structure might free its contents.
