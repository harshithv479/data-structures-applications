# data-structures-applications
This is my first application on data structures
#include<stdio.h>
#include<stdlib.h>
struct Day{
int date;
char*dayName;
char*activity;
};
void create(struct Day*day){
day->dayName=(char*)malloc(sizeof(char)*20);
day->activity=(char*)malloc(sizeof(char)*100);
printf("Enter the day name:");
scanf("%s",day->dayName);
printf("Enter the date:");
scanf("%d",&day->date);
printf("Enter the activity for the day:\n");
scanf("%s",day->activity);
}
void read(struct Day*calender,int size){
for(int i=0;i<size;i++){
    printf("Enter the details for day %d: \n",i+1);
    create(& calender[i]);
}}
void display(struct Day*calender,int size){
printf("week details activity:");
for(int i=0;i<size;i++){
    printf("Day %d:\n",i+1);
    printf("dayName: %s\n",calender[i].dayName);
    printf("date:%d\n",calender[i].date);
    printf("Activity:%s\n",calender[i].activity);
    printf("\n\n");
}
}
void freememory(struct Day*calender,int size){
for(int i=0;i<size;i++){
    free(calender[i].dayName);
    free(calender[i].activity);
}
}
int main()
{
    int size;
    printf("Enter the number of days in the week:");
    scanf("%d",&size);
    struct Day*calender=(struct Day*)malloc(sizeof(struct Day)*size);
    if(calender==NULL){
    printf("Memory allocation failed exiting program\n");
    return 1;
    }
    read(calender,size);
    display(calender,size);
    freememory(calender,size);
    free(calender);

    return 0;

}
