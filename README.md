WEEK04
=============

01
-------------

```C
#include <GL/glut.h>  ///使用GLUT外掛
#include <stdio.h>
void display()
{
    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);///清空
    glutSolidTeapot(0.3);
    glutSwapBuffers();   ///交換兩倍的buffers
}

void mouse(int button,int state,int x,int y)
{
    printf("button:%d state:%d x:%d                     
    y:%d\n",button,state,x,y);
}

int main(int argc,char ** argv)
{
    glutInit(&argc,argv);    ///GLUT初始設定
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH); ///顯示模式
    glutCreateWindow("08160554");   ///開窗
    glutDisplayFunc(display);   ///diaplay顯示的函式
    glutMouseFunc(mouse);  ///mouse滑鼠的程式
    glutMainLoop();   ///主要迴圈
}
 ```
 
02
-------------------

```C
#include <GL/glut.h> 
#include <stdio.h>
void display()
{
    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
    glutSolidTeapot(0.3);
    glutSwapBuffers();
}
void mouse(int button,int state,int x,int y)
{
    if(state==GLUT_DOWN) ///如果 mouse 按下去，印出程式碼
    {
        printf(" glVertex3f((%d-150)/150.0,-(%d-
        150)/150.0,0);\n",x,y);
    }
}
int main(int argc,char ** argv)
{
    glutInit(&argc,argv); 
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("08160554");
    glutDisplayFunc(display);   ///diaplay顯示的函式
    glutMouseFunc(mouse);  ///mouse滑鼠的程式
    glutMainLoop(); 
}

```

03
----------------
```C
#include <GL/glut.h>
#include <stdio.h>
void display()
{
    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
    glBegin(GL_POLYGON);
         glVertex3f((118-150)/150.0,-(129-150)/150.0,0);
         glVertex3f((112-150)/150.0,-(140-150)/150.0,0);
         glVertex3f((110-150)/150.0,-(149-150)/150.0,0);
         glVertex3f((107-150)/150.0,-(163-150)/150.0,0);
         glVertex3f((109-150)/150.0,-(176-150)/150.0,0);
         glVertex3f((117-150)/150.0,-(183-150)/150.0,0);
         glVertex3f((117-150)/150.0,-(188-150)/150.0,0);
         glVertex3f((177-150)/150.0,-(184-150)/150.0,0);
         glVertex3f((181-150)/150.0,-(184-150)/150.0,0);
         glVertex3f((158-150)/150.0,-(114-150)/150.0,0);
         glVertex3f((141-150)/150.0,-(111-150)/150.0,0);
         glVertex3f((150-150)/150.0,-(125-150)/150.0,0);
         glVertex3f((120-150)/150.0,-(130-150)/150.0,0);
         glVertex3f((105-150)/150.0,-(165-150)/150.0,0);
    glEnd();
    glutSwapBuffers(); 
}
void mouse(int button,int state,int x,int y)
{
    if(state==GLUT_DOWN)  ///如果 mouse 按下去，印出程式碼
    {
        printf(" glVertex3f((%d-150)/150.0,-(%d-150)/150.0,0);\n",x,y);
    }
}
int main(int argc,char ** argv)
{
    glutInit(&argc,argv); 
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH); 
    glutCreateWindow("08160554"); 
    glutDisplayFunc(display); 
    glutMouseFunc(mouse);
    glutMainLoop(); 
}

```
04
-----------
```C
#include <GL/glut.h> 
#include <stdio.h>
float teapotX=0,teapotY=0; ///茶壺的座標-1.0...+1.0
void display()
{
    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
    glPushMatrix(); ///矩陣備份
        glTranslatef(teapotX,teapotY,0); ///照著座標移動
        glutSolidTeapot(0.3);
    glPopMatrix(); ///矩陣還原
    glEnd();
    glutSwapBuffers(); 
}

void motion (int x,int y)  ///mouse motion 的函式
{
    teapotX=(x-150)/150.0; ///座標換算
    teapotY=-(y-150)/150.0;
}
int main(int argc,char ** argv)
{
    glutInit(&argc,argv); 
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("08160554");
    glutDisplayFunc(display);  
    glutMotionFunc(motion); ///準備 mouse motion移動時的函式
    glutMainLoop(); 
}

```
