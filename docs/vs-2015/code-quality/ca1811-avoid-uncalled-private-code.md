---
title: 'CA1811: çağrılmadı özel koddan kaçının | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 223b2ff9aa25ddd94a3c62eb9e641127a1cace4e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543825"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Çağırılmayan özel kodlardan kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Özel veya iç (derleme düzeyi) bir üyenin derlemede çağıranları yok, ortak dil çalışma zamanı tarafından Çağrılmıyor ve bir temsilci tarafından çağrılmıyor. Aşağıdaki Üyeler bu kural tarafından denetlenmiyor:

- Açık arabirim üyeleri.

- Statik oluşturucular.

- Serileştirme oluşturucuları.

- Veya ile işaretlenmiş <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> Yöntemler <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> .

- Geçersiz kılan Üyeler.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, kural mantığı tarafından şu anda tanımlı olmayan giriş noktaları oluşursa, yanlış pozitif durumları bildirebilir. Ayrıca, bir derleyici, çağrılabilir olmayan kodu bir derlemeye yayabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, çağrılabilir olmayan kodu kaldırın veya onu çağıran kodu ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı gizlemek güvenlidir.

## <a name="related-rules"></a>İlgili kurallar
 [CA1812: Örneklenmemiş iç sınıflardan kaçının](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Kullanılmayan parametreleri gözden geçirin](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Kullanılmayan yerelleri kaldırın](../code-quality/ca1804-remove-unused-locals.md)
