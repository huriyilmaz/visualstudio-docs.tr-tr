---
title: Yaygın Hızlı Eylemler
description: En popüler yazılmış anahtar sözcükleri veya sembolleri düzeltme Visual Basic birleştirme çakışmalarını çözümleme, gerekli içeri aktarmaları kaldırma, tür oluşturma, yerel değişkenler ekleme gibi işlemler dahil olmak üzere C# ve Visual Basic için hızlı eylemler.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627243"
---
# <a name="common-quick-actions"></a>Yaygın Hızlı Eylemler

Bu konudaki bölümlerde hem C# hem de kod için geçerli olan bazı yaygın Hızlı Eylemler Visual Basic listelanmıştır.  Bu eylemler, *derleyici tanılamaları* veya .NET Compiler Platform çözümleyicileri [için](../code-quality/roslyn-analyzers-overview.md) kod düzeltmeleri Visual Studio.

## <a name="actions-that-fix-errors"></a>Hataları düzelten eylemler

Bu bölümdeki Hızlı Eylemler, derlemenin başarısız olmasına neden olacak kod hatalarını düzeltir. Bir kod satırındaki bir hatayı düzeltmek için Hızlı Eylemler kullanılabilir olduğunda, kenar boşluğunda veya kırmızı kısa çizginin altında görüntülenen simge üzerinde kırmızı 'x' bulunan bir ampul olur.

![Hızlı Eylemler hata simgesi ve menüsü](media/error-light-bulb-with-code.png)

### <a name="correct-misspelled-symbol-or-keyword"></a>Yanlış yazılmış simge veya anahtar sözcüğü düzeltme

Bu hızlı eylemde yanlışlıkla bir tür veya anahtar sözcüğü yanlış Visual Studio bu Hızlı Eylem sizin için otomatik olarak düzeltilir. Ampul menüsünde bu öğeleri "'' olarak ' **'" \<misspelled word> olarak \<correct word> değiştirin.** Örnek:

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

### <a name="remove-unnecessary-usingsimports"></a>Gereksiz kullanmaları/İçeri Aktarmaları kaldırma

Gereksiz **Kullanımı/İçeri Aktarmaları Kaldırma** Hızlı Eylemi, geçerli dosya için kullanılmayan `using` ve `Import` yönergelerini kaldırır. Bu öğeyi seçerek kullanılmayan ad alanı içeri aktarmaları kaldırılır.

| Geçerli Diller | Desteklenen Sürüm |
| - | - |
| C# ve Visual Basic | Visual Studio 2015 ve sonrası |

### <a name="remove-unnecessary-cast"></a>Gereksiz cast'ı kaldırma

Tür türe tür türe tür atarak türe  tür atacaksanız, Gereksiz Tür Tür At hızlı eylem öğesini kaldırma gereksiz türe neden olur.

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

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Başvuru derlemelerinde, uygulama paketlerinde veya çözümünüzdeki diğer NuGet türlerde türler için usings/imports ekleme

Çözümünüzde bulunan diğer projelerde bulunan türlerin kullanımı Hızlı Eylem'i otomatik olarak görüntüler, ancak diğerlerinin Gelişmiş sekmesinde Araçlar **> Seçenekler > C#** veya Temel > **gerekir:**

- Başvuru derlemelerinde türler için usings/imports önerme
- Paketlerde türler için usings/imports NuGet önerin

Etkinleştirildiğinde, şu anda içeri aktarılmış olan ancak bir başvuru derlemesinde veya pakette mevcut olan bir ad NuGet kullanırsanız, using veya import yönergesi oluşturulur.

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

Visual Basic'de C# veya deyiminde deyim oluştururken, eksik olay öğelerini, varsayılan servis Visual Basic deyimini veya her ikisini de otomatik olarak eklemek için Kod `switch` `Select Case` Eylemi kullanabilirsiniz.

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

Her İki **Hızlı Eylem Ekle'yi** kullanmak eksik servis servislerini doldurur ve varsayılan bir servis durumu ekler:

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

[Enterpolasyonlu dizeler](/dotnet/csharp/language-reference/keywords/interpolated-strings) , **[dize. Format](/dotnet/api/system.string.format#overloads)** yöntemine benzer şekilde, gömülü değişkenlerle dizeleri hızlı bir şekilde ifade etmenin kolay bir yoludur.  Bu hızlı eylem, dizelerin bitiştirildiği veya **String. Format** kullanan veya kullanımı enterpolasyonlu bir dizeye değiştiren durumları tanır.

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
| IDE0039 | C# 7.0 + | Visual Studio 2017 sürümü 15. ve üzeri |

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
