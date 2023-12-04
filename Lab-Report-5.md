# Lab Report 5

### Part 1

- ***The original post from a student***

  ![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/9a866b26-a21b-4577-8463-79c67bf5ab61)

Hi instructors, 

While I was trying to run the JUnit tests, I encountered an issue. Based on my understanding from the messages, something around line 42 of the ListExamples.java file caused my test on the `merge` function from ListExamplesTests.java to time out after 500 milliseconds. I tried to figure the bug out but could not. Can you help me with what is happening?

The failure-inducing input:

```
@Test(timeout = 500)
        public void testMerge2() {
		        List<String> l1 = new ArrayList<String>(Arrays.asList("a", "b", "c"));
		        List<String> l2 = new ArrayList<String>(Arrays.asList("c", "d", "e"));
		        assertArrayEquals(new String[]{ "a", "b", "c", "c", "d", "e" }, ListExamples.merge(l1, l2).toArray());
         }
```

- ***The response from a TA***

  Hello,
  You are right. Using JUnit testing to identify the location of bugs is important. It helps us minimize the time it takes to fix bugs. With this time-out issue, I recommend you check your logic. You can use `jdb` to debug and stop at the desired position as the professor mentioned in the course. You can use `step` to run to the next line.


- ***Student's implementation***

 ![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/c7bb6fb0-e862-497e-80f7-d5472a9d6ace)

![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/88b7aca6-eed4-4117-9916-b8e73c1235d3)

![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/16139fd4-185a-4508-b82d-c740dc79fbd6)

![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/178a86b8-f13e-4e96-ba6a-0615fbf937ee)

Following TA's instructions, I found the bug in my code. Since I was new to using `jdb`, I forgot to use it while trying to figure out how to solve this issue. `jdb` really worked in my case. Instead of reading the code and running it manually to see where the code has bugs, `jdb` helped me stop where I wanted to during the bugging process and then run it step by step. In each steps, I can control the values of index1 and index2 variables by printing their values. This made me realize that index2 had not changed throughout the loop. But the condition for the loop to end is that index2 is greater than or equal to the size of list2. This means my code will never stop because my index2 is constant so index2=1 is always smaller than the size of list2.

- ***all the information needed***

The file & directory structure needed:

![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/44486573-d819-42c1-937b-00f43713438f)


The contents of each file before fixing the bug:

**test.sh**

```
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
```

**ListExamples.java**

```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }


  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index1 += 1;
    }
    return result;
  }


}
```

**ListExamplesTests.java**

```
import static org.junit.Assert.*;
import org.junit.*;
import java.util.*;
import java.util.ArrayList;


public class ListExamplesTests {
	@Test(timeout = 500)
	public void testMerge1() {
    		List<String> l1 = new ArrayList<String>(Arrays.asList("x", "y"));
		List<String> l2 = new ArrayList<String>(Arrays.asList("a", "b"));
		assertArrayEquals(new String[]{ "a", "b", "x", "y"}, ListExamples.merge(l1, l2).toArray());
	}
	
	@Test(timeout = 500)
        public void testMerge2() {
		List<String> l1 = new ArrayList<String>(Arrays.asList("a", "b", "c"));
		List<String> l2 = new ArrayList<String>(Arrays.asList("c", "d", "e"));
		assertArrayEquals(new String[]{ "a", "b", "c", "c", "d", "e" }, ListExamples.merge(l1, l2).toArray());
        }

}
```

The full command line (or lines) you ran to trigger the bug:

	```
	bash test.sh
	```

The content of files after fixing the bugs:

In the file **ListExamples.java**, start at line 42:

```
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index2 += 1;
    }

```

Because index2 always is 1, the loop's condition is always true. So the loop never stops. This causes a bug and causes the test to time out. Also `index1 +=1` has no meaning in this loop. But if it's `index2 +=1`, it actually makes sense: Every time a loop occurs, index2 is incremented by 1, until it no longer satisfies the loop's condition, and the loop automatically ends. So in line 43 of file `ListExamples.java`, I changed `index1` to `index2`

### Part 2

I learned a lot of new things like `.sh`, vim,... But the thing that interested me the most was the `jdb` command. Before taking this course, many people suggested to me to use Visual Studio Code. But I didn't use it even though it could minimize my computer's memories. I have always chosen to use IDEs like Visual Studio Community even though they take up a lot of space on my computer because of their convenience, such as the ability to stop at a line that I want and run step by step. But `jdb` helped me do it on Visual Studio Code. JUnit tests also show where bugs appear. So far,  I can use Visual Studio Code easily. Therefore, this course taught me a lot of new knowledge and I really appreciate it.
