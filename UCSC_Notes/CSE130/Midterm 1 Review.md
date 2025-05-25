#UCSC #CSE130

#### **Format**
12 Multiple Choice -- 1/2 "recall" 1/2 "application"
2 Free response

**Four Issues of Complexity**
1. propagation of effects -- problems in one component affect other components
2. Emergent properties -- properties that show up only when combining individual components
3. incommensurate scaling -- 
4. tradeoffs

**"Signs" of Complexity**
1. Large number of components
2. Large number of interconnections
3. Lots of irregularities (little differences)
4. Long description (high information content)
5. Large team of designers, implementers, or maintainers
     - weakest symptom: many complex systems lack this

**Modularity**
- Break big things into smaller pieces
- Allows development of a smaller unit
	- reduces the number of components and interactions

**Abstraction**
- Break into components at logical points
- Treat an individual component as a black box
- Benefit from the Robustness principle
	- be tolerant of inputs and strict on outputs
- Maintain a safety margin: fragility is bad

**Layering**
- Each module is only communicating with the one above and below
	- Layering presents a new abstraction (interface) for layers above

**Hierarchy**
- combine small groups of modules into small subsystems
- combine small subsystems into large subsystems
- combine large subsystems into systems
- limit the visibility of each level of abstraction

**Memory Properties**
- registers 
- caches (L1,L2,L2)
- DRAM
- SSDs
- HDDs
- Tape


**Abstract Interpreter**
- Instruction reference
- Repertoire
- Environment reference
