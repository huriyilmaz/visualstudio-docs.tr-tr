---
title: 'CA1700: ayrılmış &#39;&#39; Enum değerlerini adlandırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9b5ddeb77a255bcfab121746cd8748c6fcb1f113
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669311"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: ayrılmış Enum değerlerini &#39;adlandırma&#39;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir numaralandırma üyesinin adı "ayrılmış" sözcüğünü içerir.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, "ayrılmış" içeren bir ada sahip numaralandırma üyesi şu anda kullanılmamaktadır ancak yeniden adlandırılabilir veya gelecekteki bir sürüme kaldırıldığını varsayar. Üye kaldırma veya yeniden adlandırma bölünmesi farklıdır. Kullanıcıların, adı "ayrılmış" içerdiğinden veya belgelere göre okumak veya onları okumak için kullanıcılara güvenebilmesi için, yalnızca bir üyeyi yok saymasını beklememelisiniz. Ayrıca, ayrılmış Üyeler nesne tarayıcılarında ve akıllı tümleşik geliştirme ortamlarında göründüğünden, gerçekte hangi üyelerin kullanıldığı hakkında karışıklık oluşmasına neden olabilirler.

 Ayrılmış bir üye kullanmak yerine gelecekteki sürümde numaralandırmaya yeni bir üye ekleyin. Çoğu durumda, ek olarak özgün üyelerin değerlerinin değişmesine neden olmadığı sürece yeni üyenin eklenmesi bir son değişiklik değildir.

 Sınırlı sayıda durumda, özgün Üyeler orijinal değerlerini korusa bile bir üyenin eklenmesi Son değişiklik olur. Birincil olarak, yeni üye, tüm üye listesini kapsayan ve varsayılan durumda özel durum oluşturan dönüş değerindeki bir `switch` ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `Select`) ifadesinde kullanan çağıranlar olmadan mevcut kod yollarından geri döndürülemez. İkincil bir sorun, istemci kodunun <xref:System.Enum.IsDefined%2A?displayProperty=fullName> gibi yansıma yöntemlerinden davranış değişikliğini işleyemeyebilir. Buna uygun olarak, yeni üyenin mevcut metotlardan döndürülmesi gerekiyorsa veya kötü yansıma kullanımı nedeniyle bilinen bir uygulama uyumsuzluğu oluşursa, tek bölünemez çözüm şu şekilde olur:

1. Özgün ve yeni üyeleri içeren yeni bir sabit listesi ekleyin.

2. Özgün numaralandırmayı <xref:System.ObsoleteAttribute?displayProperty=fullName> özniteliğiyle işaretleyin.

   Tüm dışarıdan görünen türler veya özgün numaralandırmayı kullanıma sunan Üyeler için aynı yordamı izleyin.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için üyeyi kaldırın veya yeniden adlandırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Şu anda kullanılan bir üyenin veya daha önce sevk edilen kitaplıklarda bu kuraldan bir uyarının görüntülenmesini güvenlidir.

## <a name="related-rules"></a>İlgili kurallar
 [CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1712: Numaralandırma değerleri için tür adıyla önek kullanmayın](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: Numaralandırma depolaması Int32 olmalıdır](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1008: Numaralandırmalar sıfır değerine sahip olmalıdır](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: Numaralandırmaları FlagsAttribute ile işaretleyin](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
