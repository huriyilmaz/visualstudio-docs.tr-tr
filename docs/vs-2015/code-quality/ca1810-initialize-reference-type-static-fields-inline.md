---
title: 'CA1810: başvuru türü statik alanları satır içi Başlat | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c4ad2f4db9290430bb8a378bd264078370ca7b66
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543838"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Başvuru türü statik alanları satır içinden başlatın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Başvuru türü açık bir statik oluşturucu bildirir.

## <a name="rule-description"></a>Kural Tanımı
 Bir tür açık statik yapıcı bildirdiğinde, JIT derleyici her bir statik yöntemi kontrol ekler ve türün yapıcı örneği statik yapıcının daha önceden çağrıldığından emin olur. Statik başlatma, herhangi bir statik üyeye erişildiğinde veya türün bir örneği oluşturulduğunda tetiklenir. Ancak, türün bir değişkenini bildirirseniz ancak kullanmıyorsanız, başlatma genel durumu değiştirdiğinde önemli olabilecek bir statik başlatma tetiklenmez.

 Tüm statik veriler satır içi olarak başlatıldığında ve açık bir statik Oluşturucu bildirilmemiş ise, Microsoft ara dili (MSIL) derleyicileri `beforefieldinit` bayrağı ve statik verileri Başlatan bir örtük statik OLUŞTURUCUYU MSIL tür tanımına ekler. JıT derleyicisi `beforefieldinit` bayrağıyla karşılaştığında, çoğu zaman statik oluşturucu denetimleri eklenmez. Statik başlatma, bir statik bir yöntem veya örnek Oluşturucu çağrılmadan önce değil, herhangi bir statik alana erişilmediği, ancak bir süre önce oluşma garantisi. Statik başlatmanın, türden bir değişken bildirildiğinde herhangi bir zamanda gerçekleşebileceğini unutmayın.

 Statik oluşturucu denetimleri performansı düşürebilir. Genellikle statik bir Oluşturucu yalnızca statik alanları başlatmak için kullanılır, bu durumda yalnızca statik başlatmanın statik bir alana ilk erişimden önce meydana geldiğinden emin olmanız gerekir. `beforefieldinit`Bu davranış, ve diğer birçok tür için uygundur. Yalnızca statik başlatma genel durumu etkiliyorsa ve aşağıdakilerden biri doğru olduğunda uygunsuz olur:

- Genel durum üzerindeki etkisi pahalıdır ve tür kullanılmazsa gerekli değildir.

- Genel durum efektlerine, türdeki herhangi bir statik alana erişmeden erişilebilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için bildirildiğinde, tüm statik veriyi başlatın ve statik oluşturucuyu kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Performans sorunu değilse, bu kuraldan bir uyarı bastırmak güvenlidir; veya statik başlatmanın neden olduğu genel durum değişiklikleri pahalıdır veya türün statik bir yöntemi çağrılmadan veya türün bir örneği oluşturulmadan önce gerçekleşmesi gerekir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı `StaticConstructor` ve bir türü ihlal eden bir türü gösterir, `NoStaticConstructor` Bu, kuralı karşılamak için statik oluşturucunun satır içi başlatma ile yerini almıştır.

 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/cs/FxCop.Performance.RefTypeStaticCtor.cs#1)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/vb/FxCop.Performance.RefTypeStaticCtor.vb#1)]

 `beforefieldinit`Sınıfı IÇIN MSIL tanımına bayrağın eklenmesini aklınızda yapın `NoStaticConstructor` .

 **. Class public Auto ANSI StaticConstructor** , **[mscorlib] System. Object** 
 **{** 
 **}//StaticConstructor sınıfının sonunu**genişletiyor 
 **. sınıf genel otomatik ANSI beforefiledinit NoStaticConstructor** , **[mscorlib] System. Object** 
 **{** 
 **}//NoStaticConstructor sınıfının sonunu** genişletiyor
## <a name="related-rules"></a>İlgili kurallar
 [CA2207: Değer türü statik alanları satır içi başlatın](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)
