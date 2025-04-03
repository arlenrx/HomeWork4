#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_JUDGES 10
#define MAX_NAME_LENGTH 100
#define MAX_AFFILIATION_LENGTH 100
#define MAX_TITLE_LENGTH 100
#define MAX_EXPERTISE_LENGTH 50
#define MAX_EMAIL_LENGTH 100
#define MAX_PHONE_LENGTH 20

struct Judge {
    char name[MAX_NAME_LENGTH];
    char gender[10];
    char affiliation[MAX_AFFILIATION_LENGTH];
    char title[MAX_TITLE_LENGTH];
    char expertise[MAX_EXPERTISE_LENGTH];
    char email[MAX_EMAIL_LENGTH];
    char phone[MAX_PHONE_LENGTH];
};

int main() {
    struct Judge judges_array[MAX_JUDGES];
    int total_judges, i;
    char project_name[MAX_NAME_LENGTH];
    char check_info;
    
    printf("####################################\n");
    printf("#      Judge List Data Entry      #\n");
    printf("####################################\n");
    
    printf("Enter the participating project name: ");
    fgets(project_name, sizeof(project_name), stdin);
    project_name[strcspn(project_name, "\n")] = '\0';

    printf("Total Number of Judges: ");
    scanf("%d", &total_judges);
    getchar();  // Consume the newline character left by scanf

    printf("Number of Selected Members: ");
    int selected_members;
    scanf("%d", &selected_members);
    getchar();  // Consume the newline character

    printf("++++++++++++++++++++++++++++++++++++\n");
    printf("Starting to input information for %d judges.\n", total_judges);
    printf("++++++++++++++++++++++++++++++++++++\n");

    for (i = 0; i < total_judges; i++) {
        printf("Judge %d:\n", i + 1);

        printf("Name: ");
        fgets(judges_array[i].name, sizeof(judges_array[i].name), stdin);
        judges_array[i].name[strcspn(judges_array[i].name, "\n")] = '\0';

        printf("Gender: ");
        fgets(judges_array[i].gender, sizeof(judges_array[i].gender), stdin);
        judges_array[i].gender[strcspn(judges_array[i].gender, "\n")] = '\0';

        printf("Affiliation: ");
        fgets(judges_array[i].affiliation, sizeof(judges_array[i].affiliation), stdin);
        judges_array[i].affiliation[strcspn(judges_array[i].affiliation, "\n")] = '\0';

        printf("Title: ");
        fgets(judges_array[i].title, sizeof(judges_array[i].title), stdin);
        judges_array[i].title[strcspn(judges_array[i].title, "\n")] = '\0';

        printf("Expertise: ");
        fgets(judges_array[i].expertise, sizeof(judges_array[i].expertise), stdin);
        judges_array[i].expertise[strcspn(judges_array[i].expertise, "\n")] = '\0';

        printf("Email: ");
        fgets(judges_array[i].email, sizeof(judges_array[i].email), stdin);
        judges_array[i].email[strcspn(judges_array[i].email, "\n")] = '\0';

        printf("Phone: ");
        fgets(judges_array[i].phone, sizeof(judges_array[i].phone), stdin);
        judges_array[i].phone[strcspn(judges_array[i].phone, "\n")] = '\0';

        // Validate if all information is filled out
        if (strlen(judges_array[i].name) == 0 || strlen(judges_array[i].gender) == 0 ||
            strlen(judges_array[i].affiliation) == 0 || strlen(judges_array[i].title) == 0 ||
            strlen(judges_array[i].expertise) == 0 || strlen(judges_array[i].email) == 0 ||
            strlen(judges_array[i].phone) == 0) {
            printf("The input items are incorrect. Please enter them again.\n");
            i--;  // Retry current judge entry
            continue;
        }
        printf("++++++++++++++++++++++++++++++++++++\n");
    }

    printf("Judge information entry is complete.\n");
    printf("++++++++++++++++++++++++++++++++++++\n");

    printf("Should we check the judge information? (Y/N): ");
    scanf(" %c", &check_info);
    getchar();  // Consume the newline character

    if (check_info == 'Y' || check_info == 'y') {
        printf("####################################\n");
        printf("#        Display Judge Data        #\n");
        printf("####################################\n");

        for (i = 0; i < total_judges; i++) {
            printf("[Judge %d]\n", i + 1);
            printf("Name: %s\n", judges_array[i].name);
            printf("Gender: %s\n", judges_array[i].gender);
            printf("Affiliation: %s\n", judges_array[i].affiliation);
            printf("Title: %s\n", judges_array[i].title);
            printf("Expertise: %s\n", judges_array[i].expertise);
            printf("Email: %s\n", judges_array[i].email);
            printf("Phone: %s\n", judges_array[i].phone);
            printf("-----------------------------------\n");
        }
    }

    return 0;
}
