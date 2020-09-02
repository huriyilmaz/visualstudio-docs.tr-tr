---
title: 'CA1716: tanımlayıcılar anahtar sözcüklerle eşleşmemelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 67a3588a857a0eea7d338217f975ed593dfdad52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543708"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Tanımlayıcılar anahtar sözcükler ile eşleşmemelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bir ad alanı, tür veya bir sanal ya da arabirim üyesi, programlama dilinde ayrılmış bir anahtar sözcükle eşleşir.

## <a name="rule-description"></a>Kural Tanımı
 Ad alanları, türler ve sanal ve arabirim üyelerinin tanımlayıcıları, ortak dil çalışma zamanını hedefleyen diller tarafından tanımlanan anahtar sözcüklerle eşleşmemelidir. Kullanılan dile ve anahtar sözcüğüne bağlı olarak, derleyici hataları ve belirsizlikleri, kitaplığı kullanmayı zorlaştırır.

 Bu kural aşağıdaki dillerdeki anahtar sözcüklere karşı denetler:

- Visual Basic

- C#

- C++/CLI

  Anahtar sözcükler için büyük/küçük harfe duyarsız karşılaştırma kullanılır [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ve diğer diller için büyük/küçük harfe duyarlı karşılaştırma kullanılır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Anahtar sözcük listesinde görünmeyen bir ad seçin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Tanımlayıcının API kullanıcılarını şaşırmadığına ve kitaplığın içindeki kullanılabilir tüm dillerde kullanılabilir olduğunu ikna ediyorsanız, bu kuraldan bir uyarıyı gizleyebilirsiniz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .
