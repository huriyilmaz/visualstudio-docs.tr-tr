---
title: 'CA2207: Değer türü statik alanları satır içi başlatın'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 695f15c73120f766157fabb09193d32115dda588
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305936"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Değer türü statik alanları satır içi başlatın

|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Category|Microsoft. Usage|
|Son değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
Değer türü açık bir statik oluşturucu bildirir.

## <a name="rule-description"></a>Kural açıklaması
Bir değer türü bildirildiğinde, tüm değer türü alanları sıfıra ayarlandığı ve tüm başvuru türü alanları `null` (Visual Basic `Nothing`) olarak ayarlandığı varsayılan bir başlatma daha olur. Açık bir statik oluşturucunun yalnızca bir örnek Oluşturucu veya türün statik üyesi çağrılmadan önce çalıştırılması garanti edilir. Bu nedenle, tür bir örnek Oluşturucusu çağrılmadan oluşturulduysa, statik oluşturucunun çalıştırılması garanti edilmez.

Tüm statik veriler satır içi olarak başlatılmışsa ve açık statik Oluşturucu bildirilmemiş ise, C# ve Visual Basic DERLEYICILERI, MSIL sınıf tanımına `beforefieldinit` bayrağını ekler. Derleyiciler statik başlatma kodunu içeren bir özel statik oluşturucu da ekler. Bu özel statik oluşturucunun, türdeki herhangi bir statik alana erişilebilmesi için çalıştırılması garanti edilir.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kuralın ihlalini onarmak için, bildirildiği zaman tüm statik verileri başlatın ve statik oluşturucuyu kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Bu kuraldan uyarıyı bastırmayın.

## <a name="related-rules"></a>İlgili kurallar
[CA1810: Başvuru türü statik alanlarını Başlat satır içi @ no__t-0