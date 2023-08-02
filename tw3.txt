:- discontiguous list_member/2.

intersection([X|Y],M,[X|Z]):-list_member(X,M),intersection(Y,M,Z).
intersection([X|Y],M,Z):- \+list_member(X,M),intersection(Y,M,Z).
intersection([],_,[]).

list_member(X,[X|_]).
list_member(X,[_|TAIL]) :-list_member(X,TAIL).

union([X|Y],Z,W) :-list_member(X,Z),union(Y,Z,W).
union([X|Y],Z,[X|W]) :- \+list_member(X,Z),union(Y,Z,W).
union([],Z,Z).

list_member(X,[X|_]).
list_member(X,[_|TAIL]):-list_member(X,TAIL).

