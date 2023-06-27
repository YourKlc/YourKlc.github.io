---
title: TITLED
date: 2023-06-27 17:00:00 +0800
categories: [Language, CSharp]
tags: [c#]     # TAG names should always be lowercase
---

---
<author_id>:
  name: klccc
  url: YourKlc.github.io
---

---
toc: true
---

---
comments: false
---

---
math: false
---

---
mermaid: true
---

---
pin: true
---

`/path/to/a/file.extend`{: .filepath}

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
