# Week 3 Lab Report

## Part 1 : Search Engine
*Below is the code for the search engine I built*
```
import java.io.IOException;
import java.net.URI;
import java.util.*;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    int num = 0;
    List<String> list = new ArrayList<String>();
    List<String> retList = new ArrayList<String>();

    public String handleRequest(URI url) {

        if (url.getPath().contains("/add")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                list.add(parameters[1]);

            }
            return (parameters[1] + " " + "has been added to the list");

        }
        if (url.getPath().contains("/search")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                for (String str : list) {
                    if (str.contains(parameters[1])) {
                        retList.add(str);

                    }

                }
                return retList.toString();

            }

        }
        return "404 Not Found!";

    }
}

class SearchEngine {
    public static void main(String[] args) throws IOException {
        if (args.length == 0) {
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
**Here are few images of how the search engine works**\
![Image](https://cdn.discordapp.com/attachments/891952727641456661/1030527394794197113/unknown.png)\
In the above image, the `handleRequest(URI url)` method is called. The value of the argument is decided by the Server Class which has the `start()` method. The value of the `URI url` also depends upon the number we enter as the argument. In this case,we pass 4000 as the argument and we can see the number in our `URL`. Also, when the method checks for `add` and `search` it finds neither of them and hence returns `404 Not Found!`\
![Image](https://cdn.discordapp.com/attachments/891952727641456661/1030527396127985724/unknown.png)\
Now, when we change the `URL` to http://localhost:4000/add?s=apple, we see that the first `if` case in my code is implemented. It searches for `add` in the `query` and finds it. It creates an array of Strings which are present before and after the `=`. It adds the string present after the `=` to the array which would store all the `Strings` the users add. As a result of this implementation, the `String` **apple** is added to the array. We can add other `Strings` to this array in the same way  \
![Image](https://cdn.discordapp.com/attachments/891952727641456661/1030527396539011102/unknown.png)\
Now when we change the `URL` to http://localhost:4000/search?s=app, we see that the second `if` case in my code is implemented. It searches for `search` in the query and finds it. It creates an array of Strings which are present before and after the `=`. It goes through the list of `Strings` entered by the user and checks if the substring is present in any of the `Strings` in the list. If the substring is present in any of the `Strings` in the list, it adds that particular `String` to the `list` to be returned. As we cannot return a list, we use the `toString()` method in order to print out the `Strings` which contain the `substring` entered by the user.

*The Search Engine supports a path for adding a new string to the list, and a path for querying the list of strings and returning a list of all strings that have a given substring.*


## Part 2
**Array Methods** \
The first method we will be looking at is the `reverseInPlace()`\
*This is the failure-inducing input:*
```
 @Test
  public void testReversedWith4Elements() {
    int[] input = { 2, 3, 4, 5 };
    ArrayExamples.reverseInPlace(input);
    assertArrayEquals(new int[] { 5, 4, 3, 2 }, input);
  }
  ```
*This is the symptom:*\
![Image](https://media.discordapp.net/attachments/891952727641456661/1030667265022111874/unknown.png)

*This is the code fix required:*
```
// Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    int value = 0;
    for (int i = 0; i < arr.length / 2; i += 1) {
      value = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = value;

    }
  }

```
In the inital buggy code, the implementation is only able to change the values of the array halfway through. For example, if we take the array : {1,2,3,4} and implement this method on the given array, we would get something like this\
```
arr[0]=arr[3]=4
arr[1]=arr[2]=3
arr[2]=arr[1]=3
arr[3]=arr[0]=4
```
As we can see, the implementation fails to change the value of `arr[2]` and `arr[3]`. The code fails to take into record the change in the values of `arr[0]` and `arr[1]` and hence, the code is buggy.

**The second method we will be looking at is the `reversed(arr[])`**

*The failure inducing input is:*
```
@Test
  public void testReversedWith3Elements() {
    int[] input = { 1, 5, 4 };
    assertArrayEquals(new int[] { 4, 5, 1 }, ArrayExamples.reversed(input));

  }
  ```
  *The symptom:*
  ![Image](https://media.discordapp.net/attachments/891952727641456661/1030674392394514442/unknown.png)

  *Here is how to fix the code*
  ```
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];

    for (int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
      

    }
    return newArray;
  }

```

In the initial code, it returns the old array instead of the new array. We just got to change the `return` statement in the initial code to `return newArray`. Hence, the method returns the initial array instead of the new array.














