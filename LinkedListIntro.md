# LinkedListIntro
#Using input statement in a linkedlist
class Node:

    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:

    def __init__(self):
        self.head = None

    def printList(self):
        temp = self.head
        while(temp):
            print(temp.data)
            temp = temp.next

    def push(self, newData):
        newNode = Node(newData)
        newNode.next = self.head
        self.head = newNode

    def insertAfter(self, prevNode, newData):

        if prevNode is None:
            print("The given node must be in the linked list")
            return
        newNode = Node(newData)
        newNode.next = prevNode.next
        prevNode.next = newNode

    def append(self, newData):
        newNode = Node(newData)
        if self.head is None:
            self.head = newNode
            return
        last = self.head
        while(last.next):
            last = last.next
        last.next = newNode
    def deleteNode(self, key):
        temp = self.head
        if(temp is not None):
            if(temp.data == key):
                self.head = temp.next
                temp = None
                return
        while(temp is not None):
            if temp.data == key:
                break
            prev = temp
            temp = temp.next
        if(temp == None):
            return
        prev.next = temp.next
        temp = None

    def insertAfter(self, prevData, newData):

        prevNode = self.find(prevData)
        if prevNode is None:
            print("The given node must be in the linked list")
            return
        newNode = Node(newData)
        newNode.next = prevNode.next
        prevNode.next = newNode

    def find(self, data):
        current = self.head
        while current:
            if current.data == data:
                return current
            current = current.next

    def __repr__(self):
        return 'LinkedList(%s)' % str(self)

    def __iter__(self):
        current = self.head
        while current:
            yield current.data
            current = current.next

    def __str__(self):
        return 'Linkedlist : [%s]' % ', '.join([x for x in self])


if __name__ == '__main__':
    list = LinkedList()

    while True:
        print("[0].ADD an element")
        print("[1].Append an element")
        print("[2].Delete an element")
        print("[3].Push an element")
        print("[4].Insert an element")
        print("[5].Print the list")

        menu = int(input("Select a number: "))

        if menu == 0:
            n = input("How many element(s) would you like to add? ")
            n = int(n)
            for i in range(n):
                add = input("Enter data item: ")
                list.append(add)
        elif menu == 1:
            n = input("How many element(s) would you like to append? ")
            n = int(n)
            for i in range(n):
                append = input("Enter item to append: ")
                list.append(append)
        elif menu == 2:
            delete = input("Add an existing element to delete: ")
            list.deleteNode(delete)
        elif menu == 3:
            n = input("How many element(s) would you like to push? ")
            n = int(n)
            for i in range(n):
                push = input("Enter item to push: ")
                list.push(push)
        elif menu == 4:
            prevNode = input("Input an existing element to insert [Previous Node]: ")
            newData = input("Input new element to insert after a Node [New Data]: ")
            list.insertAfter(prevNode, newData)
        elif menu == 5:
            print(list)
        else:
            print("Wrong input try again ")
