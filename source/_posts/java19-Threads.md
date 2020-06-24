---
title: java19 线程
date: 2020-02-29 16:58:47
tags: java
---

## 创建线程

1. 继承Thread类

<img src='java19-Threads\6f5112ff-489e-48a8-95b3-978f90f8950d.jpg' >

2. 实现Runnable接口

继承Thread的方式需要重写run方法，然后创建Thread对象，调用start方法，线程开始执行run方法，方法执行结束或抛出异常，线程死亡被垃圾回收器回收。

### 线程的六种状态

1. new 线程还没开始start

2. runnable线程已经开启

3. blocked被阻断，等待锁

4. waiting等待其他线程执行

5. timed_waiting超时等待

6. terminated线程退出

### Thread构造器

<pre style='background:#e6e6e6;padding=10px;'>

//无参构造
public Thread()
//指定名称
public Thread(String name)
//添加接口
public Thread(Runnable target)
//添加接口，指定名称
public Thread(Runnable target, String name)

</pre>

### 相关方法

<pre style='background:#e6e6e6;padding=10px;'>

//获取名称
public String getName()
//获取状态
public Thread.State getState()
//中断线程
public void interrupt()
//开启线程
public void start()
//睡眠一定的时间
public static void sleep(long millis)

</pre>

获取当前的线程：

<img src='java19-Threads\61e2ebda-6fad-45af-9ea3-78d92fa93acc.jpg'>

### 使用示例

<img src='java19-Threads\3eb48243-3db1-40bc-be96-3c8e6929d6f2.jpg'>

继承Thread，重写run方法，创建对象并调用start方法。

## 实现Runnable接口

需要实现Runnable接口，重写run方法，创建Thread对象，使用Thread对象启动。

<img src='java19-Threads\f57af7b2-53bf-430f-9536-76098f49baa8.jpg'>

## 设置优先级

通过setPriority设置优先级，数值越大，优先级越高，执行频率越高，速度越快。

<img src='java19-Threads\5879fabb-1684-4fbc-bc3e-6ec012531e9a.jpg'>

## 线程终止的方法

Thread自带了一个stop方法，但是不安全，建议不要使用。

对于线程内部的run方法，设置while标志位而退出线程是最安全的。

<pre style='background:#e6e6e6;padding=10px;'>

class CounterThread extends Thread {
    public void run() {
        //使用标志位
        while (!stopped) {
            try {
                sleep(10);
            } catch (InterruptedException e) {
            }
            if (count == 1000) {
                count = 1;
            }
            counterLabel.setText(Integer.toString(count++));
        }
    }
}

</pre>

终止线程，只需要设置标志位即可：

<img src='java19-Threads\5ef6c5ed-c542-432a-bea5-200c237f2ffd.jpg'>

## 线程同步

### 线程干扰

<pre style='background:#e6e6e6;padding=10px;'>

package app23;
public class UserStat {
    int userCount;
    public int getUserCount() {
        return userCount;
    }
    public void increment() {
        userCount++;
    }
    public void decrement() {
        userCount--;
    }
}

</pre>

自增自减操作是三个步骤，读取-更改-写入

多个线程对相同的数据进行读写容易出现线程干扰。线程干扰容易出现竞争条件，然后数据出现不一致。

### 原子操作

原子操作指的是最小的操作单元，不会发生线程干扰。除long和double，其他基本数据类型的读写操作都是原子操作。

## 锁同步

锁是实现<code style='background:#ff3385;color:white;padding:5px;'>线程同步</code>一种方式，synchronized可以用于锁定对象，非静态方法被访问时，先获取锁，<code style='background:#ff3385;color:white;padding:5px;'>获取</code>锁的才能执行方法，否则将<code style='background:#ff3385;color:white;padding:5px;'>等待</code>锁释放。

锁被锁定的时候，其他线程<code style='background:#ff3385;color:white;padding:5px;'>不得</code>访问与该锁相关的所有方法。锁是<code style='background:#ff3385;color:white;padding:5px;'>可重入</code>的，即，获取了锁就可以获取使用相同锁同步的方法。

静态方法需要使用<code style='background:#ff3385;color:white;padding:5px;'>Class类</code>的对象进行锁定。

重写上面的类，使之线程安全：

<pre style='background:#e6e6e6;padding=10px;'>

package app23;
public class SafeUserStat {
    int userCount;
    public synchronized int getUserCount() {
        return userCount;
    }
    public synchronized void increment() {
        userCount++;
    }
    public synchronized void decrement() {
        userCount--;
    }
}

</pre>

这里使用synchronized修饰了三个方法，进而保证了线程安全性。

## 代码块锁定

如果接触不到源码，你是无法使用synchronized同步方法的，因此，可以使用块同步。

<img src='java19-Threads\a8a22510-a77d-4d37-9a2b-c06e42505705.jpg'>

示例代码：

<pre style='background:#e6e6e6;padding=10px;'>

UserStat userStat = new UserStat();

public void incrementCounter() {
    synchronized(userStat) {
        // statements to be synchronized, such as calls to
        // the increment, decrement, and getUserCount methods
        // on userStat
        userStat.increment();
    }
}

</pre>

锁定了UserStat对象，可以实现块同步。

可以直接使用this代替这个对象：

<img src='java19-Threads\a290f1a3-39b6-497a-87fb-5f1980e29ced.jpg'>

## volatile

我们先看一个不安全的代码。来说明线程之间的变量可见性问题。

<pre style='background:#e6e6e6;padding=10px;'>

public class Inconsistent {
    static boolean started = false;
    public static void main(String[] args) {
        Thread thread1 = new Thread(new Runnable() {
            public void run() {
                try {
                    Thread.sleep(3000);
                } catch (InterruptedException e) {
                }
                started = true;
                System.out.println("started set to true");
            }
        });
    thread1.start();
    while (!started) {
        // wait until started
    }
    System.out.println("Wait 3 seconds and exit");
    }
}

</pre>

外围主线程等待started标志位改变，终止主线程。然而，这段打印退出代码始终没有执行。

这是因为不同线程之间的数据变更的可见性问题。

修改一：使用同步代码

<pre style='background:#e6e6e6;padding=10px;'>

public class Consistent {
    static boolean started = false;
    public synchronized static void setStarted() {
        started = true;
    }
    public synchronized static boolean getStarted() {
        return started;
    }
    public static void main(String[] args) {
        Thread thread1 = new Thread(new Runnable() {
            public void run() {
                try {
                    Thread.sleep(3000);
                } catch (InterruptedException e) {
                }
                setStarted();
                System.out.println("started set to true");
            }
        });
        thread1.start();
        while (!getStarted()) {
            // wait until started
        }
        System.out.println("Wait 3 seconds and exit");
    }
}

</pre>

使用同步代码，对可见性进行强制保障。但是，没有多个线程写入的问题，使用同步代码添加了 很多性能损失，因此，使用volatile更合适：

<pre style='background:#e6e6e6;padding=10px;'>

public class LightAndConsistent {
    static volatile boolean started = false;
    public static void main(String[] args) {
        Thread thread1 = new Thread(new Runnable() {
            public void run() {
                try {
                    Thread.sleep(3000);
                } catch (InterruptedException e) {
                }
                started = true;
                System.out.println("started set to true");
            }
        });
        thread1.start();
        while (!started) {
            // wait until started
        }
        System.out.println("Wait 3 seconds and exit");
    }
}

</pre>


## 线程协作

object自带的方法：

<pre style='background:#e6e6e6;padding=10px;'>

//等待
public final void wait() throws InterruptedException
//等待一定时长
public final void wait(long timeout) throws InterruptedException
//通知
public final void notify()
//通知所有线程
pubic final void notifyAll()

</pre>

我们来实现一个货物处理的案例：

<pre style='background:#e6e6e6;padding=10px;'>

public class DeliveryNoteHolder {
    //货物
    private String deliveryNote;
    //标志位
    private boolean available = false;
    //派送货物同步方法
    public synchronized String get() {
        //没有货物
        while (available == false) {
            try {
                //等待
                wait();
            } catch (InterruptedException e) { }
        }
        //修改标志，处理货物
        available = false;
        System.out.println(System.currentTimeMillis() + ": got " + deliveryNote);
        //通知其他线程
        notifyAll();
        return deliveryNote;
    }
    //追加货物
    public synchronized void put(String deliveryNote) {
        //有货等待
        while (available == true) {
            try {
                wait(); //等待
            } catch (InterruptedException e) { }
        }
        //修改状态，处理货物，通知其他线程
        this.deliveryNote = deliveryNote;
        available = true;
        System.out.println(System.currentTimeMillis() + ": Put " + deliveryNote);
        notifyAll();
    }
}

</pre>

<pre style='background:#e6e6e6;padding=10px;'>

public class DispatcherThread extends Thread {
    private DeliveryNoteHolder deliveryNoteHolder;
    String[] deliveryNotes = { "XY23. 1234 Arnie Rd.",
        "XY24. 3330 Quebec St.",
        "XY25. 909 Swenson Ave.",
        "XY26. 4830 Davidson Blvd.",
        "XY27. 9900 Old York Dr." };
    public DispatcherThread(DeliveryNoteHolder holder) {
        deliveryNoteHolder = holder;
    }
    public void run() {
        for (int i = 0; i < deliveryNotes.length; i++) {
            String deliveryNote = deliveryNotes[i];
            //追加货物
            deliveryNoteHolder.put(deliveryNote);
            try {
                sleep(100);
            } catch (InterruptedException e) {
            }
        }
    }
}

</pre>

<pre style='background:#e6e6e6;padding=10px;'>

public class DriverThread extends Thread {
    DeliveryNoteHolder deliveryNoteHolder;
    boolean stopped = false;
    String driverName;
    public DriverThread(DeliveryNoteHolder holder, String driverName) {
        deliveryNoteHolder = holder;
        this.driverName = driverName;
    }
    public void run() {
        while (!stopped) {
            //配送货物
            String deliveryNote = deliveryNoteHolder.get();
            try {
                sleep(300);
            } catch (InterruptedException e) {
            }
        }
    }
}

</pre>

两个线程共享同一个对象的实例，遵守wait方法和notifyAll方法

## java.util.Timer

定时器主要用于执行定时任务。

构造器：

<pre style='background:#e6e6e6;padding=10px;'>

public Timer()

</pre>

调用schedule方法：

<pre style='background:#e6e6e6;padding=10px;'>

//固定时间点执行一次
public void schedule(TimerTask task, Date time)

//定时任务，从某时刻开始，定时执行
public void schedule(TimerTask task, Date firstTime, long period)

//指定延时后开始执行，定时执行
public void schedule(TimerTask task, long delay, long period)

//取消任务
public void cancel()

</pre>

















