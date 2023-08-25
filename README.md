# Student-Database-System
#include <stdio.h>
#include <string.h>

// Define structure for student record
struct Student {
    char name[50];
    int rollNumber;
    float marks;
};

// Function to add a student record
void addStudent(struct Student students[], int *count) {
    if (*count < 100) { // Limiting to 100 students for simplicity
        struct Student newStudent;
        printf("Enter student name: ");
        scanf("%s", newStudent.name);
        printf("Enter roll number: ");
        scanf("%d", &newStudent.rollNumber);
        printf("Enter marks: ");
        scanf("%f", &newStudent.marks);

        students[*count] = newStudent;
        (*count)++;
        printf("Student added successfully.\n");
    } else {
        printf("Database is full. Cannot add more students.\n");
    }
}

// Function to display all student records
void displayStudents(struct Student students[], int count) {
    printf("Student Records:\n");
    for (int i = 0; i < count; i++) {
        printf("Name: %s, Roll Number: %d, Marks: %.2f\n", students[i].name, students[i].rollNumber, students[i].marks);
    }
}

// Function to search for a student by roll number
void searchStudent(struct Student students[], int count, int rollNumber) {
    for (int i = 0; i < count; i++) {
        if (students[i].rollNumber == rollNumber) {
            printf("Student Found:\n");
            printf("Name: %s, Roll Number: %d, Marks: %.2f\n", students[i].name, students[i].rollNumber, students[i].marks);
            return;
        }
    }
    printf("Student not found.\n");
}

int main() {
    struct Student students[100]; // Array to store student records
    int studentCount = 0; // Current count of student records

    while (1) {
        printf("\nStudent Database System\n");
        printf("1. Add Student\n");
        printf("2. Display Students\n");
        printf("3. Search Student\n");
        printf("4. Exit\n");
        printf("Select an option: ");

        int choice;
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                addStudent(students, &studentCount);
                break;
            case 2:
                displayStudents(students, studentCount);
                break;
            case 3:
                printf("Enter roll number to search: ");
                int rollNumber;
                scanf("%d", &rollNumber);
                searchStudent(students, studentCount, rollNumber);
                break;
            case 4:
                printf("Exiting...\n");
                return 0;
            default:
                printf("Invalid choice.\n");
        }
    }

    return 0;
}
