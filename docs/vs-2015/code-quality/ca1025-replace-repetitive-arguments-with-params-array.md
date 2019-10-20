---
title: 'CA1025: yinelenen bağımsız değişkenleri params dizisi ile Değiştir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 21d13611a3c4dd11eb691c746f8746347fb9a83b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661975"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Tekrarlanan bağımsız değişkenleri params dizisi ile değiştirin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Ortak bir türdeki ortak veya korumalı yöntemin üçten fazla parametresi vardır ve son üç parametresi aynı türde.

## <a name="rule-description"></a>Kural Tanımı
 Bağımsız değişkenlerin tam sayısı bilindiğinde ve değişken bağımsız değişkenleri aynı türde olduğunda veya aynı türde bir değer geçirirse tekrarlanabilir bağımsız değişkenler yerine bir parametre dizisi kullanın. Örneğin, <xref:System.Console.WriteLine%2A> yöntemi herhangi bir sayıda <xref:System.Object> bağımsız değişken kabul etmek için bir parametre dizisi kullanan genel amaçlı bir aşırı yükleme sağlar.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için yinelenen bağımsız değişkenleri bir parametre dizisi ile değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarının gösterilmemesi her zaman güvenlidir; Ancak, bu tasarım kullanılabilirlik sorunlarına neden olabilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir türü gösterir.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RepeatArgs/cs/FxCop.Design.RepeatArgs.cs#1)]
