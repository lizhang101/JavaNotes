## General

![hierarchy of collection framework](https://www.javatpoint.com/images/collection-hierarchy.png)

| No.  | Method                                   | Description                              |
| ---- | ---------------------------------------- | ---------------------------------------- |
| 1    | public boolean add(Object element)       | is used to insert an element in this collection. |
| 2    | public boolean addAll(Collection c)      | is used to insert the specified collection elements in the invoking collection. |
| 3    | public boolean remove(Object element)    | is used to delete an element from this collection. |
| 4    | public boolean removeAll(Collection c)   | is used to delete all the elements of specified collection from the invoking collection. |
| 5    | public boolean retainAll(Collection c)   | is used to delete all the elements of invoking collection except the specified collection. |
| 6    | public int size()                        | return the total number of elements in the collection. |
| 7    | public void clear()                      | removes the total no of element from the collection. |
| 8    | public boolean contains(Object element)  | is used to search an element.            |
| 9    | public boolean containsAll(Collection c) | is used to search the specified collection in this collection. |
| 10   | public Iterator iterator()               | returns an iterator.                     |
| 11   | public Object[] toArray()                | converts collection into array.          |
| 12   | public boolean isEmpty()                 | checks if collection is empty.           |
| 13   | public boolean equals(Object element)    | matches two collection.                  |
| 14   | public int hashCode()                    | returns the hashcode number for collection. |

### Iterator interface

1. **public boolean hasNext()** it returns true if iterator has more elements.
2. **public object next()** it returns the element and moves the cursor pointer to the next element.
3. **public void remove()** it removes the last elements returned by the iterator. It is rarely used.

## ArrayList

![Java ArrayList class hierarchy](https://www.javatpoint.com/images/arraylist.png)

| Constructor             | Description                              |
| ----------------------- | ---------------------------------------- |
| ArrayList()             | It is used to build an empty array list. |
| ArrayList(Collection c) | It is used to build an array list that is initialized with the elements of the collection c. |
| ArrayList(int capacity) | It is used to build an array list that has the specified initial capacity. |

| Method                                  | Description                              |
| --------------------------------------- | ---------------------------------------- |
| void add(int index, Object element)     | It is used to insert the specified element at the specified position index in a list. |
| boolean addAll(Collection c)            | It is used to append all of the elements in the specified collection to the end of this list, in the order that they are returned by the specified collection's iterator. |
| void clear()                            | It is used to remove all of the elements from this list. |
| int lastIndexOf(Object o)               | It is used to return the index in this list of the last occurrence of the specified element, or -1 if the list does not contain this element. |
| Object[] toArray()                      | It is used to return an array containing all of the elements in this list in the correct order. |
| Object[] toArray(Object[] a)            | It is used to return an array containing all of the elements in this list in the correct order. |
| boolean add(Object o)                   | It is used to append the specified element to the end of a list. |
| boolean addAll(int index, Collection c) | It is used to insert all of the elements in the specified collection into this list, starting at the specified position. |
| Object clone()                          | It is used to return a shallow copy of an ArrayList. |
| int indexOf(Object o)                   | It is used to return the index in this list of the first occurrence of the specified element, or -1 if the List does not contain this element. |
| void trimToSize()                       | It is used to trim the capacity of this ArrayList instance to be the list's current size. |

| Method                                 | Description                              |
| -------------------------------------- | ---------------------------------------- |
| void add(int index,Object element)     | It is used to insert element into the invoking list at the index passed in the index. |
| boolean addAll(int index,Collection c) | It is used to insert all elements of c into the invoking list at the index passed in the index. |
| object get(int index)                  | It is used to return the object stored at the specified index within the invoking collection. |
| object set(int index,Object element)   | It is used to assign element to the location specified by index within the invoking list. |
| object remove(int index)               | It is used to remove the element at position index from the invoking list and return the deleted element. |
| ListIterator listIterator()            | It is used to return an iterator to the start of the invoking list. |
| ListIterator listIterator(int index)   | It is used to return an iterator to the invoking list that begins at the specified index. |

## ArrayList

![Java LinkedList class hierarchy](https://www.javatpoint.com/images/linkedlist.png)

## List Interface

| Method                                 | Description                              |
| -------------------------------------- | ---------------------------------------- |
| void add(int index,Object element)     | It is used to insert element into the invoking list at the index passed in the index. |
| boolean addAll(int index,Collection c) | It is used to insert all elements of c into the invoking list at the index passed in the index. |
| object get(int index)                  | It is used to return the object stored at the specified index within the invoking collection. |
| object set(int index,Object element)   | It is used to assign element to the location specified by index within the invoking list. |
| object remove(int index)               | It is used to remove the element at position index from the invoking list and return the deleted element. |
| ListIterator listIterator()            | It is used to return an iterator to the start of the invoking list. |
| ListIterator listIterator(int index)   | It is used to return an iterator to the invoking list that begins at the specified index. |

### ListIterator

| Method                | Description                              |
| --------------------- | ---------------------------------------- |
| boolean hasNext()     | This method return true if the list iterator has more elements when traversing the list in the forward direction. |
| Object next()         | This method return the next element in the list and advances the cursor position. |
| boolean hasPrevious() | This method return true if this list iterator has more elements when traversing the list in the reverse direction. |
| Object previous()     | This method return the previous element in the list and moves the cursor position backwards. |

## HashSet

![Java HashSet class hierarchy](https://www.javatpoint.com/images/hashset.png)

| Constructor           | Description                              |
| --------------------- | ---------------------------------------- |
| HashSet()             | It is used to construct a default HashSet. |
| HashSet(Collection c) | It is used to initialize the hash set by using the elements of the collection c. |
| HashSet(int capacity) | It is used to initialize the capacity of the hash set to the given integer value capacity. The capacity grows automatically as elements are added to the HashSet. |

| Method                     | Description                              |
| -------------------------- | ---------------------------------------- |
| void clear()               | It is used to remove all of the elements from this set. |
| boolean contains(Object o) | It is used to return true if this set contains the specified element. |
| boolean add(Object o)      | It is used to adds the specified element to this set if it is not already present. |
| boolean isEmpty()          | It is used to return true if this set contains no elements. |
| boolean remove(Object o)   | It is used to remove the specified element from this set if it is present. |
| Object clone()             | It is used to return a shallow copy of this HashSet instance: the elements themselves are not cloned. |
| Iterator iterator()        | It is used to return an iterator over the elements in this set. |
| int size()                 | It is used to return the number of elements in this set. |

## LinkedHashSet

Maintains insertion order.

## TreeSet

![TreeSet class hierarchy](https://www.javatpoint.com/images/treeset.png)

- Contains unique elements only like HashSet.
- Access and retrieval times are quiet fast.
- Maintains ascending order.

| Constructor              | Description                              |
| ------------------------ | ---------------------------------------- |
| TreeSet()                | It is used to construct an empty tree set that will be sorted in an ascending order according to the natural order of the tree set. |
| TreeSet(Collection c)    | It is used to build a new tree set that contains the elements of the collection c. |
| TreeSet(Comparator comp) | It is used to construct an empty tree set that will be sorted according to given comparator. |
| TreeSet(SortedSet ss)    | It is used to build a TreeSet that contains the elements of the given SortedSet. |

| Method                       | Description                              |
| ---------------------------- | ---------------------------------------- |
| boolean addAll(Collection c) | It is used to add all of the elements in the specified collection to this set. |
| boolean contains(Object o)   | It is used to return true if this set contains the specified element. |
| boolean isEmpty()            | It is used to return true if this set contains no elements. |
| boolean remove(Object o)     | It is used to remove the specified element from this set if it is present. |
| void add(Object o)           | It is used to add the specified element to this set if it is not already present. |
| void clear()                 | It is used to remove all of the elements from this set. |
| Object clone()               | It is used to return a shallow copy of this TreeSet instance. |
| Object first()               | It is used to return the first (lowest) element currently in this sorted set. |
| Object last()                | It is used to return the last (highest) element currently in this sorted set. |
| int size()                   | It is used to return the number of elements in this set. |

## Queue 

| Method                | Description                              |
| --------------------- | ---------------------------------------- |
| boolean add(object)   | It is used to insert the specified element into this queue and return true upon success. |
| boolean offer(object) | It is used to insert the specified element into this queue. |
| Object remove()       | It is used to retrieves and removes the head of this queue. |
| Object poll()         | It is used to retrieves and removes the head of this queue, or returns null if this queue is empty. |
| Object element()      | It is used to retrieves, but does not remove, the head of this queue. |
| Object peek()         | It is used to retrieves, but does not remove, the head of this queue, or returns null if this queue is empty. |

## PriorityQueue Interface

## Deque

offerFirst() and pollLast()

## Map Interface

| Object put(Object key, Object value) | It is used to insert an entry in this map. |
| ------------------------------------ | ---------------------------------------- |
| void putAll(Map map)                 | It is used to insert the specified map in this map. |
| Object remove(Object key)            | It is used to delete an entry for the specified key. |
| Object get(Object key)               | It is used to return the value for the specified key. |
| boolean containsKey(Object key)      | It is used to search the specified key from this map. |
| Set keySet()                         | It is used to return the Set view containing all the keys. |
| Set entrySet()                       | It is used to return the Set view containing all the keys and values. |

Map.Entry Interface
| Method            | Description                 |
| ----------------- | --------------------------- |
| Object getKey()   | It is used to obtain key.   |
| Object getValue() | It is used to obtain value. |

