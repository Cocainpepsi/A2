# A2
int main() {
    printf("Enter text for analysis: ");
    int count[26] = {0};
    char text[1024];
    fgets(text, 1024, stdin);
    int index = 0;
    while (text[index] != '\0') {
        if (text[index] >= 'a' && text[index] <= 'z') {
            count[text[index] - 'a']++;
        } else if (text[index] >= 'A' && text[index] <= 'Z') {
            count[text[index] - 'A']++;
        }
        index++;
    }

    printf("\n\nLetter Analysis Complete!\n\n");
    printf("%-10s%-15s%-15s\n", "Letter", "Occurrences", "Percentage");
    printf("****************************************\n");

    int total = index - 1;
    int max = 0;
    int maxIndex = 0;
    int min = 0;
    int minIndex = 0;
    for (int i = 0; i < 26; i++) {
        double percentage = (double)count[i] / (double)total * 100;
        printf("%-10c%-15d%-15.2f\n", i + 'A', count[i], percentage);
        if (count[i] > max) {
            max = count[i];
            maxIndex = i;
        }
        if (count[i] < min && count[i] != 0 || min == 0) {
            min = count[i];
            minIndex = i;
        }
    }
    printf("\nThe most frequently occurring character is %c.\n", maxIndex + 'A');
    printf("The least frequently occurring character is %c.\n", minIndex + 'A');

    return 0;
}
