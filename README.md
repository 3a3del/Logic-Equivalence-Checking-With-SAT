# Logic-Equivalence-Checking-With-SAT
An Assignment 2 in VLSI CAD Part I: Logic Course under supervision of Rob A. Rutenbar, Adjunct Professor
We can also use a SAT solver to determine if two gate-level networks are implementing the same function or not. And, if they are not the same, the SAT solver can find an assignment of the variables that will make the network outputs different. In this problem, we will let you play with a real SAT solver package: MiniSat, from Niklas Eén, Niklas Sörensson (                                        
http://minisat.se
).                                        
To explain how to use MiniSat, let us compare these two very simple logic networks. (For your convenience, we label each signal, both primary inputs/outputs, and internal wires, with the name “x” and a subscript i; this will help you easily connect them to the corresponding numerical variable i in MiniSat)
![](https://github.com/3a3del/Logic-Equivalence-Checking-With-SAT/blob/main/Q10_sim0.png)                    
If you go look in the TOOLS section of the course website (https://www.coursera.org/learn/vlsi-cad-logic/programming/992FM/minisat), you will find two helpful tutorials about kbdd: a written document that explains the tool and its capabilities 'Don't worry i will provide them here', and also a short video tutorial about to use MiniSat in the Coursera MOOC environment (https://www.youtube.com/watch?v=3WHng8TU5a0). Please go look at those before you proceed further in this problem.

Assuming you have read/viewed these tutorial materials, the MiniSat input file for checking equivalence of 𝑥 4 and 𝑥 6 is developed below                                                                                                                                                          
First, we connect the two circuits’ outputs with an EXOR gate; we will use MiniSat to check if this new logic network can be satisfied ( 𝑥 7 = 1 x 7 ​ =1) or not. If it is satisfiable, we will know the original two circuits are not equivalent, because there exists one satisfying assignment such that < 𝑥 4 = 1 , 𝑥 6 = 0 > <x 4 ​ =1,x 6 ​ =0> or < 𝑥 4 = 0 , 𝑥 6 = 1 > <x 4 ​ =0,x 6 ​ =1>.                                                                         
![](https://github.com/3a3del/Logic-Equivalence-Checking-With-SAT/blob/main/Q10_sim1.png)
# Here are SAT clauses converted from this little logic network:
( 𝑥 2 + 𝑥 3 ) ( ¬ 𝑥 2 + ¬ 𝑥 3 ) ( ¬ 𝑥 1 + ¬ 𝑥 2 + 𝑥 5 ) ( 𝑥 1 + ¬ 𝑥 5 ) ( 𝑥 2 + ¬ 𝑥 5 ) ( 𝑥 1 + 𝑥 3 + ¬ 𝑥 4 ) ( ¬ 𝑥 1 + 𝑥 4 ) ( ¬ 𝑥 3 + 𝑥 4 ) ⋅ (x 2 ​ +x 3 ​ )(¬x 2 ​ +¬x 3 ​ )(¬x 1 ​ +¬x 2 ​ +x 5 ​ )(x 1 ​ +¬x 5 ​ )(x 2 ​ +¬x 5 ​ )(x 1 ​ +x 3 ​ +¬x 4 ​ )(¬x 1 ​ +x 4 ​ )(¬x 3 ​ +x 4 ​ )⋅ ( 𝑥 5 + 𝑥 6 ) ( ¬ 𝑥 5 + ¬ 𝑥 6 ) ( 𝑥 4 + ¬ 𝑥 6 + 𝑥 7 ) ( 𝑥 4 + 𝑥 6 + ¬ 𝑥 7 ) ( ¬ 𝑥 4 + 𝑥 6 + 𝑥 7 ) ( ¬ 𝑥 4 + ¬ 𝑥 6 + ¬ 𝑥 7 ) ( 𝑥 7 ) (x 5 ​ +x 6 ​ )(¬x 5 ​ +¬x 6 ​ )(x 4 ​ +¬x 6 ​ +x 7 ​ )(x 4 ​ +x 6 ​ +¬x 7 ​ )(¬x 4 ​ +x 6 ​ +x 7 ​ )(¬x 4 ​ +¬x 6 ​ +¬x 7 ​ )(x 7 ​ )
The input file for the MiniSat solver is as follows.
![](https://github.com/3a3del/Logic-Equivalence-Checking-With-SAT/blob/main/t.png)

You will see two sorts of results: (1) some “internal information” about what actions MiniSat took during its DPLL search (see tutorial document for a discussion of these); (2) a result about the satisfiability of the circuit, and maybe a solution which is a satisfying assignment. In this case, the second part produces this: “SAT 1 2 -3 4 5 -6 7 0” It means 𝑥 1 = 1 and 𝑥 2 = 1 will lead to 𝑥 7 = 1
#So, Our Assignment
![](https://github.com/3a3del/Logic-Equivalence-Checking-With-SAT/blob/main/temp1.png)
compare these two logic networks 𝐹 and 𝐺 , which are each functions of 5 variables 𝑥 1, 𝑥 2, 𝑥 3, 𝑥 4, and 𝑥 5.                                                            
 #You need to EXOR the outputs of 𝐹 and 𝐺 to see if the EXOR gate can be satisfied or not. So, this is the network to submit to MiniSat:
  ![](https://github.com/3a3del/Logic-Equivalence-Checking-With-SAT/blob/main/temp2.png)
  
  So transforming gate networks into SAT clauses as in the MiniSat'input                                        
  # Results 
  UNSATISFIABLE
  
  
  
  
                                                        
  
  
  

  
  
  
  
  
  
  
