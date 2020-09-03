---
title: 'CA1061: temel sınıf yöntemlerini gizlemeyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c884eb569d5682326d2dc667363f991467171386
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533360"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: Temel sınıf metotlarını gizlemeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Türetilmiş bir tür, aynı ada sahip ve temel yöntemlerinden biri ile aynı sayıda parametreye sahip bir yöntem bildirir; bir veya daha fazla parametre, temel yöntemde karşılık gelen parametrenin temel türüdür; ve kalan parametrelerde, temel yöntemde karşılık gelen parametrelerle özdeş olan türler vardır.

## <a name="rule-description"></a>Kural Tanımı
 Türetilmiş yöntemin parametre imzası yalnızca temel yöntemin parametre imzasında karşılık gelen türlerden daha zayıf olan türlere göre farklılık gösterdiğinde, temel türdeki bir yöntem türetilmiş bir tür içinde aynı adlı bir yöntem tarafından gizlenir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için yöntemi kaldırın veya yeniden adlandırın ya da yöntemin temel yöntemi gizlemez şekilde parametre imzasını değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden bir yöntemi gösterir.

 [!code-csharp[FxCop.Design.HideBaseMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.HideBaseMethod/cs/FxCop.Design.HideBaseMethod.cs#1)]
