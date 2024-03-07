lexing -> token stream
parsing, macro expand -> ast
ast checking
ast generating -> IR A
    compile time code checking
    compile time code computing
hydrygen, desugar -> IR B
borrow checking, type checking, ..
optimization -> IR C
codegen, monomorphicsing -> LLVM IR 
