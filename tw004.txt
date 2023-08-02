% Helper predicates
concatenate([], L, L).
concatenate([H|T], L, [H|R]) :- concatenate(T, L, R).
add_element(X, L, [X|L]).
delete_element(X, [X|T], T) :- !.
delete_element(X, [H|T], [H|R]) :- delete_element(X, T, R).
delete_element(_, [], []).
permute([], []).
permute([H|T], R) :- permute(T, X), select(H, R, X).

% Menu-driven functions
menu :-
    writeln('MENU\n1. Concatenate lists\n2. Add element\n3. Delete element\n4. Permute list\n5. Quit\nEnter the number of your choice: '),
    read(Choice), process(Choice), (Choice == 5 -> true; menu).

process(1) :- read_lists(L1, L2), concatenate(L1, L2, R), writeln('Concatenated list: '), write_list(R).
process(2) :- read_element_list(X, L), add_element(X, L, R), writeln('List after adding element: '), write_list(R).
process(3) :- read_element_list(X, L), delete_element(X, L, R), writeln('List after deleting element: '), write_list(R).
process(4) :- write('Enter a list: '), read(L), findall(X, permute(L, X), R), writeln('Permutations: '), maplist(writeln, R).
process(5) :- writeln('Goodbye!').

% Read helpers
read_lists(L1, L2) :- write('Enter first list: '), read(L1), write('Enter second list: '), read(L2).
read_element_list(X, L) :- write('Enter an element: '), read(X), write('Enter a list: '), read(L).
write_list(L) :- writeln(L), nl.

% Main predicate
main :-
    menu.
