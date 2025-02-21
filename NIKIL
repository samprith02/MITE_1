#include<stdio.h>

typedef struct {
    int rollNo;          // Student Roll Number
    char name[50];       // Student Name
    int maths, physics, chemistry, cs; // Subject Marks
    int totalMarks;      // Sum of all subjects
    float percentage;    // Percentage calculation
    char grade;          // Assigned grade (A, B, C, D, F)
} Student;

void readstudent(const char* filename, Student std[], int* count){
    FILE *file = fopen(filename, "r");
    if(file == NULL){
        printf("Cannot read file\n");
        return;
    }

    printf("Enter the %d students details:\n", *count);
    for(int i = 0; i < *count; i++){
        printf("Enter student Id, Name, 4 subject marks: ");
        fscanf(file, "%d %s %d %d %d %d", &std[i].rollNo, std[i].name, &std[i].maths, &std[i].physics, &std[i].chemistry, &std[i].cs);
        std[i].totalMarks = std[i].maths + std[i].physics + std[i].chemistry + std[i].cs;
        std[i].percentage = std[i].totalMarks / 4.0;

        if (std[i].percentage >= 90)
            std[i].grade = 'A';
        else if (std[i].percentage >= 75)
            std[i].grade = 'B';
        else if (std[i].percentage >= 50)
            std[i].grade = 'C';
        else if (std[i].percentage >= 35)
            std[i].grade = 'D';
        else
            std[i].grade = 'F';
    }
    fclose(file);
}

void main(){
    Student std[100];
    int count;
    printf("Enter the number of students: ");
    scanf("%d", &count);

    readstudent("Students.txt", std, &count);
    
    // Display the details of each student
    for(int i = 0; i < count; i++){
        printf("Roll No: %d, Name: %s, Total Marks: %d, Percentage: %.2f, Grade: %c\n", 
               std[i].rollNo, std[i].name, std[i].totalMarks, std[i].percentage, std[i].grade);
    }
}
