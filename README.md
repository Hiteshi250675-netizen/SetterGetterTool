# SetterGetterTool
SetterGetterGenerator is a runtime code generation utility that uses the Reflection API of Java Programming Language to automatically generate a default constructor, setter method and getter method. Instead of manually writing boilerplate code, this tool generates it dynamically and copies it directly to the system clipboard. 

import java.awt.*;
import java.awt.datatransfer.*;
import java.lang.reflect.*;
import java.util.*;

class ccc
{
}
class aaa
{
private int x1;
protected char x2;
public String x3;
}
class bbb extends aaa
{
private int x4;
double x5;
protected char x6;
public char x7;
private ccc x8;
private String x9;
}
class SetterGetterGenerator
{
public static void main(String gg[])
{
if(gg.length==0)
{
System.out.println("Usage :[java SetterGetterGenerator class_name]");
return;
}
Map<String,String> map=new HashMap<>();
map.put("java.lang.String","\"\"");
map.put("long","0");
map.put("int","0");
map.put("short","0");
map.put("byte","0");
map.put("float","0.0f");
map.put("double","0.0");
map.put("char","(char)0");
map.put("boolean","false");
StringBuffer sb=new StringBuffer();
String line;
String className=gg[0];
try
{
Class c=Class.forName(className);
Field f[];
String nameOfProperty;
String dataTypeOfProperty;
f=c.getDeclaredFields();
int i;
line="public "+className+"()\n";
sb.append(line);
line="{\n";
sb.append(line);
for(i=0;i<f.length;i++)
{
nameOfProperty=f[i].getName();
dataTypeOfProperty=f[i].getType().toString();
if(dataTypeOfProperty.startsWith("class "))
{
dataTypeOfProperty=dataTypeOfProperty.substring(6);
}
if(map.containsKey(dataTypeOfProperty))
{
line="this."+nameOfProperty+"="+map.get(dataTypeOfProperty)+";\n";
}
else
{
line="this."+nameOfProperty+"=null;\n";
}
sb.append(line);
}
line="}\n";
sb.append(line);
for(i=0;i<f.length;i++)
{
nameOfProperty=f[i].getName();
dataTypeOfProperty=f[i].getType().toString();
if(dataTypeOfProperty.startsWith("class "))
{
dataTypeOfProperty=dataTypeOfProperty.substring(6);
}
line="public void set"+(nameOfProperty.substring(0,1).toUpperCase());
if(nameOfProperty.length()>1)
{
line=line+nameOfProperty.substring(1);
}
line=line+"("+dataTypeOfProperty+" "+nameOfProperty+")\n";
sb.append(line);
line="{\n";
sb.append(line); line="this."+nameOfProperty+"="+nameOfProperty+";\n";
sb.append(line);
line="}\n";
sb.append(line); line="public "+dataTypeOfProperty+" get"+(nameOfProperty.substring(0,1).toUpperCase());
if(nameOfProperty.length()>1)
{
line=line+nameOfProperty.substring(1);
}
line=line+"()\n";
sb.append(line);
line="{\n";
sb.append(line);
line="return this."+nameOfProperty+";\n";
sb.append(line);
line="}\n";
sb.append(line);
}
String str=sb.toString();
StringSelection ss=new StringSelection(str); Clipboard clipBoard=Toolkit.getDefaultToolkit().getSystemClipboard();
clipBoard.setContents(ss,null);
// System.out.println(str);
}catch(Exception e)
{
System.out.println(e);
}
}
}



   
