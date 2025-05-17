         CLIPS (6.30 3/17/15)
CLIPS> (deftemplate person
   (multislot name 
      (type SYMBOL STRING)
      (cardinality 2 4))
   (slot age 
      (type INTEGER)
      (range 20 25))
)
CLIPS> (deffacts people
   (person (name Abdulbari Sabri) (age 22))
   (person (name Mohamed Ahmed) (age 24))
   (person (name Ahmed Adel) (age 21))
)
CLIPS> (defrule check_age
   (person (name $?n) (age ?a&:(and (> ?a 20) (<= ?a 25))))
   =>
   (printout t ?n " is between 20 and 25 years old." crlf)
)
CLIPS> (reset)
CLIPS> (facts)
f-0     (initial-fact)
f-1     (person (name Abdulbari Sabri) (age 22))
f-2     (person (name Mohamed Ahmed) (age 24))
f-3     (person (name Ahmed Adel) (age 21))
For a total of 4 facts.
CLIPS> (run)
(Ahmed Adel) is between 20 and 25 years old.
(Mohamed Ahmed) is between 20 and 25 years old.
(Abdulbari Sabri) is between 20 and 25 years old.
CLIPS> 
