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
ms.openlocfilehash: 686640cbe3c93cbe3d938cd3025a77129c829bd7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595117"
---
# <a name="special-characters-to-escape"></a>Kaçış için özel karakterler
Özel karakterler yalnızca kullanıldıkları bağlamda özel anlam içeriyorsa kaçışmalıdır. Örneğin, yıldız işareti (*) yalnızca bir öğe tanımının "Içerme" ve "hariç tutma" özniteliklerinde veya <xref:Microsoft.Build.Tasks.CreateItem>çağrısında özel bir karakterdir. Diğer tüm durumlarda, yıldız işareti sabit bir yıldız işareti olarak değerlendirilir. Proje dosyalarında herhangi bir yerde yıldız işaretleri gerekmez, ancak bunu yapmak zarar vermez.

 Özel karakterin yerine%\<xx > gösterimini kullanın; burada \<xx >, ASCII karakterinin onaltılı değerini temsil eder. Örneğin, bir yıldız işareti (*) sabit karakter olarak kullanmak için `%2A`değerini kullanın.

 Kaçış için özel karakterlerin tam listesi aşağıdadır:

|Karakter|Açıklama|
|---------------|-----------------|
|%|Meta verilere başvurmak için kullanılan yüzde işareti.|
|$|Dolar işareti, özelliklere başvurmak için kullanılır.|
|@|Öğesinde, öğe listelerine başvurmak için kullanılır.|
|(|Listelerde kullanılan parantez açın.|
|)|Listelerde kullanılan parantez kapatma.|
|;|Noktalı virgül, liste ayırıcısı.|
|?|Soru işareti, bir öğenin Içerme/hariç tutma bölümünde bir dosya belirtimini açıklayan bir joker karakterdir.|
|*|Bir öğenin Içerme/hariç tutma bölümünde bir dosya belirtimini açıklayan bir joker karakter olan yıldız işareti.|

> [!NOTE]
> Bazı senaryolarda, `Exec` bir görevde kullanırken olduğu gibi çift tırnak (") karakterlerini kaçış gerekebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: MSBuild 'de özel karakterleri kaçış](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
