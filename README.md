# myrepository
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class SinglyLinkedList:
    def __init__(self):
        self.head = None

    # Traverse the list and print each node's data
    def traverse(self):
        temp = self.head
        if not temp:
            print("The list is empty.")
            return
        while temp:
            print(temp.data, end=" -> ")
            temp = temp.next
        print("None")
    
    # Search for a node by its value
    def search(self, key):
        temp = self.head
        while temp:
            if temp.data == key:
                return True
            temp = temp.next
        return False

    # Prepend a new node at the beginning of the list
    def prepend(self, data):
        new_node = Node(data)
        new_node.next = self.head
        self.head = new_node
    
    # Remove a node by value
    def remove(self, key):
        temp = self.head
        
        # If the node to be deleted is the head
        if temp and temp.data == key:
            self.head = temp.next
            temp = None
            return
        
        # Search for the node to delete
        prev = None
        while temp and temp.data != key:
            prev = temp
            temp = temp.next
        
        if temp is None:  # Node not found
            print(f"Node with value {key} not found.")
            return
        
        # Unlink the node from the list
        prev.next = temp.next
        temp = None
    
    # Append a new node at the end of the list
    def append(self, data):
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            return
        last = self.head
        while last.next:
            last = last.next
        last.next = new_node

# Example usage
if __name__ == "__main__":
    ll = SinglyLinkedList()
    
    # Adding nodes to the list
    ll.append(10)
    ll.append(20)
    ll.append(30)
    
    print("Traversing the list:")
    ll.traverse()  # Output: 10 -> 20 -> 30 -> None

    # Prepending a node
    ll.prepend(5)
    print("After prepending 5:")
    ll.traverse()  # Output: 5 -> 10 -> 20 -> 30 -> None

    # Searching for a node
    print("Is 20 in the list?", ll.search(20))  # Output: True
    print("Is 40 in the list?", ll.search(40))  # Output: False

    # Removing a node
    ll.remove(20)
    print("After removing node with value 20:")
    ll.traverse()  # Output: 5 -> 10 -> 30 -> None

    ll.remove(50)  # Node with value 50 doesn't exist
    ll.remove(5)
    print("After removing node with value 5:")
    ll.traverse()  # Output: 10 -> 30 -> None
