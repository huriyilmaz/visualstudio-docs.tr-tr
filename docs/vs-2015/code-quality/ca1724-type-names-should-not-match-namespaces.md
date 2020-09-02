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
ms.openlocfilehash: aa0b73b6608f0dfd5daa4b770b7d780e64704c99
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544436"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Tür adları ad alanları ile eşleşmemelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bir tür adı [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , büyük/küçük harfe duyarsız bir karşılaştırmada ad alanı adlarıyla eşleşir.

## <a name="rule-description"></a>Kural Tanımı
 Tür adları, sınıf kitaplığında tanımlanan ad alanlarının adlarıyla eşleşmemelidir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Bu kuralın ihlali kitaplığın kullanılabilirliğini azaltabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bir sınıf kitaplığı ad alanının adıyla eşleşmeyen bir tür adı seçin [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yeni geliştirme için, bu kuraldan bir uyarıyı bastırmalısınız hiçbir bilinen senaryo oluşmaz. Uyarıyı bastırmadan önce, kitaplığınızdaki kullanıcıların eşleşen ad ile nasıl karışabileceği hakkında dikkatle düşünün. Gönderim kitaplıkları için, bu kuraldan bir uyarıyı bastırın.
