# Leak report

Without knowledge of C, I assumed that ALL variables, regardless of how (or where) they were created had to be __free()__'d.

My first implemenation was filled with hilarity as I __free()__'d everything under under the sun, causing a shocking number of errors when I attempted to compile.

This motivated me to read the documentation.

My second implemenation was to include __free(cleaned)__ in __is_clean__, directly before the return statement. This made a lot of sense, since this was the only pointer-variable that wasn't a paramater.

Further errors.

It took me quite a bit longer to realise that the empty string was messing the culprit. I messed around a bit, and concluded that __free()__ couldn't be called on an empty string.

My third implemenation correctly caught the use-case of an empty __cleaned__ variable.

I hope this explains my thinking, and excuses my lack of meaningfull commits.

~Liam Koehler (SirLich)
