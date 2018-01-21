# Reward system

This is a plan for a cryptocurrency applied through the plan smart contract. We
call the currency `demos` from now on. 

# Money


If the currency will be included, then all plan resources will run through the
system valued in `demos` and be managed by it. All plan tasks need to be
fulfilled before the reward mechanism activates. External market mechanisms are
allowed.


## Reward collection 

There will be no mining, all demos are created at system creation: 10^12 (1
trillion). All `demos` will be distributed by the smart contract due to the
following rules. The system also raises a 1% tax on all revenue to refill its
pool. Initially all demos are distributed through by the system described here.

### Amount of reward

The amount of reward will be contributed by each rule equally:

1. Reward for plan surplus in per cent due to 
~~~python
def surplus(x): return 1/(e-1) * (exp(min(x,20)/20) - 1) 
~~~
   Note: This function has a range from 0.0 - 1.0. It is exponential in
   reward signal, encouraging higher growth rates. In general higher growth
   rates are exponentially more difficult to achieve and therefore the
   function's behavior balances this difficulty.
2. Reward for revenue: 
~~~python
def revenue(x): return math.log(min(10**12, x+1))/math.log(10**12)
~~~

   Note: This function weakly encourages more revenue in the executing plan. It
   saturates if the plan has a revenue of 1 trillion `demos`.

3. Reward for sustainability: Each task can be flagged as sustainable. The ratio
   of the volume in sustainable tasks versus all tasks is rewarded. 
   
   
## Reward distribution

### Management responsibility

1. Number of votes for each position. Votes are counted for each delegate they
   flow through and the rewards are normalized to sum to one. (0.5 of reward)

### Good behaviour

1. Labor contributed, measured in `demos`. The rewards are then normalized to sum
   to one. (0.25 of reward)
2. Evaluation sheet for each user. This anonymous mechanism allows people to
   distribute demos to people they enjoy working with. (0.25 of reward)


# Problems
- Fake completion of the plan to gain rewards. But this will devalue `demos`, as
  its purpose is plan fulfillment and it won't be used if the system is faked.
