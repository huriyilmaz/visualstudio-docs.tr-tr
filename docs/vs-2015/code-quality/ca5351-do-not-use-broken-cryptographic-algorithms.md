---
title: CA5351 kopuk şifreleme algoritmaları kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7b4a15530a43937b4f73fba1779216391c862c11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669025"
---
# <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: Bozuk Şifreleme Algoritmaları Kullanmayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|Donotusebrokencryptographicalgoritmaları|
|CheckId|CA5351|
|Kategori|Microsoft. Cryptography|
|Yeni Değişiklik|Kırılmamış|

> [!NOTE]
> Bu uyarı en son 2015 Kasım tarihinde güncelleştirildi.

## <a name="cause"></a>Sebep
 @No__t_0 ve <xref:System.Security.Cryptography.DES> ve <xref:System.Security.Cryptography.RC2> gibi şifreleme algoritmaları gibi karma işlevler önemli bir riski ortaya çıkarır ve bu durum, deneme yanılma saldırıları ve karma çarpışmaları gibi önemsiz saldırı teknikleriyle hassas bilgilerin açığa çıkmasına neden olabilir.

 Aşağıdaki şifreleme algoritmaları listesi, bilinen şifreleme saldırılarına tabidir. Şifreleme karma algoritması <xref:System.Security.Cryptography.MD5> karma çakışma saldırılarına tabidir.  Bir karma çarpışması, kullanıma bağlı olarak, karma işlevinin benzersiz şifreleme çıktısına bağlı olan sistemlerde kimliğe bürünme, izinsiz değişiklik veya diğer saldırı türlerine yol açabilir. @No__t_0 ve <xref:System.Security.Cryptography.RC2> şifreleme algoritmaları şifrelenmiş verilerin istenmeden açıklanmasına neden olabilecek şifreleme saldırılarına tabidir.

## <a name="rule-description"></a>Kural Tanımı
 Bozuk şifreleme algoritmaları güvenli olarak kabul edilmez ve kullanımları önerilmez. MD5 karma algoritması bilinen çakışma saldırılarına açıktır, ancak belirli güvenlik açığı kullanım bağlamına göre farklılık gösterir.  Veri bütünlüğünü sağlamak için kullanılan karma algoritmalar (ör. dosya imzası veya dijital sertifika) özellikle savunmasız.  Bu bağlamda, saldırganlar iki ayrı veri parça oluşturabilir. bu şekilde, kötü amaçlı veriler, karma değer değiştirilmeksizin veya ilişkili dijital imzayı geçersiz kılarak kötü amaçlı verilerle değiştirilebilir.

 Şifreleme algoritmaları için:

- <xref:System.Security.Cryptography.DES> şifrelemesi, bir günden kısa bir sürede deneme yanılma olabilecek küçük bir anahtar boyutu içerir.

- <xref:System.Security.Cryptography.RC2> şifrelemesi, saldırganın tüm anahtar değerleri arasında matematik ilişkileri bulduğu ilgili anahtar saldırılarına açıktır.

  Bu kural, kaynak kodundaki yukarıdaki şifreleme işlevlerinden herhangi birini bulduğunda tetiklenir ve kullanıcıya bir uyarı oluşturur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Şifreleme daha güçlü seçenekleri kullanın:

- MD5 için [SHA-2](https://msdn.microsoft.com/library/windows/desktop/aa382459.aspx) ailesindeki karmaları kullanın (ör.  <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).

- DES ve RC2 için <xref:System.Security.Cryptography.Aes> şifrelemesi kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bir şifreleme uzmanı tarafından incelenmediği takdirde bu kuraldan bir uyarıyı bastırmayın.

## <a name="pseudo-code-example"></a>Sözde kod örneği
 Aşağıdaki sözde kod örneği, bu kural tarafından algılanan ve olası alternatifler gösterir.

### <a name="md5-hashing-violation"></a>MD5 karma Ihlali

```
using System.Security.Cryptography;
...
var hashAlg = MD5.Create();

```

### <a name="solution"></a>Çözüm

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="rc2-encryption-violation"></a>RC2 şifreleme Ihlali

```
using System.Security.Cryptography;
...
RC2 encAlg = RC2.Create();

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

### <a name="des-br-br-encryption-violation"></a>MADDESINI <br /><br />Şifreleme Ihlali

```
using System.Security.Cryptography;
...
DES encAlg = DES.Create();

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