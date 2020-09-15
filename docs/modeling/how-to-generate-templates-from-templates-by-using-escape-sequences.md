---
title: Metin şablonundan metin şablonu oluşturma
description: Kaçış dizileri kullanarak başka bir metin şablonundan metin şablonu oluşturma hakkında bilgi sağlar.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: d7ef983525842023247433e7a3c2b51e206a1cee
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90100767"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Nasıl yapılır: Çıkış Sıraları Kullanarak Şablonlardan Şablon Oluşturma
Oluşturulan metin çıktısı olarak başka bir metin şablonu oluşturan bir metin şablonu oluşturabilirsiniz. Bunu yapmak için, metin şablonu etiketlerini belirtmek için kaçış dizilerini kullanmanız gerekir. Kaçış dizilerini kullanmıyorsanız, oluşturduğunuz metin şablonunuz önceden tanımlı bir anlamı olacaktır. Metin şablonlarında kaçış dizilerini kullanma hakkında daha fazla bilgi için bkz. [Metin şablonlarında kaçış dizilerini kullanma](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Metin şablonu içinden metin şablonu oluşturmak için

- \\Farklı bir metin şablonu dosyasındaki yönergeler, deyimler, ifadeler ve sınıf özellikleri için metin şablonu içinde gerekli biçimlendirme etiketlerini oluşturmak için bir kaçış karakteri olarak ters eğik çizgi () kullanın.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir metin şablonundan metin şablonu oluşturmak için kaçış karakterleri kullanır. `output`Yönergesi, hedef dosya türünü metin şablonu dosya türüne (. tt) ayarlar.

```csharp
\<#@ output extension=".tt" \#>
\<#@ assembly name="System.Xml.dll" \#>
\<#@ import namespace="System.Xml" \#>
\<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {\#>
           \<#= attr.Name \#>
       \<#}
     }
\#>
```

 Oluşturulan metin çıktısı bir metin şablonudur.

```
<#@ output extension=".tt" #>
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {#>
           <#= attr.Name #>
       <#}
     }
#>
```
