---
title: 'CA2124: açık olan finally yan tümcelerini dış TRY içinde sarın | Microsoft Docs'
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
ms.openlocfilehash: 4e191ca10456f133e1213961ca2d1ed9cb8e040b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544306"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Savunmasız sonunda yan tümcelerini dış deneme içine sarmalayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Öğesinin 1,0 ve 1,1 sürümlerinde [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , genel veya korumalı bir yöntem bir `try` / `catch` / `finally` blok içerir. `finally`Blok güvenlik durumunu sıfırlayıp bir blok içine alınmaz `finally` .

## <a name="rule-description"></a>Kural Tanımı
 Bu kural `try` / `finally` , [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] çağrı yığınında mevcut olan kötü amaçlı özel durum filtrelerindekilerle açık olabilecek, 1,0 ve 1,1 sürümlerini hedefleyen koddaki blokları bulur. Kimliğe bürünme gibi hassas işlemler try bloğunda gerçekleşirse ve bir özel durum oluşturulursa, filtre bloğundan önce yürütülür `finally` . Kimliğe bürünme örneği için bu, filtrenin kimliğine bürünülen kullanıcı olarak yürütüleceği anlamına gelir. Filtreler Şu anda yalnızca Visual Basic ' de uygulardır.

> [!WARNING]
> Sürüm 2,0 ve üzeri sürümlerde, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] `try` / `catch` /  `finally` sıfırlama işlemi özel durum bloğunu içeren yöntem içinde doğrudan gerçekleşirse, çalışma zamanı kötü amaçlı özel durum filtrelerinden bir bloğu otomatik olarak korur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Sarmalanmamış `try` / `finally` bir dış try bloğuna yerleştirin. Aşağıdaki ikinci örneğe bakın. Bu, `finally` kodu filtre kodundan önce yürütmeye zorlar.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="pseudo-code-example"></a>Sözde kod örneği

### <a name="description"></a>Description
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
