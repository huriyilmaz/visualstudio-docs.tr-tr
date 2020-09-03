---
title: 'CA1812: Örneklendirilmemiş iç sınıflardan kaçının | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 401fbfbccfeeeeec5cbdc0e791b110d1b5f0201b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543981"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Örneklenmemiş iç sınıflardan kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir derleme düzeyi türünün örneği, derleme içindeki kod tarafından oluşturulmaz.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, türün oluşturucularından birine yönelik çağrıyı bulmaya çalışır ve hiçbir çağrı bulunmazsa bir ihlalin bildirir.

 Aşağıdaki türler bu kural tarafından incelendi:

- Değer türleri

- Soyut türler

- Listelemeler

- Temsilciler

- Derleyicinin yayınlaması dizi türleri

- Örneklenemez ve `static` `Shared` yalnızca (Visual Basic) yöntemleri tanımlayan türler.

  <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName>Çözümlenmekte olan derlemeye uygularsanız, bu kural, `internal` bir alanın başka bir derleme tarafından kullanılıp kullanılmadığını söyleyeceğinden, olarak işaretlenen herhangi bir Oluşturucu üzerinde gerçekleşmeyecektir `friend` .

  Kod çözümlemede bu sınırlamaya geçici bir çözüm yapmasanız bile [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , her `friend` derleme analizde varsa dış tek başına FxCop iç oluşturucular üzerinde gerçekleşmeyecektir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, türü kaldırın veya onu kullanan kodu ekleyin. Tür yalnızca statik yöntemler içeriyorsa, derleyicinin varsayılan bir ortak örnek Oluşturucu yaymasını engellemek için aşağıdakilerden birini türüne ekleyin:

- 1,0 ve 1,1 sürümlerini hedefleyen türler için özel Oluşturucu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

- `static` `Shared` Hedeflenen türler için (Visual Basic) değiştirici [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı gizlemek güvenlidir. Aşağıdaki durumlarda bu uyarıyı bastırmalarını öneririz:

- Sınıfı, gibi geç bağlantılı yansıma yöntemleriyle oluşturulur <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> .

- Sınıf, çalışma zamanı veya çalışma zamanı tarafından otomatik olarak oluşturulur [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . Örneğin, veya uygulayan sınıflar <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> <xref:System.Web.IHttpHandler?displayProperty=fullName> .

- Sınıfı, yeni kısıtlaması olan bir genel tür parametresi olarak geçirilir. Örneğin, aşağıdaki örnek bu kuralı yükseltir.

  ```csharp
  internal class MyClass
  {
      public DoSomething()
      {
      }
  }
  public class MyGeneric<T> where T : new()
  {
      public T Create()
      {
          return new T();
      }
  }
  // [...]
  MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
  mc.Create();
  ```

  Bu durumlarda, bu uyarıyı bastırdığınız için tavsiye ederiz.

## <a name="related-rules"></a>İlgili kurallar
 [CA1811: Çağırılmayan özel kodlardan kaçının](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1801: Kullanılmayan parametreleri gözden geçirin](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Kullanılmayan yerelleri kaldırın](../code-quality/ca1804-remove-unused-locals.md)
