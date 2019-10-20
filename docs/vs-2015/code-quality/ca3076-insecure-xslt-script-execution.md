---
title: 'CA3076: güvensiz XSLT betiği yürütme | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 558e205fa37569bfa12d7b93f989d0f8ebabab43
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669056"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Güvensiz XSLT Betiği Yürütme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|Insecurexsltscriptexecution|
|CheckId|CA3076|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 .NET uygulamalarında [Genişletilebilir Stil sayfaları Dil Dönüşümleri (XSLT)](https://support.microsoft.com/kb/313997) çalıştırıyorsanız, işlemci [güvenilir olmayan URI başvurularını](https://msdn.microsoft.com/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) , saldırganlar için duyarlı bilgileri açığa çıkartabilir ve bunların reddedilmesine karşı önde bir şekilde çözümleyebilir Hizmet ve çapraz site saldırıları.

## <a name="rule-description"></a>Kural Tanımı
 [XSLT](https://msdn.microsoft.com/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) , XML verilerini dönüştürmek için bir World WIDE Web KONSORSIYUMU (W3C) standardıdır. XSLT genellikle, XML verilerini HTML, sabit uzunlukta metin, virgülle ayrılmış metin veya farklı bir XML biçimi gibi diğer biçimlere dönüştürmek üzere stil sayfaları yazmak için kullanılır. Varsayılan olarak yasaklanmış olmasına karşın, bunu projeniz için etkinleştirmeyi tercih edebilirsiniz.

 Bir saldırı yüzeyi açığa çıkarmadığından emin olmak için, bu kural XslCompiledTransform her seferinde tetiklenir. <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> kötü amaçlı betik işlemeye izin veren <xref:System.Xml.Xsl.XsltSettings> ve <xref:System.Xml.XmlResolver> ' in güvensiz birleşim örneklerini alır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?

- Güvenli olmayan XsltSettings bağımsız değişkenini XsltSettings ile değiştirin. <xref:System.Xml.Xsl.XsltSettings.Default%2A> ya da belge işlev ve betik yürütmeyi devre dışı bırakmış bir örnekle.

- @No__t_0 bağımsız değişkenini null ya da bir <xref:System.Xml.XmlSecureResolver> örneğiyle değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Girişin güvenilen bir kaynaktan geldiğinden emin olmadığınız için, bu uyarıdan bir kuralı engellemez.

## <a name="pseudo-code-examples"></a>Sözde kod örnekleri

### <a name="violation"></a>Edildiği

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
         void TestMethod()
        {
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
             var settings = XsltSettings.TrustedXslt;
             var resolver = new XmlUrlResolver();
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
        }
    }
} 
```

### <a name="solution"></a>Çözüm

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        void TestMethod()
        {
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
            var settings = XsltSettings.Default;
            var resolver = new XmlUrlResolver();
            xslCompiledTransform.Load("testStylesheet", settings, resolver);
        }
    }
}
```

### <a name="violation"></a>Edildiği

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
            }
            catch { throw; }
            finally { }
        }
    }
}
```

### <a name="solution"></a>Çözüm

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                settings.EnableDocumentFunction = false;
                settings.EnableScript = false;
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver);
            }
            catch { throw; }
            finally { }
        }
    }
}
```
