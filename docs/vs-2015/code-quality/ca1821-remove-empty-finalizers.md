---
title: 'CA1821: boş sonlandırıcıları kaldır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a2e704202773447e353f041df66b05cb5f648c00
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545359"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Boş sonlandırıcıları kaldırın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|Removeemptyfinalleyiciler|
|CheckId|CA1821|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir tür, boş bir Sonlandırıcı uygular, yalnızca temel tür sonlandırıcısını çağırır veya yalnızca koşullu olarak yayınlanan yöntemleri çağırır.

## <a name="rule-description"></a>Kural Tanımı
 Güncelleştirirken, nesne kullanım süresini izleme söz konusu olduğunda ek performans yükü nedeniyle sonlandırıcılardan kaçının. Çöp toplayıcı, nesneyi toplamadan önce sonlandırıcıyı çalıştırır. Bu, nesnenin toplanması için iki koleksiyonun gerekli olacağı anlamına gelir. Boş bir Sonlandırıcı bu ek yükü herhangi bir avantajsız olarak doğurur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Boş sonlandırıcıyı kaldırın. Hata ayıklama için bir Sonlandırıcı gerekliyse, tüm sonlandırıcıyı yönergelerden çevreden alın `#if DEBUG / #endif` .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir ileti bastırmayın. Sonlandırma performansı gizlenmemesi ve hiçbir avantaj sunamaması.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kaldırılması gereken boş bir Sonlandırıcı, yönergeler içine alınması gereken sonlandırıcının `#if DEBUG / #endif` ve yönergeleri doğru bir şekilde kullanan sonlandırıcının gösterildiği gösterilmektedir `#if DEBUG / #endif` .

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]
