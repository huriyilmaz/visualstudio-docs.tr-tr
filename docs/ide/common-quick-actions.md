---
title: Yaygın Hızlı Eylemler
description: En popüler anahtar sözcükleri veya sembolleri düzeltme, birleştirme çakışmalarını çözümleme, gerekli içeri aktarmaları kaldırma, türleri oluşturma, yerel değişkenleri tanıtma gibi işlemleri içeren C# ve Visual Basic için Hızlı Eylemler'i kullanın.
ms.date: 03/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6fcf1ab1fdb5565cd4ba76c6eaa5c6b5a8fd74d6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124106"
---
# <a name="common-quick-actions"></a>Yaygın Hızlı Eylemler

Bu konudaki bölümler, hem C# **hem** de kod için geçerli olan bazı Visual Basic listele. Bu *eylemler, derleyici tanılamaları* veya .NET Compiler Platform çözümleyicileri [](../code-quality/roslyn-analyzers-overview.md) için kod düzeltmeleri Visual Studio.

## <a name="actions-that-fix-errors"></a>Hataları düzelten eylemler

Bu bölümdeki Hızlı Eylemler, derlemenin başarısız olmasına neden olacak kod hatalarını düzeltir. Bir kod satırındaki bir hatayı düzeltmek için Hızlı Eylemler kullanılabilir olduğunda, kenar boşluğunda veya kırmızı düğmenin altında görüntülenen simge üzerinde kırmızı 'x' bulunan bir ampul olur.

![Hızlı Eylemler hata simgesi ve menüsü](media/error-light-bulb-with-code.png)

### <a name="correct-misspelled-symbol-or-keyword"></a>Yanlış yazılmış simge veya anahtar sözcüğü düzeltme

Bu hızlı eylemde yanlışlıkla bir tür veya anahtar Visual Studio yanlış satış yaptıysanız, bu Hızlı Eylem sizin için otomatik olarak düzeltilir. Ampul menüsünde bu öğeleri "'' olarak ' **'" \<misspelled word> olarak \<correct word> değiştirin.** Örnek:

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

| Hata Kimliği | Geçerli Diller |
| - | - |
| CS0103, BC30002 | C# ve Visual Basic |

### <a name="resolve-git-merge-conflict"></a>Git birleştirme çakışmalarını çözme

Bu Hızlı Eylemler, çakışan kodu ve işaretçileri kaldıran "değişiklik alarak" git birleştirme çakışmalarını çözmenize olanak sağlar.

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

| Hata Kimliği | Geçerli Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| CS8300, BC37284 | C# ve Visual Basic | Visual Studio 2017 sürüm 15.3 ve sonrası |

## <a name="actions-that-remove-unnecessary-code"></a>Gereksiz kodu kaldıran eylemler

### <a name="remove-unnecessary-usingsimports"></a>Gereksiz usings/Imports'ı kaldırma

Gereksiz **Kullanımı/İçeri Aktarmaları Kaldırma** Hızlı Eylemi, geçerli dosya için kullanılmayan `using` ve `Import` yönergelerini kaldırır. Bu öğeyi seçerek kullanılmayan ad alanı içeri aktarmaları kaldırılır.

| Geçerli Diller | Desteklenen Sürüm |
| - | - |
| C# ve Visual Basic | Visual Studio 2015 ve sonrası |

### <a name="remove-unnecessary-cast"></a>Gereksiz cast'ı kaldırma

Tür türe tür türe tür atarak gereksiz  türe neden olan gereksiz türe neden olan Hızlı Eylem'i kaldırmanız gerekir.

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

| Tanılama Kimliği | Geçerli Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0004 | C# ve Visual Basic | Visual Studio 2015 ve sonrası |

### <a name="remove-unused-variables"></a>Kullanılmayan değişkenleri kaldırma

Bu Hızlı Eylem, bildirilen ancak kodunda hiç kullanılmadan değişkenleri kaldırmanıza olanak sağlar.

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

| Tanılama Kimliği | Geçerli Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| CS0219, BC42024 | C# ve Visual Basic | Visual Studio 2017 sürüm 15.3 ve sonrası |

### <a name="remove-type-from-default-value-expression"></a>Varsayılan değer ifadesinde türü kaldırma

Bu Hızlı Eylem, değer türünü varsayılan değer [](/dotnet/csharp/language-reference/operators/default#default-literal) ifadelerinden kaldırır ve derleyici ifadenin türünü çıkaraya kadar varsayılan değişmez değeri kullanır.

```csharp
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }
```

| Tanılama Kimliği | Geçerli Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0034 | C# 7.1+ | Visual Studio 2017 sürüm 15.3 ve sonrası |

## <a name="actions-that-add-missing-code"></a>Eksik kod ekseren eylemler

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Başvuru derlemelerinde, uygulama paketlerinde veya çözüm NuGet türler için usings/imports ekleme

Çözümünüzde bulunan diğer projelerde bulunan türlerin kullanımı Hızlı Eylem'i otomatik olarak görüntüler, ancak diğerlerinin Gelişmiş sekmesinde Araçlar **> Seçenekler > C#** veya Temel > **etkinleştirilmesi** gerekir:

- Başvuru derlemelerinde türler için usings/imports önerme
- Paketlerde türler için usings/imports NuGet önerin

Etkinleştirildiğinde, şu anda içeri aktarılmış olan ancak başvuru derlemesinde veya pakette mevcut olan bir ad NuGet kullanırsanız, using veya import yönergesi oluşturulur.

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

| Tanılama Kimliği | Geçerli Diller |
| - | - |
| CS0103, BC30451 | C# ve Visual Basic|

### <a name="add-missing-casesdefault-caseboth"></a>Eksik servis/varsayılan servis/her ikisi ekleme

C# içinde veya deyiminde bir Visual Basic oluştururken, eksik servis Visual Basic, varsayılan durum deyimi veya her ikisini de otomatik olarak eklemek için Kod `switch` `Select Case` Eylemi kullanabilirsiniz.

Aşağıdaki numaralama ve boş veya deyimini `switch` göz önünde `Select Case` bulundurarak:

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

Her İki **Hızlı Eylem** Ekle'yi kullanmak eksik servis servislerini doldurur ve varsayılan bir durum ekler:

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

| Tanılama Kimliği | Geçerli Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0010 | C# ve Visual Basic| Visual Studio 2017 sürüm 15.3 ve sonrası |

### <a name="add-null-checks-for-parameters"></a>Parametreler için null denetimler ekleme

Bu Hızlı Eylem, parametrenin null olup olmadığını söylemek için kodunuzda bir denetim eklemenize olanak sağlar.

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

| Geçerli Diller | Desteklenen Sürüm |
| -------------------- | ---------------- |
| C# ve Visual Basic| Visual Studio 2017 sürüm 15.3 ve sonrası |

### <a name="add-argument-name"></a>Bağımsız değişken adı ekleme

```csharp
// Before
var date = new DateTime(1997, 7, 8);

// Include argument name 'year' (include trailing arguments)

// After
var date = new DateTime(year: 1997, month: 7, day: 8);
```

| Geçerli Diller | Desteklenen Sürüm |
| -------------------- | ---------------- |
| C# ve Visual Basic| Visual Studio 2017 sürüm 15.3 ve sonrası |

### <a name="add-braces"></a>Küme ayraçları ekleme

Küme ayracı Ekle Hızlı Eylemi, küme ayraçlarını tek satırlı `if` deyimler çevresinde sarmalar.

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

| Tanılama Kimliği | Geçerli Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0011 | C# | Visual Studio 2017 ve sonrası |

### <a name="add-and-order-modifiers"></a>Değiştirici ekleme ve sıralama

Bu Hızlı Eylemler, var olan verileri sıralamanıza ve eksik erişilebilirlik değiştiricileri eklemenize olanak sağlayarak değiştiricileri düzenlemenize yardımcı olur.

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

| Tanılama Kimliği | Geçerli Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0036 | C# ve Visual Basic| Visual Studio 2017 sürüm 15.5 ve sonrası |
| IDE0040 | C# ve Visual Basic| Visual Studio 2017 sürüm 15.5 ve sonrası |

## <a name="code-transformations"></a>Kod dönüştürmeleri

### <a name="convert-if-construct-to-switch"></a>'if' yapıyı 'switch' olarak dönüştürme

Bu Hızlı Eylem, **if-then-else yapılarını switch** yapısına **dönüştürmeye olanak** sağlar.

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

| Geçerli Diller | Desteklenen Sürüm |
| -------------------- | ---------------- |
| C# ve Visual Basic| Visual Studio 2017 sürüm 15.3 ve sonrası |

### <a name="convert-to-interpolated-string"></a>İlişkili dizeye dönüştürme

[İlişkili dizeler,](/dotnet/csharp/language-reference/keywords/interpolated-strings) **[String.Format](/dotnet/api/system.string.format#overloads)** yöntemine benzer şekilde, ekli değişkenlerle dizeleri ifade etmek için kolay bir yöntemdir.  Bu Hızlı Eylem, dizelerin bir noktada veya **String.Format** kullanımında olduğu ve kullanımı ibiçimlendirilmiş bir dize olarak değiştirir.

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

| Geçerli Diller | Desteklenen Sürüm |
| -------------------- | ---------------- |
| C# 6.0+ ve Visual Basic 14+ | Visual Studio 2017 ve sonrası |

### <a name="use-object-initializers"></a>Nesne başlatıcıları kullanma

Bu Hızlı Eylem, oluşturucuya çağrı [yapmak ve ek](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) atama deyimleri satırlarına sahip olmak yerine nesne başlatıcılarını kullanmana olanak sağlar.

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

| Tanılama Kimliği | Geçerli Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0017 | C# ve Visual Basic | Visual Studio 2017 ve sonrası |

### <a name="use-collection-initializers"></a>Koleksiyon başlatıcılarını kullanma

Bu Hızlı Eylem, sınıf [yöntemine yapılan birden](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) çok çağrı yerine koleksiyon `Add` başlatıcılarını kullanmanızı sağlar.

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

| Tanılama Kimliği | Geçerli Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0028 | C# ve Visual Basic | Visual Studio 2017 ve sonrası |

### <a name="convert-auto-property-to-full-property"></a>Otomatik özelliği tam özelliye dönüştürme

Bu Hızlı Eylem, bir otomatik özelliği tam özelliye (veya tam) dönüştürmeye olanak sağlar.

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

| Geçerli Diller | Desteklenen Sürüm |
| -------------------- | ---------------- |
| C# ve Visual Basic | Visual Studio 2017 sürüm 15.5 ve sonrası |

### <a name="convert-block-body-to-expression-bodied-member"></a>Blok gövdeyi ifadeye dönüştürülmüş üyeye dönüştürme

Bu Hızlı Eylem, metotlar, oluşturucular, işleçler, özellikler, dizin oluşturucular ve erişimciler için blok gövdelerini ifadeye dönüştürülmüş üyelere dönüştürmeye olanak sağlar.

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

| Tanılama Kimliği | Geçerli Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0021-27 | C# 6.0+ | Visual Studio 2017 ve sonrası |

### <a name="convert-anonymous-function-to-local-function"></a>Anonim işlevi yerel işleve dönüştürme

Bu Hızlı Eylem anonim işlevleri yerel işlevlere dönüştürür.

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

### <a name="convert-referenceequals-to-is-null"></a>'ReferenceEquals' değerini 'null' olarak dönüştürme

| Tanılama Kimliği | Geçerli Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0041 | C# 7.0+ | Visual Studio 2017 sürüm 15.5 ve sonrası |

Bu Hızlı Eylem mümkün olduğunca [kodlama deseni yerine](/dotnet/csharp/pattern-matching) desen ```ReferenceEquals``` eşleştirmenin kullanımını önerir.

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

| Tanılama Kimliği | Geçerli Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0039 | C# 7.0+ | Visual Studio 2017 sürüm 15. ve sonraki |

### <a name="introduce-pattern-matching"></a>Desen eşleştirmeyi tanıtma

Bu Hızlı Eylem C# içinde [dökümler ve](/dotnet/csharp/pattern-matching) null denetimlerle desen eşleştirmenin kullanımını önerir.

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

| Tanılama Kimliği | Geçerli Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0020 | C# 7.0+ | Visual Studio 2017 ve sonrası |
| IDE0019 | C# 7.0+ | Visual Studio 2017 ve sonrası |

### <a name="change-base-for-numeric-literals"></a>Sayısal değişmez değerler için temel değiştirme

Bu Hızlı Eylem, bir sayısal değişmez değeri bir temel sayısal sistemden diğerine dönüştürmeye olanak sağlar. Örneğin, bir s numarayı onaltılık veya ikili biçime değiştirebilirsiniz.

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

| Geçerli Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| C# 7.0+ ve Visual Basic 14+ | Visual Studio 2017 sürüm 15.3 ve sonrası |

### <a name="insert-digit-separators-into-literals"></a>Değişmez değerlerin içine basamak ayırıcıları ekleme

Bu Hızlı Eylem, değişmez değerlere ayırıcı karakterler eklemenize olanak sağlar.

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

| Geçerli Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| C# 7.0+ ve Visual Basic 14+ | Visual Studio 2017 sürüm 15.3 ve sonrası |

### <a name="use-explicit-tuple-names"></a>Açık tuple adlarını kullanma

Bu Hızlı Eylem, belirtik tanımlama adı yerine Item1, Item2 vb. kullanılabilir alanları tanımlar.

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

| Tanılama Kimliği | Geçerli Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0033 | C# 7.0+ ve Visual Basic 15+ | Visual Studio 2017 ve sonrası |

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
