---
title: Şifreleme Uyarıları
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2414a12c00b7d496e09f01982783a90874721cdc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649687"
---
# <a name="cryptography-warnings"></a>Şifreleme Uyarıları
Şifreleme uyarıları, doğru şifreleme kullanımıyla daha güvenli kitaplıkları ve uygulamaları destekler. Bu uyarılar, programınızdaki güvenlik açıklarını önlemeye yardımcı olur. Bu uyarılardan birini devre dışı bırakırsanız, bunun sebebini kodunuzda açıkça işaretlemelisiniz ve ayrıca geliştirme projeniz için güvenlik çalışanını bilgilendirmelisiniz.

|Kural|Açıklama|
|----------|-----------------|
|[CA5350: Zayıf Şifreleme Algoritmaları Kullanmayın](../code-quality/ca5350.md)|Zayıf şifreleme algoritmaları ve karma işlevleri bugün çok sayıda nedenden dolayı kullanılır, ancak korudukları verilerin gizliliğini veya bütünlüğünü sağlamak için kullanılmamalıdır.        Bu kural, koddaki TripleDES, SHA1 veya RIPEMD160 algoritmaları bulduğunda tetikler.|
|[CA5351: Bozuk Şifreleme Algoritmaları Kullanmayın](../code-quality/ca5351.md)|Bozuk şifreleme algoritmaları güvenli olarak kabul edilmez ve kullanımları kesinlikle önerilmez. Bu kural, MD5 karma algoritmasını veya koddaki DES veya RC2 şifreleme algoritmalarından birini bulduğunda tetikler.|
