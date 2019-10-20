---
title: 'CA2207: değer türü statik alanları satır içi Başlat | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a2b3c1faf4ecf3ecf79a3c78d0ded106b88345ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609372"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Değer türü statik alanları satır içi başlatın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Değer türü açık bir statik oluşturucu bildirir.

## <a name="rule-description"></a>Kural Tanımı
 Bir değer türü bildirildiğinde, tüm değer türü alanları sıfıra ayarlandığı ve tüm başvuru türü alanları `null` (Visual Basic `Nothing`) olarak ayarlandığı varsayılan bir başlatma daha olur. Açık bir statik oluşturucunun yalnızca bir örnek Oluşturucu veya türün statik üyesi çağrılmadan önce çalıştırılması garanti edilir. Bu nedenle, tür bir örnek Oluşturucusu çağrılmadan oluşturulduysa, statik oluşturucunun çalıştırılması garanti edilmez.

 Tüm statik veriler satır içi olarak başlatılmışsa ve açık statik Oluşturucu bildirilmemiş ise, C# ve Visual Basic DERLEYICILERI, MSIL sınıf tanımına `beforefieldinit` bayrağını ekler. Derleyiciler statik başlatma kodunu içeren bir özel statik oluşturucu da ekler. Bu özel statik oluşturucunun, türdeki herhangi bir statik alana erişilebilmesi için çalıştırılması garanti edilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, bildirildiği zaman tüm statik verileri başlatın ve statik oluşturucuyu kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="related-rules"></a>İlgili kurallar
 [CA1810: Başvuru türü statik alanları satır içi başlatın](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)
