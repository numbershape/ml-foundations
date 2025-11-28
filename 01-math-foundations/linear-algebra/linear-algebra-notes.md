# Linear Algebra

## Resources
- 3Blue1Brown: "Essence of Linear Algebra" series
- Claude Sonnet 4.5: Supporting tool for further investigation and additional notes

## Notation

**Symbols and Formatting:**
- Multiplication: *
- Dot product: ·
- Cross product: X
- Direct sum: ⊕
- Matrix dimensions: rows×columns (1×2, 2x3)
- Vector: [1, 2] (comma indicates vertical stacking)
- Matrix: [a b; c d] where a b and c d are rows
    - row elements separated by spaces [a b] 
    - rows separated by semicolon [a b; c d]
    - columns separated by comma [a, c]

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
    - Example: "Walk 1 to the right, then two up, then 3 to the right, then 1 down"
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
    - The span of most pairs of 2D vectors is all vectors of 2D space (remember rare case: all vectors whose tips sits on a straight line)
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

- 2x2 Matrix-Vector Multiplication:
    - We package the four numbers into a 2x2 grid
    - Two columns: where i-hat lands, and where j-hat lands
    - We can even define the process as Matrix-Vector Multiplication
    - The multiplication formula order is due to the vertical bracket notation (x coordinate goes with i-hat and y coordinate goes with j-hat)
    - For a Matrix-vector multiplication with Matrix ***[a b; c d] * [x, y]*** vector, we do ***x * [a, c] + y * [b, d]***, which equals the resulting vector ***[ax+by, cx+dy]***

- Linear dependence (added note):
    - If i-hat and j-hat are linearly dependent (one is a scaled version of the other), linear transformation squishes all 2D into the line where vectors sit
    - This is called the 1D span of linearly dependent vectors

- Linear Trasformations summary:
    - A way to move around space such that grid lines remain parallel and evenly spaced
    - These transformations can be described using the coordinates where each basis vector lands
    - Matrices give us a way to describe these transformations, where columns represend those coordinates
    - Matrix vector multiplication is a way to compute what that transformation does to a given vector
    - Every time we see a Matrix we can interpret it as a certain transformation of space
    - In standard notation: if a vector v = x·i + y·ĵ, then after transformation: v' = x·î' + y·ĵ'

---

### Video 4: Matrix Multiplication as Composition

**Key Concepts:**

- Combine two transformations into one - Composite Function (longer way):
    - If we did them one by one, we would multiply the original vector by the first matrix (the firstly-transformed i-hat and j-hat), get an intermediate result of where the vector is now, and then multiply this intermediate vector by the second matrix (the secondly-transformed i-hat and j-hat) to get the final vector
    - We do this as: Matrix2*(Matrix1*vector) 
    - This is like the composite function f(g(x)) - read and done right to left

- Combine two transformations into one - Matrix Multiplication (faster, preferred way):
    - Composite_Matrix = (i-hat of Matrix1 * Matrix2) for composite i-hat; (j-hat of Matrix1 * Matrix2) for composite j-hat; which expands to:
    - Composite_Matrix i-hat = (x "scalar" of Matrix1 i-hat-vector * Matrix2 i-hat) + (y "scalar" of Matrix1 i-hat-vector * Matrix2 j-hat)
    - Composite_Matrix j-hat = (x "scalar" of Matrix1 j-hat-vector * Matrix2 i-hat) + (y "scalar" of Matrix1 j-hat-vector * Matrix2 j-hat)

- 2x2 Matrix-Matrix Multiplication:
    - Matrix2 = [a b; c d]
    - Matrix1 = [e f; g h]
    - We break down Matrix1 into two intermediate vectors, multiply each by Matrix2, and get a resulting vector each
        - [a b; c d] * [e, g] ->  e * [a, c] + g * [b, d] ->  [ae, ce] + [bg, dg] ->  vector [ae+bg, ce+dg]
        - [a b; c d] * [f, h] ->  f * [a, c] + h * [b, d] ->  [af, cf] + [bh, dh] ->  vector [af+bh, cf+dh]
    - Composite_Matrix is: [ae+bg af+bh; ce+dg cf+dh]
    - After we find Composite_Matrix, we multiply it by the ORIGINAL vector: ***[ae+bg af+bh; ce+dg cf+dh] * [x, y]***
    - The result is where the original vector landed after both transformations

- Order importance: 
    - The order we do the intermediate calculation matters! 
    - In Composite_Matrix [Matrix2 Matrix1], first apply Matrix1 and then Matrix2 - read right to left like function composition
    - Transformations are applied sequentially: Matrix1 first moves the basis vectors to new positions, then Matrix2 transforms those already-moved vectors. Reversing the order would mean that Matrix2 transforms the original basis vectors first, leading to different intermediate positions and thus a different final result
    - In the intermediate stage, we treat the Matrix1's (not Matrix2's) i-hat and j-hat as regular vectors (since their value changed from implicit unit vectors to a different value), and we multiply each one of them by Matrix2
    - THEN we multiply the final Composite_Matrix by the original vector

- Associativity:
    - Why does this work? Because in Linear Transformations we can use the same scalars of the original vector 
    - And because it is associative A(BC) = (AB)C, or (Matrix2 * Matrix1) * vector = Matrix2 (Matrix1 * vector), we can pre-compute the composite matrix.
    - Meaning that, as long as we keep the correct cross-matrix calculation order, original vector (C) can be either multiplied with Matrix1 (B), and then their result multiplied with Matrix2 (A), or we can wait for Matrix1 (B) to be multiplied by Matrix2 (A), and then their result multiplied by original vector (C).
    
---

### Video 5: Three-dimensional Linear Transformations

**Key Concepts:**

- 3D Transformations:
    - So far we studied transformations from 2D vectors to 2D vectors
    - Transformations from 3D vectors to 3D vectors behave similarly
    - Now we have 3 basis vectors: i-hat for x-axis; j-hat for y-axis; k-hat for z-axis
    - Matrices are now 3x3
    - A 3x3 Matrix completely describes the transformation using only 9 numbers (which represent the 3 coordinates of where each of the 3 basis vectors end up)

- 3x3 Matrix-Vector Multiplication (Simple Transformations):
    - Same multiplication reasoning as with 2D: input vector * transformation
    - To see where our vector lands, we multiply the input vector coordinates by the corresponding columns of the matrix
    - For a Matrix-vector multiplication with a 3x3 Matrix, we do ***vector x-coordinate * transformed i-hat; plus vector y-coordinate * transformed j-hat; plus vector z-coordinate * transformed k-hat***, to find the resulting vector

- 3x3 Matrix-Matrix Multiplication: 
    - For composite transformations, we can multiply two 3x3 matrices
    - Order: first we apply the transformation encoded by the right Matrix, and then the transformation encoded by the left one
    - Calculation process follows the same logic as in 2x2 Matrix-Matrix Multiplication

---

### Video 6: The Determinant

**Key Concepts:**

- The Determinant:
    - A way to measure how much the transformation stretches or squishes things, by measuring the factor by which the area of a given region increases or decreases (all areas are scaled uniformly)
    - The area of the unit square formed by the basis vectors is 1x1; if it increases to 2x3, the new area is 6
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
    - Instead of square becoming a rectangle, cube becomes a parallelepiped
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
    - For 2D: In a 2x2 Matrix [a b; c d], where i-hat coordinates are a c, and j-hat coordinates are b d, the 2D determinant equals: ***ad - bc***
    - Why this formula? Since c = (y-coordinate of i-hat) and b = (x-coordinate of j-hat):
        - If both c and b are 0: Basis vectors simply stretch along their axes by factors a and d, forming a rectangle of area ad
        - If only one of c or b is 0: One basis vector stays on its axis while the other tilts, creating a vertical or horizontal shear. The parallelogram leans but maintains the same base (a) and perpendicular height (d), so area remains ad
        - If both c and b are non-zero: Neither basis vector stays axis-aligned, both tilt creating a diagonal shear. The perpendicular height is no longer d because it's affected by how both vectors tilt
        - When c and b have the same sign, vectors tilt "together," reducing perpendicular height; conversely, opposite signs increase it
        - The formula ad - bc accounts for this: ad gives the "naive" rectangle area, bc corrects for the actual perpendicular height
    
- How to compute the Determinant (3D):
    - For 3D: In a 3x3 Matrix, the 3D determinant can be broken down into three smaller 2D determinant problems
    - Take each value from the first row (a,b,c) and pair it with a 2×2 determinant calculated from the remaining values
    - Form each 2×2 determinant by deleting the row and column of its paired coordinate:
        - a · det([e f; h i]) - delete row 1 and column 1
        - b · det([d f; g i]) - delete row 1 and column 2
        - c · det([d e; g h]) - delete row 1 and column 3
    - Calculate: value * (up left * down right) - (up right * down left)
        - a · det([e f; h i]) = a·(ei - fh)
        - b · det([d f; g i]) = b·(di - fg)
        - c · det([d e; g h]) = c·(dh - eg)
    - Combine the results of the three 2x2 determinants, with alternating signs (+, -, +) to get the final 3D determinant
    - The final 3D determinant equals: ***a·(ei - fh) - b·(di - fg) + c·(dh - eg)***

- How to compute the Determinant (3D) alternatively:
    - Instead of taking a value from each row, we can get a value from each column instead
    - Calculate in a similar way, but now the values are a, d and g, and the 2x2 matrices are formed by the rest of the values
    - The final 3D determinant equals: ***a·(ei − fh) − d·(bi − ch) + g·(bf − ce)***
    - If we want to get rid of the - sign, we can invert the values inside the parenthesis, for example: − d·(bi − ch) = + d·(ch - bi)
    - The resulting vector is the same as when calculating based on rows

---

### Video 7: Inverse Matrices, Column Space and Null Space

**Key Concepts (with additional notes):**

- Linear systems of equations:
    - Linear Algebra lets us solve certain systems of equations (like 3 systems with 3 variables each)
    - Variables are scaled by some constant, and those scaled variables are added to each other
    - No exponents, variable multiplications and other complex forms
    - To prepare our equations, align variables on the left, constants on the right
    - Vertically line up similar variables, adding 0 coefficients if necessary

- Linear systems as Matrices:
    - Linear systems of equations look like Matrix-vector multiplication
    - We can package all equations together into a single vector equation (of the form Matrix * vector)
    - This "constant" Matrix will contain all the coefficients (we will call it Matrix A)
    - The vector will hold all the variables (we will call it vector x)
    - Their matrix-vector product will hold a new "constant" vector (we will call it vector v)
    - In this way, the simplified representation of this matrix-vector equation is: ***Ax = v***

- Geometric interpretation of the problem:
    - The Matrix A corresponds to some linear transformation (because that's what a Matrix is!)
    - As we know, the Matrix columns represent the position of the basis vectors after the transformation has taken place (so columns are the transformed basis vectors)
    - And to find where any other vector has landed, we multiply this vector's starting position by the transformation Matrix (transformation Matrix * known starting vector = unknown landing position)
    - The resulting vector is where the initial vector has landed
    - Solving for Ax = v means that we are doing the reverse calculation (transformation Matrix * unknown starting vector = known landing position)
    - Normal case: A * x = ? (find where x lands)
    - Reverse case: A * ? = v (find what lands on v)
    - So we are looking for a starting vector x which, after the transformation, lands on v

- Cases:
    - The determinant is non-0: most commonly; keeps the existing dimension
    - The determinant is 0: space is squished into a lower dimension
    
- Non-0 determinant:
    - In this case there will always be one and only one starting vector x that lands on v
    - We can find it by playing the transformation IN REVERSE
    - "Which vector x would we find, if we went backwards from v and played the transformation in reverse?"
    - Inverse transformation is just another tranformation itself
    - A-inverse is the unique transformation with the property that if you first apply A and then A-inverse, you end up back where you started 
    - As we know, applying one transformation after another is captured algebraically with Matrix Multiplication (followed by multiplying the final transformation by the original vector)
    - So A-inverse * A = remaining in place
    - The composite Matrix that corresponds to "doing nothing" is called the "identity transformation"
    - So A-inverse * A = identity transformation (standard notation: A⁻¹A = I)
    
- Non-0 det calculation process:
    - Once we have the inverse, we can solve by multiplying A-inverse * v:
        - Ax = v 
        - A-inverse * A * x = A-inverse * v
        - A-inverse and A cancel out (identity transformation)
        - ***x = A-inverse * v***
        - So now this means we are playing the transformation in reverse and following v back to its original place
    - In practice, we use computers to find the inverses of transformations
    - Example: Say we have the equations 2x + 3y = 8 and 1x + 2y = 5
        - This is the Matrix equation: [2 3]; [1 2] * [x, y] = [8, 5]
        - Find the inverse of [2 3]; [1 2] (using a computer or formula)
        - Multiply: inverse * [8, 5] = [x, y] = [1, 2]
        - Check: 2(1) + 3(2) = 8 ✓ and 1(1) + 2(2) = 5 ✓
    - So for non-0 determinant, if we have 2 unknowns and 2 equations, it's almost certainly the case that there is a single unique solution
    - This is also the case in higher dimensions, when the number of equations equals the number of unknowns

- When determinant is 0:
    - In this case, there is no inverse. For instance in 2D, we cannot "unsquish" a line to turn it into a plane!
    - At least not with any function. To do that, we would have to transform each individual vector into a full line of vectors
    - But functions can only take a single input to a single output; they cannot map to multiple vectors
    - So a determinant of 0 means that the transformation is non-invertible or "singular"
    - Solutions can exist even without an inverse, if for example 2D gets squished into a line, and vector v is ON that line
    
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
 
- Full rank cases: 
    - For square matrices, "full rank" means that the transformation preserves the dimension, the determinant is non-0 and the inverse exists
    - For non-square matrices, "full rank" means the maximum possible rank, where rank cannot exceed the smaller of the two dimensions (rows or columns); and it does not guarantee invertibility
    - Why? Because rank represents the dimension of the output space we actually reach, and we are limited by:
        - How many independent directions we start with (columns = input dimension)
        - How many independent directions we can express in the output (rows = output dimension)
        - We can't create more independent directions than we started with, AND we can't express more independent directions than the output space allows.
        - Therefore, 3x5 and 5x3 matrices both have a rank of 3

- Full-rank definition:
    - Remember that rows = landing coordinates, and columns = amount of basis vectors
    - A Matrix is "full rank" when rank is as high as possible for that matrix shape
        - A tall matrix (3×2) takes 2D inputs and produces 3D outputs. The rank gives us the dimension of the output space. In this case, rank = number of columns
        - A square matrix (3x3) rank = number of columns too
        - A wide matrix (2×3) takes 3D inputs and produces 2D outputs. The rank tells you the dimension of the output space. So in this case, rank = number of rows
        - In short: rank ≤ min(rows, columns)
    - A matrix is not full rank, if and only if it has linear dependencies
        - if rank is less than the number of columns, that means you have fewer independent columns than total columns, which means at least one column can be written as a combination of others
        - this connects to the rank-nullity theorem we are about to see below (rank + nullity = number of columns), as when nullity is > 0, it means linear dependencies exist among the columns
    - Example with a 3x4 matrix:
        - full rank (3) means we moved from 4D to 3D and now we have just 3 linearly independent columns (the 4th is now linearly dependent on the first 3)
        - not full rank (<3) means we have fewer than 3 independent columns, meaning multiple dependencies exist

- Null space:
    - When we multiply a matrix by an input vector, the column space is the set of all possible outputs
    - When we multiply the matrix by the zero vector input, we get the zero vector as output (A * 0 = 0). So the initial 0 vector is always included in the column space
    - The set of vectors that lands on the origin is called the "null space" or "kernel" of the Matrix
    - It is the space of all vectors that become null (land on the 0 vector)
    - For a full-rank transformation, the only vector that lands at the origin is the 0 vector itself
    - But for matrices that aren't full rank (which squish space into a smaller dimension), we can have many vectors that land on 0
        - If a 2D transformation squishes space onto a 1D line, there is a separate line (in a different direction) full of vectors that get squished onto the origin
        - If a 3D transformation squishes space onto a 2D plane, there is also a line full of vectors that land on the origin
        - So for instance, if a 3×3 matrix has rank 2, the dimension of its null space is a 1D line 
        - If a 3D transformation squishes space onto a 1D line, there is a PLANE full of vectors that land on the origin
    - Rank-nullity theorem: For any matrix, ***number of columns - rank = null space dimension***
    - Why? 3×3 matrix with rank 2 means null space dimension is 1 (because 3 - 2 = 1)
    - A 5×7 matrix with rank 4 means null space dimension is 3 (because 7 - 4 = 3)

- Null space in equations:
    - In terms of a linear system of equations, the null space gives us all the possible solutions to the Ax = 0 equation
    - For the general solution to Ax = v, we need the particular solution + the null space.
    - Why? If a 3D transformation squishes onto a 2D plane, and v is on that 2D plane, then there is an entire LINE of starting vectors that all landed on v! That line is parallel to the null space line. So if we pick any point on that line, it's a solution for v. 
    - So we do: ***find one vector that lands on v + null space = line of vectors that land on v***
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

- Transformations can happen between dimensions, represented by non-square matrices
- Again, grid line remain parallel and evenly spaced, and the origin maps to the origin
- If we have 3 rows (3 landing coordinates: x-row, y-row, z-row) and 2 columns (2 basis vectors): 3x2 Matrix goes from 2D to 3D
- The span of columns or column space (the place all vectors land) is a 2D plane slicing through the origin of 3D space
- But the Matrix is still full rank, because the rank equals the smaller dimension, which in this 3×2 case is the number of columns (2), assuming both columns are linearly independent (neither is a scalar of the other)
- Conversely, a 2x3 Matrix maps 3D to 2D (2 rows as 2 coordinates and 3 columns as basis vectors)
- We could also have a transformation from 2D to 1D, on a 1x2 Matrix (1 row for x coordinate only, 2 rows as basis vectors)
- Regarding the fact that grid lines remain parallel and evenly spaced, in 1D there are no grid lines, but this property is retained: if you have a line of evenly spaced dots on the 2D plane, it would remain evenly spaced once they've mapped onto the number line


**Additional note: 3x3 Matrix with rank 2 VS 2x3 Matrix with rank 2**

- 3x3 Matrix with rank 2: "Dimensional constraint"
    - 3×3 Matrix maps 3D space to 3D space (same dimensional space), but rank = 2
    - The full 3D input is squished onto a 2D plane embedded in 3D
    - The output still lives in 3D, but is constrained to a 2D plane (like a sheet of paper floating in a room)
    - So output lives in lower-dimensional subspace of the same ambient space
    - Analogy: Squishing a 3D sculpture into the flat 2D table surface. The flattened result is still in the 3D room, just stuck to a 2D surface within it. We can still describe the position of the flattened sculpture with (x, y, z) coordinates. One of the coordinates will now be constrained (z representing height will be constant along the entire flat surface of the table), but it's still a 3D description
    - For linear transformations specifically, the output must be a subspace, which means it must pass through the origin. So a more helpful analogy would be to think of the 3D sculpture being squished on the floor, with the z-coordinate that represents height becoming 0
    - Each point of the sculpture represents a possible output vector; the entire flattened sculpture shows the 2D subspace of all possible outputs
    - The null space is a line through origin, within the 3D input and 3D output space, and perpendicular to the 2D output plane
        - Row space (2D) = the directions in the input space that will produce non-zero output after the transformation (when 3D sculpture is standing on the floor, row space is the floor)
        - Null space (1D) = "What will collapse to zero" (when 3D sculpture is standing on the floor, null space is a vertical pole through the sculpture)
        - Row space ⊕ null space = entire 3D input
        - Column space (2D) = All possible outputs where things can land" (after we flattened the sculpture on the floor, column space is where the sculpture landed)
        - Left null space (1D) = "Directions never reached - empty space outside of plane" (after we flattened the sculpture on the floor, left null space is the space not touched)
        - Column space ⊕ Left null space = the entire 3D output
    - A 3×3 matrix with rank 2:
        - Input: vector [x, y, z] in 3D
        - Output: constrained to a 2D plane through the origin within 3D space
        - Example: Output can be [x+z, y, 0] - still has 3 components, third is always 0
        - The matrix for this example would be: [1 0 1] [0 1 0] [0 0 0]

- 2x3 Matrix with rank 2: "Dimensional reduction"
    - 2×3 Matrix maps 3D space to 2D space, so output lives in a different, genuinely lower dimensional space
    - The output lives in 2D entirely (an actual flatland, not a plane embedded in 3D). No third dimension exists
    - Even at what is now considered a full rank (rank 2), we are going from 3D down to 2D
    - Analogy: Taking a photo of the 3D sculpture. The sculpture in the photo is now genuinely 2D - no depth information exists anymore. We can only describe positions in the photo with (x, y) coordinates; there's no third coordinate at all. Information is lost, not just constrained. 
    - Null space is a line in the 3D input space, that collapses to zero in the 2D output space
        - Row space: 2D (the 2 independent rows span a 2D plane in 3D input)
        - Null space: 1D (one direction will collapse to zero)
        - Row space ⊕ Null space = 3D input
        - Column space: 2D (full rank means it spans the entire 2D output)
        - Left null space: 0D
        - Column space ⊕ Left null space (0) = 2D output
    - 2x3 matrix with rank 2:
        - Input: vector [x, y, z] in 3D
        - Output: vector [x+z, y] in 2D (just 2 components, living in flat 2D)
        - No third component exists at all: [1 0 1] [0 1 0]
        
---

### Video 9: Dot products and Duality

**Key Concepts:**

- Dot product numerically:
    - If you have two vectors of the same dimension, we can compute their dot product
    - Starting with: [2, 7, 1] · [8, 2, 8]
        - pair up all of the coordinates: [2, 8] [7, 2] [8, 1]
        - multiply the pairs together: (2 * 8) (7 * 2) (1 * 8)
        - add the results: (2 * 8) + (7 * 2) + (1 * 8)
        - complete calculation: ***[2, 7, 1] · [8, 2, 8] = (2 * 8) + (7 * 2) + (1 * 8)***

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
    - The length of projected w is: |w| * cos(θ) so the total calculation is ***|v| * |w| * cos(θ)***

- Order doesn't matter:
    - Initially we would think that the above interpretation is asymmetric and treats the two vectors differently
    - However, the order of multiplying for the dot product does not matter
    - Instead of projecting w onto v, we could project v onto w, multiply the length of projected v by the length of w and get the same result
    - Explanation: 
        - if w and v had the same length, we could leverage some symmetry and say that no matter which vector we chose to project, their dot product would be the same
        - if we scaled one of them by 2, for example w · 2v, that symmetry would break
        - but actually, the ratio of changes would still balance out in the end
        - if we projected w onto 2v, the length of projected w would stay the same, while the length of v would double
        - so their dot product 2v · w would be exactly twice that of v . w and would result in 2 (v · w)
        - if we projected 2v onto w instead, now the length of projected 2v is what gets scaled, while the actual length of w would stay constant, resulting again in 2 (v · w)
        - so the overall effect in both cases is to just double the dot product        

- Numerical and Geometrical relationship:
    - How does the numerical process of matching coordinates, multiplying the pairs and adding them, is related to geometrical projection?
    - The answer comes from the concept of DUALITY

    - Geometric operation:
        - Linear Transformations that go from 2D to 1D, are functions that take in a 2D vector and return a single number
        - but Linear Transformations have some restrictions
        - in the case of 2D to 1D, if you take a diagonal line of evenly spaced dots and apply a transformation, if it's linear the dots will remain evenly spaced in the output line
        - one of these linear transformations is completely determined by where it takes i-hat and j-hat
        - in this case they land on a number each
        - so when we record them in a matrix it will be a 1x2 matrix: [2 1]
    
    - Applying this transformation to a non-basis vector:
        - imagine a linear transformation that takes i-hat to 1 and j-hat to -2
        - to follow an original vector of coordinates [4, 3], we can break it into 4i-hat + 3j-hat, since the basis vectors have a unit of 1
        - due to linearity, after the transformation the vector will be 4 * where i-hat lands, plus 3 * where j-hat lands, so 4 * 1  +  3 * (-2) = 4 + (-6) = -2
        - it lands in -2, just like where j-hat landed! (note: the original vector was longer and diagonal to j-hat)
       
    - Numerical operations:
        - when we do this calculation purely numerically, it's a Matrix-vector multiplication
        - we multiply a 1x2 matrix by a vector [1 -2] * [4, 3] = 4 * 1 + 3 * (-2)
        - this is like taking the dot product of two vectors [1, -2] · [4, 3]
        - so there is a nice association between 1x2 (2D -> 1D) matrices and 2D vectors
        - we can tilt the numerical representation of a vector on its side to get the associated matrix, or tip the matrix back up to get the associated vector
        - which means that there is a connection between:
            - linear transformations that take 2D vectors to 1D numbers (represented by 1x2 matrices) 
            - and vectors THEMSELVES!

- Another way to see the connection:
    - Define a linear transformation from 2D to 1D:
        - let's say we didn't know that a dot product relates to projection
        - place a numberline copy diagonally in space, with 0 at the origin
        - think of the 2D unit vector whose tip sits at 1 on that line, let's call it u-hat
        - if we project 2D vectors straight onto this diagonal line, we just defined a function that takes 2D vectors to numbers (2D to 1D)
        - and this function is actually linear, since it passes our visual test that any line of evenly spaced dots remains evenly spaced once it lands on the numberline
        - remember that the output of the function are numbers, not 2D vectors, as we are in 1D
        - the function takes 2 coordinates and outputs one
        - u-hat is a diagonal 2D vector of the input space that overlaps with the embedding of the number line
    
    - Find the associated Matrix:
        - now let's try to find, WHERE the basis vectors landed 
        - if we find that, we will find the 1x2 matrix that describes this transformation
        - but the only information we have is where u-hat landed (1)
        - we know that i-hat and j-hat are both unit vectors, and the angle between them is the same regardless of which you project onto which
        - the projection of a unit vector onto another unit vector equals the cosine of the angle between them: i-hat · u-hat = cos(θ) = ux (the x-component of u-hat)
        - therefore, projecting i-hat into the line that passes through u-hat, is symmetric to projecting u-hat into the x-axis (so taking the x-coordinate of u-hat: ux)
        - and so they land on the SAME number on their respective projection lines (ux)
        - this reasoning is similar for the j-hat case
        - using symmetry in this way we find that [ux uy] is where i-hat and j-hat landed 
        - therefore, the 1x2 matrix describing the transformation are actually the coordinates of u-hat!
        - more generally, computing this projection-transformation matrix for any arbitrary vector in space, and multiplying the matrix by that vector [ux uy] * [x, y] = ux * x + uy * y, is computationally identical to taking a dot product of the vector and u-hat! [ux, uy] * [x, y] = ux * x + uy * y
        - this is why taking the dot product of a vector and a unit vector, can be interpreted as PROJECTING a vector onto the SPAN of that unit vector and taking the projection length

    - Non-unit vectors:
        - now let's see scaled vectors; say we have a vector 3u-hat
        - following a similar reasoning as before, its coordinates will be [3ux, 3uy]
        - and its associated transformation matrix will be [3ux 3uy]
        - looking at the matrix, it takes i-hat and j-hat to 3 times the values where they landed before
        - due to linearity, this new matrix can be interpreted as projeting any vector onto the numberline copy, and multiplying where it lands by 3
        - this is why the dot product with a non-unit vector can be interpreted as first projecting onto that vector, and then scaling up the length of that projection by the length of the vector
        
    - Process summary:
        - we had a linear transformation from 2D to 1D, NOT defined in terms of numerical vectors or numerical dot products
        - it was just defined by projecting space on to a diagonal copy of the numberline 
        - but because the transformation is linear, it was NECESSARILY described by some 1x2 Matrix
        - since multiplying a 1x2 matrix by a 2D vector is the same as turning that matrix on its side and taking the dot product, this transformation was related to some vector
        - in conclusion, any time we have one of these linear transformations where output space is the number line, no matter how it was defined, there will be some unique vector v corresponding to that transformation, in the sense that applying the transformation is the same thing as taking a dot product with that vector

    - Duality:
        - the dual of a vector is the linear transformation to 1D it encodes
        - the dual of a linear transformation from some space to 1D, is a certain vector in that input space
        - duality works because there are as many independent measurements (linear transformations to 1D) as there are dimensions. This equal count creates a one-to-one pairing: each measurement equals one unique vector
        - the duality between linear transformations and dot products works when the output space is 1D (the number line), regardless of the input dimension
        
- Summary of important concepts:
    - The dot product is a very useful geometrical tool for:
        - understanding projections
        - test whether or not vectors tend to point in the same direction
    - On a deeper level, dotting two vectors together is a way to translate one of them into the world of transformations
    - Vectors are not just arrows in space, but also the physical embodiment or conceptual shorthand of a linear transformation


**Additional notes:**

- When we compute v · w, we are using v as a measuring stick to see how much of w aligns with v's direction.
- Every vector w can be broken into components: w = (component along v) + (component perpendicular to v)
- The dot product v · w extracts only the first part, and filters out everything perpendicular to v
- The duality reveals that every vector defines a way to "measure" other vectors
- When we compute v · w, we are essentially asking: "How much does w contribute in the v-direction?"
- This is why dot products appear everywhere; they're the natural way to decompose vectors into components
        
---

### Video 10: Cross Products

**Key Concepts:**

- If we have two vectors, v and w, they span out a parallelogram:
    - if we take a copy of v and move its tail to the tip of w
    - and we also take a copy of w and move its tail to the tip of v
    - the 4 vectors enclose a certain parallelogram
- The cross product of v and w (v X w) is the area of this parallelogram
- But we also need to consider orientation:
    - if v is on the right of w, then v X w is positive
    - if v is on the left of w, then v X w is negative
    - so order matters: v X w is the reverse of w X v (v X w = - w X v)
    - to help us remember, if we take the cross product of basis vectors in order, the result should be positive, because the order of the basis vectors is actually what defines orientation (i-hat X j-hat = +1; jhat X i-hat = - 1)

- How to compute the cross product (2D):
    - write a matrix with the first column being the coordinates of v vector, and the second column the coordinates of w vector
    - then compute the determinant of this Matrix
    - so cross product calculation: ***v X w = det([v-coordinates w-coordinates])***
    - example: v X w = det([3 2; 1 -1]) where [3,1] is the v vector coordinates and [2,-1] is the w vector coordinates
        - alternatively, we could list the coordinates as rows rather than columns
        - the result would be the same because during the determinant calculation (ad-bc), bc = cb
        - so in our example the calculation would be v X w = det([3 1; 2 -1])
        - determinant = 3 * (-1) - 1 * 2 = -3 -2 = -5 
        - v X w = -5 

- Why the determinant of the 2-vectors Matrix?
    - a matrix is a linear transformation that moves i-hat and j-hat to v and w
    - as we know, the determinant is the change of area after a transformation
    - after the transformation, the unit square with area of 1, turns into a parallelogram
    - so the determinant which measures the factor by which area changes, gives us the area of the parallelogram
    - if v is now on the left of w, this means that orientation has been flipped during the transformation
    - and this is what it means for the determinant to be negative
    - so the cross product is the determinant of the parallelogram formed by 2 vectors
    - note that if vectors are perpendicular to each other, their cross product is larger than if they were pointing in similar directions
    - also, if we scale one of the vectors by an amount, the area of the parallelogram is also scaled by that amount: (3v) X w = 3(v X w)

- The cross product has different interpretations in 2D vs 3D:
    - In 2D: we compute a signed scalar (the area of the parallelogram)
    - In 3D: we compute a vector (perpendicular to both input vectors, with magnitude equal to the parallelogram area)
    - Connection: The 2D scalar result equals the z-component of the 3D cross product, when both vectors lie in the xy 2D plane embedded in 3D space

- The cross product is actually a VECTOR (3D)
    - in 2D we treat the cross product as a scalar, but the true cross product is a 3D operation producing a vector
    - additionally to the calculation above, a true cross product is a vector, not a number: v X w = p
    - this is because the the cross product is something that combines two 3D vectors to get a new 3D vector!
    - how can the area of a shape be a vector?
    - the area of the parallelogram will be the new vector's LENGTH
    - and its DIRECTION will be perpendicular to the parallelogram
    - which way? there are two possible vectors with this length that are perpendicular to a given plane
    - for this we use the right hand rule: point forefinger in the direction of v and middle finger in the direction of w; thumb will show the direction of the cross product v X w

- Example: say v is a vector with length 2 pointing up in the pure positive z direction, and w is a vector with length 2 pointing in the pure positive y direction
    - they form a square because they are perpendicular to each other and have the same length
    - the area of the square is 4
    - so the cross product should be a vector with length 4
    - and to find the orientation, we use the right hand rule:
        - point the forefinger up (in the +z direction) for v
        - point the middle finger in the +y direction for w
        - naturally our thumb will extend towards us, which is the negative x direction
        - the thumb naturally extends in the negative x direction (pointing toward us)
        -so the cross product points purely in the negative x direction
    - therefore, the cross product of these two vectors is -4
    - or we could say that the cross product is -4 * i-hat (because i-hat is the basis vector of the x direction)
    - and since this vector is purely in the x direction, the full coordinates of the v X w vector will be [-4, 0, 0]

- Calculation trick:
    - since we are in 3D, v and w vectors have 3 coordinates each
    - so the cross product can be written as [v1, v2, v3] X [w1, w2, w3]
    - the final vector would be: 
        [v2 * w3 - w2 * v3;
         v3 * w1 - w3 * v1;
         v1 * w2 - w1 * v2]

- But it's easier to remember a certain process involving the 3D determinant:
    - we create a 3D matrix and place the two vectors as the second and third columns
    - and as the first column, we write the basis vectors i-hat, j-hat, k-hat
    - then we compute the determinant of this "matrix"
    - alternatively, we could list the coordinates as rows rather than columns, with the same result
    - so now, we use the regular 3D matrix determinant calculation: a·(ei - fh) - b·(di - fg) + c·(dh - eg) for rows, 
    or a·(ei − fh) − d·(bi − ch) + g·(bf − ce) for columns
    - but instead of a, b and c, we now use i-hat, j-hat and k-hat
    - ***i-hat(v2w3 - v3w2) + j-hat(v3w1 - v1w3) + k-hat(v1w2 - v2w1)***
    - note that the j-hat changed from -j-hat(v1w3 - v3w1) to + j-hat(v3w1 - v1w3), so the negative sign is already incorporated in the computation
    - this finds the unique vector perpendicular to v and w, whose magnitude is the area of their parallelogram, and whose direction obeys the right hand rule
    - so generally, to find the vector p = v X w:
        - v × w = det([i-hat, j-hat, k-hat; v1, v2, v3; w1, w2, w3]) (row form)
        - v × w = det([i-hat, v1, w1; j-hat, v2, w2; k-hat, v3, w3]) (column form)
        
---

### Video 11: Cross Products in the light of Linear Transformations

**Key Concepts:**

- In the formula i-hat(v2w3 - v3w2) + j-hat(v3w1 - v1w3) + k-hat(v1w2 - v2w1), we have three different numbers that are interpreted as the coordinates of some resulting vector p
- This vector p has a length equal to the parallelogram area defined by v and w, is perpendicular to both v and w, and obeys the right hand rule

- Duality:
    - every time we have a transformation from some space into the 1D numberline, it's associated with a unique vector in that space, in the sense that performing the linear transformation is the same as taking a dot product with that vector
    - numerically, this is because one of those transformations is described by a matrix with just one row, where each column tells you the number that each basis vector lands on
    - and multiplying this matrix by some vector v is computationally identical to taking the dot product between v and the vector you get by turning that matrix on its side

- Steps to find this duality:
    - define a 3D to 1D linear transformation in terms of v and w
    - associate that transformation with its dual vector in 3D space
    - that dual vector will be the cross product of v and w

- Computing cross product in 2D:
    - when we have two vectors v and w, we put the coordinates of v as the first column of a 2x2 matrix and the coordinates of w as the second. Then we just compute the determinant
    - geometrically this gives us the area of a parallelogram spaned out by those two vectors (with the possibility of being negative depending on the orientation of the vectors)

- Computing cross product in 3D:
    - the 2D calculation could lead us into thinking that for 3D we can just take three vectors and make their coordinates the columns of a 3x3 matrix, compute the determinant and get the signed volume of the parallilepiped spanned out by those three vectors
    - but this is not the real cross product, because the actual 3D cross product takes in two vectors and spits out a third vector (so the same amount of vectors as in the 2D case)
    - if we do want to think about "taking three vectors" we could consider the first vector to be a variable (with variable entries x, y, z), while columns for v and w remain fixed
    - so we are defining this function: f([x, y, z]) = det([x, y, z] | v | w)
    - so now we have a function whose span is revolving around v and w (depending on the choice of variables), and includes mapping output from 3D to 1D
    - we input some vector that represents the variables [x, y, z] and get a scalar number, by taking the determinant of a matrix whose other two columns are the coordinates of the constant vectors v and w
    - geometrically for any input vector [x, y, z], we consider the parallilepiped defined by this vector, v and w; then we return its volume and sign for orientation
    - this function is linear so the idea of duality is valid; since it's linear, there is a way to describe this function as a matrix multiplication
    - and since we are going from 3D to 1D, that transformation will be a 1x3 matrix
    - the special property about transformations to 1D is that we can turn that Matrix on its side to produce a vector and interpret the transformation as the dot product with that vector

- What we are looking for:
    - we are looking for a 3D vector p such that taking the dot product between p and any other vector [x, y, z] gives the same result as plugging in x, y, z as the first column of a 3x3 matrix, whose other two columns have the coordinates of v and w, and then computing the determinant

- Computationally:
    - taking the dot product between p and [x, y, z] will give us something * x + something * y + something * z, where those "somethings" are the coordinates of p
    - alternatively, when we compute the determinant of the 3x3 matrix, we can organize it to look like: some constant * x + some constant * y + some constant * z, where those constants involve certain combinations of the components v and w
    - so those constants will be the coordinates of the vector we are looking for
    - this is the same as plugging i-hat, j-hat, k-hat to that first column (as a way of signaling that we should interpret those coefficients as the coordinates of a vector)

- Computational Question:
    - which vector p has the special property that when you take a dot product between p and some other vector [x, y, z] it gives the same result as plugging in [x, y, z] to the first column of a matrix whose other two columns have the coordinates of v and w and then computing the determinant?
    
- Geometric Question:
    - which vector p has the special property that when you take a dot product between p and some other vector [x, y, z] it gives the same result as if you took the signed volume of a parallilepiped defined by this vector [x, y, z] along with v and w?

- Dot product reminder:
    - remember that taking the dot product between p and some other vector is to project that other vector onto p, and then to multiply the length of that projection by the length of p
    - if we take the area of the parallelogram defined by v and w, and multiply it, NOT by the length of [x, y, z] but by the "shadow" component of [x, y, z] that's perpendicular to the parallelogram (perpendicular to both v and w), and multiply that projection by the area of the parallelogram spanned by v and w
    - the "shadow" component of [x, y, z] perpendicular to both v and w, is actually the height of [x, y, z] above that plane
    - so this product equals the volume of the parallilepiped
    - this is the same as taking a dot product between [x, y, z] and a vector perpendicular to v and w, and with a length equal to the area of that parallelogram
    - plus if you choose the appropriate direction for that vector, the cases where the dot product is negative will match the cases where the right hand rule for orientation of [x, y, z] is negative
    - so our computational answer corresponds geometrically to this vector

- Why perpendicular?
    - the cross product is a perpendicular "measuring stick" whose length equals the base area, so that dotting it with any vector [x, y, z] automatically computes the volume
    - say we want to find the volume of a parallelepiped formed by three vectors: [x, y, z], v, and w
    - volume = base * height
    - base area = the parallelogram formed by v and w (lying flat like a table)
    - height = how far [x, y, z] sticks up above that table
    - so volume = area of v-w parallelogram * height of [x, y, z]
    - the dot product gives us  p · [x, y, z] = |p| * height
    - for this to equal the volume: |p| * height = base area * height
    - therefore |p| must equal the base area! (|p| is the magnitude of p, not the vector itself)
    - the cross product p = v × w is that measuring stick:
        - perpendicular to the v-w plane (points "straight up")
        - length = area of the v-w parallelogram
        - oriented by the right-hand rule
    - if p wasn't perpendicular, the dot product p · [x, y, z] would give us the projection in the wrong direction - not the true height, but some slanted measurement. Only when p is perpendicular do we measure the actual height
    - both properties (perpendicular + correct length) are forced by the requirement that p · [x, y, z] = det([x, y, z]|v|w) for ALL vectors [x, y, z]

---

### Video 12: Cramer's rule, explained geometrically

**Key Concepts:**

- Let's see the geometry behind a certain method for computing solutions to systems of linear equations known as the Cramer's rule
- It's not the best way to compute solutions to systems of linear equations - Gaussian Elimination is faster
- But it's a good way to understand the theory behind those systems and consolidate linear algebra concepts

- The problem:
    - say we have a linear system of two equations with two unknowns:
        -  3x + 2y = -4
        - -1x + 2y = - 2
    - as we know, we can think of this system geometrically as a known matrix transforming un unknown vector [x, y], into a known output
        - [3 2; -1 2] * [x, y] = [-4, -2]
    - remember that each of the columns of the matrix is telling us where the basis vectors of the input space have landed
    - so now we need to find which input vector will land on the output [-4, -2]

- Where to start from:
    - we know that the given output vector [-4, -2] is a linear combination of the columns of the matrix: (x * where i-hat lands) + (y * where j-hat lands)
    - so we want to figure out this linear combination: x * [3, -1] + y * [2, 2] = [-4, -2]
    - in the case the transformation has a 0 determinant, either none of the inputs land on a given output, or several imputs land on that output
    - on this chapter we will limit our view in the case of a non-0 determinant, meaning the outputs of this transformation will still span the full in-dimensional space that it started in; every input lands on one and only one output, and every output has one and only one input

- Wrong but helpful idea:
    - the x-coordinate of the input vector we are looking for [x, y], is what we get by taking the dot product of [x, y] with the FIRST basis vector i-hat (1,0)
    - the y-coordinate of the input vector we are looking for [x, y], is what we get by taking the dot product of [x, y] with the SECOND basis vector j-hat (0,1)
    - so [x, y] · [1, 0] = x; [x, y] · [0, 1] = y
    - it is wrong to think that after the transformation, the dot products of the TRANSFORMED version of the vector [x, y] and the TRANSFORMED version of the basis vectors, would also be the coordinates of x and y
    - for most linear transformations, the dot product before and after the transformation is NOT the same:
        - for example, two vectors pointing in the same direction with a positive dot product, could get pulled apart from each other during the transformation and end up having a negative dot product
        - or if they started perpendicular to each other with a dot product of 0 (like basis vectors), they may not stay perpendicular or preserve their dot product after the transformation
        - usually, since most vectors are getting stretched out, dot products tend to get bigger
    - exception: transformations that do preserve dot products are called orthonormal transformations
        - they leave the basis vectors perpendicular to each other, and still with unit lengths
        - these are rotation matrices that correspond to rigid motion without stretching, squishing or morphing
        - solving a linear system with an orthonormal matrix is easy: because dot products are preserved
        -  taking the dot product between the known output vector and all the columns of the matrix (where the basis vectors land), will be the same as taking the dot product between the unknown input vector [x, y] and the basis vectors, finding the coordinates of the input vector
        - first column (where i-hat landed) · output vector = x
        - second column (where j-hat landed) · output vector = y

- Expand on the right idea (2D):
    - we need a coordinate-extraction method that survives transformation
    - take the parallelogram defined by i-hat and the mystery input vector [x, y]
    - the area of this parallelogram is the base(1) * the height perpendicular to that base
    - which is the y-coordinate of that input vector
    - because the base = 1, the signed area IS the y-coordinate of that input vector
    - and symmetrically, if we now take the parallelogram defined by j-hat and the mystery input vector [x, y]
    - its area will be the x-coordinate of that mystery input vector

- In 3D:
    - normally when we want to think about one of the coordinates of a vector (ie the z-coordinate), we take its dot product with the corresponding basis vector (k-hat), so z = [x, y, z] · [0, 0, 1]
    - but an alternative geometric interpretation would be to consider the parallilepiped that the vector creates with the other two basis vectors (i-hat and j-hat)
    - since volume = base * height
    - if the square spanned by i-hat and j-hat as the base has area 1, then the volume of the parallilepiped equals just its height, which is the third coordinate of our vector
    - similarly, to find the other coordinates of the vector, we would form other parallilepipeds using the vector and any basis vectors other than the one correspoding to the direction we are looking for
    - signed volume: the order of listing the three vectors matters; that way, negative coordinates still make sense
    - z = det([1 0 x; 0 1 y; 0 0 z]); so the z-coordinate equal the determinant of a matrix with vectors i-hat [1, 0, 0], j-hat [0, 1, 0] and [x, y, z]

- How to continue (2D):
    - using the example [2 -1; 0 1] * [x, y] = [4, 2]
    - as we apply matrix transformations (for example [2 -1; 0 1]), the areas of these parallelograms may get scaled up or down, BUT all the areas get scaled by the same factor (the determinant of the transformation matrix)
        - earlier we took a parallelogram with base 1 (i-hat) * height (y-coordinate of input vector) and found that the are EQUALS the y-coordinate
        - assuming that all areas get scaled by the same factor (the determinant)
        - this means that after the transformation, the new area will be the y-coordinate * the determinant of the transformation
        - so ***signed area = det(A) * y***
        - we can solve for y by dividing the area of the parallelogram in the output space, by the determinant of the full transformation
        - ***y = area / det(A)***
    - how to get the output area:
        - we know the coordinates of where the vector lands
        - we can create a new matrix whose first column is the same as our original matrix (where i-hat landed), but whose second column is the output vector, and take its determinant
        - y = area / det(A) = det([2 4; 0 2]) / det([2 -1; 0 1]) = 2 * 2 - 4 * 0 / 2 * 1 - (-1) * 0 = 4 / 2 = 2
        - so y-coordinate is 2
        - reminder that [4, 2] is where vector has landed
    - so just using data from the output of our transformation (the columns of the matrix / where the basis vectors landed, and the coordinates of the output vector), we can recover the y-coordinate of the mystery input vector
    
    - likewise, we can then get the x-coordinate in the same way:
        - look at the parallelogram which encodes the x-coordinate of the mystery input vector (spanned by the vector and j-hat)
        - base 1 (j-hat) * height (x-coordinate of input vector)
        - the transformed version of it, is spanned by the output vector and the second column of the matrix, and its area will have been multiplied(scaled) by the determinant of that matrix 
        - to solve for x, we can take the new area divided by the determinant of the full transformation x = area / det(A)
        - and compute the area of that output parallelogram by creating a new matrix whose first column is the output vector, and second column is the same as the original matrix 
        - x = area / det(A) = det([4 -1; 2 1]) / det([2 -1; 0 1]) = 4 * 1 - (-1) * 2 / 2 * 1 - (-1) * 0 = 6 / 2 = 3
        - where det([4 -1; 2 1]) is det([output | where j-hat landed])
        - so the x-coordinate is 3

- Summary:
    - just using data from the output space (the numbers we see in our original linear system) we can solve for x
    - this formula for finding the solution to a linear system of equations is known as Cramer's rule
    - general formula: for ax = b:
        - xi = det(Ai)/det(A), where Ai is A with column i replaced by b
    - original parallelogram: spanned by [basis vector] and [mystery input]
    - after transformation: spanned by [transformed basis vector = column of A] and [output vector b]
    - we replace the i-th column with b because we want the parallelogram that would have the i-th coordinate as its area
    -  the transformation scales ALL areas by det(A), so to "undo" this scaling and recover the original coordinate (which was equal to the original area), we must divide the transformed area by det(A)

---

### Video 13: Change of basis

**Key Concepts:**

- In Linear Algebra we think of each coordinate number as a scalar (which scales i-hat and j-hat)
- The tip-to-tail sum of these vectors is what the coordinates are meant to describe
- These basis vectors are encapsulationg all the implicit assumptions of our coordinate system, like that the first number indicates rightward motion, the second indicates upward motion, or how far a unit of distance is
- Any way to translate between vectors and sets of numbers is called a coordinate system; i-hat & j-hat are the basis vectors of our standard coordinate system
- But we could be using a different set of basis vectors, for example:
    - b1 for a vector pointing up and to the right
    - b2 for a vector pointing up and to the left
- In this system, we could describe our standard [3, 2] as [(5/3) / (1/3)], because we need to scale b1 by 5/3 and b2 by 1/3 and add them, to get to this vector
- So the first coordinate scales b1, the second scales b2 and we add the results
- In our coordinate system, we would describe b1 as [2, 1] and b2 as [-1, 1]
- But from the perspective of the alternative system, the coordinates are [1, 0] and [0, 1] respectively
- And they are the basis vectors, so what defines the meaning of the coordinates [1, 0] and [0, 1] 
- It's like speaking different languages to describe the same vectors
- [0, 0] is common between different coordinate systems; it's what we get when we scale any vector by 0
- But the direction of the axis and the spacing of the grid line may be different, depending on our choice of basis vectors

- How to translate between coordinate systems:
    - in the coordinate system with b1 and b2, how would a vector [-1, 2] translate into our standard coordinate system?
    - the vector is (-1 * b1) + (2 * b2)
    - if from our perspective, b1 has coordinates of [2, 1] and b2 is [-1, 1]
    - we can compute -1 * [2, 1] + 2 * [-1 1] = [-4 1]
    - which means that [-1, 2] in that system is [-4 1] in our system
    - so we are performing Matrix-vector multiplication (scaling the basis vectors with the corresponding coordinates of some vector, then adding them together)
    - the Matrix columns represent the basis vectors of some coordinate system but in our perspecive
    - that Matrix can be thought of as a transformation that moves our basis vectors to the basis vectors of the other system (ie what is [1, 0], [0, 1] in the standard coordinate system, to what is [1, 0], [0, 1] in the new coordinate system)
    - before the transformation we are thinking of vector [-1, 2] as a linear transformation of our basis vectors (-1 * i-hat + 2 * j-hat)
    - and the key feature of a linear transformation is that the resulting vector will be that same linear combination, but of the new basis vectors: -1 * where i-hat lands (b1) + 2 * where j-hat lands (b2)
    - [in progress - 634]