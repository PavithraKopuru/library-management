#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define MAX_BOOKS 100
struct Book {
    int id;
    char title[100];
    char author[100];
    int year;
};
struct Book library[MAX_BOOKS];
void addBook(int *count) {
    if (*count >= MAX_BOOKS) {
        printf("\nLibrary is full! Cannot add more books.\n");
        return;
    }

    printf("\nEnter Book ID: ");
    scanf("%d", &library[*count].id);
    getchar(); 

    printf("Enter Book Title: ");
    fgets(library[*count].title, sizeof(library[*count].title), stdin);
    library[*count].title[strcspn(library[*count].title, "\n")] = 0;  

    printf("Enter Book Author: ");
    fgets(library[*count].author, sizeof(library[*count].author), stdin);
    library[*count].author[strcspn(library[*count].author, "\n")] = 0;

    printf("Enter Publication Year: ");
    scanf("%d", &library[*count].year);

    (*count)++;
    printf("\nBook added successfully!\n");
}
void viewBooks(int count) {
    if (count == 0) {
        printf("\nNo books in the library.\n");
        return;
    }

    printf("\nList of Books in the Library:\n");
    printf("ID\tTitle\tAuthor\tYear\n");
    for (int i = 0; i < count; i++) {
        printf("%d\t%s\t%s\t%d\n", library[i].id, library[i].title, library[i].author, library[i].year);
    }
}
void deleteBook(int *count) {
    int id, found = 0;

    if (*count == 0) {
        printf("\nNo books in the library to delete.\n");
        return;
    }

    printf("\nEnter Book ID to delete: ");
    scanf("%d", &id);

    for (int i = 0; i < *count; i++) {
        if (library[i].id == id) {
            found = 1;
            for (int j = i; j < *count - 1; j++) {
                library[j] = library[j + 1]; 
            }
            (*count)--; 
            printf("\nBook deleted successfully!\n");
            break;
        }
    }

    if (!found) {
        printf("\nBook with ID %d not found.\n", id);
    }
}
void searchBook(int count) {
    int id, found = 0;

    if (count == 0) {
        printf("\nNo books in the library to search.\n");
        return;
    }

    printf("\nEnter Book ID to search: ");
    scanf("%d", &id);

    for (int i = 0; i < count; i++) {
        if (library[i].id == id) {
            printf("\nBook found:\n");
            printf("ID: %d\n", library[i].id);
            printf("Title: %s\n", library[i].title);
            printf("Author: %s\n", library[i].author);
            printf("Year: %d\n", library[i].year);
            found = 1;
            break;
        }
    }

    if (!found) {
        printf("\nBook with ID %d not found.\n", id);
    }
}
void menu() {
    int choice, count = 0;

    do {
        printf("\nLibrary Management System\n");
        printf("1. Add a Book\n");
        printf("2. View All Books\n");
        printf("3. Delete a Book\n");
        printf("4. Search for a Book\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                addBook(&count);
                break;
            case 2:
                viewBooks(count);
                break;
            case 3:
                deleteBook(&count);
                break;
            case 4:
                searchBook(count);
                break;
            case 5:
                printf("\nExiting the system...\n");
                break;
            default:
                printf("\nInvalid choice, please try again.\n");
        }
    } while (choice != 5);
}
int main() {
    menu();
    return 0;
}
