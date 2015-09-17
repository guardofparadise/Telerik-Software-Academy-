# Structural Patterns

## Proxy/������

 * �����, ����� �� ��������� �� ���� �����, ����������� ����� ���������, ���� ���������� ��������� ��� ��������� �� ����� ������ �����, ������������ ����������� ������ �� ����.
 * ������� ������ ��������:
 	* *���������� ������ (remote proxy):* ������� ������������� �� �����, ����� �� ������ � ���� ������, �������� �� ���������� ������.
 	* *��������� ������ (virtual proxy):* K����������� �� ������� �� ������������ � ������������� �� �����, ������ ����� �����.
 	* *������� ������ (protection proxy):* ������ ��������� � �������� �� ����� �� ������ �� �����.

�������� �� ������ �� ���������� ������, ����� �� ���� �� ������� ����������, ���� ������ ��� �� ����������� � ����� ���� �� �����. � ������ ������ ������ �� �� ������� � �������� �� ����������� ����� ������������.

� ��� ����� �� ���� ��-����� �� ����������, ����� � �� �� ���� ������� ������ �� ��������� �� ������, � ����� �������� �� ���������� �������������� � ����, ����� �� ����� �� �������������, �� ����� ���������.

������ �� ������� ������ � �� ���� ������� ������� �����, ����� ������� ���������������� �� ��������� ����� � ������������ �� ������ �������� ����� ����, ����� �� �������� ���������, � ������ ������ �� ������������� � ����������� ����� �� ���� �������� � �������� - ������ ������.

## ���� ��������:

![Factory method](http://www.codeproject.com/KB/architecture/492594/GofProxy.jpg)

����������:

 * *__Subject:__* ���������� ���������, ����� �� ���� ������������� ����� �� ��������, ���� � �� ������� ����, ���� �� �������� �� ���� ����� �������� ���� ���������� �� ������� ���� (*RealSubject*).
 * *__Proxy:__* ������, ����� �� ���� ��������� �� ������������ � ���������� ���� ��������� �������� �� *Subject*. ������������ �������� ���� ����, ����� ������������ �������� �� ����������� � *RealSubject* � ����� ���������� ����� ��� ��������� ����������.
 * *__RealSubject:__* �������� �����, ����� ������� �������� �� ���������� �� �����/��������������. ���� � ������, ����� �������� �������, ������������� ���������������� �� �� �������� �� ��������� ����������.

�������� ���:

```
using System;

  // MainApp test application 
  class MainApp
  {
    static void Main()
    {
      // Create proxy and request a service 
      Proxy proxy = new Proxy();
      proxy.Request();

      // Wait for user 
      Console.Read();
    }
  }

  // "Subject" 
  abstract class Subject 
  {
    public abstract void Request();    
  }

  // "RealSubject" 
  class RealSubject : Subject
  {
    public override void Request()
    {
      Console.WriteLine("Called RealSubject.Request()");
    }
  }

  // "Proxy" 
  class Proxy : Subject
  {
    RealSubject realSubject;

    public override void Request()
    {
      // Use 'lazy initialization' 
      if (realSubject == null)
      {
        realSubject = new RealSubject();
      }

      realSubject.Request();
    }  
  }
```