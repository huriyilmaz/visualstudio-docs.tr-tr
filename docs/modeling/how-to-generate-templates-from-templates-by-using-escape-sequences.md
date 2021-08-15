---
title: Metin şablonundan metin şablonu oluşturma
description: Kaçış dizilerini kullanarak başka bir metin şablonundan metin şablonu oluşturma hakkında bilgi sağlar.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: c0dbad0b68e0245073124254940f17e1cdb5147b0550846871fe40db546eb091
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121288639"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Nasıl yapılır: Çıkış Sıraları Kullanarak Şablonlardan Şablon Oluşturma
Oluşturulan metin çıkışı olarak başka bir metin şablonu oluşturan bir metin şablonu oluşturabilirsiniz. Bunu yapmak için kaçış dizilerini kullanarak metin şablonu etiketlerini çizin. Kaçış dizileri kullanmayacaksanız, oluşturulan metin şablonunuz önceden tanımlanmış bir anlama sahip olur. Metin şablonlarında kaçış dizilerini kullanma hakkında daha fazla bilgi için [bkz. Metin Şablonlarında Kaçış Dizilerini Kullanma.](../modeling/using-escape-sequences-in-text-templates.md)

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Metin şablonunun içinde bir metin şablonu oluşturmak için

- Yönergeler, deyimler, ifadeler ve sınıf özellikleri için metin şablonu içinde ayrı bir metin şablonu dosyasında gerekli işaretleme etiketlerini üretmek için kaçış karakteri olarak ters eğik çizgi ( \\ ) kullanın.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir metin şablonundan metin şablonu oluşturmak için kaçış karakterlerini kullanır. `output`yönergesi, hedef dosya türünü metin şablonu dosya türüne (.tt) ayarlar.

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

 Oluşturulan metin çıkışı bir metin şablonudur.

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
