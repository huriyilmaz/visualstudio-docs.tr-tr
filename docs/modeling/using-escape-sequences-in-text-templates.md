---
title: Metin Şablonlarında Çıkış Sıraları Kullanma
description: Metin şablonu etiketleri oluşturmak ve yalnızca C# kodunda kaçış denetimi karakterleri ve tırnak işaretleri oluşturmak için metin şablonlarındaki kaçış dizilerini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: b4ffb5ee7fd21b5d549a90a3c86378f2f00356287d6a54d387559fc2343a22cc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121316622"
---
# <a name="use-escape-sequences-in-text-templates"></a>Metin şablonlarında kaçış dizilerini kullanma

Metin şablonlarındaki kaçış dizilerini kullanarak metin şablonu etiketleri oluşturabilir ve (yalnızca C# kodunda) denetim karakterlerini ve tırnak işaretlerini atabilirsiniz.

Standart bir kod bloğu için açık ve kapalı etiketleri çıktı dosyasına yazdırmak için aşağıdaki gibi etiketlerin kaçışını yapın:

```
\<# ... \#>
```

Aynı şeyi diğer metin şablonu yönergesi ve kod bloğu etiketleriyle de kullanabilirsiniz.

Metin bloğunda metin şablonu etiketlerinden kaçış için kullanılan dizeler varsa aşağıdaki kaçış dizilerini kullanabilirsiniz:

- Bir metin şablonu etiketinin önünde eşit sayıda kaçış ( ) karakteri varsa, şablon ayrıştırıcı kaçış karakterlerinin yarısını içerir ve diziyi metin şablonu \\ etiketi olarak içerir. Örneğin, metin şablonunda dört kaçış karakteri varsa, oluşturulan dosyada \\ iki " " " karakteri olur.

- Metin şablonu etiketinin önünde tek sayıda kaçış karakteri ( ) karakteri varsa, şablon ayrıştırıcısı " " karakterlerinin yarısını ve etiketinin kendisini \\ \\ () \<# or #> içerecektir. Etiket bir metin şablonu etiketi olarak kabullanmaz.

- Bir kaçış ( ) karakteri, bir denetim karakterinden veya tırnak karakterinden (yalnızca C# ile) kaçış karakteri dışında herhangi bir sıranın başka bir yerinde \\ görünürse, karakter doğrudan çıkış olarak görünür.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Çıkış Sıraları Kullanarak Şablonlardan Şablon Oluşturma](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
