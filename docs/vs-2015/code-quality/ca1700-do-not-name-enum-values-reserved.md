---
title: 'CA1700: Enum değerlerini &#39;ayrılmış&#39; olarak adlandırma | Microsoft Docs'
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
ms.openlocfilehash: 57f2a2e5959860a99a921101ff5782f9bce9ace3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545658"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: &#39;Enum değerlerini ayrılmış&#39; olarak adlandırın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bir numaralandırma üyesinin adı "ayrılmış" sözcüğünü içerir.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, "ayrılmış" içeren bir ada sahip numaralandırma üyesi şu anda kullanılmamaktadır ancak yeniden adlandırılabilir veya gelecekteki bir sürüme kaldırıldığını varsayar. Üye kaldırma veya yeniden adlandırma bölünmesi farklıdır. Kullanıcıların, adı "ayrılmış" içerdiğinden veya belgelere göre okumak veya onları okumak için kullanıcılara güvenebilmesi için, yalnızca bir üyeyi yok saymasını beklememelisiniz. Ayrıca, ayrılmış Üyeler nesne tarayıcılarında ve akıllı tümleşik geliştirme ortamlarında göründüğünden, gerçekte hangi üyelerin kullanıldığı hakkında karışıklık oluşmasına neden olabilirler.

 Ayrılmış bir üye kullanmak yerine gelecekteki sürümde numaralandırmaya yeni bir üye ekleyin. Çoğu durumda, ek olarak özgün üyelerin değerlerinin değişmesine neden olmadığı sürece yeni üyenin eklenmesi bir son değişiklik değildir.

 Sınırlı sayıda durumda, özgün Üyeler orijinal değerlerini korusa bile bir üyenin eklenmesi Son değişiklik olur. Birincil olarak, yeni üye, `switch` `Select` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] tüm üye listesini kapsayan ve varsayılan durumda özel durum oluşturan dönüş değerindeki bir (ın) bildiriminde bir (ın) ifadesinde olmayan çağıranlar olmadan mevcut kod yollarından geri döndürülemez. İkincil bir sorun, istemci kodunun gibi yansıma yöntemlerinden davranış değişikliğini işleyemeyebilir <xref:System.Enum.IsDefined%2A?displayProperty=fullName> . Buna uygun olarak, yeni üyenin mevcut metotlardan döndürülmesi gerekiyorsa veya kötü yansıma kullanımı nedeniyle bilinen bir uygulama uyumsuzluğu oluşursa, tek bölünemez çözüm şu şekilde olur:

1. Özgün ve yeni üyeleri içeren yeni bir sabit listesi ekleyin.

2. Özgün numaralandırmayı <xref:System.ObsoleteAttribute?displayProperty=fullName> özniteliğiyle işaretleyin.

   Tüm dışarıdan görünen türler veya özgün numaralandırmayı kullanıma sunan Üyeler için aynı yordamı izleyin.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için üyeyi kaldırın veya yeniden adlandırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Şu anda kullanılan bir üyenin veya daha önce sevk edilen kitaplıklarda bu kuraldan bir uyarının görüntülenmesini güvenlidir.

## <a name="related-rules"></a>İlgili kurallar
 [CA2217: Sabit listelerini FlagsAttribute ile işaretlemeyin](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1712: Sabit listesi değerlerine tür adını önek olarak eklemeyin](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: Sabit listesi depolaması Int32 olmalıdır](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1008: Sabit listelerinin sıfır değeri olmalıdır](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: Sabit listelerini FlagsAttribute ile işaretleyin](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
