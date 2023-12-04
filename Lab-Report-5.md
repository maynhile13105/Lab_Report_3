# Lab Report 5

### Part 1

- ***The original post from a student***

  ![image](https://github.com/maynhile13105/Lab_Reports/assets/146885739/9a866b26-a21b-4577-8463-79c67bf5ab61)

Hi instructors, 

While I was trying to run the JUnit tests, I encountered an issue. Based on my understanding from the messages, something in line 42 of the ListExamples.java file caused my test to time out after 500 milliseconds. But what happened there? I tried to figure the bug out but could not. Can you help me with what is happening?

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

  

- Student's implementation

- Screenshots
