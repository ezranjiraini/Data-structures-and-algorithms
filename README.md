Hash Table (Dictionary in Python): for fast lookup by ID

Linked List: to maintain order of registration

# student_registry.py
class Student:
    def __init__(self, student_id, name, year):
        self.id = student_id
        self.name = name
        self.year = year

class Node:
    def __init__(self, student):
        self.student = student
        self.next = None

class StudentRegistry:
    def __init__(self):
        self.students = {}   # dictionary: ID → Student
        self.head = None
        self.tail = None

    def add_student(self, student):
        # 1. Check if student exists
        if student.id in self.students:
            print("Student already exists!")
            return
        # 2. Add to dictionary
        self.students[student.id] = student
        # 3. Add to linked list for order
        new_node = Node(student)
        if not self.head:
            self.head = self.tail = new_node
        else:
            self.tail.next = new_node
            self.tail = new_node

    def find(self, student_id):
        return self.students.get(student_id)
