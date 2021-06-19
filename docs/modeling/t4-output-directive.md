---
title: T4 Çıkış Yönergesi
description: Visual Studio metin şablonlarında, çıkış yönergesinin, dönüştürülmüş dosyanın dosya adı uzantısını ve kodlamasını tanımlamak için kullanıldığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8105edc57e68aa7cedcb612ec4f6bcd0ef367d2f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386117"
---
# <a name="t4-output-directive"></a>T4 Çıkış Yönergesi

Visual Studio metin şablonlarında, yönerge, `output` dönüştürülmüş dosyanın dosya adı uzantısını ve kodlamasını tanımlamak için kullanılır.

 Örneğin, Visual Studio projeniz aşağıdaki yönergeyi içeren **myTemplate.tt** adlı bir şablon dosyası içeriyorsa:

 `<#@output extension=".cs"#>`

 ardından, Visual Studio **myTemplate. cs** adlı bir dosya oluşturur

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
