Allways when the topic came to dapps the tenor was that these dapps can do awesom things like smart contracts, which we imagine to be small programm snippets containing the logic of the contract between the parties which also have direct access to the bank accounts of the parties.

It was not clear to us how the conditions of a potential money transfer could be implemented in dapp.
```python
if (condition):
    transferMoneyFromAtoB(10,A,B)
```
We think the dapps idea would be much more versatile if dapp creator would have a service at hand which allows to connet to the real world, and situations/events/conditions in the real world.

At first we though of a bet between A and B:

```python
# A puts up a bet and wants to find someone willing to bet against it(A will always be for it)
bettext = getBetText(A) #e.g.: "Club K will win 2018 Championship in League X"
value = getBetValue(A) # e.g.: 10
if(getBuyIn(A, value)): return false  # get money from A and if it fails take off the bet 

# Now we search for someone willing to bet against it
while(true):
    B = searchOpponent()
    if(getBuyIn(B, value)): break


# time passes until end of championship while dApp holds both parties money
...


# let A and B vote themselfes about the outcome of the bet
bool vA = getVote(A,bettext)
bool vB = getVote(B,bettext)

if vA == vB: # both agree on whatever the outcome was
    if (vA == True):
        # A won
        transferMoney(value,A)   #payout to A
    else:
        # B won
        transferMoney(value,B)	 #payout to B
else: 		# parties disagree
    # if parties disagree, need to have some form of outside validation
    # payoutValue is the amount of the pot left after paying for validation
    betres, finished, payoutValue = eval(bettext) # call some api for evaluation
    
    # time passes until evaluation is setteled
    if(finished):
        if (betres == True):
            # A won
            transferMoney(payoutValue,A)
        else:
            # B won
            transferMoney(payoutValue,B)
    else:
        # bet could not be evaluated
        paybackBuyIn(A)
        paybackBuyIn(B)
```

The most important part is the "eval(bettext" function which will settle who won. This function has to obtain the relevant information from an unbiased, decentralised source in order to validate the outcome of the event that is object of the bet.

Our approach would involve people voting for an outcome, with the majority of votes setting the outcome we see as "true". Ideally, each of these validators has no preference towards either outcome and each of them obtains the information about the outcome through a different reliable source. Even in this case, the outcome could be opposite to the "true" outcome if, for example, the outcome of an event is not known to the general public or if the truth is hard to verify for each person individually.(e.g.: "Is the 21-trillionth digit of pi 8?")

In reality, the outcome can also have other biases such as people believing in common misconceptions or the object of the bet changing over time.(e.g.: "Is it the year 2017?"). 
So, in order to obtain the correct result, the phrasing of the question as well as the time of the bet are vitally important.

We now know:
There is no proof for the outcome being in fact "true" since it is effectively a poll of "random" people who want to participate. BUT this is exactly how "truth" is found in real life, a group of people(society/politicians/judges/jurors/scientists) find a consensus about the "truth" and therefore give the accepted answer to a question. 

So, for an unbiased, decentralised set of validators, we can assume that the "true" outcome that is formed from this consensus is at least as reliable as a consensus found in the real world. Now it is important to form a system that is at least as trustworthy as the real world consensus:
[- rule that needs to be implemented (real world equivalent it is derived from)]
- Validators have to be punished for making a false claim (discredit for wrong claims)
- Validators have to be commended for making a correct claim (Science Prizes/respect)
- The set of validators have to be trustworthy as a whole since they consist of many people with many different oppinions and biases that eventually balance (many parties in a parliament)
- The number of validators has to be sufficiently large (number of seats in parliaments are usually not dependent on the voter participation)
- Events/"Truths" that are harder to evaluate and validate have to be rewarded higher (Nobel Prize)





