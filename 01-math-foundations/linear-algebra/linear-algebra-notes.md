# Linear Algebra

## Resources
- 3Blue1Brown: Essence of Linear Algebra (Videos 1-16)
- Khan Academy: Linear Algebra exercises

## Notation

**Symbols and Formatting:**
- Multiplication: *
- Dot product: ·
- Matrix dimensions: rows×columns (1×2, 2x3)
- Vector: squared brackets with comma to indicate verticality [1, 2]
- Matrix: squared brackets without comma [1 2]

**Variables:**
- Scalar: lowercase (a, b, c, x, y)
- Vector: lowercase (v, w, x)
- Matrix: uppercase (A, M)

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
    - Multiplying by -1.8: flips the vector around and stretches it by 1.8
    
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
    - Rare case: if the two original vectors line up, then the tip of the resulting vector is limited to this line
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
    - The 3rd vector must provide a component "out of" the plane formed by the first two vectors to span all of 3D space.
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
    - In these transformations, we only need to record where the basis vectors land
    
- Transformation Process:
    - Say a vector is represented as the sum of the two (scaled accordingly) basis-vectors i-hat and j-hat
    - Now lets transform and follow where the three vectors go
    - Linear transformations preserve the grid structure (parallel lines stay parallel, evenly spaced lines stay evenly spaced, origin stays fixed)
    - The transformed vector equals the sum of the two transformed basis-vectors, scaled using the same scalars as before (the original basis scalars we used to represent the original vector)
    - So basically the transformed result-vector equals the original scalar for i-hat multiplied by the transformed i-hat, plus the original scalar for j-hat multiplied by the transformed j-hat! 
    - In other words, if an original vector has coordinates x and y (i-hat and j-hat scalars), to find where it lands we multiply its original x coordinate by the new i-hat coordinates, plus its original y coordinate by the new j-hat coordinates
    - The final result is where the original vector landed
    - So we only need to know where the basis vectors landed, and we can deduce where any other vector landed, without visual aid
    - Any 2D Linear Transformation is described by just 4 numbers (the two coordinates where i-hat lands, and the two coordinates where j-hat lands), because linear transformations preserve linear combinations

- 2x2 Matrix:
    - We package the four numbers into a 2x2 grid
    - Two columns: where i-hat lands, and where j-hat lands
    - We can even define the process as Matrix Vector Multiplication
    - The multiplication formula order is not too clear, but it's actually just due to the vertical bracket notation (x coordinate goes with i-hat and y coordinate goes with j-hat)

- Linear dependence (added note):
    - If i-hat and j-hat are linearly dependent (one is a scaled version of the other), linear transformation squishes all 2D into the line where vectors sit
    - This is called the 1-D span of linearly dependent vectors

- Linear Trasformations summary:
    - A way to move around space such that grid lines remain parallel and evenly spaced
    - These transformations can be described using the coordinates where each basis vector lands
    - Matrices give us a way to describe these transformations, where columns represend those coordinates
    - Matrix vector multiplication is a way to compute what that transformation does to a given vector
    - Every time we see a Matrix we can interpret it as a certain transformation of space
    - In notation: if a vector v = x·î + y·ĵ, then after transformation: v' = x·î' + y·ĵ'

---

### Video 4: Matrix Multiplication as Composition

**Key Concepts:**

- Combine two transformations into one - Composite Function (longer way):
    - If we did them one by one, we would multiply the original vector by the first matrix (the firstly-transformed i-hat and j-hat), get an intermediate result of where the vector is now, and then multiply this intermediate vector by the second matrix (the secondly-transformed i-hat and j-hat) to get the final vector
    - We do this as: Matrix2*(Matrix1*vector) 
    - This is like the composite function f(g(x)) - read and done right to left

- Combine two transformations into one - Matrix Multiplication (faster, preferred way):
    - CompositeMatrix = (i-hat of Matrix1 * Matrix2) for composite i-hat; (j-hat of Matrix1 * Matrix2) for composite j-hat; which expands to:
    - CompositeMatrix i-hat = (x"scalar" of Matrix1 i-hat-vector * Matrix2 i-hat) + (y"scalar" of Matrix1 i-hat-vector * Matrix2 j-hat)
    - CompositeMatrix j-hat = (x"scalar" of Matrix1 j-hat-vector * Matrix2 i-hat) + (y"scalar" of Matrix1 j-hat-vector * Matrix2 j-hat)

- Symbolic representation of the above for calculations:
    - Written in notation: Matrix1 = M₁; Matrix2 = M₂
    - Column1 of (M₂M₁) = x₁(M₂ column1) + y₁(M₂ column2), where [x₁, y₁] is M₁'s column1
    - Column2 of (M₂M₁) = x₂(M₂ column1) + y₂(M₂ column2), where [x₂, y₂] is M₁'s column2

- Finalizing the calculation:
    - After we find Composite Matrix, we multiply it by the original vector
    - The result is where the original vector landed after both transformations

- Order importance: 
    - The order we do the intermediate calculation matters! 
    - "In CompositeMatrix [Matrix2 Matrix1], first apply Matrix1 and then Matrix2 - read right to left like function composition
    - Transformations are applied sequentially: Matrix1 first moves the basis vectors to new positions, then Matrix2 transforms those already-moved vectors. Reversing the order would mean that Matrix2 transforms the original basis vectors first, leading to different intermediate positions and thus a different final result.
    - In the intermediate stage, we treat the Matrix1's (not Matrix2's) i-hat and j-hat as regular vectors (since their value changed from implicit unit vectors to a different value), and we multiply each one of them by Matrix2
    - THEN we multiply the final Composite Matrix by the original vector

- Associativity:
    - Why does this work? Because in Linear Transformations we can use the same scalars of the original vector 
    - And because it is associative A(BC) = (AB)C, or in notation (M₂M₁)v = M₂(M₁v), we can pre-compute the composite matrix.
    - Meaning that, as long as we keep the correct cross-matrix calculation order, original vector (C) can be either multiplied with Matrix1 (B), and then their result multiplied with Matrix2 (A), or we can wait for Matrix1 (B) to be multiplied by Matrix2 (A), and then their result multiplied by original vector (C).
    
---

### Video 5: Three-dimensional Linear Transformations

**Key Concepts:**

- 3D Transformations:
    - So far we studied transformations from 2D vectors to 2D vectors
    - Transformations from 3D vectors to 3D vectors behave similarly
    - Now we have 3 basis vectors: i-hat for x-axis; j-hat for y-axis; k-hat for z-axis
    - Matrices are now 3x3
    - A 3x3 Matrix completely describes the transformation using only 9 numbers (which represent the 3 coordinates of where each of the 3 basis vectors ended up)

- Simple Transformations:
    - Same multiplication reasoning as with 2D: input vector * transformation
    - To see where our vector lands, we multiply the input vector coordinates by the corresponding columns of the matrix
    - Vector x-coordinate * transformed i-hat; vector y-coordinate * transformed j-hat; vector z-coordinate * transformed k-hat
    - And then we add together the three results

- Matrix Multiplication: 
    - For composite transformations, we can multiply two 3x3 matrices
    - First we apply the transformation encoded by the right Matrix, and then the left one

---

### Video 6: The Determinant

**Key Concepts:**

- The Determinant:
    - A way to measure how much the transformation stretches or squishes things
    - By measuring the factor by which the area of a given region increases or decreases (all areas are scaled uniformly)
    - The area of te unit square formed by the basis vectors is 1x1; if it increases to 2x3, the new area is 6
    - In this case, the linear transformation has scaled the area by 6
    - This scaling factor by which a linear transformation changes any area is called the determinant
    - Some transformations leave the area unchanged, like the shear that transforms a 1x1 square into a 1x1 parallelogram

- Usefulness:
    - If you know how much the unit square area changes, it can tell you how much the area of any possible region changes
    - What happens to one square happens to all no matter the size (because grid lines remain parallel and evenly shaped)
    - And anything that's not a grid square can be approximated by them (any region can be approximated by a collection of small grid squares)

- Cases: 
    - Usual: The determinant is a positive number. For example, a determinant of 3 means that the area is increased by a factor of 3; while a determinant of 0.5 reduces the area to half its original size
    - Also usual: The determinant is a negative number. Actually, the negative sign only means an invertion of orientation. The scaling factor is still only defined by the absolute value of the determinant
    - Less commonly: the determinant is 0. This means that the transformation squishes everything into a SMALLER DIMENSION! Either a line (1D), or a point (0D)

- Spotting inversion (2D):
    - The basis vector i-hat is always on the right of j-hat, while j-hat is on the left of i-hat. If this is reversed, it means the entire orientation has been inverted and the determinant will be negative.
    - Intuitively, we can think of the grid being squished as the determinant approaches 0, and expanding again on the other side after flipping, as the determinant becomes negative

- The Determinant in 3D:
    - Instead of areas, now volumes are what gets scaled
    - Instead of unit square, we have a unit cube 1x1x1 with edges resting on the basis vectors
    - Instead of square becoming a rectange, cube becomes a parallelepiped
    - Since the cube starts with the volume of 1 and the determinant gives the factor by which any volume is scaled, we can think of the determinant as the actual VOLUME of the parallelepiped the cube turns into
    - So the Determinant of [Matrix of scaled basis vectors] = the volume
    - Similar to 2D, a determinant of 0 means that space is squished into 0 volume and therefore into a SMALLER DIMENSION. In this case a flat plane (2D), a line (1D), or a point (0D)
    - As a reminder, this happens when Matrix columns are linearly dependent

- Spotting inversion (3D):
    - Use "right hand rule" to confirm positive determinant
    - Forefinger: i-hat direction
    - Middle finger: j-hat direction
    - Thumb up: k-hat direction
    - If left hand makes more sense: orientation has been flipped and the determinant is negative

- How to compute the Determinant (2D):
    - For 2D: In a 2x2 Matrix, where i-hat coordinates are a and c, and j-hat coordinates are b and d, the determinant = ad - bc
    - Why this formula? Since c = (y-coordinate of i-hat) and b = (x-coordinate of j-hat):
        - If both c and b are 0: Basis vectors simply stretch along their axes by factors a and d, forming a rectangle of area ad
        - If only one of c or b is 0: One basis vector stays on its axis while the other tilts, creating a vertical or horizontal shear. The parallelogram leans but maintains the same base (a) and perpendicular height (d), so area remains ad
        - If both c and b are non-zero: Neither basis vector stays axis-aligned—both tilt, creating a diagonal shear. The perpendicular height is no longer d because it's affected by how both vectors tilt
        - When c and b have the same sign, vectors tilt "together," reducing perpendicular height; opposite signs increase it
        - The formula ad - bc accounts for this: ad gives the "naive" rectangle area, bc corrects for the actual perpendicular height
    
- How to compute the Determinant (3D):
    - The 3D determinant can be broken down into three smaller 2D determinant problems
    - Take each value from the first row (a,b,c) and pair it with a 2×2 determinant calculated from the remaining values
    - Form each 2×2 determinant by deleting the row and column of its paired coordinate:
        - a · det([[e,f],[h,i]]) - delete row 1 and column 1
        - b · det([[d,f],[g,i]]) - delete row 1 and column 2
        - c · det([[d,e],[g,h]]) - delete row 1 and column 3
    - Combine with alternating signs: determinant = a·(ei - fh) - b·(di - fg) + c·(dh - eg)

---

### Video 7: Inverse Matrices, Column Space and Null Space

**Key Concepts (with additional notes):**

- Linear systems of equations:
    - Linear Algebra lets us solve certain systems of equations (like 3 systems with 3 variables each)
    - Variables are scaled by some constant, and those scaled variables are added to each other
    - No exponents, variable multiplications and other complex forms
    - To prepare our equations, align variables on the left, constants on the right
    - Vertically line up similar variables, adding 0 coefficients if necessary
    - Linear systems of equations look like vector Matrix multiplication

- Linear systems as Matrices:
    - We can package all equations together into a single vector equation (of the form Matrix * vector)
    - This "constant" Matrix will contain all the coefficients (we will call it Matrix A)
    - The vector will hold all the variables (we will call it vector x)
    - Their matrix-vector product will hold a new "constant" vector (we will call it vector v)
    - In this way, the simplified representation of this matrix-vector equation is: Ax = v

- Geometric interpretation of the problem:
    - The Matrix A corresponds to some linear transformation (because that's what a Matrix is!)
    - As we know, the Matrix columns represent the position of the basis vectors after the transformation has taken place (so columns are the transformed basis vectors)
    - And to find where any other vector has landed, we multiply this vector's starting position by the transformation Matrix (transformation Matrix * known starting vector = unknown landing position)
    - The resulting vector is where the initial vector has landed
    - Solving for Ax = v means that we are doing the reverse calculation (transformation Matrix * unknown starting vector = known landing position)
    - Normal case: A * x = ? (find where x lands)
    - Reverse case: A * ? = v (find what lands on v)
    - So we are looking for a starting vector X which, after the transformation, lands on v

- Cases:
    - The determinant is non-0: most commonly; keeps the existing dimension
    - The determinant is 0: space is squished into a lower dimension
    
- Non-0 determinant:
    - In this case there will always be one and only one starting vector x that lands on v
    - We can find it by playing the transformation IN REVERSE
    - "Which vector x would we find, if we went backwards from v and played the transformation in reverse?"
    - Inverse transformation is just another tranformation itself
    - A-inverse is the unique transformation with the property that if you first apply A and then A-inverse, you end up back where you started 
    - As we know, applying one transformation after another is captured algebraically with Matrix multiplication (followed by multiplying the final transformation by the original vector)
    - So A-inverse * A = remaining in place
    - The composite Matrix that corresponds to "doing nothing" is the identity transformation
    - So A-inverse * A = identity transformation (A⁻¹A = I)
    
- Non-0 det calculation process:
    - Once we have the inverse, we can solve by multiplying A-inverse * v:
        - Ax = v 
        - A-inverse * A * x = A-inverse * v
        - A-inverse and A cancel out (identity transformation)
        - x = A-inverse * v
        - So now this means we are playing the transformation in reverse and following v
    - In practice, we use computers to find the inverses of transformations
    - Example: Say we have the equations 2x + 3y = 8 and 1x + 2y = 5
        - This is the Matrix equation: [[2,3], [1,2]] times [x,y] = [8,5]
        - Find the inverse of [[2,3], [1,2]] (using a computer or formula)
        - Multiply: inverse times [8,5] gives [x,y] = [1,2]
        - Check: 2(1) + 3(2) = 8 ✓ and 1(1) + 2(2) = 5 ✓
    - So for non-0 determinant, if we have 2 unknowns and 2 equations, it's almost certainly the case that there is a single unique solution
    - This is also the case in higher dimensions, when the number of equations equals the number of unknowns

- When determinant is 0:
    - In this case, there is no inverse. For instance in 2D, we cannot "unsquish" a line to turn it into a plane!
    - At least not with any function. To do that, we would have to transform each individual vector into a full line of vectors
    - But functions can only take a single input to a single output; they cannot map to multiple vectors
    - So a determinant of 0 means that the transformation is non-invertible or "singular"
    - Solutions can exist even without an inverse, if for example 2D gets squished into a line, and vector V is on that line
    
- Rank and column space:
    - Rank is the number of dimensions in the output of a transformation
        - Rank 1: When the output of a transformation is a 1D line
        - Rank 2: When the output of a transformation is a 2D plane
        - Rank 3: When the output of a transformation is a 3D space
    - The set of all possible outputs for our Matrix Av (1D line, 2D plane, 3D space) is the "column space" of our Matrix (also sometimes called the "range" or "image" of the transformation)
    - Why? Because the columns of a Matrix tell us where the basis vectors land
    - And the span of those transformed basis vectors gives us all possible outputs
    - So span of Matrix columns = column space
    - And rank is the number of dimensions in the column space
    - Full-rank Matrix: when rank equals the number of Matrix columns, it is as high as can be for that dimension

- Full rank cases: 
    - For square matrices, "full rank" means that the transformation preserves the dimension, the determinant is non-0 and the inverse exists
    - For non-square matrices, "full rank" means the maximum possible rank, where rank cannot exceed the smaller of the two dimensions (rows or columns); and it does not guarantee invertibility
    - Why? Because rank represents the dimension of the output space we actually reach, and we are limited by:
        - How many independent directions we start with (columns = input dimension)
        - How many independent directions we can express in the output (rows = output dimension)
        - We can't create more independent directions than we started with, AND we can't express more independent directions than the output space allows.
        - Therefore, 3x5 and 5x3 matrices both have a rank of 3

- Null space:
    - The 0 vector is always included in the column space (because the origin remains fixed)
    - The set of vectors that lands on the origin is called the "null space" or "kernel" of the Matrix
    - It is the space of all vectors that become null (land on the 0 vector)
    - For a full-rank transformation, the only vector that lands at the origin is the 0 vector itself
    - But for matrices that aren't full rank (which squish space into a smaller dimension), we can have many vectors that land on 0
    - If a 2D transformation squishes space onto a 1D line, there is a separate line (in a different direction) full of vectors that get squished onto the origin
    - If a 3D transformation squishes space onto a 2D plane, there is also a line full of vectors that land on the origin
    - So for instance, if a 3×3 matrix has rank 2, the dimension of its null space is a 1D line 
    - If a 3D transformation squishes space onto a 1D line, there is a PLANE full of vectors that land on the origin
    - Rank-nullity theorem: For any matrix, number of columns - rank = null space dimension
    - Why? 3×3 with rank 2 means null space dimension is 1 (because 3 - 2 = 1)
    - A 5×7 matrix with rank 4 means null space dimension is 3 (because 7 - 4 = 3)

- Null space in equations:
    - In terms of a linear system of equations, the null space gives us all the possible solutions to the Ax = 0 equation
    - For the general solution to Ax = v, we need the particular solution + the null space.
    - Why? If a 3D transformation squishes onto a 2D plane, and v is on that 2D plane, then there is an entire LINE of starting vectors that all landed on v! That line is parallel to the null space line. So if we pick any point on that line, it's a solution for v. 
    - So we do: find one vector that lands on v + null space = line of vectors that land on v
    - This is shifting the null space line so it passes through our particular solution point
    - If the null space is a line through the origin, our solution line is that same line but translated so it passes through our particular solution instead of through the origin
    - The particular solution (one vector that satisfies Ax = v)
    - Plus the null space (all solutions to the homogeneous equation Ax = 0)
    - Equals the general solution (all vectors that satisfy Ax = v)

- Summary:
    - We can think of linear systems of equations geometrically
    - Each system has a linear transformation associated with it 
    - When transformation has an inverse, we can use it to solve the system
    - Otherwise, column space lets us understand when a solution even exists (when v is on the column space)
    - And the idea of null space helps us understand what the set of all possible solutions can look like

---

### Video 8: Non-square matrices as transformation between dimensions

**Key Concepts:**

- Transformations can happen between dimensions
- Again, grid line remain parallel and evenly spaced, and the origin maps to the origin
- If 3 rows (3 landing coordinates: x-row, y-row, z-row) and 2 columns (2 basis vectors): 3x2 Matrix goes from 2D to 3D
- The span of columns or column space (the place all vectors land) is a 2D plane slicing through the origin of 3D space
- BUT the Matrix is still full rank because the number of dimensions in the column space (2) equals the number of dimensions in the input space (2)
- So a 3x2 Matrix maps 2 dimensions to 3 dimensions
- Conversely, a 2x3 Matrix maps 3 dimensions to 2 dimensions (2 rows as 2 coordinates and 3 columns as 3 basis vectors)
- We could also have a transformation from 2D to 1D, on a 1x2 Matrix (1 row for x coordinate only, 2 rows as basis vectors)
- Regarding the fact that grid lines remain parallel and evenly spaced, in 1D there are no grid lines, but this property is retained: if you have a line of evenly spaced dots on the 2D plane, it would remain evenly spaced once they've mapped onto the number line


**Additional note: 3x3 Matrix with rank 2 VS 2x3 Matrix with rank 2**

- 3x3 Matrix with rank 2:
  - 3×3 Matrix maps 3D space to 3D space (same dimensional space):
    - When rank = 2, it squishes the full 3D input onto a 2D plane embedded in 3D
    - Output lives in 3D but is constrained to a 2D plane (like a sheet of paper floating in a room)
    - Analogy: Taking a 3D sculpture and flattening it against a wall in a 3D room. The flattened result is still "in the room" (3D), just stuck to a 2D surface
    - Null space is a line through origin, WITHIN the 3D input/output space and perpendicular to the output plane
    - So 3×3 matrix with rank 2:
        - Input: vector [x, y, z] in 3D
        - Output: vector [x+z, y, 0] in 3D (on the xy-plane within 3D space)
        - The output has 3 components, third is always 0: [1 0 1] [0 1 0] [0 0 0]

- 2x3 Matrix with rank 2:
    - 2×3 Matrix maps 3D space to 2D space (different dimensional space):
    - The output lives in flat 2D world, not a plane embedded in 3D
    - Even at what is now considered a full rank (rank 2), you're going from 3D down to 2D
    - 2×3 with rank 2: Output lives in 2D entirely (like actual flatland - no third dimension exists)
    - Null space is a line in the 3D input space, that collapses to zero in the 2D output space
    - Analogy: Taking a 3D sculpture and projecting its shadow onto a piece of paper. The shadow exists in actual 2D space 2D, not as a plane in 3D
    - 2x3 matrix with rank 2:
        - Input: vector [x, y, z] in 3D
        - Output: vector [x+z, y] in 2D (just 2 components, living in flat 2D)
        - No third component exists at all: [1 0 1] [0 1 0]
        
---

### Video 9: Dot products and Duality

**Key Concepts:**

- Dot product numerically:
    - If you have two vectors of the same dimension, taking their dot product means:
        - starting with: [2, 7, 1] · [8, 2, 8]
        - pairing up all of the coordinates: [2, 8] [7, 2] [8, 1]
        - multiplying those pairs together: 2 * 8, 7 * 2, 1 * 8
        - and adding the results: 2 * 8  +  7 * 2  +  1 * 8

- Dot product geometrically:
    - If the two vectors have the same direction:
        - their dot product is positive (v · w > 0)
        - imagine projecting w onto the line that passes through the origin and the tip of v
        - multiplying the length of this projected w by the length of v, we get the dot product v · w
    - If the two vectors have the opposite direction:
        - their dot product is negative (v · w < 0)
        - imagine the projection of w pointing in the opposite direction from v
        - the w vector will have negative coordinates, so their product will be naturally negative
    - If the two vectors are perpendicular to each other;
        - their dot product is zero (v · w = 0)
        - imagine the projection of w into v, disappears into the 0 vector
        - since the coordinates of w are 0, their product will be 0
    - The length of projected w is: |w| * cos(θ) so the total calculation is |v| * |w| * cos(θ)

- Order doesn't matter:
    - Initially we would think that the above interpretation is asymmetric and treats the two vectors differently
    - However, the order of multiplying for the dot product does not matter
    - Instead of projecting w onto v, we could: project v onto w, multiply the length of projected v by the length of w and get the same result
    - Explanation: 
        - if w and v had the same length, we could leverage some symmetry and say that no matter which vector we chose to project, their dot product would be the same
        - if we scaled one of them by 2, for example w · 2v, that symmetry would break
        - but actually, the ratio of changes would still balance out in the end
        - if we projected w onto 2v, the length of projected w would stay the same, while the length of v would double
        - so their dot product 2v · w would be exactly twice that of v . w and would result in 2 (v · w)
        - if we projected 2v onto w instead, now the length of projected 2v is what gets scaled, while the actual length of w would stay constant, resulting again in 2 (v · w)
        - so the overall effect in both cases is to just double the dot product        

- Numerical and Geometrical relationship:

    - How does the numerical process of matching coordinates, multiplying the pairs and adding them, is related to geometrical projection:
        - the answer comes from the concept of DUALITY

    - Geometric operation:
        - Linear Transformations that go from 2D to 1D, are functions that take in a 2D vector and return a single number
        - but Linear Transformations have some restrictions
        - in the case of 2D to 1D, if you take a diagonal line of evenly spaced dots and apply a transformation, if it's linear the dots will remain evenly spaced in the output line
        - one of these linear transformations is completely determined by where it takes i-hat and j-hat
        - in this case they land on a number each
        - so when we record them in a matrix it will be a 1x2 matrix: [2 1]
    
    - Applying this transformation to a vector:
        - imagine a linear transformation that takes i-hat to 1 and j-hat to -2
        - to follow an original vector of coordinates [4, 3], we can break it into 4i-hat + 3j-hat (since the basis vectors have a unit of 1)
        - after the transformation, due to linearity the vector will be 4 * [where i-hat lands (1)], plus 3 * [where j-hat lands (-2)], so 4 * 1  +  3 * (-2), so 4 + (-6), resulting in -2
        - just like where j-hat landed! (the original vector was longer and diagonal to j-hat)
       
    - Numerical operations:
        - when we do this calculation purely numerically, it's a matrix vector multiplication
        - we multiply a 1x2 matrix by a vector [1 -2] * [4, 3] = 4 * 1 + 3 * (-2)
        - and it's just like taking the dot product of two vectors [1, -2] * [4, 3]
        - so there is a nice association between 1x2 (2D -> 1D) matrices and 2D vectors
        - we can tilt the numerical representation of a vector on its side to get the associated matrix, or tip the matrix back up to get the associated vector
        - so there is a connection between linear transformations that take vectors to numbers, and vectors THEMSELVES!

- Another way to see the connection:

    - Define a linear transformation from 2D to 1D:
        - let's say we didn't know that a dot product relates to projection
        - place a numberline copy diagonally in space, with 0 at the origin
        - think of the 2D unit vector whose tip sits at 1 on that line, let's call it u-hat
        - if we project 2D vectors straight onto this diagonal line, we just defined a function that takes 2D vectors to numbers (2D to 1D)!
        - and this function is actually linear, since it passes our visual test that any line of evenly spaced dots remains evenly spaced once it lands on the number line
        - remember that the output of the function are numbers, not 2D vectors, as we are in 1D
        - the function takes 2 coordinates and outputs one
        - u-hat is a diagonal 2D vector of the input space that overlaps with the embedding of the number line
    
    - Find the associated Matrix:
        - now let's try to find, WHERE did the basis vectors landed? 
        - if we find that, we will find the 1x2 matrix that describes this transformation
        - but the only information we have is where u-hat landed (1)
        - we know that i-hat and j-hat are both unit vectors, and the angle between them is the same regardless of which you project onto which
        - the projection of a unit vector onto another unit vector equals the cosine of the angle between them: i-hat · u-hat = cos(θ) = ux (the x-component of u-hat)
        - therefore, projecting i-hat into the line that passes through u-hat, is symmetric to projecting u-hat into the x-axis (so taking the x-coordinate of u-hat: ux)
        - and so they land on the SAME number on their respective projection lines (ux)
        - this reasoning is similar for the j-hat case
        - using symmetry in this way we find that [ux uy] is where i-hat and j-hat landed 
        - therefore, the 1x2 matrix describing the transformation are actually the coordinates of u-hat!
        - so more generally, computing this projection transformation for any arbitrary vector in space, and multiplying the matrix by that vector [ux uy] * [x, y] = ux·x + uy·y, is computationally identical to taking a dot product of the vector and u-hat! [ux, uy] * [x, y] = ux·x + uy·y
        - this is why taking the dot product of a vector and a unit vector, can be interpreted as PROJECTING a vector onto the SPAN of that unit vector and taking the projection length

    - Non-unit vectors:
        - now let's see scaled vectors
        - let's say we have a vector 3u-hat
        - following a similar reasoning as before, its coordinates will be [3ux, 3uy]
        - and its associated transformation matrix will be [3ux 3uy]
        - looking at the matrix, it takes i-hat and j-hat to 3 times the values where they landed before
        - due to linearity, this new matrix can be interpreted as projeting ANY vector onto the numberline copy, and multiplying where it lands by 3
        - this is why the dot product with a non-unit vector can be interpreted as first projecting onto that vector, and then scaling up the length of that projection by the length of the vector
        
    - Process summary:
        - we had a linear transformation from 2D to 1D
        - NOT defined in terms of numerical vectors or numerical dot products
        - just defined by projecting space on to a diagonal copy of the numberline 
        - but because the transformation is linear, it was NECESSARILY described by some 1x2 Matrix
        - since multiplying a 1x2 matrix by a 2D vector is the same as turning that matrix on its side and taking the dot product, this transformation was RELATED to some vector
        - in conclusion, any time we have one of these linear transformations where output space is the number line, no matter how it was defined, there will be some unique vector v corresponding to that transformation, in the sense that applying the transformation is the same thing as taking a dot product with that vector

    - Duality:
        - the DUAL of a vector is the linear transformation it encodes
        - the DUAL of a linear transformation from some space to 1D is a certain vector in that space
        - Why does duality work? The fundamental reason is that the dual space (space of linear functionals) has the same dimension as the original space. In finite dimensions, this creates a natural isomorphism
        

- Summary of important concepts:
    - The dot product is a very useful geometrical tool for:
        - understanding projections
        - test whether or not vectors tend to point in the same direction
    - In a deeper level, dotting two vectors together is a way to translate one of them into the world of transformations
    - Vectors are not just arrows in space, but also the physical embodiment or conceptual shorthand, of a linear transformation


**Additional notes:**

-  When we compute v · w, we are using v as a measuring stick to see how much of w aligns with v's direction.
- Every vector w can be broken into components: w = (component along v) + (component perpendicular to v)
- The dot product v · w extracts only the first part and filters out everything perpendicular to v
- The duality reveals that every vector defines a way to "measure" other vectors
- When we compute v · w, we are essentially asking: "How much does w contribute in the v-direction?"
- This is why dot products appear everywhere; they're the natural way to decompose vectors into components
