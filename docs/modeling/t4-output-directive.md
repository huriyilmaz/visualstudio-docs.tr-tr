---
title: T4 Çıkış Yönergesi
description: Visual Studio metin şablonlarında, çıkış yönergesinin, dönüştürülmüş dosyanın dosya adı uzantısını ve kodlamasını tanımlamak için kullanıldığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9849a326549aa534d9cd558337b825b7e0b8d1f
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363646"
---
# <a name="t4-output-directive"></a>T4 Çıkış Yönergesi

Visual Studio metin şablonlarında, yönerge, `output` dönüştürülmüş dosyanın dosya adı uzantısını ve kodlamasını tanımlamak için kullanılır.

 Örneğin, Visual Studio projeniz aşağıdaki yönergeyi içeren **myTemplate.tt** adlı bir şablon dosyası içeriyorsa:

 `<#@output extension=".cs"#>`

 ardından, Visual Studio **myTemplate.cs** adlı bir dosya oluşturur

 `output`Yönerge, çalışma zamanı (önceden işlenmiş) metin şablonunda gerekli değildir. Bunun yerine, uygulamanız oluşturulan dizeyi çağırarak edinir `TextTransform()` . Daha fazla bilgi için bkz. [T4 metin şablonlarıyla çalışma zamanı metin üretimi](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Output yönergesini kullanma

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 `output`Her metin şablonunda birden fazla yönerge olmamalıdır.

## <a name="extension-attribute"></a>uzantı özniteliği
 Oluşturulan metin çıkış dosyasının dosya adı uzantısını belirtir.

 Varsayılan değer **. cs** 'dir

 Örnekler `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Kabul edilebilir değerler: herhangi bir geçerli dosya adı uzantısı.

## <a name="encoding-attribute"></a>Encoding özniteliği
 Çıkış dosyası oluşturulduğunda kullanılacak kodlamayı belirtir. Örneğin:

 `<#@ output encoding="utf-8"#>`

 Varsayılan değer, metin şablonu dosyası tarafından kullanılan kodlamadır.

 Kabul edilebilir değerler: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (Sistem varsayılanı)

 Genel olarak, WebName dizesini veya tarafından döndürülen kodlamalara ait kod sayfasının numarasını kullanabilirsiniz <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> .
