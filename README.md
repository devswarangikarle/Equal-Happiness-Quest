# Equal-Happiness-Quest

In a cheerful toy store, two friends, Lily and Alex, stumbled upon N toys lined up beautifully. Each toy had a happiness value associated with it, represented by hᵢ. Excitedly, Lily decided to start picking toys from the left side of the line without skipping any. Meanwhile, Alex began his collection from the right side, also without skipping any. However, there was a catch: once one of them picked a toy, the other could no longer choose that toy.
Determined to make their happiness equal, Lily and Alex wanted to maximize the total number of toys they could collect while ensuring that the sum of happiness values from their selected toys matched. Can you help them figure out the maximum number of toys they can pick together?

Input
The first line of the input contains a single integer N.
The second line of the input contains N space-separated integers.

Constraints:
1 ≤ N ≤ 10^5
1 ≤ hi ≤ 10^4
Output
Print the maximum number of toys they can pick in total.

def equal_happiness_quest():
    # Input reading
    N = int(input())
    happiness = list(map(int, input().split()))

    # Initialize pointers and sums
    left, right = 0, N - 1
    sum_left, sum_right = 0, 0
    max_toys = 0

    # Two-pointer technique
    while left <= right:
        if sum_left < sum_right:
            sum_left += happiness[left]
            left += 1
        elif sum_left > sum_right:
            sum_right += happiness[right]
            right -= 1
        else:  # sum_left == sum_right
            max_toys = max(max_toys, left + (N - right - 1))
            sum_left += happiness[left]
            left += 1

    # Output the maximum number of toys
    print(max_toys)

# Call the function
equal_happiness_quest()
