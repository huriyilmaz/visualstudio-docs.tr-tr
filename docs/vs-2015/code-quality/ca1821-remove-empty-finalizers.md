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
ms.openlocfilehash: 3d340d69ee32de20142abf740f7fedc871c9733a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657470"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Boş sonlandırıcıları kaldırın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|Removeemptyfinalleyiciler|
|CheckId|CA1821|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir tür, boş bir Sonlandırıcı uygular, yalnızca temel tür sonlandırıcısını çağırır veya yalnızca koşullu olarak yayınlanan yöntemleri çağırır.

## <a name="rule-description"></a>Kural Tanımı
 Güncelleştirirken, nesne kullanım süresini izleme söz konusu olduğunda ek performans yükü nedeniyle sonlandırıcılardan kaçının. Çöp toplayıcı, nesneyi toplamadan önce sonlandırıcıyı çalıştırır. Bu, nesnenin toplanması için iki koleksiyonun gerekli olacağı anlamına gelir. Boş bir Sonlandırıcı bu ek yükü herhangi bir avantajsız olarak doğurur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Boş sonlandırıcıyı kaldırın. Hata ayıklama için bir Sonlandırıcı gerekliyse, tüm sonlandırıcıyı `#if DEBUG / #endif` yönergelerden alın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir ileti bastırmayın. Sonlandırma performansı gizlenmemesi ve hiçbir avantaj sunamaması.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, kaldırılması gereken boş bir Sonlandırıcı, `#if DEBUG / #endif` yönergeler içine alınması gereken sonlandırıcının ve `#if DEBUG / #endif` yönergelerini doğru bir şekilde kullanan sonlandırıcının gösterildiği gösterilmektedir.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]
