We want to create  open source tools which will achieve the slcing of c programs(maybe support more languages in the future). Our approaches are based on PDG&SDG(program dependency graph & system dependency graph).It is much alike the commercial products "CodeSurfer of GrammaTech Company",however at current time, it is at the stage of designing.
Our basic thoughts are as follows:
1.The c front end:
> i.the c preprocessor which will maintain the accurate source information
> ii.the c parser which will output the abstract syntax tree,luckily, we have the GCC now which dumps the abstract syntax tree alrealy which greatly facilitates the construction of AST in memory.
> iii.based on the AST(abstract syntax tree),we want to construct the CFG(control flow graph) which is annotated with the def sets and ref sets(basic concept in programming slicing).And we will have a dump represention for the CFG
> iv.based on the AST, we want to construct the call graph of the programs ,which will be used in the construction of SDG.Also, like the CFG, we will dump it out in the file.
2. The SDG Builder
> i.PDG builder.In this step, we will do the analysis of data and control dependency.Based on the above information, we build the PDG for each function
> ii.SDG builder.Based on call graph, we link each PDG, generating the SDG.


Difficulties:
1.pointer analysis
2.compound types:struct, union, arrays
3.function call:library call. Without the knowledges of information,we have to do more specific analysis