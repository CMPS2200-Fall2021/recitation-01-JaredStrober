# CMPS 2200  Recitation 01

**Name (Team Member 1):**Jared Strober
**Name (Team Member 2):**Aidan Hussain

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various
technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and
others will require you to edit `main.py`.

## Setup

- Login to Github.
- Click on the assignment link sent through canvas and accept the assignment.
- Click on your personal github repository for the assignment (
  e.g., https://github.com/tulane-cmps2200/recitation-01-your_username).
- [Clone](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository-from-github/cloning-a-repository)
  the repository to your local device
- Complete the lab task
- [Add, commit, and push](https://docs.github.com/en/github/managing-files-in-a-repository/managing-files-using-the-command-line/adding-a-file-to-a-repository-using-the-command-line)
  your completed lab back up to GitHub.
    - You will need to issue `git add` for all files that you have modified, e.g., `main.py`, `README.md`, and any
      others that you modify as well.
    - For example, on the command line, in the same directory as your cloned lab:

```
$ git add main.py
$ git commit -m "Implement Required Functions"
$ git push origin main
```

You'll work with a partner to complete this recitation. You will be able to code together in the same `repl.it`
instance. You can choose whose repl.it instance you will share. This person will click the "Share" button in their
repl.it instance and email the lab partner.

## Turning in your work

- Only one team member needs to push your completed lab to github.
- In the README.md file, include the name of the team members.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

- [ ] 
    1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to
       implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`.

- [ ] 
    2. Test that your function is correct by calling from the command-line `pytest main.py::test_binary_search`

- [ ] 
    3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [ ] 
    4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`?

For linear_search and binary_search the worst case input is if the value of key is not in the array. This is because it
would need to search through the entire array before not finding the element and returning -1.

If the key is in the array, then the worst case for linear_search would be if the key was stored at the very end of the
array. If the key is in the array for binary_search, then the worst case input would be if the key is stored in the
middle of one of the two bisects.

- [ ] 
    5. Describe the best case input value of `key` for `linear_search`? for `binary_search`?

Best case input value for linear_search is if the value is at the 0th index. For binary_search it would be at the
midpoint.

- [ ] 
    6. Complete the `time_search` function to compute the running time of a search function. Note that this is an
       example of a "higher order" function, since one of its parameters is another function.

- [ ] 
    7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm
       the implementation by running `pytest main.py::test_compare_search`, which contains some simple checks.

- [ ] 
    8. Call `print_results(compare_search())` and paste the results here:

|            n |   linear |   binary |
|--------------|----------|----------|
|       10.000 |    0.002 |    0.004 |
|      100.000 |    0.006 |    0.002 |
|     1000.000 |    0.058 |    0.006 |
|    10000.000 |    0.613 |    0.007 |
|   100000.000 |    6.040 |    0.012 |
|  1000000.000 |   55.698 |    0.019 |
| 10000000.000 |  518.168 |    0.019 |

- [ ] 
    9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these
       theoretical running times match your empirical results? Why or why not?

Yes. If you look at the results, the linear search produces linear results. It goes from .002 -> .006 -> .058 and has a steady increase
as the n value increases. If you plot these using matplotlib, you would see a nearly straight line. As for the binary search, you can see that the
points are not steadily increasing. It goes from .004 -> .002 -> .006 -> .007 even when the n values increase substantially. 

- [ ] 
    10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of
        length $n$. Suppose you know ahead of time that you will search the same list $k$ times.

    + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search?
      The worst case time complexity is that the item is not in the list. Thus you need to search the entire list even if it is sorted.
      So the worst case complexity would be O(N * K).
      
    + For binary search? 
    
    Theta(n^2) + O(log_2(n)) = O(n^2). You need to first sort the entire list and then still search through the bisection list to find the element.
      
    + For what values of $k$ is it more efficient to first sort and than use binary search versus just using linear
      search without sorting?
      
    When K is greater than N, it makes sense to use binary search rather than linear search. This is because if it takes Theta(N^2) time to sort a 
    list, and you only need to sort the list once, then when K is greater than N, each additional linear search will cost more then just doing a singular
    binary search. 
    