# CodeVita-2019-Distribute-Books

def mult(a, b, p):
    return (a * b) % p  # can do this in python since a*b will fit
 
 
def derangements(n, p):
    # sf[0] will represent !(n-2)
    # sf[1] will represent !(n-1)
    # sf[2] will represent !(n)
    sf = [1, 0, 1]
 
    if n <= 2:
        return sf[n]
 
    # !(n) = (n-1) * (!(n-1) + !(n-2)) - check derangements formula
    for i in range(3, n + 1):
        sf_i = mult(i - 1, sf[2] + sf[1], p)
        sf = [sf[1], sf[2], sf_i]
 
    return sf[2]
 
 
def solve(n):
    p = int(1e9 + 7)
    print(derangements(n, p))
 
 
if __name__ == "__main__":
    n = int(input())
 
    solve(n)
