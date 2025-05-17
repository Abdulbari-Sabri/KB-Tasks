         CLIPS (6.30 3/17/15)
CLIPS> (deftemplate person
   (multislot name 
      (type SYMBOL STRING)
      (cardinality 2 4))
   (slot age 
      (type INTEGER)
      (range 20 25))
   (slot hair-color 
      (type SYMBOL))
)
CLIPS> (deffacts sample-people
   (person (name Abdulbari Sabri) (age 22) (hair-color blonde))
   (person (name Awad Elmansy) (age 24) (hair-color red))
   (person (name Sabri Awad) (age 21) (hair-color black))
)
CLIPS> (defrule check_color
   (person (name $?n) (hair-color ?color&~black&~brown))
   =>
   (printout t "Hair color is: " ?color crlf)
)
CLIPS> (reset)
CLIPS> (facts)
f-0     (initial-fact)
f-1     (person (name Abdulbari Sabri) (age 22) (hair-color blonde))
f-2     (person (name Awad Elmansy) (age 24) (hair-color red))
f-3     (person (name Sabri Awad) (age 21) (hair-color black))
For a total of 4 facts.
CLIPS> (run)
Hair color is: red
Hair color is: blonde
CLIPS> 
