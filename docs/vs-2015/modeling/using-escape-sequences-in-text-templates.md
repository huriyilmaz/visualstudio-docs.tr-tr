---
title: Metin şablonlarında kaçış dizilerini kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a45aa36ddce57141a7e1e851f7f0766b77015ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659430"
---
# <a name="using-escape-sequences-in-text-templates"></a>Metin Şablonlarında Çıkış Sıraları Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: Çıkış Sıraları Kullanarak Şablonlardan Şablon Oluşturma](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
