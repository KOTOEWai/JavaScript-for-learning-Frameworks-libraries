
# My JavaScript Journey

JavaScript ရဲ့ အခြေခံကနေ Advanced concepts တွေအထိ စနစ်တကျ လေ့လာထားတဲ့ Practice Repository ဖြစ်ပါတယ်။

---

## Table of Contents

- [JavaScript Execution Model](#javaScript-execution-model)
  - [Js Engine](#js-engine)
  - [Web APIs](#web-apis)
  - [Event Loop](#event-loop)
  - [Callback Queue](#callback-queue)
 
- [LexicalStructure](#LexicalStructure)
- [Expressions](#Expressions)
- [DataTypes](#DataTypes)
- [Variables](#Variables)
- [Operators](#Operators)
- [Conditions](#Conditions)
- [Loops](#Loops)
- [Functions](#Functions)
- [Objects](#Objects)
- [Arrays](#Arrays)
- [Asynchronous](#Asynchronous-JavaScript)
- [TypeCasting](#TypeCasting)
- [Modules](#Modules)
- [ErrorHandling](#ErrorHandling)
- [OOP](#OOPConpects)
- [JSON](#JSON)
- [FetchAPI](#FetchAPI)
- [ES6+(Modern JavaScript)](#ES6)
- [Hoisting](#Hoisting)
- [Scope](#scope)
- [Scope Chain](#scope-chain)
- [Lexical Scoping](#lexical-scoping)
- [Closure](#closure)
---
 ##  Useful Links
* <a href="https://preparefrontend.com/blog/blog/25-javascript-best-practices-for-modern-development" title="25 JavaScript Best Practices for Modern Development">25 JavaScript Best Practices for Modern Development</a>
* [UsefulLink](https://playcode.io/javascript)
---


## JavaScript Execution Model

<img width="691" height="478" alt="image" src="https://github.com/user-attachments/assets/7dd32f98-cae3-4ce2-9c47-967549653772" />

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>



### Js Engine

 JavaScript Engine ဆိုတာ JavaScript code တွေကို Machine Code (သို့) Bytecode အဖြစ် ပြောင်းပြီး execute လုပ်ပေးတဲ့ software program တစ်ခုဖြစ်ပါတယ်။

* Google Chrome, Edge → V8 Engine

* Firefox → SpiderMonkey

* Safari → JavaScriptCore (Nitro)

* Node.js → V8 Engine ကိုပဲသုံးတယ်

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### JS Engine ရဲ့ အဓိက အစိတ်အပိုင်းများ

* 1. Memory Heap
* 2. Call Stack

### Memory Heap
```
JavaScript Engine ထဲက Memory Heap ဆိုတာ variable တွေ၊ objects တွေနဲ့
 data တွေကို သိမ်းဆည်းထားတဲ့ "ဂိုဒေါင်" တစ်ခုလိုပါပဲ။

Memory Heap ရဲ့ အဓိက အချက်များ

၁။ Unstructured Memory (ပုံသေ သတ်မှတ်မထားသော နေရာ)

Call Stack လိုမျိုး အစီအစဉ်တကျ (LIFO) သိမ်းတာမျိုး မဟုတ်ဘဲ၊ 
Heap ကတော့ ကြီးမားတဲ့ memory ဧရိယာကြီးတစ်ခုပါ။ ပုံထဲမှာလည်း data တွေကို
နေရာအနှံ့ ကြဲပြန့်ပြီး သိမ်းထားတာကို တွေ့နိုင်ပါတယ်။

၂။ ဘာတွေကို သိမ်းသလဲ?

Objects & Arrays: JavaScript မှာရှိတဲ့ reference types တွေ 
(ဥပမာ- {name: "Mg Mg"}, [1, 2, 3]) ကို ဒီမှာ သိမ်းပါတယ်။

Functions: Function definition တွေကိုလည်း memory heap ထဲမှာပဲ သိမ်းဆည်းပါတယ်။

Large Data: Stack ထဲမှာ သိမ်းဖို့ အရွယ်အစား ကြီးမားလွန်းတဲ့ data တွေကို
 ဒီနေရာမှာ နေရာချ (Allocate) ပေးပါတယ်။

၃။ Allocation vs Garbage Collection

Memory Allocation: Variable အသစ်တစ်ခု ဆောက်လိုက်တိုင်း Engine က Heap ထဲမှာ 
နေရာအလွတ်တစ်ခု ရှာပြီး သိမ်းပေးပါတယ်။

Garbage Collection: JavaScript မှာ Memory ကို ကိုယ်တိုင် ဖျက်ပေးစရာ မလိုပါဘူး။ 
Engine ထဲမှာ Garbage Collector ဆိုတာ ပါပါတယ်။
သူက Heap ထဲကို အမြဲစစ်ဆေးပြီး ဘယ် variable ကိုမှ အသုံးမပြုတော့ဘူး
(Reference မရှိတော့ဘူး) ဆိုရင် အဲဒီ memory ကို အလိုအလျောက် ပြန်သိမ်းသွားပါတယ်။


Call Stack နဲ့ ဘယ်လို ချိတ်ဆက်သလဲ?

ဒီအချက်က အရေးကြီးပါတယ်။

Object တစ်ခုကို Heap ထဲမှာ သိမ်းလိုက်တဲ့အခါ သူ့ရဲ့ 
Memory Address (Reference) လေးတစ်ခု ရလာပါတယ်။

အဲဒီ Address လေးကိုမှ Call Stack ထဲမှာရှိတဲ့ variable ထဲကို ထည့်သိမ်းလိုက်တာပါ။

ဥပမာ: const user = { name: "Aung Aung" }; လို့ ရေးရင်:

{ name: "Aung Aung" } ဆိုတဲ့ object ကြီးက Heap ထဲ ရောက်သွားမယ်။

user ဆိုတဲ့ variable နာမည်နဲ့ အဲဒီ data ရှိရာနေရာကို ညွှန်ပြတဲ့ Memory Address (Reference)လေးကတော့ Call Stack ထဲမှာ ရှိနေပါမယ်။

Memory Heap ထဲမှာ data တွေ အရမ်းများလာပြီး Garbage Collector ကလည်း
မဖျက်ပေးနိုင်တဲ့အခါ Memory Leak (စက်လေးသွားတာမျိုး) ဖြစ်တတ်ပါတယ်။

```
### Call Stack
```
Call Stack ဆိုတာ JavaScript Engine က လက်ရှိ ဘယ် function တွေကို လုပ်ဆောင်နေသလဲ၊ 
ဘယ် function ထဲမှာ ရောက်နေသလဲဆိုတာကို ခြေရာခံတဲ့ ယန္တရားတစ်ခု ဖြစ်ပါတယ်။

သူ့ကို ရိုးရိုးရှင်းရှင်း ပြောရရင် "အလုပ်စာရင်းမှတ်တဲ့ စာအုပ်" လိုမျိုးဖြစ်ပြီး 

အောက်ပါ အချက်တွေက သူ့ရဲ့ အဓိက သဘောတရားတွေပါပဲ-

၁။ LIFO (Last In, First Out)

Call Stack ဟာ LIFO စနစ်နဲ့ အလုပ်လုပ်ပါတယ်။ 

ပန်းကန်ပြားတွေကို တစ်ချပ်ပေါ်တစ်ချပ် ဆင့်တင်ထားသလိုမျိုးပါပဲ။

Push: Function တစ်ခုကို ခေါ်လိုက်တဲ့အခါ Stack ရဲ့ အပေါ်ဆုံးကို ရောက်လာပါတယ်။

Pop: Function ထဲက အလုပ်တွေ ပြီးသွားတဲ့အခါ (Return ပြန်တဲ့အခါ) အပေါ်ဆုံးကနေ ပြန်ထွက်သွားပါတယ်။

၂။ Single Call Stack

JavaScript က Single-threaded ဖြစ်တဲ့အတွက် Call Stack တစ်ခုပဲ ရှိပါတယ်။
 ဒါကြောင့် သူက တစ်ကြိမ်မှာ အလုပ်တစ်ခုတည်းကိုပဲ အာရုံစိုက်လုပ်နိုင်ပါတယ်။ 
 အပေါ်က function မပြီးမချင်း အောက်က function ဆီကို မသွားပါဘူး။

၃။ အလုပ်လုပ်ပုံ ဥပမာ


function greet() {
  sayHi();
  console.log("Greet done");
}

function sayHi() {
  console.log("Hi!");
}

greet();


greet() ကို ခေါ်လိုက်ရင် Stack ထဲကို greet ရောက်လာပါတယ်။

greet ထဲမှာမှ sayHi() ကို ထပ်ခေါ်တဲ့အတွက် Stack ရဲ့ အပေါ်ဆုံးကို sayHi ထပ်ရောက်လာပါတယ်။

sayHi အလုပ်ပြီးသွားတဲ့အခါ Stack ထဲကနေ sayHi ထွက်သွားပါတယ်။

နောက်ဆုံးမှာ greet အလုပ်ပြီးလို့ Stack ထဲကနေ greet ထွက်သွားပြီး Stack က ပြန်လွတ် (Empty) သွားပါတယ်။

၄။ Stack Overflow (Error)

Function တစ်ခုကနေ နောက်ထပ် function တစ်ခုကို အဆုံးမရှိ (Infinite) ခေါ်နေမယ်ဆိုရင်
 Stack ထဲမှာ နေရာမဆန့်တော့ဘဲ ပြည့်လျှံသွားတတ်ပါတယ်။ ဒါကို Stack Overflow လို့ ခေါ်ပါတယ်။

Call Stack နဲ့ Event Loop
ပုံထဲမှာ မြင်ရတဲ့အတိုင်း Call Stack ထဲက အလုပ်တွေ အကုန်လုံး ပြီးသွားမှသာ 
Event Loop က Callback Queue ထဲမှာ စောင့်နေတဲ့ အလုပ်တွေကို Stack ထဲကို ပို့ပေးတာ ဖြစ်ပါတယ်။
```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>



### Web APIs

```
Web APIs ဆိုတာ Browser (Web Runtime Environment) ကနေ ထောက်ပံ့ပေးထားတဲ့ 
အပိုထည့်ပေးထားတဲ့ Features  ဖြစ်ပါတယ်။

JavaScript က single-threaded ဖြစ်ပေမဲ့ နောက်ကွယ်မှာ အလုပ်တွေအများကြီးကို တစ်ပြိုင်နက်
လုပ်ဆောင်နိုင်နေတာဟာ ဒီ Web APIs တွေကြောင့် ဖြစ်ပါတယ်။

Web APIs ရဲ့ အဓိက တာဝန်များ

ပုံထဲမှာ ပြထားတဲ့အတိုင်း Web APIs တွေဟာ Engine ရဲ့ အပြင်ဘက်မှာ သီးသန့် အလုပ်လုပ်ကြတာပါ။

DOM (Document Object Model): JavaScript ကနေ HTML element တွေကို ရှာတာ၊ အရောင်ပြောင်းတာ၊ 
စာသားအသစ် ထည့်တာတွေကို လုပ်ဆောင်ပေးပါတယ်။

Timer (setTimeout/setInterval): သတ်မှတ်ထားတဲ့ အချိန်တစ်ခုအထိ စောင့်ဆိုင်းပေးတဲ့ အလုပ်ကို 
လုပ်ဆောင်ပေးပါတယ်။

Fetch APIs (Network Requests): Server ဆီကနေ data တွေ လှမ်းတောင်းတဲ့အခါ Browser ရဲ့ 
Network thread ကို သုံးပြီး အလုပ်လုပ်ပေးပါတယ်။

Other APIs: ပုံထဲမှာ ... လို့ ပြထားတဲ့အထဲမှာ Geolocation (တည်နေရာကြည့်ခြင်း)၊ 
Local Storage နဲ့ Canvas လိုမျိုး APIs တွေလည်း ပါဝင်ပါတယ်။

Web APIs က ဘယ်လို အလုပ်လုပ်သလဲ?

၁။ Request: Call Stack ကနေ setTimeout ဒါမှမဟုတ် fetch လိုမျိုး function ကို ခေါ်လိုက်တဲ့အခါ 
JS Engine က အဲဒီအလုပ်ကို Web APIs ဆီကို လွှဲပေးလိုက်ပါတယ်။

၂။ Offloading: Web APIs က အဲဒီအလုပ်ကို Browser ရဲ့ အခြား thread တွေ (ဥပမာ Network thread 
သို့မဟုတ် Timer thread) ကို သုံးပြီး နောက်ကွယ်မှာ သီးသန့် လုပ်ဆောင်ပါတယ်။

၃။ Callback: အလုပ်ပြီးသွားတဲ့အခါ (ဥပမာ Timer ပြည့်သွားတဲ့အခါ) Web API က အဲဒီအလုပ်နဲ့ သက်ဆိုင်တဲ့
Callback function ကို Callback Queue ထဲကို ပို့ပေးလိုက်ပါတယ်။

ဘာကြောင့် အရေးကြီးတာလဲ?

Web APIs မရှိဘူးဆိုရင် JavaScript ဟာ အရမ်း "နှေး" တဲ့ ဘာသာစကား ဖြစ်သွားပါလိမ့်မယ်။
ဥပမာ- Server ကနေ data လာတာကို စောင့်နေတဲ့အချိန်မှာ Web API မရှိရင် Browser ကြီး တစ်ခုလုံး 
ဘာမှလုပ်လို့မရဘဲ "Hang" နေမှာပါ။

အခုတော့ Web APIs က နောက်ကွယ်မှာ အလုပ်လုပ်ပေးနေလို့ ကျနော်တို့ Browser မှာ UI တွေကို ဆက်ပြီး
 အသုံးပြုနိုင်နေတာ ဖြစ်ပါတယ်။

```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

### Event Loop
```
Event Loop ဆိုတာ JavaScript Runtime ရဲ့ "စပယ်ယာ" သို့မဟုတ် "ယာဉ်ထိန်းရဲ" လိုမျိုး အဓိကကျတဲ့
အစိတ်အပိုင်းဖြစ်ပါတယ်။ သူက Call Stack နဲ့ Callback Queue တို့ကြားမှာ အလုပ်တွေကို ဘယ်အချိန်မှာ
လုပ်ဆောင်ရမလဲဆိုတာကို အမြဲတမ်း စီစဉ်ပေးနေတာပါ။

ပုံထဲက မြှားလေးကို ကြည့်ရင် Event Loop က အလုပ်တွေ လှည့်ပတ်နေပုံကို မြင်နိုင်ပါတယ်။

Event Loop ရဲ့ အလုပ်လုပ်ပုံ အဆင့်ဆင့်

Event Loop က အောက်ပါ အဆင့် ၃ ဆင့်ကို အမြဲတမ်း ထပ်ခါတလဲလဲ (Loop) ပတ်ပြီး လုပ်ဆောင်နေပါတယ်-

၁။ Call Stack ကို စစ်ဆေးခြင်း
Event Loop က Call Stack ထဲမှာ လက်ရှိ လုပ်နေတဲ့ code တွေ ရှိသေးလားဆိုတာကို အရင်ကြည့်ပါတယ်။
 အကယ်၍ Stack ထဲမှာ function တစ်ခုခု အလုပ်လုပ်နေတုန်းဆိုရင် သူက ဘာမှ ထပ်မလုပ်ဘဲ စောင့်နေပါတယ်။

၂။ Callback Queue ကို ကြည့်ခြင်း
Call Stack ထဲမှာ ဘာအလုပ်မှ မရှိတော့ဘူး (လွတ်သွားပြီ) ဆိုတာနဲ့ Event Loop က Callback Queue ဘက်ကို
လှည့်ကြည့်ပါတယ်။ Queue ထဲမှာ Web APIs ဆီကနေ ပြီးစီးလို့ ရောက်လာတဲ့ callback အလုပ်တွေ 
(ဥပမာ- click, timer, data) ရှိနေသလားလို့ စစ်ပါတယ်။

၃။ အလုပ်ကို လွှဲပြောင်းပေးခြင်း (The Push)
Queue ထဲမှာ အလုပ်ရှိနေရင် Event Loop က အဲဒီထဲက ပထမဆုံးအလုပ်ကို ယူပြီး Call Stack ထဲကို 
တွန်းတင် (Push) ပေးလိုက်ပါတယ်။ အဲဒီအခါမှသာ အဲဒီ callback function က တကယ် အလုပ်လုပ်တာဖြစ်ပါတယ်။

ဘာကြောင့် Event Loop က အရေးကြီးတာလဲ?

JavaScript က Single-threaded ဖြစ်ပေမဲ့ "မထစ်" ဘဲ အလုပ်လုပ်နိုင်တာဟာ ဒီ Event Loop ကြောင့်ပါ။

Non-blocking: setTimeout သို့မဟုတ် fetch လိုမျိုး ကြာမယ့်အလုပ်တွေကို Web APIs ဆီ လွှဲပေးထားနိုင်လို့ UI က 
ပုံမှန်အတိုင်း အလုပ်လုပ်နေနိုင်တာပါ။

Concurrency: အလုပ်တွေကို တစ်ပြိုင်နက် လုပ်နေသလိုမျိုး ခံစားရစေပါတယ်။ တကယ်တော့ နောက်ကွယ်မှာ 
Web APIs တွေက အလုပ်လုပ်ပေးနေပြီး Event Loop က အဖြေတွေကို အစီအစဉ်တကျ ပြန်စီပေးနေတာ ဖြစ်ပါတယ်။

```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

### Callback Queue

```
Callback Queue (သို့မဟုတ် Task Queue) ဆိုတာ Web APIs တွေဆီကနေ အလုပ်ပြီးစီးလို့ 
ပြန်လာတဲ့ function လေးတွေ Call Stack ထဲကို ပြန်ဝင်ဖို့အတွက် စောင့်ဆိုင်းရတဲ့ "တန်းစီဇယား" နေရာဖြစ်ပါတယ်။

ပုံထဲက JS Runtime Environment ရဲ့ ညာဘက်အောက်ခြေမှာ click, timer, data စတဲ့ 
အလုပ်လေးတွေ တန်းစီနေတဲ့ နေရာပဲ ဖြစ်ပါတယ်။

၁။ Callback Queue ထဲကို ဘယ်လိုရောက်လာသလဲ?
အလုပ်တစ်ခုက Callback Queue ထဲကို တိုက်ရိုက်မရောက်ပါဘူး။ အဆင့်ဆင့် ဖြတ်သန်းရပါတယ်:

Web APIs ကနေ တဆင့်လာခြင်း: ဥပမာ- setTimeout ရဲ့ timer ပြည့်သွားတဲ့အခါ သို့မဟုတ် fetch ကနေ 
data ရလာတဲ့အခါ အဲဒီအလုပ်နဲ့ သက်ဆိုင်တဲ့ callback function ကို Web API က Queue ထဲကို ပို့ပေးလိုက်တာပါ။

Events များ: User က ခလုတ်တစ်ခုကို နှိပ်လိုက်ရင် (click) အဲဒီ click event အတွက် ရေးထားတဲ့ function က 
Queue ထဲမှာ လာပြီး တန်းစီပါတယ်။

၂။ FIFO (First In, First Out) စနစ်
Callback Queue ဟာ FIFO စနစ်နဲ့ အလုပ်လုပ်ပါတယ်။ မှတ်တိုင်မှာ လူတွေ တန်းစီသလိုမျိုး 
အရင်ရောက်တဲ့ အလုပ်က အရင်ဆုံး ပြန်ထွက်ခွင့် ရပါတယ်။ Call Stack ရဲ့ LIFO စနစ်နဲ့ ဆန့်ကျင်ဘက်ပါ။

၃။ Event Loop နဲ့ ချိတ်ဆက်ပုံ
Callback Queue ထဲမှာ အလုပ်တွေ ဘယ်လောက်ပဲ ရှိနေပါစေ၊ သူတို့က Call Stack ထဲကို တန်းပြီး ဝင်လို့မရပါဘူး။

Event Loop က Call Stack ကို အမြဲကြည့်နေပြီး Stack လုံးဝ အားသွားပြီဆိုမှ Queue ထဲက အလုပ်တွေကို 
တစ်ခုချင်းစီ Stack ထဲကို ပို့ပေးတာဖြစ်ပါတယ်။

Callback Queue အမျိုးအစားများ (The Priority)
တကယ်တော့ Browser ထဲမှာ Queue က တစ်ခုတည်း မဟုတ်ပါဘူး။ ဦးစားပေးအဆင့် (Priority) ကွာခြားမှု ရှိပါတယ်:

Microtask Queue (Promises): Promise.then() ဒါမှမဟုတ် async/await တွေအတွက်ပါ။ သူက ဦးစားပေး အမြင့်ဆုံးပါ။

Callback Queue (Macrotask): setTimeout, setInterval နဲ့ DOM events တွေအတွက်ပါ။

ဥပမာ: Timer အလုပ်နဲ့ Promise အလုပ် နှစ်ခုစလုံး Queue ထဲမှာ တန်းစီနေရင် Event Loop က Promise အလုပ်
 (Microtask) ကို အရင်ယူပြီးမှ Timer အလုပ်ကို လုပ်ဆောင်ပေးမှာ ဖြစ်ပါတယ်။
```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>




## LexicalStructure

JavaScript's **lexical structure** describes the basic building blocks of the language — the rules for writing code, forming tokens, naming variables, writing comments, and more. This document explains each part clearly.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---


### 1. What is Lexical Structure?

```
JavaScript ရဲ့ Lexical Structure ဆိုတာ အခြေခံကျတဲ့ စည်းမျဉ်းတွေ (Grammar Rules) ဖြစ်ပါတယ်။ Programming language တစ်ခုမှာ စာလုံးတွေကို ဘယ်လိုပေါင်းရမယ်၊
ဘယ်လိုရေးရမယ်ဆိုတဲ့ အခြေခံ "သဒ္ဒါ" လို့ ပြောလို့ရပါတယ်။

၁။ Case Sensitivity (အကြီးအသေး ခွဲခြားခြင်း)

JavaScript ဟာ Case-sensitive ဖြစ်ပါတယ်။ ဆိုလိုတာက စာလုံးအကြီးအသေး ကွာခြားရင် အဓိပ္ပာယ် မတူတော့ပါဘူး။

let name = "Aung Aung";
let Name = "Su Su";
let NAME = "Kyaw Kyaw";
// ဒီသုံးခုလုံးဟာ variable သီးခြားစီ ဖြစ်ပါတယ်။

၂။ Whitespace and Line Breaks
JavaScript မှာ ကွက်လပ် (Space) တွေနဲ့ စာကြောင်းဆင်းတာ (Line break) တွေကို များသောအားဖြင့် လျစ်လျူရှုပါတယ်။ ဒါကြောင့် ကုဒ်တွေကို ဖတ်ရလွယ်အောင် စီရေးလို့ရပါတယ်။

// အတူတူပါပဲ
let x=5;
let x  =   5;

၃။ Literals (တိုက်ရိုက်တန်ဖိုးများ)
Literals ဆိုတာ ကုဒ်ထဲမှာ တိုက်ရိုက်ရေးသားလိုက်တဲ့ data တန်ဖိုးတွေ ဖြစ်ပါတယ်။

123 (Number literal)

"Hello" (String literal)

true (Boolean literal)

{a: 1} (Object literal)

၄။ Identifiers (အမည်ပေးခြင်း စည်းမျဉ်း)

Variables တွေ၊ Functions တွေကို နာမည်ပေးတဲ့အခါ လိုက်နာရမယ့် စည်းမျဉ်းတွေပါ။

အစစာလုံးကို အက္ခရာ (letter)၊ underscore (_) ဒါမှမဟုတ် dollar sign ($) နဲ့ စရပါမယ်။

ကိန်းဂဏန်း (0-9) နဲ့ စလို့ မရပါ။

Reserved Keywords (ဥပမာ- if, while, return) တွေကို သုံးလို့မရပါ။

၆။ Semicolons (;)
JavaScript မှာ statement တစ်ခုပြီးတိုင်း semicolon ထည့်လေ့ရှိပါတယ်။ အခုခေတ်မှာ JavaScript က အလိုအလျောက် ထည့်ပေးတဲ့စနစ် (Automatic Semicolon Insertion)
ပါဝင်ပေမဲ့ အမှားနည်းအောင် ကိုယ်တိုင်ထည့်တာက အကောင်းဆုံး အလေ့အကျင့်ပါ။

၇။ Unicode
JavaScript ကုဒ်တွေကို Unicode character set နဲ့ ရေးသားထားတာဖြစ်လို့ variable name တွေမှာ မြန်မာစာအပါအဝင် ဘာသာစကားအမျိုးမျိုးကို သုံးလို့ရပါတယ်။

let နာမည် = "မောင်မောင်";
console.log(နာမည်); // Output: မောင်မောင်



```

Lexical structure defines **how JavaScript source code is read and broken into tokens**. It includes:

* Character set
* Case sensitivity
* Whitespace
* Line terminators
* Comments
* Literals
* Identifiers & keywords
* Operators & punctuators


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 2. Character Set

JavaScript uses the **Unicode** character set.

* This means it supports characters from almost all languages.
* Variable names can include Unicode letters — even emojis (not recommended in production).

```js
let မြန်မာ = "Hello";
let  = 10;
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 3. Case Sensitivity

JavaScript is **case-sensitive**.

```js
let name = "A";
let Name = "B"; // different variable
```

Keywords are also case-sensitive.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 4. Whitespace

Whitespace includes spaces, tabs, and newlines.

* JavaScript generally **ignores whitespace**, except in specific cases.

Example:

```js
let x = 10;
let  y    =    20;
```

Both are valid.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 5. Line Terminators

Line terminators are characters such as:

* `\n` (newline)
* `\r` (carriage return)

They can affect automatic semicolon insertion (ASI), so be careful.

Example (dangerous):

```js
return
  5; // returns undefined due to ASI
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 6. Comments

### Single-line comment

```js
// This is a comment
```

### Multi-line comment

```js
/*
  This is a multi-line comment
*/
```

**Note:** Comments do not nest.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 7. Identifiers

Identifiers are names for:

* variables
* functions
* classes

Rules:

* Must start with: letter, `_`, `$`
* After first char: digits are allowed.

Valid:

```js
let _value;
let $item;
let user123;
```

Invalid:

```js
let 1user; // cannot start with digit
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 8. Keywords

These words have special meaning and cannot be used as identifiers.
Examples:

```
break, case, class, const, continue, debugger, default,
delete, do, else, export, extends, finally, for, function,
if, import, in, instanceof, let, new, return, super,
switch, this, throw, try, typeof, var, void, while, with, yield
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 9. Literals

Literals are fixed values appearing directly in code.

### Number literals

```js
let a = 10;
let b = 3.14;
let hex = 0xFF;
let binary = 0b1010;
```

### String literals

```js
let s1 = "hello";
let s2 = 'world';
let s3 = `template literal`;
```

### Boolean literals

```js
true, false
```

### Null & Undefined

```js
null;
undefined;
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 10. Operators & Punctuators

These include:

* `+ - * / %`
* `= += -= *=`
* `== === != !==`
* `{ } [ ] ( )`
* `, ; . ? :`

JavaScript treats these as tokens during lexical scanning.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 11. Automatic Semicolon Insertion (ASI)

JavaScript automatically inserts semicolons in some cases.
This can cause unexpected behavior.

Bad:

```js
let x = 5
let y = 10
(x + y).toString() // treated as function call
```

Recommended:

* Always use semicolons
  or
* Follow JS formatting rules carefully.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 12. Escape Sequences

Used inside strings:

* `\n` → newline
* `\t` → tab
* `\"` → double-quote
* `\\` → backslash

Example:

```js
let text = "Hello\nWorld";
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 13. Unicode Escapes

Identifiers may include Unicode escapes:

```js
let \u006Eame = "John"; // same as "name"
```

String Unicode:

```js
"\u{1F600}"; // 
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### Summary

JavaScript lexical structure defines **how source code is read**, including:

* Unicode support
* Case sensitivity
* Whitespace handling
* Comments
* Identifiers & keywords
* Literals
* Operators & punctuation
* ASI behavior

Understanding these rules helps you write cleaner and more predictable JavaScript.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---


## Expressions

JavaScript **expressions** are pieces of code that produce a value. They are the building blocks of statements and logic in JavaScript.

JavaScript မှာ Expression ဆိုတာ တန်ဖိုးတစ်ခု (Value) ထွက်လာအောင် လုပ်ပေးတဲ့ Code အစိတ်အပိုင်းလေးတွေကို ခေါ်တာပါ။ လွယ်လွယ်ပြောရရင် တွက်ချက်မှုတစ်ခု လုပ်လိုက်လို့ဖြစ်စေ၊ ခေါ်ယူလိုက်လို့ဖြစ်စေ အဖြေတစ်ခုခု ထွက်လာရင် အဲဒါ Expression ပါပဲ။


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 1. What Is an Expression?

```
JavaScript မှာ Expression ဆိုတာ တန်ဖိုးတစ်ခုခု (Value) ထွက်လာအောင် တွက်ချက်ပေးတဲ့ Code အပိုင်းအစကို ခေါ်တာပါ။

အရိုးရှင်းဆုံး မှတ်သားချင်ရင် - "တစ်ခုခုကို တွက်ချက်ပြီး အဖြေ (Value) တစ်ခု ပြန်ပေးရင် အဲဒါ Expression ပဲ" လို့ မှတ်နိုင်ပါတယ်။

၁။ Expression အမျိုးအစားများ

JavaScript မှာ Expression အမျိုးအစား အများကြီးရှိပါတယ်။

Arithmetic Expressions: ကိန်းဂဏန်း တွက်ချက်မှုများ။

5 + 5 (အဖြေ 10 ထွက်သည်)

10 * 2 (အဖြေ 20 ထွက်သည်)

String Expressions: စာသားများ ပေါင်းစပ်ခြင်း။

"Hello " + "World" (အဖြေ "Hello World" ထွက်သည်)

Logical Expressions: ဟုတ်/မဟုတ် စစ်ဆေးခြင်း။

10 > 5 (အဖြေ true ထွက်သည်)

Primary Expressions: အခြေခံ တန်ဖိုးများ။

true, 22, "Mg Mg" (၎င်းတို့ကိုယ်တိုင်သည်လည်း expression များ ဖြစ်သည်)

၂။ Expression vs Statement (အရေးကြီးသော ကွာခြားချက်)

Programming မှာ Expression နဲ့ Statement ကို မှားတတ်ကြပါတယ်။

Expression: တန်ဖိုးတစ်ခုကို ပြန်ပေးတယ်။ ဥပမာ- 2 + 2

Statement: အလုပ်တစ်ခုကို လုပ်ဆောင်တယ်။ ဥပမာ- let x = 10; (ဒါက variable ကြေညာတဲ့ statement ဖြစ်ပြီး ဘာတန်ဖိုးမှ ပြန်မပေးပါဘူး)

၃။ React မှာ Expression ကို ဘယ်လိုသုံးသလဲ?

React (JSX) ရေးတဲ့အခါ JavaScript Expression တွေကို Curly Braces { } ထဲမှာ ထည့်ရေးရပါတယ်။



function Welcome() {
  const name = "Aung Aung";
  
  return (
    <div>
      {/* ဤသည်မှာ Expression ဖြစ်သည် */}
      <h1>မင်္ဂလာပါ {name}</h1> 
      
      {/* ဤသည်မှာလည်း Expression ဖြစ်သည် */}
      <p>၅ ပေါင်း ၅ သည် {5 + 5} ဖြစ်သည်။</p>
    </div>
  );
}

၄။ Ternary Operator (Expression အဖြစ်သုံးသော If-Else)
React မှာ if-else statement ကို JSX ထဲမှာ ရေးလို့မရပါဘူး (ဘာလို့လဲဆိုတော့ သူက statement ဖြစ်လို့ပါ)။ ဒါကြောင့် အဖြေပြန်ပေးတဲ့ Ternary Expression ကို သုံးရပါတယ်။

JavaScript

{isLoggedIn ? "Welcome Back!" : "Please Log In"}
အနှစ်ချုပ်
Expression သည် တန်ဖိုး (Value) တစ်ခုကို ထုတ်ပေးသည်။

React ၏ JSX ထဲတွင် Expression များကိုသာ { } ဖြင့် သုံးနိုင်သည်။

```

An **expression** is any valid unit of code that **evaluates to a value**.

Examples:

```js
5          // number expression
"Hi"       // string expression
x + y      // arithmetic expression
sayHello() // function call expression
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 2. Primary Expressions

These are the simplest expressions that represent literal values or keywords.

### Examples:

```js
42
true
"hello"
null
undefined
this
```

### Identifier Reference

```js
name;
count;
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 3. Object & Array Initializer Expressions

### Object Literal

```js
let user = {
  name: "Aye",
  age: 20,
};
```

### Array Literal

```js
let numbers = [1, 2, 3];
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 4. Arithmetic Expressions

Perform mathematical operations.

```js
x + y
x - y
x * 2
x / 10
x % 3
x ** 2
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 5. String Expressions

Involves string concatenation or template literals.

```js
"Hello" + " World"
`User: ${username}`
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 6. Logical Expressions

Use `&&`, `||`, and `!`.

```js
true && false
isLoggedIn || hasToken
!isAdmin
```

Logical operators return **values**, not booleans only.

```js
"A" && "B"  // "B"
"A" || "B"  // "A"
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 7. Comparison Expressions

```js
x > y
x < y
x >= y
x === y
x !== y
```

They return `true` or `false`.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 8. Assignment Expressions

These assign values and return the assigned value.

```js
x = 10
x += 5
x -= 2
x *= 3
```

Example:

```js
let a;
console.log(a = 5); // prints 5
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 9. Function Call Expressions

Calling a function is an expression.

```js
doSomething()
alert("Hi")
sum(10, 20)
```

Even methods:

```js
user.getName()
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 10. Optional Chaining Expression

Safely access nested properties.

```js
user?.address?.city
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 11. Member Access Expressions

Access properties:

### Dot notation

```js
user.name
```

### Bracket notation

```js
user["name"]
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 12. Conditional (Ternary) Expression

Short "if...else" that returns a value.

```js
let status = age >= 18 ? "Adult" : "Child";
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 13. Arrow Function Expressions

Functions used as expressions.

```js
const add = (a, b) => a + b;
```

Arrow function without body braces implicitly returns:

```js
const double = x => x * 2;
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 14. Spread & Rest Expressions

### Spread

```js
let newArr = [...oldArr];
```

### Rest

```js
function sum(...nums) {
  return nums.reduce((a, b) => a + b);
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 15. Comma Operator Expression

Evaluates multiple expressions but returns the last one.

```js
let x = (1, 2, 3); // x = 3
```

Rarely used.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 16. `new` Expression

Used to create instances.

```js
let date = new Date();
let user = new User("Aye");
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 17. `typeof`, `void`, and `delete` Expressions

### typeof

```js
typeof 123 // "number"
```

### void

```js
void 0 // undefined
```

### delete

```js
delete obj.key
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 18. Await Expression

Used in async functions.

```js
let data = await fetch("/api");
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 19. Grouping Expressions

Control evaluation order.

```js
(2 + 3) * 4
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### Summary

JavaScript expressions:

* Always produce a **value**
* Can be simple (like `5`) or complex (like `user?.profile?.name ?? "Unknown"`)
* Form the core of JavaScript logic

Understanding expressions helps you write more powerful and flexible code.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

## DataTypes

JavaScript has a flexible and dynamic type system. Every value in JavaScript belongs to a **data type**, and understanding them is essential for writing clean, predictable code.

---

```
JavaScript မှာ Data Types ဆိုတာ ကွန်ပျူတာက ဒေတာတွေကို ဘယ်လိုအမျိုးအစားအဖြစ် မှတ်သားမလဲဆိုတဲ့ သတ်မှတ်ချက် ဖြစ်ပါတယ်။ 
JavaScript မှာ ဒေတာအမျိုးအစားတွေကို အဓိက အုပ်စုကြီး (၂) စု ခွဲထားပါတယ်။

၁။ Primitive Data Types (အခြေခံ အမျိုးအစားများ)
ဒါတွေက တန်ဖိုးတစ်ခုတည်းကိုပဲ သိမ်းဆည်းနိုင်ပြီး ပြောင်းလဲလို့မရတဲ့ (Immutable) အခြေခံအမျိုးအစား ၇ ခု ဖြစ်ပါတယ်။

String: စာသားများ။ (ဥပမာ- "Hello", 'Mingalarbar')

Number: ကိန်းဂဏန်းများ (Integer ရော Float ပါ ပါဝင်သည်)။ (ဥပမာ- 25, 3.14)

Boolean: ဟုတ်/မဟုတ်။ (true သို့မဟုတ် false)

Undefined: Variable တစ်ခုကို ကြေညာထားပြီး တန်ဖိုးမထည့်ရသေးတဲ့ အခြေအနေ။

Null: တမင်တကာ "ဘာမှမရှိဘူး" လို့ သတ်မှတ်ထားတဲ့ တန်ဖိုး (Empty value)။

Symbol: ထူးခြားပြီး တစ်ခုတည်းသော identifier အဖြစ် သုံးပါတယ်။ (ES6)

BigInt: အလွန်ကြီးမားတဲ့ ကိန်းဂဏန်းတွေ သိမ်းဖို့ သုံးပါတယ်။


၂။ Non-Primitive (Reference) Data Types

ဒါတွေကတော့ ရှုပ်ထွေးတဲ့ ဒေတာပုံစံတွေဖြစ်ပြီး တန်ဖိုးအများကြီးကို စုစည်းသိမ်းဆည်းနိုင်ပါတယ်။

1. Object: Key-value အတွဲလိုက် သိမ်းဆည်းတဲ့ ဒေတာပုံစံ။

const person = { name: "Aung Aung", age: 20 };


2. Array: စာရင်း (List) ပုံစံ သိမ်းဆည်းတာဖြစ်ပြီး တကယ်တော့ Object အမျိုးအစားထဲကပါပဲ။

const fruits = ["Apple", "Banana", "Orange"];


3. Function: အလုပ်လုပ်ဆောင်ချက်တွေကို သိမ်းဆည်းထားတဲ့ အမျိုးအစား။

၃။ Static vs Dynamic Typing

JavaScript ဟာ Dynamic Typed Language ဖြစ်ပါတယ်။ ဆိုလိုတာက Variable တစ်ခုကို ဘာ အမျိုးအစားလဲဆိုတာ ကြိုပြောစရာမလိုဘဲ ထည့်လိုက်တဲ့ တန်ဖိုးပေါ်မူတည်ပြီး အမျိုးအစားက အလိုအလျောက် ပြောင်းလဲသွားပါတယ်။

let x = 5;       // x က Number ဖြစ်သွားပြီ
x = "Hello";     // အခု x က String ဖြစ်သွားပြန်ပြီ

၄။ typeof Operator

Variable တစ်ခုက ဘာ Data Type လဲဆိုတာကို သိချင်ရင် typeof ကို သုံးပြီး စစ်ဆေးနိုင်ပါတယ်။

typeof 10;        // "number"
typeof "hi";     // "string"
typeof true;      // "boolean"
typeof undefined; // "undefined"
typeof null;      // "object" (bug)
typeof {};        // "object"
typeof [];        // "object"
typeof function(){}; // "function"


Primitive တွေက ရိုးရှင်းပြီး Memory ထဲမှာ တိုက်ရိုက်သိမ်းတယ်။

Reference (Objects) တွေက ရှုပ်ထွေးပြီး Memory ထဲမှာ Reference (လိပ်စာ) အနေနဲ့ သိမ်းတယ်။

```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>


### 1. Overview of Data Types

JavaScript has **8 main data types**:

 **Primitive Data Types** (7 types)

1. **Number**
2. **String**
3. **Boolean**
4. **Undefined**
5. **Null**
6. **Symbol**
7. **BigInt**

**Non‑Primitive Data Type** (1 type)

8. **Object**


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 2. Primitive Data Types

Primitive values:

* are **immutable**
* compared by **value**
* stored directly in memory


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

#### 2.1 Number

Represents both integers and floating‑point numbers.

```js
let age = 18;
let price = 19.99;
let infinity = Infinity;
let notNumber = NaN;
```

JavaScript does **not** have separate types for int, float, double.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

#### 2.2 String

Represents text.

```js
let name = "Aye";
let message = 'Hello';
let greeting = `Hi ${name}`; // template literal
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

#### 2.3 Boolean

Represents logical values.

```js
let isLoggedIn = true;
let hasToken = false;
```

Common Boolean operations:

```js
true && false
true || false
!true
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

#### 2.4 Undefined

A variable that has been declared but not assigned.

```js
let x;
console.log(x); // undefined
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

#### 2.5 Null

Represents an **intentional absence of value**.

```js
let user = null;
```

Note:

```js
typeof null; // "object" (JS historical bug)
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

#### 2.6 Symbol (ES6)

Unique and immutable values, often used as object keys.

```js
let id = Symbol("id");
let obj = {
  [id]: 123,
};
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

#### 2.7 BigInt (ES2020)

Used for very large integers.

```js
let big = 12345678901234567890n;
let sum = big + 10n;
```

BigInts cannot mix with normal numbers:

```js
10 + 10n; //  error
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---



### 3. Non‑Primitive Data Type

#### 3.1 Object

Objects store key‑value pairs.

```js
let user = {
  name: "Aye",
  age: 20,
};
```

Objects include:

* arrays
* functions
* dates
* regex
* maps
* sets

Everything that is **not primitive** is an **object**.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 4. Special Object Types

#### 4.1 Array

Ordered list of values.

```js
let arr = [1, 2, 3];
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

#### 4.2 Function

Functions are objects with callable behavior.

```js
function greet() {
  return "Hello";
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

#### 4.3 Date

Represents date and time.

```js
let now = new Date();
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

#### 4.4 Map

Stores key‑value pairs with any key type.

```js
let map = new Map();
map.set("name", "Aye");
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

#### 4.5 Set

Stores unique values.

```js
let set = new Set([1, 2, 2, 3]); // {1,2,3}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 5. Dynamic Typing

JavaScript is **dynamically typed**, meaning variables can change type at runtime.

```js
let x = 10;
x = "ten";
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 6. Type Checking

### typeof operator

```js
typeof 10;        // "number"
typeof "hi";     // "string"
typeof true;      // "boolean"
typeof undefined; // "undefined"
typeof null;      // "object" (bug)
typeof {};        // "object"
typeof [];        // "object"
typeof function(){}; // "function"
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 7. Difference Between Primitive & Object

| Feature     | Primitive            | Object                |
| ----------- | -------------------- | --------------------- |
| Storage     | Value                | Reference             |
| Mutable?    | No                   | Yes                   |
| Compared by | Value                | Reference             |
| Examples    | `10`, `"hi"`, `true` | `{}`, `[]`, functions |

Example:

```js
let a = { x: 1 };
let b = { x: 1 };
a === b; // false (different references)
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 8. Type Conversion

### Implicit Conversion (Coercion)

```js
"5" - 1  // 4
"5" + 1  // "51"
```

### Explicit Conversion

```js
Number("5")
String(123)
Boolean(1)
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### Summary

JavaScript data types include:

* **7 primitive types**: Number, String, Boolean, Undefined, Null, Symbol, BigInt
* **1 non‑primitive type**: Object
* JavaScript is **dynamically typed**
* Primitive values are simple and immutable
* Objects are complex and mutable

Understanding data types helps prevent bugs and write cleaner, more predictable code.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---


## Variables

Variables are one of the most fundamental parts of JavaScript. They allow you to store, update, and reuse values inside your programs.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 1. What Is a Variable?

A **variable** is a named container for storing data.

```js
let message = "Hello World";
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 2. Variable Declaration Keywords

JavaScript has **3 ways** to declare variables:

### `var`

### `let`

### `const`

Each behaves differently.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 3. `let`

Introduced in ES6, used for **block-scoped** variables.

```js
let age = 20;
age = 21; // reassign allowed
```

### Features:

* Block scoped `{}`
* Can be reassigned
* Cannot be redeclared in the same scope

Example:

```js
if (true) {
  let x = 10;
}
console.log(x); //  Error (x is block-scoped)
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 4. `const`

Also block-scoped, but **cannot be reassigned**.

```js
const PI = 3.14;
// PI = 3.15;  Error
```

### Important:

`const` does **not** make objects immutable.

```js
const user = { name: "Aye" };
user.name = "Ko"; //  allowed
```

You cannot reassign a new object:

```js
user = {}; //  not allowed
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 5. `var`

Function-scoped and older keyword.

```js
var name = "Aye";
```

### Problems with `var`:

* Not block scoped
* Can be redeclared
* Causes unexpected behavior due to **hoisting**

Example:

```js
if (true) {
  var x = 10;
}
console.log(x); //  10 (var ignores block scope)
```

Use `let` or `const` instead.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

## 6. Scope

Scope determines **where a variable can be used**.

### Types:

1. **Block Scope** (`let`, `const`)
2. **Function Scope** (`var`)
3. **Global Scope**

Example:

```js
let globalVar = "I am global"; // Global scope

function exampleFunction() {
  var functionVar = "I am function-scoped"; // Function scope (var)

  if (true) {
    let blockVar = "I am block-scoped"; // Block scope (let)
    console.log(blockVar); // Accessible here
  }

  // console.log(blockVar); // Error: blockVar is not defined here
  console.log(functionVar); // Accessible here
}

exampleFunction();
console.log(globalVar); // Accessible here
// console.log(functionVar); // Error: functionVar is not defined here
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

## 7. Hoisting

Hoisting ဆိုတာ
️ JavaScript engine က code run မလုပ်ခင်
️ variable declarations (var, let, const)
️ function declarations
တွေကို memory ထဲကို အရင် ထားသွားတဲ့ behavior ကို ဆိုလိုတာပါ။

### `var` is hoisted with **undefined** value:

```js
console.log(x); // undefined
var x = 10;
```

### `let` and `const` are hoisted but in **Temporal Dead Zone (TDZ)**:

```js
console.log(y); //  Error
let y = 10;
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 8. Initialization vs Declaration

```js
let x;       // declaration
x = 5;       // initialization

let y = 10;  // declared + initialized
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 9. Naming Variables

Variable names must follow rules.

### Valid:

```js
let name;
let _counter;
let $money;
let age2;
```

### Invalid:

```js
let 1age;   // cannot start with number
let @name;  // symbols not allowed
```

### Best Practices:

* Use camelCase → `userName`
* Use descriptive names → `totalPrice`
* Constants in ALL_CAPS → `MAX_USERS`


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 10. `let` vs `const` vs `var`

| Feature    | var             | let   | const |
| ---------- | --------------- | ----- | ----- |
| Scope      | Function        | Block | Block |
| Redeclare? |  Yes           |  No  |  No  |
| Reassign?  |  Yes           |  Yes |  No  |
| Hoisting   | Yes (undefined) | TDZ   | TDZ   |

### Recommended:

* Use **const** by default
* Use **let** when value will change
* Avoid **var**


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 11. Global Variables

Variables declared outside functions.

```js
let a = 10; // global
```

Global variables can cause bugs — use only when needed.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 12. Reassignment Examples

```js
let count = 1;
count = 2; //  allowed

const PI = 3.14;
PI = 3.2; //  not allowed
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### Summary

JavaScript variables:

* Store values for reuse
* Declared using `var`, `let`, or `const`
* `let` & `const` are block-scoped
* `var` is function-scoped and outdated
* `const` prevents reassignment
* Hoisting affects how variables behave

Understanding variables helps you control data flow and avoid bugs.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---



## Operators


### **1. What Are Operators?**

Operators are symbols that tell JavaScript to perform some action (calculations, comparisons, assignments, logic, etc.).

Example:

```js
let x = 10 + 5;
```

Here:

* `=` is an **assignment operator**
* `+` is an **arithmetic operator**


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **2. Types of Operators**

JavaScript has several categories of operators:

1. **Arithmetic Operators**
2. **Assignment Operators**
3. **Comparison Operators**
4. **Logical Operators**
5. **Unary Operators**
6. **Ternary Operator**
7. **String Operators**
8. **Bitwise Operators**
9. **Type Operators** (`typeof`, `instanceof`)
10. **Optional Chaining & Nullish Coalescing Operators**


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **3. Arithmetic Operators**

| Operator | Name                | Example        |
| -------- | ------------------- | -------------- |
| `+`      | Addition            | `5 + 2` → `7`  |
| `-`      | Subtraction         | `5 - 2` → `3`  |
| `*`      | Multiplication      | `5 * 2` → `10` |
| `/`      | Division            | `10 / 2` → `5` |
| `%`      | Modulus (remainder) | `5 % 2` → `1`  |
| `**`     | Exponentiation      | `2 ** 3` → `8` |
| `++`     | Increment           | `x++`          |
| `--`     | Decrement           | `x--`          |

Example:

```js
let a = 10;
a++;
console.log(a); // 11
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **4. Assignment Operators**

| Operator | Meaning             | Example              |
| -------- | ------------------- | -------------------- |
| `=`      | Assign              | `x = 10`             |
| `+=`     | Add and assign      | `x += 5` (x = x + 5) |
| `-=`     | Subtract and assign | `x -= 5`             |
| `*=`     | Multiply and assign | `x *= 5`             |
| `/=`     | Divide and assign   | `x /= 5`             |
| `%=`     | Modulus and assign  | `x %= 5`             |
| `**=`    | Power and assign    | `x **= 2`            |


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **5. Comparison Operators**

These return **true** or **false**.

| Operator | Meaning          | Example             |
| -------- | ---------------- | ------------------- |
| `==`     | Equal (loose)    | `5 == "5"` → true   |
| `===`    | Strict equal     | `5 === "5"` → false |
| `!=`     | Not equal        | `5 != 3`            |
| `!==`    | Strict not equal | `5 !== "5"`         |
| `>`      | Greater than     | `10 > 5`            |
| `<`      | Less than        | `5 < 10`            |
| `>=`     | Greater or equal | `10 >= 10`          |
| `<=`     | Less or equal    | `5 <= 5`            |

Example:

```js
console.log(5 === "5"); // false
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **6. Logical Operators**
```js
| Operator | Meaning | Example                   |   
| -------- | ------- | ------------------------- | 
| `&&`     | AND     | `true && false` → `false` |    
| `||`     | OR      | `true || false`→`true`    |         
| `!`      | NOT     | `!true` → `false`         |      

```
Example:

```js
let isLoggedIn = true;
let isAdmin = false;
console.log(isLoggedIn && isAdmin); // false
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **7. Unary Operators**

| Operator | Meaning                         |
| -------- | ------------------------------- |
| `typeof` | Returns data type               |
| `void`   | Evaluates but returns undefined |
| `delete` | Removes object property         |
| `+`      | Convert to number               |
| `-`      | Convert to negative number      |

Example:

```js
console.log(typeof 123); // "number"
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **8. Ternary Operator** (Conditional Operator)

Shorthand for `if/else`.

```js
condition ? valueIfTrue : valueIfFalse;
```

Example:

```js
let age = 18;
let msg = age >= 18 ? "Adult" : "Minor";
console.log(msg);
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **9. String Operator**

The `+` operator is used for string concatenation.

```js
let name = "Toe" + "Wai";
console.log(name); // "ToeWai"
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **10. Nullish Coalescing Operator (`??`)**

Returns the right-hand value when the left side is `null` or `undefined`.

```js
let user;
console.log(user ?? "Guest"); // Guest
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **11. Optional Chaining Operator (`?.`)**

Avoids errors when accessing properties of `undefined` or `null`.

```js
let user = {};
console.log(user.address?.street); // undefined, no error
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **12. Bitwise Operators**

Advanced topic — used for low-level operations.
```js
| Operator | Meaning               |    
| -------- | --------------------- | 
| `&`      | AND                   |    
|  ||      | OR                    |  
| `^`      | XOR                   |    
| `~`      | NOT                   |    
| `<<`     | Left shift            |    
| `>>`     | Right shift           |    
| `>>>`    | Zero-fill right shift |    
```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **13. Operator Precedence (Which Runs First?)**

Example:

```js
2 + 3 * 4; // 14 (because * runs before +)
```

Shortcut:

* `()` parentheses highest
* Then unary (`!`, `typeof`)
* Then `* / %`
* Then `+ -`
* Then comparisons
* Then logical
* Last: assignment


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---





## Conditions

A complete guide to how decisions are made in JavaScript — using `if`, `else`, `switch`, ternary, truthy/falsy, and more.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **1. What Are Conditions?**

Conditions allow JavaScript to make decisions based on **true/false** results.

Example:

```js
let age = 18;
if (age >= 18) {
  console.log("You are an adult");
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **2. Types of Conditional Statements**

JavaScript supports:

1. `if` statement
2. `if...else` statement
3. `else if` chain
4. `switch` statement
5. Ternary operator (`? :`)
6. `&&` and `||` short‑circuit conditions
7. Optional chaining (`?.`) with conditions


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **3. The `if` Statement**

Runs code only when the condition is **true**.

```js
if (condition) {
  // code
}
```

Example:

```js
let score = 80;
if (score > 50) {
  console.log("Pass");
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **4. `if...else` Statement**

Runs one block if true, another if false.

```js
if (condition) {
  // true block
} else {
  // false block
}
```

Example:

```js
let isOnline = false;
if (isOnline) {
  console.log("User is online");
} else {
  console.log("User is offline");
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **5. `else if` Chain**

Checks multiple conditions one by one.

```js
if (temperature > 30) {
  console.log("Hot");
} else if (temperature > 20) {
  console.log("Warm");
} else {
  console.log("Cold");
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **6. `switch` Statement**

Used when checking one value against many possible cases.

```js
switch (day) {
  case "Mon":
    console.log("Work day");
    break;
  case "Sat":
    console.log("holiday");
  case "Sun":
    console.log("Weekend");
    break;
  default:
    console.log("Unknown day");
}
```

### Why use `switch`?

* Cleaner when many `else if` conditions
* Great for checking a single variable


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **7. Ternary Operator (`? :`)**

Short version of `if...else`.

```js
condition ? valueIfTrue : valueIfFalse;
```

Example:

```js
let age = 18;
let message = age >= 18 ? "Adult" : "Minor";
console.log(message);
```

Best used for simple decisions.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **8. Truthy and Falsy Values**

JavaScript treats some values as **true** or **false** automatically.

### Falsy values:

* `false`
* `0`
* `""` (empty string)
* `null`
* `undefined`
* `NaN`

Everything else is **truthy**.

Example:

```js
if ("") console.log("This won't run");
if ("hello") console.log("This will run");
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **9. Logical Operators in Conditions**

### `&&` (AND)

Runs only if both conditions are true.

```js
if (isLoggedIn && isAdmin) {
  console.log("Welcome Admin");
}
```

### `||` (OR)

Runs if at least one condition is true.

```js
if (day === "Sat" || day === "Sun") {
  console.log("Weekend");
}
```

### `!` (NOT)

Reverses a boolean.

```js
if (!isOnline) {
  console.log("Offline");
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **10. Optional Chaining in Conditions (`?.`)**

Avoids errors when checking nested properties.

```js
if (user?.address?.city) {
  console.log("City found");
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **11. Combining Multiple Conditions**

Example:

```js
let age = 20;
let hasID = true;

if (age >= 18 && hasID) {
  console.log("You may enter");
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **12. Common Mistakes**

### Using `=` instead of `==` or `===`

```js
if (x = 5) { } // WRONG
```

This assigns, not compares.

Correct:

```js
if (x === 5) { }
```

### Forgetting `break` in switch

```js
switch(x) {
  case 1:
    console.log("One");
  case 2:
    console.log("Two"); // Both run 
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **13. Summary**

Use conditions to:

* Make decisions
* Control program flow
* Validate data
* React to user input

Tools for conditions:

* `if`, `else`, `else if`
* `switch`
* Ternary operator
* Logical operators
* Truthy/falsy evaluation


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---


## Loops

A complete guide to loops in JavaScript — how to repeat actions, iterate data, and control flow efficiently.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **1. ထပ်ခါထပ်ခါ လုပ်ဆောင်ခြင်း (What Are Loops?)**

Loops (ကွင်းဆက်များ) ဆိုတာ JavaScript မှာ ကုဒ်တစ်ခုတည်းကိုပဲ အကြိမ်ကြိမ် အခါခါ အလိုအလျောက် ပြန်လည်လုပ်ဆောင်ခိုင်းချင်တဲ့အခါ အသုံးပြုရတဲ့ နည်းလမ်းဖြစ်ပါတယ်။

**ဥပမာ -** ၁ ကနေ ၃ အထိ print ထုတ်ချင်တယ်ဆိုရင်:

```js
for (let i = 1; i <= 3; i++) {
  console.log(i);
}
```

အပေါ်ကကုဒ်ဟာ `1, 2, 3` လို့ အစဉ်လိုက် ထုတ်ပေးသွားမှာ ဖြစ်ပါတယ်။


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **2. Loop အမျိုးအစားများ (Types of Loops in JavaScript)**

JavaScript မှာ Loop အမျိုးမျိုးရှိပါတယ်။ အဓိကအားဖြင့် အောက်ပါ ၅ မျိုးကို အသုံးများပါတယ်။

1. **`for` loop** (အကြိမ်အရေအတွက် အတိအကျ သိတဲ့အခါ)
2. **`while` loop** (အကြိမ်ရေမသိဘဲ အခြေအနေ မှန်နေသရွေ့ အလုပ်လုပ်ချင်တဲ့အခါ)
3. **`do...while` loop** (အခြေအနေကို နောက်မှစစ်ပြီး အနည်းဆုံး ၁ ကြိမ်တော့ အလုပ်လုပ်ချင်တဲ့အခါ)
4. **`for...of` loop** (Array တွေနဲ့ String တွေရဲ့ တန်ဖိုးတွေကို ပတ်ချင်တဲ့အခါ)
5. **`for...in` loop** (Object တွေရဲ့ Key တွေကို ပတ်ချင်တဲ့အခါ)


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **3. The `for` Loop (`for` ကို အသုံးပြုခြင်း)**

`for` loop ကို ကိုယ်က ဘယ်နှစ်ကြိမ် အလုပ်လုပ်ရမယ်ဆိုတာ အတိအကျ သိထားတဲ့အခါ အများဆုံး သုံးပါတယ်။

**ပုံစံ (Syntax):**

```js
for (အစမှတ်လုပ်ခြင်း; အခြေအနေစစ်ဆေးခြင်း; တိုးခြင်းလျော့ခြင်း) {
  // လုပ်ဆောင်မည့် ကုဒ်များ
}
```

**ဥပမာ:** 

```js
for (let i = 0; i < 5; i++) {
  console.log("Number is:", i);
}
```

ဒီနေရာမှာ `let i = 0` (အစမှတ်), `i < 5` (၅ ထက်ငယ်နေသရွေ့ ဆက်လုပ်မယ်), `i++` (တစ်ကြိမ်ပြီးတိုင်း i ကို ၁ တိုးမယ်) ဆိုတဲ့ အဆင့် ၃ ဆင့်နဲ့ လုပ်ဆောင်ပါတယ်။


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **4. The `while` Loop (`while` ကို အသုံးပြုခြင်း)**

`while` loop ဟာ သူ့ရဲ့ အခြေအနေ (condition) အမှန် (true) ဖြစ်နေသရွေ့ အကြိမ်ကြိမ် ဆက်တိုက် အလုပ်လုပ်နေမယ့် loop အမျိုးအစားဖြစ်ပါတယ်။

```js
let i = 0;
while (i < 3) {
  console.log("While Loop:", i);
  i++; // မပါရင် Infinite loop ဖြစ်သွားပါမယ်
}
```

*သတိပြုရန်:* အမြဲတမ်း condition အမြဲမှန်နေရင် "Infinite Loop" (မရပ်တဲ့ Loop) ဖြစ်သွားပြီး စက်ဟန်း (crash/hang) သွားနိုင်ပါတယ်။


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **5. The `do...while` Loop (`do...while` ကို အသုံးပြုခြင်း)**

`do...while` loop ကတော့ `while` နဲ့ တူပေမယ့် **အခြေအနေ (condition) ကို မစစ်ခင်မှာ အနည်းဆုံး တစ်ကြိမ်တော့ အလုပ်လုပ်ပေးတာ** ကွာခြားချက်ဖြစ်ပါတယ်။

```js
let count = 5;
do {
  console.log("Count is:", count);
  count++;
} while (count < 3); // condition မှားနေပေမယ့် ပထမတစ်ကြိမ် အလုပ်လုပ်ပါတယ်
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **6. The `for...of` Loop**

Array တွေ၊ String တွေ စတဲ့ iterables (အစီအစဉ်လိုက် ရှိနေတဲ့ ဒေတာတွေ) ထဲက တန်ဖိုး (value) တစ်ခုချင်းစီကို တိုက်ရိုက်ယူပြီး ပတ်ချင်တဲ့အခါ သုံးရပါတယ်။

**ဥပမာ (Array ကို ပတ်ခြင်း):**

```js
let fruits = ["Apple", "Mango", "Banana"];
for (const fruit of fruits) {
  console.log(fruit);
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **7. The `for...in` Loop**

Object တွေရဲ့ ဂုဏ်သတ္တိများ (Properties / Keys) ကို လိုက်ပြီး အရယူချင်တဲ့အခါ သုံးပါတယ်။

**ဥပမာ (Object ကို ပတ်ခြင်း):**

```js
let student = {
  name: "Aung Aung",
  age: 20,
  major: "Computer Science"
};

for (const key in student) {
  console.log(`${key}: ${student[key]}`);
}
```

*သတိပြုရန်:* Array တွေအတွက် `for...in` ကို သုံးဖို့ မထောက်ခံပါဘူး (not recommended)။ Array နဲ့ဆိုရင် `for...of` ဒါမှမဟုတ် `forEach` သုံးပါ။


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **8. Breaking and Continuing (ရုတ်တရက် ရပ်ခြင်း နှင့် ကျော်သွားခြင်း)**

- **`break`**: Loop ကြီးတစ်ခုလုံးကနေ လုံးဝ ထွက်ချင်တဲ့အခါ သုံးပါတယ်။
- **`continue`**: လက်ရှိအကြိမ် (iteration) ကို ကျော်ပြီး နောက်တစ်ကြိမ်ကနေ ဆက်လုပ်ချင်တဲ့အခါ သုံးပါတယ်။

**`break` ဥပမာ:**

```js
for (let i = 1; i <= 5; i++) {
  if (i === 3) break; // ၃ ရောက်ရင် Loop လုံးဝ ရပ်ပါမယ်
  console.log("Break:", i); // Output: 1, 2
}
```

**`continue` ဥပမာ:**

```js
for (let i = 1; i <= 5; i++) {
  if (i === 3) continue; // ၃ ရောက်ရင် အဲဒီအကြိမ်ကို ကျော်သွားပါမယ်
  console.log("Continue:", i); // Output: 1, 2, 4, 5
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **9. Labeled Loops (Loop များကို နာမည်ပေးခြင်း)**

Nested Loop (Loop အထပ်ထပ်) တွေမှာ အပြင်ဘက် Loop ကို `break` သို့မဟုတ် `continue` လုပ်ချင်ရင် Label တွေ (Loop အမည်များ) တပ်ပေးရပါတယ်။

```js
outerLoop: for (let i = 1; i <= 3; i++) {
  for (let j = 1; j <= 3; j++) {
    if (i === 2 && j === 2) {
      break outerLoop; // i=2, j=2 ရောက်ရင် အပြင် Loop ကြီးပါ လုံးဝရပ်သွားမယ်
    }
    console.log(`i=${i}, j=${j}`);
  }
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **10. Nested Loops (Loop အထပ်ထပ် သုံးခြင်း)**

Loop တစ်ခုရဲ့ အထဲမှာ နောက်ထပ် Loop တစ်ခု ထည့်သုံးတာကို Nested Loop လို့ ခေါ်ပါတယ်။ Multi-dimensional array တို့ စစ်တုရင်ခုံပုံစံ Array တို့လို matrix-style မျိုးတွေမှာ အသုံးများပါတယ်။

```js
for (let i = 1; i <= 2; i++) {
  console.log("Outer loop #", i);
  for (let j = 1; j <= 2; j++) {
    console.log("   --- Inner loop #", j);
  }
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **11. Infinite Loops (အဆုံးမရှိ Loop များ)**

Loop ရဲ့ အဆုံးသတ် ရပ်တန့်မယ့် Condition က ဘယ်တော့မှ အလုပ်မလုပ်ဘူးဆိုရင် အဲ့ဒီ Loop ဟာ "Infinite Loop" (စက်ဟန်းသွားစေမည့် လည်ပတ်မှု) ပြောင်းသွားပါမယ်။ သတိထားရှောင်ကြဉ်ရပါမယ်။

```js
// သတိပေးချက်: စမ်းမကြည့်ပါနှင့် (Browser ဟန်းသွားပါလိမ့်မည်)
// while (true) {
//   console.log("This will never stop");
// }
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **12. ဘယ် Loop ကို ဘယ်အချိန်မှာ သုံးသင့်လဲ? (When to Use Which Loop?)**

| Loop အမျိုးအစား    | အသင့်တော်ဆုံး အသုံးပြုမှု                     |
| ------------ | ---------------------------- |
| `for`        | ပတ်မည့် အကြိမ်အရေအတွက် အတိအကျသိနေလျှင်  |
| `while`      | အကြိမ်ရေမသိဘဲ အခြေအနေ တစ်ခုပေါ်မူတည်၍ ပတ်ချင်လျှင် |
| `do...while` | အခြေအနေကို မစစ်ခင် အနည်းဆုံး ၁ ကြိမ်တော့ သေချာပေါက် ပတ်ချင်လျှင် |
| `for...of`   | Array / String တို့၏ တန်ဖိုးများကို ပတ်ချင်လျှင်   |
| `for...in`   | Object ၏ Property (Keys) များကို ပတ်ချင်လျှင် |
| `forEach`    | Array တစ်ခုတည်းကိုသာ ရိုးရိုးပတ်ချင်လျှင်  |


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **13. အဖြစ်များသော အမှားများ (Common Mistakes)**

- Condition အစစ်ခံရမယ့် ကိန်းဂဏန်း (counter) ကို `++` သို့မဟုတ် `--` နဲ့ Update မလုပ်မိဘဲ မေ့ကျန်ခဲ့ခြင်း (Infinite loop ဖြစ်စေနိုင်သည်)။
- Array တွေကို ပတ်ဖို့အတွက် `for...in` ကို သုံးမိခြင်း (Array index တွေဟာ String တွေဖြစ်သွားတတ်လို့ ရှောင်ပါ)။
- Array.forEach() ထဲမှာ `break` ဒါမှမဟုတ် `continue` သုံးဖို့ ကြိုးစားခြင်း (သုံးလို့မရပါ၊ error တက်တတ်ပါတယ်)။


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **14. အနှစ်ချုပ် (Summary)**

Loops ဟာ ပရိုဂရမ်တစ်ခုမှာ အချိန်ကုန်သက်သာစေပြီး အကြိမ်ကြိမ် လုပ်ရမယ့် အလုပ်တွေကို အလွယ်တကူ ကိုင်တွယ်နိုင်အောင် ကူညီပေးပါတယ်။ `for`, `while` တွေကို အခြေခံအားဖြင့် နားလည်ထားပြီး ၊ Array တွေ Object တွေပေါ် မူတည်ပြီး `for...of`, `for...in` နဲ့ Array method တွေဖြစ်တဲ့ `forEach()` ကဲ့သို့သော နည်းလမ်းတွေကို လိုအပ်သလို တွဲဖက် အသုံးပြုတတ်ပါစေ။


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---


## Functions

A complete guide to JavaScript functions — definitions, types, parameters, return values, arrow functions, scopes, closures, and more.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **1. What Is a Function?**

A function is a reusable block of code designed to perform a task.

Example:

```js
function greet() {
  console.log("Hello!");
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **2. Why Use Functions?**

Functions help you:

* Avoid repeating code
* Organize logic
* Make code cleaner
* Create modular programs
* Return values from operations


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **3. Function Declaration**

Also called a **named function**.

```js
function add(a, b) {
  return a + b;
}

console.log(add(2, 3)); // 5
```

### Features:

* Hoisted (usable before declaration)


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **4. Function Expression**

Function stored in a variable.

```js
const multiply = function (a, b) {
  return a * b;
};
```

### Features:

* Not hoisted
* Can be anonymous or named


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **5. Arrow Functions**

Short syntax introduced in ES6.

```js
const greet = () => {
  console.log("Hi!");
};
```

Short single-line form:

```js
const square = n => n * n;
```

### Differences from normal functions:

* No `this` binding
* No `arguments` object
* Great for callbacks


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **6. Parameters vs Arguments**

**Parameters** → variables written in function definition
**Arguments** → values passed when calling

Example:

```js
function hello(name) { // parameter
  console.log("Hello", name);
}

hello("Toe"); // argument
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **7. Default Parameters**

```js
function greet(name = "Guest") {
  console.log("Hello", name);
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **8. Rest Parameters (...args)**

Used when the number of arguments is unknown.

```js
function sum(...numbers) {
  return numbers.reduce((a, b) => a + b, 0);
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **9. Return Statement**

Functions can return a value.

```js
function add(a, b) {
  return a + b;
}
```

If no `return` → returns `undefined`.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **10. Anonymous Functions**

Functions without a name.

Used in callbacks:

```js
setTimeout(function () {
  console.log("Done");
}, 1000);
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **11. Callback Functions**

A function passed as an argument to another function.

```js
function process(callback) {
  callback();
}

process(() => console.log("Running!"));
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **12. Higher-Order Functions**

Functions that:

* Take another function as an argument, or
* Return a function

Example:

```js
function createMultiplier(x) {
  return function (y) {
    return x * y;
  };
}

const double = createMultiplier(2);
console.log(double(5)); // 10
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **13. Function Scope**

Functions create their own scope.

```js
function test() {
  let x = 10;
}
// x is not accessible here
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **14. Block Scope vs Function Scope**

* `let` & `const` → block scoped
* `var` → function scoped

```js
if (true) {
  let a = 10; // block
  var b = 20; // function
}
// b is still accessible
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **15. Closures**

A closure is when a function remembers variables from its outer scope.

```js
function outer() {
  let count = 0;
  return function () {
    count++;
    console.log(count);
  };
}

const counter = outer();
counter(); // 1
counter(); // 2
```

Closures are used in:

* Private variables
* Factory functions
* Module patterns


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **16. Named vs Anonymous Functions**

### Named function

```js
function sayHi() {}
```

### Anonymous function

```js
const sayHi = function() {}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **17. Immediately Invoked Function Expression (IIFE)**

Runs immediately after creation.

```js
(function () {
  console.log("I am an IIFE");
})();
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **18. Pure vs Impure Functions**

### Pure

* No side effects
* Same input → same output

```js
function add(a, b) {
  return a + b;
}
```

### Impure

```js
let x = 1;
function addToX(y) {
  x += y; // modifies outside variable
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **19. Functions as Objects**

Functions in JavaScript are **first-class citizens**:

* Can be stored in variables
* Can be passed as arguments
* Can be returned from functions


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### **20. Summary**

You learned:

* Function declarations & expressions
* Arrow functions
* Parameters, arguments, return values
* Scope & closures
* Callbacks & higher-order functions
* IIFE, pure functions, rest parameters

Functions are the foundation of JavaScript. Mastering them = mastering JS.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---



## Objects

JavaScript **objects** are one of the most important parts of the language. They let you store data in key-value pairs and model real-world entities.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 1. What Is an Object?

An **object** is a collection of related data and functions.

```js
const user = {
  name: "Alex",
  age: 18,
  isStudent: true,
};
```

* **Keys** → `name`, `age`, `isStudent`
* **Values** → "Alex", 18, true


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 2. Creating Objects

### **A. Object Literal (most common)**

```js
const car = {
  brand: "Toyota",
  model: "Vios",
  year: 2020
};
```

### **B. Using `new Object()`**

```js
const obj = new Object();
obj.x = 10;
obj.y = 20;
```

### **C. Using a Constructor Function**

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}

const p1 = new Person("John", 20);
```

### **D. Using Classes (ES6)**

```js
class User {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}

const u1 = new User("Alice", 25);
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 3. Accessing Object Properties

### **Dot Notation**

```js
console.log(user.name);
```

### **Bracket Notation**

```js
console.log(user["age"]);
```

Useful when:

* key contains spaces
* key is dynamic


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 4. Adding / Updating Properties

### **Add new property**

```js
user.email = "alex@example.com";
```

### **Update existing property**

```js
user.age = 19;
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 5. Deleting Properties

```js
delete user.isStudent;
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 6. Methods (Functions inside Objects)

```js
const person = {
  name: "Leo",
  greet() {
    console.log(`Hi, I am ${this.name}`);
  }
};

person.greet();
```

`this` refers to the current object.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 7. Nested Objects

```js
const student = {
  name: "Nyein",
  address: {
    city: "Yangon",
    township: "Hlaing"
  }
};
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 8. Looping Through Objects

### **for…in**

```js
for (let key in user) {
  console.log(key, user[key]);
}
```

### **Object.keys()**

```js
console.log(Object.keys(user));
```

### **Object.values()**

```js
console.log(Object.values(user));
```

### **Object.entries()**

```js
console.log(Object.entries(user));
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 9. Copying Objects

### **Shallow Copy**

```js
const copy = { ...user };
```

### **Deep Copy**

```js
const deepCopy = JSON.parse(JSON.stringify(user));
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 10. Object Destructuring

```js
const { name, age } = user;
console.log(name, age);
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 11. Optional Chaining (?.)

Prevents errors when a property might be missing.

```js
console.log(student.address?.city);
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 12. Useful Built-in Methods

* `Object.keys(obj)` → returns keys
* `Object.values(obj)` → returns values
* `Object.entries(obj)` → returns key/value pairs
* `Object.assign(target, source)` → merges objects


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 13. Real-Life Example

```js
const product = {
  id: 1,
  name: "Laptop",
  price: 980000,
  specs: {
    cpu: "i5",
    ram: "16GB"
  },
  getInfo() {
    return `${this.name} - ${this.price} Ks`;
  }
};
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### Summary

* Objects store data in key/value pairs
* Methods = functions inside objects
* Dot & bracket notation for access
* Use destructuring for cleaner code
* Objects are used everywhere in JS (React, APIs, Node.js)


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

## Asynchronous-JavaScript

### Introduction

JavaScript is **single-threaded**, but it can perform non-blocking operations using **asynchronous programming**.

Async JS allows tasks like:

* Fetching data from a server
* Reading files
* Timers
* Events

to run **without blocking** the main thread.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### Why Asynchronous JavaScript?

Without async code:

* Long operations freeze the page
* UI becomes unresponsive
* Slow APIs block execution

Async JS lets the browser handle tasks in the background.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 1. The Event Loop

The **Event Loop** is the system that manages asynchronous operations.

JavaScript uses:

* **Call Stack** → executes code
* **Web APIs** → timers, fetch, DOM
* **Callback Queue** → completed tasks
* **Event Loop** → sends tasks to stack when it's empty

This enables async behavior even though JS has one thread.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 2. Callbacks

A **callback** is a function passed as an argument.

```js
function getData(callback) {
  setTimeout(() => {
    callback("Done!");
  }, 1000);
}

getData(result => {
  console.log(result);
});
```

### Callback Hell

Nested callbacks become hard to read:

```js
a(() => {
  b(() => {
    c(() => {
      d();
    });
  });
});
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 3. Promises

A **Promise** represents a value that will be available in the future.

### States:

* **pending**
* **fulfilled**
* **rejected**

### Example

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Success"), 1000);
});

promise.then(result => console.log(result));
```

### `.catch()` for errors

```js
promise.catch(err => console.error(err));
```

### `.finally()`

```js
promise.finally(() => console.log("Done"));
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 4. Async / Await

Introduced in ES2017, **async/await** lets you write asynchronous code like synchronous code.

### Example

```js
async function loadData() {
  const result = await fetch("/api/data");
  const data = await result.json();
  console.log(data);
}

loadData();
```

### Try/Catch for errors

```js
async function run() {
  try {
    const res = await fetch("/invalid");
  } catch (err) {
    console.log("Error:", err);
  }
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 5. Microtasks vs Macrotasks

### Microtasks

* Promise callbacks (`then`, `catch`)

### Macrotasks

* `setTimeout`
* `setInterval`

Execution order:

1. Call Stack
2. **All microtasks**
3. One macrotask
4. Repeat


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 6. Common Asynchronous Functions

### `setTimeout`

```js
setTimeout(() => console.log("Hi"), 1000);
```

### `setInterval`

```js
setInterval(() => console.log("Tick"), 1000);
```

### `fetch`

```js
fetch("/api").then(res => res.json()).then(data => console.log(data));
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 7. Parallel, Sequential, and Race

### Sequential

```js
await task1();
await task2();
```

### Parallel

```js
await Promise.all([task1(), task2()]);
```

### Race

```js
Promise.race([task1(), task2()]);
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 8. Error Handling

### Promise error

```js
promise.catch(err => console.error(err));
```

### Async/await error

```js
try {
  await something();
} catch (err) {
  console.error(err);
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 9. Real-World Examples

### Fetching API Data

```js
async function getUsers() {
  const res = await fetch("https://jsonplaceholder.typicode.com/users");
  return res.json();
}
```

### File Reading (Node.js)

```js
const fs = require("fs/promises");

async function readFile() {
  const data = await fs.readFile("text.txt", "utf8");
  console.log(data);
}
```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>



## TypeCasting

### Introduction

JavaScript is a **dynamically typed language**, meaning variables can change their type at runtime.
Type casting (also called **type coercion**) is the process of **converting one data type to another**.

JavaScript performs two types of type casting:

* **Implicit (Automatic) Type Coercion**
* **Explicit (Manual) Type Conversion**


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 1. Implicit Type Coercion (Automatic)

JavaScript automatically converts types during operations.

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>


### String Coercion

When one operand is a string → JS converts the other to **string**.

```js
"5" + 3;   // "53"
5 + "3";   // "53"
```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>


### Number Coercion

When using `-`, `*`, `/`, `%`, JS converts both values to **numbers**.

```js
"10" - 2;   // 8
"6" * "2"; // 12
"20" / 5;   // 4
```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>


### Boolean Coercion

Values are converted to **true/false** in logical contexts.

Falsy values:

```
false, 0, "", null, undefined, NaN
```

Everything else → `true`

```js
Boolean(0);      // false
Boolean("Hi");  // true
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 2. Explicit Type Conversion (Manual)

You convert types using built-in functions.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

#### 2.1 Convert to Number

Use:

* `Number(value)`
* `parseInt(value)`
* `parseFloat(value)`
* Unary `+value`

```js
Number("10");     // 10
parseInt("10px"); // 10
parseFloat("9.5"); // 9.5
+"5";             // 5
```

### Invalid conversions

```js
Number("hello"); // NaN
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

#### 2.2 Convert to String

Use:

* `String(value)`
* `.toString()`

```js
String(123);     // "123"
(100).toString(); // "100"
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

#### 2.3 Convert to Boolean

Use:

* `Boolean(value)`
* `!!value`

```js
Boolean(1);  // true
Boolean(0);  // false
!!"hi";     // true
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 3. Common Coercion Scenarios

### With `+` operator

* If one operand = string → convert to string

```js
1 + "2"; // "12"
```

### With comparison `==`

JavaScript tries to convert values to the same type

```js
"5" == 5; // true
true == 1; // true
false == 0; // true
```

### Strict comparison `===`

No type coercion

```js
"5" === 5; // false
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 4. Type Coercion Table

| Expression      | Result |
| --------------- | ------ |
| `true + 1`      | 2      |
| `false + 1`     | 1      |
| `"5" * 2`       | 10     |
| `"5" + 2`       | "52"   |
| `null + 1`      | 1      |
| `undefined + 1` | NaN    |


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 5. Checking Types

```js
typeof "hello"; // "string"
typeof 50;      // "number"
typeof true;    // "boolean"
typeof null;    // "object" (known JS bug)
typeof []       // "object"
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 6. Best Practices

 Use **explicit conversion** instead of relying on coercion
 Avoid using loose equality (`==`)
 Use strict equality (`===`)
 Use `Number()` instead of `parseInt()` when possible
 Be careful with `+` → it triggers string coercion


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---


## Modules

### Introduction

JavaScript **modules** allow you to split your code into reusable, maintainable files. Each module can **export** variables/functions/classes and another file can **import** them.

Modules help with:

* Better code organization
* Reusability
* Avoiding global namespace pollution
* Easier maintenance
* Cleaner architecture

Modern JavaScript uses **ES Modules (ESM)**.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 1. ES Modules (ESM)

The modern module system using:

```js
import ... from "module";
export ...;
```

Supported in:

* Browsers (using `<script type="module">`)
* Node.js (with `.mjs` or package.json type: module)


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 2. Exporting

Exports allow a file to expose code so other files can import it.

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>


### Named Exports

You can export multiple items.

```js
// math.js
export const PI = 3.14;
export function add(a, b) {
  return a + b;
}
```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>


### Default Export

One file can have **only one default export**.

```js
// greet.js
export default function greet(name) {
  console.log(`Hello, ${name}`);
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 3. Importing

### Import Named Exports

```js
import { PI, add } from "./math.js";
console.log(add(2, 3));
```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>


### Import Default Export

```js
import greet from "./greet.js";
greet("Koko");
```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>


### Rename Imports

```js
import { add as sum } from "./math.js";
```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>


### Import Everything

```js
import * as math from "./math.js";
math.add(2, 3);
math.PI;
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 4. Mixing Exports

You can mix named + default exports.

```js
// utils.js
export default function log(msg) {
  console.log(msg);
}
export const version = "1.0.0";
```

```js
import log, { version } from "./utils.js";
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 5. Module Execution

* A module is executed **only once**, even if imported multiple times.
* Imports are read **before** code runs (top-level scope).
* Modules always run in **strict mode**.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 6. Using Modules in Browser

```html
<script type="module" src="/app.js"></script>
```

Features:

* Modules load **deferred** automatically
* `import` works inside scripts


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 7. Modules in Node.js

### Option 1: Use `.mjs`

```bash
node app.mjs
```

### Option 2: Add to package.json

```json
{
  "type": "module"
}
```

Then use:

```js
import { add } from "./math.js";
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 8. CommonJS vs ES Modules

| Feature  | CommonJS       | ES Modules                 |
| -------- | -------------- | -------------------------- |
| Syntax   | require/export | import/export              |
| Loaded   | runtime        | compile-time               |
| File Ext | .js            | .mjs or js w/ type: module |
| Default  | Node.js        | Browser + Node             |

### CommonJS Example

```js
const fs = require("fs");
module.exports = {};
```

### ES Module Example

```js
import fs from "fs";
export default {};
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 9. Dynamic Imports

Useful for lazy loading or conditional imports.

```js
if (true) {
  const module = await import("./math.js");
  console.log(module.add(2, 3));
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 10. Real-World Example Structure

```
project/
 ├─ utils/
 │   ├─ math.js
 │   └─ helpers.js
 ├─ components/
 │   └─ navbar.js
 └─ app.js
```

### math.js

```js
export function multiply(a, b) {
  return a * b;
}
```

### app.js

```js
import { multiply } from "./utils/math.js";
console.log(multiply(4, 5));
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 11. Best Practices

 Use **named exports** when exporting many items
 Use **default export** when exporting a single main value
 Keep file names **descriptive**
 Group similar modules into folders
 Avoid circular imports
 Prefer ES Modules over CommonJS for new projects


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

## ErrorHandling

### Introduction

**Error handling** in JavaScript allows you to catch and manage errors so your program doesn’t crash unexpectedly.
Errors can happen due to:

* Invalid input
* Network failure
* Wrong code logic
* Unexpected API responses
* Missing files (Node.js)

JavaScript provides tools like **try/catch**, **throw**, **finally**, and **error objects** to manage these situations safely.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 1. Types of Errors in JavaScript

### Syntax Error

Code cannot run due to incorrect syntax.

```js
console.log("Hello"   // missing parenthesis
```

### Reference Error

Using a variable that does not exist.

```js
console.log(x); // x is not defined
```

### Type Error

Wrong operation on the wrong data type.

```js
const num = 5;
num.toUpperCase(); // TypeError
```

### Range Error

Invalid length or number range.

```js
new Array(-2); // RangeError
```

### Custom Errors (using throw)

You can throw your own custom errors.

```js
throw new Error("Something went wrong!");
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 2. try / catch

Used to handle errors gracefully.

```js
try {
  const result = dangerousFunction();
} catch (error) {
  console.log("Error happened:", error);
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 3. finally Block

Runs **always**, whether there's an error or not.

```js
try {
  console.log("Trying...");
} catch (err) {
  console.log("Error!");
} finally {
  console.log("Always runs");
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 4. Throwing Custom Errors

Use `throw` to trigger your own error.

```js
function divide(a, b) {
  if (b === 0) {
    throw new Error("Cannot divide by zero");
  }
  return a / b;
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 5. The Error Object

JavaScript error objects contain useful information:

```js
try {
  throw new Error("Failed to load");
} catch (e) {
  console.log(e.name);    // "Error"
  console.log(e.message); // "Failed to load"
  console.log(e.stack);   // stack trace
}
```

Common error types:

* Error
* TypeError
* ReferenceError
* SyntaxError
* RangeError
* EvalError


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 6. Error Handling in Asynchronous Code

### Callbacks

```js
fs.readFile("test.txt", (err, data) => {
  if (err) return console.error(err);
  console.log(data);
});
```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>


### Promises

```js
fetch("/api")
  .then(res => res.json())
  .catch(err => console.log("Error:", err));
```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>


### async / await with try/catch

```js
async function loadData() {
  try {
    const res = await fetch("/api/users");
    const data = await res.json();
  } catch (error) {
    console.log("Failed to load:", error);
  }
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 7. Global Error Handling

### Browser

```js
window.onerror = function(message, source, line, column, error) {
  console.log("Global Error: ", message);
};
```

### Node.js

```js
process.on("uncaughtException", (err) => {
  console.log("Unhandled Exception:", err);
});
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 8. Validation Errors

Throw custom errors when data is invalid.

```js
function register(user) {
  if (!user.name) {
    throw new Error("Name is required");
  }
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 9. Error Logging (Best Practices)

 Log errors clearly
 Include timestamp
 Never show internal errors to users
 Use monitoring tools (Sentry, LogRocket, Datadog)
 Use custom error classes for clarity


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 10. Creating Custom Error Classes

```js
class ValidationError extends Error {
  constructor(message) {
    super(message);
    this.name = "ValidationError";
  }
}

throw new ValidationError("Invalid email format");
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 11. Best Practices

 Use try/catch only where needed
 Throw meaningful error messages
 Clean and consistent error structure
 Handle async errors with `try/catch` or `.catch()`
 Avoid silent error handling
 Use custom errors for validation and logic problems


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---



## OOPConpects

JavaScript supports **Object-Oriented Programming (OOP)** using prototypes and ES6 classes.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### What is OOP?

OOP is a programming paradigm that organizes code into **objects** — each object contains data (properties) and behavior (methods).

JavaScript implements OOP using:

* **Objects**
* **Prototypes**
* **Constructor functions**
* **Classes (ES6)**


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### Core OOP Concepts

### 1. **Classes**

A `class` is a blueprint for creating objects.

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(`Hello, my name is ${this.name}`);
  }
}

const p1 = new Person("John", 20);
p1.greet();
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

## 2. **Objects**

Objects are instances created from classes.

```js
const user = new Person("Alice", 25);
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 3. **Constructor**

The `constructor()` method initializes object properties.

```js
class Car {
  constructor(brand, year) {
    this.brand = brand;
    this.year = year;
  }
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 4. **Encapsulation**

Encapsulation hides internal details and protects data.

Modern JS supports **private fields**:

```js
class BankAccount {
  #balance = 0; // private

  deposit(amount) {
    this.#balance += amount;
  }

  getBalance() {
    return this.#balance;
  }
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 5. **Abstraction**

Abstraction shows only essential features and hides complexity.

```js
class CoffeeMachine {
  start() {
    this._heatWater();
    console.log("Coffee ready!");
  }

  _heatWater() { // Pretend private
    console.log("Heating...");
  }
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 6. **Inheritance**

One class can inherit properties & methods from another.

```js
class Animal {
  speak() {
    console.log("Animal sound");
  }
}

class Dog extends Animal {
  speak() {
    console.log("Woof!");
  }
}

const d = new Dog();
d.speak();
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 7. **Polymorphism**

Child classes can override parent class methods.

Example above: `Dog.speak()` overrides `Animal.speak()`.

Another example:

```js
class Shape {
  area() {
    return 0;
  }
}

class Circle extends Shape {
  constructor(r) {
    super();
    this.r = r;
  }

  area() {
    return Math.PI * this.r * this.r;
  }
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 8. **The "this" Keyword**

`this` refers to the current object instance.

```js
class User {
  constructor(name) {
    this.name = name; // "this" = current object
  }
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 9. **Static Methods**

Static methods belong to the class (not instances).

```js
class MathUtils {
  static add(a, b) {
    return a + b;
  }
}

MathUtils.add(5, 3); // OK
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 10. **Prototypes (Behind the Scenes)**

Before ES6 classes, OOP in JS used prototypes.

```js
function Person(name) {
  this.name = name;
}

Person.prototype.greet = function () {
  console.log("Hello " + this.name);
};
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### Summary Table

| Concept        | Description                       |
| -------------- | --------------------------------- |
| Class          | Blueprint for objects             |
| Object         | Instance of a class               |
| Constructor    | Initializes properties            |
| Encapsulation  | Hiding data, using private fields |
| Abstraction    | Hiding complexity                 |
| Inheritance    | Reusing parent class features     |
| Polymorphism   | Overriding methods                |
| Static methods | Methods used on class, not object |
| Prototype      | JS's underlying OOP system        |


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### Real-World Example

```js
class User {
  constructor(username) {
    this.username = username;
  }

  login() {
    console.log(this.username + " logged in");
  }
}

class Admin extends User {
  deleteUser(user) {
    console.log(`Admin deleted ${user.username}`);
  }
}

const admin = new Admin("Admin1");
const user = new User("Tom");

admin.login();
admin.deleteUser(user);
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---


## JSON

JSON is one of the most important data formats in modern web development.
It is used to store, exchange, and transport data between servers, APIs, and applications.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### What is JSON?

JSON stands for **JavaScript Object Notation**.

It is:

* A **text-based** data format
* Lightweight
* Easy for humans to read
* Easy for machines to parse
* Language-independent (not only for JavaScript)

Example JSON:

```json
{
  "name": "John",
  "age": 25,
  "isStudent": false,
  "skills": ["HTML", "CSS", "JavaScript"]
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### JSON vs JavaScript Object

## JSON

```json
{
  "name": "John",
  "age": 25
}
```

* Keys are always **strings** (double quotes)
* Cannot contain functions
* Only supports values: string, number, object, array, boolean, null

### JavaScript Object

```js
const user = {
  name: "John",
  age: 25,
  greet() {
    console.log("Hello");
  }
};
```

* Keys can be without quotes
* Can contain methods & variables


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### Valid JSON Data Types

| Type    | Example      |
| ------- | ------------ |
| String  | "Hello"      |
| Number  | 10, 2.5      |
| Boolean | true / false |
| Object  | { "a": 1 }   |
| Array   | [1, 2, 3]    |
| Null    | null         |

 JSON does **not** support:

* Functions
* Comments
* Undefined
* Date objects (must be a string)


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### Converting JSON in JavaScript

### 1. `JSON.stringify()` → Convert JS object to JSON string

```js
const user = {
  name: "Alice",
  age: 20
};

const jsonData = JSON.stringify(user);
console.log(jsonData);
// "{"name":"Alice","age":20}""
```

This is often used when:

* Sending data to a server
* Saving data in localStorage


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 2. `JSON.parse()` → Convert JSON string to JS object

```js
const json = '{"name":"Alice","age":20}';

const obj = JSON.parse(json);
console.log(obj.name); // Alice
```

Used when:

* Receiving data from API
* Reading from localStorage


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### ️ Real API Example

```js
fetch("https://api.example.com/user")
  .then(res => res.json()) // parse JSON response
  .then(data => console.log(data));
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### JSON in Local Storage

```js
const user = { name: "Tom", age: 30 };

// Save
localStorage.setItem("user", JSON.stringify(user));

// Read
const data = JSON.parse(localStorage.getItem("user"));
console.log(data.name);
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### Common Errors

### 1. Using single quotes in JSON

```json
{
  'name': 'John'  //  invalid
}
```

JSON requires **double quotes**.

---

### 2. Trailing commas

```json
{
  "name": "John",
  "age": 30,   //  invalid
}
```

---

### 3. Comments not allowed

```json
{
  "name": "John" //  comments not allowed
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### JSON.stringify Additional Options

### Pretty Format

```js
const json = JSON.stringify(user, null, 2);
console.log(json);
```

Output:

```json
{
  "name": "Alice",
  "age": 20
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### Summary

| Feature     | Description                                  |
| ----------- | -------------------------------------------- |
| JSON        | Data exchange format                         |
| stringify() | JS → JSON string                             |
| parse()     | JSON string → JS object                      |
| Data types  | string, number, object, array, boolean, null |
| Used in     | APIs, databases, configs, localStorage       |


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

## FetchAPI

The **Fetch API** is a modern, promise-based way to make HTTP requests in JavaScript.
It is widely used in web development for calling APIs, sending data to servers, and retrieving JSON.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### What is Fetch API?

`fetch()` is a built-in browser function that allows you to request resources over the network.

Basic syntax:

```js
fetch(url, options?)
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 1. Basic GET Request

```js
fetch("https://api.example.com/users")
  .then(res => res.json())
  .then(data => console.log(data))
  .catch(err => console.log(err));
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 2. Using Async/Await (Recommended)

```js
async function getUsers() {
  try {
    const res = await fetch("https://api.example.com/users");
    const data = await res.json();
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 3. POST Request (Send Data)

```js
async function createUser() {
  const newUser = {
    name: "John",
    age: 22
  };

  const res = await fetch("https://api.example.com/users", {
    method: "POST",
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify(newUser)
  });

  const data = await res.json();
  console.log(data);
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 4. PUT Request (Update Data)

```js
fetch("https://api.example.com/users/1", {
  method: "PUT",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ name: "Updated User" })
})
  .then(res => res.json())
  .then(data => console.log(data));
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 5. DELETE Request

```js
await fetch("https://api.example.com/users/1", {
  method: "DELETE"
});
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 6. Handling Errors Correctly

`fetch()` **does NOT** throw errors for HTTP status codes like `404` or `500`.
You must check them manually:

```js
async function loadData() {
  try {
    const res = await fetch("https://api.example.com/data");

    if (!res.ok) {
      throw new Error(`HTTP Error: ${res.status}`);
    }

    const data = await res.json();
    console.log(data);
  } catch (error) {
    console.error("Fetch Error:", error);
  }
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 7. Sending Headers

```js
fetch(url, {
  headers: {
    "Authorization": "Bearer token123",
    "Content-Type": "application/json"
  }
});
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 8. Fetching Text, Blob, FormData, etc.

### Text

```js
const res = await fetch("/info.txt");
const text = await res.text();
```

### Blob (images/files)

```js
const res = await fetch("/image.png");
const blob = await res.blob();
```

### FormData

```js
const formData = new FormData();
formData.append("photo", fileInput.files[0]);

await fetch("/upload", {
  method: "POST",
  body: formData
});
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 9. Abort Fetch Request

Cancel a long-running request:

```js
const controller = new AbortController();

fetch(url, { signal: controller.signal });

controller.abort();
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 10. Fetch Options Summary

| Option  | Description                            |
| ------- | -------------------------------------- |
| method  | GET, POST, PUT, DELETE                 |
| headers | Additional metadata (JSON, Auth, etc.) |
| body    | Request payload                        |
| signal  | AbortController for canceling          |


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 11. Real-World Example: Pagination

```js
async function loadPage(page) {
  const res = await fetch(`/api/users?page=${page}`);
  const data = await res.json();
  console.log(data);
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 12. Fetch in Next.js (App Router)

```js
export async function GET() {
  const res = await fetch("https://api.example.com/products", {
    cache: "no-store"
  });
  const data = await res.json();
  return Response.json(data);
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### Summary

* `fetch()` is Promise-based
* Supports GET, POST, PUT, DELETE
* Use `res.json()` to convert API response
* Must manually check `res.ok`
* Supports headers, FormData, Blob, File uploads
* Works great with async/await


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---
## ES6

ES6+ refers to **ECMAScript 2015 (ES6) and all versions after it**.
It introduced many powerful features that make JavaScript cleaner, faster, and easier to write.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 1. `let` and `const`

### `let`

* Block scoped
* Can be reassigned

```js
let age = 20;
age = 21;
```

### `const`

* Block scoped
* Cannot be reassigned

```js
const name = "Alex";
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 2. Arrow Functions

Shorter, cleaner syntax.

```js
const add = (a, b) => a + b;
```

Arrow functions **do not have their own `this`**.


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 3. Template Literals

Use backticks `` ` ``, variable interpolation, and multiline strings.

```js
const name = "John";
console.log(`Hello ${name}!`);
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 4. Default Parameters

```js
function greet(name = "Guest") {
  console.log(`Hello ${name}`);
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 5. Destructuring

### Object Destructuring

```js
const user = { name: "Tom", age: 30 };
const { name, age } = user;
```

### Array Destructuring

```js
const nums = [10, 20, 30];
const [a, b] = nums;
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 6. Spread Operator `...`

### Spread into arrays

```js
const arr1 = [1,2];
const arr2 = [...arr1, 3, 4];
```

### Spread into objects

```js
const user = { name: "Alice" };
const newUser = { ...user, age: 22 };
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 7. Rest Parameters

```js
function sum(...nums) {
  return nums.reduce((a, b) => a + b);
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 8. Enhanced Object Literals

```js
const name = "John";
const age = 20;

const user = {
  name,
  age,
  greet() {
    console.log("Hello!");
  }
};
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 9. Modules (import/export)

```js
// math.js
export function add(a, b) { return a + b; }

// app.js
import { add } from "./math.js";
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 10. Classes

```js
class Person {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} speaks`);
  }
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 11. Promises

```js
const getData = () => new Promise((resolve) => {
  resolve("Done");
});
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 12. Async/Await

Cleaner way to handle asynchronous code.

```js
async function load() {
  const data = await fetch("/api");
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 13. Optional Chaining `?.`

Safer property access.

```js
console.log(user?.address?.city);
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 14. Nullish Coalescing `??`

Returns right value only if left is `null` or `undefined`.

```js
const username = input ?? "Guest";
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 15. `Map` and `Set`

### Set

```js
const set = new Set([1,2,2,3]);
```

### Map

```js
const map = new Map();
map.set("name", "John");
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 16. Iterators & for...of

```js
for (const value of [10,20,30]) {
  console.log(value);
}
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 17. Symbol

Unique identifier.

```js
const id = Symbol("id");
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 18. BigInt

Large integers.

```js
const n = 12345678901234567890n;
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 19. Dynamic Import

```js
import("./module.js").then(module => {
  module.run();
});
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 20. Promise.all, Promise.any, Promise.race

```js
await Promise.all([p1, p2]);
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### Summary Table

| Feature           | Description            |
| ----------------- | ---------------------- |
| let/const         | Block-scoped variables |
| Arrow functions   | Shorter, no `this`     |
| Template literals | Backtick strings       |
| Destructuring     | Extract values         |
| Spread/Rest       | Expand or collect      |
| Classes           | OOP support            |
| Promises          | Async operations       |
| Async/await       | Cleaner async          |
| Optional chaining | Safe access            |
| Modules           | import/export          |


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

## BrowserAPIs

Browser APIs (Application Programming Interfaces) are built-in features provided by web browsers that allow JavaScript to interact with the browser and the environment.

They let you:

* Manipulate the DOM
* Handle user events
* Store data
* Work with multimedia
* Access device features
* Fetch network resources


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 1. DOM (Document Object Model) API

The DOM API lets JavaScript interact with HTML elements.

### Select Elements

```js
document.getElementById("title");
document.querySelector(".item");
```

### Modify Elements

```js
const title = document.querySelector("h1");
title.textContent = "Updated Title";
title.style.color = "blue";
```

### Create & Append Elements

```js
const div = document.createElement("div");
div.textContent = "Hello";
document.body.appendChild(div);
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 2. Events API

Handle clicks, input, submit, keyboard, scroll, etc.

```js
document.querySelector("button").addEventListener("click", () => {
  console.log("Button clicked!");
});
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 3. Storage API (localStorage & sessionStorage)

### localStorage

* Stores data **permanently** (until deleted)

```js
localStorage.setItem("theme", "dark");
localStorage.getItem("theme");
```

### sessionStorage

* Stores data for **one tab session**

```js
sessionStorage.setItem("token", "123");
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 4. Fetch API

Used to make HTTP requests.

```js
fetch("/api/data")
  .then(res => res.json())
  .then(data => console.log(data));
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### ️ 5. Timers (setTimeout, setInterval)

```js
setTimeout(() => {
  console.log("Runs once after 2 seconds");
}, 2000);

setInterval(() => {
  console.log("Repeats every second");
}, 1000);
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 6. Geolocation API

Retrieve user location (with permission).

```js
navigator.geolocation.getCurrentPosition(pos => {
  console.log(pos.coords.latitude, pos.coords.longitude);
});
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 7. Media Devices & Camera API

Access camera/microphone.

```js
navigator.mediaDevices.getUserMedia({ video: true })
  .then(stream => console.log(stream));
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 8. Audio & Video API

Control audio and video elements.

```js
document.querySelector("video").play();
document.querySelector("audio").pause();
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### ️ 9. Clipboard API

Copy text to clipboard.

```js
navigator.clipboard.writeText("Copied!");
```

Paste (with permission):

```js
navigator.clipboard.readText().then(text => console.log(text));
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### ️ 10. Canvas API

Used for drawing graphics.

```js
const canvas = document.getElementById("myCanvas");
const ctx = canvas.getContext("2d");
ctx.fillStyle = "red";
ctx.fillRect(10, 10, 100, 100);
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 11. History API

Manage browser navigation.

```js
history.pushState({ page: 1 }, "Title", "?page=1");
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 12. Web Storage API

Includes:

* `localStorage`
* `sessionStorage`
* `Cookies` (via document.cookie)


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### ️ 13. WebSocket API

Real-time communication.

```js
const socket = new WebSocket("ws://example.com");
socket.onmessage = event => console.log(event.data);
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 14. Notification API

Show system notifications.

```js
Notification.requestPermission().then(() => {
  new Notification("Hello!");
});
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 15. Intersection Observer API

Detect when elements enter the viewport.

```js
const observer = new IntersectionObserver(entries => {
  if (entries[0].isIntersecting) {
    console.log("Element visible");
  }
});

observer.observe(document.querySelector("#target"));
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### 16. URL & URLSearchParams API

```js
const url = new URL(window.location);
console.log(url.searchParams.get("id"));
```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

### Summary Table

| API          | Purpose                       |
| ------------ | ----------------------------- |
| DOM API      | Work with HTML elements       |
| Events API   | User interactions             |
| Storage API  | localStorage / sessionStorage |
| Fetch API    | Make network requests         |
| Geolocation  | Get location                  |
| MediaDevices | Camera/Mic access             |
| Canvas       | Draw graphics                 |
| WebSocket    | Real-time data                |
| Notification | System notifications          |
| Timers       | setTimeout, setInterval       |
| URL API      | Parse/manipulate URLs         |


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

## Hoisting

```
Hoisting ဆိုတာ JavaScript မှာ variable တွေနဲ့ function တွေကို code မ run ခင် 
(Execution context တည်ဆောက်တဲ့အချိန်) memory ထဲမှာ နေရာကြိုယူထားတဲ့ သဘောတရားဖြစ်ပါတယ်။

ရိုးရိုးရှင်းရှင်းပြောရရင် သင်က variable တစ်ခုကို မကြေညာခင် (Declare မလုပ်ခင်) အပေါ်ကနေ လှမ်းသုံးလိုက်ရင်တောင် 
JavaScript က error မတက်စေဘဲ variable declaration ကို code ရဲ့ ထိပ်ဆုံးကို ဆွဲတင်လိုက်သလိုမျိုး 
ပြုမူတာကို ခေါ်တာပါ။

၁။ Function Hoisting
Function တွေက Hoisting မှာ အထူးအခွင့်အရေးရပါတယ်။ Function တစ်ခုလုံးကို memory ထဲ ကြိုတင်သိမ်းထားတဲ့အတွက် 
သူ့ကို မရေးခင် (အပေါ်ကနေ) လှမ်းခေါ်လို့ ရပါတယ်။


sayHello(); // အလုပ်လုပ်တယ်: "မင်္ဂလာပါ"

function sayHello() {
  console.log("မင်္ဂလာပါ");
}


၂။ Variable Hoisting (var, let, const)

Variable တွေမှာတော့ သူတို့ကို ကြေညာတဲ့ keyword ပေါ်မူတည်ပြီး အလုပ်လုပ်ပုံ ကွာခြားပါတယ်။

var: Hoisting ဖြစ်ပါတယ်။ ဒါပေမဲ့ variable ရဲ့ တန်ဖိုး (value) ကိုတော့ မသိသေးဘဲ undefined 
အဖြစ်ပဲ မှတ်ထားပါတယ်။

let နှင့် const: သူတို့လည်း Hoisting ဖြစ်ပါတယ်။ ဒါပေမဲ့ သူတို့ကို memory ထဲမှာ နေရာယူထားရုံပဲ
 ရှိပြီး code က သူတို့ဆီ မရောက်မချင်း အသုံးပြုခွင့် မပေးပါဘူး။ ဒါကို Temporal Dead Zone (TDZ) လို့ ခေါ်ပါတယ်။

** Temporal Dead Zone (TDZ) ဆိုတာ let နဲ့ const variable တွေမှာ ဖြစ်လေ့ရှိတဲ့ အပြုအမူတစ်ခုပါ။
variable ကို စတင်ကြေညာ (declare) တဲ့ code အကြောင်းဆီ မရောက်ခင် အပေါ်ကနေ လှမ်းသုံးမိရင်
ReferenceError တက်စေတဲ့ နယ်မြေ (Area) ကို ခေါ်တာ ဖြစ်ပါတယ်။**

```
| Keyword        | 	Hoisted ဖြစ်လား	    |   တန်ဖိုး (Initial Value)       |     	Error တက်လား              |
|----------------|---------------------|-------------------------------|----------------------------------|
| var	           |     ဖြစ်တယ်         |    undefined	                  |        မတက်ဘူး(undefined ပြမယ်) |
|                |                     |                               |                                  |
| let / const	   |     ဖြစ်တယ်	       |        မရှိဘူး (Uninitialized)   |    	ReferenceError တက်မယ်       |


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---
## Scope

```
Scope ဆိုတာ JavaScript မှာ variable တွေ၊ functions တွေနဲ့ objects တွေကို 
"ဘယ်နေရာကနေ လှမ်းသုံးလို့ရသလဲ" ဆိုတဲ့ အတိုင်းအတာ သို့မဟုတ် နယ်နိမိတ်ကို ခေါ်တာ ဖြစ်ပါတယ်။

ရိုးရိုးရှင်းရှင်းပြောရရင် Variable တစ်ခုရဲ့ "သက်တမ်း" နဲ့ "မြင်နိုင်စွမ်း" (Visibility) ကို Scope က ဆုံးဖြတ်ပေးတာပါ။

၁။ Scope အမျိုးအစား (၃) မျိုး

JavaScript မှာ အဓိကအားဖြင့် အောက်ပါ Scope ၃ ခု ရှိပါတယ်-

(က) Global Scope

မည်သည့် function သို့မဟုတ် block ရဲ့ အပြင်ဘက်မှာမဆို ကြေညာထားတဲ့ variable တွေပါ။

ထူးခြားချက်: Code တစ်ခုလုံးရဲ့ ဘယ်နေရာကနေမဆို လှမ်းသုံးလို့ရပါတယ်။

ဥပမာ: const website = "Google"; (ဒါကို function ထဲကနေလည်း လှမ်းခေါ်လို့ ရပါတယ်)


(ခ) Function Scope (Local Scope)

Function တစ်ခုရဲ့ { } အတွင်းမှာ ကြေညာထားတဲ့ variable တွေပါ။

ထူးခြားချက်: အဲဒီ function အတွင်းမှာပဲ သုံးလို့ရပါတယ်။ Function အပြင်ဘက်ကနေ လှမ်းခေါ်ရင် Error တက်ပါလိမ့်မယ်။

var keyword နဲ့ ကြေညာရင် Function Scope ဖြစ်ပါတယ်။

(ဂ) Block Scope

if statement, for loop သို့မဟုတ် ရိုးရိုး curly braces { } အတွင်းမှာ ရှိတဲ့ နေရာပါ။

ထူးခြားချက်: let နဲ့ const ကို သုံးမှသာ Block Scope အလုပ်လုပ်ပါတယ်။ (အဲဒီ { } အပြင်ဘက်မှာ သုံးလို့မရပါ)

သတိထားရန်: var နဲ့ ကြေညာရင် block scope မရှိပါဘူး (Global သို့မဟုတ် Function scope ဆီကို ပေါက်ထွက်သွားပါလိမ့်မယ်)။

၂။ နှိုင်းယှဉ်ချက် ဥပမာ


// --- Global Scope ---
const user = "Aung Aung"; 

function sayHi() {
    // --- Function Scope ---
    const message = "Hello"; 
    
    if (true) {
        // --- Block Scope ---
        const greeting = "Hi there";
        var legacy = "I am everywhere"; // var သည် block scope ကို ဖောက်ထွက်နိုင်သည်
        console.log(greeting); // အလုပ်လုပ်သည်
    }

    console.log(message);  // အလုပ်လုပ်သည်
    // console.log(greeting); // Error! (Block Scope အပြင်ဘက်ဖြစ်နေ၍)
    console.log(legacy);   // အလုပ်လုပ်သည် (var ဖြစ်သောကြောင့်)
}

sayHi();
// console.log(message); // Error! (Function Scope အပြင်ဘက်ဖြစ်နေ၍)

၃။ ဘာကြောင့် Scope က အရေးကြီးတာလဲ?

Security (လုံခြုံမှု): Variable တွေကို လိုအပ်တဲ့ နေရာမှာပဲ ထားခြင်းဖြင့် အခြား code တွေက မတော်တဆ 
လာပြင်တာမျိုးကို တားဆီးနိုင်ပါတယ်။

Naming Collisions (နာမည်တူခြင်း): Scope မတူရင် variable နာမည်တူပေးလို့ ရပါတယ်။
 (ဥပမာ- function A ထဲမှာလည်း x သုံး၊ function B ထဲမှာလည်း x သုံးလို့ ရတာမျိုး)

Memory Management: Function တစ်ခု အလုပ်ပြီးသွားရင် သူ့ထဲက Local variables တွေကို
 memory ထဲကနေ ဖျက်ထုတ်ပေးတဲ့အတွက် memory သက်သာစေပါတယ်။

အနှစ်ချုပ်

Global Scope: လူတိုင်း မြင်နိုင်တဲ့ "လမ်းမပေါ်က ဆိုင်းဘုတ်" လိုမျိုးပါ။

Function Scope: အိမ်တစ်အိမ်ရဲ့ "ဧည့်ခန်း" လိုမျိုးပါ။ အိမ်ထဲဝင်မှ မြင်ရပါတယ်။

Block Scope: အိမ်ထဲကမှ "သေတ္တာအသေးလေး" ထဲ ထည့်ထားသလိုမျိုးပါ။ အဲဒီသေတ္တာကို ဖွင့်မှပဲ မြင်ရတာပါ။

```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

## Scope Chain

```
Scope Chain ဆိုတာ JavaScript မှာ variable တစ်ခုကို ရှာဖွေတဲ့ "လှေကားထစ်" လိုမျိုး စနစ်တစ်ခု ဖြစ်ပါတယ်။
လက်ရှိရှိနေတဲ့ နေရာမှာ variable ကို ရှာလို့မတွေ့ရင် သူ့ရဲ့ အပြင်ဘက် (Parent Scope) ဆီကို အဆင့်ဆင့် 
တက်ရှာသွားတဲ့ ဖြစ်စဉ်ကို ခေါ်တာပါ။

ဒီ concept ကို နားလည်ဖို့ Scopes အမျိုးအစားတွေကို အရင်သိထားဖို့ လိုပါတယ်။

၁။ Scopes အမျိုးအစား ၃ ခု
Global Scope: Code တစ်ခုလုံးရဲ့ အပြင်ဘက်ဆုံးနေရာ။ ဘယ်နေရာကမဆို လှမ်းသုံးလို့ရတယ်။

Function Scope: Function တစ်ခုအတွင်းမှာပဲ ရှိတဲ့နေရာ။

Block Scope: if သို့မဟုတ် for loop ရဲ့ { } brackets အတွင်းမှာပဲ ရှိတဲ့နေရာ (let နဲ့ const အတွက်သာ)။

၂။ Scope Chain ဘယ်လို အလုပ်လုပ်သလဲ?

JavaScript Engine က variable တစ်ခုကို တွေ့တဲ့အခါ အောက်ပါအစီအစဉ်အတိုင်း ရှာဖွေပါတယ်-

Local Scope: အရင်ဆုံး လက်ရှိ အလုပ်လုပ်နေတဲ့ နေရာ (Current Scope) မှာ ရှာပါတယ်။

Outer Scope: မတွေ့ရင် သူ့ကို ဝန်းရံထားတဲ့ အပြင်ဘက် Scope (Parent) ဆီကို သွားရှာပါတယ်။

Global Scope: အပြင်ဘက်အဆင့်ဆင့်မှာ ရှာရင်းနဲ့ နောက်ဆုံး Global Scope အထိ ရောက်သွားပါတယ်။ 
အဲဒီမှာမှ မတွေ့တော့ဘူးဆိုရင်တော့ ReferenceError ပြပါလိမ့်မယ်။

အရေးကြီးချက်: Scope Chain ဟာ အောက်ကနေ အပေါ်ကိုပဲ ရှာလို့ရပါတယ်။ အပေါ် (Global) ကနေ 
အောက် (Local function) ထဲက variable ကို လှမ်းရှာလို့ မရပါဘူး။

၃။ Code ဥပမာဖြင့် ကြည့်ခြင်း

const globalVar = "Global";

function outerFunction() {
    const outerVar = "Outer";

    function innerFunction() {
        const innerVar = "Inner";

        console.log(innerVar);  // ၁။ Local မှာတွေ့တယ် -> "Inner"
        console.log(outerVar);  // ၂။ Local မှာမတွေ့လို့ Parent (outerFunction) မှာသွားရှာတယ် -> "Outer"
        console.log(globalVar); // ၃။ Parent မှာမတွေ့လို့ Global မှာသွားရှာတယ် -> "Global"
        console.log(unknown);   // ၄။ ဘယ်မှာမှမတွေ့လို့ -> ReferenceError
    }

    innerFunction();
}

outerFunction();

၄။ Lexical Scoping
Scope Chain ဟာ Lexical Scoping ပေါ်မှာ အခြေခံပါတယ်။ ဆိုလိုတာက variable တစ်ခုရဲ့ scope ကို
code ရေးကတည်းက (ဘယ်နေရာမှာ ရေးထားသလဲဆိုတာကို ကြည့်ပြီး) ဆုံးဖြတ်လိုက်တာပါ။ Function ကို 
ဘယ်နေရာမှာ "ခေါ်သလဲ" ဆိုတာထက် ဘယ်နေရာမှာ "ရေးထားသလဲ" ဆိုတာက ပိုအရေးကြီးပါတယ်။

အကျဉ်းချုပ် (Analogy)

အိမ်တစ်အိမ်မှာ ပစ္စည်းတစ်ခု ရှာသလိုပါပဲ-

ကိုယ့်အခန်းထဲမှာ အရင်ရှာမယ် (Local Scope)။

မတွေ့ရင် ဧည့်ခန်းထဲထွက်ရှာမယ် (Outer Scope)။

မတွေ့ရင် အိမ်ရှေ့ကွင်းပြင်ထဲမှာ ထွက်ရှာမယ် (Global Scope)။

အပြင်မှာမှ မတွေ့ရင်တော့ အဲဒီပစ္စည်း မရှိဘူးလို့ သတ်မှတ်လိုက်တာပါပဲ။
```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

## Lexical Scoping
```
JavaScript မှာ Lexical Scope (သို့မဟုတ် Static Scope) ဆိုသည်မှာ variable တစ်ခု၏ 
တည်ရှိမှုနယ်ပယ် (Scope) ကို ၎င်းအား code ရေးသားစဉ်က ထားရှိခဲ့သော နေရာ  ပေါ်မူတည်၍
သတ်မှတ်ခြင်းကိုဆိုလိုပါသည်။

ရိုးရိုးရှင်းရှင်းပြောရရင် "Function တစ်ခုဟာ သူ့ရဲ့ အပြင်ဘက် (Parent) မှာရှိတဲ့ Variable တွေကို လှမ်းမြင်နိုင်တယ်" 
ဆိုတာပါပဲ။ 

function outer() {
  const name = "Aung Aung";

  function inner() {
    // inner function ထဲမှာ 'name' မရှိပေမဲ့
    // သူ့ရဲ့ lexical parent ဖြစ်တဲ့ outer ဆီက variable ကို လှမ်းသုံးလို့ရတယ်
    console.log(name); 
  }

  inner();
}

outer(); // Output: Aung Aung
ဒီနေရာမှာ inner() function ကို outer() ရဲ့ အထဲမှာ ရေးထားတဲ့အတွက် inner ရဲ့ lexical environment
 ထဲမှာ outer ရဲ့ variable တွေ ပါဝင်နေတာ ဖြစ်ပါတယ်။

အဓိက အချက်များ

အထဲကနေ အပြင်ကိုပဲ မြင်ရတယ်: Function အငယ်လေးတွေက သူတို့ကို ဝန်းရံထားတဲ့ အပြင်ဘက်
(Parent) scope တွေကို လှမ်းမြင်နိုင်ပေမဲ့၊ အပြင်ဘက်က function ကတော့ အထဲက function ထဲက variable
တွေကို လှမ်းမမြင်နိုင်ပါဘူး။

Static ဖြစ်တယ်: Function ကို ဘယ်နေရာမှာ "ခေါ်သလဲ" (Call-site) ဆိုတာက အရေးမကြီးပါဘူး။
ဘယ်နေရာမှာ "ကြေညာခဲ့သလဲ" (Definition-site) ဆိုတာကပဲ အရေးကြီးပါတယ်။

Lexical Scoping vs Dynamic Scoping

JavaScript ဟာ Lexical Scoping ကို သုံးပါတယ်။ တချို့ ဘာသာစကားတွေမှာ သုံးတဲ့ Dynamic Scoping နဲ့ မတူပါဘူး။

JavaScript
const x = 10;

function a() {
  console.log(x);
}

function b() {
  const x = 20;
  a(); // x က ဘယ်လောက်ထွက်မလဲ?
}

b(); 
Lexical Scoping (JS): အဖြေက 10 ထွက်ပါမယ်။ ဘာလို့လဲဆိုတော့ a() ကို ကြေညာခဲ့တဲ့ 
နေရာရဲ့ အပြင်ဘက်မှာ x = 10 ပဲ ရှိလို့ပါ။

Dynamic Scoping: အဖြေက 20 ထွက်ပါလိမ့်မယ် (ဘာလို့လဲဆိုတော့ a() ကို ခေါ်လိုက်တဲ့ နေရာမှာ x က 20 ဖြစ်နေလို့ပါ)။ 
ဒါပေမဲ့ JS က ဒါမျိုး အလုပ်မလုပ်ပါဘူး။


Lexical Scoping ကို "မျိုးရိုးဗီဇ" လို မှတ်သားနိုင်ပါတယ်။ သင်ဟာ သင့်မိဘတွေဆီက အမွေ (Variables) တွေကို ရပိုင်ခွင့်ရှိပါတယ်။ 
သင် ဘယ်မြို့ကိုပဲ ရောက်သွားရောက်သွား (Function ကို ဘယ်မှာပဲ ခေါ်ခေါ်)၊ သင့်ရဲ့ မိဘက ဘယ်သူလဲဆိုတာ (Lexical Parent) မပြောင်းလဲတဲ့အတွက် အဲဒီအမွေတွေကို သင် ဆက်ပြီး သုံးစွဲခွင့် ရှိနေမှာ ဖြစ်ပါတယ်။

```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

## Closure
```
JavaScript မှာ Closure  ဆိုတာက Function တစ်ခုဟာ သူ့ရဲ့အပြင်ဘက် scope (outer function scope)
က variable တွေကို သူကိုယ်တိုင်ပြီးဆုံးသွားရင်တောင် မှတ်မိနေပြီး ပြန်သုံးနိုင်တဲ့ စွမ်းရည် ကို ခေါ်တာဖြစ်ပါတယ်. 

ရိုးရှင်းရှင်း ပြောရရင် "Function တစ်ခုက သူ့ကို ဖန်တီးခဲ့တဲ့ ပတ်ဝန်းကျင် (Outer Scope) မှာရှိတဲ့ Variable တွေကို အမြဲတမ်း မှတ်မိနေခြင်း" ကို ခေါ်တာပါ။

ပုံမှန်အားဖြင့် Function တစ်ခုက အလုပ်လုပ်ပြီးသွားရင် သူ့ထဲက variable တွေဟာ memory ထဲကနေ ပျောက်သွားရမှာပါ။
 ဒါပေမဲ့ Closure ကြောင့် အဲဒီ variable တွေကို ဆက်ပြီး သိမ်းထားနိုင်တာ ဖြစ်ပါတယ်။

၁။ Closure ဘယ်လို ဖြစ်ပေါ်လာသလဲ?

Function တစ်ခုအတွင်းမှာ နောက်ထပ် Function တစ်ခု (Inner Function) ကို ထပ်ရေးပြီး အဲဒီ Inner function ကို 
အပြင်ကို return ပြန်ထုတ်လိုက်တဲ့အခါ Closure ဖြစ်ပေါ်လာပါတယ်။

function outerFunction() {
  let outerVariable = "I am outside!";

  function innerFunction() {
    console.log(outerVariable); // innerFunction က outerVariable ကို သုံးနေတယ်
  }

  return innerFunction; // function ကိုပြန်ထုတ်လိုက်တယ်
}

const myClosure = outerFunction();
myClosure(); // Output: "I am outside!"


ဘာဖြစ်သွားတာလဲ?
outerFunction() အလုပ်လုပ်ပြီးဆုံးသွားပေမယ့် myClosure() ကို ခေါ်လိုက်တဲ့အချိန်မှာ outerVariable ရဲ့ တန်ဖိုးကို ဆက်မှတ်မိနေဆဲဖြစ်ပါတယ်. 


အလုပ်လုပ်ပုံ အဆင့်ဆင့် (Execution Context အရ)

Creation: outerFunction ကို ခေါ်လိုက်တဲ့အခါ သူ့အတွက် Memory နေရာတစ်ခု ရလာပါတယ်။

Returning: သူက innerFunction ကို ပြန်ပေးလိုက်တဲ့အခါ အဲဒီ inner function နဲ့အတူ သူ့ရဲ့ 
Scope Chain  ပါ ပါသွားပါတယ်။

Persistence: Closure က count variable ကို Garbage Collector ကနေ မဖျက်ပစ်အောင်
တားဆီးထားလိုက်ပါတယ်။ ဒါကြောင့် counter() ကို ခေါ်တိုင်း count တန်ဖိုးက ဆက်ရှိနေတာပါ။

၄။ သတိထားရန်အချက်
Closures တွေက variable တွေကို memory ထဲမှာ ဆက်သိမ်းထားတဲ့အတွက် အသုံးမလိုဘဲ အများကြီး 
သုံးရင် Memory Leak (Memory နေရာလွတ် မကျန်တော့ခြင်း) ဖြစ်တတ်ပါတယ်။ အလုပ်ပြီးသွားရင် reference
 ကို null ပြန်လုပ်ပေးဖို့ လိုအပ်ရင် လိုအပ်ပါလိမ့်မယ်။

အနှစ်ချုပ် (Analogy)
Closure ဆိုတာ "ကျောပိုးအိတ်" နဲ့ တူပါတယ်။ Function က တစ်နေရာကို ခရီးထွက်သွားတဲ့အခါ 
(Return ပြန်တဲ့အခါ) သူ့အိမ်မှာရှိတဲ့ ပစ္စည်းတွေကို ကျောပိုးအိတ်ထဲ ထည့်ယူသွားသလိုပါပဲ။ အဲဒီ ပစ္စည်းတွေ 
(Variables) ကို သူရောက်တဲ့နေရာတိုင်းမှာ ပြန်ထုတ်သုံးလို့ ရနေတာမျိုး ဖြစ်ပါတယ်။


```


<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>

---

## Arrays

JavaScript မှာ Arrays ဆိုတာ data တွေကို စုစည်းပြီး သိမ်းဆည်းထားနိုင်တဲ့ data structure တစ်ခုဖြစ်ပါတယ်။ Data တွေကို list အနေနဲ့ ထားချင်တဲ့အခါမှာ အသုံးပြုပါတယ်။ Array တွေဟာ zero-indexed ဖြစ်တဲ့အတွက် ပထမဆုံး data ဟာ index `0` ကနေ စပါတယ်။

### Array Methods (အသုံးများသော Method များ)

JavaScript Arrays တွေမှာ data တွေကို ပြင်ဆင်ဖို့၊ ရှာဖွေဖို့၊ စစ်ဆေးဖို့အတွက် အသင့်သုံးနိုင်တဲ့ (built-in) methods အများကြီး ပါဝင်ပါတယ်။ အောက်မှာ အသုံးများတဲ့ Array Methods တွေကို အုပ်စုခွဲပြီး အသေးစိတ် ဖော်ပြပေးထားပါတယ်။

### 1. Element များ ထည့်ခြင်း / ဖယ်ရှားခြင်း (Adding & Removing)

- **`push()`**: Array ရဲ့ နောက်ဆုံးမှာ အချက်အလက် (element) အသစ်တစ်ခု ဒါမှမဟုတ် အများကြီးကို ထည့်ပါတယ်။
  ```js
  let fruits = ['apple', 'banana'];
  fruits.push('orange'); // ['apple', 'banana', 'orange']
  ```

- **`pop()`**: Array ရဲ့ နောက်ဆုံးက element ကို ဖယ်ရှားပြီး အဲ့ဒီ element ကို ပြန်ထုတ်ပေးပါတယ်။
  ```js
  let last = fruits.pop(); // last: 'orange', fruits: ['apple', 'banana']
  ```

- **`unshift()`**: Array ရဲ့ အစ (အရှေ့ဆုံး) မှာ element အသစ်ထည့်ပါတယ်။
  ```js
  fruits.unshift('mango'); // ['mango', 'apple', 'banana']
  ```

- **`shift()`**: Array ရဲ့ အစ (အရှေ့ဆုံး) က element ကို ဖယ်ရှားပါတယ်။
  ```js
  let first = fruits.shift(); // first: 'mango', fruits: ['apple', 'banana']
  ```

### 2. Array ကို ဖြတ်တောက်ခြင်း / ဆက်ခြင်း (Extracting & Combining)

- **`slice(startIndex, endIndex)`**: Array ရဲ့ သတ်မှတ်ထားတဲ့ အပိုင်းကို ဖြတ်ယူပြီး Array အသစ်အနေနဲ့ ပြန်ထုတ်ပေးပါတယ်။ (မူလ Array ကို မပြောင်းလဲစေပါ)
  ```js
  let arr = [1, 2, 3, 4, 5];
  let sliced = arr.slice(1, 4); // [2, 3, 4]
  ```

- **`splice(startIndex, deleteCount, items...)`**: Array ထဲက element တွေကို ဖျက်တာ၊ အစားထိုးတာ၊ အသစ်ထည့်တာတွေ လုပ်လို့ရပါတယ်။ (မူလ Array ပြောင်းလဲသွားပါတယ်)
  ```js
  let months = ['Jan', 'March', 'April'];
  months.splice(1, 0, 'Feb'); // index 1 နားမှာ ဘာမှမဖျက်ဘဲ 'Feb' ထည့်မည် -> ['Jan', 'Feb', 'March', 'April']
  months.splice(2, 1, 'May'); // index 2 နေရာက ၁ ခုကို ဖျက်ပြီး 'May' ကို အစားထိုးမည် -> ['Jan', 'Feb', 'May', 'April']
  ```

- **`concat()`**: Array နှစ်ခု ဒါမှမဟုတ် အဲ့ဒီထက်ပိုတဲ့ Array တွေကို ပေါင်းပြီး Array အသစ်တစ်ခု ပြုလုပ်ပေးပါတယ်။
  ```js
  let arr1 = [1, 2];
  let arr2 = [3, 4];
  let combined = arr1.concat(arr2); // [1, 2, 3, 4]
  ```

### 3. ရှာဖွေခြင်း (Searching)

- **`indexOf(element)`**: Array ထဲမှာ မိမိရှာချင်တဲ့ element ရှိနေတဲ့ index (နေရာ) ကို ပြန်ပေးပါတယ်။ မရှိရင် `-1` ပြန်ပေးပါတယ်။
  ```js
  let names = ['Mg Mg', 'Aung Aung', 'Su Su'];
  names.indexOf('Aung Aung'); // 1
  ```

- **`includes(element)`**: Array ထဲမှာ မိမိရှာချင်တဲ့ element ပါ/မပါ ကို `true` / `false` ပြန်ပေးပါတယ်။
  ```js
  names.includes('Su Su'); // true
  ```

- **`find(callback)`**: ကိုယ်သတ်မှတ်ထားတဲ့ ပေးချက် (condition) နဲ့ ကိုက်ညီတဲ့ ပထမဆုံး element ကို ရှာပေးပါတယ်။
  ```js
  let numbers = [10, 20, 30, 40];
  let found = numbers.find(num => num > 25); // 30
  ```

- **`findIndex(callback)`**: `find` နဲ့ ဆင်တူပေမယ့် သူက element အစား သူရှိနေတဲ့ index ကို ပြန်ပေးပါတယ်။
  ```js
  let foundIndex = numbers.findIndex(num => num > 25); // 2
  ```

### 4. ပတ်ပြီး အလုပ်လုပ်ခြင်း / ပြောင်းလဲခြင်း (Iterating & Transforming)

- **`forEach(callback)`**: Array ထဲက element တစ်ခုစီတိုင်းအတွက် ကိုယ်ရေးထားတဲ့ function တိုင်းကို လိုက်ပြီး အလုပ်လုပ်ပေးပါတယ်။ 
  ```js
  let items = ['a', 'b', 'c'];
  items.forEach(item => console.log(item));
  ```

- **`map(callback)`**: Element တစ်ခုချင်းစီတိုင်းကို တွက်ချက်မှုတစ်ခုခုလုပ်ပြီး **Array အသစ်တစ်ခု** အနေနဲ့ အဖြေပြန်ထုတ်ပေးပါတယ်။
  ```js
  let nums = [1, 2, 3];
  let doubled = nums.map(n => n * 2); // [2, 4, 6]
  ```

- **`filter(callback)`**: ကိုယ်လိုချင်တဲ့ Data တွေကိုပဲ စစ်ထုတ်ပြီး **Array အသစ်တစ်ခု** အဖြစ် ပြန်ထုတ်ပေးပါတယ်။
  ```js
  let ages = [12, 18, 25, 8];
  let adults = ages.filter(age => age >= 18); // [18, 25]
  ```

- **`reduce(callback, initialValue)`**: Array ထဲက တန်ဖိုးတွေကို အခြေခံပြီး တန်ဖိုး တစ်ခုတည်း (single value) ထွက်လာအောင် တွက်ချက်ပါတယ်။
  ```js
  let prices = [10, 20, 30];
  let total = prices.reduce((sum, price) => sum + price, 0); // 60
  ```

### 5. စစ်ဆေးခြင်း (Checking)

- **`some(callback)`**: Array ထဲမှာ condition နဲ့ ကိုက်ညီတဲ့ element **အနည်းဆုံး တစ်ခု** ပါနေရင် `true` ပြန်ပေးပါတယ်။
  ```js
  let scores = [45, 80, 30, 95];
  let hasPassed = scores.some(score => score >= 50); // true
  ```

- **`every(callback)`**: Array ထဲက element **အားလုံး** condition နဲ့ ကိုက်ညီမှ `true` ပြန်ပေးပါတယ်။
  ```js
  let allPassed = scores.every(score => score >= 50); // false
  ```

### 6. အစီအစဉ် ပြောင်းလဲခြင်း (Sorting & Ordering)

- **`sort()`**: String စာသားတွေကို အက္ခရာစဉ် (Alphabetical order) အတိုင်း စီပေးပါတယ်။ နံပါတ်တွေကို စီချင်ရင် callback သုံးပေးဖို့ လိုအပ်ပါတယ်။
  ```js
  let letters = ['c', 'a', 'b'];
  letters.sort(); // ['a', 'b', 'c']

  let numsForSort = [40, 100, 1, 5, 25];
  numsForSort.sort((a, b) => a - b); // [1, 5, 25, 40, 100]
  ```

- **`reverse()`**: Array တစ်ခုလုံးရဲ့ အစီအစဉ်ကို နောက်ပြန် (Reverse) လှည့်ပစ်ပါတယ်။ 
  ```js
  let step = [1, 2, 3];
  step.reverse(); // [3, 2, 1]
  ```

### 7. String အဖြစ် ပြောင်းလဲခြင်း (Converting to String)

- **`join(separator)`**: Array ထဲက element တွေကို တစ်ဆက်တည်း String စာသားအဖြစ် ပေါင်းစပ်ပေးပါတယ်။
  ```js
  let words = ['Hello', 'World'];
  let sentence = words.join(' '); // "Hello World"
  ```

<div align="right"><a href="#table-of-contents">↑ Back to Top</a></div>
