# Leak report

Without knowledge of C, I assumed that ALL variables, regardless of how (or where) they were created had to be __free()__'d.

My first implemenation was filled with hilarity as I __free()__'d everything under under the sun, causing a shocking number of errors when I attempted to compile.

This motivated me to read the documentation.

The main issue that needs to be understood is where memory leaks can happen. Non-pointer variables locally created in functions do not need to be freed, and neither do paramaters, regardless of their pointer status. This leaves local pointer values as possible memory leaks. Essentialy anywhere that __malloc__ or __calloc__ is called, you should expect to see a corresponding __free()__.

My implemenation was nothing more than free()ing the only variable that fit the above, with some attention paid to the empty-string case.
