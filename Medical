#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct Medicine {
    int id;
    char name[50];
    char expiryDate[11];
    float price;
};

int compareByExpiryDate(const void *a, const void *b) {
    struct Medicine *medA = (struct Medicine *)a;
    struct Medicine *medB = (struct Medicine *)b;
    return strcmp(medA->expiryDate, medB->expiryDate);
}

void saveToFile(struct Medicine meds[], int count) {
    FILE *file = fopen("medicine_inventory.txt", "w");
    if (file == NULL) {
        printf("Error opening file!\n");
        return;
    }
    for (int i = 0; i < count; i++) {
        fprintf(file, "%d, %s, %s, ₹%.2f\n", meds[i].id, meds[i].name, meds[i].expiryDate, meds[i].price);
    }
    fclose(file);
    printf("Records saved in \"medicine_inventory.txt\"\n");
}

int main() {
    int n;
    printf("Enter number of medicines: ");
    scanf("%d", &n);

    struct Medicine meds[n];
    for (int i = 0; i < n; i++) {
        printf("Medicine %d:\n", i + 1);
        printf("  ID: ");
        scanf("%d", &meds[i].id);
        printf("  Name: ");
        scanf(" %[^\n]s", meds[i].name); // To read the whole line for name
        printf("  Expiry Date (YYYY-MM-DD): ");
        scanf("%s", meds[i].expiryDate);
        printf("  Price (in ₹): ");
        scanf("%f", &meds[i].price);
    }

    qsort(meds, n, sizeof(struct Medicine), compareByExpiryDate);

    printf("\nSorted Medicines (by Expiry Date):\n");
    for (int i = 0; i < n; i++) {
        printf("%d. %s - %s\n", i + 1, meds[i].name, meds[i].expiryDate);
    }

    saveToFile(meds, n);

    return 0;
}
