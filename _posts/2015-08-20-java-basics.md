---
layout: post
title: "Java Basics - my cheeting sheet"
date: 2015-08-20
---

## Map
### 1. Declaration and Initialization

```java
    private static final Map<Character, Character> map = new HashMap<Character, Character>(){
            {
                put('(', ')');
                put('[', ']');
                put('{', '}');
                put('key', 'value');
            }
    };
```
### 2. loop keySet(), valueSet(), EntrySet()
```java
    Map<String, Object> map = ...;
    
    for (String key : map.keySet()) {
        // ...
    }
    
    for (Object value : map.values()) {
        // ...
    }
    
    for (Map.Entry<String, Object> entry : map.entrySet()) {
        String key = entry.getKey();
        Object value = entry.getValue();
        // ...
    }
```
## Character
```java
    Character.isLetterOrDigit();
    Character.toLowerCase();
```

## Bit Manipulation
```java
    &   // bitwise AND
    ^   // bitwise exclusive OR, boolean exclusive OR 
    |   //  bitwise inclusive OR
    >>  // signed right shift
    >>> // unsigned right shift
    -a == ~(a - 1) = true
```

## StringBuilder

```java
    deleteCharAt(index)
```

## Comparator & Comparable
```java
    public Comparator<Integer> comparator = new Comparator<Integer>(){
         @Override
         public int compare(Integer num1, Integer num2){
             String str = "";
             return (str+num2+num1).compareTo(str+num1+num2);
          }
    };
    
    // comparator ---> compareTo()
    // comparable ---> compare()
```

## String
```java
    String str = new String(char[]);
```

## TreeSet
```java
    TreeSet<Integer> treeSet = new TreeSet<Integer>();
    treeSet.floor(E e);
    treeSet.ceiling(E e);
```
## Deque
```java
   Deque<Integer> q = new ArrayDeque<>();
   q.peek();
   q.peekLat();
   q.poll();
   q.offer(Integer e);
```
## Priority Queue
```java
   PriorityQueue<Integer> q = new PriorityQueue<>(k, comparator);
   q.peek();
   q.poll();
   q.offer(Integer e);
   q.remove();
```

## Iterator
```java
    public class MyCollection<E> implements Iterator<E>{
        public Interator<E> iterator(){
            return new MyIterator<E>();
        }
    }
    
    public class MyIterator<T> implements Iterator<T>{
        public boolean hasNext(){
            // implement...
        }
        
        public T next(){
            // implement...
        }
    }
    // how to use 
    public static void main(String[] args){
        MyCollection<String> stringCollection = new MyCollection<String>();
        for(String string : stringCollection){
        
        }
    }
    
```
