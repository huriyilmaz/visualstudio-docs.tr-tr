---
title: 'CA2201: ayrılmış özel durum türleri yükseltmeyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9533a597a33deaed17ff2a73d56ef306ea7b5613
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546347"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: Ayrılmış özel durum türlerini harekete geçirmeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotRaiseReservedExceptionTypes|
|CheckId|CA2201|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bir yöntem, çok genel olan veya çalışma zamanı tarafından ayrılmış bir özel durum türü oluşturur.

## <a name="rule-description"></a>Kural Tanımı
 Aşağıdaki özel durum türleri kullanıcıya yeterli bilgi sağlamak için çok genel bir durumdur:

- <xref:System.Exception?displayProperty=fullName>

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.SystemException?displayProperty=fullName>

  Aşağıdaki özel durum türleri ayrılmıştır ve yalnızca ortak dil çalışma zamanı tarafından oluşturulmalıdır:

- <xref:System.ExecutionEngineException?displayProperty=fullName>

- <xref:System.IndexOutOfRangeException?displayProperty=fullName>

- <xref:System.NullReferenceException?displayProperty=fullName>

- <xref:System.OutOfMemoryException?displayProperty=fullName>

  **Genel özel durumlar throw**

  Ya da bir kitaplık ya da çerçevede gibi genel bir özel durum türü oluşturursanız, <xref:System.Exception> <xref:System.SystemException> müşterileri nasıl ele alınacağını bilmeyen bilinmeyen özel durumlar da dahil olmak üzere tüm özel durumları yakalayacak şekilde zorlar.

  Bunun yerine, çerçevede zaten bulunan daha fazla türetilmiş bir tür oluşturun ya da ' den türetilen kendi türünü oluşturun <xref:System.Exception> .

  **Belirli özel durumlar oluşturun**

  Aşağıdaki tabloda, bir özelliğin set erişimcisinde value parametresi de dahil olmak üzere parametresini doğruladığınızda, parametreleri ve hangi özel durumların oluşturulacağı gösterilmektedir:

|Parametre açıklaması|Özel durum|
|---------------------------|---------------|
|`null`başvurunun|<xref:System.ArgumentNullException?displayProperty=fullName>|
|İzin verilen değer aralığının dışında (bir koleksiyon veya liste için Dizin gibi)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|Geçersiz `enum` değer|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|Bir yöntemin parametre belirtimlerini karşılamayan bir biçim içerir (örneğin, için biçim dizesi gibi `ToString(String)` )|<xref:System.FormatException?displayProperty=fullName>|
|Aksi takdirde geçersiz|<xref:System.ArgumentException?displayProperty=fullName>|

 Bir nesnenin geçerli durumu için geçersiz bir işlem<xref:System.InvalidOperationException?displayProperty=fullName>

 Atılmış bir nesne üzerinde bir işlem gerçekleştirildiğinde<xref:System.ObjectDisposedException?displayProperty=fullName>

 Bir işlem desteklenmadığında (örneğin, geçersiz kılınan bir **akışta** ) throw<xref:System.NotSupportedException?displayProperty=fullName>

 Bir dönüştürme bir taşma ile sonuçlanacaksa (örneğin, açık bir atama işleci aşırı yüklemesi) throw<xref:System.OverflowException?displayProperty=fullName>

 Diğer tüm durumlar için, ' den türetilen kendi türünü oluşturmayı düşünün <xref:System.Exception> ve bunu oluşturun.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, oluşturulan özel durumun türünü ayrılmış türlerden biri olmayan belirli bir türe değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="related-rules"></a>İlgili kurallar
 [CA1031: Genel özel durum türlerini yakalamayın](../code-quality/ca1031-do-not-catch-general-exception-types.md)
