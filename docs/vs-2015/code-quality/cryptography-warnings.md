---
title: Şifreleme uyarıları | Microsoft Docs
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d9f5694ccf48615ebdf7157adc80543b0fbb71eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667668"
---
# <a name="cryptography-warnings"></a>Şifreleme Uyarıları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Şifreleme uyarıları, doğru şifreleme kullanımıyla daha güvenli kitaplıkları ve uygulamaları destekler. Bu uyarılar, programınızdaki güvenlik açıklarını önlemeye yardımcı olur. Bu uyarılardan birini devre dışı bırakırsanız, bunun sebebini kodunuzda açıkça işaretlemelisiniz ve ayrıca geliştirme projeniz için güvenlik çalışanını bilgilendirmelisiniz.

|Kural|Açıklama|
|----------|-----------------|
|[CA5350: Zayıf Şifreleme Algoritmaları Kullanmayın](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Zayıf şifreleme algoritmaları ve karma işlevleri bugün çok sayıda nedenden dolayı kullanılır, ancak korudukları verilerin gizliliğini veya bütünlüğünü sağlamak için kullanılmamalıdır.        Bu kural, koddaki TripleDES, SHA1 veya RIPEMD160 algoritmaları bulduğunda tetikler.|
|[CA5351: Bozuk Şifreleme Algoritmaları Kullanmayın](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Bozuk şifreleme algoritmaları güvenli olarak kabul edilmez ve kullanımları kesinlikle önerilmez. Bu kural, MD5 karma algoritmasını veya koddaki DES veya RC2 şifreleme algoritmalarından birini bulduğunda tetikler.|
