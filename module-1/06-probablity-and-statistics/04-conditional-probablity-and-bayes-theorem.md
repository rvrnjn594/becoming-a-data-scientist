# Conditional Probablity and Bayes Theorem

Discuss Conditional Probablity and Bayes Theorem

> We'll cover the following:
>
> - Conditional probablity
>   - Example
>   - Solution
> - Baye's theorem

## Conditioanl probablity

The probablity of an event B occurring when an event A has occurred is called conditional probablity. It is denoted as P(B|A), and it is read as "The probablity that B occurs given A has occurred."

It is calculated using the formula below:

P(B|A) = P(A intersection B) / P(A) given P(A) > 0.

#### Example

A math teacher gave her class two tests. 25% of the class passed both tests and 45% of the class passed the first test.  
What percent of those who passed the first test also passed the second test?

#### Solution

From the above question, we can deduce the following:

- Let A be the event that each class passed the first test. Then P(A) = 0.45.
- Let B be the event that each class passed the second test.
- The joint probablity that each class passed both tests is P(A intersection B) = 0.25.
- P(B|A) = ?.

P(B|A) = P(A intersection B) / P(A) = 0.25 / 0.45 = 0.60 = 60% of the class who passed the first class also passed the second class.

## Baye's theorem

On Wikipedia, Bayes Theorem is defined as:

_"Baye's theorem (alternatively Baye's law or Bayes' rule) describes the probablity of an event, based on prior knowledge of conditions that might be related to the event."_

Baye's theorem is stated as seen below:

P(A|B) = (P(B|A) \* P(A)) / P(B)

- P(A|B) is the conditional probablity of A given B has occurred. It is called the **Posterior Probablity.**
- P(B|A) is the conditional probablity of B given A has occurred. It is called the **Likelihood.**
- P(A) is the probablity of A. It is called the **Prior Probablity.**
- P(B) is the probablity of B. It is called the **Evidence.**
