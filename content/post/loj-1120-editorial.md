---
title: "Light OJ 1120: Rectangle Union Editorial with Multiset"
date: 2020-10-01T21:51:20+06:00
draft: false
tags: ["LOJ 1120", "Light OJ 1120", "Line Sweeping", "Multiset", "Editorial"]
index: true
description: "Light Oj 1120: Rectangle Union Editorial with Multiset"
highlight: true
---

##

Problem Link: [Click Here](http://lightoj.com/volume_showproblem.php?problem=1120)

**প্রবলেমঃ** $n$ সংখ্যক "Axis Parallel" আয়তক্ষেত্রের বামদিকের নিচের কর্নার এবং ডানদিকের উপরের কর্নারের কো-অর্ডিনেট দেওয়া থাকবে । বের করতে হবে আয়তক্ষেত্রগুলো দ্বারা আবদ্ধ ক্ষেত্রের ক্ষেত্রফল কত ?

![](https://lh3.googleusercontent.com/MYHzwBqJGGxl5gw1OR5vZiYMcYVemWvesF9I6hvFXgUGZ6DQyG0_UyuVbf0knTKHPKBuHz923pK3TRWDyBggmzwuz_S8PqhlUJmLD2xGFhwR1OhWj0zpmFPUNDXGadeEvZSBsvw4S_t6VFmoWQ)

Example: উপরের চিত্রের হলুদ আয়তক্ষত্রের কো-অর্ডিনেটদ্বয় হচ্ছে $A(0, 2)$ এবং $X(3, 6)$ । সবুজ আয়তক্ষত্রের কো-অর্ডিনেটদ্বয়ঃ $C(2, 1)$ ও $Y(5, 4)$ এবং নীল আয়তক্ষত্রের কো-অর্ডিনেটদ্বয়ঃ $W(1, 3)$ ও $M(6, 7)$ । তাহলে এই তিনটি আয়তক্ষেত্রের মিলিত আবদ্ধ ক্ষেত্রের (ধূসর শেড করা অংশ) ক্ষেত্রফলঃ $31$ ।

**সলিউশনঃ** প্রথমে আমরা বামদিক থেকে ডানদিকে এগোতে শুরু করি । $A$ বিন্দু থেকে এগোতে থাকলে দেখা যাচ্ছে যে $ABGF$ একটি আয়তক্ষেত্র গঠন করেছে । এর পরবর্তী আয়তক্ষেত্র হচ্ছে $BSIH$ । এভাবে যেতে থাকলে $CDJI, DNLJ$ এবং $OPML$ আয়তক্ষেত্র পাওয়া যায়। সুতরাং,

$(ABGF + BSIH + CDJI + DNLJ + OPML)$ এর ক্ষেত্রফল = উদাহরণের তিনটি আয়তক্ষেত্রের মিলিত আবদ্ধ ক্ষেত্রের ক্ষেত্রফল ।

এখানে দেখা যাচ্ছে, মূল কাজ হচ্ছে সাব-আয়তক্ষেত্রগুলো বের করা । ভালমত লক্ষ্য করলে দেখা যাবে পরপর দুটো $x-$স্থানাংক এবং এদের মধ্যকার সর্বনিম্ন এবং সর্বোচ্চ $y-$স্থানাংক বের করতে পারলেই সাব-আয়তক্ষেত্রগুলো পাওয়া যাবে । যেমনঃ $ABFG$ আয়তক্ষেত্রের জন্য, পরপর দুটো $x-$স্থানাংকের বিন্দু হচ্ছে $A$ এবং $W$। $B$ এবং $W$ বিন্দুর $x-$স্থানাংক একই । 
এদের মধ্যকার সর্বনিম্ন $y-$স্থানাংকের বিন্দু হচ্ছে $A$ (এবং $B$) । আর সর্বোচ্চ $y-$স্থানাংকের বিন্দু হচ্ছে $F$ (এবং $G$) । 

$F$ বিন্দুর $y-$স্থানাংক বের করা তেমন কোনো কঠিন কাজ না । $F$ বিন্দুটি হলুদ আয়তক্ষেত্রের উপরের বাহুর একটি বিন্দু । অর্থাৎ $X$ এবং $F$ বিন্দুর $y-$স্থানাংক একই । আর $X$ বিন্দুর স্থানাংক ইনপুট থেকেই পাওয়া যাচ্ছে । তো, স্থানাংকগুলো বের হয়ে গেলে $(x_2 – x_1) \times (y_2 – y_1)$ সূত্র থেকেই কোরেসপন্ডিং আয়তক্ষেত্রের ক্ষেত্রফল বের করে ফেলা সম্ভব । এখানে একটি জিনিস লক্ষণীয়, আমরা যেহেতু বামদিক থেকে ডানদিকে যাচ্ছি সেহেতু কোনো আয়তক্ষত্রের ডানদিকের বাহু অতিক্রম করে গেলে সেই আয়তক্ষেত্রের কোনো কিছু আর পরবর্তী ক্যালকুলেশনে ব্যবহার করা যাবে না । ওই আয়তক্ষেত্র সম্পর্কিত ক্যালকুলেশন ওখানেই শেষ । সাথে আরও একটি বিষয় খেয়াল রাখা জরুরি, $ABGF$ আয়তক্ষেত্রের ক্ষেত্রফল বের করার সময় যদিও আমরা নীল আয়তক্ষেত্রের $W$ বিন্দুর $x-$স্থানাংক ব্যবহার করেছি কিন্তু তখন আমরা এই নীল আয়তক্ষেত্রের কোন $y-$স্থানাংক ব্যবহার করিনি যেহেতু $ABGF$ আয়তক্ষেত্র $WH$ রেখার বামদিকে অবস্থিত । এই প্রবলেম সেগমেন্ট ট্রি, মাল্টিসেট ব্যবহার করা সহ বিভিন্ন ভাবে সলভ করা সম্ভব । **একদিক থেকে অপরদিকে যাওয়ার এই বেসিক আইডিয়াটার নামই হল লাইন সুইপিং।**

এখন, এটার কোড কীভাবে করা যায়?

কোডিং এপ্রোচ **C++** এ আলোচনা করব । একটা স্ট্রাকচারে আয়তক্ষেত্রের স্থানাংকগুলো থাকবে । যেহেতু বামদিক থেকে ডানদিক থেকে যাচ্ছি, তাই স্ট্রাকচারের একটি ইনডেক্সে একটি আয়তক্ষেত্রের বামদিকের $x-$স্থানাংক $x_1$ এবং $y_1, y_2$ থাকবে । আরেকটি ইনডেক্সে ডানদিকের $x-$স্থানাংক $x_2$ এবং $y_1, y_2$ থাকবে । $x-$স্থানাংক বামদিকের নাকি ডানদিকের সেটা বুঝার সুবিধার্থে স্ট্রাকচারে $state$ নামে একটা ভ্যারিয়েবল থাকবে । $state = 0$ হলে বামদিকের স্থানাংক আর $state = 1$ হলে ডানদিকের স্থানাংক । ইনপুট নেওয়া শেষ হলে স্ট্রাকচার $Ascending$ সর্ট করা হবে । সর্ট করার সময় শুধুমাত্র $x-$স্থানাংক কমপেয়ার করা হবে । সর্ট করা শেষে স্ট্রাকচার থেকে একটি একটি করে $x-$স্থানাংক নিতে হবে আর পরপর দুটো $x-$স্থানাংকের মধ্যকার সর্বোচ্চ এবং সর্বনিম্ন $y-$স্থানাংকগুলো পাওয়ার জন্য $y-$স্থানাংকগুলো $Multiset-$এ ইনসার্ট করতে হবে । যখন কোনো আয়তক্ষেত্রের ডানদিকের বাহুর স্থানাংক অতিক্রম করব অর্থাৎ, স্ট্রাকচারের কোনো ইনডেক্সের $state = 1$ পাব তখন তার কোরেসপন্ডিং $y-$স্থানাংকগুলো $Multiset$ থেকে ইরেজ করে দিতে হবে । পরপর দুটো $x-$স্থানাংক এবং এদের মধ্যকার সর্বোচ্চ এবং সর্বনিম্ন $y-$স্থানাংক থেকে সহজেই সাব-আয়তক্ষেত্রগুলোর ক্ষেত্রফল পাওয়া যাবে আর সেগুলোর ক্ষেত্রফল যোগ করলেই সেখান থেকে সম্পূর্ণ ক্ষেত্রফল পাওয়া যাবে ।

[বিঃদ্রঃ আয়তক্ষেত্রগুলোর ক্যালকুলেশন এবং $Multiset$ এ $y-$স্থানাংকগুলোর ইনসার্টিং/ইরেজিং আগে-পরে করার ব্যাপারে সতর্ক থাকতে হবে । ]

* **Multiset:** $Multiset$ হচ্ছে এমন একটি কনটেইনার যেখানে ইনসার্ট করা ভ্যালুগুলো বাই ডিফল্ট $Ascending$  সর্টেড হয়ে থাকে ।

* **Declaration:** ```multiset <int> mset;```

* **Iterator:** ```multiset <int> ::iterator it;```


**Some Functions:**

* **Insert:** ```mset.insert(num);``` [$num$ ভ্যারিয়েবলের ভ্যালু ইনসার্ট করে]

* **Erase (by iterator):** ```mset.erase(it);``` [$Iterator$-এর পয়েন্টকৃত মেমরির ভ্যালু ইরেজ করে]

* **Erase (by value):** ```mset.erase(num);``` [$num$-র সমান সকল ভ্যালু ইরেজ করে]

* **Find (by value):** ```mset.find(num);``` [$Multiset$ থেকে $num$-র সমান একটি ভ্যালু খুঁজে বের করে তার $iterator$ রিটার্ন করে । খুঁজে না পেলে $mset.end()$ এর সমান $iterator$ রিটার্ন করে ]

> $Multiset$ থেকে $num$ এর সমান একটি ভ্যালু ইরেজ করার উপায়ঃ
```c++
it = mset.find(num);
if( it != mset.end()) {
    mset.erase(it);
}
```

> $Multiset$ এর মিনিমাম ভ্যালুঃ
```c++
if(mset.size() != 0) {
	it = mset.begin();
	minimum = *it;
}
```

> $Multiset$ এর ম্যাক্সিমাম ভ্যালুঃ
```c++
if(mset.size() != 0) {
	it = mset.end();
	--it;
	maximum = *it;
}
```

### CODE:

### C++
-----
```c++
#include <bits/stdc++.h>
using namespace std;
 
#define ll long long
 
struct node {
    ll x, state, y1, y2;
} ara[60009];
 
bool cmp(const node &a, const node &b)
{
    return a.x < b.x;
}
 
int main()
{
    multiset <ll> ys;
    ll t, caseno = 0;
    cin >> t;
    while(t--) {
        ll n;
        scanf("%lld", &n);
        ll indx = 1;
        for(ll i = 1; i <= n; i++) {
            ll x1, x2, y1, y2;
            scanf("%lld %lld %lld %lld", &x1, &y1, &x2, &y2);
            ara[indx].x = x1, ara[indx].y1 = y1, ara[indx].y2 = y2, ara[indx].state = 0;
            indx++;
            ara[indx].x = x2, ara[indx].y1 = y1, ara[indx].y2 = y2, ara[indx].state = 1;
            indx++;
        }
 
        sort(ara + 1, ara + indx, cmp);
        ll ans = 0, lx;
 
        for(ll i = 1; i < indx; i++) {
            if(i != 1) {
                ll mny = *(ys.begin());
                ll mxy = *(--ys.end());
                ans += (ara[i].x - lx) * (mxy - mny);
            }
 
            if(ara[i].state == 0) {
                ys.insert(ara[i].y1);
                ys.insert(ara[i].y2);
            }
            else {
                ys.erase(ys.find(ara[i].y1) );
                ys.erase(ys.find(ara[i].y2) );
            }
            lx = ara[i].x;
        }
 
        printf("Case %lld: %lld\n", ++caseno, ans);
        ys.clear();
    }
 
    return 0;
}
```