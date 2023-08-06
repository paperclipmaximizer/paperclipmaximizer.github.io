---
layout: post
slug: how i wrote mupl
category: cs-education
---

I recently had the opportunity to write a programming language in Racket. This was a challenging but rewarding experience, and it taught me a lot about the design and implementation of programming languages.

---
## The basics
Static checking is a type of code analysis that is performed on a program's source code. The goal of static checking is to find errors in the program's code before the program is run. Static checking can be used to find a variety of errors, including:
- Type errors: These errors occur when a variable is assigned a value of the wrong type.
- Semantic errors: These errors occur when the program's code does not make sense semantically. For example, a semantic error could occur if a function is called with the wrong number of arguments.
- Logical errors: These errors occur when the program's code does not do what it is supposed to do. For example, a logical error could occur if a loop is infinite.
Part of a programming languages definition is *what kind of static checking is done before code evaluation can be performed*. Notice the implication here, all programming languages to some degree do static type checking, static type checking itself refers to anything that is done to reject a program before it runs.

---
**The Importance of Concrete and Abstract Syntax**
In many programming languages, there is a distinction between concrete syntax and abstract syntax. Concrete syntax is the way that programs are written in human-readable form. Abstract syntax is the internal representation of programs that is used by the compiler or interpreter.

The distinction between concrete and abstract syntax allows for a separation of concerns. The concrete syntax can be designed to be easy for humans to read and write, while the abstract syntax can be designed to be efficient for computers to parse and execute.

Racket is a programming language that makes a distinction between concrete and abstract syntax. In Racket, programs are written in a concrete syntax that is based on the Scheme programming language. However, the abstract syntax of Racket programs is represented using a data structure called a **struct**.

The use of structs to represent the abstract syntax of Racket programs has several advantages. First, it makes it easy to define the semantics of Racket programs. The semantics of a program can be defined by simply specifying the operations that are performed on the structs that represent the program's abstract syntax.

Second, the use of structs makes it easy to implement a compiler or interpreter for Racket. The compiler or interpreter can simply parse the concrete syntax of a Racket program and then construct the corresponding structs that represent the program's abstract syntax.

Finally, the use of structs makes it easy to implement extensions to Racket. New features can be added to Racket by simply defining new structs that represent the new features.

The use of concrete and abstract syntax is a powerful tool that can be used to improve the design of programming languages. Racket is a good example of a language that makes extensive use of this technique.

In Racket, Scheme, LISP, Javascript, Ruby and countless other languages, something called an `eval` receives a list of concrete syntax that it then has to parse and then run. Racket's approach of having the concrete and abstract syntax is extreme convenient to anyone that wants to implement their own programming language.

---
**Racket as a Metaprogramming Platform**

Racket is a powerful programming language that can be used to create other programming languages. This is because Racket has a well-defined abstract syntax, and it provides a number of features that make it easy to create new languages.

One of the key features of Racket that makes it a good metaprogramming platform is the `eval` function. The `eval` function takes a list of expressions and evaluates them. This means that we can write functions that return lists of expressions, and then use the `eval` function to evaluate those expressions.

This makes it possible to create new programming languages by defining new syntactic forms and then using the `eval` function to evaluate expressions that use those new syntactic forms.

Another key feature of Racket that makes it a good metaprogramming platform is the fact that every Racket file is its own programming language. This is because every Racket file through function and procedure definitions expands the semantics its own file and any file connected to it. The language is essentially compose of Racket files calling other Racket files, the injection of "definition-meanings" is called macro expansion.

- **Macro expansion** is a process that replaces a macro call with the body of the macro. The body of the macro is a function that is evaluated to produce the desired output.
- **`define-syntax`** is a function that defines a new macro. The macro definition takes two arguments: the name of the macro and the body of the macro.

The two concepts are similar because they both allow you to define new syntactic forms. However, there are some important differences between them.

- **Macro expansion** is performed automatically by the compiler or interpreter. This means that you do not need to explicitly call the `macroexpand` function to expand a macro.
- **`define-syntax`** is a function that you have to call explicitly. This means that you have more control over when and how the macro is expanded.

Here is an example of how macro expansion and `define-syntax` can be used to define a new syntactic form:

```scheme
(define-syntax if
  (lambda (x y z)
    (if (eval x)
      y
      z)))

(if (> 1 0)
  "greater than"
  "less than or equal to")
```

In this example, the `if` macro is defined to take three arguments: the condition, the then-clause, and the else-clause. The macro expansion of the `if` macro is a function that takes the three arguments and returns the appropriate value.

The `define-syntax` function is used to define the `if` macro. The first argument to `define-syntax` is the name of the macro, which is `if` in this case. The second argument to `define-syntax` is the body of the macro, which is the function that is evaluated to produce the desired output.

---
**MUPL Syntax**

MUPL programs are written directly in Racket by using the constructors defined by the structs defined at the beginning of our file. The syntax for MUPL is as follows:
- If `s` is a Racket string, then `(var s)` is a MUPL expression (a variable use).
- If `n` is a Racket integer, then `(int n)` is a MUPL expression (a constant).
- If `e1` and `e2` are MUPL expressions, then `(add e1 e2)` is a MUPL expression (an addition).
- If `s1` and `s2` are Racket strings and `e` is a MUPL expression, then `(fun s1 s2 e)` is a MUPL expression (a function). In `e`, `s1` is bound to the function itself (for recursion) and `s2` is bound to the (one) argument. Also, `(fun #f s2 e)` is allowed for anonymous nonrecursive functions.
- If `e1`, `e2`, and `e3`, and `e4` are MUPL expressions, then `(ifgreater e1 e2 e3 e4)` is a MUPL expression. It is a conditional where the result is `e3` if `e1` is strictly greater than `e2` else the result is `e4`. Only one of `e3` and `e4` is evaluated.
- If `e1` and `e2` are MUPL expressions, then `(call e1 e2)` is a MUPL expression (a function call).
- If `s` is a Racket string and `e1` and `e2` are MUPL expressions, then `(mlet s e1 e2)` is a MUPL expression (a let expression where the value resulting `e1` is bound to `s` in the evaluation of `e2`).
- If `e1` and `e2` are MUPL expressions, then `(apair e1 e2)` is a MUPL expression (a pair-creator).
- If `e1` is a MUPL expression, then `(fst e1)` is a MUPL expression (getting the first part of a pair).
- If `e1` is a MUPL expression, then `(snd e1)` is a MUPL expression (getting the second part of a pair).
- `(aunit)` is a MUPL expression (holding no data, much like `()` in ML or `null` in Racket). Notice `(aunit)` is a MUPL expression, but `aunit` is not.
- If `e1` is a MUPL expression, then `(isaunit e1)` is a MUPL expression (testing for `(aunit)`).
- `(closure env f )` is a MUPL value where `f` is mupl function (an expression made from `fun`) and `env` is an environment mapping variables to values. Closures do not appear in source programs; they result from evaluating functions.

---
## What writing a Programming Language in Racket taught me

One of the things that I learned is that it is important to have a clear understanding of the goals of the language before you start writing it. In my case, I wanted to create a simple language that would be easy to understand. I also wanted to create a language that would be expressive and powerful.

Another thing that I learned is that it is important to have a good design for the language. This includes things like the syntax, the semantics, and the libraries that are provided with the language. I spent a lot of time thinking about these things, and I think that the design of MUPL is pretty good.

Of course, no language is perfect, and there are always things that could be improved. However, I am happy with the way that MUPL turned out, and I think that it is a good learning experience for anyone who is interested in the design and implementation of programming languages.

Here are some personal reflections on the experience of writing MUPL in Racket:

- **Racket is a great language for writing programming languages.** The Racket syntax is very clean and concise, and the Racket environment provides a lot of tools that make it easy to write and test code.
- **Writing a programming language is a lot of work.** There are a lot of things to think about, such as the syntax, the semantics, the libraries, and the implementation. It takes a lot of time and effort to get everything right.
- **It is rewarding to create something new.** It was satisfying to see MUPL come together, and it was even more satisfying to see other people using it and learning from it.

*I am grateful for the opportunity to have written MUPL and the excellent class Programming Languages Part B. I am excited to see what the future holds for my implementation of MUPL. I hope that MUPL will continue to be used and learned by people all over the world :-).*