---
title: T4 Çıkış Yönergesi
description: Metin şablonlarında Visual Studio yönergenin, dönüştürülen dosyanın dosya adı uzantısını ve kodlamasını tanımlamak için olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: b5b8bae97dbed7afbcae7611bd9787979b8ab882
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637382"
---
# <a name="t4-output-directive"></a>T4 Çıkış Yönergesi

Metin Visual Studio dosyasında, dönüştürülen dosyanın dosya adı uzantısını ve kodlamasını `output` tanımlamak için yönergesi kullanılır.

 Örneğin, Visual Studio projeniz aşağıdaki yönergeyi içeren **MyTemplate.tt** adlı bir şablon dosyası içeriyorsa:

 `<#@output extension=".cs"#>`

 ardından Visual Studio **MyTemplate.cs adlı bir dosya oluşturacak**

 yönergesi `output` bir çalışma zamanı (önceden işlenmiştir) metin şablonunda gerekli değildir. Bunun yerine, uygulamanız çağrılarak oluşturulan dizeyi `TextTransform()` alır. Daha fazla bilgi için [bkz. T4 Metin Şablonları ile Çalışma Zamanı Metin Oluşturma.](../modeling/run-time-text-generation-with-t4-text-templates.md)

## <a name="using-the-output-directive"></a>Çıkış Yönergesi Kullanma

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 Her metin şablonunda birden `output` fazla yönerge olması gerekir.

## <a name="extension-attribute"></a>extension özniteliği
 Oluşturulan metin çıktı dosyasının dosya adı uzantısını belirtir.

 Varsayılan değer **.cs'dir**

 Örnekler: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Kabul Edilebilir Değerler: Herhangi bir geçerli dosya adı uzantısı.

## <a name="encoding-attribute"></a>encoding özniteliği
 Çıkış dosyası oluşturulurken kullanılacak kodlamayı belirtir. Örnek:

 `<#@ output encoding="utf-8"#>`

 Varsayılan değer, metin şablonu dosyası tarafından kullanılan kodlamadır.

 Kabul Edilebilir Değerler: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (Sistem varsayılanı)

 Genel olarak, tarafından döndürülen herhangi bir kodlamanın WebName dizesini veya CodePage numarasını <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> kullanabilirsiniz.
