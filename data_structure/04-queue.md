# Queue

### Implementasi Queue di Java

Created by [Fahri Firdausillah](http://fahrifirdaus.web.id)

---

### Basic Queue

Queue is a data structure to 

---

# 3 Alternatives of Queue Algorithm

---

### 1st Alternative

- ```isEmpty()```: when the last index value = -1
- ```isFull()```: when the last index value = array.length - 1
- ```isOneElement()```: when the last index value = 0

-- 

### 1st Alternative cont'd

- ```add()```: increase the value of last index by 1, then insert the
  value into array[index]
- ```remove()```: decrease the value of the last index by 1, shift all
  of array values into an index before them, then return the removed value

---

### 2nd Alternative

- ```isEmpty()```: when the first and last index value = -1
- ```isFull()```: when the last index value = array.length - 1
  and the first index value = 0
- ```isOneElement()```: when the value of last = first
- ```semiFull()```*: when the last index value = array.length - 1
  and the first index value != 0

--

### 2nd Alternative cont'd

- ```add()```: 
  - if empty increase the value of last and first index by 1
  - if not semi full increase the value of the last index by 1
  - if semi full shift all data into the empty slots, then
    increase the valuo of last index by 1
  - then increase the value of the last index by 1 and insert
    the value into array[last]
- ```remove()```:
  - if is one element set the value of the first and last index into -1
  - then increase the value of the first index by 1 and return the 
    removed value
    
---

### 3rd Alternative

- ```isEmpty()```: when the first and last index value = -1
- ```isFull()```: 
  - when the last index value = array.length - 1 and the first index value = 0
  - when first - last = 1
- ```isOneElement()```: when the value of last = first
- ```semiFull()```*: when the last index value = array.length - 1
  and the first index value != 0
  
--

### 3rd Alternative cont'd

- ```add()```: 
  - if empty increase the value of last and first index by 1
  - if not semi full increase the value of the last index by 1
  - if last = array.length - 1 set the value of last index to -1
  - then increase the value of the last index by 1 and insert
    the value into array[last]
- ```remove()```:
  - if is one element set the value of the first and last index into -1
  - if first = array.length - 1, set the value of first index to -1
  - then increase the value of the first index by 1 and return the 
    removed value

---

# Queue Implementations

---
