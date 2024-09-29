# Basic
## sentence
- so on and so forth
## Tip
> clarify thought, flexibility, knowledge
- Don't dive into detail
- diff architecture
- keep it simple stupid
- make justifications for points you made
- discuss pros and cons of choices
## load balance
> many request to servers, use hashmap to map into servers

Reference:
- [Performant Front-End Architecture](https://www.debugbear.com/blog/performant-front-end-architecture)

## requirement

- user/customers
  - who will use it
  - how the system will be used
    - frequency
- scale(r/w)
  - How many read queries per second
  - How much data is queried per request
  - How many video views are pocessed per second
  - Can there be spikes in traffic
- performance
  - What is expected write-to-read data delay?
  - What is expected p99 latency fo read queries?
- cost
  - Should the design minimize the cost of development?
  - Should the design minimize the cost of maintenance?
