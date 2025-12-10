# Calculus

## Resources
- 3Blue1Brown: "Essence of Calculus" series
- Claude Sonnet 4.5 & Opus 4.5: Supporting tools for investigation, additional notes and final summary

## Notation

**Symbols and Formatting:**
- [XXX]

---

## Notes

### Video 1: The Essence of Calculus

**Key Concepts:**

- Think about the area of a circle: area = πR². Where does this formula come from?
    - Trying to find its area, we can think of the idea of slicing the circle into many concentric rings - this respects the symmetry of the circle
    - Say the radius of the full circle is 3, and that one of those rings has some inner radius r that is between 0 and 3
    - If we can get the area of each ring like this one, and add them all up, we can get the full circle's area
    - We can imagine straightening out this inner ring, and approximate it as a rectagle
    - Its width is the circumference of the original inner ring 2πr
    - Its thickness depends on how finely we chopped up the circle, so let's call it a variable dr for a tiny diffrence in the radius from one ring to the next; say dr = 0.1
    - Approximating this unwrapped ring as a thin rectangle, its area is 2πr (circumference) * dr (difference in radius/thickness), or 2πrdr
    - For smaller and smaller choices of dr (thinner and thinner rings), this formula will give a better approximation for that area, since the top and bottom sides of this shape will get closer to being exactly the same length
    - So we have broken up the area of the circle into several rings, and we approximate their area as 2πrdr, where the specific value for the inner radius r ranges from 0 for the smallest ring up to just under 3 for the biggest ring, spaced out by the thickness is that we choose for dr
    - The spacing between the values corresponds to the thickness dr of each ring, the difference of radius from one ring to the next
    - If we fit all the rectangles upright side by side along an axis (r for x and 2πr for y), each straightened ring has a thickness dr, and the height of any one of them sitting above some specific value of r (say 0.6), is exactly 2π times that value (2πr = 2π * 0.6)
    - That's the circumference of the corresponding ring that the rectangle approximates
    - We can see that the graph of 2πr is a straight line with slope 2π, with all the straightened ring rectangles fitting in the area under it
    - For smaller and smaller choices of dr, it may initially look like we are getting too many values to sum up; however they eventually cover the entire area under the graph, and the portion under the graph is now just a triagle (triangle area = 1/2bh) with a base of 3 and a height 2π3
    - So its area 1/2bh is 1/2(3)(2π·3) = π(3²)
    - More generally, if the radius of the original circle is some value R, the area is πR²; which is the formula for the area of a circle!
    - So our problem could be approximated with the sum of many small numbers, each of which looked like 2πr dr, for values of r ranging between 0 and 3, with the small number dr representing our choice for the thickness of each ring
    - Not only is dr a factor in the quantities we are adding up 2πr dr, it also gives the spacing between the different values of r: The smaller our choice for dr, the better the approximation
    - Adding all of those numbers could be seen as adding the areas of many thin rectangles sitting underneath a graph, the graph of the function 2πr in this case
    - Then by considering smaller and smaller choices for dr, the sum, thought of as the aggregate area of those rectangles, approaches the area under the graph
    - And because of that we can conclude that the answer to our original question is exactly the same as the area underneath this graph
    - Many problems can be approximated as the sum of many small quantities, like figuring out how far a car has traveled based on its velocity at each point in time v(t)dt: range between different points in time and at each one multiply the velocity at that time v(t) * a tiny change in time dt, which would give the corresponding distance traveled during that little time

- What about the area of a parabola?
    - To find the area under the parabola x² curve, we need a function A(x) that lets us find the area under this parabola between 0 and a variable x. This function is called an "integral" of x²
    - When we slightly increase x by a small amount dx, there is a resulting difference in Area (area added under the graph) represented by dA
    - This dA can be approximated by a rectangle whose height is x² and width is dx: dA ≈ x²dx
    - The smaller the width dx, the more it looks like a rectangle and the better the approximation
    - A change to the output of dA is about equal to x² (where x is the imput we start at) * dx (the nudge to the input that caused A to change)
    - If we rearrange dA ≈ x²dx to dA/dx ≈ x², we can see that the ratio of a change in area A to the change in x that caused it, is approximately whatever x² is at that point, with the approximation getting better for smaller choices of dx
    - Example for dA/dx ≈ x²:
        - Say the change in x is from 3 to 3.001
        - A(3.001) - A(3) is the change in area dA
        - 0.001 is the change in x
        - [A(3.001) - A(3)] / 0.001 ≈ 3² (dA/dx ≈ x²)
    - Any function defined as the area under some graph has this property

- The ratio dA/dx is called the "derivative" of A
    - The derivative is whatever this ratio approaches as dx gets smaller and smaller
    - Its a measure of how sensitive a function is to small changes in its input
    - There are many ways to visualize a derivative
    - Derivatives are the key to solving integral questions: problems that require finding the area under a curve
    - Once we get the derivative, we can reverse-engineer the integral
    - The derivative of a function for the area under a graph gives us the function defining the graph itself. This is called the Fundamental Theorem of Calculus, which shows that derivatives and integrals are inverses of each other

---

### Video 2: The Paradox of the Derivative

**Key Concepts:**

- What is a derivative?
    - "Instantaneous rate of change" is not exactly correct, as change by definition requires multiple points in time
    - Say a car starts at some point A, speeds up, slows down, and arrives at some point B 100 meters away, over the course of 10 seconds
    - We can graph this motion, letting the horizontal axis represent time (in seconds), and the vertical axis represent the distance traveled (in meters)
    - At each time t (represented with a point along the horizontal axis), the height of the graph will tell us how far the car has traveled in total after that amount of time
    - A distance function like this is commonly named s(t) (instead of d(t), because d is used for 'change' in calculus, not 'distance')

- The Distance/Time s(t) graph has a positive slope but is not entirely linear:
    - Initially the curve is shallow, since the car is slow to start
    - As the car speeds up, the distance traveled in a given second gets larger, corresponding to a steeper slope in the graph
    - Towards the end when it slows down, the curve shallows out again

- The Velocity/Time v(t) graph for the car's velocity in meters/second as a function of time v(t), would look like a normal distribution bump:
    - Initially the velocity is very small
    - Up to the middle of the journey, the car builds up to some maximum velocity, covering a relatively large distance each second
    - Then it slows back down towards a speed of zero

- These two graphs / curves are related to each other. We want to understand the specifics of that relationship
    - Firstly, what does velocity mean?
        - Change in distance/change in time
        - What the car's speedometer shows in any given moment
        - Higher when the car traverses more distance per unit time
    - But velocity at a single moment makes no sense; we need two separate points in time to compute the change in distance/change in time
    - So what about the velocity function which takes a single value of t, a single snapshot in time?
        - At some point, for example 3 seconds into the journey, the speedometer might measure how far the car goes in a very small amount of time, like the distance traveled between 3 seconds and 3.01 seconds
        - Then it computes the speed in meters/second as that tiny distance traversed in meters divided by a tiny amount of time
        - For example (20.21 - 20) meters / (3.01 - 3) seconds
        - So the rate of change is not instantaneous, but over a small time
    - Let's call that difference in time dt (dt = 0.01 seconds)
    - And let's call the resulting difference in distance ds (ds = 0.21 meters)
    - So the velocity at some point in time is ds/dt
    - Graphically, we can imagine zooming in on some point of this distance vs time graph, above t = 3:
        - The dt is a small step to the right, since time is on the horizontal axis, and the ds is the resulting change in the height of the graph, since the vertical axis represents distance traveled
        - So ds/dt = rise/run slope between two very close points on this graph
        - This expression ds/dt is a function of t. We can give it a time t and it returns the value of this ratio at that time, the velocity as a function of time ds/dt(t)
    - If we define a tiny change in time dt = 0.01:
        - The distance traveled is s(t + dt) - s(t)
        - So the velocity is ds/dt(t) = [s(t + dt) - s(t)] / dt
        - So by having any curve representing the distance function s(t), we can figure out the curve representing velocity

- The idea of ds/dt is almost what a derivative is, but the true derivative is not based on a specific value of dt
- Instead, it's whatever that ratio approaches as our choice for dt approaches zero
- Derivative: ***ds/dt = [s(t + dt) - s(t)] / dt, dt -> 0***
    - Remember that for any specific choice of dt, the ratio ds/dt is the rise/run, or slope of a line passing through two separate points on the graph
    - As dt approaches 0, and as those two points approach each other, the slope of the line approaches the slope of a line tangent to the graph at whatever point t we are looking at
    - So the true derivative is not the rise/run slope between two nearby points on the graph; it's equal to the slope of a line tangent to the graph at a single point
    - The idea of "approaching 0" allows the rate of change at a single point in time
    - It's the best constant approximation for a rate of change around a point 
    - Using "d" in calculus implies that dt -> 0 

- How the derivative gets simplified:
    - Say we have a distance/time function s(t) = t³:
        - After 1 second, the car has traveled 1³ = 1 meters
        - After 2 seconds, it has traveled 2³ = 8 meters, and so on
    - We want to compute the velocity ds/dt at some specific time like t = 2
    - ds/dt(t=2) = [s(2 + dt) - s(2)] / dt
    - ds/dt(t=2) = [(2 + dt)³ - (2)³] / dt
    - By algebraic expansion, it becomes:
        - [2³ + 3(2)²dt + 3(2)(dt)² + (dt)³ - 2³] / dt
        - the cubed terms 2³ and - 2³ cancel out
        - the dt in the denominator cancels out one dt power from each term of the numerator 
        - leaving the expression 3(2)² + 3(2)(dt) + (dt)²
        - now if we assume that dt approaches 0, the terms containing dt become insignificantly small, and we can completely ignore them!
        - so we are left with just 3(2)²
    - This means that the slope of a line tangent to the point at t = 2 of this graph, is exactly 3(2)² = 12
    - Generally, the derivative of t³ as a function of t, is 3(t)²:
        - d(t³) / dt = 3(t)²

- Back to "instantaneous rate of change":
    - At time t = 0, is the car moving?
    - 0 m/s around that point is the best constant approximation


    

    