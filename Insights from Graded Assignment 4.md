(Question: 6)
Consider the following two tables:  
Table 1: records
![[Pasted image 20260505222044.png|551]]
Table 2: players
![[Pasted image 20260505222107.png|459]]
What will be the output of following code?  
```
SELECT players.name_
    _FROM players_
    _INNER JOIN records ON records.player_id = players.player_id_
    _WHERE players.role = "opening_batsman" and records.format = "odi"_
    _ORDER BY records.highest_score DESC_
    _LIMIT 1;_
```
(A) Rohit Sharma
(B) AB de Villiers
(C) Virat Kohli
(D) David warner

Correct answer: (A) Rohit Sharma