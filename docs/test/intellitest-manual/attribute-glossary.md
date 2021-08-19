---
title: Öznitelik sözlüğü | Microsoft IntelliTest Geliştirici Test Aracı
description: Bu makalede ad alanına göre düzenlenmiş IntelliTest özniteliklerinin bir listesi ve özniteliklerin ayrıntıları yer almaktadır.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Attribute glossary
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c15c9be9f8f4f2f8933a289908c27725eb14298e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092429"
---
# <a name="attribute-glossary"></a>Öznitelik sözlüğü

## <a name="attributes-by-namespace"></a>Ad alanına göre öznitelikler

* **Microsoft.Pex.Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
    * [PexExplorationAttributeBase](#pexexplorationattributebase)

* **Microsoft.Pex.Framework. Ayarlar**
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

Bu öznitelik, yönetilen değerin null olayamaz olduğunu **onaylar.** Şu şekilde iliştirilmiş olabilir:

* **parametreli** test yönteminin parametresi

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

Ayrıca bir test derlemesi, test sınaması veya test yöntemine de iliştirilmiş olabilir; Bu durumda, ilk bağımsız değişkenler varsayımların hangi alana veya türe uygulan gerektiğini belirtelim. Öznitelik bir türe uygulandığında, bu resmi türe sahip tüm alanlara uygulanır.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

Bu öznitelik, keşifler içeren bir *sınıfı işaretler.* MSTest **TestClassAttribute** (veya NUnit **TestFixtureAttribute ) ile eşdeğerdir.** Bu öznitelik isteğe bağlıdır.

[PexClass](#pexclass) ile işaretlenmiş sınıfların varsayılan *olarak yapılamaz olması gerekir:*

* genel olarak dışarı aktarıldı türü
* varsayılan oluşturucu
* soyut değil

Sınıfı bu gereksinimleri karşılamıyorsa bir hata bildiriliyor ve araştırma başarısız oluyor.

Ayrıca IntelliTest'in sınıfın  parçası olan ancak ayrı bir dosyada yeni testler oluşturamalarını için bu sınıfların kısmi hale de sahip olunmaları önemle önerilir. Bu yaklaşım, görünürlük nedeniyle birçok sorunu [çözer ve](input-generation.md#visibility) C# ile tipik bir tekniktir.

**Ek paket ve kategoriler:**

```csharp
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**Test altında türü belirtme:**

```csharp
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

sınıfı [PexMethod ile açıklamalı yöntemler içerebilir.](#pexmethod) IntelliTest, ayarlama [ve yok yöntemini de anlar.](test-generation.md#setup-teardown)

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

Bu öznitelik, genel parametreli birim testini örneği için [bir tür tuple sağlar.](test-generation.md#generic-parameterized)

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

Bu öznitelik, bir yöntemi parametreli [birim testi olarak işaretler.](test-generation.md#parameterized-unit-testing)
yöntemi, [PexClass](#pexclass) özniteliğiyle işaretlenmiş bir sınıf içinde yer a olmalıdır.

IntelliTest, parametreli birim testini farklı parametrelerle [çağıran geleneksel, parametresiz](test-generation.md#parameterized-unit-testing) testler oluşturacak.

Parametreli birim testi:

* bir örnek yöntemi olması gerekir
* , [oluşturulan](input-generation.md#visibility) testlerin Ayarlar Waterfall'a göre yerleştiril olduğu test [sınıfına görünür olmalıdır](settings-waterfall.md)
* herhangi bir sayıda parametre al
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

Bu öznitelik, tüm araştırmalarda varsayılan ayar değerlerini geçersiz kılmak için derleme düzeyinde ayarlanır.

```csharp
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "MSTestv2")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

Bu öznitelik, geçerli test projesi tarafından test edilen bir derlemeyi belirtir.

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

Bu öznitelik, takip etmek için bir derleme belirtmek için kullanılır.

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

Bu öznitelik, IntelliTest'e belirli bir tür kullanarak temel türlerin veya arabirimlerin örneğini (soyut) kullanabileceğini söyler.

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

Bu öznitelik bir [PexMethod'a](#pexmethod) (veya [PexClass'a)](#pexclass)eklenmişse, testlerin başarısız olduğunu belirten varsayılan IntelliTest mantığını değiştirir. Belirtilen özel durumu atsa bile test başarısız olarak kabul edilir.

**Örnek**

Aşağıdaki test, **Stack** oluşturucuslarının **ArgumentOutOfRangeException oluşturmasına neden olduğunu belirtir:**

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

Filtre aşağıdaki gibi bir fiilen eklidir (derleme veya test düzeyinde de tanımlanabilir):

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

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://aka.ms/feedback/suggest?space=8)’na gönderin.
