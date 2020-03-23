---
title: Kaçmak için Özel Karakterler | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1b17ded468e262d4f636ed5494081adab7b8c5f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632257"
---
# <a name="special-characters-to-escape"></a>Kaçmak için özel karakterler

Özel karakterler, yalnızca kullanıldıkları bağlamda özel bir anlamları varsa kaçılmalıdır. Örneğin, yıldız işareti (*) yalnızca madde tanımının "Ekle" ve "Hariç Tutma" özniteliklerinde veya <xref:Microsoft.Build.Tasks.CreateItem>. Diğer tüm durumlarda, yıldız gerçek bir yıldız olarak kabul edilir. Proje dosyalarında her yerde yıldız yıldızlardan kaçmanız gerekmezken, bunu yapmanın bir zararı yoktur.

 Xx>'nin\<ASCII karakterinin hexadecimal değerini temsil ettiği \<özel karakter yerine % xx> gösterimini kullanın. Örneğin, bir yıldız işareti (*) gerçek bir karakter olarak `%2A`kullanmak için, değeri kullanın.

 Kaçmak için özel karakterlerin tam listesi aşağıdaki gibidir:

|Karakter|Açıklama|
|---------------|-----------------|
|%|Meta verilere başvurmak için kullanılan yüzde işareti.|
|$|Dolar işareti, referans özellikleri için kullanılır.|
|@|İşarette, madde listelerine başvurmak için kullanılır.|
|(|Açık parantez, listelerde kullanılır.|
|)|Listelerde kullanılan yakın parantez.|
|;|Semicolon, bir liste ayırıcı.|
|?|Soru işareti, bir öğenin Ekle/Hariç albölümünde bir dosya spec açıklarken bir joker karakter.|
|*|Bir öğenin Ekle/Hariç Tut bölümünde bir dosya spec açıklarken bir joker karakter yıldız.|

> [!NOTE]
> Bazı senaryolarda, görev `Exec` içinde kullanırken olduğu gibi çift tırnak (") karakterlerden kaçmanız gerekebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl: MSBuild özel karakterler kaçış](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
