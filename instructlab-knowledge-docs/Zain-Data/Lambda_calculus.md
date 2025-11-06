# Lambda calculus

In mathematical logic, the lambda calculus (also written as λ-calculus) is a formal system for expressing computation based on function abstraction and application using variable binding and substitution. Untyped lambda calculus, the topic of this article, is a universal machine, a model of computation that can be used to simulate any Turing machine (and vice versa). It was introduced by the mathematician Alonzo Church in the 1930s as part of his research into the foundations of mathematics. In 1936, Church found a formulation which was logically consistent, and documented it in 1940.


## Definition


The lambda calculus consists of a language of lambda terms, that are defined by a certain formal syntax, and a set of transformation rules for manipulating the lambda terms. In BNF, the syntax is 
  
    
      
        e
        ::=
        x
        ∣
        λ
        x
        .
        e
        ∣
        e
        
        e
        ,
      
    
    {\displaystyle e::=x\mid \lambda x.e\mid e\,e,}
  
 where variables x,y,z range over an infinite set of names. Terms M,N,t,s,e,f range over all lambda terms. This corresponds to the following inductive definition:

 A variable x is itself a valid lambda term.
 An abstraction is a lambda term 
  
    
      
        (
        λ
        x
        .
        t
        )
      
    
    {\displaystyle (\lambda x.t)}
  
 where t is a lambda term and x is a variable,
 An application is a lambda term 
  
    
      
        (
        t
        s
        )
      
    
    {\displaystyle (ts)}
  
 where t and s are lambda terms.
A lambda term is syntactically valid if and only if it can be obtained by repeated application of these three rules. For convenience, parentheses can often be omitted when writing a lambda term—see Lambda calculus definition § Notation for details.
In the term 
  
    
      
        λ
        x
        .
        M
      
    
    {\displaystyle \lambda x.M}
  
, occurrences of x within M that are under the scope of this λ are termed bound; any occurrence of a variable not bound by an enclosing λ is free. FV(M) is the set of free variables of M. The notation 
  
    
      
        M
        [
        x
        :=
        N
        ]
      
    
    {\displaystyle M[x:=N]}
  
 denotes capture-avoiding substitution: substituting N for every free occurrence of x in M, while avoiding variable capture. This operation is defined inductively as follows:

  
    
      
        x
        [
        x
        :=
        N
        ]
        =
        N
      
    
    {\displaystyle x[x:=N]=N}
  
; 
  
    
      
        y
        [
        x
        :=
        N
        ]
        =
        y
      
    
    {\displaystyle y[x:=N]=y}
  
 if 
  
    
      
        y
        ≠
        x
      
    
    {\displaystyle y\neq x}
  
.

  
    
      
        (
        
          M
          
            1
          
        
        
          M
          
            2
          
        
        )
        [
        x
        :=
        N
        ]
        =
        (
        
          M
          
            1
          
        
        [
        x
        :=
        N
        ]
        )
        (
        
          M
          
            2
          
        
        [
        x
        :=
        N
        ]
        )
      
    
    {\displaystyle (M_{1}M_{2})[x:=N]=(M_{1}[x:=N])(M_{2}[x:=N])}
  
.

  
    
      
        (
        λ
        x
        .
        M
        )
        [
        x
        :=
        N
        ]
        =
        λ
        x
        .
        M
      
    
    {\displaystyle (\lambda x.M)[x:=N]=\lambda x.M}
  
.  (x is bound; no change)

  
    
      
        (
        λ
        y
        .
        M
        )
        [
        x
        :=
        N
        ]
        =
        λ
        y
        .
        (
        M
        [
        x
        :=
        N
        ]
        )
      
    
    {\displaystyle (\lambda y.M)[x:=N]=\lambda y.(M[x:=N])}
  
 if 
  
    
      
        y
        ∉
        F
        V
        (
        N
        )
      
    
    {\displaystyle y\notin FV(N)}
  
.
If 
  
    
      
        y
        ∈
        F
        V
        (
        N
        )
      
    
    {\displaystyle y\in FV(N)}
  
, first α-rename 
  
    
      
        λ
        y
        .
        M
      
    
    {\displaystyle \lambda y.M}
  
 to 
  
    
      
        λ
        
          y
          ′
        
        .
        M
        [
        y
        :=
        
          y
          ′
        
        ]
      
    
    {\displaystyle \lambda y'.M[y:=y']}
  
 with y' fresh to avoid name collisions, then continue as above.
There are several notions of "equivalence" and "reduction" that make it possible to reduce lambda terms to equivalent lambda terms.

α-conversion captures the intuition that the particular choice of a bound variable, in an abstraction, does not (usually) matter. If 
  
    
      
        y
        ∉
        F
        V
        (
        M
        )
      
    
    {\displaystyle y\notin FV(M)}
  
, then the terms 
  
    
      
        λ
        x
        .
        M
      
    
    {\displaystyle \lambda x.M}
  
 and 
  
    
      
        λ
        y
        .
        M
        [
        x
        :=
        y
        ]
      
    
    {\displaystyle \lambda y.M[x:=y]}
  
 are considered alpha-equivalent, written 
  
    
      
        λ
        x
        .
        M
        
          ≡
          
            α
          
        
        λ
        y
        .
        M
        [
        x
        :=
        y
        ]
      
    
    {\displaystyle \lambda x.M\equiv _{\alpha }\lambda y.M[x:=y]}
  
. The equivalence relation is the smallest congruence relation on lambda terms generated by this rule. For instance, 
  
    
      
        λ
        x
        .
        x
      
    
    {\displaystyle \lambda x.x}
  
 and 
  
    
      
        λ
        y
        .
        y
      
    
    {\displaystyle \lambda y.y}
  
 are alpha-equivalent lambda terms.
The β-reduction rule states that a β-redex, an application of the form 
  
    
      
        (
        λ
        x
        .
        t
        )
        s
      
    
    {\displaystyle (\lambda x.t)s}
  
, reduces to the term 
  
    
      
        t
        [
        x
        :=
        s
        ]
      
    
    {\displaystyle t[x:=s]}
  
. For example, for every 
  
    
      
        s
      
    
    {\displaystyle s}
  
, 
  
    
      
        (
        λ
        x
        .
        x
        )
        s
        →
        x
        [
        x
        :=
        s
        ]
        =
        s
      
    
    {\displaystyle (\lambda x.x)s\to x[x:=s]=s}
  
. This demonstrates that 
  
    
      
        λ
        x
        .
        x
      
    
    {\displaystyle \lambda x.x}
  
 really is the identity. Similarly, 
  
    
      
        (
        λ
        x
        .
        y
        )
        s
        →
        y
        [
        x
        :=
        s
        ]
        =
        y
      
    
    {\displaystyle (\lambda x.y)s\to y[x:=s]=y}
  
, which demonstrates that 
  
    
      
        λ
        x
        .
        y
      
    
    {\displaystyle \lambda x.y}
  
 is a constant function.
η-conversion expresses extensionality and converts between 
  
    
      
        λ
        x
        .
        f
        x
      
    
    {\displaystyle \lambda x.fx}
  
 and 
  
    
      
        f
      
    
    {\displaystyle f}
  
 whenever 
  
    
      
        x
      
    
    {\displaystyle x}
  
 does not appear free in 
  
    
      
        f
      
    
    {\displaystyle f}
  
. It is often omitted in many treatments of lambda calculus.
The term redex, short for reducible expression, refers to subterms that can be reduced by one of the reduction rules. For example, (λx.M) N is a β-redex in expressing the substitution of N for x in M. The expression to which a redex reduces is called its reduct; the reduct of (λx.M) N is M[x := N].


## Explanation and applications

Lambda calculus is Turing complete, that is, it is a universal model of computation that can be used to simulate any Turing machine. Its namesake, the Greek letter lambda (λ), is used in lambda expressions and lambda terms to denote binding a variable in a function.
Lambda calculus may be untyped or typed. In typed lambda calculus, functions can be applied only if they are capable of accepting the given input's "type" of data. Typed lambda calculi are strictly weaker than the untyped lambda calculus, which is the primary subject of this article, in the sense that typed lambda calculi can express less than the untyped calculus can. On the other hand, more things can be proven with typed lambda calculi. For example, in simply typed lambda calculus, it is a theorem that every evaluation strategy terminates for every simply typed lambda-term, whereas evaluation of untyped lambda-terms need not terminate (see below). One reason there are many different typed lambda calculi has been the desire to do more (of what the untyped calculus can do) without giving up on being able to prove strong theorems about the calculus.
Lambda calculus has applications in many different areas in mathematics, philosophy, linguistics, and computer science. Lambda calculus has played an important role in the development of the theory of programming languages. Functional programming languages implement lambda calculus. Lambda calculus is also a current research topic in category theory.


## History

Lambda calculus was introduced by mathematician Alonzo Church in the 1930s as part of an investigation into the foundations of mathematics. The original system was shown to be logically inconsistent in 1935 when Stephen Kleene and J. B. Rosser developed the Kleene–Rosser paradox.
Subsequently, in 1936 Church isolated and published just the portion relevant to computation, what is now called the untyped lambda calculus. In 1940, he also introduced a computationally weaker, but logically consistent system, known as the simply typed lambda calculus.
Until the 1960s when its relation to programming languages was clarified, the lambda calculus was only a formalism. Thanks to Richard Montague and other linguists' applications in the semantics of natural language, the lambda calculus has begun to enjoy a respectable place in both linguistics and computer science.


### Origin of the λ symbol

There is some uncertainty over the reason for Church's use of the Greek letter lambda (λ) as the notation for function-abstraction in the lambda calculus, perhaps in part due to conflicting explanations by Church himself. According to Cardone and Hindley (2006):

By the way, why did Church choose the notation "λ"? In [an unpublished 1964 letter to Harald Dickson] he stated clearly that it came from the notation "
  
    
      
        
          
            
              x
              ^
            
          
        
      
    
    {\displaystyle {\hat {x}}}
  
" used for class-abstraction by Whitehead and Russell, by first modifying "
  
    
      
        
          
            
              x
              ^
            
          
        
      
    
    {\displaystyle {\hat {x}}}
  
" to "
  
    
      
        ∧
        x
      
    
    {\displaystyle \land x}
  
" to distinguish function-abstraction from class-abstraction, and then changing "
  
    
      
        ∧
      
    
    {\displaystyle \land }
  
" to "λ" for ease of printing.
This origin was also reported in [Rosser, 1984, p.338]. On the other hand, in his later years Church told two enquirers that the choice was more accidental: a symbol was needed and λ just happened to be chosen.

Dana Scott has also addressed this question in various public lectures.
Scott recounts that he once posed a question about the origin of the lambda symbol to Church's former student and son-in-law John W. Addison Jr., who then wrote his father-in-law a postcard:

Dear Professor Church,
Russell had the iota operator, Hilbert had the epsilon operator. Why did you choose lambda for your operator?

According to Scott, Church's entire response consisted of returning the postcard with the following annotation: "eeny, meeny, miny, moe".


## Motivation

Computable functions are a fundamental concept within computer science and mathematics. The lambda calculus provides simple semantics for computation which are useful for formally studying properties of computation. The lambda calculus incorporates two simplifications that make its semantics simple.
The first simplification is that the lambda calculus treats functions "anonymously"; it does not give them explicit names. For example, the function

  
    
      
        
          s
          q
          u
          a
          r
          e
          _
          s
          u
          m
        
        ⁡
        (
        x
        ,
        y
        )
        =
        
          x
          
            2
          
        
        +
        
          y
          
            2
          
        
      
    
    {\displaystyle \operatorname {square\_sum} (x,y)=x^{2}+y^{2}}
  

can be rewritten in anonymous form as

  
    
      
        (
        x
        ,
        y
        )
        ↦
        
          x
          
            2
          
        
        +
        
          y
          
            2
          
        
      
    
    {\displaystyle (x,y)\mapsto x^{2}+y^{2}}
  

(which is read as "a tuple of x and y is mapped to 
  
    
      
        
          x
          
            2
          
        
        +
        
          y
          
            2
          
        
      
    
    {\textstyle x^{2}+y^{2}}
  
"). Similarly, the function

  
    
      
        id
        ⁡
        (
        x
        )
        =
        x
      
    
    {\displaystyle \operatorname {id} (x)=x}
  

can be rewritten in anonymous form as

  
    
      
        x
        ↦
        x
      
    
    {\displaystyle x\mapsto x}
  

where the input is simply mapped to itself.
The second simplification is that the lambda calculus only uses functions of a single input. An ordinary function that requires two inputs, for instance the 
  
    
      
        
          s
          q
          u
          a
          r
          e
          _
          s
          u
          m
        
      
    
    {\textstyle \operatorname {square\_sum} }
  
 function, can be reworked into an equivalent function that accepts a single input, and as output returns another function, that in turn accepts a single input. For example,

  
    
      
        (
        x
        ,
        y
        )
        ↦
        
          x
          
            2
          
        
        +
        
          y
          
            2
          
        
      
    
    {\displaystyle (x,y)\mapsto x^{2}+y^{2}}
  

can be reworked into

  
    
      
        x
        ↦
        (
        y
        ↦
        
          x
          
            2
          
        
        +
        
          y
          
            2
          
        
        )
      
    
    {\displaystyle x\mapsto (y\mapsto x^{2}+y^{2})}
  

This method, known as currying, transforms a function that takes multiple arguments into a chain of functions each with a single argument.
Function application of the 
  
    
      
        
          s
          q
          u
          a
          r
          e
          _
          s
          u
          m
        
      
    
    {\textstyle \operatorname {square\_sum} }
  
 function to the arguments (5, 2), yields at once

  
    
      
        (
        (
        x
        ,
        y
        )
        ↦
        
          x
          
            2
          
        
        +
        
          y
          
            2
          
        
        )
        (
        5
        ,
        2
        )
      
    
    {\textstyle ((x,y)\mapsto x^{2}+y^{2})(5,2)}
  

  
    
      
        =
        
          5
          
            2
          
        
        +
        
          2
          
            2
          
        
      
    
    {\textstyle =5^{2}+2^{2}}
  

  
    
      
        =
        29
      
    
    {\textstyle =29}
  
,
whereas evaluation of the curried version requires one more step

  
    
      
        
          
            (
          
        
        
          
            (
          
        
        x
        ↦
        (
        y
        ↦
        
          x
          
            2
          
        
        +
        
          y
          
            2
          
        
        )
        
          
            )
          
        
        (
        5
        )
        
          
            )
          
        
        (
        2
        )
      
    
    {\textstyle {\Bigl (}{\bigl (}x\mapsto (y\mapsto x^{2}+y^{2}){\bigr )}(5){\Bigr )}(2)}
  

  
    
      
        =
        (
        y
        ↦
        
          5
          
            2
          
        
        +
        
          y
          
            2
          
        
        )
        (
        2
        )
      
    
    {\textstyle =(y\mapsto 5^{2}+y^{2})(2)}
  
 // the definition of 
  
    
      
        x
      
    
    {\displaystyle x}
  
 has been used with 
  
    
      
        5
      
    
    {\displaystyle 5}
  
 in the inner expression. This is like β-reduction.

  
    
      
        =
        
          5
          
            2
          
        
        +
        
          2
          
            2
          
        
      
    
    {\textstyle =5^{2}+2^{2}}
  
 // the definition of 
  
    
      
        y
      
    
    {\displaystyle y}
  
 has been used with 
  
    
      
        2
      
    
    {\displaystyle 2}
  
. Again, similar to β-reduction.

  
    
      
        =
        29
      
    
    {\textstyle =29}
  

to arrive at the same result.
In lambda calculus, functions are taken to be 'first class values', so functions may be used as the inputs, or be returned as outputs from other functions. For example, the lambda term 
  
    
      
        λ
        x
        .
        x
      
    
    {\displaystyle \lambda x.x}
  
 represents the identity function, 
  
    
      
        x
        ↦
        x
      
    
    {\displaystyle x\mapsto x}
  
. Further, 
  
    
      
        λ
        x
        .
        y
      
    
    {\displaystyle \lambda x.y}
  
 represents the constant function 
  
    
      
        x
        ↦
        y
      
    
    {\displaystyle x\mapsto y}
  
, the function that always returns 
  
    
      
        y
      
    
    {\displaystyle y}
  
, no matter the input. As an example of a function operating on functions, the function composition can be defined as 
  
    
      
        λ
        f
        .
        λ
        g
        .
        λ
        x
        .
        (
        f
        (
        g
        x
        )
        )
      
    
    {\displaystyle \lambda f.\lambda g.\lambda x.(f(gx))}
  
.


## Normal forms and confluence


It can be shown that β-reduction is confluent when working up to α-conversion (i.e. we consider two normal forms to be equal if it is possible to α-convert one into the other). If repeated application of the reduction steps eventually terminates, then by the Church–Rosser theorem it will produce a unique β-normal form. However, the untyped lambda calculus as a rewriting rule under β-reduction is neither strongly normalising nor weakly normalising; there are terms with no normal form such as Ω.
Considering individual terms, both strongly normalising terms and weakly normalising terms have a unique normal form. For strongly normalising terms, any reduction strategy is guaranteed to yield the normal form, whereas for weakly normalising terms, some reduction strategies may fail to find it.


## Encoding datatypes


The basic lambda calculus may be used to model arithmetic, Booleans, data structures, and recursion, as illustrated in the following sub-sections i, ii, iii, and § iv.


### Arithmetic in lambda calculus
There are several possible ways to define the natural numbers in lambda calculus, but by far the most common are the Church numerals, which can be defined as follows:

0 := λf.λx.x
1 := λf.λx.f x
2 := λf.λx.f (f x)
3 := λf.λx.f (f (f x))
and so on. Or using an alternative syntax allowing multiple uncurried arguments to a function:

0 := λfx.x
1 := λfx.f x
2 := λfx.f (f x)
3 := λfx.f (f (f x))
A Church numeral is a higher-order function—it takes a single-argument function f, and returns another single-argument function. The Church numeral n is a function that takes a function f as argument and returns the n-th composition of f, i.e. the function f composed with itself n times. This is denoted f(n) and is in fact the n-th power of f (considered as an operator); f(0) is defined to be the identity function. Functional composition is associative, and so, such repeated compositions of a single function f obey two laws of exponents, f(m)∘f(n) = f(m+n) and (f(n))(m) = f(m*n), which is why these numerals can be used for arithmetic. (In Church's original lambda calculus, the formal parameter of a lambda expression was required to occur at least once in the function body, which made the above definition of 0 impossible.)
One way of thinking about the Church numeral n, which is often useful when analyzing programs, is as an instruction 'repeat n times'. For example, using the PAIR and NIL functions defined below, one can define a function that constructs a (linked) list of n elements all equal to x by repeating 'prepend another x element' n times, starting from an empty list. The lambda term 

λn.λx.n (PAIR x) NIL
creates, given a Church numeral n and some x, a sequence of n applications

PAIR x (PAIR x...(PAIR x NIL)...)
By varying what is being repeated, and what argument(s) that function being repeated is applied to, a great many different effects can be achieved.
We can define a successor function, which takes a Church numeral n and returns its successor n + 1 by performing one additional application of the function f it is supplied with, where (n f x) means "n applications of f starting from x":

SUCC := λn.λf.λx.f (n f x)
Because the m-th composition of f composed with the n-th composition of f gives the m+n-th composition of f, f(m)∘f(n) = f(m+n), addition can be defined as 

PLUS := λm.λn.λf.λx.m f (n f x)
PLUS can be thought of as a function taking two natural numbers as arguments and returning a natural number; it can be verified that

PLUS 2 3
and

5
are beta-equivalent lambda expressions. Since adding m to a number can be accomplished by repeating the successor operation m times, an alternative definition is:

PLUS′ := λm.λn.m SUCC n 
Similarly, following (f(n))(m) = f(m*n), multiplication can be defined as

MULT := λm.λn.λf.m (n f)
Thus multiplication of Church numerals is simply their composition as functions. Alternatively

MULT′ := λm.λn.m (PLUS n) 0
since multiplying m and n is the same as adding n repeatedly, m times, starting from zero.
Exponentiation, being the repeated multiplication of a number with itself, translates as a repeated composition of a Church numeral with itself, as a function. And repeated composition is what Church numerals are: 

POW := λb.λn.n b
Alternatively here as well,

POW′ := λb.λn.n (MULT b) 1
Simplifying, it becomes

POW′′ := λb.λn.λf.n b f
but that is just an eta-expanded version of POW we already have, above.
The predecessor function, specified by two equations PRED (SUCC n) = n and PRED 0 = 0, is considerably more involved. The formula

PRED := λn.λf.λx.n (λg.λh.h (g f)) (λu.x) (λu.u)
can be validated by showing inductively that if T denotes (λg.λh.h (g f)), then T(n)(λu.x) = (λh.h(f(n−1)(x))) for n > 0. Two other definitions of PRED are given below, one using conditionals and the other using pairs. With the predecessor function, subtraction is straightforward. Defining

SUB := λm.λn.n PRED m,
SUB m n yields m − n when m > n and 0 otherwise.


### Logic and predicates
By convention, the following two definitions (known as Church Booleans) are used for the Boolean values TRUE and FALSE:

TRUE := λx.λy.x
FALSE := λx.λy.y
Then, with these two lambda terms, we can define some logic operators (these are just possible formulations; other expressions could be equally correct):

AND := λp.λq.p q p
OR := λp.λq.p p q
NOT := λp.p FALSE TRUE
IFTHENELSE := λp.λa.λb.p a b
We are now able to compute some logic functions, for example:

AND TRUE FALSE
≡ (λp.λq.p q p) TRUE FALSE →β TRUE FALSE TRUE
≡ (λx.λy.x) FALSE TRUE →β FALSE
and we see that AND TRUE FALSE is equivalent to FALSE.
A predicate is a function that returns a Boolean value. The most fundamental predicate is ISZERO, which returns TRUE if its argument is the Church numeral 0, but FALSE if its argument were any other Church numeral:

ISZERO := λn.n (λx.FALSE) TRUE
The following predicate tests whether the first argument is less-than-or-equal-to the second:

LEQ := λm.λn.ISZERO (SUB m n),
and since m = n, if LEQ m n and LEQ n m, it is straightforward to build a predicate for numerical equality.
The availability of predicates and the above definition of TRUE and FALSE make it convenient to write "if-then-else" expressions in lambda calculus. For example, the predecessor function can be defined as:

PRED := λn.n (λg.λk.ISZERO (g 1) k (PLUS (g k) 1)) (λv.0) 0
which can be verified by showing inductively that n (λg.λk.ISZERO (g 1) k (PLUS (g k) 1)) (λv.0) is the add n − 1 function for n > 0.


### Pairs
A pair (2-tuple) can be defined in terms of TRUE and FALSE, by using the Church encoding for pairs. For example, PAIR encapsulates the pair (x,y), FIRST returns the first element of the pair, and SECOND returns the second.

PAIR := λx.λy.λf.f x y
FIRST := λp.p TRUE
SECOND := λp.p FALSE
NIL := λx.TRUE
NULL := λp.p (λx.λy.FALSE)
A linked list can be defined as either NIL for the empty list, or the PAIR of an element and a smaller list. The predicate NULL tests for the value NIL. (Alternatively, with NIL := FALSE, the construct l (λh.λt.λz.deal_with_head_h_and_tail_t) (deal_with_nil) obviates the need for an explicit NULL test).
As an example of the use of pairs, the shift-and-increment function that maps (m, n) to (n, n + 1) can be defined as

Φ := λx.PAIR (SECOND x) (SUCC (SECOND x))
which allows us to give perhaps the most transparent version of the predecessor function:

PRED := λn.FIRST (n Φ (PAIR 0 0)).


## Additional programming techniques

There is a considerable body of programming idioms for lambda calculus. Many of these were originally developed in the context of using lambda calculus as a foundation for programming language semantics, effectively using lambda calculus as a low-level programming language. Because several programming languages include the lambda calculus (or something very similar) as a fragment, these techniques also see use in practical programming, but may then be perceived as obscure or foreign.


### Named constants
In lambda calculus, a library would take the form of a collection of previously defined functions, which as lambda-terms are merely particular constants. The pure lambda calculus does not have a concept of named constants since all atomic lambda-terms are variables, but one can emulate having named constants by setting aside a variable as the name of the constant, using abstraction to bind that variable in the main body, and apply that abstraction to the intended definition. Thus to use f to mean N (some explicit lambda-term) in M (another lambda-term, the "main program"), one can say

(λf.M) N
Authors often introduce syntactic sugar, such as let, to permit writing the above in the more intuitive order

let f = N in M
By chaining such definitions, one can write a lambda calculus "program" as zero or more function definitions, followed by one lambda-term using those functions that constitutes the main body of the program.
A notable restriction of this let is that the name f may not be referenced in N, for N is outside the scope of the abstraction binding f, which is M; this means a recursive function definition cannot be written with let. The letrec construction would allow writing recursive function definitions, where the scope of the abstraction binding f includes N as well as M. Or self-application a-la that which leads to Y combinator could be used.


### Recursion and fixed points

Recursion is when a function invokes itself. What would a value be which were to represent such a function? It has to refer to itself somehow inside itself, just as the definition refers to itself inside itself. If this value were to contain itself by value, it would have to be of infinite size, which is impossible. Other notations, which support recursion natively, overcome this by referring to the function by name inside its definition. Lambda calculus cannot express this, since in it there simply are no names for terms to begin with, only arguments' names, i.e. parameters in abstractions. Thus, a lambda expression can receive itself as its argument and refer to (a copy of) itself via the corresponding parameter's name. This will work fine in case it was indeed called with itself as an argument. For example,  (λx.x x) E = (E E) will express recursion when E is an abstraction which is applying its parameter to itself inside its body to express a recursive call. Since this parameter receives E as its value, its self-application will be the same (E E) again.
As a concrete example, consider the factorial function F(n), recursively defined by

F(n) = 1, if n = 0; else n × F(n − 1).
In the lambda expression which is to represent this function, a parameter (typically the first one) will be assumed to receive the lambda expression itself as its value, so that calling it with itself as its first argument will amount to the recursive call. Thus to achieve recursion, the intended-as-self-referencing argument (called s here, reminiscent of "self", or "self-applying") must always be passed to itself within the function body at a recursive call point:

E := λs. λn.(1, if n = 0; else n × (s s (n−1)))
with  s s n = F n = E E n  to hold, so  s = E  and
F := (λx.x x) E = E E
and we have

F = E E = λn.(1, if n = 0; else n × (E E (n−1)))
Here s s becomes the same  (E E) inside the result of the application  (E E), and using the same function for a call is the definition of what recursion is. The self-application achieves replication here, passing the function's lambda expression on to the next invocation as an argument value, making it available to be referenced there by the parameter name s to be called via the self-application s s, again and again as needed, each time re-creating the lambda-term  F = E E. 
The application is an additional step just as the name lookup would be. It has the same delaying effect. Instead of having  F inside itself as a whole up-front, delaying its re-creation until the next call makes its existence possible by having two finite lambda-terms  E inside it re-create it on the fly later as needed.
This self-applicational approach solves it, but requires re-writing each recursive call as a self-application. We would like to have a generic solution, without the need for any re-writes:

G := λr. λn.(1, if n = 0; else n × (r (n−1)))
with  r x = F x = G r x  to hold, so  r = G r =: FIX G  and
F := FIX G  where  FIX g = (r where r = g r) = g (FIX g)
so that  FIX G = G (FIX G) = (λn.(1, if n = 0; else n × ((FIX G) (n−1))))
Given a lambda term with first argument representing recursive call (e.g. G here), the fixed-point combinator FIX will return a self-replicating lambda expression representing the recursive function (here, F). The function does not need to be explicitly passed to itself at any point, for the self-replication is arranged in advance, when it is created, to be done each time it is called. Thus the original lambda expression (FIX G) is re-created inside itself, at call-point, achieving self-reference.
In fact, there are many possible definitions for this FIX operator, the simplest of them being:

 Y := λg.(λx.g (x x)) (λx.g (x x))
In the lambda calculus, Y g  is a fixed-point of g, as it expands to:

Y g
~> (λh.(λx.h (x x)) (λx.h (x x))) g
~> (λx.g (x x)) (λx.g (x x))
~> g ((λx.g (x x)) (λx.g (x x)))
<~ g (Y g)
Now, to perform the recursive call to the factorial function for an argument n, we would simply call (Y G) n. Given n = 4, for example, this gives:

Every recursively defined function can be seen as a fixed point of some suitably defined higher order function (also known as functional) closing over the recursive call with an extra argument. Therefore, using Y, every recursive function can be expressed as a lambda expression. In particular, we can now cleanly define the subtraction, multiplication, and comparison predicates of natural numbers, using recursion.
When Y combinator is coded directly in a strict programming language, the applicative order of evaluation used in such languages will cause an attempt to fully expand the internal self-application 
  
    
      
        (
        x
        x
        )
      
    
    {\displaystyle (xx)}
  
 prematurely, causing stack overflow or, in case of tail call optimization, indefinite looping. A delayed variant of Y, the Z combinator, can be used in such languages. It has the internal self-application hidden behind an extra abstraction through eta-expansion, as 
  
    
      
        (
        λ
        v
        .
        x
        x
        v
        )
      
    
    {\displaystyle (\lambda v.xxv)}
  
, thus preventing its premature expansion:

  
    
      
        Z
        =
        λ
        f
        .
        (
        λ
        x
        .
        f
        (
        λ
        v
        .
        x
        x
        v
        )
        )
         
        (
        λ
        x
        .
        f
        (
        λ
        v
        .
        x
        x
        v
        )
        )
         
        .
      
    
    {\displaystyle Z=\lambda f.(\lambda x.f(\lambda v.xxv))\ (\lambda x.f(\lambda v.xxv))\ .}
  


### Standard terms
Certain terms have commonly accepted names:

 I := λx.x
 S := λx.λy.λz.x z (y z)
 K := λx.λy.x
 B := λx.λy.λz.x (y z)
 C := λx.λy.λz.x z y
 W := λx.λy.x y y
 ω or Δ or U := λx.x x
 Ω := ω ω
I is the identity function. SK and BCKW form complete combinator calculus systems that can express any lambda term - see 
the next section. Ω is UU, the smallest term that has no normal form. YI is another such term.
Y is standard and defined above, and can also be defined as Y=BU(CBU), so that Yg=g(Yg). TRUE and FALSE defined above are commonly abbreviated as T and F.


### Abstraction elimination

If N is a lambda-term without abstraction, but possibly containing named constants (combinators), then there exists a lambda-term T(x,N) which is equivalent to λx.N but lacks abstraction (except as part of the named constants, if these are considered non-atomic). This can also be viewed as anonymising variables, as T(x,N) removes all occurrences of x from N, while still allowing argument values to be substituted into the positions where N contains an x. The conversion function T can be defined by:

T(x, x) := I
T(x, N) := K N if x is not free in N.
T(x, M N) := S T(x, M) T(x, N)
In either case, a term of the form T(x,N) P can reduce by having the initial combinator I, K, or S grab the argument P, just like β-reduction of (λx.N) P would do. I returns that argument. K throws the argument away, just like (λx.N) would do if x has no free occurrence in N. S passes the argument on to both subterms of the application, and then applies the result of the first to the result of the second.
The combinators B and C are similar to S, but pass the argument on to only one subterm of an application (B to the "argument" subterm and C to the "function" subterm), thus saving a subsequent K if there is no occurrence of x in one subterm. In comparison to B and C, the S combinator actually conflates two functionalities: rearranging arguments, and duplicating an argument so that it may be used in two places. The W combinator does only the latter, yielding the B, C, K, W system as an alternative to SKI combinator calculus.


## Typed lambda calculus


A typed lambda calculus is a typed formalism that uses the lambda-symbol (
  
    
      
        λ
      
    
    {\displaystyle \lambda }
  
) to denote anonymous function abstraction. In this context, types are usually objects of a syntactic nature that are assigned to lambda terms; the exact nature of a type depends on the calculus considered (see Kinds of typed lambda calculi). From a certain point of view, typed lambda calculi can be seen as refinements of the untyped lambda calculus but from another point of view, they can also be considered the more fundamental theory and untyped lambda calculus a special case with only one type.
Typed lambda calculi are foundational programming languages and are the base of typed functional programming languages such as ML and Haskell and, more indirectly, typed imperative programming languages. Typed lambda calculi play an important role in the design of type systems for programming languages; here typability usually captures desirable properties of the program, e.g., the program will not cause a memory access violation.
Typed lambda calculi are closely related to mathematical logic and proof theory via the Curry–Howard isomorphism and they can be considered as the internal language of classes of categories, e.g., the simply typed lambda calculus is the language of a Cartesian closed category (CCC).


## Reduction strategies


Whether a term is normalising or not, and how much work needs to be done in normalising it if it is, depends to a large extent on the reduction strategy used. Common lambda calculus reduction strategies include:

Normal order
The leftmost outermost redex is reduced first. That is, whenever possible, arguments are substituted into the body of an abstraction before the arguments are reduced. If a term has a beta-normal form, normal order reduction will always reach that normal form.
Applicative order
The leftmost innermost redex is reduced first. As a consequence, a function's arguments are always reduced before they are substituted into the function. Unlike normal order reduction, applicative order reduction may fail to find the beta-normal form of an expression, even if such a normal form exists. For example, the term 
  
    
      
        (
        
        λ
        x
        .
        y
        
        
        (
        λ
        z
        .
        (
        z
        z
        )
        
        λ
        z
        .
        (
        z
        z
        )
        )
        
        )
      
    
    {\displaystyle (\;\lambda x.y\;\;(\lambda z.(zz)\;\lambda z.(zz))\;)}
  
 is reduced to itself by applicative order, while normal order reduces it to its beta-normal form 
  
    
      
        y
      
    
    {\displaystyle y}
  
.
Full β-reductions
Any redex can be reduced at any time. This means essentially the lack of any particular reduction strategy—with regard to reducibility, "all bets are off".
Weak reduction strategies do not reduce under lambda abstractions:

Call by value
Like applicative order, but no reductions are performed inside abstractions. This is similar to the evaluation order of strict languages like C: the arguments to a function are evaluated before calling the function, and function bodies are not even partially evaluated until the arguments are substituted in.
Call by name
Like normal order, but no reductions are performed inside abstractions. For example, λx.(λy.y)x is in normal form according to this strategy, although it contains the redex (λy.y)x.
Strategies with sharing reduce computations that are "the same" in parallel:

Optimal reduction
As normal order, but computations that have the same label are reduced simultaneously.
Call by need
As call by name (hence weak), but function applications that would duplicate terms instead name the argument. The argument may be evaluated "when needed", at which point the name binding is updated with the reduced value. This can save time compared to normal order evaluation.


## Computability

There is no algorithm that takes as input any two lambda expressions and outputs TRUE or FALSE depending on whether one expression reduces to the other. More precisely, no computable function can decide the question. This was historically the first problem for which undecidability could be proven. As usual for such a proof, computable means computable by any model of computation that is Turing complete. In fact computability can itself be defined via the lambda calculus: a function F: N → N of natural numbers is a computable function if and only if there exists a lambda expression f such that for every pair of x, y in N, F(x)=y if and only if f x =β y, where x and y are the Church numerals corresponding to x and y, respectively and =β meaning equivalence with β-reduction. See the Church–Turing thesis for other approaches to defining computability and their equivalence.
Church's proof of uncomputability first reduces the problem to determining whether a given lambda expression has a normal form. Then he assumes that this predicate is computable, and can hence be expressed in lambda calculus. Building on earlier work by Kleene and constructing a Gödel numbering for lambda expressions, he constructs a lambda expression e that closely follows the proof of Gödel's first incompleteness theorem. If e is applied to its own Gödel number, a contradiction results.


## Complexity

The notion of computational complexity for the lambda calculus is a bit tricky, because the cost of a β-reduction may vary depending on how it is implemented. 
To be precise, one must somehow find the location of all of the occurrences of the bound variable V in the expression E, implying a time cost, or one must keep track of the locations of free variables in some way, implying a space cost. A naïve search for the locations of V in E is O(n) in the length n of E. Director strings were an early approach that traded this time cost for a quadratic space usage. More generally this has led to the study of systems that use explicit substitution.
In 2014, it was shown that the number of β-reduction steps taken by normal order reduction to reduce a term is a reasonable time cost model, that is, the reduction can be simulated on a Turing machine in time polynomially proportional to the number of steps. This was a long-standing open problem, due to size explosion, the existence of lambda terms which grow exponentially in size for each β-reduction. The result gets around this by working with a compact shared representation. The result makes clear that the amount of space needed to evaluate a lambda term is not proportional to the size of the term during reduction. It is not currently known what a good measure of space complexity would be.
An unreasonable model does not necessarily mean inefficient. Optimal reduction reduces all computations with the same label in one step, avoiding duplicated work, but the number of parallel β-reduction steps to reduce a given term to normal form is approximately linear in the size of the term. This is far too small to be a reasonable cost measure, as any Turing machine may be encoded in the lambda calculus in size linearly proportional to the size of the Turing machine. The true cost of reducing lambda terms is not due to β-reduction per se but rather the handling of the duplication of redexes during β-reduction. It is not known if optimal reduction implementations are reasonable when measured with respect to a reasonable cost model such as the number of leftmost-outermost steps to normal form, but it has been shown for fragments of the lambda calculus that the optimal reduction algorithm is efficient and has at most a quadratic overhead compared to leftmost-outermost. In addition the BOHM prototype implementation of optimal reduction outperformed both Caml Light and Haskell on pure lambda terms.


## Lambda calculus and programming languages

As pointed out by Peter Landin's 1965 paper "A Correspondence between ALGOL 60 and Church's Lambda-notation", sequential procedural programming languages can be understood in terms of the lambda calculus, which provides the basic mechanisms for procedural abstraction and procedure (subprogram) application.


### Anonymous functions

For example, in Python the "square" function can be expressed as a lambda expression as follows:

The above example is an expression that evaluates to a first-class function. The symbol lambda creates an anonymous function, given a list of parameter names—just the single argument x, in this case—and an expression that is evaluated as the body of the function, x**2. Anonymous functions are sometimes called lambda expressions.
Pascal and many other imperative languages have long supported passing subprograms as arguments to other subprograms through the mechanism of function pointers. However, function pointers are an insufficient condition for functions to be first class datatypes, because a function is a first class datatype if and only if new instances of the function can be created at runtime. Such runtime creation of functions is supported in Smalltalk, JavaScript, Wolfram Language, and more recently in Scala, Eiffel (as agents), C# (as delegates) and C++11, among others.


### Parallelism and concurrency
The Church–Rosser property of the lambda calculus means that evaluation (β-reduction) can be carried out in any order, even in parallel. This means that various nondeterministic evaluation strategies are relevant. However, the lambda calculus does not offer any explicit constructs for parallelism. One can add constructs such as futures to the lambda calculus. Other process calculi have been developed for describing communication and concurrency.


## Semantics

The fact that lambda calculus terms act as functions on other lambda calculus terms, and even on themselves, led to questions about the semantics of the lambda calculus. Could a sensible meaning be assigned to lambda calculus terms? The natural semantics was to find a set D isomorphic to the function space D → D, of functions on itself. However, no nontrivial such D can exist, by cardinality constraints because the set of all functions from D to D has greater cardinality than D, unless D is a singleton set.
In the 1970s, Dana Scott showed that if only continuous functions were considered, a set or domain D with the required property could be found, thus providing a model for the lambda calculus.
This work also formed the basis for the denotational semantics of programming languages.


## Variations and extensions

These extensions are in the lambda cube:

Typed lambda calculus – Lambda calculus with typed variables (and functions)
System F – A typed lambda calculus with type-variables
Calculus of constructions – A typed lambda calculus with types as first-class values
These formal systems are extensions of lambda calculus that are not in the lambda cube:

Binary lambda calculus – A version of lambda calculus with binary input/output (I/O), a binary encoding of terms, and a designated universal machine.
Lambda-mu calculus – An extension of the lambda calculus for treating classical logic
These formal systems are variations of lambda calculus:

Kappa calculus – A first-order analogue of lambda calculus
These formal systems are related to lambda calculus:

Combinatory logic – A notation for mathematical logic without variables
SKI combinator calculus – A computational system based on the S, K and I combinators, equivalent to lambda calculus, but reducible without variable substitutions


## See also



## Further reading

Abelson, Harold & Gerald Jay Sussman. Structure and Interpretation of Computer Programs. The MIT Press. ISBN 0-262-51087-1.
Barendregt, Hendrik Pieter Introduction to Lambda Calculus.
Barendregt, Hendrik Pieter, The Impact of the Lambda Calculus in Logic and Computer Science. The Bulletin of Symbolic Logic, Volume 3, Number 2, June 1997.
Barendregt, Hendrik Pieter, The Type Free Lambda Calculus pp1091–1132 of Handbook of Mathematical Logic, North-Holland (1977) ISBN 0-7204-2285-X
Cardone, Felice and Hindley, J. Roger, 2006. History of Lambda-calculus and Combinatory Logic Archived 2021-05-06 at the Wayback Machine. In Gabbay and Woods (eds.), Handbook of the History of Logic, vol. 5. Elsevier.
Church, Alonzo, An unsolvable problem of elementary number theory, American Journal of Mathematics, 58 (1936), pp. 345–363. This paper contains the proof that the equivalence of lambda expressions is in general not decidable.
Church, Alonzo (1941). The Calculi of Lambda-Conversion. Princeton: Princeton University Press. Retrieved 2020-04-14. (ISBN 978-0-691-08394-0)
Frink Jr., Orrin (1944). "Review: The Calculi of Lambda-Conversion by Alonzo Church" (PDF). Bulletin of the American Mathematical Society. 50 (3): 169–172. doi:10.1090/s0002-9904-1944-08090-7.
Kleene, Stephen, A theory of positive integers in formal logic, American Journal of Mathematics, 57 (1935), pp. 153–173 and 219–244. Contains the lambda calculus definitions of several familiar functions.
Landin, Peter, A Correspondence Between ALGOL 60 and Church's Lambda-Notation, Communications of the ACM, vol. 8, no. 2 (1965), pages 89–101. Available from the ACM site. A classic paper highlighting the importance of lambda calculus as a basis for programming languages.
Larson, Jim, An Introduction to Lambda Calculus and Scheme. A gentle introduction for programmers.
Michaelson, Greg (10 April 2013). An Introduction to Functional Programming Through Lambda Calculus. Courier Corporation. ISBN 978-0-486-28029-5.
Schalk, A. and Simmons, H. (2005) An introduction to λ-calculi and arithmetic with a decent selection of exercises. Notes for a course in the Mathematical Logic MSc at Manchester University.
de Queiroz, Ruy J.G.B. (2008). "On Reduction Rules, Meaning-as-Use and Proof-Theoretic Semantics". Studia Logica. 90 (2): 211–247. doi:10.1007/s11225-008-9150-5. S2CID 11321602. A paper giving a formal underpinning to the idea of 'meaning-is-use' which, even if based on proofs, it is different from proof-theoretic semantics as in the Dummett–Prawitz tradition since it takes reduction as the rules giving meaning.
Hankin, Chris, An Introduction to Lambda Calculi for Computer Scientists, ISBN 0954300653
Monographs/textbooks for graduate students

Sørensen, Morten Heine and Urzyczyn, Paweł (2006), Lectures on the Curry–Howard isomorphism, Elsevier, ISBN 0-444-52077-5 is a recent monograph that covers the main topics of lambda calculus from the type-free variety, to most typed lambda calculi, including more recent developments like pure type systems and the lambda cube. It does not cover subtyping extensions.
Pierce, Benjamin (2002), Types and Programming Languages, MIT Press, ISBN 0-262-16209-1 covers lambda calculi from a practical type system perspective; some topics like dependent types are only mentioned, but subtyping is an important topic.
Documents
A Short Introduction to the Lambda Calculus-(PDF) by Achim Jung
A timeline of lambda calculus-(PDF) by Dana Scott
A Tutorial Introduction to the Lambda Calculus-(PDF) by Raúl Rojas
Lecture Notes on the Lambda Calculus-(PDF) by Peter Selinger
Graphic lambda calculus by Marius Buliga
Lambda Calculus as a Workflow Model by Peter Kelly, Paul Coddington, and Andrew Wendelborn; mentions graph reduction as a common means of evaluating lambda expressions and discusses the applicability of lambda calculus for distributed computing (due to the Church–Rosser property, which enables parallel graph reduction for lambda expressions).


## Notes



## References

Some parts of this article are based on material from FOLDOC, used with permission.


## External links

