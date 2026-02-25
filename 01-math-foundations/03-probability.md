# Probability

## Resources
- StatQuest with Josh Starmer: Statistics & Probability videos

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

**Key Concepts:**

- The width of the Normal Distribution curve is defined by the "standard deviation"
- Knowing the standard deviation is helpful because normal curves are drawn such that 95% of the measurements fall between +/- 2 standard deviations ("2 widths") around the mean:
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

- If one-tailed test gives a p-value of 0.03, and two-tailed test gives a p-value of 0.06, which p-value should we use?
    - The one-tailed p-value tests the hypothesis that our treatment is "better" than the standard treatment (but it doesn't distinguish between "worse" and "not significantly different")
    - The two-tailed p-value tests whether the new treatment is "better", "worse", or "not significantly different"
    - Since we would want to know if our new treatment was worse than the standard treatment, we should use the two-tailed p-value

- But doesn't the data suggest that we don't need to test the new drug for being "worse", since it's skewed towards it being "better" anyway?
    - No. Good statistical practice means we need to decide what test and what p-value we want to use BEFORE we do the experiment, otherwise we are "p-hacking", which increases the probability of reporting invalid results

- Imagine taking 2 samples of 3 data points each, from a normal distribution
    - In most cases, a two-tailed t-test on these two samples should give a p-value > 0.05, because the 2 samples will overlap most of the time (in the center, where probabilities are higher - meaning that we cannot be confident the 2 samples are different)
    - Every now and then, the samples will not overlap, and the t-test will give a p-value < 0.05 (because the samples are different)
    - This happens 5% of the time and is called a "false positive"
    - Now imagine taking 10,000 two-tailed t-tests like this
    - 5% of 10,000 = 500, so we expect 500 false positives
    
- What if we switched to a one-tailed test when things look good?
    - If sample 1 had two or more values that were LESS than all of values in sample 3, then we used a one-tailed t-test
    - The chance of reporting a false positive went from 5% to 8% (from 500 to 800 false positives)

- So when we have a choice, we should always go with a two-tailed p-value, as we always want to know both sides of the story


### Video 13: p-hacking and power calculations

**Key Concepts:**

- Say our p-value is 0.051 so totally borderline, and we have time to run one more replicate
    - On a normal distribution, most of the time we expect the values of two samples to be close to each other and to overlap
    - Rarely we get the opposite where the p-value is < 0.05, and in this case we conclude that the data were gathered from two separate distributions (for example, two different mouse strains, if we are talking about mice weights). This is how we get a false positive sometimes

- But let's focus on the samples that have p-values barely greater than 0.05
    - The goal is to have a test that works 95% of the time
    - For most of science, the cost/benefit ratio of being more stict does not make sense
    - If 53 out of 1000 p-values < 0.05, it means it's a 5.3% false positives, which means that the t-test performs as expected
    - But what about the next ~50 p-values that are barely over 0.05, like 0.051 and so on? They are so close to 0.05
    - It would be tempting to think "if I add one more replicate, maybe the p-value will get below 0.05"
    - So we add one more random value to datasets with p-values between 0.05 and 0.1
    - And now 30% of the new t-tests result in p-values < 0.05

- Why 30%? Understanding the mechanism:
    - We're running 1000 separate experiments, each with small sample sizes (n ≈ 5-20 per group)
    - About 50 experiments land in the borderline zone (p between 0.05-0.1)
    - For those 50, we add 1 sample to each group and recompute
    - Result: ~15 of those 50 cross the threshold (30%)
    - The key: with n=10 per group, adding 1 sample means old:new ratio = 20:2 = 90% old data
    - The original "lucky fluctuation" that produced p=0.051 still dominates the result
    - One new sample per group is enough to nudge a borderline case over the threshold, but not enough to dilute the existing pattern
    - This gives the 30% crossing rate (vs the 5% we would expect from a fresh experiment)
    - Overall false positive rate: 5% → 6.5% (50 + 15 out of 1000)
    - Conditional rate for p-hacked experiments: 30% (the rate that matters when we are the researcher with p=0.051)
    - Among experiments where we p-hacked (the 50 borderline ones):
        - 15 out of 50 became false positives
        - That's a 30% false positive rate for the p-hacked subset

 - So when totally bogus data gave a "close" p-value, adding more bogus data gave a "significant" p-value 30% of the time, which is a huge false positive rate
    - So we should not just add samples until we get a good p-value, because this increases our chances of reporting a false positivey
    - Instead we should do a Power Calculation before the experiment to determine how many samples we need to do

- A Power Calculation is a way to determine how many samples we need in advance of doing an experiment in order to correctly get a small p-value
    - Power = The probability a test will correctly give a small p-value
    - 4 things effect power:
        - The effect size (how "apart" the distributions are)
        - The variation in the data (how "thin" the distribution curve is). When variation is small, there is a high probability that our samples will also have low variations, and we will correctly get a small p-value
        - The sample size (a large sample size can compensate for a small effect size and high variation). If we are using a t-test (which compares means, which are estimated from the samples), it is more accurate when the sample is larger. Additionally, the variation determines how much power will increase when sample size is increased
        - The statistical test we use (some tests are more powerful than others)
    - How to do a Power Calculation:
        - Gather preliminary data or guesses
        - Estimate means
        - Calculate standard deviations
        - With means and standard deviations, estimate how the distributions will look like
        - If there is quite a bit of overlap, it means that the effect size is small, so we will need a larger sample size
        - The variation in the means of sample sizes, is called the Standard Error and it is easily calculated. If N = sample size:
            - Standard Error = Standard Deviation / √N
        - We need 2 of these 3 variables:
            - effect size
            - variation in data
            - sample size 
        -  For sample & effect size, if we don't have preliminary data, start by assuming 3 replicates, looking for a 2 fold difference; then we will see how much variation will still give good power, and increase sample size/effect size accordingly
        - Alternatively, if we have the known variation, plug in an effect size we want to detect and determine the sample size, or the other way around


### Video 14: p-hacking: What it is and how to avoid it!

**Key Concepts:**

- Doing a lot of tests and ending up with false positives is called the Multiple Testing Problem
- There are many ways to compensate for it, like the False Discovery Rate, with which we input the p-values for every single comparison, the math adjusts p-values that are usually larger than the original p-values, and some of the tests that were False Positives before, end up with adjusted p-values > 0.05
- A Power Analysis is performed before doing an experiment and tells us how many replicates we need in order to have a relatively high probability of correctly rejecting the null hypothesis (the hypothesis that there is no difference between the groups)


### Video 15: How to calculate p-values

**Key Concepts:**

- Imagine we flipped a coin twice and got Heads both times
    - At this point we may be tempted to think "My coin is special because it landed on Heads twice in a row". This is a "hypothesis"
    - However, in Statistics Lingo, the hypothesis is the opposite: "Even though I got 2 Heads in a row, my coin is no different from a normal coin"
    - This is the "Null Hypothesis", and a small p-value rejects it, and in that case, we know that our coin is special
    - So let's test this hypothesis by calculating a p-value

- p-values are determined by adding up probabilities. So let's start by figuring out the probability of getting 2 Heads in a row:
    - There is a 50% chance in each toss, that we will get Heads
    - Getting 2 Heads in a row can result in H-H, H-T, T-H, T-T
    - So 1 out of 4 possible outcomes equals 1/4 = 0.25
    - This is the number of times we got 2 Heads / The total number of outcomes

- A p-value is composed of 3 parts:
    - The probability random chance would result in the observation (0.25)
    - The probability of observing something else that is equally rare (0.25 for T-T)
    - The probability of observing something rarer or more extreme (0)
    - Add everything together: p-value = 0.5
    - Note that the probability (0.25) is different from the p-value (0.5)
    - So this does not reject Null hypothesis

- When we calculate probabilities and p-values for something continuous like Height, we usually use a statistical distribution
    - The area under the curve shows the probability of a value being within the values covered by the area
    - To calculate p-values with a distribution, we add up the percentages of area under the curve
    - "Is this measurement so far away from the mean of the assumed distribution, that we can reject the idea that it came from it?"
    - If so, that would suggest that another distribution might do a better job explaining the data
    - When working with a distribution, we are interested in adding equal to or more extreme values to the p-value (rather than rarer values)
    - A p-value of 0.03 rejects the hypothesis that "given the assumed distribution, it is normal to get those measurements", meaning that it's pretty special getting those measurements, which means that a different distribution makes more sense

- One sided p-value:
    - A two-sided p-value from a drug performance distribution for illness recovery times, would calculate both extremes giving a p-value of 0.03, which tells us that the drug did something unusual, and that some other distribution does a better job at explaining the data
    - For a one-sided value, we check only one side for recovery time (if recovering time is shorter). So only values from one side are counted as "more extreme" than our cutoff. p-value results in 0.016, showing the drug did something unusual, even more so than before.
    - But if the drug was not good and recovery time was longer than not taking it (15 days), a two-sided p-value would still be 0.03 but the one-sided p-value (if we are still checking the shorter recovery time side) would be 0.98, not detecting anything unusual, so missing the issue
    - The two-sided p-value detects both unusual cases (short and long recovery times)


### Video 16: Power Analysis, Clearly Explained!!!

**Key Concepts:**

- Say we test two drugs and get a p value of 0.06. Because the p-value is > 0.05, the threshold that we are using to define a statistically significant difference, we can't say that Drug A is better than Drug B
- Even though we suspect that the measurements represent two different distributions, we cannot rule out that the data doesn't come from a common distribution formed where they overlap
- It would be tempting to give one more person Drug A and one more person Drug B and recalculate the means and redo the statistical test, but that would be p-hacking
- Instead, we will do a Power Analysis to determine the sample size for the next run of the experiment
- As we know, a Power Analysis determines what Sample Size will ensure a high probability that we correctly reject the Null Hypothesis that there is no difference between the two groups
- If we use the Sample Size recommended by the Power Analysis, we will know that regardless of the p-value
, we used enough data to make a good decision
- Two main factors:
    - How much overlap there is between the two distributions we want to identify
    - The Sample Size; the number of measurements we collect from each group

- To calculate:
    - First, we need to decide how much power we want 
        - A common value for Power is 0.8
        - A power of 0.8 means having at least 80% chance of correctly rejecting the Null Hypothesis. If there is very little overlap, we only need a small Sample size to get that 0.8; and the other way around
    - We will also need to determine the threshold for significance ("alpha")
        - We can use any value between 0 and 1, but a very common threshold is 0.05
    - Lastly, we need to estimate the Overlap between the two distributions. This is effected by both the distance between the population means and the standard deviations
        - To combine means and standard deviations into a single metric, we can use Effect Size(d) = Estimated difference in the means / Pooled estimated standard deviations 
        - Pooled estimated standard deviations  = √ (s²+s² / 2), with the s representing the estimated standard deviation for each distribution
    - Once we know the Effect size (say 1.5), and the power (0.8) and the threshold for significance (0.05), we can use an online statistics power calculator. With the above numbers, this would give a sample size of 9
    - This means that if we get 9 measurements per group, we will have an 80% chance to correctly reject the Null Hypothesis


### Video 17: Conditional Probabilities, Clearly Explained!!!

**Key Concepts:**

- Say we ask 14 people whether they love Candy and/or Soda:
    - 4 people love just Candy
    - 2 people love Candy AND Soda
    - 5 people love just Soda
    - 3 people don't love either
- So basically Candy is loved by 6 people, and Soda is loved by 7 people
- We can track the data through a Contingency Table
    - Loves Candy + Loves Soda: 2
    - Loves Candy + Doesn't Love Soda: 4
    - Doesn't Love Candy + Loves Soda: 5
    - Doesn't Love Candy + Doesn't Love Soda: 3

- Let's calculate the probability of meeting someone who loves both:
    - p(loves candy and soda) = 2/14 = 0.14 (a pretty small probability)
- Let's calculate all the probabilities in a similar way:
    - Loves Candy + Loves Soda: 2, p=2/14 = 0.14 
    - Loves Candy + Doesn't Love Soda: 4, p=4/14 = 0.29
    - Doesn't Love Candy + Loves Soda: 5, p=5/14 = 0.36
    - Doesn't Love Candy + Doesn't Love Soda: 3, p=3/14 = 0.21
- We can also determine:
    - The probability that someone loves Soda, regardless of how they feel about Candy: 2 + 5 = 7, p=7/14
    - The probability that someone does not love Soda, regardless of how they feel about Candy: 4 + 3 = 7, p=7/14
    - The probability that someone loves Candy, regardless of how they feel about Soda: 2 + 4 = 6, p=6/14
    - The probability that someone does not love Candy, regardless of how they feel about Soda: 5 + 3 = 8, p=8/14

- Conditional Probability: Knowing that a person loves Soda, what is the probability that they ALSO love Candy?
    - In other words, what is the probability that someone loves Soda AND Candy, given that we know they love Soda? ("Given that" is represented by the | symbol):
        - p(loves candy and soda | loves soda), or
        - p(loves c and s | loves s), or
        - p(loves c | loves s)
    - Earlier, we calculated the probability that someone loved both, but without already knowing that they loved Soda. Because we didn't already know that, the denominator consisted of the total number of people, 14
    - But now that we know the person loves Soda, we can focus on just the 7 people who love Soda
    - As we know, there are only 2 people that love both, so we put that in the numerator, and since there are 7 people in total who love Soda, we put that in the denominator:
        - p(loves c and s | loves s) = 2/(2+5) = 0.29
    - So the probability that someone loves Candy given that we know they love Soda, is 0.29
    - And as we can see, this probability is different from the original probability, that was calculated without knowing whether or not they liked Soda
    - Knowing that they loved Soda, increased the probability that they would love Candy

- Another Conditional Probability:
    - What is the probability that someone doesn't love Candy, given that we know they love Soda?
        - p(not love c and loves s | loves s)
    - As we know, there are 5 people that don't love Candy and love Soda, so we put 5 in the numerator
    - And there are 7 people in total who love Soda, so we put that in the denominator
        - p(not love c and loves s | loves s) = 5/(2+5) = 0.71
    - So the probability that someone doesn't love Candy (but loves Soda), given that we know they love Soda, is 0.71
    - Interestingly, if we divide both the numerator and the denominator by the total number of people (14), we get the same probability:
        - 5/14 / (2+5)/14 = 0.71
    - But now the numerator (5/14) is the original, unconditional probability that someone from the entire group does not love Candy but loves Soda, and the denominator (7/14) is the unconditional probability that someone from the entire group loves Soda
    - So the probability that someone does not love Candy but loves Soda, given that we know that they love Soda, is equal to the probability that someone does not love Candy but loves Soda, divided by the probability that someone in the entire group loves Soda
        - p(not love c and loves s | loves s) = p(not love c and loves s) / p(loves s) = 0.71
- In general, a Conditional Probability is the probability that something will happen, scaled by the knowledge we alrady have about the event


### Video 18: Bayes' Theorem, Clearly Explained!!!

**Key Concepts:**

- Continuing from the previous chapter:
    - Let's change the knowledge we have about the event, from knowing that they love Soda, to knowing that they do not love Candy
        - p(not love c & loves s | not love c) = p(not love c and loves s) / p(not loves c) = (5/14) / (8/14) = 0.63
    - In both cases (previous and present chapter), we wanted to know the probability of the same event: meeting someone who does not love Candy but loves Soda
    - However, since we have different knowledge in each case, we scale the probabilities of the events differently, and ultimately get different probabilities

- But what if we didn't know at all the p(not love c and loves s)? Can we still solve the Conditional Probabilities without the numerator? Yes, with algebraic manipulation!
    - We can multiply both sides of the first equation by p(loves s) and get:
        - p(not love c & loves s | loves s) * p(loves s) = p(not love c & loves s) / p(loves s) * p(loves s)
        - p(not love c & loves s | loves s) * p(loves s) = p(not love c & loves s)
    - Likewise, we can multiply both sides of the second equation by p(no love c) and get:
        - p(not love c & loves s | not love c) * p(not love c) = p(not love c and loves s) / p(not love c) * p(not love c)
        - p(not love c & loves s | not love c) * p(not love c) = p(not love c and loves s)
    - In both cases, we end up with the probability of meeting someone who does not love Candy but loves Soda p(not love c and loves s), equal to:
        - p(not love c & loves s | loves s) * p(loves s), and
        - p(not love c & loves s | not love c) * p(not love c)
    - Which means that both equations are equal to each other:
        - p(not love c & loves s | loves s) * p(loves s) = p(not love c & loves s | not love c) * p(not love c)
    - Remember that we want to solve for these two terms:
        - p(not love c & loves s | loves s)
        - p(not love c & loves s | not love c)
    - Starting with the first one, we divide both sides by p(loves s) and get:
        - [p(not love c & loves s | loves s) * p(loves s)] / p(loves s) = [p(not love c & loves s | not love c) * p(not love c)] / p(loves s)
        - p(not love c & loves s | loves s) = [p(not love c & loves s | not love c) * p(not love c)] / p(loves s)
    - And now with the second one, we divide both sides by p(not love c) and get:
        - [p(not love c & loves s | not love c) * p(not love c)] / p(not love c) = [p(not love c & loves s | loves s) * p(loves s)] / p(not love c)
        - p(not love c & loves s | not love c) = [p(not love c & loves s | loves s) * p(loves s)] / p(not love c)
    - So we dont need to know p(not love c & loves s). We have derived Bayes's Theorem!

- Bayes' Theorem tells us that the first Conditional Probability, which is based on knowing that the person loves Soda, can be derived from the second Conditional Probability, based on knowing that the person do not love Candy (and the other way around)
    - If we use A for "does not love Candy" and B for "loves Soda", then we can rewrite each equation into the standard formula for Bayes' Theorem:
        - p(A&B|B) = p(A&B|A)*p(A) / p(B)
        - p(A&B|A) = p(A&B|B)*p(B) / p(A)
    - The Conditional Probability given that we know one thing about an event, can be derived from knowing the other thing about the event
    - If we don't have all the data, we can use this formula. For example if we know:
        - p(not love c & loves s | loves s) = 0.71
        - p(loves s) ≈ 0.6
        - p(not love c) = 0.57
    - Then we plug in the numbers:
        - p(not love c & loves s | not love c) = (0.71 * 0.6) / 0.57 ≈ 0.75

- Note that we got a different number now (0.75) than before (0.63), because we guessed one of the probabilities (0.6)
    - Bayesian Statistics is about understanding what it means to make a guess like this (in absence of real data) and all it implies
    - Bayes' Theorem is the basis for Bayesian Statistics, which is this equation paired with a broader philosophy of how statistics should be calculated


### Video 19: Naive Bayes, Clearly Explained!!!

**Key Concepts:**

- By Naive Bayes we mean the Multinomial Naive Bayes Classifier; There is another commonly used version called Gaussian Naive Bayes Classification, which we will see on the next chapter
- Imagine we receive normal messages from friends and family, and we also receive spam, and want to filter out the spam messages
    - We make a histogram of all the words that occur in the normal messages from friends and family, and we can use it to calculate the probabilities of seeing each word, given that it was in a normal message:
        - "Dear": p(Dear|Normal) = 8/17 = 0.47
        - "Friend": p(Friend|Normal) = 5/17 = 0.29
        - "Lunch": p(Lunch|Normal) = 3/17 = 0.18
        - "Money": p(Money|Normal) = 1/17 = 0.06
    - Now we make a histogram of all the words that occur in the spam messages, and calculate the probabilities of seeing each word, given that it was in a spam message:
        - "Dear": p(Dear|Spam) = 2/7 = 0.29
        - "Friend": p(Friend|Spam) = 1/7 = 0.14
        - "Lunch": p(Lunch|Spam) = 0/7 = 0.00
        - "Money": p(Money|Spam) = 4/7 = 0.57
    - These Probabilities are also called Likelihoods, being of discrete, individual words and not something continuous

- Now imagine we got a new message saying "Dear Friend", and we want to decide if it's a normal message or spam:
    - We start with an initial guess about the probability that any message, regardless of what it says, is a normal message:
        - The guess can be any probability that we want, but a common guess is estimated from the training data
        - For example, since 8 of the initial 12 messages were normal messages, our initial guess will be 0.67:
            - p(N) = 8 / (8+4) = 0.67
        - The initial guess that our message is normal, is called a Prior Probability
        - Now we multiply the initial guess by the probability that the word Dear occurs in a normal message, and the probability that the word Friend occurs in a normal message:
            - p(N) * p(Dear|N) * p(Friend|N)
            - 0.67 * 0.47 * 0.29 = 0.09
        - So 0.09 is the score that Dear Friend gets if it is a normal message
        - However, technically, it is proportional to the probability that the message is normal, given that it says Dear Friend:
            - p(N|Dear Friend) ∝ 0.09 
    - Now we repeat the process with an initial guess about the probability that any message, regardless of what it says, is a spam message:
        - From the training data we estimate that p(S) is 0.33:
            - p(S) = 4 / (4+8) = 0.33
        - Now we multiply the initial guess by the probability that the word Dear occurs in a spam message, and the probability that the word Friend occurs in a spam message:
            - p(S) * p(Dear|S) * p(Friend|S)
            - 0.33 * 0.29 * 0.14 = 0.01
        - So 0.01 is the score that Dear Friend gets if it is a spam message
        - However, technically, it is proportional to the probability that the message is normal, given that it says Dear Friend:
            - p(S|Dear Friend) ∝ 0.01
    - Because 0.09 > 0.01, we conclude that the message is normal
    - This is the way Naive Bayes Classification works

- Now, let's try to classify the message "Lunch Money Money Money Money"
    - Since p(Money|N) = 0.06 and p(Money|S) = 0.57, it seems reasonable to predict that this message will end up being spam, especially with "Money" being repeated four times
    - However, we encounter an issue:
        - First, we guess that it is a normal message:
            - p(N) * p(Lunch|N) * p(Money|N)⁴ = 0.000002
        - Then, we guess that it is a spam message:
            - p(S) * p(Lunch|S) * p(Money|S)⁴ = 0 
    - The issue is that we only get 0 just because the probability of Lunch in spam was 0, since it was not in the Training Data. That 0 makes the entire equation equal 0
    - That means that no matter how many times we see the word Money, if the word Lunch is in the same message, it always will be classified as normal!
    - The solution is to add 1 count to each word for all words (i.e. if the probability was 4/12 before, now it is 5/12)
    - The number of counts we add to each word is typically referred to with the Greek letter α (alpha). In this case α = 1, but we could have set it to anything
    - Now the probability of the word Lunch in a spam message is:
        - p(Lunch|S) = 1 / (7+4) = 0.09
    - Note: Adding counts to each word does not change our initial guess that a message is normal p(N), or spam p(S), because it did not change the number of messages in the Training Dataset that are normal (8) or spam (4)
    - Now if we recalculate the scores for this message:
        - p(N) * p(Lunch|N) * p(Money|N)⁴ = 0.00001
        - p(S) * p(Lunch|S) * p(Money|S)⁴ = 0.00122
    - Since 0.00122 > 0.00001, we classify the message as spam

- Why is Naive Bayes, naive?
    - It treats all word orders the same:
    - The Normal message score for the phrase "Dear Friend" is the same as the score for "Friend Dear", which is not how people communicate
    - Naive Bayes ignores grammar rules and common phrases, treating language like a bag full of words and each message is a random handful of them
    - But it performs surprisingly well when separating Normal messages from Spam
    - In ML lingo, we say that Naive Bayes has high bias (because it ignores relationships among words) and low variance (because it works well in practice)


### Video 20: Gaussian Naive Bayes, Clearly Explained!!!

**Key Concepts:**

- Gaussian Naive Bayes is named after the Gaussian distributions that represent the data in the Training Dataset
- Say we wanted to predict if someone would love the 1990 movie Troll 2 or not
    - We measure the amount of popcorn, soda pop, and candy they consume per day
    - For example, the mean for popcorn for people who loved Troll 2 was 24, and standard deviation was 4; this forms a "Gaussian", or normal distribution
    - We go on to plot the normal distributions for all three datasets: We create three graphs (popcorn, soda, and candy) containing the love/don't love bell curves for each. Some overlap, and some don't
    
- Say someone new shows up and says they eat 20g of popcorn, drink 500ml of soda and eat 25g of candy every day. Let's use the Gaussian Naive Bayes to decide if they love Troll 2 or not
    - First, we make an initial guess ("prior probability") that they love Troll 2, based on the training data
    - Since 8 of the 16 people in the training data loved Troll 2, the initial guess is 0.5:
        - p(loves Troll 2) = 0.5
        - p(does not love Troll 2) = 0.5
    - The score for loves Troll 2 is the initial guess that the person loves Troll 2, times the Likelihood that they eat 20g of popcorn given that they love Troll 2, times the Likelihood that they drink 500ml of soda given that they love Troll 2, times the Likelihood that they drink 25g of candy given that they love Troll 2 (note: the Likelihood is the y-axis coordinate on the curve that corresponds to the x-axis coordinate)
        - p(loves) * L(popcorn = 20 | loves) * L(soda = 500 | loves)
        - 0.5 * 0.06 * 0.004 * a really small number
    - When we get really small numbers, it's a good idea to take the log() of everything to prevent something called Underflow:
        - Every computer has a limit to how close a number can get to 0 before it can no longer accurately keep track of that number. When a number gets smaller than that limit, we run into Underflow problems and errors occur
        - So we use the log() function to avoid it. Any log will do, but the natural log (ln), or log base e, is the most commonly used log() in statistics and machine learning
    - So we take the log (base e) of:
        - 0.5 * 0.06 * 0.004 * a really small number
    - The log() turns the multiplication to addition:
        - log(0.5) + log(0.06) + log(0.004) + log(a really small number)
        - (-0.69) + (-2.8) + (-5.5) + (-115) = -124
        - log(loves Troll 2 Score) = -124
    - We repeat the same process for Does not love Troll 2, and get:
        - log(not love Troll 2 Score) = - 48
    - Since -48 > -124, we classify the person as someone who does not love Troll 2

- When we looked at the raw data (the graphs), visually it almost looked like we should have classified this person as someone who loves Troll 2, because in 2 out of the 3 graphs (popcorn and soda), the person was inside the "love Troll 2" distributions. However, it turns out that candy had a much larger say, due to its large distance from the "love Troll 2" distribution
    - This means we may only need candy to make classifications
    - We can use Cross Validation to help us decide which things (popcorn, soda, and/or candy) make the best classifications. We will see Cross Validation in a future lesson


### Video 21: In Statistics, Probability is not Likelihood.

**Key Concepts:**

- For probability, imagine a normal distribution of mouse weights:
    - It has a mean of 32 grams and a standard deviation of 2.5
    - On the low end we have 24 grams and on the high end we have 40 grams
    - The probability that we will weigh a randomly selected mouse between 32 and 34 grams, is the area under the curve between 32 and 34 grams
    - That area equals 0.29, meaning there is a 29% chance a randomly selected mouse will weigh between 32 and 34 grams:
        - pr(weight between 32 and 34 grams | mean = 32 and standard deviation = 2.5) = 0.29
    - If we want to see different mouse weights, we change the left side of the equation. The right side, describing the distribution, stays the same
    - When we talk about probabilities, we are talking about a distribution that is described by the right side of the equation, and the area under the curve that is described on the left side
    - Using the same distribution, we can change the left side to get a new probability

- Likelihood is the opposite:
    - In this case we have already weighed our mouse/mice
    - Say our mouse weighs 34 grams
    - The likelihood of weighing a 34 gram mouse is, the y-axis height when x = 34; this equals 0.12:
        - L(mean = 32 and standard deviation = 2.5 | mouse weighs 34 grams) = 0.12
    - If we shifted the distribution over so that the mean was 34 grams, the new likelihood would now be the top of the bell curve, with y-axis value 0.21
    - So with likelihoods, the measurements on the right side are fixed, and we modify the shape and location of the distribution with the left side

- In summary: 
    - Probabilities are the areas under a fixed distribution:
        - pr(data|distribution)
    - Likelihoods are the y-axis valies for fixed data points with distributions that can be moved
        - L(distribution|data)


### Video 22: Maximum Likelihood, clearly explained!!!

**Key Concepts:**

- Let's say we weighed a bunch of mice:
    - The goal of maximum likelihood is to find the optimal way to fit a distribution to the data
    - There are lots of different types of distributions for different types of data, but in this case, we think the weights may be normally distributed
    - As "normally distributed", we expect:
        - Most of the measurements to be close to the mean (average)
        - The measurements to be relatively symmetrical around the mean
    - Once we settle on the shape, we have to figure out where to center it
    - Most of the values we measure (the average weight) should be near the distibution's mean/average
    - Then the probability, or "likelihood" of observing these weights is relatively high

- Find the maximum likelihood estimate for the mean:
    - We can plot the likelihood of observing the data (y-axis) over the location of the center of the distribution (x-axis)
        - We start on the left with a leftmost distribution and plot the likelihood of observing these measurements
        - We continue to the right, all the way to the end
        - We want the location that "maximizes the likelihood" of observing the weights we measured
        - We see that the central location for the mean does that, and thus it is the "maximum likelihood estimate for the mean" (the mean of the distribution, not the data; but in a normal distribution those two things are the same)

- Find the maximum likelihood estimate for the standard deviation:
    - Similar to before, we can plot the likelihood of observing the data, for different values of the standard deviation
    - And we find the standard deviation that maximizes the likelihood of observing the weights that we measured

- So now we have a normal distribution that has been "fit" to the data, by using the maximum likelihood estimations for the mean and standard deviation
    - So when someone says that they have the maximum likelihood estimates for the mean or the standard deviation or for something else, it means that they found the value for the mean or standard deviation or something else, that maximizes the likelihood that we observed what we observed
    - As we saw on the previous chapter, "likelihood" refers to this situation, where we are trying to find the optimal value for the mean or standard deviation for a distribution, given a bunch of observed measurements


### Video 23: The Main Ideas of Fitting a Line to Data (The Main Ideas of Least Squares and Linear Regression.)

**Key Concepts:**

- How to fit a line in our plotted data?
    - We want to minimize the distance between the data points and the line
    - We square the difference between each data point and then add them up
    - The reason we square them is for all values to be positive, whether the data point lies on top or below the line
    - The result is the "sum of the squared residuals" 
    - A smaller value is a better fit

- Method:
    - Take the generic line equation:
        - y = ax + b, where a is the slope and b is the y-intercept
    - We want to find the optimal values for a and b to minimize the value of squared residuals
    - Since we want the line that will give us the smallest sum of squares, this method is called "Least squares"
    - Distance between line and observed value:
        - ((a x₁ + b) - y₁)² + ((a x₂ + b) - y₂)² + ...
    - Try a few lines (rotate the line a few times) and plot the results of the sum of squared residuals for each calculation; the sum data points will go down and then back up
    - To find the optimal rotation for the line, take the derivative (slope) of the function of the plotted sum of squared residuals, and find where it equals zero
    - Remember that the different rotations are just different values for a (line slope) and b (line intercept)
    - Taking the derivatives of both the slope and the intercepts tells us where the optimal values are for the best fit
    

### Video 24: Lowess and Loess, Clearly Explained!!!

**Key Concepts:**

- What about fitting a curve to data?
    - Use a sliding window to divide 


    


