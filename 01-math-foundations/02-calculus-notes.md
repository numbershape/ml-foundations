# Calculus

## Resources
- 3Blue1Brown: "Essence of Calculus" series
- Claude Sonnet 4.5 & Opus 4.5: Supporting tools for investigation, additional notes and final summary

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
    - The derivative of a function for the area under a graph gives us the function defining the graph itself. This is called the Fundamental Theorem of Calculus, which shows that derivatives and integrals are inverses of each other.

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

---

### Video 3: Derivative Formulas Through Geometry

**Key Concepts:**

- Let's learn to compute derivatives and rates of change
- If we get a function with an explicit formula, we want to be able to find its derivative formula
- "Given f(x) = sin(x)x², compute df/dx(x)"
- A lot of real world phenomena like oscilations, or population growth, are modeled using:      
    - polynomials f(x) = 2x² - x³
    - trigonometric functions f(x) = sin(x)
    - exponentials f(x) = eˣ
    - other pure functions

- The derivative of f(x) = x² geometrically
- If we take a value x, like x = 2, and compare it to a value just slightly bigger (dx bigger) what is the corresponding change in the value of the function (df)?
- And what is df/dx, the rate at which this function is changing per unit change in x?
    - We can think of df/dx as the slope of a tangent line to the graph x²
    - We can see that the slope generally increases as x increases (at 0, the tangent line is flat and the slope is zero; at x = 1 it is steeper, at x = 2 it is even steeper)
    - Let's picture a square with side x and area x²
    - If we increase x by a little dx, the resulting change in the area of that square is what df means
    - There are 3 new pieces of area added: two thin rectangles and a small square between them
    - The two thin rectangles each have side lengths of x and dx, so their area is x dx, and both of them are 2x dx
        - For example if x = 3 and dx = 0.01, the two rectangles would be 2 * 3 * 0.01 = 0.06, about 6 times the size of dx
    - And the small square has area of dx²
        - For example if dx = 0.01, then dx² = 0.0001
            - Note: area and length have different units
                - side length = 1 cm = 0.01 m
                - area = 1 cm² = 0.0001 m²
        - In derivatives, dx represents an infinitesimally small length, so dx² represents an even more infinitesimally small area. The fact that 0.0001 < 0.01 reflects that small areas shrink faster than small lengths as things approach zero 
        - So it's safe to ignore anything that includes a dx raised to a power greater than 1
    - We are left with df = 2x dx (df is just some multiple of dx)
    - Rearranging, df / dx = 2x, so 2x is the derivative of x²
    - More examples for x²: 
        - if we started at x = 3, the rate of change in area per unit change in length added, or change in area/change in x, or d(x²)/dx, would be 2 * 3 = 6
        - if we started at x = 5, then the rate of change would be 10 units of area per unit change in x 

- Let's try f(x) = x³ geometrically:
    - We can think of x³ as the volume of an actual cube whose side lengths are x
    - When we increase x by a tiny dx, the resulting added volume is comprised of several pieces from three sides
        - Three of the components are the three large squares
        - As dx approaches 0, those three squares comprise a portion closer and closer to 100% of the new volume
        - Each of those three squares has a volume of x²dx (the area of the side times that little thickness dx)
        - So in total we get 3x²dx of volume change
        - The rest of the components can be ignored because they are multiples of dx
        - This is ultimately because they will be divided by dx, and if there is still any dx remaining, then those terms will not survive the process of letting dx approach 0
        - So the derivative of x³, the rate at which x³ changes per unit change of x, is 3x²
        - Graphically, this means that the slope of the graph of x³ at every single point x is exactly 3x²

- So there is a pattern for polynomial terms:
    - The "power rule": ***d(xⁿ)/dx = nxⁿ⁻¹***
    - For example d(x⁵)/dx = 5x⁵⁻¹ = 5x⁴
    - Why does this work?
        - For xⁿ, when we increase x to x + dx, working out the exact value of the output would involve multiplying x + dx together n times
        - While expanding, the first term would be xⁿ (analogous to the area of the original square or the volume of the original cube)
        - For the next terms of the expansion we have mostly x's with a single dx:
            - dx x x ... x
            - x dx x ... x
            - x x dx ... x
            - x x x ... dx
        - Since there are n different parentheticals, we have n separate terms that include n-1 x's * dx, giving a value of xⁿ⁻¹dx
        - This is analogous to how the majority of the new area in the square came from the two bars, each with area x dx; or how the bulk of the new volume of the cube came from the three thin squares, each with area x²dx
        - There are more terms on this expansion but all of them are multiples of dx², so we can ignore them
        - All but a negligible portion of the increase in the output comes from n copies of nxⁿ⁻¹dx

- Consider the function f(x) = 1/x:
    - We know that 1/x can be rewritten as x⁻¹
    - So we could apply the power rule and add -1 in the front while subtracting one from the top: -1x⁻²
    - Let's reason about it geometrically:
        - 1/x means "what number * x equals 1?"
        - Imagine a 2D square with area 1
        - Let's say that the width is x, so the height is 1/x, since the total area is 1
        - So if x = 2, then the height is 1/2
        - And if x = 3, then the height is 1/3
        - If we increase width by dx, how much should we decrease height so that the area remains 1?
        - This creates the graph of 1/x for every possible value
        - d(1/x) is a negative amount because it is decreasing the height of the rectangle

- Let's try the function f(θ) = sin(θ):
    - Reminder: The unit circle has radius 1 and is centered at the origin
    - An angle θ = 0.8 represents a distance of 0.8 arc length from the rightmost point (0.8 is 80% of the length from the origin to 1 on the x-axis, but traversed in an arc counterclockwise)
    - This is the same thing as saying that the angle is exactly θ radians, since the circle has a radius of 1 (the angle θ being defined by the length of the arc opposite it)
    - Then sin(θ) is the height of the point above the x-axis that reaches the top of the arc
    - As our θ value increases and we move around the circle, that height goes up and down between -1 and 1
    - So when we graph f(θ) = sin(θ) we get a wave pattern, the "quintessential wave pattern"
    - d(sin(θ)) / d(θ) = slope of this graph
    - Let's find its derivative:
        - The slope at 0 is positive, since sin(θ) starts from 0 and is starting to increase
        - As we move to the right and sin(θ) increases and approaches its positive peak, the slope decreases until reaching zero at the peak
        - Then the slope turns negative for a little as sin(θ) is decreasing
        - As sin(θ) approaches the negative peak, the slope becomes less negative until it reaches 0 at the negative peak
        - The slope graph is the cos(θ) graph, meaning that the derivative of sin(θ) is cos(θ)

    - A more precise line of reasoning looking at the unit circle itself:
        - Having traversed an arc with length θ and thinking about sin(θ) as the height of that point
        - If we zoom into that point on the circle (reached by the height) and consider a slight addition of dθ along the circumference, like a tiny step in the walk around the unit circle
        - How much does that tiny step change the sin(θ)? Meaning, how much does this increase of arc length, increase the height above the x-axis?
        - If we zoom in on dθ on the circle enough, it looks like a straight line, so we can think of a little right triangle of which the hypotenuse represents dθ along the circumference, and the vertical left side represents the change in height d(sin(θ))
        - This tiny triangle is similar to the large triangle with the defining angle θ, whose hypotenuse is the radius of the circle with length 1, just turned once to the left
        - So the little angle on the small triangle that sits where the new height reaches, is equal to θ radians
        - The derivative of sin(θ) is the ratio between the tiny change to the height d(sin(θ)) divided by the tiny change to the input of the function dθ
        - And that is the ratio between adjacent to angle θ / hypotenuse, and adj / hyp = cos(θ)!

---

### Video 4: Visualizing the chain rule and product rule

**Key Concepts:**

- How to take derivatives of combined functions
- Functions can be added, multiplied, or composed (one inside the other)
- If you know the derivative of two functions, what is the derivative of their sum, their product, and the function composition between them?

- The sum rule: 
    - The derivative of the sum of two functions is the sum of their derivatives: ***d/dx (g(x) + h(x)) = dg/dx + dh/dx***
    - Example d/dx (sin(x) + x²) = cos(x) + 2x
    - Let's think about the function f(x) = sin(x) + x²
    - On the graph, we add together the values of sin(x) + x² at each input
    - For example, at x = 0.5, their sum is the length we get by stacking 
    sin(0.5) + (0.5)² together
    - To find the derivative, we have to think what happens if we nudge the input slightly, increasing it to 0.5 + dx:
        - sin (0.5 + dx) + (0.5 + dx)²
        - The difference between "before" and "after" is the df
        - df = d(sin(x)) + d(x²)
        - We know that the derivative of sin(x) is cos(x)
        - This means that the little change d(sin(x)) = cos(0.5)dx
        - Likewise, because the derivative of x² is 2x, the change in the height of the x squared graph is 2x times whatever dx was: 2(0.5)dx
        - Rearranging: df/dx = cos(x) + 2x (the sum of the derivatives of its parts)
            - d/dx (sin(x)) + (x²) = cos(x) + 2x
            - d/dx (g(x) + h(x)) = dg/dx + dh/dx

- The product rule:
    - Think of a box with sides sin(x) and x²
    - Focusing on the sin(x) side, we can see it increase as x increases until reaching 1, then decreasing as x still increases (due to the wavelike nature of the sin(x) graph)
    - In the same way, the height is always changing as x²
    - So f(x), defined as the product of these two functions, is the area of this box: f(x) = sin(x)x² = area
    - For the derivative, let's think about how a tiny change dx in x, influences that area: what is the resulting change in area (df)?
    - The dx nudge caused the width to change by some small d(sin(x)), and the height to change by some small d(x²)
    - This gives us three little snippets of new area:
        - A thin rectangle on the bottom whose area is its width sin(x) * its thin height d(x²)
        - A thin rectangle on the right whose area is its height x² * its thin width d(sin(x))
        - And a little d(x²) * d(sin(x)) piece we can ignore, as its area will be proportional to (dx)² since both changes are proportional to dx. And that becomes negligible as dx approaches zero
    - Applying what we know about the derivatives of x² and sin(x), the tiny change d(x²) will be about 2x dx, and d(sin(x)) will be cos(x)dx
        - df = sin(x)2x dx + x²cos(x)dx
        - df/dx = sin(x)2x + x²cos(x)
    - More generally:
        - df = g(x)dh + h(x)dg
        - ***df/dx = g(x) dh/dx + h(x) dg/dx***
    - "Left d(Right) + Right d(Left)"
        - d/dx (sin(x)x²)
        - Left: sin(x)
        - Right: x²
        - Left (Right derivative): sin(x)2x
        - Right (Left derivative): x²cos(x)
    - Note: If we multiply by a constant, things get a lot simpler. The derivative is the constant multiplied by the derivative of the function:
    d/dx(2sin(x)) = 2cos(x)

- The chain rule for function composition:
    - If g(x) = sin(x) and h(x) = x², function composition is g(h(x))
    - g(h(x)) = sin(x²)
    - Imagine three number lines:
        - The first one holds the value of x
        - The second one holds the value of x²
        - The third one holds the value of sin(x²)
    - So the function (...)² gets us from line 1 to line 2
    - And the function sin() gets us from line 2 to line 3
    - If I move x to 3, x² will move up to 9
    - And the bottom value being sin(9) goes to approximately 0.412
    - For the derivative, let's nudge x by a little dx
        - Imagine the starting x was 1.5
        - The resulting nudge to the second value, the change in x² caused by such a dx, is d(x²), expanding to 2x dx, which for our specific input would be 2(1.5)dx
        - But for now, we can just simplify x² to h, and d(x²) to dh for this nudge
        - This makes it easier to think about the third value, which is now sin(h)
        - Its change is d(sin(h)), the tiny change caused by the nudge dh
            - Note: The fact that d(sin(h)) is moving to the left, while dh is going to the right, it means that d(sin(h)) will be negative. The sign depends on whether cos(h) is positive or negative at that particular point
        - We know that d(sin(h)) = cos(h)dh
        - If we replace h with x² again, d(sin(x²)) = cos(x²)d(x²)
        - So we know that the bottom nudge on the third line will be a size of cos(x²)d(x²)
        - Unfolding even further, the intermediate nudge d(x²) = 2x dx
        - So the final bottom nudge on the third line will be cos(x²) 2x dx
        - For example cos(1.5²) * 2(1.5)dx
            - We started at x = 1.5
            - And the size of the nudge on that third line will be about 
            cos(1.5²) * 2(1.5)dx
            - It's proportional to the size of dx, and this derivative is giving us that proportionality constant
    - d/dx sin(x²) = cos(x²)2x
    - We have the derivative of the outer function taking in the unaltered inner function, multiplied by the derivative of the inner function
    - The derivative of Outer(Inner) = d(Outer(Inner)) * d(Inner)
    - d/dx g(h(x)) = dg/dh(h(x)) * dh/dx(x)
    - dg/dh: The derivative of g evaluated on h, multiplied by the derivative of h
        - In our 3 line setup, when we took the derivative of the d(sin(h)), we expanded the size of that nudge as cos(h)dh
        - We didn't immediately know how the size of that bottom nudge depended on x
        - But we could take the derivative with respect to that intermediate variable h
        - Figure out how to express the size of the nudge of that third line as some multiple of dh, the size of the nudge on the second line
        - And it was only after that that we unfolded further by figuring out what dh was
    - ***d/dx g(h(x)) = dg/dh * dh/dx = dg/dx***
        - In this chain rule expression, we are looking at the ratio between a tiny change in g (dg) - the final output, to a tiny change in h that caused it (dh) h being the value that we plug into g
        - Then multiply that by the tiny change in h (dh) divided by the tiny change in x that caused it (dx)
        - Those dh cancel out and they give us a ratio between the change in that final output and the change to the input that cause it through a chain of events.

---

### Video 5: What's so special about Euler's number e?

**Key Concepts:**

- Let's focus on the derivatives of exponential functions, and especially eˣ
- To get an intuition, focus on the function 2ˣ: f(x) = 2ˣ
    - Let's think of the input as a time t (in days) and the output 2ᵗ, as a population mass
    - As days pass, population mass grows
    - t = time (measured in days)
    - M(t) = 2ᵗ (meaning that the population mass doubles every day)
        - At day t = 0, the total population mass is 2⁰ = 1, for the mass of 1 creature
        - At day t = 1, it's 2¹ = 2 
        - At day t = 2, it's 2² = 4 
        - At day t = 3, it's 2³ = 8 
        - And in general it keeps doubling every day

- For the derivative, we want to find dM/dt, the rate at which this population mass is growing, thought of as a tiny change in the mass, divided by a tiny change in time
    - Let's start by thinking of the rate of change over a full day, say between day 3 and day 4
    - In this case, it grows from 8 to 16, so that's 8 new creatures added over the course of one day
    - That rate of growth equals the population size at the start of the day
    - Between day 4 and day 5, it grows from 16 to 32, so that's a rate of 16 creatures/1 day
    - Which again equals the population size at the start of the day
    - In general the rate of growth over a full day equals the population size at the start of that day
    - So it may be tempting to say that this means that the derivative of 2ᵗ equals itself: d(2ᵗ)/dt = 2ᵗ, that the rate of change of this function at a given time t, is equal to the value of that function
    - But this is not correct, as we are making comparisons over a full day, considering the difference between 2ᵗ⁺¹ and 2ᵗ
    - Rate of change over one full day: (2ᵗ⁺¹ - 2ᵗ) / 1 = 2ᵗ
    - The fact that the population doubles exactly in one full day is specific to the base 2 and the time unit we chose, not a general property
        - For 2ᵗ, the population doubles every 1 unit of whatever time scale we use
        - If we used 3ᵗ, it would triple every day

- To find the actual derivative, we need to be asking what happens for smaller and smaller changes: what is the growth over the course of a 10th of a day, a 100th of a day, a billionth of a day? 
    - This is why we think of the function as representing a population "mass" over "size", since it makes sense to ask about a tiny change in mass over a tiny fraction of a day, but it doesn't make as much sense to ask about a tiny change in a discrete population size per second
    - More abstractly, for a tiny change in time (dt), we want to understand the difference between 2ᵗ⁺ᵈᵗ and 2ᵗ, all divided by dt (the change in the function per unit time), but now looking very narrowly

- Let's examine (2ᵗ⁺ᵈᵗ - 2ᵗ)/dt numerically:
    - A core property of exponentials is that we can break 2ᵗ⁺ᵈᵗ to 2ᵗ2ᵈᵗ
    - This lets us convert additive ideas (like steps in time) to multiplicative ideas (like rates and ratios)
    - After that move we now have (2ᵗ2ᵈᵗ - 2ᵗ)/dt
    - Which means we can factor 2ᵗ out: ***2ᵗ((2ᵈᵗ - 1)/dt)***
    - This manipulation is useful because it separates the 2ᵗ term from the dt terms - so the dt part doesn't depend on the actual time we started, it's just the nudge of the difference in time
    - And remember that the derivative of 2ᵗ is whatever the whole expression approaches as dt approaches zero [dt -> 0]
    - We can start plugging in very small values for dt, for example: 
        - (2⁰·⁰⁰¹ - 1) / 0.001 = 0.6933875...
        - (2⁰·⁰⁰⁰⁰¹ - 1) / 0.00001 = 0.6931496...
        - (2⁰·⁰⁰⁰⁰⁰⁰⁰¹ - 1) / 0.00000001 = 0.6931472...
    - We notice that for smaller and smaller choices of dt, the value approaches a very specific number, around 0.6931
    - This is some kind of constant to be multiplied by 2ᵗ
    - Unlike derivatives of other functions, everything that depends on dt, is separate from the value of t itself, so this is how we get the constant
    - So the derivative of 2ᵗ is just itself, but multiplied by some constant:
        - d(2ᵗ)/dt = 2ᵗ(0.6931472...)
    - Or generally: ***d(xᵗ)/dt = xᵗ * its proportionality constant***
    - This limiting process actually defines the "natural logarithm": 
        - lim [dt → 0] ((aᵈᵗ - 1)/dt) = ln(a)
    - So for any exponential: ***d/dt(aᵗ) = aᵗ * ln(a)***
    - This isn't just a coincidence - the natural log is literally defined as "the proportionality constant for base a"
    - Earlier it looked like the derivative for 2ᵗ was itself, but that was over the course of a full day. The rate of change over much smaller timescales, is not quite equal to itself but it's proportional to itself, with this very peculiar proportionality constant 0.6931
    - For example, the slope at 2³ is 2³(0.6931472...)
    - More generally, the slope at 2ᵗ is 2ᵗ(0.6931472...)

- If instead we dealt with the function 3ᵗ, the exponential property would also have led us to the conclusion that the derivative of 3ᵗ is proportional to itself, but this time it would have had a proportionality constant of 1.0986: 
    - dM/dt(3ᵗ) = 3ᵗ((3ᵈᵗ - 1) /dt), dt -> 0
    - 3⁰·⁰⁰⁰⁰⁰⁰⁰¹ - 1 / 0.00000001 = 1.0986123
    - Similarly, for 8ᵗ, the constant is 2.0794... (which interestingly, is 3 times more than the constant for 2ᵗ 0.6931...)

- There is a base for which that propotionality constant for an aᵗ, is 1
    - For this base, the derivative of aᵗ is not just proportional to itself, but actually equal to itself
    - This is the special number e = 2.71828...
        - e⁰·⁰⁰⁰⁰⁰⁰⁰¹ - 1 / 0.00000001 = 1.0000000
        - this is actually what defines the number "e"
    - All exponential functions are proportional to their own derivative
    - But e is the special number for which the proportionality constant is 1, meaning that ***eᵗ actually equals its own derivative***
    - The graph eᵗ has the peculiar property that the slope of a tangent line to any point on this graph, equals the height of that point above the horizontal axis (e¹ at 1, e² at 2, and so on)

- A different way to think about functions that are proportional to their own derivative, is by using the chain rule:
    - What is the derivative of e³ᵗ? d(e³ᵗ)/dt
    - To solve that, we take the derivative of the outermost function e³ᵗ, which due to the special nature of e, is just itself (e³ᵗ), and then by the chain rule, we multiply by the derivative of that inner function 3t = 3t¹, which is the constant 3
    - So d(e³ᵗ)/dt = 3e³ᵗ
    - Or in the visual example with the three numberlines, the first numberline would be t, the second one 3t, and the third one e³ᵗ, and we would think of how a slight nudge to t changes the value of 3t, and how that intermediate change nudges the final value of e³ᵗ
    - The derivative of e to the power of some constant times t, is therefore equal to that same constant times itself:
        - ***d(eᶜᵗ)/dt = ceᶜᵗ***

- Exponential functions with bases other than e have an extra constant when you take their derivative
    - For example, when we differentiate 2ᵗ, we get ln(2)2ᵗ. That ln(2) factor appears because 2 isn't the "natural" base e, meaning that the proportionality constant of 2ᵗ isn't 1, which in turn means that the derivative of 2ᵗ is not 2ᵗ * 1, but 2ᵗ * some other proportionality constant. The constant in this case is ln(2)

- To explain further how we get ln(2) as being the constant, let's first review why eˡⁿ⁽ᵃ⁾= a:
    - The natural logarithm and exponential function are inverse functions that undo each other
    - "ln" means "e to some power", or "2.71828^?"
    - ln is called "natural" precisely because e is the natural base for calculus - it makes derivatives the cleanest
    - ln(a) asks the question: "e to what power gives me a?"
    - eᵃ provides the answer: "e to this power gives the result"
    - ***if ln(a) = k, then eᵏ = a***
    - "e to what power k gives me a?" "e to the k power gives me a"
        - if ln(a) = k, then eˡⁿ⁽ᵃ⁾ = eᵏ
        - but eᵏ = a
        - therefore, ***eˡⁿ⁽ᵃ⁾ = a***
    - For example, for a = 2:
        - ln(2) ≈ 0.6931, which means e⁰·⁶⁹³¹ ≈ 2
        - So eˡⁿ⁽²⁾ = e⁰·⁶⁹³¹ = 2 
    - This identity allows us to rewrite any exponential in terms of e
    - 2ᵗ = (eˡⁿ⁽²⁾)^ᵗ = eˡⁿ⁽²⁾ᵗ
    - The middle step uses eˡⁿ⁽²⁾ = 2
    - Without this identity, we couldn't convert between different exponential bases
    - This is the foundation for understanding why derivatives of aᵗ have the ln(a) constant
    - eᵃ and ln(a) undo each other in both directions:
        - eˡⁿ⁽ᵃ⁾ = a (exponential undoes logarithm)
        - ln(eᵃ) = a (logarithm undoes exponential)
        - This is analogous to how (√x)² = x and √(x²) = x
        - Being inverses means composing them (applying one then the other) returns the original value

- So now the function 2ᵗ = (eˡⁿ⁽²⁾)^ᵗ = eˡⁿ⁽²⁾ᵗ
- Now our function is in terms of e, which we know how to differentiate:
    - Let's apply the chain rule:
        - instead of 2ᵗ, we now have eˡⁿ⁽²⁾ᵗ
        - ln(2) is just a number (approximately 0.693), as e⁰·⁶⁹³ = 2
        - the exponent is ln(2)t, which is a constant * t, so e⁰·⁶⁹³ᵗ
    - When we differentiate a constant * t:
        - the derivative of a constant * a variable is the constant * the derivative of variable
        - d/dt(constant * t) = constant * d/dt(t) = constant * 1 = constant
            - for example, d/dt(5t) = 5 * d/dt(t) = 5 * 1 = 5
            - similarly, d/dt(ln(2)t) = ln(2) * d/dt(t) = ln(2) * 1 = ln(2)
        - The d/dt(t) = 1 part means "t itself changes at rate 1 with respect to t" (trivially true - it's the independent variable)
        - The ln(2) part is the constant multiplier that scales this rate
    - Why? When differentiating ln(2)t:
        - ln(2) stays (it's a constant)
        - d/dt(t) = 1 (it changes at the same rate as itself, 1:1 ratio)
        - ln(2) * 1 = ln(2)
        - so we are left with just the constant ln(2)
    - So to differentiate eˡⁿ⁽²⁾ᵗ, we multiply itself by the derivative of the exponent, and the derivative of the exponent ln(2)t is ln(2)

- Remember that the natural logarithm fundamentally measures "the proportionality constant between aᵗ and its derivative". When we computed (2⁰·⁰⁰¹ - 1)/0.001 ≈ 0.6931 earlier, we were literally calculating ln(2) numerically
- Combinining the fact that eᵗ is its own derivative with the chain rule, the derivative of this function 2ᵗ is proportional to itself, with a proportionality constant equal to the natural log of 2 ln(2)
- So the derivative of 2ᵗ = eˡⁿ⁽²⁾ᵗ is ln(2)eˡⁿ⁽²⁾ᵗ
- Since eˡⁿ⁽²⁾ᵗ = 2ᵗ, we can substitute 2ᵗ back and get: d/dt(2ᵗ) = ln(2)2ᵗ
- The key pattern: The number we raise e to in order to GET our base 2, is the SAME number we multiply by in the derivative
    - For 2ᵗ: eˡⁿ⁽²⁾ = e⁰·⁶⁹³ = 2, derivative = 0.693 * 2ᵗ
    - For 3ᵗ: eˡⁿ⁽³⁾ = e¹·⁰⁹⁹ = 3, derivative = 1.099 * 3ᵗ
    - For aᵗ: eˡⁿ⁽ᵃ⁾ = a, derivative = ln(a) * aᵗ

- The same goes for all the other bases. The mystery proportionality constant that pops up when taking derivatives, is just the natural log of the base. The answer to the question "e to the what?" equals that base
- In calculus we rarely see exponentials written as some base a to the power of t (aᵗ). Instead, we almost always write the exponential as e to the power of some constant * t (eᶜᵗ)
    - For example instead of 3ᵗ we write e⁽¹·⁰⁹⁸⁶···⁾ᵗ
    - Actually, there are many ways to write any particular exponential function: 2ᵗ = e⁽⁰·⁶⁹³⁾ᵗ = π⁽⁰·⁶⁰⁵⁾ᵗ = ...
    - What is special about writing exponentials in terms of e, is that it gives the constant in the exponent a nice readable meaning

- All sorts of natural phenomena involve some rate of change that's proportional to the thing that is changing:
    - For example the rate of growth of a population actually does tend to be proportional to the size of the population itself
    - Or if we put a cup of hot water in a cool room, the rate at which the water cools is proportional to the difference in temperature between the room and the water, meaning that the rate at which that difference changes, is proportional to itself
    - If we invest our money, the rate at which it grows is proportional to the amount of money we have invested at any time
- In all of these cases, where some variable's rate of change is proportional to itself, the function describing that variable over time will be an exponential
- The constant c in eᶜᵗ directly represents the growth/decay rate (positive for growth, negative for decay)
- And even though there are lots of ways to write any exponential function, it's very natural to choose to express these functions as e to the power of some constant times t, since that constant carries a very natural meaning: it's the same as the proportionality constant between the size of the changing variable and the rate of change

- Summary of important concepts:
    - All exponentials are self-similar under differentiation (proportional to themselves)
    - e is special because its proportionality constant is 1
    - For any base a: aᵗ = eˡⁿ⁽ᵃ⁾ᵗ, which explains why ln(a) appears in derivatives
    - Writing exponentials as eᶜᵗ makes c directly interpretable as the "rate constant" in natural phenomena

---

### Video 6: Implicit differentiation, what's going on here?

**Key Concepts:**

- Say that you have a circle with radius 5 centered at the origin of the xy plane, defined by the equation x² + y² = 5²:
    - All the points of this circle are distance 5 from the origin, as encapsulated by the pythagorean theorem, where the sum of the squares of the two legs of the triangle (x=3)² + (y=4)² equals the hypotenuse 5²
    - Suppose we want to find the slope of a tangent line to the circle at the point x,y = 3,4
    - By geometry we already know that this tangent line is perpendicular to the radius touching it at that point, forming a right corner
    - But if we didn't already know that, or if we want a technique that generalizes to curves other than just circles, we need a different approach
    
- As with other problems about the slopes of tangent lines to curves, the key is to zoom in close enough that the curve basically looks just like its own tangent line, and then ask about a tiny step along that curve:
    - The y component of that little step is dy, and for the x component is dx
    - So the slope we want is rise over run, dy/dx
    - But unlike other tangent slope problems in calculus, this curve is not the graph of a function (as x² + y² = 5² is not a function)
    - So we can't just take a simple derivative asking about the size of some tiny nudge to the output of a function, caused by some tiny nudge to the input: x is not an input, and y is not an output; they are both just interdependent values related by some equation

- Reminder: Why a circle is not a function:
    - A function needs a single output for each input
    - With a circle like x² + y² = 5², if x = 3, then:
        - 3² + y² = 25
        - y² = 16
        - y = ±4
    - So we get two outputs, y = 4 and y = -4

- Explicit vs Implicit Relationships:
    - Usually in calculus we write y = f(x), meaning "y is determined by x"
        - This is an explicit function: y is isolated on one side
        - dy/dx measures how y changes when we nudge x
    - But some relationships can't be (or aren't) solved for y explicitly
        - Example: A circle x² + y² = 25 constrains x and y together, as they both change together
        - We can't write y = f(x) for the whole circle (we would need two pieces: y = ±√(25-x²))  
    - Implicit Curves:
        - An "implicit curve" is just the set of all points x,y that satisfy some property that involves both variables x and y (F(x,y) = 0)
        - This describes the relationship between x and y without isolating either variable
        - Examples:
            - Circle: x² + y² - 25 = 0
            - Even explicit y = ln(x) can be rewritten implicitly as: y - ln(x) = 0
        - Explicit functions are just special cases of implicit curves - the ones we can solve for y
    - Why Implicit Differentiation?
        - Implicit differentiation is essential when solving for y explicitly is difficult or impossible (like x³ + y³ = 6xy) or when we want to avoid messy algebra
        - When we have F(x,y) = 0, both x and y change together along the curve
        - When we can't just "plug in x and get y" - they are interdependent
        - Implicit differentiation lets us find dy/dx directly from F(x,y) = 0 without solving for y first
        - We treat both x and y as changing together, constrained by their relationship, rather than y being a simple output of x

- For implicit differentiation, we can use two notations:
    - The Leibniz/derivative notation:
        - A derivative is a rate of change; a single number or function that tells you how fast one quantity changes relative to another
        - Everything is explicitly "with respect to x"
        - dy/dx is treated as a single symbol (the derivative)
        - It's a ratio: derivative = (change in y) / (change in x)
        - y is secretly a function of x even though we can't write it explicitly, so whenever we differentiate something containing y, we need to account for that hidden dependence using the chain rule
        - When differentiating implicitly in derivative notation:
            - For terms containing only x: Apply derivative rules directly (for x² we write 2x)
            - For terms containing only y: Apply derivative rules, then multiply result by dy/dx (for y² we write 2y dy/dx)
                - Note: This applies the chain rule to y²(x): the outer function is u² with derivative 2u (evaluated at u=y and giving 2y), then multiplied by the inner derivative dy/dx"
            - For terms containing both x and y: Apply derivative rules, treating y as a function of x, so any derivative of y gets multiplied by dy/dx
            - For constants: Derivative is 0

    - The differential notation (more elegant):
        - A differential is an infinitesimal change in a variable; a tiny increment
        - dy and dx are treated as separate infinitesimal quantities (a tiny change in y and a tiny change in x)
        - They're separate objects and can be manipulated independently in equations
        - Uses no fraction bars, just products
        - When differentiating implicitly in differential notation:
            - For terms containing only x: Apply derivative rules, then multiply by dx (for x² we write 2x dx)
            - For terms containing only y: Apply derivative rules, then multiply by dy (for y² we write 2y dy)
            - For terms containing both x and y: Apply derivative rules, then multiply the x-derivative parts by dx, and the y-derivative parts by dy
            - For constants: Derivative is 0, no differential needed

    - We can move between derivative and differential notations algebraically:
        - Differential form: 2y dy = -2x dx
        - Divide both sides by dx: (2y dy)/dx = (-2x dx)/dx
        - Separate coefficient from differentials: 2y (dy/dx) = -2x (dx/dx)
        - Simplify: 2y (dy/dx) = -2x * 1
        - Derivative form: 2y (dy/dx) = -2x
        - The other way around: multiply derivative form by dx to get differential form

    - The relationship between derivatives and differentials:
        - The derivative is like Speed:
            - Speed = distance/time (rate of change, a ratio)
            - dy/dx (slope): change in distance/change in time
            - "I'm going 60 km/h" 
        - The differential is like Distance:
            - Distance = speed * time (actual small change, a product)
            - dy = (dy/dx)dx: distance = 60 * dt hours = 60 km/h * 2 h = 120 km
            - "In dt hours, I travel 60 * dt km"  
         - A notational subtlety:
            - In dy = (dy/dx) dx, the two "dx"s are actually different things:
                - The dx in dy/dx is part of the derivative symbol (it means "with respect to x")
                - The dx being multiplied is the actual infinitesimal change in x
            - Like in distance = 60 km/h * 2h:
                - The "h" in km/h is part of the rate unit
                - The "2h" is the actual time interval
                - They look the same but serve different roles
                - The units cancel algebraically: km/h * h = km
            - Leibniz designed the notation so it looks like dx "cancels":
                - While this manipulation is algebraically valid in differential calculus, dy/dx is actually defined as a limit (lim Δx→0 Δy/Δx), not literally a fraction. The notation's genius is that it behaves like one
                - Visually: dy/dx * dx = dy (the dx appears to cancel out)
                - What's really happening: rate * input change = resulting change
                - The unit cancellation makes the notation intuitive even though the dx's play different roles
                

- The implicit differentiation procedure to find dy and dx for implicit curves like the circle:
    - We start by taking the derivative of both sides (x² + y² = 5²)
        - For x² we write 2x dx
        - For y² we write 2y dy
        - And the derivative of the constant 5² is 0 
        - The equation becomes 2x dx + 2y dy = 0
        - So we have  2x * (small change in x) + 2y * (small change in y) = 0
    - We continue by rearranging 2x dx + 2y dy = 0, to get dy/dx = -x/y:
        - 2x dx + 2y dy = 0
        - 2y dy = - 2x dx
        - 2y (dy/dx) = - 2x 
            - Note that 2y is a coefficient and when dividing an entire product with a differential, only the differential part (dy or dx) participates in the division operation. The coefficient 2y stays as a multiplier
        - dy/dx = -2x/(2y)
        - dy/dx = -x/y
    - The equation 2x dx + 2y dy = 0 is a differential equation, and dividing by dx converts it to the derivative notation dy/dx
    - If we have 2x * (small change in x) + 2y * (small change in y) = 0, we can rearrange to find the RATIO of these small changes: (change in y)/(change in x) = -x/y
    - So at the point with coordinates x,y = 3,4, that slope would be -3/4

- This is connected to a different type of calculus problem - the related rates problem:
    - Imagine a 5 meter long ladder held up against a wall:
        - The top of the ladder starts 4 meters above the ground 
        - By the pythagorean theorem, the bottom is 3 meters away from the wall
        - The ladder is slipping down in such a way that its top is dropping at a rate of 1 meter per second (1m/s)
    - Our question is: In that initial moment, what is the rate at which the botton of the ladder is moving away from the wall?
        - That distance from the bottom of the ladder to the wall is 100% determined by the distance from the top of the ladder to the floor
    - How do the rates of change for each of those values depend on each other?
        - Let's label the distance from the top of the ladder to the ground y(t), written as a function of time because it's changing
        - Let's label the distance from the bottom of the ladder and the wall x(t), also written as a function of time because it's changing
        - The key equation that relates these terms is the pythagorean theorem  x(t)² + y(t)² = 5²
        - This is true at all points in time

- There are two methods in which we could solve this problem. Both methods solve the same problem but take fundamentally different approaches to applying calculus:
    - Solution 1 - Explicit Function approach
        - Isolate x(t) first, then differentiate:
            - Express x explicitly as a function of y: x(t) = √(25 - y(t)²)
            - Then take the derivative of this explicit formula
        - Process:
            - Solve the constraint equation for one variable
            - Apply the chain rule to the resulting nested function
            - Substitute known values at the end
        - Characteristics:
            - More algebraically intensive: it requires nested chain rule application
            - Single-variable thinking: we treat x as depending on y, which depends on t
            - Formula-first: we get a general expression for dx/dt before plugging in numbers
        - Analogy:
            - Like finding a direct route on a map: "To get from A to B, first go north, then east. Now calculate the exact distance"

    - Solution 2 - Implicit Differentiation approach
        - Differentiate the relationship directly without isolating variables:
            - Work with both x(t) and y(t) simultaneously in the equation
            - Treat the constraint x² + y² = 25 as an implicit relationship
        - Process:
            - Differentiate both sides of the constraint equation with respect to time
            - Use chain rule on each term separately (2x dx/dt and 2y dy/dt)
            - Solve the resulting algebraic equation for the unknown rate
        - Characteristics:
            - Conceptually elegant: no need to isolate variables, and it works even when we can't easily isolate a variable (like if the constraint was something like x³ + y³ + xy = 25)
            - Cleaner algebra: the chain rule is applied to each term in parallel, so we avoid the messy nested chain rule usage
            - Multi-variable thinking: both variables stay in play throughout
            - We directly see how the rates of change must balance each other: 2x(dx/dt) = -2y(dy/dt)
            - The equation 2x(dx/dt) + 2y(dy/dt) = 0 has a clear interpretation: "The changes in x² and y² must cancel out because their sum is constant"
            - Direct to the answer: immediately gives you a solvable equation
            - Symmetric treatment: both x and y are handled the same way
        - Analogy:
            - Like using a compass bearing: "Whatever direction you move, the constraint tells you how all variables must change together"

    - Comparison:
        - Solution 1 treats the problem as: "x is a function of y, which is a function of t"
        - Solution 2 treats the problem as: "x and y are both functions of t, constrained by a relationship"
        - Solution 2 leverages implicit differentiation, a powerful technique that says: "I don't need to solve for one variable explicitly; I can just differentiate the relationship itself and solve for the rate I care about"
        - Implicit differentiation essentially automates the chain rule for nested functions - it's computationally equivalent but conceptually cleaner

    - Solution 1 Analytically:
        - One way to solve x(t)² + y(t)² = 5² would be to isolate x(t) and then figure out y(t) based on that 1m/s drop rate: x(t) = (5² - y(t)²)¹⁄²
        - Then we would take the derivative of the resulting function dx/dt, the rate at which x is changing with respect to time
        - This method involves a couple of layers of using the chain rule:
            - Step 1 is to isolate x(t):
                - x(t)² + y(t)² = 5²
                - x(t)² = 25 - y(t)²
                - x(t) = √(25 - y(t)²)
            - Step 2 is to take the derivative with respect to time:
                - dx/dt = d/dt √(25 - y(t)²)
            - Step 3 is to apply the chain rule to the outer function:
                - The outer function is the square root
                - The derivative of √u is (1/2)u⁻¹⁄²
                - dx/dt = (1/2)(25 - y(t)²)⁻¹⁄² * d/dt 25 - y(t)² 
                    - Recall that: a⁻ⁿ = 1/aⁿ
                    - Recall that: a¹⁄² = √a
                - dx/dt = 1 / (2√(25 - y(t)²)) * d/dt 25 - y(t)² 
            - Step 4 is to apply the chain rule to the inner function:
                - d/dt 25 = 0
                - d/dt y(t)² = 2y(t) * dy/dt (chain rule again!)
                - d/dt 25 - y(t)² = -2y(t) * dy/dt
            - Step 5 is to combine the results:
                - Substitute back:
                    - dx/dt = 1/(2√(25 - y(t)²)) * (-2y(t) * dy/dt)
                - Simplify:
                    - dx/dt = -y(t) * dy/dt / √(25 - y(t)²)
            - Step 6 is to plug in the known values at the initial moment:
                - y(t) = 4 meters
                - dy/dt = -1 m/s (negative because falling)
                - √(25 - y(t)²) = √(25 - 16) = √9 = 3 meters (this is x(t)!)
                - Therefore: dx/dt = -4 * (-1) / 3 = 4/3 m/s
            - Answer: 
                - The bottom of the ladder is moving away from the wall at 4/3 meters per second (approximately 1.33 m/s)
                - The final formula dx/dt = -y * (dy/dt)/x makes physical sense, as the rate depends on the ratio of the heights and the rate of vertical change
    
    - Solution 2 Analytically:
        - The left hand side of x(t)² + y(t)² = 5² is a function of time
            - It just so happens to equal a constant (the length of the ladder which doesn't change as time passes)
            - But it's still written as an expression dependent on time, so we can manipulate it like any other function with t as an input

        - First, let's take the derivative of x(t)² + y(t)²:
            - d(x(t)² + y(t)²) / dt
            - This means "if I let a little time dt pass, which causes y to slightly decrease and x to slightly increase, how much does x(t)² + y(t)² change?
            - We also know that that the derivative should equal 0, since the expression is a constant, and nudges in time do not affect constants:
                - d(x(t)² + y(t)²) / dt = 0

        - Next, let's compute this derivative:
            - x(t) is a function (it takes time as input and outputs a distance)
            - The expression x(t)² is composite, formed by composing two functions (the squaring function and the position function)
            - So by the chain rule we need the derivative of the Outer(Inner) * the derivative of the Inner
            - We need the derivative of x(t)² * the derivative of x(t)
                - The derivative of x(t)² is 2x(t) 
                - The derivative of x(t) is dx/dt
                - 2x(t) * dx/dt
                - 2x dx represents the size of a change to x² caused by some change to x, and then we are dividing out by dt
            - Likewise, the rate at which y(t)² is changing is 2y(t) * the derivative of y with respect to time:
                - 2y(t) * dy/dt
            - Let's not forget to set the whole expression equal to 0, as x(t)² + y(t)² must not change while the ladder moves (the ladder size does not change):
                - 2x(t) dx/dt + 2y(t) dy/dt = 0

        - Next, let's plug in the known values:
            - At the very start with time t=0, the height y(t) is 4m and the distance of x(t) is 3m:
                - 2(3) dx/dt + 2(4) dy/dt = 0
            - Since the top of the ladder is dropping at a rate of 1m/s, the derivative dy/dt is -1m/s:
                - 2(3) dx/dt + 2(4) (-1) = 0 
            - This gives us enough information to isolate the derivative dx dt

        - Finally, let's work it out algebraically:
            - 2(3) dx/dt + 2(4) (-1) = 0
            - 6 dx/dt + 8(-1) = 0
            - 6 dx/dt - 8 = 0
            - 6 dx/dt = 8
            - dx/dt = 8/6
            - dx/dt = 4/3
        
        - So dx/dt comes out to be 4/3 meters per second
        - And this answers our question "In that initial moment, what is the rate at which the botton of the ladder is moving away from the wall?"

- How does this compare to finding the slope of a tangent line to the circle:
    - In both cases, we had the equation x² + y² = 5²
    - And in both cases, we ended up taking the derivative of each side of this expression: 2x dx + 2y dy = 0
    - But for the ladder question, these expressions were functions of time, so taking the derivative of x(t)² + y(t)² = 5² has a clear meaning:
        - 2x(t) dx/dt + 2y(t) dy/dt = 0
        - It's the rate at which the expression changes as time changes
    - But for the circle question, rather than saying that a small amount of time dt has passed, which causes x and y to change, the derivative just has these tiny nudges dx and dy just floating free (without dt), not tied to some other common variable, like time: 
        - 2x dx + 2y dy = 0 (no dt)
    - Derivative vs differential notation:
        - 2x(t) dx/dt + 2y(t) dy/dt = 0 is the Leibniz/derivative notation
        - 2x dx + 2y dy = 0 is the differential notation

- Another intuitive way to think about implicit differentiation:
    - Let's give the expression x² + y² the name "S"
    - S is a function of two variables, x and y
        - It takes every point x, y on the plane, and associates it with a number
        - For points on the circle, that number happens to be 5² so 25
        - If we stepped off the circle away from the center, that value would be bigger
        - For other points x, y closer to the origin, that value would be smaller
    - What it means to take a derivative of this expression S, is to consider a tiny change to BOTH of these variables, some tiny change dx to x, and some tiny change dy to y (not necessarily one that keeps us on the circle; just any tiny step in any direction of the xy plane)
        - dS = 2x dx + 2y dy
    - And from there we ask "how much does the value of S change?"
    - That difference in the value of S before and after the nudge, is dS
    - For example, if we start off at point where x = 3 and y = 4, and if dx is -0.02 and dy is -0.01
    - Then the decrease in s, the amount that x² + y² changes over that step, would be: 
        - dS = 2(3)(-0.02) + 2(4)(-0.01)
    - This is what the derivative expression dS = 2x dx + 2y dy actually means
    - It's a recipe that tells us how much the value x² + y² changes as determined by the point x,y where we start and the tiny step dx dy that we take
    - This is only an approximation that gets truer and truer for smaller and smaller choices of dx and dy
    - The key point is that when we restrict ourselves to steps along the circle, we want to ensure that this value of S does not change
    - Ww are currently at a point (say x=3, y=4) where S equals 25, and we want to keep it at that value of 25. That is, dS should be 0
    - So setting the expression 2x dx + 2y dy equal to 0 is the condition under which one of these tiny steps actually stays on the circle we are currently on (this same condition dS = 0 applies to staying on ANY circle, and what makes it specific to the radius 5 circle is that we started at a point where x² + y² = 25)
    - Or more precisely, that condition is what keeps us on the tangent line of the circle, not the circle itself (but for tiny enough steps, those are essentially the same thing)

- One more example: sin(x)y² = x
    - This expression corresponds to several u-shaped curves on the plane (multiple curves exist because sin(x) is periodic, so different x values can give the same sin(x)y² value)
    - Those curves represent all of the points x,y where the value of sin(x)y² equals the value of x
    - Imagine taking some tiny step with components dx and dy, and not necessarily one that keeps us on the curve
    - Taking the derivative of each side of this equation will tell us how much the value of that side changes during the tiny step
    - On the left side, by the product rule we get "Left d-Right + Right d-Left":
        - The left side is a product of two functions of x:
            - sin(x)
            - y² (remember that y is implicitly a function of x)
        - In derivative form:
            - sin(x) * (d(y²)/dx) + y² * (d(sin(x))/dx)
            - By the chain rule, the derivative of y² is 2y * dy/dx
            - And the derivative of sin(x) is cos(x)
            - sin(x)(2y dy/dx) + y² cos(x)
            - Differentiate the right side:
                - d/dx (x) = 1
            - Combine:
                - sin(x)(2y dy/dx) + y² cos(x) = 1
        - In differential form:
            - sin(x) d(y²) + y² d(sin(x))
            - sin(x)(2y dy) + y²(cos(x) dx) = dx
    - The right side is simply x, so the size of a change to that value is exactly dx
    - Setting these two sides equal to each other constrains which steps (dx, dy) are allowed. Only steps where the left and right sides change by the same amount will keep us on the curve
    - From there, depending on what problem we are trying to solve, we have something to work with algebraically, most commonly trying to figure out what dy/dx is

- How we can use the technique of implicit differentiation to find new derivative formulas:
    - As we know the derivative of eˣ is itself; but what is the derivative of its inverse function, the natural log of x (d(ln(x))/dx)?
        - The expression of y = ln(x) is explicit (y is isolated and explicitly defined as a function of x)
        - But its graph can be thought of as an implicit curve: it's all the points x,y on the plane where y happens to equal ln(x)
        - The x's and the y's on this curve aren't as intermingled as in the previous examples
    - The slope of the graph dy/dx is the derivative of ln(x)
        - Rather than differentiating ln(x) directly, we can rearrange y = ln(x) in the implicit form as eʸ = x, so that we can then use the known derivative of eʸ (which is itself)
    - Now both variables are intermingled in the equation, and we can use implicit differentiation
    - We can take the derivative of both sides, effectively asking how a tiny step with components dx, dy changes the value of each one of these sides:  
        - eʸ = x
        - eʸdy = dx
    - For a step to stay on the curve (remain tangent to it), the changes to both sides must be equal: eʸdy = dx. This constrains the relationship between dx and dy
    - Rearrange to find the derivative:
        - eʸdy = dx
        - dy = dx/eʸ
        - dy = dx * 1/eʸ
        - dy/dx = 1/eʸ
    - When we are on the curve, eʸ is by definition the same thing as x (eʸ=x):
        - So we can simplify the slope as dy/dx = 1/x
    - An expression for the slope of a function graph written in terms of x like this, is the derivative of that function
    - So the derivative of ln(x) is 1/x (which is a decreasing hyperbola)
        - The graphs of y = eˣ and y = ln(x) are reflections across y = x (inverse functions)
        - Interestingly, while the derivative of eˣ is identical to the function, the derivative of ln(x) is 1/x, a completely  different-looking curve. This reflects the inverse relationship: exponential growth versus logarithmic growth
            - eˣ is self-similar: Its rate of change maintains the same character as the function itself (exponential)
            - ln(x) is self-inverting: Its rate of change (1/x) has the opposite character - where ln(x) grows without bound, 1/x shrinks toward zero
    - This technique demonstrates the power of implicit differentiation: by cleverly rewriting an explicit function in implicit form, we can derive formulas for derivatives we don't yet know using derivatives we already know

- All of the above is a peek into multivariable calculus, where we consider functions with multiple inputs and how they change as we tweek those multiple inputs, such as f(x,y) = sin(x)y²

---

### Video 7: Limits, L'Hôpital's rule, and epsilon delta definitions

**Key Concepts:**

- The formal definition of a derivative:
    - When we have a function f(x), to think about its derivative at a particular imput, say at x=2, we imagine nudging that input a little dx and looking at the resulting change to the output, df
    - The ratio Δf/Δx (or [f(2+dx) - f(2)]/dx), the rise/run slope between the starting point and the nudged point, is almost what the derivative is; but the actual derivative is whatever this ratio approaches as dx approaches 0
        - Using Δf/Δx notation, as the df/dx notation already implies the limit has been taken
    - The nudge to the output df, is the difference between f at the starting input plus dx, and f at the starting input; the change to the output caused by dx:
        - (f(2+dx) - f(2)) / dx, dx -> 0
    - To express that we want to find what this ratio approaches as dx approaches 0, we write "lim" for limit, with "dx -> 0" below it
    - We almost never see terms with a lowercase dx inside a limit expression like this; the standard is to use the variable "Δx", or often "h"
    - Terms with the lowercase d in the typical derivative expression have the idea of a limit already built in (the idea that dx is supposed to eventually go to 0), whereas Δx or h write out the limit process explicitly:
        - df/dx(2) = lim h->0 (f(2+h) - f(2)) / h
    - This is the formal definition of the derivative
    - The paradoxical idea of an infinitely small change:
        - We are analyzing what happens for arbitrarily small choices of h
        - These changes to the input are ordinary numbers, not infinitesimals
        - Remember to ask what happens when that small thing approaches 0
        - Limits help us avoid talking about infinitely small changes, and instead ask what happens as the size of some small change to our variable approaches 0 

- The (ε, δ) definition of limits:
    - What does it mean exactly for one value to approach another?
    - Consider the function ((2+h)³ - (2)³)/h
    - This is the definition of a derivative of x³ evaluated at x=2: 
        - d(x³)/dx(2)
    - Let's think of it like any function with an input h
    - The graph is a continuous-looking parabola (which makes sense because it's a cubic term divided by a linear term)
    - For h=0, plugging in 0 would give us 0/0, which is undefined:
        - ((2+0)³-(2)³) / 0 = 0/0
    - So actually the parabola graph has a hole at that point, although it is defined for all inputs as close to 0 as we want
    - As h approaches 0, the corresponding output (the height of this graph) approaches 12 from both sides
    - So the limit of this ratio as h approaches 0 is equal to 12
    - For a given range of inputs within some distance of 0 (excluding 0 itself) let's look at all possible heights of the graph within that range:
    - As the range of input values closes in more and more tightly around 0, the range of output values closes in more and more closely around 12
    - And the size of that range of output values can be made as small as we want
    - As a counter example, for a function which is also not defined at 0 but kind of jumps up that point, when we approach h=0 from the right the function approaches the value 2, but when we approach h=0 from the left the function approaches the value 1
        - Since there is not a single clear, unambiguous value that this function approaches as h approaches 0, the limit is not defined at that point
        - When we look at any range of inputs around 0 and consider the corresponding range of outputs, as we shrink that input range the corresponding outputs don't narrow in on any specific value
        - Instead, those outputs straddle a range that never shrinks smaller than 1 unit, even as we make that input range as tiny as we can imagine
        - This perspective of shrinking an input range around the limiting point and seeing whether or not we are restricted in how much that shrinks the output range, leads to the (ε, δ) definition of limits
        - This is a glimpse into the field of real analysis, that makes the intuitive ideas of calculus more vigorous
        - When a limit exists, we can make the output range as small as we want, but when the limit doesn't exist, that output range cannot get smaller than some particular value, no matter how much we shrink the input range around the limiting input
    
    - (ε, δ) as input/output:
        - δ is the range around the input point (0 in our example) - how close we need to keep h to 0
        - ε is the range around the limit value (12 in our example) - how close we demand the outputs stay to the limit
        - For any ε-range we demand around the limit, we can find a δ-range around the input point such that staying within the δ-range guarantees staying within the ε-range

    - In our original example where the limit was 12:
        - Think about demanding that all outputs stay within some distance of 12 (say from 11 to 13), where it is common to use epsilon (ε) to denote that distance; the intent is that the distance ε is as small as we want
        - What it means for the limit to exist, is that for any range of outputs we demand (any distance ε around 12, no matter how small), we will always be able to find a corresponding range of inputs (some distance delta δ around 0) so that any input within δ of 0 corresponds to an output within ε of 12
            - δ could be from -0.001 to 0.001
            - ε could be from 11 to 13
        - That is true for any ε we choose, no matter how small; for that given ε, we must always be able to find a corresponding δ
    - In contrast, when the limit does not exist, like in our example of a function not defined at 0

    - There exists a sufficiently small ε (for example 0.4) such that no matter how small we make our δ-range around 0, the corresponding range of outputs is always bigger than ε
    - If we try to claim L = 1 is the limit:
        - Choose ε = 0.4
        - This means we demand outputs stay in the range (1 - 0.4, 1 + 0.4) = (0.6, 1.4)
        - No matter how small we make δ, inputs just to the right of 0 give outputs near 2
        - Since 2 is outside the range (0.6, 1.4), we have violated the ε constraint
        - The distance from 2 to 1 is 2-1 = 1, which is greater than ε = 0.4
    - If we try to claim L = 2 is the limit:
        - Choose ε = 0.4
        - This means we demand outputs stay in the range (2 - 0.4, 2 + 0.4) = (1.6, 2.4)
        - No matter how small we make δ, inputs just to the left of 0 give outputs near 1
        - Since 1 is outside the range (1.6, 2.4), we have violated the ε constraint
        - The distance from 1 to 2 is |2-1| = 1, which is greater than ε = 0.4
    - If we try L = 1.5:
        - Choose ε = 0.4
        - This means we demand outputs stay in the range (1.5 - 0.4, 1.5 + 0.4) = (1.1, 1.9)
        - Outputs near 1 are outside this range (since 1 < 1.1)
        - Outputs near 2 are outside this range (since 2 > 1.9)
    - We see that the outputs jump between ~1 and ~2, and that gap of 1 unit is larger than our ε = 0.4 tolerance, so no single value can be "the limit."
    - Limits are used to formally define the derivative, ε and δ define the limit itself

- How to compute limits:
    - Say we have the function sin(πx) / x²-1 modelling a dampened oscilation
    - The function looks continuous, but there is a problematic value at x=1
    - When we plug x=1 in, the denominator comes out to be 0
    - And the numerator sin(πx) is also 0
        - Reminder: The sine function gives us the y-coordinate of a point on a unit circle
        - The angle π radians is 180°
        - At 180° we are at the point (-1,0) on the unit circle
        - The y-coordinate is 0, so sin(π) = 0
        - sin(nπ) = 0 for any integer n, because these angles correspond to points on the horizontal axis of the unit circle (at 0°, ±180°, ±360°, etc.), where the y-coordinate is always zero
    - So plugging in x=1 results in 0/0, meaning that the function is not defined at that input, and the graph should have a hole there
    - This also happens at x=-1, but let's focus on x=1 for now
    - The graph certainly does seem to approach a distict value at that point
    - How to find the output it approaches as x approaches 1, since we can't just plug in 1?
        - One way to approximate it would be to plug in a number that is really close to 1, like 1.00001
        - Doing that, we would get a number around -1.5708...
    
- A better way to compute limits - L'Hôpital's rule:
    - A systematic process that takes an expression that looks like 0/0 at some input, and asks what is its limit as x approaches that input
    - After limits helped us write the definition for derivatives:
        - lim h->0, df/dx
    - Derivatives can in turn help us evaluate limits

    - For the function sin(πx) / x²-1, consider the graphs sin(πx) and x²-1 separately:
        - Focus on what happens on both graphs around x=1
        - They are both 0 at that point, crossing the x-axis
        - Remember we are looking for the derivative of their composite function at that point

    - Let's first consider sin(πx):
        - Just like when plugging in a specific value near 1, like 1.00001, let's zoom in on that point and consider a tiny nudge dx away from it
        - The value of sin(πx) changes by some amount. The change in output caused by the nudge dx to the input, is approximately d(sin(πx)) ≈ derivative * dx. We use d(sin(πx)) to denote this infinitesimal change, similar to how we wouldd write dy for a generic function y
        - Next, we take the derivative of d(sin(πx))
        - Using the chain rule, the derivative evaluates to cos(πx)·π, so the change in sin(πx) is approximately π·cos(πx)·dx (differential notation)
        - How is π the derivative of πx?
            - For d/dx cx where c is any constant, the derivative equals c
            - Think about the basic derivative rule: d/dx x = 1
            - This means "the rate of change of x with respect to x is 1" (for every 1 unit x increases, the function increases by 1)
            - Now multiply by a constant (when we have πx instead of just x, for every 1 unit x increases, the function increases by π * 1)
            - Therefore d/dx πx = π
            - Using the constant multiple rule: d/dx(c f(x)) = c d/dx(f(x))
            - Another example: d/dx 5x = 5
            - Analogy: Imagine x represents time in hours, and πx represents distance traveled by a car moving at constant speed π meters per hour. The derivative (rate of change) is just the speed: π meters per hour

    - So now we have a general derivative formula: the derivative of d(sin(πx)) which is cos(πx) π dx
        - This formula tells us the rate of change at any point x along the curve
            - Analogy: Speed(t) = 3t² m/s - gives the speed at any time t
        - But we have a specific question: What is the rate of change specifically at x=1?
            - Analogy: How fast were we going at t=5 seconds? Speed(5) = 3(5²) = 75 m/s
        - So we substitute x=1 into our general derivative formula to get the specific rate of change at that location:
            - cos(πx) π dx
            - cos(π * 1) π dx

    - The amount that this sin(πx) graph changes is approximately proportional to dx, with a proportionality constant equal to the derivative: π·cos(π·1) = -π. So the change is approximately -π·dx. (The approximation becomes exact as dx→0, which is why derivatives give us "instantaneous" rates of change)
        - Reminder: The derivative is the rate that converts input changes into output changes 
            - For any function f(x): df ≈ f'(x) × dx
            - Or: dy ≈ (derivative / rate) × dx 
            - Analogy: If we are driving at 60 km/h (our "derivative"/ RATE):
                - Drive for dx = 0.1 hours
                - Distance traveled (dy) ≈ 60 × 0.1 = 6 km
            - The change in output (dy) is approximately proportional to the change in input (dx), and the proportionality constant IS the derivative
            - In our case: d(sin(πx)) ≈ cos(π·1)·π × dx
        - By trigonometry we know that cos(π) = -1
        - So our expression simplifies to -π dx

    - Now let's consider the second graph x²-1:
        - The value of this graph changes by d(x²-1)
        - The derivative is 2x, so the size of that nudge is approximately 2x·dx:
            - Reminder: Why is 2x the derivative of x²-1?
                - The derivative of a difference is the difference of the derivatives
                - The derivative of any constant is zero (a constant doesn't change as x changes; if we graph y = 1, it's a horizontal line with slope 0)
                - Think of x²-1 as a shifted parabola. The "-1" just moves the entire parabola down by 1 unit, but doesn't change its slope at any point. So the rate of change (derivative) is the same as x² alone: 2x
        - Now we plug in x=1 to the general derivative expression 2x dx, meaning the size of the output nudge is about 2(1) dx
    
    - Now let's consider the ratio between the two derivatives:
        - At x=1, the function sin(πx) has a derivative of -π, so its change is approximately -π·dx
        - At x=1, the function x²-1 has a derivative of 2, so its change is approximately 2·dx 
        - For the composite function sin(πx)/x²-1:
            - Numerator change: When x moves away from x=1 by dx:
                - sin(πx) changes by approximately the rate of -π dx
            - Denominator change: When x moves away from x=1 by dx:
                - x²-1 changes by approximately the rate of 2 dx
            - When both numerator and denominator change slightly, the fraction changes by approximately:
                - change in numerator / change in denominator
                - -π dx / 2 dx
            - Simplify by canceling out dx terms:
                - -π/2
                - this means the ratio is independent of how small we make dx
    
    - This tells us that near x=1, the fraction sin(πx)/x²-1 behaves like:
        - For every tiny change in the denominator (2 dx)
        - The numerator changes by (-π dx)
        - The ratio stabilizes at -π/2
        - As dx → 0, both numerator and denominator → 0 (that's why we had 0/0 originally), but their ratio approaches the constant -π/2
        - This is L'Hôpital's rule in action: The limit of f(x)/g(x) equals the limit of f'(x)/g'(x)
        - The limit at x=1 for the composite function sin(πx)/(x²-1) is -π/2
            - lim (x→1) sin(πx)/(x²-1) = -π/2
        - Direct substitution gives 0/0 (indeterminate)
        - Using L'Hôpital's rule, we take derivatives:
            - Derivative of numerator at x=1: -π
            - Derivative of denominator at x=1: 2
        - The ratio of derivatives: -π/2
        - This ratio tells us the actual height the function approaches as x gets closer and closer to 1
        - These approximations get more and more accurate for smaller and smaller choices of dx
        - So this ratio -π/2 actually tells us the precise limiting value as x approaches 1
        - This means that the limiting height on the original graph is exactly -π/2

    - What this means graphically:
        - Even though the function sin(πx)/x²-1 is undefined at x=1 (we can't plug in 1 directly because you get 0/0), if we approach x=1 from either side, the y-value approaches -π/2 ≈ -1.571
        - There's a "hole" in the graph at x=1, but if we could "fill it in" naturally, it would be at height -π/2

- Let's go through it again more generally:
    - Instead of these two specific functions that both equal 0 at x=1, think of any two functions f(x) and g(x) which are both 0 at some common value x=a
    - Why do both functions have to equal 0 at x=a? 
        - Because that's when we get the indeterminate form 0/0 that we need L'Hôpital's rule to resolve
        - If f(a) ≠ 0 or g(a) ≠ 0, we can just plug in directly
        - If f(a) = 5 and g(a) = 2, then f(a)/g(a) = 5/2
    - The only constraint is that these have to be functions where we are able to take the derivative of them at x=a, which basically means they each basically look like a line when we zoom in close enough to that value
    - Even though we can't compute f(a)/g(a) at this trouble point (because it will return 0/0), we can ask about this ratio for values of x really close to a, the limit as x approaches a:
        - lim x -> a, f(x)/g(x) = ?
    - It's helpful to think of those nearby inputs as just a tiny nudge dx away from a
    - The value of f at that nudged point is approximately the derivative of f, evaluated at a * dx
        - df/dx a dx
    - The value of f at that nudged point is approximately its derivative at a, times dx. Since f starts at zero when x=a, the value of f at the nudged point is approximately just:
        - (derivative of f at a) * dx, or f'(a)·dx
    - Likewise, the value of g at that nudged point is approximately its derivative at a, times dx:
        - (derivative of g at a) × dx, or g'(a)·dx
    - Near that trouble point, the ratio between the outputs of f and g is approximately f'(a)·dx / g'(a)·dx
    - The dx's cancel out, so the ratio of f and g near a is about the same as the ratio between their derivatives:
        - f'(a) / g'(a)
    - Therefore: lim(x→a) f(x)/g(x) = f'(a)/g'(a)
        - This is because near x=a, functions behave linearly (like straight lines when zoomed in)
        - Since both functions START at 0, their values near a are entirely determined by how fast they are changing (their derivatives)
        - Analogy: Two cars start at the same point (position = 0). After a tiny time dx:
            - Car f travels: (speed of f) × time dx
            - Car g travels: (speed of g) × time dx
            - Ratio of distances = ratio of speeds
    - The dx's cancel out, so the ratio of f and g near a is about the same as the ratio between their derivatives
        - lim x -> a, f(x)/g(x) = (df/dx a) / (dg/dx a)
    - Because each of those approximations get more and more accurate for smaller and smaller nudges, this ratio of derivatives gives the precise value for the limit
    - Let's say the true value is f(a+dx) and our approximation is f'(a)×dx
        - For dx = 0.1:
            - The function has curved noticeably over this interval
            - Our linear approximation has some error
            - Maybe f(a+0.1) = 0.52 but we predicted 0.50
        - For dx = 0.000001:
            - The curve looks essentially straight
            - Our approximation is nearly perfect
            - f(a+0.000001) ≈ 0.00000500000... matches our prediction extremely closely
        - As dx → 0:
            - The approximation becomes exact
            - The ratio f'(a)/g'(a) becomes the precise limit
        - Visual analogy:
            - Zoom out on a circle → looks curved
            - Zoom in closer → looks flatter
            - Zoom in extremely close → indistinguishable from a straight line
    - This is a really handy trick for computing a lot of limits
    - L'Hôpital's Rule (Formal Statement):
        - When lim(x→a) f(x) = 0 and lim(x→a) g(x) = 0 (giving us 0/0), and both derivatives exist at a with g'(a) ≠ 0, then:
            - lim(x→a) f(x)/g(x) = f'(a)/g'(a)
        - The rule also works for ∞/∞ forms and can be applied multiple times if needed
    - Whenever we come across some expression that seems to equal 0/0 when we plug in some particular input, we can just take the derivative of the top and bottom expressions and plugging in that same trouble input
        - lim x -> 0, sin(x)/x = cos(0)/1 = 1
    - This clever trick is called L'Hôpital's rule (which was actually discovered by Johann Bernoulli)

- A tempting but invalid use of L'Hôpital's rule:
    - Say we are trying to discover what the derivative of sin(x) is, without knowing the answer yet
    - We use the definition of the derivative and substitute in sin(x)
        - f'(x) = lim (h→0) [f(x+h) - f(x)] / h
        - d(sin)/dx = lim (h→0) [sin(x+h) - sin(x)] / h
    - We notice that when h→0, this becomes 0/0 and decide to use L'Hôpital's rule
    - L'Hôpital's rule says: When you have 0/0, take the derivative of the top and bottom
    - But we don't know the derivative of the denominator, in fact this is what we are trying to figure out
    - So we already need to know the derivatives we need
    - L'Hôpital's rule is great for evaluating limits, but we can't use it to discover fundamental derivatives like d(sin)/dx, d(cos)/dx, d(e^x)/dx, etc. Those require other creative methods

- Summary for the L'Hôpital's rule:
    - If we are trying to find the limit of sin(πx)/(x²-1) as x→1, using L'Hôpital's rule, we:
        - Take derivatives of numerator and denominator separately
        - Evaluate those derivatives at x=1 (the point you're approaching)
        - Take the ratio of those values
        - This ratio equals the limit at that point


    

    