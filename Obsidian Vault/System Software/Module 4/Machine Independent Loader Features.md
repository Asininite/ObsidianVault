### Automatic Library Search
- routines are fetched from library automatically as they are needed
- loader can automatically fetch routines into the program being loaded
- programmer give subroutine name in EXTREF

### Loader Options
- loaders have special language used to specify options

- [ ] INCLUDE program_name (library_name) 
      directs loader to read the program from a library 
- [ ] DELETE CSECT_name 
      delete control section
- [ ] CHANGE name1, name2 
	    external symbol name1 changed to name2 everywhere in object program
- [ ] LIBRARY MYLIB
	    use an external or defined library


