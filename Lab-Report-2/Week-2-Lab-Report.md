# **Week 2 Lab Report**
## **_Part 1_**
**Code for StringServer.java**
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String wordsString = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return wordsString;
        } else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    wordsString += parameters[1] + '\n';
                    return wordsString;
                }
            }
            return "404 Not Found!";
        }
    }
}

class StringServer {
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

| **Wesbsite Url & Screenshot**    | **Description** |
| ----------- |----------- |
| `http://localhost:8008/add-message?s=hello there`<br><img src=Lab-Report-2-Photos/Lab-Report-First_Message.png height = "auto" width="2000">|The `class StringServer` method is called when first running the program in which it takes the command line argument of 8008 and turns it from a String to an int value as the port number. As you click on the link for the website and type in `/add-message?s=hello there` at the end of the `localhost:8008` url, the `class Handler implements URLHandler` method takes in that input, adds the `hello there` part of query to an array called `String[] parameters`, adds that string to the `String wordsString` variable with adding a `\n` (newline) and lastly returning the variable `wordsString`.|
| `http://localhost:8008/add-message?s=bye bye` <br> <img src=Lab-Report-2-Photos/Lab-Report-Second-Message.png height = "auto" width="2000">|`public String handleRequest(URI url)` is called with it taking the url `http://localhost:8008/add-message?s=bye bye` and having the `bye bye` part of the query added to the variable `wordString`. The value of the `int port` isn't changed because the `class StringServer` method isn't being called.|

## **_Part 2_**
**Chosen faulty method from the ArrayExamples.java file :**
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for (int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
**A failure-inducing input for the buggy program :**
```
@Test
  public void testReversedMultiple() {
    int[] input1 = { 3, 2, 1 };
    assertArrayEquals(new int[] { 1, 2, 3 }, ArrayExamples.reversed(input1));
  }
  ```
**An input that doesn’t induce a failure :**
```
@Test
  public void testReversed() {
    int[] input1 = {};
    assertArrayEquals(new int[] {}, ArrayExamples.reversed(input1));
  }
 ```
 **Symptom of faulty program :**
 <img src=Lab-Report-2-Photos/Lab-Report-2-Symptom.png>
 
 | **Before**      | **After** |
| ----------- | ----------- |
| <pre>static int[] reversed(int[] arr) {<br>  int[] newArray = new int[arr.length];<br>  for(int i = 0; i < arr.length; i += 1) {<br>    <ins>arr[i] = newArray[arr.length - i - 1];</ins><br> }<br> return arr;<br>}| <pre>static int[] reversed(int[] arr) {<br> int[] newArray = new int[arr.length];<br> for (int i = 0; i < arr.length; i += 1) {<br>   <ins>newArray[i] = arr[arr.length - i - 1];</ins><br> }<br> return newArray;<br>}      |
| `arr[i] = newArray[arr.length - i - 1];` is the bug because it tries to assign values of the array `int[] newArray` but its newly created meaning that all its values are 0.  | Now this addresses the issue by having the newly created array `int[] newArray` as the one that have values being inputted in it with it taking in values from the original array `int[] arr`. Also, now instead of `return arr` its now `return newArray` for its a new array that is being returned.    |

## **_Part 3_**
During Lab 2, I learned how to fork code from Github into my own computer, edit that code using VScode, and save the changes to my own Github account. Also, during that same lab I learned how to create my own server and learned that you can change the url of a website to change contents of the page you're viewing. During Lab 3, I learned how to ultize Junit to find the symptom of a bug in one of your methods and to take that knowledge and try and fix the bugs in the method to make it run as you want it to.
