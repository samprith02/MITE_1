#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct Employee {
    int id;
    char name[50];
    float basicSalary;
    float allowances;
    float grossSalary;
};

void computeGrossSalary(struct Employee *emp) {
    emp->grossSalary = emp->basicSalary + emp->allowances;
}

void saveToFile(struct Employee emps[], int count) {
    FILE *file = fopen("payroll.txt", "w");
    if (file == NULL) {
        printf("Error opening file!\n");
        return;
    }
    for (int i = 0; i < count; i++) {
        fprintf(file, "%d, %s, ₹%.2f, ₹%.2f, ₹%.2f\n", emps[i].id, emps[i].name, emps[i].basicSalary, emps[i].allowances, emps[i].grossSalary);
    }
    fclose(file);
    printf("Record saved in \"payroll.txt\"\n");
}

void retrieveEmployeeSalary(struct Employee emps[], int count, int empId) {
    for (int i = 0; i < count; i++) {
        if (emps[i].id == empId) {
            printf("Employee: %s\n", emps[i].name);
            printf("Gross Salary: ₹%.2f\n", emps[i].grossSalary);
            return;
        }
    }
    printf("Employee ID %d not found!\n", empId);
}

int main() {
    int n;
    printf("Enter number of employees: ");
    scanf("%d", &n);

    struct Employee emps[n];
    for (int i = 0; i < n; i++) {
        printf("Employee %d:\n", i + 1);
        printf("  ID: ");
        scanf("%d", &emps[i].id);
        printf("  Name: ");
        scanf(" %[^\n]s", emps[i].name); // To read the whole line for name
        printf("  Basic Salary (in ₹): ");
        scanf("%f", &emps[i].basicSalary);
        printf("  Allowances (in ₹): ");
        scanf("%f", &emps[i].allowances);
        computeGrossSalary(&emps[i]);
    }

    saveToFile(emps, n);

    int empId;
    printf("Enter Employee ID to search: ");
    scanf("%d", &empId);

    retrieveEmployeeSalary(emps, n, empId);

    return 0;
}
