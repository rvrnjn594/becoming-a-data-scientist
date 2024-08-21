# Probablity

Probablity theory is a branch of Mathmatics which deals with **describing the chances of an occurrene of event.**

> We'll cover the following:
>
> - Probablity
>   - Event
>   - Sample Space
>   - An example
>     - Solution
> - Schools of probablity
>   - Frequentist or Classical Probablity
>   - Baysian Probablity

## Probablity

Probability deals with how likely an event is to occur.  
It has a lot of components that are used in the Data Science field. It is mostly used to describe the uncertainty in our predictions and other results.  
It also helps a lot in the Machine Learning field.  
 Probability is usually described by a number, between 0 and 1.  
 The close the number is to 1, the more likely an event is to occur.

## Event

The event is the outcome to which the probablity is assigned.

## Sample Space

It is the set of possible outcomes or events.

> - An event with probablity one is called a certain event.
> - An event with probablity zero is called an impossible event.
> - The sum of all the probablities of an experiment is always equal to 1.
>
> We can calculate probablity by counting all of the occurrences of the event and dividing it by the total possible occurrences of the event.
>
>       Probablity = (occurrences) / (non-occurrences + occurrences)

## An example

> A coin is tossed twice. What is probablity that at least 1 head occurs?

## Solution

We can deduce the following things from the above statement.

H = Head outcome on coin toss
T = Tail outcome on coin toss

After flipping the coin twice, we can have the following possible outcomes, which is our sample space.

**Sample Space** = {HH, HT, TH, TT}
**Event** = At least 1 Head(H) occurs.

We can see that there are three events in which at least one head(H) occurs. So applying the formula above we have.

Probablity = 3/4 = 0.75

We can also calculate the inverse of the above probablity, i.e., events in which no head(H) occurs.

Inverse probablity = 1 - 0.75 = 0.25

> - 0.75 is the probablity that at least one head appears.
> - 0.25 is the probablity that no head appears.

## Schools of probablity

There are two main ways of thinking about probablity.

#### Frequentist or Classical Probablity

The frequentist approch is objective.  
 Events are observed and counted, and their frequencies provide the basis for directly calculating a probablity, hence the name frequentist.

> We explored an example of classical probablity above in the coin flipping example.

#### Bayesian Probablity

The Bayesian approach to probablity is subjective.  
 Probablities are assigned to events based on evidence and personal belief and are centered around Baye's theorem, hence the name Bayesian.  
This allows us to assign probablities to very infrequent events and events that have not been observed before, unlike frequentist probablity.

Both of the above definitions have been taken from the famous books of Jason Brownlee on probablity.
