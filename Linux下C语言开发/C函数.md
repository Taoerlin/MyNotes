## C常用库函数示例及区别
### fread()与fgets()
* fread()用例
```
#include <stdio.h>
#include <string.h>
int main()
{
   FILE *fp;
   char c[] = "This is runoob";
   char buffer[20];
 
   /* 打开文件用于读写 */
   fp = fopen("file.txt", "w+");
 
   /* 写入数据到文件 */
   fwrite(c, strlen(c) + 1, 1, fp);
 
   /* 查找文件的开头 */
   fseek(fp, 0, SEEK_SET);
 
   /* 读取并显示数据 */
   fread(buffer, strlen(c)+1, 1, fp);
   printf("%s\n", buffer);
   fclose(fp);
   
   return(0);
}
```
* fgets()用例
```
#include <stdio.h>

int main()
{
   FILE *fp;
   char str[60];

   /* 打开用于读取的文件 */
   fp = fopen("file.txt" , "r");
   if(fp == NULL) {
      perror("打开文件时发生错误");
      return(-1);
   }
   if( fgets (str, 60, fp)!=NULL ) {
      /* 向标准输出 stdout 写入内容 */
      puts(str);
   }
   fclose(fp);
   
   return(0);
}
```
* fgets()当读取 (n-1) 个字符时，或者读取到换行符时，或者到达文件末尾时，它会停止。
* fread()读取所有内容