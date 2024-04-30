#include <iostream>
#include <string>
#include <queue>

using namespace std;

class StockNode {
public:
    string name;
    int quantity;
    StockNode* next;

    StockNode(const string& n, int q) : name(n), quantity(q), next(nullptr) {}
};

class StockManagement {
private:
    StockNode* head;
    queue<pair<string, int>> stockQueue;

public:
    StockManagement() : head(nullptr) {}

    // Function to add a new item to the stock linked list
    void addItemToLinkedList(const string& name, int qty) {
        StockNode* newNode = new StockNode(name, qty);
        if (!head) {
            head = newNode;
        } else {
            StockNode* temp = head;
            while (temp->next) {
                temp = temp->next;
            }
            temp->next = newNode;
        }
        cout << "Item added to stock linked list: " << name << " (Quantity: " << qty << ")" << endl;
    }

    // Function to add a new item to the stock queue
    void addItemToQueue(const string& name, int qty) {
        stockQueue.push(make_pair(name, qty));
        cout << "Item added to stock queue: " << name << " (Quantity: " << qty << ")" << endl;
    }

    // Function to display all items in the stock linked list
    void displayItemsInLinkedList() {
        cout << "Stock Linked List:" << endl;
        StockNode* temp = head;
        int index = 1;
        while (temp) {
            cout << index << ". " << temp->name << ": " << temp->quantity << endl;
            temp = temp->next;
            index++;
        }
    }

    // Function to display all items in the stock queue
    void displayItemsInQueue() {
        cout << "Stock Queue:" << endl;
        int index = 1;
        while (!stockQueue.empty()) {
            cout << index << ". " << stockQueue.front().first << ": " << stockQueue.front().second << endl;
            stockQueue.pop();
            index++;
        }
    }
};

int main() {
    StockManagement stockManager;

    // Adding sample items to the stock linked list and queue
    stockManager.addItemToLinkedList("Item B", 20);
    stockManager.addItemToQueue("Item C", 15);

    // Displaying items in the stock linked list and queue
    stockManager.displayItemsInLinkedList();
    cout << endl;
    stockManager.displayItemsInQueue();

    return 0;
}
