The program UNIF is an implementation in AlgolW of the algorithm
published as:

G. P. HUET,
A unification algorithm for typed lambda-calculus, 
Theoretical Computer Science 1 (1975) 27-57. 

As in the article, lambda terms are represented in head normal form:
*x1x2...xn.h(e1,e2,... ep) (n >= 0, p >= 0)
x1 x2 ... xn are different variables,
h is a variable or a constant
e1 e2 ... en are terms
* stands for lambda

variables are x y z u v w f g h optionally followed by an integer
constants start with other letters.
Every atom is given with its type.
Atomic types are i and o
Functional types are (t1, ..., tk - a) where a is an atomic type,
standing for (t1 -> (t2 -> ... -> (tk -> a)...)) in the usual notation.

The program starts by asking for a list of pairs of terms to unify,
and for each term asks fot the type of its atoms. 
When the list is finished (answer n to query "any more pairs?"),
the program asks for an integer used as a bound to the number of nodes
of the spanning tree.
It then enumerates the tree of solutions, within this limit.

The following gives the complete transcript of a 
session, corresponding to exemple 3.5.3 in the paper.
The nodes in the tree are named NULL for the root, RCCLxy.z for others. 

===================================================================
PAIR NO  1
FIRST TERM
ENTER YOUR TERM:
x

ENTER TYPE OF ATOM :X
(((i-i),i,i-i)-i)

SECOND TERM
ENTER YOUR TERM:
*u.u(*v.w,x(*u1v1w1.a(u1(v1),w1)),x(f))

ENTER TYPE OF ATOM :U
((i-i),i,i-i)-i)

ENTER TYPE OF ATOM :V
i

ENTER TYPE OF ATOM :W
i

ENTER TYPE OF ATOM : U1
(i-i)

ENTER TYPE OF ATOM : V1
i

ENTER TYPE OF ATOM : W1
i

ENTER TYPE OF ATOM : A
(i,i-i)

ENTER TYPE OF ATOM : F
((i-i),i,i-i)

ANY MORE PAIRS ALLOWED ?
n

HOW MANY NODES ALLOWED ?
10

    RCCL08.1 FOLLOWS NULL
THE NEXT PAIR TO UNIFY IS
    X
    *U1.U1(*V2.W,X(*U3V4W5.A(U3(V4),W5)),X(F))
TIME SPENT IN JIFFIES=  20
TO X MATCH SUBSTITUTES
   *U9.U9(H6(U9),H7(U9),H8(U9))
   RCCL08.2     FOLLOWS RCCL08.1
THE NEXT PAIR TO UNIFY IS
    H8(U9)
    F(H6(F),H7(F),H8(F))
THE NEXT PAIR TO UNIFY IS
    H7(U9)
    A(H6(*U10V11W12.A(U10(V11),W12),H7(*U13V14W15.A(U13(V14),W15))),H8(*U16V17W18.A(U16(V17),W18)))
THE NEXT PAIR TO UNIFY IS
    H6(U9)
    *V19.W
TIME SPENT IN JIFFIES=  35
TO H00007 MATCH SUBSTITUTES
1  *W25.W25(H22(W25),H23(W25),H24(W25))
TO H00007 MATCH SUBSTITUTES
   *W26.A(H20(W26),H21(W26))
   RCCL04.2     FOLLOWS RCCL08.2
   RCCL04.2     IS TSN!
   RCCL04.1     FOLLOWS RCCL08.2
   RCCL04.1     IS TFN!
TIME SPENT IN JIFFIES=  58
EXIT
TIME SPENT IN JIFFIES=  58
===================================================================






