Adapton Example: Divide-by-Zero 
==================================
- Illustrates **demand-driven change propagation**.
- See also: [Example Rust code](https://docs.rs/adapton/0/adapton/macros/index.html#demand-driven-change-propagation)

Initial Graph, before initial demand
----------------------------------------------
![Slide 05](Adapton_Avoiddivbyzero_05.png)

Initial Graph, before initial demand (due to 1st `get`)
------------------------------------------------------
![Slide 10](Adapton_Avoiddivbyzero_10.png)

Initial Graph, after first dirtying phase (due to 1st `set`)
---------------------------------------------------------
![Slide 12](Adapton_Avoiddivbyzero_12.png)

Updated Graph, after first cleaning phase (due to 2nd `get`)
---------------------------------------------------------
![Slide 16](Adapton_Avoiddivbyzero_16.png)

Dirtied graph, after second dirtying phase (due to 2nd `set`)
---------------------------------------------------------
![Slide 17](Adapton_Avoiddivbyzero_17.png)

Updated graph, after second cleaning phase (due to 3rd `get`)
---------------------------------------------------------
![Slide 23](Adapton_Avoiddivbyzero_23.png)


As a movie:
-------------
![All Slide Key Frames](Adapton_Avoiddivbyzero.png)
