---
title: 'CA1504: yanıltıcı alan adlarını gözden geçirin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c3f1cca5dd33047a4d19c78013dd535e0e9dd6f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607761"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Yanlış alan adlarını gözden geçirin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Kategori|Microsoft. Bakımolmaması|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir örnek alanının adı "s_" ile başlar veya bir `static` adı ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `Shared`) alanında "m_" ile başlar.

## <a name="rule-description"></a>Kural Tanımı
 "S_" ile başlayan alan adları, birçok kullanıcı tarafından statik verilerle ilişkilendirilir. Benzer şekilde, "m_" ile başlayan alan adları, örnek (üye) verilerle ilişkilendirilir. Daha kolay yönetilebilir kod için adlar genellikle kullanılan kurallara uymalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, uygun öneki kullanarak alanı yeniden adlandırın. Alternatif olarak, `static` değiştiricisini ekleyerek veya kaldırarak alanı geçerli soneke kabul edin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.
