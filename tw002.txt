
list(X,[X|_]).
list(X,[_|TAIL]) :- list(X,TAIL).

con([],L,L).
con([X1|L1],L2,[X1|L3]) :- con(L1,L2,L3).

del(X,[X|T],T).
del(X,[H|T],[H|T1]) :- del(X,T,T1).
