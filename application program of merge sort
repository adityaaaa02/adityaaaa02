#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Function to merge two subarrays
void merge(char **arr, int left, int mid, int right) {
    int n1 = mid - left + 1;
    int n2 = right - mid;

    // Create temporary arrays
    char *L = (char *)malloc(n1 * sizeof(char *));
    char *R = (char *)malloc(n2 * sizeof(char *));

    // Copy data to temporary arrays L[] and R[]
    for (int i = 0; i < n1; i++)
        L[i] = arr[left + i];
    for (int j = 0; j < n2; j++)
        R[j] = arr[mid + 1 + j];

    // Merge the temporary arrays back into arr[left..right]
    int i = 0, j = 0, k = left;
    while (i < n1 && j < n2) {
        if (strcmp(L[i], R[j]) <= 0) {
            arr[k] = L[i];
            i++;
        } else {
            arr[k] = R[j];
            j++;
        }
        k++;
    }

    // Copy the remaining elements of L[], if any
    while (i < n1) {
        arr[k] = L[i];
        i++;
        k++;
    }

    // Copy the remaining elements of R[], if any
    while (j < n2) {
        arr[k] = R[j];
        j++;
        k++;
    }

    // Free temporary arrays
    free(L);
    free(R);
}

// Function to perform merge sort
void mergeSort(char **arr, int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        merge(arr, left, mid, right);
    }
}

int main() {
    int n;
    printf("Enter the number of mobile numbers: ");
    scanf("%d", &n);

    // Allocating memory for an array of strings
    char *mobileNumbers = (char *)malloc(n * sizeof(char *));
    for (int i = 0; i < n; i++) {
        mobileNumbers[i] = (char *)malloc(20 * sizeof(char));
        printf("Enter mobile number %d: ", i + 1);
        scanf("%s", mobileNumbers[i]);
    }

    // Sorting the mobile numbers using merge sort
    mergeSort(mobileNumbers, 0, n - 1);

    // Displaying the sorted mobile numbers
    printf("Sorted Mobile Numbers:\n");
    for (int i = 0; i < n; i++) {
        printf("%s\n", mobileNumbers[i]);
    }

    // Freeing allocated memory
    for (int i = 0; i < n; i++) {
        free(mobileNumbers[i]);
    }
    free(mobileNumbers);

    return 0;
}
