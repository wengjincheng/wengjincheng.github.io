---
title: Priority queue
published: 2025-03-23
description: ''
image: './pic-priorityqueue.webp'
tags: ['Heap', 'Priority queue', 'Array', 'JavaScript', 'Algorithm']
category: 'Algorithm'
draft: false 
---

*Everytime I met the LeetCode question which need Heap Structure or specific of Priority, I just have difficulties to implement this data structure ASAP, because of it's complexity. So, Let me complete it once and use it for future!*

### The Priority Queue Algorithm implement by JavaScript

``` javascript

// The Priority Queue class

class PriorityQueue {
    constructor(comparator = (a, b) => a > b) {
        this.heap = [null] // the heap implement by array
        this.comparator = comparator // custom compare function
    }

    // add element
    enqueue(value) {
        this.heap.push(value)
        this._bubbleUp(this.size())
    }

    // delete element
    dequeue() {
        if (this.isEmpty()) {
            throw new Error('Priority queue is empty')
        }

        const root = this.heap[1]
        const last = this.heap.pop()

        if (this.size() > 0) {
            this.heap[1] = last
            this._sinkDown(1)
        }

        return root
    }

    // get numbers of elements of heap
    size() {
        return this.heap.length - 1
    }

    // check empty
    isEmpty() {
        return this.size() === 0
    }

    // clear
    clear() {
        this.heap = [null]
    }

    // check next element which can be put out
    peek() {
        if (this.isEmpty()) {
            throw new Error('Priority queue is empty')
        }
        return this.heap[1]
    }

    // ------- private functions ---------
    
    _bubbleUp(index) {
        while (index > 1) {
            const parentIndex = Math.floor(index / 2)
            
            if (this._compare(parentIndex, index)) {
                break
            }

            this._swap(parentIndex, index)
            index = parentIndex
        }
    }

    _sinkDown(index) {
        const lastIndex = this.size()

        while (true) {
            let targetIndex = index
            const leftChild = 2 * index
            const rightChild = 2 * index + 1

            // check whether swap left child
            if (leftChild <= lastIndex && this._compare(leftChild, targetIndex)) {
                targetIndex = leftChild
            }

            // check whether swap right child
            if (rightChild <= lastIndex && this._compare(rightChild, targetIndex)) {
                targetIndex = rightChild
            }

            if(targetIndex === index) {
                break
            }

            this._swap(index, targetIndex)
            index = targetIndex
        }
    }

    // compare the priority of i and j
    _compare(i, j) {
        return this.comparator(this.heap[i], this.heap[j])
    }

    // swap i and j
    _swap(i, j) {
        [this.heap[i], this.heap[j]] = [this.heap[j], this.heap[i]]
    }
}

export default PriorityQueue
```

``` javascript

// index.js

const maxQueue = new PriorityQueue((a, b) => a < b);
maxQueue.enqueue(3);
maxQueue.enqueue(5);
maxQueue.enqueue(1);
console.log(maxQueue.dequeue()); // 1
console.log(maxQueue.dequeue()); // 3
console.log(maxQueue.dequeue()); // 5

```


