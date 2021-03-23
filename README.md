# Coleman-Liau-index
Finds Coleman-Liau index from text input.

#include <ctype.h>
#include <cs50.h>
#include <stdio.h>
#include <string.h>

int c_count(string text);
int w_count(string text);
int s_count(string text);
int index(int c, int w, int s);

int main(void)
{
get the text from the book
    string text = get_string("Enter your text: ");

counting characters
    int c_amount = c_count(text);
counting words
    int w_amount = w_count(text);
counting sentenses
    int s_amount = s_count(text);
determining the index
    int ind = index(c_amount, w_amount, s_amount);
    
print the results
    printf("There are %i characters\nThere are %i words\nThere are %i sentences\n", c_amount, w_amount, s_amount);

    if (ind < 1)
    {
        printf("Grade below 1");
    }
    else if (ind > 16)
    {
        printf("Grade 16+");
    }
    else
    {
        printf("Grade %i", ind);
    }
}
