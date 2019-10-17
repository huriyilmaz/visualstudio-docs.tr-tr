---
title: 'CA1700: ayrılmış Enum değerlerini &#39;adlandırma&#39;'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7642885a953f4974a9440acced027552bd64f72e
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440000"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: ayrılmış Enum değerlerini &#39;adlandırma&#39;

|||
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|Kategori|Microsoft. Naming|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep

Bir numaralandırma üyesinin adı "ayrılmış" sözcüğünü içerir.

## <a name="rule-description"></a>Kural açıklaması

Bu kural, "ayrılmış" içeren bir ada sahip numaralandırma üyesi şu anda kullanılmamaktadır ancak yeniden adlandırılabilir veya gelecekteki bir sürüme kaldırıldığını varsayar. Üye kaldırma veya yeniden adlandırma bölünmesi farklıdır. Kullanıcıların, adı "ayrılmış" içerdiğinden veya belgelere göre okumak veya onları okumak için kullanıcılara güvenebilmesi için, yalnızca bir üyeyi yok saymasını beklememelisiniz. Ayrıca, ayrılmış Üyeler nesne tarayıcılarında ve akıllı tümleşik geliştirme ortamlarında göründüğünden, gerçekte hangi üyelerin kullanıldığı hakkında karışıklık oluşmasına neden olabilirler.

Ayrılmış bir üye kullanmak yerine gelecekteki sürümde numaralandırmaya yeni bir üye ekleyin. Çoğu durumda, ek olarak özgün üyelerin değerlerinin değişmesine neden olmadığı sürece yeni üyenin eklenmesi bir son değişiklik değildir.

Sınırlı sayıda durumda, özgün Üyeler orijinal değerlerini korusa bile bir üyenin eklenmesi Son değişiklik olur. Birincil olarak, yeni üye, tüm üye listesini kapsayan ve varsayılan durumda özel durum oluşturan dönüş değerindeki bir `switch` (@no__t-@no__t 1) bildiriminde olmayan çağıranlar olmadan mevcut kod yollarından geri döndürülemez. İkincil bir sorun, istemci kodunun <xref:System.Enum.IsDefined%2A?displayProperty=fullName> gibi yansıma yöntemlerinden davranış değişikliğini işleyemeyebilir. Buna uygun olarak, yeni üyenin mevcut metotlardan döndürülmesi gerekiyorsa veya kötü yansıma kullanımı nedeniyle bilinen bir uygulama uyumsuzluğu oluşursa, tek bölünemez çözüm şu şekilde olur:

1. Özgün ve yeni üyeleri içeren yeni bir sabit listesi ekleyin.

2. Özgün numaralandırmayı <xref:System.ObsoleteAttribute?displayProperty=fullName> özniteliğiyle işaretleyin.

   Tüm dışarıdan görünen türler veya özgün numaralandırmayı kullanıma sunan Üyeler için aynı yordamı izleyin.

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Bu kural ihlalini onarmak için üyeyi kaldırın veya yeniden adlandırın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Şu anda kullanılan bir üyenin veya daha önce sevk edilen kitaplıklarda bu kuraldan bir uyarının görüntülenmesini güvenlidir.

## <a name="related-rules"></a>İlgili kurallar

[CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217.md)

[CA1712: Numaralandırma değerleri için tür adıyla önek kullanmayın](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

[CA1028: Numaralandırma depolaması Int32 olmalıdır](../code-quality/ca1028-enum-storage-should-be-int32.md)

[CA1008: Numaralandırmalar sıfır değerine sahip olmalıdır](../code-quality/ca1008-enums-should-have-zero-value.md)

[CA1027: Numaralandırmaları FlagsAttribute ile işaretleyin](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
