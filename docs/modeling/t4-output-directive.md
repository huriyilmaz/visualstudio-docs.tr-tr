---
title: T4 Çıkış Yönergesi
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb1634da6374ad49f1386be4403e72e8edeff2ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591820"
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
