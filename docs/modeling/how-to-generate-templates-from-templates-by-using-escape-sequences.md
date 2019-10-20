---
title: Şablonlardan şablon oluşturmak için kaçış dizilerini kullanma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a9afe2670bb086627407a9f1bc674edfc2fe354
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72605465"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Nasıl yapılır: Çıkış Sıraları Kullanarak Şablonlardan Şablon Oluşturma
Oluşturulan metin çıktısı olarak başka bir metin şablonu oluşturan bir metin şablonu oluşturabilirsiniz. Bunu yapmak için, metin şablonu etiketlerini belirtmek için kaçış dizilerini kullanmanız gerekir. Kaçış dizilerini kullanmıyorsanız, oluşturduğunuz metin şablonunuz önceden tanımlı bir anlamı olacaktır. Metin şablonlarında kaçış dizilerini kullanma hakkında daha fazla bilgi için bkz. [Metin şablonlarında kaçış dizilerini kullanma](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Metin şablonu içinden metin şablonu oluşturmak için

- Farklı metin şablonu dosyasındaki yönergeler, deyimler, ifadeler ve sınıf özellikleri için metin şablonunda gerekli biçimlendirme etiketlerini oluşturmak için bir kaçış karakteri olarak ters eğik çizgi (\\) kullanın.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir metin şablonundan metin şablonu oluşturmak için kaçış karakterleri kullanır. @No__t_0 yönergesi, hedef dosya türünü metin şablonu dosya türüne (. tt) ayarlar.

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