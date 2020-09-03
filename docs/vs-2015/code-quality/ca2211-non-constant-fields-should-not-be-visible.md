---
title: 'CA2211: sabit olmayan alanlar görünür olmamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aa67c33eac5d618c0a080323720775beea7b68c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548219"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: Sabit olmayan alanlar görünür olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ortak veya korumalı bir statik alan sabit değildir ve salt okunurdur.

## <a name="rule-description"></a>Kural Tanımı
 Ne sabitler, ne de salt okunur olan statik alanlar güvenli iş parçacığı değildir. Bu tür bir alana erişimin dikkatle denetlenmesi ve sınıf nesnesine erişimin eşitlenmesi için gelişmiş programlama teknikleri olması gerekir. Bunlar öğrenmek ve ana öğe hakkında zor beceriler olduğundan, bu tür bir nesnenin test edilmesi, kendi zorluk sergilediğinin yanı sıra, değişmeyen verileri depolamak için en iyi şekilde kullanılır. Bu kural kitaplıklar için geçerlidir; uygulamalar herhangi bir alanı kullanıma sunmamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için statik alanı sabit veya salt okunurdur yapın. Bu mümkün değilse, temel alana iş parçacığı açısından güvenli erişimi yöneten iş parçacığı güvenli özelliği gibi alternatif bir mekanizma kullanmak için türü yeniden tasarlayabiliriz. Kilit çakışması ve kilitlenmeleri gibi sorunların, kitaplığın performansını ve davranışını etkileyebileceğini fark edebilirsiniz.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bir uygulama geliştiriyorsanız bu kuraldan bir uyarıyı gizlemek güvenlidir ve bu nedenle statik alanı içeren türe erişim üzerinde tam denetime sahip olursunuz. Kitaplık tasarımcıları bu kuraldan bir uyarı göstermemelidir; sabit olmayan statik alanları kullanmak, geliştiricilerin doğru bir şekilde kullanması için kitaplık kullanımını zorlaştırır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir türü gösterir.

 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/cs/FxCop.Usage.AvoidStaticNonConstants.cs#1)]
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/vb/FxCop.Usage.AvoidStaticNonConstants.vb#1)]
