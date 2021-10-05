# observer-patern


/******************************************************************************

                              Online C++ Compiler.
               Code, Compile, Run and Debug C++ program online.
Write your code in this editor and press "Run" button to compile and execute it.

*******************************************************************************/

#include <iostream>
#include<bits/stdc++.h>
using namespace std;
//interface 
class iobserver{
  public:
  virtual void update()=0;
};

class subject{
    private:
    list<iobserver*> v1;
    
    public:
    void attach(iobserver *a){
        v1.push_back(a);
    }
    void detach(iobserver *a){
        v1.remove(a);
    }
    void notify(){
        for(auto a:v1){
            a->update();
        }
        
    }
    
};


class o1:public iobserver{
   

    public:
    o1(subject &a){a.attach(this);}
    void update(){
        cout<<"o1\n";
    }
};

class o2:public iobserver{    
    public:
     o2(subject&a){a.attach(this);}
    void update(){
        cout<<"o2\n";
    }};
    
class o3:public iobserver{    
    public:
     o3(subject&a){a.attach(this);}
    void update(){
        cout<<"o3\n";
    }};

  
int main()
{
    subject s1;
    
    o1 *obj1=new o1(s1);
     o2 *obj2=new o2(s1);
     o3 *obj3=new o3(s1);
    
    
    // s1.attach(obj1);
    // s1.attach(obj2);
    // s1.attach(obj3);
    // s1.attach(obj4);
    
    s1.notify();
    s1.detach(obj2);
    cout<<endl;
    s1.notify();
    

    return 0;
}
