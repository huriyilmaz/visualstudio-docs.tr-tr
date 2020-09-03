---
title: Yaygın Hızlı Eylemler
description: C# ve Visual Basic yanlış yazılmış anahtar sözcükleri veya sembolleri düzeltme, birleştirme çakışmalarını çözme, gerekli içeri aktarmaları kaldırma, türleri oluşturma, yerel değişkenlere giriş vb. gibi popüler hızlı eylemler.
ms.date: 03/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: db7a3a550f6bfc1250679eeefa0ba3ec6291eef0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75585528"
---
# <a name="common-quick-actions"></a>Yaygın Hızlı Eylemler

Bu konudaki bölümler, hem C# hem de Visual Basic kodu için geçerli olan genel **hızlı eylemlerin** bazılarını listeler. Bu eylemler, derleyici tanılamaları veya Visual Studio 'daki yerleşik [.net Compiler platform Çözümleyicileri](../code-quality/roslyn-analyzers-overview.md) için *kod düzeltmelerdir* .

## <a name="actions-that-fix-errors"></a>Hataları gidermeye yönelik eylemler

Bu bölümdeki hızlı eylemler, bir yapılandırmanın başarısız olmasına neden olan koddaki hataları düzeltir. Bir kod satırındaki bir hatayı onarmak için hızlı eylemler kullanılabilir olduğunda, kenar boşluğunda veya kırmızı dalgalı çizgi altında görüntülenen simge, üzerinde kırmızı ' x ' olan bir ampul olur.

![Hızlı eylemler hata simgesi ve menü](media/error-light-bulb-with-code.png)

### <a name="correct-misspelled-symbol-or-keyword"></a>Yanlış yazılmış sembol veya anahtar sözcüğü düzelt

Visual Studio 'da bir tür veya anahtar sözcüğü yanlışlıkla yanlış yazarsanız, bu hızlı eylem sizin için otomatik olarak düzeltir. Bu öğeleri ampul menüsünde "' ' öğesini ' ' olarak **Değiştir \<misspelled word> \<correct word> "** olarak görürsünüz. Örneğin:

```csharp
// Before
private viod MyMethod()
{
}

// Change 'viod' to 'void'

// After
private void MyMethod()
{
}
```

```vb
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

| Hata KIMLIĞI | Uygun diller |
| - | - |
| CS0103, BC30002 | C# ve Visual Basic |

### <a name="resolve-git-merge-conflict"></a>Git birleştirme çakışmasını çözümle

Bu hızlı eylemler, çakışan kod ve işaretçileri kaldıran git birleştirme çakışmalarını "değişiklik yaparak" çözmenizi sağlar.

```csharp
// Before
private void MyMethod()
{
    if (false)
    {

    }
}

// Take changes from 'HEAD'

// After
private void MyMethod()
{
    if (true)
    {

    }
}
```

| Hata KIMLIĞI | Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| CS8300, BC37284 | C# ve Visual Basic | Visual Studio 2017 sürüm 15,3 ve üzeri |

## <a name="actions-that-remove-unnecessary-code"></a>Gereksiz kodu kaldırma eylemleri

### <a name="remove-unnecessary-usingsimports"></a>Gereksiz kullanımlar/Içeri aktarmaları kaldır

**Gereksiz kullanımlar/Içeri aktarmalar kaldırma** hızlı eylemi, `using` `Import` geçerli dosya için kullanılmayan ve yönergeleri kaldırır. Bu öğeyi seçtiğinizde, kullanılmayan ad alanı içeri aktarmaları kaldırılır.

| Uygun diller | Desteklenen Sürüm |
| - | - |
| C# ve Visual Basic | Visual Studio 2015 ve üzeri |

### <a name="remove-unnecessary-cast"></a>Gereksiz tür dönüştürmeyi kaldır

Bir türü, atama gerektirmeyen başka bir türe çevirebilirsiniz, **Gereksiz atama kaldırma** hızlı eylem öğesi gereksiz tür dönüştürmeyi kaldırır.

```csharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```

```vb
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

| Tanılama KIMLIĞI | Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0004 | C# ve Visual Basic | Visual Studio 2015 ve üzeri |

### <a name="remove-unused-variables"></a>Kullanılmayan değişkenleri kaldır

Bu hızlı eylem, kodunuzda tanımlanmış ancak hiç kullanılmamış değişkenleri kaldırmanıza olanak sağlar.

```csharp
// Before
public MyMethod()
{
    var unused = 8;
    var used = 1;
    return DoStuff(used);
}

// Remove unused variables

// After
public MyMethod()
{
    var used = 1;
    return DoStuff(used);
}
```

| Tanılama KIMLIĞI | Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| CS0219, BC42024 | C# ve Visual Basic | Visual Studio 2017 sürüm 15,3 ve üzeri |

### <a name="remove-type-from-default-value-expression"></a>Türü varsayılan değer ifadesinden kaldır

Bu hızlı eylem değer türünü varsayılan değer ifadesinden kaldırır ve derleyici ifadenin türünü çıkardığında [varsayılan değişmez](/dotnet/csharp/language-reference/operators/default#default-literal) değeri kullanır.

```csharp
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }
```

| Tanılama KIMLIĞI | Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0034 | C# 7.1 + | Visual Studio 2017 sürüm 15,3 ve üzeri |

## <a name="actions-that-add-missing-code"></a>Eksik kodu ekleyen eylemler

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Çözümünüzde başvuru derlemelerindeki, NuGet paketlerindeki veya diğer türlerdeki türler için kullanımlar/içeri aktarmalar ekleyin

Çözümünüzde diğer projelerde bulunan türlerin kullanılması hızlı eylemi otomatik olarak görüntüler, ancak diğerlerinin C# veya **temel > gelişmiş** sekmesinden **> araçlar > seçenekleri** arasından etkinleştirilmesi gerekir:

- Başvuru derlemelerindeki türler için kullanımlar/içeri aktarmalar öner
- NuGet paketlerindeki türler için kullanımlar/içeri aktarmalar öner

Etkinleştirildiğinde, şu anda içeri aktarılmamış ancak başvuru derlemesinde veya NuGet paketinde bulunan bir ad alanında bir tür kullanırsanız, using veya Import yönergesi oluşturulur.

```csharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```vb
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

' After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

| Tanılama KIMLIĞI | Uygun diller |
| - | - |
| CS0103, BC30451 | C# ve Visual Basic|

### <a name="add-missing-casesdefault-caseboth"></a>Eksik durumları/varsayılan durumu/her ikisini de ekle

`switch`C# veya Visual Basic içinde bir ifade oluştururken, `Select Case` eksik durum öğelerini otomatik olarak eklemek Için bir kod eylemi, varsayılan bir Case ifadesini veya her ikisini de kullanabilirsiniz.

Aşağıdaki sabit listesini ve boş veya ifadesini göz önünde bulundurun `switch` `Select Case` :

```csharp
enum MyEnum
{
    Item1,
    Item2,
    Item3
}

...

MyEnum myEnum = MyEnum.Item1;

switch(myEnum)
{
}
```

```vb
Enum MyEnum
    Item1
    Item2
    Item3
End Enum

...

Dim myEnum as MyEnum = MyEnum.Item1

Select Case myEnum
End Select
```

Hem hızlı eylem **ekleme hem de** eksik durumlarda dolgu, varsayılan bir durum ekler:

```csharp
switch(myEnum)
{
    case MyEnum.Item1:
        break;
    case MyEnum.Item2:
        break;
    case MyEnum.Item3:
        break;
    default:
        break;
}
```

```vb
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

| Tanılama KIMLIĞI | Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0010 | C# ve Visual Basic| Visual Studio 2017 sürüm 15,3 ve üzeri |

### <a name="add-null-checks-for-parameters"></a>Parametreler için null denetimleri Ekle

Bu hızlı eylem, bir parametrenin null olup olmadığını söylemek için kodunuzda bir denetim eklemenize olanak sağlar.

```csharp
// Before
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty) // cursor inside myProperty
    {
        MyProperty = myProperty;
    }
}

// Add null check

// After
class MyClass
{
    public string MyProperty { get; set; }

    public MyClass(string myProperty)
    {
        MyProperty = myProperty ?? throw new ArgumentNullException(nameof(myProperty));
    }
}
```

| Uygun diller | Desteklenen Sürüm |
| -------------------- | ---------------- |
| C# ve Visual Basic| Visual Studio 2017 sürüm 15,3 ve üzeri |

### <a name="add-argument-name"></a>Bağımsız değişken adı Ekle

```csharp
// Before
var date = new DateTime(1997, 7, 8);

// Include argument name 'year' (include trailing arguments)

// After
var date = new DateTime(year: 1997, month: 7, day: 8);
```

| Uygun diller | Desteklenen Sürüm |
| -------------------- | ---------------- |
| C# ve Visual Basic| Visual Studio 2017 sürüm 15,3 ve üzeri |

### <a name="add-braces"></a>Küme ayracı Ekle

Ayraç ekleme hızlı eylemi, tek satırlık deyimler etrafında küme ayraçları kaydırır `if` .

```csharp
// Before
if (true)
    return "hello,world";

// Add braces

// After
if (true)
{
    return "hello,world";
}
```

| Tanılama KIMLIĞI | Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0011 | C# | Visual Studio 2017 ve üzeri |

### <a name="add-and-order-modifiers"></a>Ekleme ve sıralama değiştiricileri

Bu hızlı eylemler, var olan ve eksik erişilebilirlik değiştiricilerini eklemenizi sağlayarak değiştiricilerin düzenlenmesine yardımcı olur.

```csharp
// Before
enum Color
{
    Red, White, Blue
}

// Add accessibility modifiers

// After
internal enum Color
{
    Red, White, Blue
}
```

```csharp
// Before
static private int thisFieldIsPublic;

// Order modifiers

// After
private static int thisFieldIsPublic;
```

| Tanılama KIMLIĞI | Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0036 | C# ve Visual Basic| Visual Studio 2017 sürüm 15,5 ve üzeri |
| IDE0040 | C# ve Visual Basic| Visual Studio 2017 sürüm 15,5 ve üzeri |

## <a name="code-transformations"></a>Kod dönüşümleri

### <a name="convert-if-construct-to-switch"></a>' İf ' yapısını ' Switch ' olarak Dönüştür

Bu hızlı eylem **, bir if-then-else** yapısını bir **Switch** yapısına dönüştürmenize olanak sağlar.

```csharp
// Before
if (obj is string s)
{
  Console.WriteLine("obj is a string: " + s);
}

else if (obj is int i && i > 10)
{
  Console.WriteLine("obj is an int greater than 10");
}

// Convert to switch

// After
switch (obj)
{
  case string s:
    Console.WriteLine("Obj is a string: " + s);
    break;
  case int i when i > 10:
    Console.WriteLine("obj is an int greater than 10");
    break;
}
```

```vb
' Before
If TypeOf obj Is String s Then
    Console.WriteLine("obj is a string: " + s)
Else If TypeOf obj Is Integer i And i > 10 Then
    Console.WriteLine("obj is an int greater than 10")
End If

' Convert to switch

' After
Select Case obj
  Case String s
    Console.WriteLine("Obj is a string: " + s)
    Exit Sub
  Case Integer i when i > 10
    Console.WriteLine("obj is an int greater than 10")
    Exit Sub
End Select
```

| Uygun diller | Desteklenen Sürüm |
| -------------------- | ---------------- |
| C# ve Visual Basic| Visual Studio 2017 sürüm 15,3 ve üzeri |

### <a name="convert-to-interpolated-string"></a>Enterpolasyonlu dizeye Dönüştür

[Enterpolasyonlu dizeler](/dotnet/csharp/language-reference/keywords/interpolated-strings) , **[dize. Format](/dotnet/api/system.string.format#overloads)** yöntemine benzer şekilde, gömülü değişkenlerle dizeleri hızlı bir şekilde ifade etmenin kolay bir yoludur.  Bu hızlı eylem, dizelerin bitiştirildiği veya **String. Format**kullanan veya kullanımı enterpolasyonlu bir dizeye değiştiren durumları tanır.

```csharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```

```vb
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

| Uygun diller | Desteklenen Sürüm |
| -------------------- | ---------------- |
| C# 6.0 + ve Visual Basic 14 + | Visual Studio 2017 ve üzeri |

### <a name="use-object-initializers"></a>Nesne başlatıcıları kullanma

Bu hızlı eylem, oluşturucuyu çağırmak ve ek satır atama deyimlerinin olması yerine [nesne başlatıcıları](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) kullanmanıza olanak sağlar.

```csharp
// Before
var c = new Customer();
c.Age = 21;

// Object initialization can be simplified

// After
var c = new Customer() { Age = 21 };
```

```vb
' Before
Dim c = New Customer()
c.Age = 21

' Object initialization can be simplified

' After
Dim c = New Customer() With {.Age = 21}
```

| Tanılama KIMLIĞI | Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0017 | C# ve Visual Basic | Visual Studio 2017 ve üzeri |

### <a name="use-collection-initializers"></a>Koleksiyon Başlatıcıları kullanma

Bu hızlı eylem, sınıfınızın yöntemine birden çok çağrı yerine [koleksiyon başlatıcıları](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) kullanmanıza olanak sağlar `Add` .

```csharp
// Before
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);

// Collection initialization can be simplified

// After
var list = new List<int> { 1, 2, 3 };
```

```vb
' Before
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)

' Collection initialization can be simplified

' After
Dim list = New List(Of Integer) From {1, 2, 3}
```

| Tanılama KIMLIĞI | Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0028 | C# ve Visual Basic | Visual Studio 2017 ve üzeri |

### <a name="convert-auto-property-to-full-property"></a>Auto özelliğini Full özelliğine Dönüştür

Bu hızlı eylem, bir otomatik özelliği tam bir özelliğe dönüştürmenizi ve bunun tersini yapmanızı sağlar.

```csharp
// Before
private int MyProperty { get; set; }

// Convert to full property

// After
private int MyProperty
{
    get { return _myProperty; }
    set { _myProperty = value; }
}
```

```vb
' Before
Public Property Name As String

' Convert to full property

' After
Private _Name As String

Public Property Name As String
    Get
        Return _Name
    End Get
    Set
        _Name = Value
    End Set
End Property
```

| Uygun diller | Desteklenen Sürüm |
| -------------------- | ---------------- |
| C# ve Visual Basic | Visual Studio 2017 sürüm 15,5 ve üzeri |

### <a name="convert-block-body-to-expression-bodied-member"></a>Blok gövdesini ifade-Bodied üyeye Dönüştür

Bu hızlı eylem, Yöntemler, oluşturucular, işleçler, özellikler, Dizin oluşturucular ve erişimciler için blok gövdelerini Expression-Bodied üyelere dönüştürmenize olanak sağlar.

```csharp
//Before
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get { return _myProperty; }
        set
        {
            _myProperty = value;
        }
    }

    public MyClass4(int myProperty)
    {
        MyProperty = myProperty;
    }

    public void PrintProperty()
    {
        Console.WriteLine(MyProperty);
    }
}

// Use expression body for accessors/constructors/methods

// After
class MyClass4
{
    private int _myProperty;

    public int MyProperty
    {
        get => _myProperty;
        set => _myProperty = value;
    }

    public MyClass4(int myProperty) => MyProperty = myProperty;

    public void PrintProperty() => Console.WriteLine(MyProperty);
}
```

| Tanılama KIMLIĞI | Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0021-27 | C# 6.0 + | Visual Studio 2017 ve üzeri |

### <a name="convert-anonymous-function-to-local-function"></a>Anonim işlevi yerel işleve Dönüştür

Bu hızlı eylem anonim işlevleri yerel işlevlere dönüştürür.

```csharp
// Before
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};

// Use local function

// After
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}
```

### <a name="convert-referenceequals-to-is-null"></a>' ReferenceEquals ' öğesini ' null ' olarak Dönüştür

| Tanılama KIMLIĞI | Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0041 | C# 7.0 + | Visual Studio 2017 sürüm 15,5 ve üzeri |

Bu hızlı eylem, mümkün olduğunda kodlama düzeniyle değil, [model eşleme](/dotnet/csharp/pattern-matching) kullanımını önerir ```ReferenceEquals``` .

```csharp
// Before
var value = "someString";
if (object.ReferenceEquals(value, null))
{
    return;
}

// Use 'is null' check

// After
var value = "someString";
if (value is null)
{
    return;
}
```

| Tanılama KIMLIĞI | Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0039 | C# 7.0 + | Visual Studio 2017 sürüm 15. ve üzeri |

### <a name="introduce-pattern-matching"></a>Model eşleştirmeyi tanıtma

Bu hızlı eylem, C# ' deki yayınlar ve null denetimleri ile [eşleşen düzenin](/dotnet/csharp/pattern-matching) kullanımını önerir.

```csharp
// Before
if (o is int)
{
    var i = (int)o;
    ...
}

// Use pattern matching

// After
if (o is int i)
{
    ...
}
```

```csharp
// Before
var s = o as string;
if (s != null)
{
    ...
}

// Use pattern matching

// After
if (o is string s)
{
    ...
}
```

| Tanılama KIMLIĞI | Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0020 | C# 7.0 + | Visual Studio 2017 ve üzeri |
| IDE0019 | C# 7.0 + | Visual Studio 2017 ve üzeri |

### <a name="change-base-for-numeric-literals"></a>Sayısal değişmez değerler için tabanı Değiştir

Bu hızlı eylem, sayısal bir sabit değeri bir taban sayısal sistemden diğerine dönüştürmenize olanak sağlar. Örneğin, bir sayıyı onaltılı veya ikili biçime değiştirebilirsiniz.

```csharp
// Before
int countdown = 2097152;

// Convert to hex

// After
int countdown = 0x200000;
```

```vb
' Before
Dim countdown As Integer = 2097152

' Convert to hex

' After
Dim countdown As Integer = &H200000
```

| Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| C# 7.0 + ve Visual Basic 14 + | Visual Studio 2017 sürüm 15,3 ve üzeri |

### <a name="insert-digit-separators-into-literals"></a>Sabit değerlere basamak ayırıcıları ekleyin

Bu hızlı eylem, değer değerlerine Ayırıcı karakterler eklemenize olanak sağlar.

```csharp
// Before
int countdown = 1000000;

// Separate thousands

// After
int countdown = 1_000_000;
```

```vb
' Before
Dim countdown As Integer = 1000000

' Separate thousands

' After
Dim countdown As Integer = 1_000_000
```

| Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| C# 7.0 + ve Visual Basic 14 + | Visual Studio 2017 sürüm 15,3 ve üzeri |

### <a name="use-explicit-tuple-names"></a>Açık demet adlarını kullan

Bu hızlı eylem, Item1, Item2 vb. yerine açık demet adının kullanılabileceği yerleri tanımlar.

```csharp
// Before
(string name, int age) customer = GetCustomer();
var name = customer.Item1;

// Use explicit tuple name

// After
(string name, int age) customer = GetCustomer();
var name = customer.name;
```

```vb
' Before
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1

' Use explicit tuple name

' After
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name
```

| Tanılama KIMLIĞI | Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0033 | C# 7.0 + ve Visual Basic 15 + | Visual Studio 2017 ve üzeri |

### <a name="use-inferred-names"></a>Gösterilen adları kullan

Bu hızlı eylem, kod, anonim türlerde çıkartılan üye adlarını veya diziler içinde çıkartılan öğe adlarını kullanacak şekilde basitleşilerek çıkar.

```csharp
// Before
var anon = new { age = age, name = name };

// Use inferred member name

// After
var anon = new { age, name };
```

```csharp
// Before
var tuple = (age: age, name: name);

// Use inferred tuple element name

// After
var tuple = (age, name);
```

| Tanılama KIMLIĞI | Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0037 | C# | Visual Studio 2017 sürüm 15,5 ve üzeri |
| IDE0037 | C# 7.1 + | Visual Studio 2017 sürüm 15,5 ve üzeri |

### <a name="deconstruct-tuple-declaration"></a>Demet bildirimini kaldırma

Bu hızlı eylem, kayıt düzeni değişken bildirimlerinin çıkarılması işlemini mümkün hale getirmenizi.

```csharp
// Before
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");

//Deconstruct variable declaration

// After
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");
```

| Tanılama KIMLIĞI | Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0042 | C# 7.0 + | Visual Studio 2017 sürüm 15,5 ve üzeri |

### <a name="make-method-synchronous"></a>Yöntemi zaman uyumlu yap

`async` `Async` Bir yöntemde or anahtar sözcüğünü kullanırken, `await` veya `Await` anahtar sözcüğünün de kullanılması beklenmektedir. Ancak böyle bir durum yoksa, `async` veya `Async` anahtar sözcüğünü kaldırarak ve dönüş türünü değiştirerek yöntemi zaman uyumlu hale getiren hızlı bir eylem görünür. Hızlı Eylemler menüsünden **yöntemi zaman uyumlu yap** seçeneğini kullanın.

```csharp
// Before
async Task<int> MyAsyncMethod()
{
    return 3;
}

// Make method synchronous

// After
int MyAsyncMethod()
{
    return 3;
}
```

```vb
' Before
Async Function MyAsyncMethod() As Task(Of Integer)
    Return 3
End Function

' Make method synchronous

' After
Function MyAsyncMethod() As Integer
    Return 3
End Function
```

| Hata KIMLIĞI | Uygun diller |
| ------- | -------------------- |
| CS1998, BC42356 | C# ve Visual Basic |

### <a name="make-method-asynchronous"></a>Metodu zaman uyumsuz yap

`await` `Await` Bir yöntemin içinde veya anahtar sözcüğünü kullanırken, yöntemin `async` veya anahtar sözcüğüyle işaretlenmiş olması beklenir `Async` . Ancak böyle bir durum yoksa, yöntemi zaman uyumsuz hale getiren bir hızlı eylem görüntülenir. Hızlı Eylemler menüsünde **Yöntem/işlev zaman uyumsuz** seçeneğini kullanın.

```csharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method asynchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```vb
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method asynchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

| Hata KIMLIĞI | Uygun diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| CS4032, BC37057 | C# ve Visual Basic | Visual Studio 2017 ve üzeri |

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler](../ide/quick-actions.md)
