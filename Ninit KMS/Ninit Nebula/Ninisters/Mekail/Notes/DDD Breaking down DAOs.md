

Ninvestment DAO

5 friends come together to decentralize their capital allocation through different investment vehicles together. They use the amount of funds they contributed to the pool to weigh their votes on proposals to exchange their treasury for different digital assets and currencies. They collectively vote on buying and selling different assets, and can rage quit their ratio of investment if they want to cash out and leave the DAO

Addiction DAO

A DAO for individuals that lack connection and community that contribute to a pool and have access to funds to better their life and encourage and assist with sober living requiring participants to leave notes on what they used funds for, and DAO members can vote on the usage of the funds. Sponsors and addicts can be separate 

GKL DAO

A DAO for the community of GKL where we track customers spending and give governance on new menu items and events that occur within the community


Elements:

DAO Members
Capital Treasury
Decision Making processes
Weighted Governance
Tracked Reputations
Rage Quit Mechanisms
Capital Flow Tracking


------
Create the Abstract Citizen Element
What are the common abilities a Citizen or DAO member can have for Most DAOs
What are the categories of DAO members?
Most DAO members can vote on something, 

Citizen 
- Functions
		- Voting
		- Leaving
		- Propose
		- Join
		- Communicate
- Attribute

Moloch dao citizen (is citizen):
- Functions
		- Voting
		- Leaving: Rage Quit 
		- Propose
		- Join
		- Communicate
- Attribute


Ensure high modularity through class inheritance; ex:

```code
class citizen:

  

    def leave(self):

        return "leave DOA"

  

class mollacDAO_citizen(citizen):

  

    def leave(self):

        return "rage quit"

  

if __name__ == "__main__":

  

    citizen1 = citizen()

    citizen2 = mollacDAO_citizen()

  

    print(citizen1.leave())

    print(citizen2.leave())

  

    print(issubclass(mollacDAO_citizen, citizen))
```