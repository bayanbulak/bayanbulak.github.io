---
layout: post
title:  "Java Coding Tips"
date:   2024-03-09 17:37:58 +0800
categories: jekyll update tip
---
## Use less target.setXX(source.getXX)
```java
// when you want to use less target.setXX(source.getXX), same name
BeanUtils.copyProperties(source, target)
```
## Manipulate Array
### copy array
```java
//  most efficient(recommend)
void System.arraycopy(int[] srcArr, int srcBeginPos, int[] resArr, int resBeginPos, int length)
  
int[] Arrays.copyOfRange(int[] array, int start, int end)
  
// to increase array size, idle will be fullfilled with 0
int[] Arrays.copyOf(int[] srcArr, int newArrLength)
```
### array -> list
```java
int[] ints = {1,2,3};
List<Integer> list = Arrays.stream(ints).boxed().collect(Collectors.toList());
```
### list -> array

```java
String[] strings = list.stream().toArray(String[]::new);
Array<Integer> list = {0, 1, 2};
int[] array = list.stream().mapToInt(Integer::intValue).toArray()
```
### distinct array
```java
arr = Arrays.stream(arr).distinct().toArray();
```
### sort object array in descending order
```java
Integer[] cubes = new Integer[] { 8, 27, 64, 125, 256 }; 
Arrays.sort(cubes, Collections.reverseOrder());
```
[Read more](https://www.java67.com/2016/07/how-to-sort-array-in-descending-order-in-java.html#ixzz8Greh6ggX)

### sort primitive array in descending order
```java
Arrays.sort(arr);
int n = arr.length;
int temp;
for(int i = 0; i < n/2; i++) {
	temp = arr[i];
	arr[i] = arr[n - i - 1];
	arr[n - i - 1] = temp;
}
```
### Get max/min of an array
```java
Arrays.stream(arr).max().getAsInt();
```
### HashSet to List
```java
Set<Integer> set = new HashSet();
set.add(1);
set.add(2);
List<Integer> list = set.stream().collect(Collectors.toList());
// when specify the type of list use toCollection(ArrayList::new)
set.stream().collect(Collectors.toCollection(ArrayList::new));
```
## Bit Manipulate

get highest int

```java
Integer.highestOneBit(int n);
```

set k-th bit as 0
```java
n = ~ (1 << k) & n;
```

traverse all possibilties of set bits
```java
for (int submask = mask; submask >= 0; submask = (submask - 1) & mask) {
	// do something
}
```