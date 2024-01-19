---
layout: project
type: project
image: img/70d6f4e10e2badb5ef394f00c17ad2bc1c14f6e7.jpg
title: "Sentence to Alphabetically Sorted"
date: 2023
published: true
labels:
  - Java
summary: "A Java program created by me for ICS 211 that takes a sentence and sorts the characters used in alphabetical order"
---

This java project is one of the many projects I had create during ICS 211. It is a converter that takes Strings/sentences and sorts the characters used in the string alphabetically. Though the code is nothing too complicated it is still one that should be noted for its significance as it can be used, if needed, in a vital way.

Within this code it does this sorting method through selection sort, bubble, insertion, and a case called "SelectUnique" which prints out the characters used in the string while never reapeating a character that has already been used.

```
public class hw04 {

  enum SortType {
    SelectionSort,
    SelectUnique,
    BubbleSort,
    InsertionSort,
  };

  private static void swap(char[] a, int i1, int i2) {
    // student must implement
	// Swaps the elements at indices i1 and i2 in the array a
	char temp = a[i1];
	a[i1] = a[i2];
	a[i2] = temp;
  }

  static void selectionSort(char[] a) {
    // student must implement
	// Sorts the array a using the Selection Sort algorithm
	int n = a.length;
	for (int i = 0; i < n-1; i++) {
		int minIndex = i;
		// Find the index of the minimum element in the unsorted part of the array
	    for (int j = i+1; j < n; j++) {
	    	if (a[j] < a[minIndex]) {
	        minIndex = j;
	      }
	    }
	 // Swaps the minimum element with the first element of the unsorted part
	    swap(a, i, minIndex);
	  }
	  
  }

  // This is basically like selection sort, but only returns unique elements
  static String selectUnique(char[] a) {
    // student must implement
	// It removes duplicates and keeps only unique values in the array a
	StringBuilder result = new StringBuilder();
	boolean[] visited = new boolean[256]; // Assuming ASCII characters
	
	for (char c : a) {
	    if (!visited[c]) {
	    // Append the character to the result if it has not been visited before
	      result.append(c);
	      visited[c] = true;
	    }
	  }
 
    return result.toString();
  }

  static void bubbleSort(char[] a) {
    // student must implement
	// Sorts the array a using the Bubble Sort algorithm
	int n = a.length;
	for (int i = 0; i < n-1; i++) {
		for (int j = 0; j < n-i-1; j++) {
			// Compare the adjacent elements and swap them if they are in the wrong order
			if (a[j] > a[j+1]) {
				swap(a, j, j+1);
	      }
	    }
	  }
  }

  static void insertionSort(char[] a) {
    // student must implement
	// Sorts the array a using the Insertion Sort algorithm
	int n = a.length;
	for (int i = 1; i < n; i++) {
	    char key = a[i];
	    int j = i - 1;
	    // Shift elements greater than the key to the right
	    while (j >= 0 && a[j] > key) {
	      a[j+1] = a[j];
	      j--;
	    }
	    // Place the key in its correct position
	    a[j+1] = key;
	  }
  }

  static String sortChars(String s, SortType sort) {
	// Sorts the characters in the string s based on its specified sort algorithm
    char[] a = s.toCharArray();
    switch (sort) {
    case SelectionSort:
      selectionSort(a);
      break;
    case BubbleSort:
      bubbleSort(a);
      break;
    case InsertionSort:
      insertionSort(a);
      break;
    case SelectUnique:
      return selectUnique(a);
    }
    return new String(a);
  }

  public static void main(String[] a) {
    if ((a == null) || (a.length < 1)) {
      a = new String[1];
      a[0] = "the quick brown fox jumps over the lazy dog";
    }
    for (String s: a) {
      System.out.println("'" + s + "' selection sorts to '" +
                         sortChars(s, SortType.SelectionSort) + "'");
      System.out.println("'" + s + "'    bubble sorts to '" +
                         sortChars(s, SortType.BubbleSort) + "'");
      System.out.println("'" + s + "' insertion sorts to '" +
                         sortChars(s, SortType.InsertionSort) + "'");
      System.out.println("'" + s + "' has characters '" +
                         sortChars(s, SortType.SelectUnique) + "'");
    }
  }
}

```
