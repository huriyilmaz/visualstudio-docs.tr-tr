---
title: 'CA1053: Statik tutucu türlerinde oluşturucular olamaz | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 29cc322dd59dc0de66af8f92a46524d15b0022c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539587"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: Static tutucu türlerin oluşturucuları olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ortak veya iç içe geçmiş ortak tür yalnızca statik üyeleri bildirir ve ortak veya korumalı varsayılan bir oluşturucu vardır.

## <a name="rule-description"></a>Kural Tanımı
 Statik üyeleri çağırma bir tür örneği gerektirmediğinden kurucu gereksizdir. Ayrıca, tür statik olmayan üyelere sahip olmadığından, örnek oluşturmak türün üyelerinden hiçbirine erişim sağlamaz.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, varsayılan oluşturucuyu kaldırın veya özel yapın.

> [!NOTE]
> Tür herhangi bir Oluşturucu tanımlamıyorsa, bazı derleyiciler otomatik olarak ortak bir varsayılan oluşturucu oluşturur. Bu durumda, ihlalin ortadan kaldırmak için özel bir varsayılan oluşturucu ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Oluşturucunun varlığı türün statik bir tür olmadığını önerir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir türü gösterir. Kaynak kodunda varsayılan Oluşturucu olmadığına dikkat edin. Bu kod bir derlemeye derlendiğinde, C# derleyicisi varsayılan bir Oluşturucu ekleyecektir, bu da kuralı ihlal eder. Bunu düzeltmek için özel bir Oluşturucu bildirin.

 [!code-csharp[FxCop.Design.StaticTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes/cs/FxCop.Design.StaticTypes.cs#1)]
