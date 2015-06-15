# Algorithm-with-Swift

#### What is Algoritm ?

An algorithm is a way of solving WELL-SPECIFIED computation problems. It is also described as a finite set of rules that gives a sequence of operations for solving the problems.


#### Euclid's Algorithm:

Used to find Greatest Common Diviser (GCD). For instance if we have 'm' and 'n' in which m > n. We should find m divide by n and let the reminder be r. If r = 0 the 'n' is GCD. But if 'r' is not 0 we use recuirsion in way m -> n and n -> r and start the devision again until the r = 0.
```
    func findReminder (m: Int, var n:Int) -> Int {
      let r:Int =  m % n
        
      if r != 0 {
          n = findReminder(n, r)
      }
        
      return n
    }
      
    println(findReminder(210,8))
```

#### Why should we use Algorithm ?
  * it gives us estimated time of running an operation. 
  * require amount of cpu or gpu to do a task
  * Is the task feasible to do
  * Improvement is never ending process

#### Data structure
  Data structure are part of the algorithm context. Data structure descirbes the way of storing data.

#### Time comlpaxity:
  When we do an operation using algorithm, to check the time complaxity we consider the worst case scenario for an algorithm. To calculate the unit time we need to remember each memory access consider as 1 unit time and each operation (+,-,/,%,*) also consider as 1 unit time.
  
  To understand Better we are going to sort an array using Bubble sort. 
```  
    Array : [9,8,7,2,1]    // this is a reverse sort array, which means it is the worst case for sorting using bubble.
    
    Step 1) Comparing 9,and 8, and using temp data for 8, and setting swapping data. Comparison: 1, Swapping: 3 = 4 time units
    
    we continue doing till we finish going through this array.

        Comparison | Swapping
            1      |    3
            1      |    3
            1      |    3
            1      |    3
        ----------------------
                   16

    step 2) going to the list [8,7,2,1,9] but not comparing the last item.              

        Comparison | Swapping
            1      |    3
            1      |    3
            1      |    3
        ----------------------
                   12

    step 3) going to the list [7,2,1,8,9] but not comparing the last 2 items.           
    
        Comparison | Swapping
            1      |    3
            1      |    3
        ----------------------
                   8

    step 4) going to the list [2,1,7,8,9] but not comparing the last 3 items.           

        Comparison | Swapping
            1      |    3
        ----------------------
                   4

    Whole sorting algorithm takes = 16 + 12 + 8 + 4
                                    4 x (4 + 3 + 2 + 1)
                                    
                                    4 x (n-1, n-2, ..., 3+2+1)

                                    2 x n x (n-1)

                                  = pn^2 + qn + r   , (p,n,r are constants)
```

#### Sorting
The randomArray is an array with unsorted numbers. We will be using the same array for all testing purposes.
```
    let randomArray = [7,5,8,3,14,6,1]
```

##### Bubble sort:
In bubble sort items are sorted gradually. The sorting algorithm works in a way by repeatedly stepping through lists that needs to be sorted.

  * Start from left side of array
  * Compare two block items from left, for instance item in index 0 and index 1
  * if item in index 0 is bigger than item in index 1, then we swap them
  * repeat the same step with next two blocks, which are item index 1 and item index 2
  * by doing this way, the biggest number will go to the right side
  * After reaching to the end of the array, we go back to the first item and follow above step, but we remove checking the last item of the array. Imagine everytime you go through the array you put a pointer or sticker at the last array item. And each time going through the array, we keep bringing the sticker 1 item back.

```
    func sortArrayWithBubble(var myArray: [Int]) -> [Int]{
      let startTime = CFAbsoluteTimeGetCurrent()
      
      for i in 0..<myArray.count-1 {
        for j in 0..<myArray.count-1-i {
          if myArray[j] > myArray[j+1]{
              let temp:Int = myArray[j+1]
              myArray[j+1] = myArray[j]
              myArray[j] = temp
          }
        }
      }
      
      println(CFAbsoluteTimeGetCurrent() - startTime)     // get the elapsed time
      return myArray
    }
      
    sortArrayWithBubble(randomArray)
```

##### Selection sort:
In selection sort we look for smallest item in array and swap them one by one to left item of arrays.

  * We go through the array and find the smallest value
  * Then we swap it with the the first item of the array
  * We put it a pointer or sticker and we move on looking for items starting from 2nd item. 
  * we follow above step but with ignoring the first item. When we found the smallest number we swap it with the 2nd item of the array. Now we move on 3rd item. This will go on and on until we finish sorting.

```
    func sortArrayWithSelection(var myArray: [Int]) -> [Int]{
      let startTime = CFAbsoluteTimeGetCurrent()
      
      for i in 0..<myArray.count-1 {
        var minIndex: Int = i
        for j in i+1..<myArray.count {
          if myArray[j] < myArray[minIndex]{
              minIndex = j
          }
        }
        
        let temp:Int = myArray[minIndex]
        myArray[minIndex] = myArray[i]
        myArray[i] = temp
      }
      
      println(CFAbsoluteTimeGetCurrent() - startTime)     // get the elapsed time
      return myArray
    }
    sortArrayWithSelection(randomArray)
```

##### Insertion Sort:
```
    func sortArrayWithInsertion(var myArray: [Int]) -> [Int]{
      let startTime = CFAbsoluteTimeGetCurrent()
      
      for i in 1..<myArray.count {
        var current = myArray[i]
        var j = i - 1
        
        while j >= 0 && myArray[j] > current{
            myArray[j+1] = myArray[j]
            j = j - 1
        }
        
        myArray[j+1] = current
      }
      
      println(CFAbsoluteTimeGetCurrent() - startTime)     // get the elapsed time
      return myArray
    }
      
    sortArrayWithInsertion(randomArray)
```
