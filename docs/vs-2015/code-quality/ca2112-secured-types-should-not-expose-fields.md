---
title: 'CA2112: güvenli türler alanları açığa sunmamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4267b4f55f78106a4d1e8f3b2f9b296be9ddf618
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546542"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: Güvenli türler alanları açığa çıkarmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ortak veya korumalı bir tür ortak alanlar içerir ve bir [bağlantı taleplerine](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)göre güvenli hale getirilir.

## <a name="rule-description"></a>Kural Tanımı
 Bağlantı talebi tarafından güvenli türde bir örnek kod erişimi varsa, kod türün alanlarına erişmek için bağlantı talebine sahip değildir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için alanları ortak yapın ve alan verilerini döndüren ortak özellikler veya yöntemler ekleyin. Türler üzerinde LinkDemand güvenlik denetimleri, türün özelliklerine ve yöntemlerine erişimi korur. Ancak, kod erişim güvenliği alanlar için geçerlidir.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Hem güvenlik sorunları hem de iyi tasarım için genel alanları ortak hale getirerek ihlalleri çözmeniz gerekir. Alan güvenli kalması gereken bilgileri içermiyorsa ve alanın içeriğine bağlı değilseniz, bu kuraldan bir uyarıyı gizleyebilirsiniz.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `SecuredTypeWithFields` güvenli olmayan alanları olan bir kitaplık türünden () oluşur, `Distributor` kitaplık türünün örneklerini oluşturabileceğiniz bir tür () ve yanlış bir şekilde örnekleri, türü güvenlik altına alan izne sahip olmasa bile bir örneğin alanlarını okuyabilen uygulama kodu.

 Aşağıdaki kitaplık kodu, kuralı ihlal ediyor.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>Örnek
 Uygulama, güvenli türü koruyan bağlantı talebi nedeniyle bir örnek oluşturamıyor. Aşağıdaki sınıf, uygulamanın güvenli türdeki bir örneği almasını sağlar.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama, güvenli bir tür yöntemlerine erişim izni olmadan, kodun alanlarına erişip erişecebileceği gösterilmektedir.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **Bir SecuredTypeWithFields örneği oluşturuluyor.** 
 **Güvenli tür alanları: 22, 33** 
 **Güvenli türün alanı değiştiriliyor...** 
 **Önbelleğe alınmış nesne alanları: 99, 33**
## <a name="related-rules"></a>İlgili kurallar
 [CA1051: Görünür örnek alanlarını bildirmeyin](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Talep](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [verileri ve modelleme](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) bağlantısı
