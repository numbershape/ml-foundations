# Week 1: Linear Algebra - Vectors and Transformations

## Resources
- 3Blue1Brown: Essence of Linear Algebra (Videos 1-16)
- Khan Academy: Linear Algebra exercises

---

## Notes

### Video 1: Vectors

**Key Concepts:**

- Vectors:
    - Arrows pointing in space - defined by length and direction
    - ordered lists of numbers - defined by its listings (two if 2D)
    - Anything with the sense of adding two vectors, or multiplying them by a number
    
- Linear-Algebra specific vectors:
    - arrow inside a coordinate system with tail at the origin (0,0)

- Coordinates:
    - A pair of numbers that give instructions of how to get from tail (at the origin) to tip
    - Written vertically in square brackets
    - Every pair of numbers is associated with only one vector and the reverse
    - First number: How far on the x axis
    - Second number: How far parallel to the y axis
    - For 3D: add z axis perpendicular to both x and y; list has 3 numbers
    - Third number: How far parallel to the z axis

- Fundamental operations:
    - Vector addition
    - Scalar multiplication

- Vector addition:
    - Move 2nd vector so that tail sits on top of 1st one
    - Then draw a new vector from the tail of the 1st one to the tip of where the 2nd now sits
    - This is the only time in Linear Algebra we "let" a vector stray from the origin

- Addition intuition:
    - Each vector represents a STEP or MOVE (distance and direction)
    - Taking both individually or taking their sum "path" lands you at the same point in space
    - Like 2 + 5 is like taking 7 steps to the right
    - Example: "Walk 1 to the right, then two up, then 3 to the right,, then 1 down"
    - We can first do all the rightward motions and then all the vertical motions

- Vector multiplication by a number:
    - Multiplying a vector by a number results in scaling, so we call the number a "scalar"
    - Mupliplying by 2: stretches out the vector to get twice as long (each component is stretched by two)
    - Multiplying by 1/3: squishes down the vector by a third
    - Multiplying by -1.8: flips the vector around, then stretches it by 1.8
    
---

### Video 2: Linear Combinations, Span, and Basis Vectors

**Key Concepts:**

- Basis Vectors:
    - Another way to think of coordinates: think of each coordinate itself as a SCALAR (of two unit vectors)
    - i-hat and j-hat are the "basis" (unit) vectors of the coordinate system
    - i-hat is the unit vector in the x direction - points to the right with length 1
    - j-hat is the unit vector in the y direction - points up with length 1
    - So the x coordinate is a scalar that scales i-hat
    - And the y coordinate is a scalar that scales j-hat
    - So the vector of "3 i-hat + 2 j-hat" coordinates, is actually the sum of the two scaled vectors!

- Linear Combination:
    - By altering scalars you can reach every possible 2D vector
    - Note: if we used different basis, we would get different vector coordinates after scaling (for the same point in space)
    - That would be different coordinate systems
    - When we scale two vectors and add them, it is called a Linear Combination
    - Reason is because if one scalar is fixed while the other one changes, the other one forms a straight line as values change
    
- Linear Combination cases:
    - Usual case: if both scalars change value you will reach every possible point in plane
    - Rare case: if the two original vectors line up, then the tip of the resuming vector is limited to this line
    - Exception: if both original vectors are 0, you get stuck at the origin

- Span:
    - The set of all possible vectors you can reach with a linear combination of a pair of vectors (+ all possible scalars) is their SPAN
    - So span is all possible vectors you can reach using only the two fundamental operations (vector addition and scalar multiplication)
    - So basically, adding two pre-scaled vectors
    - The span of most pairs of 2D vectors is all vectors of 2D space (remember exception 1: all vectors whose tips sits on a straight line)
    - So basically, the span of most vectors is the entire 2D space sheet
    - To avoid a crowded space, when dealing with collections of vectors, we represent them as points
    - Tip of the vector is the point in space; tail is implicitly at the origin

- Span in 3D (two vectors):
    - All possible linear combinations of those two vectors (scaling them and adding them together)
    - The tip of the resulting vector will trace some kind of FLAT SHEET cutting through the origin of 3D space

- Span in 3D (three vectors):
    - Rare case: if the 3rd vector is sitting on the span of the first 2 vectors, it is redundant and span doesn't change (stays a flat sheet)
    - Usual case: if the 3rd vector is not on the span of the first 2 vectors, the result is every possible 3D vector
    - This is as if the 3rd vector moves 'around' or 'up and down' the sheet of the previous 2-vector span in 3D

- Linear dependence:
    - If a vector is redundant, we say that the related vectors are Linearly Dependent
    - This covers 2D - if the two original vectors line up (then the tip of the resuming vector is limited to this line)
    - And 3D - if the 3rd vector is sitting on the span of the first 2 vectors (span doesn't change - stays a flat sheet)
    - Also for the 3D case, one of the vectors can be expressed as a linear combination of the others, since it is already in the span of the others
    - Conversely, if each vector adds another dimention to the span, they are Linearly Independent
    - So technical definition of basis: The basis of a vector space is a set of linearly independent vectors that span the full space.

---

### Video 3: Linear Transformations and Matrices

**Key Concepts:**

- Linear Transformations:
    - Transformations are functions. They take in inputs (vectors) and return outputs (other vectors)
    - We can imagine the input vector moving over to the output vector
    - The transformation as a whole is to imagine watching every possible input vector move over to its corresponding output vector (at the same time)
    - The space itself gets transformed!
    - Because it gets crowded, we imagine vectors as points
    - So we watch every point in space move into some other point

- Linear Algebra Transformations:
    - 2D Linear Algebra limits itself to a type of transformation 
    - All lines must remain lines without getting curved
    - The origin must remain fixed in place
    - Grid lines must remain parallel and evenly spaced
    - In these trasformations, we only need to record where the basis vectors land
    
- Transformation Process:
    - Say a vector is represented as the sum of the two (scaled accordingly) basis-vectors i-hat and j-hat
    - Now lets transform and follow where the three vectors go
    - Lines remain parallel and evenly spaced
    - The transformed vector equals the sum of the two transformed basis-vectors, scaled using the same scalars as before (the original basis scalars we used to represent the original vector)
    - So basically the transformed result-vector equals the original scalar for i-hat multiplied by the transformed i-hat, plus the original scalar for j-hat multiplied by the transformed j-hat! 
    - In other words, if an original vector has coordinates x and y (i-hat and j-hat scalars), to find where it lands we multiply x by the new i-hat coordinates, plus y by the new j-hat coordinates
    - So we only need to know where the basis vectors landed, and we can deduce where any other vector landed, without visual aid
    - Any 2D Linear Transformation is described by just 4 numbers (the two coordinates where i-hat lands, and the two coordinates where j-hat lands)

- 2x2 Matrix:
    - We package the four numbers into a 2x2 grid
    - Two columns: where i-hat lands, and where j-hat lands
    - We can even define the process as Matrix Vector Multiplication
    - The multiplication formula order is not too clear, but it's actually just due to the vertical bracket notation (x coordinate goes with i-hat and y coordinate goes with j-hat)

- Linear dependence (added note):
    - If i-hat and j-hat are linearly dependent (one is a scaled version of the other), linear transformation squishes all 2D into the line where vectors sit
    - This is called the 1-D span of linearly dependent vectors

- Linear Trasformations summary:
    - A way to move around space such that gridlines remain parallel and such as the origin remains fixed
    - These transformations can be described using the coordinates where each basis vector lands
    - Matrices give us a way to describe these transformations, where columns represend those coordinates
    - Matrix vector multiplication is a way to compute what that transformation does to a given vector
    - Every time we see a Matrix we can interpret it as a certain transformation of space
---


