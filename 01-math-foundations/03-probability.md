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
    - This Expected Value represents what we would expect per bet if we made this bet a bunch of times

- Sigma notation:
    - Using sigma notation, the Expected Value of E(x) is the sum of each specific outcome x, times the probability of observing each outcome x:
        - E(X) = Σ x P(X=x)
        - Σ means sum
        - x is the outcome
        - P(X=x) means "the probability of each outcome"
        - E(X) = (0.17 * -1) + (0.83 * 1) = 0.66 = Σ x P(X=x)
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
    - The Expected Value is the sum (Σ) of: each outcome (x) times the probability of observing that outcome (P(X=x))
        - E(X) = Σ x P(X=x)
        - E(X) = Σ x P(X=x) = (10 * 0.17) + (-1 * 0.83) = 1.7 - 0.83 = 0.87
    - The Expected Value is 0.87
    - That means that we expect to gain on average, 87 cents every time we make this bet, which is even better than before

- In this lesson we only talked about how to calculate Expected Values for discrete events, like whether or not someone has heard of Troll 2
- However, we will next see how to calculate Expected Values for continuous events, like how much time passes between text messages on our phone
- In the future, we will also see why we divide the sample variance by n-1, and why dividing by n underestimates the variance

### Video 4: Expected Values for Continious Variables!!!

**Key Concepts:**

- 
    
