---
title: Metin Şablonlarında Çıkış Sıraları Kullanma
description: Metin şablonu etiketleri oluşturmak ve yalnızca C# kodundaki denetim karakterlerini ve tırnak işaretlerini atlamak için metin şablonlarında kaçış dizilerini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2a3cdabd38f2bf4ef38a31807fabed3ac837b26b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388457"
---
# <a name="use-escape-sequences-in-text-templates"></a>Metin şablonlarında kaçış dizilerini kullanma

Metin şablonu etiketleri ve (yalnızca C# kodunda) denetim karakterlerini ve tırnak işaretlerini atlamak için metin şablonlarındaki kaçış dizilerini kullanabilirsiniz.

Çıkış dosyasına standart bir kod bloğunun açık ve kapalı etiketlerini yazdırmak için etiketleri aşağıdaki gibi kaçış:

```
\<# ... \#>
```

Diğer metin şablonu yönergesi ve kod bloğu etiketleriyle aynı şekilde yapabilirsiniz.

Metin bloğu metin şablonu etiketlerini kaçış için kullanılan dizeleri içeriyorsa, aşağıdaki kaçış dizilerini kullanabilirsiniz:

- Bir metin şablonu etiketinin önünde bir dizi kaçış ( \\ ) karakteri varsa şablon ayrıştırıcısı kaçış karakterlerinin yarısını içerir ve sırası metin şablonu etiketi olarak ekler. Örneğin, metin şablonunda dört kaçış karakteri varsa, \\ oluşturulan dosyada iki "" karakteri olacaktır.

- Metin şablonu etiketinin öncesinde tek sayıda kaçış ( \\ ) karakteri varsa, şablon ayrıştırıcısı " \\ " karakterlerinin yarısını ve etiketinin kendisini ( \<# or #> ) içerir. Etiket, bir metin şablonu etiketi olarak kabul edilmez.

- Bir kaçış ( \\ ) karakteri, bir denetim karakteri veya tırnak işareti (yalnızca C# ' ta) dışında herhangi bir dizide başka bir yerde görünürse, karakter doğrudan çıktı olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Çıkış Sıraları Kullanarak Şablonlardan Şablon Oluşturma](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
