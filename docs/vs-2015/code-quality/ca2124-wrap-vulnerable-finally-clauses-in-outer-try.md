---
title: "CA2124: Dış TRY 'da savunmasız finally yan tümcelerini sarın | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7a2a296f5dd3680209c14849b5bd863c01e6351d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660241"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Savunmasız sonunda yan tümcelerini dış deneme içine sarmalayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 @No__t_0 1,0 sürümleri ve 1,1 ' de, genel veya korumalı bir yöntem bir `try` / `catch` / `finally` bloğunu içerir. @No__t_0 bloğu güvenlik durumunu sıfırlayıp bir `finally` bloğunun içine alınmaz.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, çağrı yığınında mevcut olan kötü amaçlı özel durum filtrelerine açık olabilecek [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 1,0 ve 1,1 sürümlerini hedefleyen koddaki `try` / `finally` bloklarını bulur. Kimliğe bürünme gibi hassas işlemler try bloğunda gerçekleşirse ve bir özel durum oluşturulursa, filtre `finally` bloğundan önce çalıştırılabilir. Kimliğe bürünme örneği için bu, filtrenin kimliğine bürünülen kullanıcı olarak yürütüleceği anlamına gelir. Filtreler Şu anda yalnızca Visual Basic ' de uygulardır.

> [!WARNING]
> @No__t_0 2,0 sürümleri ve sonrasında, çalışma zamanı, otomatik olarak özel durum bloğunu içeren yöntemin içinde ortaya çıkarsa, bir `try` / `catch` kötü amaçlı özel durum filtrelerinden /  bloğunu otomatik olarak korur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Sarmalanmamış `try` / `finally` bir dış try bloğuna yerleştirin. Aşağıdaki ikinci örneğe bakın. Bu, `finally` ' i filtre kodundan önce yürütmeye zorlar.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="pseudo-code-example"></a>Sözde kod örneği

### <a name="description"></a>Açıklama
 Aşağıdaki sözde kod, bu kural tarafından algılanan kalıbı gösterir.

### <a name="code"></a>Kod

```
try {
   // Do some work.
   Impersonator imp = new Impersonator("John Doe");
   imp.AddToCreditCardBalance(100);
}
finally {
   // Reset security state.
   imp.Revert();
}
```

## <a name="example"></a>Örnek
 Aşağıdaki sözde kod, kodunuzu korumak ve bu kuralı karşılamak için kullanabileceğiniz bir model gösterir.

```
try {
     try {
        // Do some work.
     }
     finally {
        // Reset security state.
     }
}
catch()
{
    throw;
}
```
