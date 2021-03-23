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
    //get the text
    string text = get_string("Enter your text: ");
    //counting characters
    int c_amount = c_count(text);
    //counting words
    int w_amount = w_count(text);
    //counting sentenses
    int s_amount = s_count(text);
    //determining the index
    int ind = index(c_amount, w_amount, s_amount);
    //print the results
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

//count the characters
int c_count (string text)
{
    int c = 0;
    for (int i = 0, n = strlen(text); i < n; i++)
    {
        if (isalpha(text[i]))
        {
            c ++;
        }
    }
    return c;
}

//count the words
int w_count (string text)
{
    int w = 1;
    for (int i = 0, n = strlen(text); i < n; i++)
    {
        if (isspace(text[i]))
        {
            w ++;
        }
    }
    return w;
}

//count the sentences
int s_count (string text)
{
    int s = 0;
    for (int i = 0, n = strlen(text); i < n; i++)
    {
        if (text[i] == '.' || text[i] == '!' || text[i] == '?')
        {
            s ++;
        }
    }
    return s;
}

//calculate Coleman-Liau index
int index(int c, int w, int s)
{
    //characters per 100 words
    int L = (c/w)*100;
    //sentences per 100 words
    int S = (s/w)*100;
    int ind = (int) (0.0588 * L - 0.296 * S - 15.8);
    return ind;
}
