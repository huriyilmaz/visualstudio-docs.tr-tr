---
title: Kaçış için özel karakterler | Microsoft Docs
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
ms.openlocfilehash: 9c3a0feed4177bd41ee2b77edc49336bfda3171b
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184048"
---
# <a name="special-characters-to-escape"></a>Kaçış için özel karakterler

Özel karakterler yalnızca kullanıldıkları bağlamda özel anlam içeriyorsa kaçışmalıdır. Örneğin, yıldız işareti (*) yalnızca bir öğe tanımının "Içerme" ve "hariç tutma" özniteliklerinde ya da öğesine yapılan çağrıda özel bir karakterdir <xref:Microsoft.Build.Tasks.CreateItem> . Diğer tüm durumlarda, yıldız işareti sabit bir yıldız işareti olarak değerlendirilir. Proje dosyalarında herhangi bir yerde yıldız işaretleri gerekmez, ancak bunu yapmak zarar vermez.

 \<xx>Özel karakter yerine% gösterimini kullanın; burada \<xx> ASCII karakterinin onaltılı değeri temsil eder. Örneğin, bir yıldız işareti (*) sabit karakter olarak kullanmak için değerini kullanın `%2A` .

 Kaçış için özel karakterlerin tam listesi aşağıdadır:

|Karakter|ASCII kodlama|Açıklama|
|---------|----------|-----------|
|%|%25|Meta verilere başvurmak için kullanılan yüzde işareti.|
|$|%24|Dolar işareti, özelliklere başvurmak için kullanılır.|
|@|%40|Öğesinde, öğe listelerine başvurmak için kullanılır.|
|(|%28|Listelerde kullanılan parantez açın.|
|)|%29|Listelerde kullanılan parantez kapatma.|
|;|% 3B|Noktalı virgül, liste ayırıcısı.|
|?|% 3F|Soru işareti, bir öğenin Içerme/hariç tutma bölümünde bir dosya belirtimini açıklayan bir joker karakterdir.|
|* |% 2A|Bir öğenin Içerme/hariç tutma bölümünde bir dosya belirtimini açıklayan bir joker karakter olan yıldız işareti.|

> [!NOTE]
> Bazı senaryolarda, bir görev içinde kullanırken olduğu gibi çift tırnak (") karakterlerini kaçış gerekebilir `Exec` .

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: MSBuild 'de özel karakterleri kaçış](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
