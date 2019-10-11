#### Please add your answers to the **_Analysis of Algorithms_** exercises here.

## Exercise I

a) Whatever n is, it will always run n times...
So, O(n)

b) As n increases, so do the number of operations required to
break the while-loop. It's not so high as n^n, but turns out to be something like n + (n/2) + ((n - 1)/2) + ((n - 2)/2) + ... and so on, until it reaches ((n - n)/2).
So, I would say: O(n log(n))

c) Even though there is recursion, the simplicity of n reducing by 1 for each operation looks very much like linear time.
So, O(n)

## Exercise II

It would look something like this, a binary search:

def find_safe_floor(f, b): #f is number of floors
#b is the secret 'break' floor

    low = 0         bottom floor of building
    top = f        number of floors the building has
    dropped_egg = 0     initialize our egg counters
    broke_egg = 0

    while low <= high:      going to find which is the safe floor, which will actually be (b - 1)

        attempt = (low + top)//2    going to start in the middle, just in case f is something like 100...

        if attempt == b:    we found it fast, but still broke an egg
            broke_egg += 1
            return attempt - 1      we discovered the limit floor, one floor down is safe for the eggs

        if attempt > b:   broke an egg, need to try again
            broke_egg += 1
            top = attempt - 1       plan our next drop by setting our 'top' to the floor below us
        else:
            dropped_egg += 1        dropped one egg, no break, gotta go higher
            low = attempt + 1       plan our next drop by setting our 'low' to the floor above us


    A binary search should prevent us from wasting too many eggs on a building with LOTS of floors, and its runtime complexity is O(log(n)), which is pretty good.
