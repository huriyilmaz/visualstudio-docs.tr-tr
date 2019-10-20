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
ms.openlocfilehash: f5a36ee8cffc221d15243ff72e2e71558e867319
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645404"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Örneklendirilmemiş iç sınıflardan kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir derleme düzeyi türünün örneği, derleme içindeki kod tarafından oluşturulmaz.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, türün oluşturucularından birine yönelik çağrıyı bulmaya çalışır ve hiçbir çağrı bulunmazsa bir ihlalin bildirir.

 Aşağıdaki türler bu kural tarafından incelendi:

- Değer türleri

- Soyut türler

- Numaralandırmalar

- Temsilciler

- Derleyicinin yayınlaması dizi türleri

- Örneklenemez ve yalnızca `static` (`Shared` Visual Basic) yöntemlerinde tanımlayan türler.

  Çözümlenmekte olan derlemeye <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> uygularsanız, bir alanın başka bir `friend` derlemesi tarafından kullanılıp kullanılmadığını söyleyeceğinden, bu kural `internal` olarak işaretlenen herhangi bir Oluşturucu üzerinde gerçekleşmeyecektir.

  @No__t_0 kodu analizinde bu kısıtlamayı geçici olarak çözemeseniz bile, her `friend` derlemesi Analize mevcutsa, dış tek başına FxCop iç oluşturucular üzerinde gerçekleşmeyecektir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, türü kaldırın veya onu kullanan kodu ekleyin. Tür yalnızca statik yöntemler içeriyorsa, derleyicinin varsayılan bir ortak örnek Oluşturucu yaymasını engellemek için aşağıdakilerden birini türüne ekleyin:

- 1,0 ve 1,1 sürümlerini [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] hedefleyen türler için özel Oluşturucu.

- @No__t_2 hedefleyen türler için `static` (Visual Basic `Shared`) değiştiricisi.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı gizlemek güvenlidir. Aşağıdaki durumlarda bu uyarıyı bastırmalarını öneririz:

- Sınıfı, <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> gibi geç bağlantılı yansıma yöntemleriyle oluşturulur.

- Sınıf, çalışma zamanı veya [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] tarafından otomatik olarak oluşturulur. Örneğin, <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> veya <xref:System.Web.IHttpHandler?displayProperty=fullName> uygulayan sınıflar.

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
 [CA1811: Çağrılmayan özel kodlardan kaçının](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1801: Kullanılmayan parametreleri gözden geçir](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Kullanılmayan yerel öğeleri kaldırın](../code-quality/ca1804-remove-unused-locals.md)
