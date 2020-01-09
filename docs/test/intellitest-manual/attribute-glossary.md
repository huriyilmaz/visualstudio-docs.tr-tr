---
title: Öznitelik sözlüğü | Microsoft IntelliTest geliştirici test aracı
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594311"
---
# <a name="attribute-glossary"></a>Öznitelik sözlüğü

## <a name="attributes-by-namespace"></a>Ad alanına göre öznitelikler

* **Microsoft.Pex.Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
    * [PexExplorationAttributeBase](#pexexplorationattributebase)

* **Microsoft. Pex. Framework. Settings**
  * [PexAssemblySettings](#pexassemblysettings)

* **Microsoft.Pex.Framework.Instrumentation**
  * [PexAssemblyUnderTest](#pexassemblyundertest)
  * [PexInstrumentAssembly](#pexinstrumentassemblyattribute)

* **Microsoft. Pex. Framework. using**
  * [PexUseType](#pexusetype)

* **Microsoft.Pex.Framework.Validation**
  * [PexAllowedException](#pexallowedexception)
  * [PexAllowedExceptionFromAssembly](#pexallowedexceptionfromassembly)
  * [PexAllowedExceptionFromType](#pexallowedexceptionfromtype)
  * [PexAllowedExceptionFromTypeUnderTest](#pexallowedexceptionfromtypeundertest)

<a name="pexassumenotnull"></a>
## <a name="pexassumenotnull"></a>PexAssumeNotNull

Bu öznitelik, yönetilen değerin **null**olamaz. Bu, şu şekilde iliştirilebilir:

* Parametreli test yönteminin **parametresi**

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

Ayrıca bir test derlemesine, test armakoduna veya test yöntemine eklenebilir; Bu durumda, ilk bağımsız değişkenlerin varsayımlar uygulanan alan veya tür olduğunu belirtmesi gerekir. Öznitelik bir tür için geçerliyse, bu biçimsel türdeki tüm alanlar için geçerlidir.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

Bu öznitelik, *araştırma*içeren bir sınıfı işaretler. MSTest **TestClassAttribute** (veya NUnit **TestFixtureAttribute**) eşdeğerdir. Bu öznitelik isteğe bağlıdır.

[PexClass](#pexclass) ile işaretlenen sınıflar *varsayılan oluşturulabilir*olmalıdır:

* Genel olarak dışarıya aktarılmış tür
* varsayılan oluşturucu
* Özet değil

Sınıf bu gereksinimleri karşılamıyorsa, bir hata bildirilir ve araştırma başarısız olur.

IntelliTest 'in sınıfın parçası olan, ancak ayrı bir dosyada yeni testler oluşturabileceği şekilde bu sınıfları **kısmi** yapmak da önemle tavsiye edilir. Bu yaklaşım, [görünürlük](input-generation.md#visibility) nedeniyle birçok sorunu çözer ve içinde C#tipik bir tekniktir.

**Ek paket ve Kategoriler**:

```csharp
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**Test altındaki türü belirtme**:

```csharp
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

Sınıfı, [PexMethod](#pexmethod)ile açıklama eklenmiş yöntemler içerebilir. IntelliTest Ayrıca [ayarlama ve ayırma yöntemlerini](test-generation.md#setup-teardown)de anlamıştır.

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

Bu öznitelik, [genel parametreli birim testi](test-generation.md#generic-parameterized)örneği oluşturmak için bir tür tanımlama grubu sağlar.

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

Bu öznitelik, bir yöntemi [parametreli birim testi](test-generation.md#parameterized-unit-testing)olarak işaretler.
Yöntem, [PexClass](#pexclass) özniteliğiyle işaretlenmiş bir sınıf içinde bulunmalıdır.

IntelliTest, farklı parametrelerle [parametreli birim testi](test-generation.md#parameterized-unit-testing) çağıran geleneksel, parametresiz testler oluşturacaktır.

Parametreli birim testi:

* bir örnek yöntemi olmalıdır
* oluşturulan testlerin, [Ayarlar şelale](settings-waterfall.md) göre yerleştirildiği test sınıfına [görünür](input-generation.md#visibility) olması gerekir
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
## <a name="pexexplorationattributebase"></a>Pexaraştırması Ationattributebase

[Daha fazla bilgi](xref:Microsoft.Pex.Framework.PexExplorationAttributeBase)

<a name="pexassemblysettings"></a>
## <a name="pexassemblysettings"></a>PexAssemblySettings

Bu öznitelik, tüm araştırmalar için varsayılan ayar değerlerini geçersiz kılmak üzere derleme düzeyinde ayarlanabilir.

```csharp
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "MSTestv2")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

Bu öznitelik, geçerli test projesi tarafından test edilmekte olan bir derlemeyi belirtir.

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

Bu öznitelik, bir derlemeyi belirlemek için kullanılır.

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

Bu öznitelik, IntelliTest 'e, temel türler veya arabirimler oluşturmak için belirli bir tür kullanıp kullanmayacağını söyler.

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

Bu öznitelik bir [PexMethod](#pexmethod) 'a (veya bir [PexClass](#pexclass)'a) eklenmişse, testlerin ne zaman başarısız olduğunu gösteren varsayılan IntelliTest mantığını değiştirir. Belirtilen özel durumu oluşturan bile test başarısız olarak değerlendirilmeyecektir.

**Örnek**

Aşağıdaki test, **yığın** oluşturucusunun bir **ArgumentOutOfRangeException**oluşturmayacağını belirtir:

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

Filtre, aşağıdaki gibi bir armatürü öğesine iliştirilir (derleme veya test düzeyinde de tanımlanabilir):

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
