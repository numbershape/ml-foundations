# Probability

## Resources
- StatQuest with Josh Starmer: selected videos
- Claude Sonnet 4.5: Supporting tools for investigation, additional notes and final summary

---

## Notes

### Video 1: The Main Ideas behind Probability Distributions

**Key Concepts:**

- What is a statistical distribution?
    - Imagine we measured the height of several people, and distributed the results into four buckets: shorter than 5'; between 5' and 5.5'; between 5.5' and 6'; and taller than 6'. This is called a histogram
    - We see that most of the measurements come from people between 5' and 6'. The histogram is taller in the middle buckets. So if we picked one measurement at random, there's a good change it would be between 5' and 6'. The histogram is showing the likelihood of a random pick, belonging to a bucket
    - What if we used smaller bin sizes for our measurements? For example, smaller than 4.5'; between 5' and 5.25'; and so on
    - Now we can be more precise and say "half the people are between 5.25' and 5.75'
    - By measuring more people and using smaller bins we get a more accurate and more precise estimate of how heights are distributed

- We can use a curve to approximate the histogram
    - The curve tells us the same thing as the histogram: there is a low probability that we will measure someone shorter than 5' tall, or someone taller than 6' tall; and there is a high probability we'll measure someone between 5' and 6' tall
    - The curve has a few advantages over the histogram
        - It shows the approximate values of empty buckets: 
            - If we haven't measured someone between 5.75' and 6', this doesn't mean that we have 0 probability of encountering someone with that height 
            - The curve connecting the buckets will show the approximate likelihood for this bin
        - The curve is not limited by the width of the bins:
            - If we wanted to know the probability of measuring someone between 5.021 and 5.317, we could use calculus to calculate it, without having to round to the nearest bin size
        - If we don't have enough time or money to get many measurements:
            - The approximate curve based on the mean and standard deviation of the data that we were able to collect, is usually good enough

- Both the histogram and the curve are distributions: 
    - They show us how the probabilities of measurements are distributed
    - The tallest part of the histogram or curve, shows the region where measurements are most likely
    - The low parts shows the measurements that are less likely
    - There are all kinds of distributions with all kinds of interesting shapes

### Video 2: Sampling from a Distribution, Clearly Explained!!!

**Key Concepts:**

- Say we have a histogram of height measurements. Each dot represents a different person that we measured
    - The tallest part of the histogram shows the region where measurements are most likely; the low parts shows the measurements that are less likely
    - As we have seen, we can approximate the histogram with a smooth curve

- What does it mean to take a sample from a distribution?
    - We use a computer to pick a random number based on the probabilities described by the histogram or the curve
    - For example, if we wanted to take 1 sample from this distribution, there is a good chance the computer will pick a value near the middle, where the histogram and curve are tallest
    - However, every now and then, the computer will return a value from the edges, where the histogram and curve are the shortest
    
- Why take a sample from a distribution?
    - To explore statistics: the computer can generate lots of samples and we can plug them into statistical tests to see what happens
    - Since we know what the original distribution is, we can compare our expectations of what will happen, to reality
    - For example, we could take two samples where N=3 from a single distribution and do t-tests on the samples
    - In this case, N equals the number of measurements we take within each sample
    - Since the distribution is the same, the t-test should give me a large p-value
    - Doing lots of tests will give us a sense of how frequently the t-test successfully gives us a large p-value
    - If we had two separate distributions, a t-test is supposed to give us a small p-value
    - If we took lots of samples, we could do lots of t-tests and see how frequently the t-test worked and gave us a small p-value; this would tell us if we needed to increase our sample size or not
    - Taking samples from a distribution, or multiple distributions, ie getting a computer to generate a bunch of random numbers that reflect the probabilities of a distribition, lets us determine what a statistical test is capable of doing without doing too much work

### Video 3: Expected Values, Main Ideas!!!

**Key Concepts:**

- Imagine we are in StatLand and we want to know the likelihood of the next person we meet, having heard of the movie Troll 2:
    - Say we have recently asked everyone in StatLand if they heard of that movie; 37 people responded that they did and 176 responded that they didn't
    - Given that there isn't anyone who has both heard of the movie and hasn't heard of the movie at the same time, each person in StatLand is in either the first group or the second
    - That means that there are 37 + 176 = 213 people living in StatLand
    - Looking at the raw numbers tells us that StatLand is pretty small, and that whatever analysis we do only applies to a handful of people
    - By looking at the numbers we can get a general sense of the trends in StatLand; we see that most of the people have never heard of Troll 2
    - But at a glance, it's not obvious how the number of people who have never heard of it relates to the total population
    - We can make this relationship obvious by calculating probabilities

- Let's calculate the probabilities of people in StatLand that have and haven't heard of Troll 2:
    - If we want to know the probability that a randomly selected person in StatLand has heard of Troll 2, we simply divide the number of people that have heard of it (37) by the total (213):
        - num. heard of Troll 2 / total = 37 / 213 = 0.17
    - That means that the probability that a randomly selected person in StatLand has heard of Troll 2 is 0.17, which is relatively low
        - Probability: 0.17
    - Likewise, the probability that a randomly selected person in StatLand has never heard of Troll 2 is 0.83, which is relatively high:
        - 176 / 213 = 0.83

- A bet:
    - Our friend StatSquatch is willing to bet 1 USD that the next person we meet has heard of the movie
    - We can use these probabilities to decide if we should agree to the bet
    - If the next person we meet has heard of Troll 2, we lose the bet, which means we lose 1 USD; otherwise we win one 1 USD
    - So let's make a table and put -1 to represent the outcome of losing 1 USD, and +1 to represent the outcome of winning 1 USD:
        - Heard of Troll 2: Probability 0.17, Outcome -1
        - Never heard of Troll 2: Probability 0.83, Outcome +1
    - The probability we will loose 1 USD is 0.17, and the probability we will win is 0.83; so the probability that we will win is much higher than the probability that we will lose
    - That makes it seem like it would be a good idea to accept the bet
    - However, there is still a low probability that we will lose! 
    - To avoid losing, we ask "Can we make this bet 100 times?"
    
- Now if we make this bet 100 times, we will probably win some and lose some, and we can use the table to predict how much we will win and lose:
    - Losing:
        - We can approximate how many times we will lose by multiplying the probability that we will lose (0.17) by 100:
            - 0.17 * 100 = 17
        - That means we expect to lose about 17 times in 100 bets
        - Since we will lose 1 USD each time we lose the bet, we can estimate the total amount of money we will lose by multiplying the number of times we expect to lose by -1:
            - 0.17 * 100 * -1 = -17
        - This represents how much money we expect to lose in 100 bets: 17 USD
    - Winning:
        - We can approximate how many times we will win by multiplying the probability that we will win (0.83) by 100:
            - 0.83 * 100 = 83
        - That means we expect to win about 83 times in 100 bets
        - Since we will win 1 USD each time we win the bet, we can estimate the total amount of money we will win by multiplying the number of times we expect to win by 1:
            - 0.83 * 100 * 1 = 83
        - This represents how much money we expect to win in 100 bets: 83 USD
    - Now that we have a term for the expected amount of money lost and a term for the expected amount of money won, we can add the two terms together to find out the total net of how much we expect to win or lose:
        - (0.17 * 100 * -1) + (0.83 * 100 * 1) = -17 + 83 = 83 - 17 = 66
    - We see that we expect to gain approximately 66 USD after 100 bets
    - We can also calculate the average amount of money we will gain PER BET, by dividing everything by the number of bets (100):
        - [(0.17 * 100 * -1) + (0.83 * 100 * 1)] / 100 = 66 / 100 = 0.66
    - So on average, we expect to gain 66 cents every time we bet
    - Even though realistically we either win or lose 1 USD each time we bet, ON AVERAGE we expect to gain 66 cents each time

- In statistics lingo: 
    - 66 cents is the "Expected Value" for the bet
    - E(Bet) = [(0.17 * 100 * -1) + (0.83 * 100 * 1)] / 100 = 0.66
    - E(X) = [(0.17 * 100 * -1) + (0.83 * 100 * 1)] / 100 = 0.66, where X represents the bet
    - Since we are multiplying each probability by the number of bets (100), and dividing by the number of bets (100), then all of the values that represent the number of bets cancel out:
        - (0.17 * -1) + (0.83 * 1)
    - So we are left with: the probability that someone in StatLand has heard of Troll 2 times the outcome (-1), plus the probability that someone has not heard of Troll 2 times the outcome (1)
    - When we do the math, we get the exact same result as before:
        - E(X) = (0.17 * -1) + (0.83 * 1) = 0.66
    - This Expected Value represents what we would expect on average per bet if we made this bet a bunch of times

- Sigma notation:
    - Using sigma notation, the Expected Value of E(x) is the sum of each specific outcome x, times the probability of observing each outcome x:
        - E(X) = Σ x P(X = x)
            - Σ: sum of
            - x: specific outcome
            - P(X = x): the probability of observing that specific outcome
        - E(X) = (0.17 * -1) + (0.83 * 1) = 0.66 = Σ x P(X = x)
    - So for the first term, Heard of Troll 2, the outcome is -1, and the probability of observing that specific outcome is 0.17
    - So we multiply those values together (-1 * 0.17)
    - Then the Sigma tells us to add that term, to the term for Not heard of Troll 2
    - For that the outcome is 1, and the probability of observing that outcome is 0.83
    - So either way we do the math, we get 0.66
    - That means that if we can make this bet a bunch of times, even though we will lose some of the time, we should make money in the long run

- A different bet:
    - Because it is relatively rare for someone in StatLand to have heard of Troll 2, StatSquatch is now willing to pay you 10 USD if the next person has heard of Troll 2, but if they have not, we will still pay him 1 USD
    - Will we win money or lose money if we make this bet a bunch of times?
    - Let's calculate the Expected Value to find out!
    - The outcome for when someone has Heard of Troll 2 is 10, because we will gain 10 USD; and the outcome for when someone has Not heard of Troll 2 is -1 because we will lose 1 USD
    - The Expected Value is the sum (Σ) of: each outcome (x) times the probability of observing that outcome (P(X = x))
        - E(X) = Σ x P(X = x)
        - E(X) = Σ x P(X = x) = (10 * 0.17) + (-1 * 0.83) = 1.7 - 0.83 = 0.87
    - The Expected Value is 0.87
    - That means that we expect to gain on average, 87 cents every time we make this bet, which is even better than before

- In this lesson we only talked about how to calculate Expected Values for discrete events, like whether or not someone has heard of Troll 2
- However, we will next see how to calculate Expected Values for continuous events, like how much time passes between text messages on our phone
- In the future, we will also see why we divide the sample variance by n-1, and why dividing by n underestimates the variance

### Video 4: Expected Values for Continious Variables!!!

**Key Concepts:**

- When we calculate the Expected Value for a bet like the one we saw, we are calculating the Expected Value for a Discrete Variable
- In this case, the Discrete Variable is the bet, and it has two outcomes: lose 1 USD or gain 1 USD
- In general, any time we have discrete outcomes, we have a Discrete Variable
- What about Expected Values for Continuous Variables?

- Continuous Variables come from measuring things with continuous outcomes
    - Imagine we walk with StatSquatch around StatLand, and he says "I wonder how long we would have to wait, per person, to see people"
    - StatSquatch wants to know the Expected Value for waiting time
        - After 10 seconds, we meet one person
        - We keep track of that by putting a dot on a numberline at 10
        - The next person we meet shows up after 30 seconds
        - The next person shows up immediately
        - The next person shows up in 10 seconds, etc
    - A histogram appears, higher in the beginning due to more data points, and lower as it continues; but there are gaps in the data, which usually means we still have more data to collect
    - Also, the data is plotted using 10 second intervals; what if we wanted different interval sizes, like 5 or 2.5 seconds?
    - Instead of collecting more data and/or worrying about interval size, we can model the waiting times with an Exponential Distribution

- The Exponential Distribution:
    - This is a curve that touches the top of the data points 
    - The unit on the x-axis is Time (seconds), while the y-axis is Likelihood
    - The equation for the Exponential Distribution is:
        - $f(X = x) = \lambda e^{-\lambda x}$ when $x \geq 0$, otherwise $0$
    - λ is the Rate, a parameter that defines the shape of the curve
    - In this example, the Rate refers to the number of people we meet per second, because that is the unit on the x-axis
    - And if we set λ to 0.05, we get a curve that fits the data we have already collected (starts high up and lowers as it goes, until almost touching the x-axis)
        - $f(X = x, λ = 0.05) = \lambda e^{-\lambda x}$ when $x \geq 0$, otherwise $0$
    - However, if we set λ to 0.1, meaning we meet more people per second, then we get a curve that has a steeper slope close to 0
    - And if we set λ to 0.01, meaning we met fewer people per second, then we get a curve that barely bends, but ends up higher on the right side compared to the other curves (looks like a straight horizontal line slightly higher on the left)

- Calculating probabilities from the curve:
    - If we want to calculate the probability that we meet someone in 10 seconds or less, we calculate the area under the curve between 0 and 10
    - In other words, we integrate the Exponential Distribution from 0 to 10
        - $\int_0^{10} f(X = x, \lambda = 0.05) = \int_0^{10} \lambda e^{-\lambda x}$
        - This integral equals 0.39
    - This means that the probability we will meet someone in 10 seconds or less is 0.39
    - Alternatively, if we wanted to know the probability of meeting someone between 25.302 seconds and 30.122 seconds, then we can calculate the area under the curve between 25.302 and 30.122
    - In this case, the area under the curve is 0.06, which means that the probability we will meet someone in this range of time is 0.06
    - In summary, the Exponential Distribution fits the data that we have collected so far, but it doesn't have any gaps or missing values, and we can use it to make calculations on any interval we want

- Notes:
    - We call the y-axis "Likelihood" because the y-axis coordinates generated by this equation: $\lambda e^{-\lambda x}$, are the Likelihood values that we use for Maximum Likelihood estimation, which we will see in a next lesson
    - The y-axis is scaled so that the total area under the curve equals 1
    - In theory, this curve should go all the way to positive infinity on the x-axis, but we stop drawing at 90 seconds, because at that time the curve is pretty close to 0 on the y-axis

- How to calculate the Expected Value for the Continuous Distribution:
    - Let's pretend this is a Discrete Distribution and let each 10 second interval represent an Outcome
    - Let's draw the curve to go through the midpoint of each sample top side
    - Since the interval is 10 seconds long, the curve intersects the first rectangle at 5 seconds, the second one at 15 seconds, etc
    - Now instead of having to integrate the function to get the area under the curve, we can approximate the area under the curve for each Outcome with the corresponding area of each rectangle
    - For example, the probability of meeting someone in the first 10 seconds is approximately the width of the first rectangle (10) times its height
    - To calculate the height, we need to find the y-axis coordinate for where the top edge of the rectangle intersects the curve
    - This means we need to find the y-axis coordinate for this exponential distribution when time=5
    - So we plug x = 5 into the equation:
        - $f(X = 5, λ = 0.05) = \lambda e^{-\lambda x}$ when $x \geq 0$, otherwise $0$ 
        - $= 0.05e^{-0.05 \times 5}$ 
        - $= 0.04$
    - So the height of the rectangle is 0.04
    - And the area of the rectangle is the height * the width:
        - 0.04 * 10 = 0.4
    - That means the probability of meeting someone in the first 10 seconds is approximately 0.4
    - Compared to the exact probability calculated with the integral (0.39) the approximation is quite close
    - Likewise, we use the Exponential Distribution to calculate the height for each rectangle and the probabilities for each Outcome (0.4, 0.2, 0.1, 0.09, 0.05, 0.02, 0.01, 0.01)
    - Now, if we want to approximate the Expected Value of the exponential distribution, we can plug the outcomes and their approximated probabilities into the equation for Discrete Outcomes:
        - E(X) = Σ x P(X = x)
    - For example, the first Outcome is meeting people in 10 seconds or less, and the probability is 0.4, so the first term is 10 * 0.4:
        - E(X) = Σ x P(X = x) = (10 * 0.4)
    - The second Outcome is the 10 second interval that ends at 20 seconds, and the associated probability is 0.2, so the second term is 20 * 0.2:
        - E(X) = Σ x P(X = x) = (10 * 0.4) + (20 * 0.2)
    - Likewise, we add the remaining terms, and when we do the math, we get 22:
        - E(X) = Σ x P(X = x) = (10 * 0.4) + (20 * 0.2) + ... = 22
    - That suggests that, on average, we expect to wait 22 seconds between each time we meet someone
    - Now, if we want to improve our approximation, we can cut the intervals in half, so that each one lasts 5 seconds instead of 10
    - And when we do the math, plugging in each Outcome and its corresponding probability, we get 21.8:
        - E(X) = Σ x P(X = x) = (5 * 0.22) + (10 * 0.17) + ... = 21.8
    - To improve the estimate of the Expected Value even more, we can keep decreasing the width of each rectangle, until the width goes to 0 and the number of rectangles goes to infinity
    - When we have an infinite number of rectangles with 0 width, then we are no longer approximating the area under the curve, but calculating it exactly
    - Remember that the probability of observing a specific Outcome is the height * width of the associated rectangle:
        - Σ x (height * width)
    - And that the height, the y-axis coordinate of the top of each rectangle, is the Likelihood at that point
    - And the width can be written as Δx
        - lim Σ x (L(X = x) * Δx)
    - If the sum of the number of rectangles goes to infinity and the width goes to 0, then we end up with an integral:
        - ∫ x L(X = x) dx

- To summarize:
    - When we have a Discrete Distribution, the Expected Value E of the corresponding Discrete Variable X, is the sum of the Outcomes * their associated probabilities:
        - E(X) = Σ x P(X = x)
    - When we have a Continuous Distribution, then the Expected Value E of the corresponding Continuous Variable X, uses an integral instead of a sum, and the rest of the equations are very similar, except we replace the Probability P with the Likelihood L (the y-axis coordinate):
        - E(X) = ∫ x L(X = x) dx
    - Although we have been using the exponential distribution, this formula works for any Continuous Variable

- Now that we have a formula, let's calculate the Expected Value for a Continuous Variable from the exponential distribution:
    - Since we use the exponential distribution equation to calculate the Likelihoods:
        - $f(X = x) = \lambda e^{-\lambda x}$ when $x \geq 0$, otherwise $0$
    - Let's plug it into the equation for the Expected Value:
        - E(X) = ∫ x L(X = x) dx
        - E(X) = ∫ x L $\lambda e^{-\lambda x}$ dx
    - And because the exponential distribution is defined for all values >=0, we will integrate everything from 0 to infinity
        - $E(X) = \int_0^{\infty} x \lambda e^{-\lambda x} dx$
    - Because we can split it into two functions  (x) and ($\lambda e^{-\lambda x}$), we can use Integration by Parts to find the solution:
        - $$\int_0^{\infty} f(x)g'(x) dx = f(x)g(x) \bigg|_0^{\infty} - \int_0^{\infty} f'(x)g(x) dx$$
    - Doing the calculation, we get E(X) = 1/λ
    - Given the specific Exponential Distribution, where λ (lambda) = 0.05:
        - 1/0.05 = 20
    - So we expect to wait on average 20 seconds between meeting people

### Video 5: The Normal Distribution, Clearly Explained!!!

**Note:**

***From this video onward, I will only be writing concise summaries of key concepts due to time limitations***

**Key Concepts:**

- The width of the Normal Distribution curve is defined by the "standard deviation"
- Knowing the standard deviation is helpful because normal curves are drawn such that 95% of the measurements fall between +/- 2 standard deviations around the mean:
    - If the width is 0.6, 95% of measurements fall between +/- 1.2 the central point
    - If the width is 4, 95% of measurements fall between +/- 8 the central point
- To draw a normal distribution, we need:
    - The average measurement (central point)
    - The standard deviation (width of the curve; this also determines the height of the curve in an inverse relationship)

### Video 6: Standard Deviation vs Standard Error, Clearly Explained!!!

**Key Concepts:**

- The standard deviation of the mean of all the means of several samples, is called the Standard Error
- The standard deviation quantifies the variation within a set of measurements
- The standard error quantifies the variation in the means from multiple sets of measurements
- However, the standard error can be estimated from a single set of measurements, even though it describes the means from multiple sets

### Video 7: Population and Estimated Parameters, Clearly Explained!!!

**Key Concepts:**

- A population represents every piece of the data group we are measuring
- The parameters that determine how a distribution fits the population data are called population parameters
    - The normal curve has the mean and standard deviation as population parameters
    - For an exponential distribution, its shape is determined by the eate, and that would be the population rate
    - The shape of a Gamma distribution is determined by two parameters, Shape and Rate, so these are its population parameters
- We rarely have all the population data, so we always estimate the population parameters
- We also calculate how much confidence we should have in those population estimates
- Specifically, we calculate p-values and confidence intervals to quantify the confidence in the estimated parameters
- The more data we have, the more confidence we have
- By estimating population parameters and quantifying our confidence, we can generate reproducible results

### Video 8: Calculating the Mean, Variance and Standard Deviation, Clearly Explained!!!

**Key Concepts:**

- Population mean = sum of measurements / total number of measurements
- Statistitians often use the symbol x̄ (x-bar) to refer to the estimated mean, also called the sample mean, and the symbol μ (mu) to refer to the true population mean
- The formula we use to calculate (not estimate) the Population Variance is :
    - ${\frac{\sum (x - \mu)^2}{n}}$
    - x - μ: each measurement - population mean
    - n: all measurements
- Squaring each term ensure that each difference is positive, otherwise the measurements on the left side of the mean would give negative differences, which would cancel out the positive differences from the measurements on the right side of the mean
- But because each term is squared, the units for the results are the original units squared.
- To compensate, we take the square root of the entire expression, and that gives us the Population Standard Deviation:
    - $\sqrt{\frac{\sum (x - \mu)^2}{n}}$

- Usually, we don't have all the data. So instead of calculating, we estimate. Estimated Population Variance:
    - ${\frac{\sum (x - \bar{x})^2}{n-1}}$
- Dividing by n-1 compensates for the fact that we are calculating differences from the sample mean instead of the population mean, otherwise we would consistently underestimate the variance around the population mean
- This is because the differences between the data and the sample mean tend to be smaller than the differences between the data and the population mean, resulting in a larger average:
    - ${\frac{\sum (x - \bar{x})^2}{n}}$ < ${\frac{\sum (x - \mu)^2}{n}}$
- And for the Estimated Population Standard Deviation:
    - ${\sqrt\frac{\sum (x - \bar{x})^2}{n-1}}$

### Video 9: The Central Limit Theorem, Clearly Explained!!!

**Key Concepts:**

- When we do an experiment, we don't always know what distribution our data comes from
- But it turns out that it doesn't matter, because if we take several samples from any kind of distribution, the means of those samples form a normal distribution (no matter what the original distribution was)
    - If we collect 20 measurements and calculate the mean, and then do that a bunch of times (collect 20 measurements and calculate a mean), a histogram of those means will be a normal distribution
    - This suggests that an individual mean, calculated from 20 measurements, is, in and of itself, normally distributed
    - For example, if we had a uniform distribution and we collected 20 values from it and calculated the mean, then that mean would be normally distributed 
    - We know this because if we repeated the process (collected another 20 values, calculated the mean, and then did that a bunch of times) the histogram of all the means we calculated would be a normal distribution
- We can use the mean's normal distribution to make confidence intervals, t-tests (where we ask if there is a difference between the means from two samples), ANOVA (where we ask if there is a difference among the means from three or more samples), and pretty much any statistical test that uses the sample mean
- For the Central Limit Theorem to work, as a rule of thumb, the sample size must be at least thirty
- Additionally, we have to be able to calculate a mean from our sample (for example, the Cauchy distribution doesn't have a sample mean, but this is very rare)

### Video 10: The Binomial Distribution and Test, Clearly Explained!!!

**Key Concepts:**

- If 4 people say they like Orange Fanta and 3 people say they like Grape Fanta, is this enough to be confident that "most people like Orange Fanta"?
    - We need to find out what to expect when there is no preference between two choices
    - We use the binomial formula to find out what to expect when there is no preference: $$pr(x | n, p) = \left(\frac{n!}{x!(n-x)!}\right) p^x (1-p)^{n-x}$$
    - If our results fit those expectations, then both Fantas are loved equally
    - If they don't, then we can reject the idea of no preference (that both Fantas are loved equally)

- Let's assume we asked 3 people if they liked Orange Fanta more than Grape Fanta: The first two people said they preferred Orange, and the third person said they prefer Grape
- We assume that if no preference, then there is a 50% chance to pick Orange and 50% to pick Grape
- We can then calculate the probability of the first two people randomly choosing Orange and the third randomly choosing Grape:
    - The probability of the first person preferring Orange is 0.5
    - The probability of the first two people preferring Orange is 0.5 * 0.5 = 0.25
    - The probability of the first two people preferring Orange and the third person preferring Grape is 0.5 * 0.5 * 0.5 = 0.125
- BUT this is not the probability that ANY 2 out of 3 people would prefer Orange:
    - If the order of preferences was different, we would multiply the same numbers together in a different order
    - So all 3 combinations (G-O-O, O-G-O, O-O-G) are equally likely
- This means that the probability that ANY 2 out of 3 people preferring Orange, is the sum of the 3 possible orders:
    - 0.125 + 0.125 + 0.125 = 0.375

- Alternatively, we could have done the math using the formula: $$pr(x | n, p) = \left(\frac{n!}{x!(n-x)!}\right) p^x (1-p)^{n-x}$$
    - First part of formula (before the = sign):
        - x is the number of people who preferred Orange (in this case, x = 2)
        - n is the total number of people we asked (n = 3)
        - note: so n - x is the people who said they prefer Grape
        - p is the probability that someone will pick Orange (p = 0.5)
        - note: so 1 - p is the probability that someone prefers Grape
        - Together this says "The probability of x (the number of people who prefer Orange), given n (the number of people asked) and p (the probability of picking Orange)..."
    - Second part of formula (factorials):
        - The factorials in the formula, are due to the number of different ways 2 of 3 people could say they prefer Orange
        - When done manually, we saw that there are 3 ways for 2/3 people to say they prefer Orange
        - So if we plug in n = 3 and x = 2 into the factorials inside the parenthesis, we get 3, representing the 3 ways
    - Third part of formula, p^x:
        - This corresponds to the probability that Orange was chosen 2 of the 3 times (0.5 * 0.5 = 0.5²)
    - Fourth part of the formula:
        - It corresponds to the probability someone prefers Grape (remember that 1 - p is the probability that someone prefers Grape, and n - x is the people who said they prefer Grape)
        - If we plug in n = 3, x = 2, p = 0.5, we get 0.5, corresponding to the one person who liked Grape
    - So the third and the fourth part of the equation correspond to: 
        - 0.5 * 0.5 * 0.5
    - And the second part (factorials) multiplies that by 3
    - Eventually the formula gets us:
        - pr(x = 2|n = 3, p = 0.5) = 3 * 0.5 * 0.5 * 0.5 = 0.375

- So the binomial distribution tells us that the probability that 2 of 3 people will prefer Orange due to random chance is 0.375
- Going back to our original question: If 4 people say they like Orange Fanta and 3 people say they like Grape Fanta, can we conclude that "most people like Orange Fanta"?
    - We plug in x = 4 (the number of people that preferred Orange), n = 7 (the number of people we asked), and p = 0.5 (the probability that someone would randomly pick Orange)
    - With the formula, we get 0.273, which is the probability that 4 of 7 people would randomly prefer Orange

- When we use a binomial distribution to calculate a p-value, it's called a Binomial Test
    - The p-value is the probability of the observed data (4 of 7 people prefering Orange), plus the probabilities of all other possibilities that are equally likely or rarer
    - So in our case of 4 Orange and 3 Grape, we need to calculate its reverse (3 Orange and 4 Grape), as well as 5-2, 6-1, and 7-0 (and their reverse) combinations
    - When including the reverse combinations, we are calculating a "two-sided p-value"
    - When adding up all the probabilities, we get 0.5 (Orange is preferred) plus 0.5 for the reverse (Grape is preferred)
    - The sum of the probabilities of all combinations of events with an equal or rarer probability is 0.5 + 0.5 = 1
    - So the p-value for 4 out of 7 people saying they prefer Orange is 1
    - This means that the model, the binomial distribution with p = 0.5 (meaning that both drinks are equally preferred) is a good fit for the observed data
    - Thus we conclude that given the sample size, 7, we cannot rule out the possibility that both Orange and Grape are equally loved

- Note that the binomial distribution works only when the probability that someone likes Orange does not change if someone else already said they liked Orange (they are independent to each other)

### Video 11: p-values: What they are and how to interpret them

**Key Concepts:**

- How to tell if drug A is more effective than drug B, and be sure that it's not just by random chance?
    - Drug A: 73 cured; 125 not cured (37% cured)
    - Drug B: 59 cured; 131 not cured (31% cured)
    - How confident can we be that drug A is superior?

- p-values are numbers between 0 and 1 that quantify how confident we should be that Drug A is different from Drug B
- The closer a p-value is to 0, the more confidence we have that Drug A and Drug B are different
- In practice, a commonly used threshold is 0.05. It means that if there is no difference between Drug A and Drug B, and if we did this experiment a bunch of times, then only 5% of those experiments would result in the wrong decision

- Say that we gave the same Drug A to both groups; now any differences in the results are 100% attributable to weird random things:
    - Drug A, group 1: 73 cured; 125 not cured 
    - Drug A, group B: 71 cured; 127 not cured
    - In this case, the p-value would be p = 0.9 (this is calculated using Fisher's Exact Test; we will see that in a following chapter)
    - 0.9 is way larger than 0.05, meaning that we fail to see a difference between these two groups
- If we repeated this same experiment a lot of times, most of the time we would get similarly large p-values, with very few exceptions due to random chance, like:
    - Drug A, group 1: 60 cured; 138 not cured 
    - Drug A, group B: 84 cured; 114 not cured
    - In this case, p-value is p = 0.01, and we would say that the two groups are different (even though they both took the same drug)
    - Getting a small p-value when there is no difference is called a False Positive
- A 0.05 threshold for p-values means that 5% of the experiments (where the only differences come from weird random reasons) will generate a p-value smaller than 0.05
- In other words, if there is no difference between Drug A and Drug B, 5% of the times we do the experiment, we will get a p-value less than 0.05, aka a False Positive

- Going back to our original numbers:
    - Drug A: 73 cured; 125 not cured (37% cured)
    - Drug B: 59 cured; 131 not cured (31% cured)
- The p-value is 0.24. Which means we are not confident that Drug A is different from Drug B

- The idea of trying to determine if these drugs are the same or not is called Hypothesis Testing:
    - The Null Hypothesis is that the drugs are the same
    - The p-value helps us decide if we should reject the Null Hypothesis or not
    - Rejecting the Null Hypothesis means that the drugs are different

- While a small p-value helps us decide if Drug A is different from Drug B, it does not tell us HOW different they are:
    - We can have a small p-value regardless of the size of difference between Drug A and Drug B; the difference can be tiny or huge
    - For example, our above experiment gave us a relatively large p-value, 0.24, even though there is a 6 point difference between Drug A and Drug B (37% vs 31% cured)
    - In contrast, the below experiment, which involves a lot more people, gives us a p = 0.04, even though there is only a 1 point difference between Drug A and Drug B:
        - Drug A: 5005 cured; 9868 not cured (34% cured)
        - Drug B: 4800 cured; 9000 not cured (35% cured)
    - So a small p-value does not imply that the effect size (or difference between Drug A and Drug B) is large

### Video 12: One or Two Tailed P-Values

**Key Concepts:**

-
    


