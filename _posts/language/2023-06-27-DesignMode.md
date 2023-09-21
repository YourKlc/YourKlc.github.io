---
title: C#设计模式
date: 2023-06-27 17:00:00 +0800
categories: [Language, CSharp] #一级目录, 二级目录
tags: [CSharp]     # TAG names should always be lowercase

toc: true #右侧内容位置是否显示, 默认值在_config.yml

comments: false #评论是否开启

math: false #数学符号是否加载

mermaid: true #mermaid是否开启.

pin: true #是否置顶

#![img-description](/path/to/image)
#_Image Caption_ 图片的说明

#![Desktop View](/assets/img/sample/mockup.png){: width="700" height="400" } 设置图片宽高

#```
#{: file="DesignMode" }   #设置代码块标题

---

<style>
hr{
  height: 4px;
  width: 100%;
  margin: 0,0,0,0;
  margin - left : auto;
  margin - right : auto;
  opacity: 100%;
  border-top: 1px dashed #ffff0080 !important;
  border-bottom: 1px dashed #00ff0080 !important;
  border-radius: 0px;
}
</style>

# 分别是普通的单例类以及继承自MonoBehaviour的单例

``` c#
public abstract class SingletonN<T> where T : class, new()
{
    private static T ins = null;
    private static readonly object locker = new object();
    public static T Ins
    {   
        get
        {
            if (ins == null)
            {
                lock (locker)
                {
                    if (ins == null)
                    {
                        ins = new T();
                    }
                }
            }
            return ins;
        }
    }
} 

public class SingletonM<T> : MonoBehaviour where T : SingletonM<T>
{
    private static T ins;
    public static T Ins
    {
        get
        {
            if (ins != null) return ins;

            ins = FindObjectOfType<T>();
            if (ins == null)
            {
                new GameObject("Singleton of " + typeof(T)).AddComponent<T>();
            }
            else ins.Ini();
            return ins;
        }
    }
    private void Awake()
    {
        ins = this as T;
        Ini();
    }
    protected virtual void Ini() { }
}
```
{: file="DesignMode" }

``` c#
观察者模式, 待补充
```
{: file="DesignMode" }
