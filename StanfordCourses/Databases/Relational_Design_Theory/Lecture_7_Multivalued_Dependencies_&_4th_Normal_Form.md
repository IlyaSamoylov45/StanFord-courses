Multivalued dependencies & 4th Normal Form Part 1
  - Example : College application info
    - Apply(SSN, cName, Hobby)
    - FDs? No
    - Keys : All attributes
    - BCNF? : Yes
    - Good Design ? 5 Colleges and 6 Hobbies -> 30 types
  - Multivalued Dependency
    - Based on Knowledge of real world
    - All instances of relation must adhere
      - R : A ↠ B for A1, ... , An and B1, ... , Bn
      - ∀t,u ∈ R
      - t[A1, A2, . . ., An] = u[A1, A2, . . ., An] then ∃v ∈ R : v[A1, A2, . . ., An] = t[A1, A2, . . ., An] and v[B1, B2, . . ., Bn] = t[B1, B2, . . ., Bn] and v[rest] = u[rest]
    - Sometimes called tuple generating dependencies

Multivalued dependencies & 4th Normal Form Part 2
  - Apply(SSN, cName, hobby)
    - SSN ↠ cName

    | -- | SSN  | cName  | hobby  |
    | -- | -- | -- | -- |                          
    | t | 123  | Stanford  | Trumpet  |
    | u | 123  | Berkley  | Tennis  |
    | v | 123  | Stanford  | Tennis  |
    | w | 123  | Berkley  | Trumpet  |
    | ... | ...  | ...  | ...  |
  - Modified example
    - Apply(SSN, cName, hobby)
      - Reveal hobbies to college selectively
      - MVDs None
      - Good Design? Yes
  - Expanded example :
    - Apply(SSN, cName, date, major, hobby)
      - Reveal hobbies to Colleges selectively
      - Apply once to each college per day
      - May apply to multiple majors
      - SSN, cName → date
      - SSN, cName, date ↠ major

Multivalued dependencies & 4th Normal Form Part 3
  - Trivial Multivalued dependency  
    - A ↠ B  B ⊆ A or A U B all attributes
  - Non Trivial MVD : otherwise
  - Rules for multivalued Dependencies
    - FD is an MVD rule
      - If A → B then A ↠ B
    - Intersection rule
      - A ↠ B and A ↠ C then A ↠ B ∩ C
    - Transitive Rule
      - A ↠ B and B ↠ C then A ↠ C - B
  - Fourth Normal Form => BCNF
    - Relation R with MVDs is in 4NF if:
      - For each nontrivial A ↠ B, A is a key
  - 4NF Decomposition algorithm
    - Input : relation R + FDs for R + MVDs for R
    - Output : decomposition of R into 4NF relations with "lossless join"
    - Compute keys for R
    - Repeat until all relations are in 4NF
      - Pick any R with nontrivial A ↠ B that violates 4NF
      - Decompose R into R1(A, B) and R2(A, rest)
      - Compute FDs and MVDs for R1 and R2
      - Compute keys for R1 and R2
  - 4NF Decomposition Example 1:
    - Apply(SSN, cName, hobby)
      - SSN ↠ cName
      - No Keys
    - A1(SSN,cName) No FDs
    - A2(SSN, hobby) No MVDs
  - 4NF Decomposition Example 2:
    - Apply(SSN, cName, date, major hobby)
      - SSN, cName → date
      - SSN, cName, date ↠ major
      - No Keys
    - A1(SSN, cName, date, major)
      - A3(SSN, cName, date)
      - A4(SSN, cName, major)
    - A2(SSN, cName, date, hobby)
      - A5(SSN, cName, hobby)
    - Final :
      - A1(SSN, cName, date)
      - A2(SSN, cName, major)
      - A3(SSN, cName, hobby)

Multivalued dependencies & 4th Normal Form Part 4
  - Relational  Design
    - Functional Dependencies and Boyce-Codd Normal Form (BCNF)
      - R(A, B, C) : A → B
    - Multivalued dependencies and Fourth Normal Form
      - R(A,B,C,D) : A ↠ B
