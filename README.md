#include <stdio.h>

int main() {
    int arr[50];
    int size = 0;
    int choice;

    while (1) {
        printf("\nMenu:\n");
        printf("1. Input size and elements of an array.\n");
        printf("2. Update \n");
        printf("3. Delete \n");
        printf("4. Display \n");
        printf("5. Sort  (Ascending/Descending)\n");
        printf("6. Binary Search\n");
        printf("7. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1: {
                printf("Enter the size of the array (1-50): ");
                scanf("%d", &size);
                
                
                printf("Enter %d values:\n", size);
                for (int i = 0; i < size; i++) {
                    printf("Value %d: ", i + 1);
                    scanf("%d", &arr[i]);
                }
                 printf("The array elements are:\n");
               for (int i = 0; i < size; i++) {
                 printf("%d ", arr[i]);}
        
                
                break;
        
               
               }  
       

        case 2: {
                if(size==0){
                    printf("Array should be initialized first using option 1.");
                    break;
                } 
            
                
      int index, newValue;
      printf("Enter the index to update (0 to %d): ", size - 1);
      scanf("%d", &index);

              if (index >= 0 && index < size) {
                printf("Enter the new value: ");
                scanf("%d", &newValue);
                 arr[index] = newValue;
            printf("Value at index %d updated to %d.\n", index, newValue);
            } else {
               printf("Invalid index.\n");
           }
 
    
             printf("Updated array:\n");
              for (int i = 0; i < size; i++) {
                 printf("%d ", arr[i]);
                 }
             break;
            }
    

            case 3: {
                if(size==0){
                    printf("Array should be initialized first using option 1.");
                    break;
                }
                int value;
                printf("Enter value to delete: ");
                scanf("%d", &value);
                int found = 0;
                for (int i = 0; i < size; i++) {
                    if (arr[i] == value) {
                        for (int j = i; j < size - 1; j++) {
                            arr[j] = arr[j + 1];
                        }
                        size--;
                        found = 1;
                        printf("Value %d deleted.\n", value);
                        break;
                    }
                }
                 printf("Updated array:\n");
              for (int i = 0; i < size; i++) {
                 printf("%d ", arr[i]);
                 }
                if (!found) {
                    printf("Value not found.\n");
                }
                break;
            }

            case 4: {
                 if(size==0){
                    printf("Array should be initialized first using option 1.");
                    break;
                }
                printf("Array elements: ");
                for (int i = 0; i < size; i++) {
                    printf("%d ", arr[i]);
                }
                printf("\n");
                break;
            }

            case 5: {
                 if(size==0){
                    printf("Array should be initialized first using option 1.");
                    break;
                }
                char order;
                printf("Enter A for Ascending or D for Descending: ");
                scanf(" %c", &order);
                if (order != 'A' && order != 'a' && order != 'D' && order != 'd') {
                    printf("Invalid option. Use A or D.\n");
                    break;
                }
                for (int i = 0; i < size - 1; i++) {
                    for (int j = i + 1; j < size; j++) {
                        if ((order == 'A' || order == 'a') && arr[i] > arr[j]) {
                            int temp = arr[i];
                            arr[i] = arr[j];
                            arr[j] = temp;
                        } else if ((order == 'D' || order == 'd') && arr[i] < arr[j]) {
                            int temp = arr[i];
                            arr[i] = arr[j];
                            arr[j] = temp;
                        }
                    }
                }
                printf("Array sorted %s.\n", (order == 'A' || order == 'a') ? "ascending" : "descending");
                 printf("Updated array:\n");
              for (int i = 0; i < size; i++) {
                 printf("%d ", arr[i]);
                 }
                break;
            }

            case 6: {
                 if(size==0){
                    printf("Array should be initialized first using option 1.");
                    break;
                }
                int v;
                printf("Enter value to search: ");
                scanf("%d", &v);
                int indices[100], count = 0;
                for (int i = 0; i < size; i++) {
                    if (arr[i] == v) {
                        indices[count++] = i;
                    }
                }
                if (count == 0) {
                    printf("V %d not found.\n", v);
                } else if (count == 1) {
                    printf("Value you are searching for is %d found at index %d\n", v, indices[0]);
                } else {
                    printf("Value %d found at %d indices: ", v, count);
                    for (int i = 0; i < count; i++) {
                        printf("%d ", indices[i]);
                    }
                    printf("\nEnter the index number to select: ");
                    int selected;
                    scanf("%d", &selected);
                    int valid = 0;
                    for (int i = 0; i < count; i++) {
                        if (indices[i] == selected) {
                            printf("Selected value %d at index %d.\n", v, selected);
                            valid = 1;
                            break;
                        }
                    }
                    if (!valid) {
                        printf("Invalid index selected.\n");
                    }
                
                
            }
            break;
            }

            case 7: {
                printf("Program finished\n");
                return 0;
            }

            default: {
                printf("Invalid choice. Please enter a number between 1 and 7.\n");
            }
        }
    }
        

return  0;
}

