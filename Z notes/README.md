# Z notes

# Schema cardinality
For a simple schema **master : DATABASE**, the field "master" leads to a single DATABASE.
https://www.cs.umd.edu/~mvz/handouts/z-manual.pdf

![image](https://user-images.githubusercontent.com/63869574/156020748-da18629d-119a-4ded-b6fe-933a1367f384.png)

For functions, **f: A->B** is a mapping every A to one B, similar to P(AxB), for example:
![image](https://user-images.githubusercontent.com/63869574/156034073-4724e087-7f69-4850-87b5-91a14686d9b7.png)


For sets, **p : PERSON** would mean the set of all PERSONs. E.g.:

![image](https://user-images.githubusercontent.com/63869574/156032939-8892d158-1118-42f1-b5fb-2a68b3f84475.png)


# Syntax error at symbol "\in"
When this error appears in fuzz, check : instead of \in.
