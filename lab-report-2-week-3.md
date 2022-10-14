# Part 1

*Below is the Code for the Simplest Search Engine:*

![Image](/w2assets/wavecode1.png)
![Image](/w2assets/wavecode2.png)

*Showing an add*
![Image](/w2assets/waveadd.png)

*Showing various queries*
![Image](/w2assets/wavequery.png)
![Image](/w2assets/wavequery2.png)

# Part 2

## Bug 1: Reverse (ArrayExamples.java)

Failure-Inducing Input: any non-empty array (e.g ``{1,2,3,4,5}`` )

Symptom: Any non-empty array will return as an array filled with 0's of the same length

The bug: We are instantiating a new array without declaring anything within it. When we try to assign the input array based on the contents of that new array, we just fill up the input array with 0's. 

Below is the code fix needed:

![Image](/w2assets/lab3code.png)

## Bug 2: Append (LinkedListExample.java)

Failure-Inducing Input: Any append past 2 elements

Symptom: There is an indefinite loop

The bug: We are making another Node and attaching it to the end of the linked list before the next loop occurs, meaning that the next Node will *never* be null

Below is the code fix needed:

* note: the "next: null" is a feature from IntelliJ to visualize method inputs (it's not a part of the code)

![Image](/w2assets/lab3code2.png)