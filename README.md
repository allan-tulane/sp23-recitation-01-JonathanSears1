 # CMPS 2200  Recitation 01

**Name (Team Member 1): Jonathan Sears**_________________________  
**Name (Team Member 2):**_________________________

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`.


## Setup
- Make sure you have a Github account.
- Login to Github.
- Login to repl.it, using "sign in with github"
- Click on the assignment link sent through canvas and accept the assignment. 
- Click on your personal github repository for the assignment.
- Login in Repls https://replit.com/repls and then create a new replit by importing from github repository.
- You'll work with a partner to complete this recitation. To do so, we'll break you into Zoom rooms. You will be able to code together in the same `repl.it` instance. You can choose whose repl.it instance you will share. This person will click the "Share" button in their repl.it instance and email the lab partner.
- Make sure the dependencies are installed. Please use 'pip install -r requirements.txt'.
py
## Running and testing your code
- In the command-line window, run `./ipy` to launch an interactive IPython shell. This is an interactive shell to help run and debug your code. Any code you change in `main.py` will be reflected from this shell. So, you can modify a function in `main.py`, then test it here.
  + If it seems things don't refresh, try running `from main import *`
- You can exit the IPython prompt by either typing `exit` or pressing `ctrl-d`
- To run tests, from the command-line shell, you can run
  + `pytest main.py` will run all tests
  + `pytest main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Version Control" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [ ] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [ ] 2. Test that your function is correct by calling from the command-line `pytest main.py::test_binary_search`

- [ ] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [ ] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`?

**The worst case input value of 'key' for binary search would be a key that is not on the list, as it would have to run binary search until the size of the list is 1, and then check to see if that last value is equivalent to the key**

- [ ] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`? 

**The best case scenario for 'key' would be if they key was right in the middle of the list, as binary search checks the middle of the list first**

- [ ] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [ ] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest main.py::test_compare_search`, which contains some simple checks.

- [ ] 8. Call `print_results(compare_search())` and paste the results here:

**
|            n |   linear |   binary |
|--------------|----------|----------|
|       10.000 |    0.004 |    0.005 |
|      100.000 |    0.011 |    0.005 |
|     1000.000 |    0.110 |    0.011 |
|    10000.000 |    1.150 |    0.010 |
|   100000.000 |   12.987 |    0.033 |
|  1000000.000 |  331.839 |    0.042 |
| 10000000.000 | 2752.812 |    0.035 |
**

- [ ] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

**The theoretical running times do match my empirical results for linear search. We can see as the input size for linear search increases by a factor of 10, the running time also roughly increases by a factor of 10, which matches the O(n) running time. However The empirical results for Binary search are even faster than I would have guessed. I'm particularly surprised by the sizes n = 100000 and n = 1000000, as n = 1000000 ran faster, which surprised me**

- [ ] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times. 
  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search? **O(kn) (number of times we search the list * worst case scenario runtime of linear search)**
  + For binary search? **O(n^2)+ O(klog(n)) ~= O(n^2) (time it takes to sort the list plus number of times we have to run binary search. I'm assuming we only need to sort the list once)**
  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting? **k>n**
