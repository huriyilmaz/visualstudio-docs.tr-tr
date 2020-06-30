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
ms.openlocfilehash: afadf41fc753051047e858758bfe0677987d726d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545073"
---
# <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Zayıf Şifreleme Algoritmaları Kullanmayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|Donotuseweakcryptographicalgoritma|
|CheckId|CA5350|
|Kategori|Microsoft. Cryptography|
|Yeni Değişiklik|Kırılmamış|

> [!NOTE]
> Bu uyarı en son 2015 Kasım tarihinde güncelleştirildi.

## <a name="cause"></a>Nedeni
 Ve gibi şifreleme algoritmaları ve gibi <xref:System.Security.Cryptography.TripleDES> karma algoritmalar <xref:System.Security.Cryptography.SHA1> <xref:System.Security.Cryptography.RIPEMD160> zayıf kabul edilir.

 Bu şifreleme algoritmaları, daha modern karşılıklarıyla çok güvenlik güvencesi sağlamaz. <xref:System.Security.Cryptography.SHA1> <xref:System.Security.Cryptography.RIPEMD160> Daha modern karma algoritmalardan daha az çakışma sağlayan şifreleme algoritmaları. Şifreleme algoritması, <xref:System.Security.Cryptography.TripleDES> daha fazla modern şifreleme algoritmalarından daha az sayıda güvenlik sağlar.

## <a name="rule-description"></a>Kural Tanımı
 Zayıf şifreleme algoritmaları ve karma işlevleri bugün çok sayıda nedenden dolayı kullanılır, ancak korudukları verilerin gizliliğini garanti etmek için kullanılmamalıdır.

 Kural, koddaki 3DES, SHA1 veya RIPEMD160 algoritmaları bulduğunda tetiklenir ve kullanıcıya bir uyarı oluşturur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Şifreleme daha güçlü seçenekleri kullanın:

- TripleDES şifrelemesi için şifreleme kullanın <xref:System.Security.Cryptography.Aes> .

- SHA1 veya RIPEMD160 karma işlevleri için [SHA-2](https://msdn.microsoft.com/library/windows/desktop/aa382459.aspx) ailesinden (ör. <xref:System.Security.Cryptography.SHA512> , <xref:System.Security.Cryptography.SHA384> ,) olanları kullanın <xref:System.Security.Cryptography.SHA256> .

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