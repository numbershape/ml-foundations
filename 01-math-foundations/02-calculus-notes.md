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
    - So its area 1/2bh is 1/2(3)(2π·3) = π3²
    - More generally, if the radius of the original circle is some value R, the area is πR²; which is the formula for the area of a circle!
    - So our problem could be approximated with the sum of many small numbers, each of which looked like 2πr dr, for values of r ranging between 0 and 3, with the small number dr representing our choice for the thrickness of each ring
    - Not only is dr a factor in the quantities we are adding up 2πr dr, it also gives the spacing between the different values of r: The smaller our choice for dr, the better the approximation
    - Adding all of those numbers could be seen as adding the areas of many thin rectangles sitting underneath a graph, the graph of the function 2πr in this case
    - Then by considering smaller and smaller choices for dr, the sum, thought of as the aggregate area of those rectangles, approaches the area under the graph
    - And because of that we can conclude that the answer to our original question is exactly the same as the area underneath this graph
    - A lot of other problems can be approximated as the sum of many small quantities, like figuring out how far a car has traveled based on its velocity at each point in time v(t)dt: range between different points in time and at each one multiply the velocity at that time v(t) * a tiny change in time dt, which would give the corresponding distance traveled during that little time

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
    