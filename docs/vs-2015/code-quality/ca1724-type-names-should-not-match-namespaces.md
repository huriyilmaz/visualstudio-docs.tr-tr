---
title: 'CA1724: tür adları ad alanlarıyla eşleşmemelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 53c99e34bf253b0962d054685ce637c3849a2857
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671590"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Tür Adları Ad Alanlarıyla Eşleşmemelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Tür adı, büyük/küçük harfe duyarsız bir karşılaştırmayla [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ad alanı adlarıyla eşleşir.

## <a name="rule-description"></a>Kural Tanımı
 Tür adları [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sınıfı kitaplığında tanımlanan ad alanlarının adlarıyla eşleşmemelidir. Bu kuralın ihlali kitaplığın kullanılabilirliğini azaltabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 @No__t_0 sınıf kitaplığı ad alanı adıyla eşleşmeyen bir tür adı seçin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yeni geliştirme için, bu kuraldan bir uyarıyı bastırmalısınız hiçbir bilinen senaryo oluşmaz. Uyarıyı bastırmadan önce, kitaplığınızdaki kullanıcıların eşleşen ad ile nasıl karışabileceği hakkında dikkatle düşünün. Gönderim kitaplıkları için, bu kuraldan bir uyarıyı bastırın.
