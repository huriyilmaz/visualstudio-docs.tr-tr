---
title: Yaygın Hızlı Eylemler
description: Yanlış yazılmış anahtar kelimeleri veya sembolleri düzeltme, birleştirme çakışmalarını çözme, gerekli içeri aktarımları kaldırma, türleri oluşturma, yerel değişkenleri tanıtma vb. dahil olmak üzere C# ve Visual Basic için en popüler Hızlı Eylemler
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585528"
---
# <a name="common-quick-actions"></a>Yaygın Hızlı Eylemler

Bu konudaki bölümler, hem C# hem de Visual Basic kodu için geçerli olan ortak **Hızlı Eylemlerden** bazılarını listeler. Bu eylemler, derleyici tanılama veya Visual Studio'daki yerleşik [.NET Derleyici Platformu çözümleyicileri](../code-quality/roslyn-analyzers-overview.md) için *kod düzeltmeleridir.*

## <a name="actions-that-fix-errors"></a>Hataları düzelten eylemler

Bu bölümdeki Hızlı Eylemler, yapının başarısız lığa neden olacak kodhatalarını düzeltir. Hızlı Eylemler bir kod satırındaki bir hatayı düzeltmek için kullanılabilir olduğunda, kenar boşluğunda veya kırmızı dalgalı çizginin altında görüntülenen simge, üzerinde kırmızı 'x' olan bir ampuldür.

![Hızlı Eylemler hata simgesi ve menüsü](media/error-light-bulb-with-code.png)

### <a name="correct-misspelled-symbol-or-keyword"></a>Yanlış yazılmış simgeyi veya anahtar kelimeyi düzeltme

Visual Studio'da yanlışlıkla bir türü veya anahtar kelimeyi yanlış yazarsanız, bu Hızlı Eylem bunu sizin için otomatik olarak düzeltir. Ampul menüsünde bu öğeleri "> yanlış **yazılmış\<sözcüğü değiştir' olarak\<' doğru sözcük>'** olarak görürsünüz. Örnek:

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

| Hata Kimliği | Uygulanabilir Diller |
| - | - |
| CS0103, BC30002 | C# ve Visual Basic |

### <a name="resolve-git-merge-conflict"></a>Git birleştirme çakışma giderme

Bu Hızlı Eylemler, çakışan kodu ve işaretçileri kaldıran "değişiklik alarak" git birleştirme çakışmalarını çözmenize olanak tanır.

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

| Hata Kimliği | Uygulanabilir Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| CS8300, BC37284 | C# ve Visual Basic | Visual Studio 2017 sürüm 15.3 ve sonrası |

## <a name="actions-that-remove-unnecessary-code"></a>Gereksiz kodu kaldıran eylemler

### <a name="remove-unnecessary-usingsimports"></a>Gereksiz kullanımı kaldırma/Alma

**Gereksiz Usings/Imports** Quick Action kaldır, geçerli `using` `Import` dosya için kullanılmayan tüm yönergeleri ve yönergeleri kaldırır. Bu öğeyi seçtiğinizde, kullanılmayan ad alanı içeri aktarımları kaldırılır.

| Uygulanabilir Diller | Desteklenen Sürüm |
| - | - |
| C# ve Visual Basic | Visual Studio 2015 ve sonrası |

### <a name="remove-unnecessary-cast"></a>Gereksiz dökümleri kaldırma

Bir türü döküm gerektirmeyen başka bir türe atarsanız, **Gereksiz Döküm** Hızlı Eylem öğesini kaldır öğesi gereksiz dökümü kaldırır.

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

| Tanılama Kimliği | Uygulanabilir Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0004 | C# ve Visual Basic | Visual Studio 2015 ve sonrası |

### <a name="remove-unused-variables"></a>Kullanılmayan değişkenleri kaldırma

Bu Hızlı Eylem, bildirilen ancak kodunuzda hiç kullanılmayan değişkenleri kaldırmanızı sağlar.

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

| Tanılama Kimliği | Uygulanabilir Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| CS0219, BC42024 | C# ve Visual Basic | Visual Studio 2017 sürüm 15.3 ve sonrası |

### <a name="remove-type-from-default-value-expression"></a>Varsayılan değer ifadesinden türü kaldırma

Bu Hızlı Eylem, varsayılan değer ifadesinden değer türünü kaldırır ve derleyici ifade türünü çıkarabildiği zaman [varsayılan literal'ı](/dotnet/csharp/language-reference/operators/default#default-literal) kullanır.

```csharp
// Before
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }

// Simplify default expression

// After
void DoWork(CancellationToken cancellationToken = default) { ... }
```

| Tanılama Kimliği | Uygulanabilir Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0034 | C# 7.1+ | Visual Studio 2017 sürüm 15.3 ve sonrası |

## <a name="actions-that-add-missing-code"></a>Eksik kod ekleyen eylemler

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Çözümdeki referans derlemeleri, NuGet paketleri veya diğer türler için kullanır/içe alma ekleme

Çözümünüzde diğer projelerde bulunan türleri kullanmak Hızlı Eylem'i otomatik olarak görüntüler, ancak diğerlerinin C# veya **Temel > Gelişmiş** **sekmesi> Araçlar > Seçenekleri'nden** etkinleştirilmesi gerekir:

- Referans derlemeler deki türler için kullanarak/içe alma önerme
- NuGet paketlerindeki türler için kullanma/alma önerme

Etkinleştirildiğinde, şu anda alınmamış ancak bir başvuru derlemesinde veya NuGet paketinde bulunan bir ad alanında bir tür kullanıyorsanız, kullanma veya alma yönergesi oluşturulur.

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

| Tanılama Kimliği | Uygulanabilir Diller |
| - | - |
| CS0103, BC30451 | C# ve Visual Basic|

### <a name="add-missing-casesdefault-caseboth"></a>Eksik kılıflar/varsayılan durum/her ikisi ekleme

C#'da veya `switch` Visual `Select Case` Basic'te bir deyim oluştururken, eksik servis talebi öğelerini, varsayılan servis talebi bildirimini veya her ikisini de otomatik olarak eklemek için bir Kod Eylemi kullanabilirsiniz.

Aşağıdaki numaralandırma ve boş `switch` veya `Select Case` ifade düşünün:

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

Her **Iki** Hızlı Eylem Ekle'yi kullanmak eksik servis taleplerini doldurur ve varsayılan bir servis talebi ekler:

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

| Tanılama Kimliği | Uygulanabilir Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0010 | C# ve Visual Basic| Visual Studio 2017 sürüm 15.3 ve sonrası |

### <a name="add-null-checks-for-parameters"></a>Parametreler için null denetimleri ekleme

Bu Hızlı Eylem, parametrenin null olup olmadığını söylemek için kodunuza bir çek eklemenize olanak tanır.

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

| Uygulanabilir Diller | Desteklenen Sürüm |
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

| Uygulanabilir Diller | Desteklenen Sürüm |
| -------------------- | ---------------- |
| C# ve Visual Basic| Visual Studio 2017 sürüm 15.3 ve sonrası |

### <a name="add-braces"></a>Ayraç ekleme

Hızlı Eylem Ekle ayraçları, ayraçları `if` tek satırlık deyimlerin etrafına sarar.

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

| Tanılama Kimliği | Uygulanabilir Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0011 | C# | Visual Studio 2017 ve sonrası |

### <a name="add-and-order-modifiers"></a>Değiştiriciler ekleme ve sipariş

Bu Hızlı Eylemler, varolan ları sıralamanızı ve eksik erişilebilirlik değiştiriciler eklemenizi sağlayarak değiştiricilerin düzenlenmesine yardımcı olur.

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

| Tanılama Kimliği | Uygulanabilir Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0036 | C# ve Visual Basic| Visual Studio 2017 sürüm 15.5 ve sonrası |
| IDE0040 | C# ve Visual Basic| Visual Studio 2017 sürüm 15.5 ve sonrası |

## <a name="code-transformations"></a>Kod dönüşümleri

### <a name="convert-if-construct-to-switch"></a>'if' yapısını 'anahtar' olarak dönüştürme

Bu Hızlı Eylem, else **else'deki bir yapıyı** **anahtar** yapısına dönüştürmenizi sağlar.

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

| Uygulanabilir Diller | Desteklenen Sürüm |
| -------------------- | ---------------- |
| C# ve Visual Basic| Visual Studio 2017 sürüm 15.3 ve sonrası |

### <a name="convert-to-interpolated-string"></a>Enterpolasyonlu dize dönüştürme

[Enterpolasyonlu dizeleri,](/dotnet/csharp/language-reference/keywords/interpolated-strings) **[String.Format](/dotnet/api/system.string.format#overloads)** yöntemine benzer şekilde katıştılı değişkenlerle dizeleri ifade etmenin kolay bir yoludur.  Bu Hızlı Eylem, dizelerin bağlandığı veya **String.Format'ı**kullandığı durumları tanır ve kullanımı enterpolasyonlu bir dize yle değiştirir.

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

| Uygulanabilir Diller | Desteklenen Sürüm |
| -------------------- | ---------------- |
| C# 6.0+ ve Visual Basic 14+ | Visual Studio 2017 ve sonrası |

### <a name="use-object-initializers"></a>Nesne baş harflerini kullanma

Bu Hızlı Eylem, oluşturucuyu çağırmak ve ek atama deyimsatırlarına sahip olmak yerine [nesne baş harflerini](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) kullanmanıza olanak tanır.

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

| Tanılama Kimliği | Uygulanabilir Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0017 | C# ve Visual Basic | Visual Studio 2017 ve sonrası |

### <a name="use-collection-initializers"></a>Koleksiyon baş harflerini kullanma

Bu Hızlı Eylem, [collection initializers](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) sınıfınızın `Add` yöntemine birden çok çağrı yerine koleksiyon başlatma layıcılarını kullanmanıza olanak tanır.

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

| Tanılama Kimliği | Uygulanabilir Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0028 | C# ve Visual Basic | Visual Studio 2017 ve sonrası |

### <a name="convert-auto-property-to-full-property"></a>Otomatik mülkü tam mülke dönüştürme

Bu Hızlı Eylem, bir otomatik mülkü tam bir özelliğe dönüştürmenize olanak tanır ve bunun tersi de vardır.

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

| Uygulanabilir Diller | Desteklenen Sürüm |
| -------------------- | ---------------- |
| C# ve Visual Basic | Visual Studio 2017 sürüm 15.5 ve sonrası |

### <a name="convert-block-body-to-expression-bodied-member"></a>Blok gövdesini ifade gövdeli üyeye dönüştürme

Bu Hızlı Eylem, blok gövdelerini yöntemler, oluşturucular, işleçler, özellikler, dizin leyiciler ve erişimciler için ifade gövdeli üyelere dönüştürmenize olanak tanır.

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

| Tanılama Kimliği | Uygulanabilir Diller | Desteklenen Sürüm |
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

### <a name="convert-referenceequals-to-is-null"></a>'ReferenceEquals'ı 'null' olarak dönüştürün

| Tanılama Kimliği | Uygulanabilir Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0041 | C# 7.0+ | Visual Studio 2017 sürüm 15.5 ve sonrası |

Bu Hızlı Eylem, mümkünse ```ReferenceEquals``` kodlama deseni yerine desen [eşleştirmesinin](/dotnet/csharp/pattern-matching) kullanılmasını önerir.

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

| Tanılama Kimliği | Uygulanabilir Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0039 | C# 7.0+ | Visual Studio 2017 sürüm 15. ve daha sonra |

### <a name="introduce-pattern-matching"></a>Desen eşleştirmetanıt

Bu Hızlı Eylem, C#'daki kalıplar ve null denetimlerle [eşleşen örüntü](/dotnet/csharp/pattern-matching) kullanımını önerir.

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

| Tanılama Kimliği | Uygulanabilir Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0020 | C# 7.0+ | Visual Studio 2017 ve sonrası |
| IDE0019 | C# 7.0+ | Visual Studio 2017 ve sonrası |

### <a name="change-base-for-numeric-literals"></a>Sayısal literaller için temeli değiştirme

Bu Hızlı Eylem, sayısal bir gerçek dosyayı bir temel sayısal sistemden diğerine dönüştürmenizi sağlar. Örneğin, bir sayıyı hexadecimal veya ikili biçime değiştirebilirsiniz.

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

| Uygulanabilir Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| C# 7.0+ ve Visual Basic 14+ | Visual Studio 2017 sürüm 15.3 ve sonrası |

### <a name="insert-digit-separators-into-literals"></a>Basamak ayırıcılarını literals'e ekleme

Bu Hızlı Eylem, ayırıcı karakterleri gerçek değerlere eklemenize olanak tanır.

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

| Uygulanabilir Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| C# 7.0+ ve Visual Basic 14+ | Visual Studio 2017 sürüm 15.3 ve sonrası |

### <a name="use-explicit-tuple-names"></a>Açık tuple adlarını kullanma

Bu Hızlı Eylem, Müstehcen tuple adının Item1, Item2, vb. yerine kullanılabildiği alanları tanımlar.

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

| Tanılama Kimliği | Uygulanabilir Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0033 | C# 7.0+ ve Visual Basic 15+ | Visual Studio 2017 ve sonrası |

### <a name="use-inferred-names"></a>Çıkarılan adları kullanma

Bu Hızlı Eylem, kodun anonim türlerde veya tuples'te çıkarılan öğe adlarında çıkarılan üye adlarını kullanmak için ne zaman basitleştirilenene işaret tir.

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

| Tanılama Kimliği | Uygulanabilir Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0037 | C# | Visual Studio 2017 sürüm 15.5 ve sonrası |
| IDE0037 | C# 7.1+ | Visual Studio 2017 sürüm 15.5 ve sonrası |

### <a name="deconstruct-tuple-declaration"></a>Tuple bildirimini deconstruct

Bu Hızlı Eylem, tuple değişken bildirimlerinin yapısızlaştırılmasını sağlar.

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

| Tanılama Kimliği | Uygulanabilir Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| IDE0042 | C# 7.0+ | Visual Studio 2017 sürüm 15.5 ve sonrası |

### <a name="make-method-synchronous"></a>Yöntem senkron yapma

Bir `async` yöntemde `Async` anahtar kelimeyi kullanırken, bu yöntemin `await` içinde `Await` anahtar kelimenin de kullanılması beklenir. Ancak, bu durumda değilse, hızlı eylem, yöntemi veya `async` `Async` anahtar sözcüğü kaldırarak ve dönüş türünü değiştirerek eşzamanlı hale getiren bir Hızlı Eylem görüntülenir. Hızlı İşlemler menüsünden **yöntem eşzamanlı lık** seçeneğini kullanın.

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

| Hata Kimliği | Uygulanabilir Diller |
| ------- | -------------------- |
| CS1998, BC42356 | C# ve Visual Basic |

### <a name="make-method-asynchronous"></a>Yöntem asynchronous olun

Bir `await` yöntemin `Await` içindeki anahtar kelimeyi kullanırken, yöntemin veya `async` `Async` anahtar kelimeyle işaretli olması beklenir. Ancak, bu durumda değilse, yöntemi eşsenkronize yapan bir Hızlı Eylem görüntülenir. Hızlı İşlemler menüsünden **Yöntem Yap/İşlev asynchronous** seçeneğini kullanın.

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

| Hata Kimliği | Uygulanabilir Diller | Desteklenen Sürüm |
| ------- | -------------------- | ---------------- |
| CS4032, BC37057 | C# ve Visual Basic | Visual Studio 2017 ve sonrası |

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Eylemler](../ide/quick-actions.md)
