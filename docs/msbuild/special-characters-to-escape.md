---
title: Kaçış Karakteri için Özel Karakterler | Microsoft Docs
description: Yalnızca kullanıldıkları bağlamda özel anlamları varsa, kaçacakları özel karakterler hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: d51afda7866fbf38642b47a99b970a6407ac4d19
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100588"
---
# <a name="special-characters-to-escape"></a>Kaçış için özel karakterler

Özel karakterler yalnızca kullanıldıkları bağlamda özel anlamlara sahipse kaçmalıdır. Örneğin, yıldız işareti (*) yalnızca bir öğe tanımının "Dahil" ve "Dışla" özniteliklerinde veya çağrısında özel bir <xref:Microsoft.Build.Tasks.CreateItem> karakterdir. Diğer tüm durumlarda, yıldız işareti değişmez yıldız olarak kabul edilir. Proje dosyalarında her yerde yıldız işareti kaçışı yapmak zorunda değil, ancak bunu yapmak bir zarar vermez.

 ASCII karakterinin onaltılık değerini temsil eden özel karakter yerine % \<xx> \<xx> değerini kullanın. Örneğin, değişmez karakter olarak yıldız (*) kullanmak için değerini `%2A` kullanın.

 Kaçış karakteri olarak özel karakterlerin tam listesi şu şekildedir:

|Karakter|ASCII kodlaması|Açıklama|
|---------|----------|-----------|
|%|%25|Meta verilere başvuru yapmak için kullanılan yüzde işareti.|
|$|%24|Özelliklere başvuru yapmak için kullanılan dolar işareti.|
|@|%40|İşarette, öğe listelerine başvuru yapmak için kullanılır.|
|(|%28|Listelerde kullanılan parantezi açın.|
|)|%29|Listelerde kullanılan parantezleri kapatın.|
|;|%3B|Noktalı virgül, liste ayırıcısı.|
|?|%3F|Soru işareti, bir öğenin Dahil Etme/Dışlama bölümünde dosya özellikleri açıklanmışken joker karakterdir.|
|* |%2A|Yıldız işareti, bir öğenin Dahil Etme/Dışlama bölümünde dosya özellikleri açıklanmışken joker karakterdir.|

> [!NOTE]
> Bazı senaryolarda, bir görev içinde kullanma gibi çift tırnak (") karakterlerinden kaçış karakterine ihtiyacınız `Exec` olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıllı: Özel karakterlerin kaçış karakteri MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
