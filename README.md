# The-Treasure-Chest-Combination-Lock

A treasure chest has a peculiar combination lock: it opens only when a subset of the n distinct-valued coins in a nearby pouch, placed onto its scale together, weighs exactly target units. Find every subset of coins from the pouch that weighs exactly target. Each individual subset must be listed with its coin weights in non-decreasing order, and the overall list of subsets must be sorted lexicographically (comparing subsets element by element, with a shorter subset counted as smaller than a longer one that agrees with it on all shared leading elements).

Input 
The first line contains two integers n n and t a r g e t target — the number of coins and the required weight. The second line contains n n distinct positive integers — the weight of each coin. 

Output 
Print a single integer on the first line — the number of qualifying subsets. Then print that many lines, each describing one subset: its size, followed by its coin weights in non-decreasing order. The subsets themselves must appear in lexicographically sorted order. 

Constraints 
1 < = n < = 20 
1 < = 1<= coin weights < = 1000 <=1000, 
all distinct. 1 < = t a r g e t < = 1000 1<=target<=1000

n, target = map(int, input().split())
coins = list(map(int, input().split()))

coins.sort()
result = []

def backtrack(start, current, total):
    if total == target:
        result.append(current[:])
        return

    if total > target:
        return

    for i in range(start, n):
        if total + coins[i] > target:
            break

        current.append(coins[i])
        backtrack(i + 1, current, total + coins[i])
        current.pop()

backtrack(0, [], 0)

result.sort()

print(len(result))

for subset in result:
    print(len(subset), *subset)
