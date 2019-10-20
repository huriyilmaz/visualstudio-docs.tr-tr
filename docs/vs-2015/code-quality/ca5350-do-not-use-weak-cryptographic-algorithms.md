---
title: 'CA5350: zayıf şifreleme algoritmaları kullanmayın | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9c2c996c383c8834e44e16f382c14b695c83f26
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668991"
---
# <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Zayıf Şifreleme Algoritmaları Kullanmayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|Donotuseweakcryptographicalgoritma|
|CheckId|CA5350|
|Kategori|Microsoft. Cryptography|
|Yeni Değişiklik|Kırılmamış|

> [!NOTE]
> Bu uyarı en son 2015 Kasım tarihinde güncelleştirildi.

## <a name="cause"></a>Sebep
 @No__t_0 ve <xref:System.Security.Cryptography.SHA1> ve <xref:System.Security.Cryptography.RIPEMD160> gibi karma algoritmalar gibi şifreleme algoritmalarının zayıf olduğu kabul edilir.

 Bu şifreleme algoritmaları, daha modern karşılıklarıyla çok güvenlik güvencesi sağlamaz. @No__t_0 ve <xref:System.Security.Cryptography.RIPEMD160> şifreleme karma algoritmaları, daha modern karma algoritmalardan daha az çakışma sağlar. Şifreleme algoritması <xref:System.Security.Cryptography.TripleDES> daha fazla modern şifreleme algoritmalarından daha az sayıda güvenlik sağlar.

## <a name="rule-description"></a>Kural Tanımı
 Zayıf şifreleme algoritmaları ve karma işlevleri bugün çok sayıda nedenden dolayı kullanılır, ancak korudukları verilerin gizliliğini garanti etmek için kullanılmamalıdır.

 Kural, koddaki 3DES, SHA1 veya RIPEMD160 algoritmaları bulduğunda tetiklenir ve kullanıcıya bir uyarı oluşturur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Şifreleme daha güçlü seçenekleri kullanın:

- Üç aylık şifreleme için <xref:System.Security.Cryptography.Aes> şifrelemesi kullanın.

- SHA1 veya RIPEMD160 karma işlevleri için [SHA-2](https://msdn.microsoft.com/library/windows/desktop/aa382459.aspx) ailesinden (ör. <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>) olanları kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Veriler için gereken koruma düzeyi bir güvenlik garantisi gerektirmiyorsa bu kuraldan bir uyarı gizleyin.

## <a name="pseudo-code-example"></a>Sözde kod örneği
 Bu yazma sırasında, aşağıdaki sözde kod örneği, bu kural tarafından algılanan kalıbı gösterir.

### <a name="sha-1-hashing-violation"></a>SHA-1 karma Ihlali

```
using System.Security.Cryptography;
...
var hashAlg = SHA1.Create();

```

### <a name="solution"></a>Çözüm

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="ripemd160-br-br-hashing-violation"></a>RIPEMD160 <br /><br />Karma Ihlali

```
using System.Security.Cryptography;
...
var hashAlg = RIPEMD160Managed.Create();

```

### <a name="solution"></a>Çözüm

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="tripledes-encryption-violation"></a>TripleDES şifreleme Ihlali

```
using System.Security.Cryptography;
...
using (TripleDES encAlg = TripleDES.Create())
{
  ...
}
```

### <a name="solution"></a>Çözüm

```
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```