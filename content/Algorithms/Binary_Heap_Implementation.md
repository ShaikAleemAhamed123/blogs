---
title: Binary Heap Implementation
draft: false
---
Steps :

1. Write sift-up function to heapify when an insertion is done.
2. write sift-down function when the extreme element is popped out.

```cpp
//  ------------------------ BINARY HEAP IMPLEMENTATION --------------------------------

#include <bits/stdc++.h>

class MaxHeap {
private:
    std::vector<int> heap;

    // Helper function to restore heap property after insertion
    void heapifyUp(int index) {
        int parent = (index - 1) / 2;
        while (index > 0 && heap[index] > heap[parent]) {
            swap(heap[index], heap[parent]);
            index = parent;
            parent = (index - 1) / 2;
        }
    }

    // Helper function to restore heap property after deletion
    void heapifyDown(int index) {
        int size = heap.size();
        while (true) {
            int largest = index;
            int left = 2 * index + 1;
            int right = 2 * index + 2;

            if (left < size && heap[left] > heap[largest]) {
                largest = left;
            }
            if (right < size && heap[right] > heap[largest]) {
                largest = right;
            }
            if (largest != index) {
                swap(heap[index], heap[largest]);
                index = largest;
            } else {
                break;
            }
        }
    }

public:
    // Insert a new element into the heap
    void insert(int value) {
        heap.push_back(value);
        heapifyUp(heap.size() - 1);
    }

    // Delete the maximum element (root of the heap)
    int deleteMax() {
        if (heap.empty()) {
            throw std::out_of_range("Heap is empty");
        }
        int maxValue = heap[0];
        heap[0] = heap.back();
        heap.pop_back();
        heapifyDown(0);
        return maxValue;
    }

    // Get the maximum element (root of the heap)
    int getMax() const {
        if (heap.empty()) {
            throw std::out_of_range("Heap is empty");
        }
        return heap[0];
    }

    // Return the size of the heap
    int size() const {
        return heap.size();
    }

    // Check if the heap is empty
    bool isEmpty() const {
        return heap.empty();
    }

    // Print the heap elements
    void printHeap() const {
        for (int val : heap) {
            cout << val << " ";
        }
        std::cout << std::endl;
    }
};

int main() {
    MaxHeap maxHeap;

    // Insert elements into the heap
    maxHeap.insert(10);
    maxHeap.insert(20);
    maxHeap.insert(15);
    maxHeap.insert(30);
    maxHeap.insert(40);

    cout << "Heap elements: ";
    maxHeap.printHeap();

    // Get and delete the maximum element
    cout << "Max element: " << maxHeap.getMax() << std::endl;
    cout << "Deleting max element: " << maxHeap.deleteMax() << std::endl;

    cout << "Heap elements after deletion: ";
    maxHeap.printHeap();

    return 0;
}
```


--------------------------------------------------------------------------

### tags
#algorithms #heap
