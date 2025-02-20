#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct Car {
    int id;
    char model[50];
    union Rent {
        float dailyRent;
        float totalRent;
    } rent;
};

void saveToFile(struct Car cars[], int count) {
    FILE *file = fopen("car_rentals.txt", "w");
    if (file == NULL) {
        printf("Error opening file!\n");
        return;
    }
    for (int i = 0; i < count; i++) {
        fprintf(file, "%d, %s, ₹%.2f/day\n", cars[i].id, cars[i].model, cars[i].rent.dailyRent);
    }
    fclose(file);
    printf("Data saved in \"car_rentals.txt\"\n");
}

void updateRentalInformation(struct Car cars[], int count) {
    int carId;
    float newRent;
    printf("Enter Car ID to update: ");
    scanf("%d", &carId);

    for (int i = 0; i < count; i++) {
        if (cars[i].id == carId) {
            printf("Enter new daily rent for %s: ", cars[i].model);
            scanf("%f", &newRent);
            cars[i].rent.dailyRent = newRent;
            printf("Updated rent for %s: ₹%.2f/day\n", cars[i].model, cars[i].rent.dailyRent);
            saveToFile(cars, count);
            return;
        }
    }
    printf("Car ID %d not found!\n", carId);
}

int main() {
    int n;
    printf("Enter number of cars: ");
    scanf("%d", &n);

    struct Car cars[n];
    for (int i = 0; i < n; i++) {
        printf("Car %d:\n", i + 1);
        printf("  ID: ");
        scanf("%d", &cars[i].id);
        printf("  Model: ");
        scanf(" %[^\n]s", cars[i].model); // To read the whole line for model
        printf("  Rent Per Day (in ₹): ");
        scanf("%f", &cars[i].rent.dailyRent);
    }

    printf("\nCars Available:\n");
    for (int i = 0; i < n; i++) {
        printf("%d. %s - ₹%.2f/day\n", i + 1, cars[i].model, cars[i].rent.dailyRent);
    }

    saveToFile(cars, n);

    char choice;
    printf("Do you want to update rental information? (y/n): ");
    scanf(" %c", &choice);
    if (choice == 'y' || choice == 'Y') {
        updateRentalInformation(cars, n);
    }

    return 0;
}
