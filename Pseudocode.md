Allways when the topic came to dapps the tenor was that these dapps can do awesom things like smart contracts, which we imagine to be small programm snippets containing the logic of the contract between the parties which also have direct access to the bank accounts of the parties.

It was not clear to us how the conditions of a potential money transfer could be implemented in dapp.
```python
if (condition):
    transferMoneyFromAtoB(10,A,B)
```
We think the dapps idea would be much more versatile if dapp creator would have a service at hand which allows to connet to the real world, and situations/events/conditions in the real world.

At first we though of a bet between A and B:

```python
bettext = "Club K will win 2018 Championship in League X"
value = 10 # bet value 

betA = True # A bets that bettext is true
betB = False # A bets the opposite

# A and B have to buy-in 
getBuyIn(A)
getBuyIn(B)

# time passes until end of championship 
...

# let A and B vote themselfes about the outcome of the bet
bool vA = getVote(A,bettext) 
bool vB = getVote(B,bettext)

if vA == vB: # both agree
    bool betres = vA
    if (betres == True):
        # A won
        transferMoney(value,B,A)
    else:
        # B won
        transferMoney(value,A,B)
else: # parties disagree
    bool betres = eval(bettext) # call some api for evaluation
    # time passes until evaluation is setteled 
    ...
    if (betres == True):
        # A won
        transferMoney(value,B,A)
    else if (betres == False):
        # B won
        transferMoney(value,A,B)
    else:
        # bet could not be evaluated
        paybackBuyIn(A)
        paybackBuyIn(B)
```
