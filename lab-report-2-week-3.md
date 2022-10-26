# Part 1

*Below is the Code for the Simplest Search Engine:*

```py
import java.io.IOException;
import java.net.URI;
import java.util.*;
class SearchEngineHandler implements URLHandler {
    int num = 0;
    ArrayList<String> items = new ArrayList<String>();
    public String handleRequest(URI url) {
        if (url.getPath().equals("/add")) {
           String[] parameters = url.getQuery().split("=");
           if(parameters[0].equals("s")){
                items.add(parameters[1]);
           }
           return "ITEM ADDED WOOOOOOOOO";
        } else if(url.getPath().contains("/search")){
            String[] parameters = url.getQuery().split("=");
            System.out.println(Arrays.toString(parameters));
           if(parameters[0].equals("s")){
                //SEARCH CODE HERE
                String ot = "";
                for(int i = 0; i < items.size(); i++){
                    if(items.get(i).contains(parameters[1])){
                        ot += items.get(i) + "\n";
                    }
                }
                return ot;
           }
        }
        return "404 not found";
        
    }
}
class SearchEngine{
    public static void main(String[] args) throws IOException {

        int port = 8888;

        Server.start(port, new SearchEngineHandler());
    }
}
```

*Showing an add*
![Image](/w2assets/waveadd.png)
* the code takes the query for s (in this case, `chinesefood`) and returns an Item Added remark. 

*Showing various queries*
![Image](/w2assets/wavequery.png)
![Image](/w2assets/wavequery2.png)

* the code takes in the input for the search via the s query (in the above screenshots, `chinese`, `a`) and searches for any added items that contain those strings.

# Part 2

## Bug 1: Reverse (ArrayExamples.java)
Here is a picture of the method:
![Image](/w2assets/10.251.png)

Failure-Inducing Input: any non-empty array (e.g ``{1,2,3,4,5}`` )

Symptom: Any non-empty array will return as an array filled with 0's of the same length

![Image](/w2assets/10.253.png)

* Here, we see that the first element is 0 when it's supposed to be 5.

The bug: We are instantiating a new array without declaring anything within it. When we try to assign the input array based on the contents of that new array, we just fill up the input array with 0's. 

Below is the code fix needed:

![Image](/w2assets/lab3code.png)

## Bug 2: Append (LinkedListExample.java)
Here is a picture of the method:
![Image](/w2assets/10.252.png)

Failure-Inducing Input: Any append past 2 elements


Symptom: There is an indefinite loop
![Image](/w2assets/10.254.png)
* Java jeap space due to the loop

The bug: We are making another Node and attaching it to the end of the linked list before the next loop occurs, meaning that the next Node will *never* be null

Below is the code fix needed:

* note: the "next: null" is a feature from IntelliJ to visualize method inputs (it's not a part of the code)

![Image](/w2assets/lab3code2.png)