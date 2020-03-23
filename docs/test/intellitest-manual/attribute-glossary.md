---
title: Öznitelik sözlüğü | Microsoft IntelliTest Geliştirici Test Aracı
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Attribute glossary
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 00d8b24d26237a3c7b4130eba4614b5ea7b7eccd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302632"
---
# <a name="attribute-glossary"></a>Öznitelik sözlüğü

## <a name="attributes-by-namespace"></a>Ad alanına göre öznitelikler

* **Microsoft.Pex.Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
    * [PexExplorationAttributeBase](#pexexplorationattributebase)

* **Microsoft.Pex.Framework.Settings**
  * [PexAssemblySettings](#pexassemblysettings)

* **Microsoft.Pex.Framework.Instrumentation**
  * [PexAssemblyUnderTest](#pexassemblyundertest)
  * [PexInstrumentAssembly](#pexinstrumentassemblyattribute)

* **Microsoft.Pex.Framework.Using**
  * [PexUseType](#pexusetype)

* **Microsoft.Pex.Framework.Validation**
  * [PexAllowedException](#pexallowedexception)
  * [PexAllowedExceptionFromAssembly](#pexallowedexceptionfromassembly)
  * [PexAllowedExceptionFromType](#pexallowedexceptionfromtype)
  * [PexAllowedExceptionFromTypeUnderTest](#pexallowedexceptionfromtypeundertest)

<a name="pexassumenotnull"></a>
## <a name="pexassumenotnull"></a>PexAssumeNotNull

Bu öznitelik, yönetilen değerin **null**olamayacağını ileri sürer. Bu eklenebilir:

* parametreli test yönteminin **parametresi**

  ```csharp
  // assume foo is not null
  [PexMethod]
  public void SomeTest([PexAssumeNotNull]IFoo foo, ...) {}
  ```

* bir **alan**

  ```csharp
  public class Foo {
     // this field should not be null
     [PexAssumeNotNull]
     public object Bar;
  }
  ```

* bir **tür**

  ```csharp
  // never consider null for Foo types
  [PexAssumeNotNull]
  public class Foo {}
  ```

Ayrıca bir test tertibatına, test fikstürüne veya test yöntemine de eklenebilir; Bu durumda ilk bağımsız değişkenler varsayımların hangi alana veya türe uygulandığını göstermelidir. Öznitelik bir türe uygulandığında, bu resmi türe sahip tüm alanlar için geçerlidir.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

Bu *öznitelik, keşifler*içeren bir sınıfı işaretler. BU MSTest **TestClassAttribute** (veya NUnit **TestFixtureAttribute)** eşdeğerdir. Bu öznitelik isteğe bağlıdır.

[PexClass](#pexclass) ile işaretlenmiş sınıflar *varsayılan olarak yapılabilir*olmalıdır:

* kamuya açık tür
* varsayılan oluşturucu
* soyut değil

Sınıf bu gereksinimleri karşılamazsa, bir hata bildirilir ve arama başarısız olur.

Ayrıca, IntelliTest sınıfın bir parçası olan yeni testler üretebilir, böylece bu sınıfları **kısmi** yapmak için güçlü bir şekilde tavsiye edilir, ancak ayrı bir dosyada. Bu yaklaşım [görünürlük](input-generation.md#visibility) nedeniyle birçok sorunu çözer ve C#'da tipik bir tekniktir.

**Ek paket ve kategoriler:**

```csharp
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**Test altındaki türü belirtme:**

```csharp
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

Sınıf, [PexMethod](#pexmethod)ile açıklamalı yöntemler içerebilir. IntelliTest de [kurmak ve yöntemleri yıkmak](test-generation.md#setup-teardown)anlar.

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

Bu [öznitelik, genel parametreli birim testi](test-generation.md#generic-parameterized)anlık için bir tür tuple sağlar.

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

Bu öznitelik, bir yöntemi [parametreli birim testi](test-generation.md#parameterized-unit-testing)olarak işaretler.
Yöntem, [PexClass](#pexclass) özniteliği ile işaretlenmiş bir sınıf içinde yer almalıdır.

IntelliTest, [parametreli birim testini](test-generation.md#parameterized-unit-testing) farklı parametrelerle arayan geleneksel, parametresiz testler üretecektir.

Parametreli birim testi:

* bir örnek yöntem olmalıdır
* oluşturulan testlerin Ayarlar Şelalesi'ne göre yerleştirildiği [Settings Waterfall](settings-waterfall.md) test sınıfına [göre görülebilmeli](input-generation.md#visibility)
* herhangi bir sayıda parametre alabilir
* genel olabilir

**Örnek**

```csharp
[PexClass]
public partial class MyTests {
     [PexMethod]
     public void MyTest(int i)
     { ... }
}
```

<a name="pexexplorationattributebase"></a>
## <a name="pexexplorationattributebase"></a>PexExplorationAttributeBase

[Daha fazla bilgi](xref:Microsoft.Pex.Framework.PexExplorationAttributeBase)

<a name="pexassemblysettings"></a>
## <a name="pexassemblysettings"></a>PexAssemblySettings

Bu öznitelik, tüm keşifler için varsayılan ayar değerlerini geçersiz kılmak için montaj düzeyinde ayarlanabilir.

```csharp
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "MSTestv2")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

Bu öznitelik, geçerli test projesi tarafından sınanmakta olan bir derleme yi belirtir.

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

Bu öznitelik, çalınacak bir derlemeyi belirtmek için kullanılır.

**Örnek**

```csharp
using Microsoft.Pex.Framework;

// the assembly containing ATypeFromTheAssemblyToInstrument should be instrumented
[assembly: PexInstrumentAssembly(typeof(ATypeFromTheAssemblyToInstrument))]

// the assembly name can be used as well
[assembly: PexInstrumentAssembly("MyAssemblyName")]
```

<a name="pexusetype"></a>
## <a name="pexusetype"></a>PexUseType

Bu öznitelik IntelliTest'e, temel türleri veya arabirimleri anlık (soyut) bir tür kullanabileceğini söyler.

**Örnek**

```csharp
[PexMethod]
[PexUseType(typeof(A))]
[PexUseType(typeof(B))]
public void MyTest(object testParameter)
{
     ... // IntelliTest will consider types A and B to instantiate 'testParameter'
}
```

<a name="pexallowedexception"></a>
## <a name="pexallowedexception"></a>PexAllowedException

Bu öznitelik bir [PexMethod](#pexmethod) 'a (veya bir [PexClass'a)](#pexclass)bağlıysa, testlerin ne zaman başarısız olduğunu gösteren varsayılan IntelliTest mantığını değiştirir. Test, belirtilen özel durumu atsa bile başarısız olarak kabul edilmez.

**Örnek**

Aşağıdaki test **Stack** oluşturucu bir **ArgumentOutOfRangeException**atabilir belirtir:

```csharp
class Stack {
  int[] _elements;
  int _count;
  public Stack(int capacity) {
    if (capacity<0) throw new ArgumentOutOfRangeException();
    _elements = new int[capacity];
    _count = 0;
  }
  ...
}
```

Filtre aşağıdaki gibi bir fikstüre eklenir (montaj veya test düzeyinde de tanımlanabilir):

```csharp
[PexMethod]
[PexAllowedException(typeof(ArgumentOutOfRangeException))]
class CtorTest(int capacity) {
  Stack s = new Stack(capacity); // may throw ArgumentOutOfRangeException
}
```

<a name="pexallowedexceptionfromassembly"></a>
## <a name="pexallowedexceptionfromassembly"></a>PexAllowedExceptionFromAssembly

[Daha fazla bilgi](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromAssemblyAttribute)

<a name="pexallowedexceptionfromtype"></a>
## <a name="pexallowedexceptionfromtype"></a>PexAllowedExceptionFromType

[Daha fazla bilgi](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromTypeAttribute)

<a name="pexallowedexceptionfromtypeundertest"></a>
## <a name="pexallowedexceptionfromtypeundertest"></a>PexAllowedExceptionFromTypeUnderTest

[Daha fazla bilgi](xref:Microsoft.Pex.Framework.Validation.PexAllowedExceptionFromTypeUnderTestAttribute)

## <a name="got-feedback"></a>Geri bildirimde mi bulunmak istiyorsunuz?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)’na gönderin.
