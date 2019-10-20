---
title: T4 Çıkış Yönergesi
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1da8ec010e878ff80a9f46748993705b87193d99
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606223"
---
# <a name="t4-output-directive"></a>T4 Çıkış Yönergesi

Visual Studio metin şablonlarında `output` yönergesi, dönüştürülmüş dosyanın dosya adı uzantısını ve kodlamasını tanımlamak için kullanılır.

 Örneğin, Visual Studio projeniz aşağıdaki yönergeyi içeren **myTemplate.tt** adlı bir şablon dosyası içeriyorsa:

 `<#@output extension=".cs"#>`

 ardından, Visual Studio **myTemplate.cs** adlı bir dosya oluşturur

 @No__t_0 yönergesi, çalışma zamanı (önceden işlenmiş) metin şablonunda gerekli değildir. Bunun yerine, uygulamanız `TextTransform()` çağırarak oluşturulan dizeyi edinir. Daha fazla bilgi için bkz. [T4 metin şablonlarıyla çalışma zamanı metin üretimi](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Output yönergesini kullanma

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 Her metin şablonunda birden fazla `output` yönergesi olmamalıdır.

## <a name="extension-attribute"></a>uzantı özniteliği
 Oluşturulan metin çıkış dosyasının dosya adı uzantısını belirtir.

 Varsayılan değer **. cs** 'dir

 Örnekler: `<#@ output extension=".txt" #>`

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

 `0` (sistem varsayılanı)

 Genel olarak, WebName dizesini veya <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> tarafından döndürülen kodlamalara ait kod sayfası numarasını kullanabilirsiniz.