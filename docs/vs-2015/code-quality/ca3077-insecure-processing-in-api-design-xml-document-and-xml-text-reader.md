---
title: 'CA3077: API tasarımında güvenli olmayan Işlem, XML belgesi ve XML metin okuyucu | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c0d6a6f6ab42d69d4503741f6625627c46d4ef77
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545112"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: API Tasarımı, XML Belgesi ve XML Metin Okuyucusunda Güvensiz İşleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|Insecuredtdprocessingınapidesign|
|CheckId|CA3077|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 XMLDocument ve XMLTextReader 'dan türetilmiş bir API tasarlarken, en az bir olmalıdır <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> .  Dış varlık kaynaklarının başvurulması veya çözümlenmesi veya XML 'deki güvenli olmayan değerlerin ayarlanması sırasında güvenli olmayan DTDProcessing örnekleri kullanmak bilgilerin açığa çıkmasına neden olabilir.

## <a name="rule-description"></a>Kural Tanımı
 Bir [belge türü tanımı (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) , bir XML ayrıştırıcısının, [World Wide Web Konsorsiyumu (W3C) Genişletilebilir Biçimlendirme Dili (XML) 1,0](https://www.w3.org/TR/2008/REC-xml-20081126/)tarafından tanımlanan bir belgenin geçerliliğini belirleyebilmesi için iki yönden biridir. Bu kural, geliştiricilerin [hizmet reddi (DOS)](https://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) saldırılarına yol açabilecek olası [bilgi açığa çıkması](https://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) tehditleri hakkında geliştiricilere uyarı vermek için güvenilmeyen verilerin kabul edildiği özellikleri ve örnekleri arar. Bu kural şu durumlarda tetiklenir:

- <xref:System.Xml.XmlDocument>veya <xref:System.Xml.XmlTextReader> SıNıFLARı DTD işleme için varsayılan çözümleyici değerlerini kullanır.

- XmlDocument veya XmlTextReader türetilmiş sınıflar için bir Oluşturucu tanımlanmamıştır veya için hiçbir güvenli değer kullanılmaz <xref:System.Xml.XmlResolver> .

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?

- Yol bilgilerinin açığa çıkmasını önlemek için tüm XmlTextReader özel durumlarını doğru bir şekilde yakalayın ve işleyin.

-  <xref:System.Xml.XmlSecureResolver>XmlTextReader 'ın erişebileceği kaynakları kısıtlamak Için XmlResolver yerine kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Girişin güvenilen bir kaynaktan geldiğinden emin olmadığınız için, bu uyarıdan bir kuralı engellemez.

## <a name="pseudo-code-examples"></a>Sözde kod örnekleri

### <a name="violation"></a>Edildiği

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass () {} // warn
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2() // warn
        {
        }
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass ()
        {
            XmlResolver = null;
        }
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2()
        {
               XmlResolver = null;
        }
    }
}
```
