#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <locale.h>
struct novel
{
    char title[100];
    char author[100];
    int pages;
    double rating;
    int year;
};
typedef struct novel R;
void get_input(R* x);
void put_output(R x);
int check(R x);
void max_pages(R a, R b, R c);

int main() {
    system("chcp 1251");
    R a, b, c;
    int found = 0;
    puts("Введите данные первого романа");
    get_input(&a);
    puts("Введите данные второго романа");
    get_input(&b);
    puts("Введите данные третьего романа");
    get_input(&c);
    puts("\nРоманы с количеством страниц от 100 до 200 и оценкой больше 5:");
    if (check(a)) {
        put_output(a);
        found++;
    }
    if (check(b)) {
        put_output(b);
        found++;
    }
    if (check(c)) {
        put_output(c);
        found++;
    }
    if (found == 0)
        puts("Подходящих романов нет.");
    puts("Книга с наибольшим количеством страниц: ");
    max_pages(a, b, c);
    return 0;
}
void get_input(R* x)
{
    printf("Название: ");
    scanf(" %99[^\n]", x->title);
    printf("Автор: ");
    scanf(" %99[^\n]", x->author);
    printf("Количество страниц: ");
    scanf("%d", &x->pages);
    printf("Средняя оценка (0-10): ");
    scanf("%lf", &x->rating);
    printf("Год издания: ");
    scanf("%d", &x->year);
}
int check(R x)
{
    return x.pages >= 100 && x.pages <= 200 && x.rating > 5;
}
void put_output(R x)
{
    printf("Название: %s | Автор: %s | Страниц: %d | Оценка: %.1f | Год: %d\n",
        x.title, x.author, x.pages, x.rating, x.year);
}
void max_pages(R a, R b, R c) 
{
    int max = a.pages;
    if (b.pages > max) {
        max = b.pages;
    }
    if (c.pages > max) {
        max = c.pages;
    }

    if (a.pages == max) {
        put_output(a);
    }
    if (b.pages == max) {
        put_output(b);
    }
    if (c.pages == max) {
        put_output(c);
    }
}
