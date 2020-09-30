# Indiana-Code
Place to house laws on the books in Indiana in order to test revisioning
This code is about how to calculate mass of molecules using stacks in c++.

#include<bits/stdc++.h>
using namespace std;
long long massofmolecules(string str,int len)
{
  stack<char> st;
  stack<int> mass;
  for (int i = 0; i < len; i++)
  {
    if (str[i]=='C')
    {
      st.push('C');
      mass.push(12);
    }
    else if (str[i]=='O')
    {
      st.push('O');
      mass.push(16);            
    }
    else if (str[i]=='H')
    {
      st.push('H');
      mass.push(1);
    }
    else if (isdigit(str[i])!=0)
    {
      mass.top()=mass.top()*(str[i]-'0');
    }
    else if (str[i]=='(')
    {
      st.push('(');
    }
    else
    {
      int sum=0;
      while(st.top()!='(')
      {
        sum+=mass.top();
        st.pop();
        mass.pop();
      }
      st.top()='#';
      mass.push(sum);
    }
  }
  long long sum1=0;
  while (!mass.empty())
  {
    sum1+=mass.top();
    mass.pop();
  }
  return sum1;
}
int main()
{
    string str;
    cin>>str;
    int len=str.length();
    cout<<massofmolecules(str,len)<<endl;
    return 0;
}
