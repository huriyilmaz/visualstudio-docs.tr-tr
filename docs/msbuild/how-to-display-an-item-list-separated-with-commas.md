---
title: 'Nasıl yapılır: virgülle ayrılmış bir öğe listesini görüntüleme | Microsoft Docs'
description: virgülle ayrılmış bir öğe listesini göstermek için MSBuild kullanmayı veya bir öğe listesi için diğer ayırıcı dizeleri belirtmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 87fc8cb1870d2c99a7e654b8f9fa3ecc31773be3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625736"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Nasıl yapılır: virgülle ayrılmış bir öğe listesini görüntüleme

Microsoft Build Engine (MSBuild) içindeki öğe listeleriyle çalışırken, bu öğe listelerinin içeriğini okunması kolay bir şekilde göstermek bazen yararlı olur. Ya da özel bir ayırıcı dizesiyle ayrılan öğelerin listesini alan bir göreviniz olabilir. Bu iki durumda da, bir öğe listesi için bir ayırıcı dize belirtebilirsiniz.

## <a name="separate-items-in-a-list-with-commas"></a>Listedeki öğeleri virgülle ayırın

MSBuild, varsayılan olarak, listedeki öğeleri ayırmak için noktalı virgül kullanır. Örneğin, `Message` aşağıdaki değere sahip bir öğe düşünün:

`<Message Text="This is my list of TXT files: @(TXTFile)"/>`

`@(TXTFile)`Öğe listesi *App1.txt*, *App2.txt* ve *App3.txt* öğelerini içerdiğinde ileti şu şekilde olur:

`This is my list of TXT files: App1.txt;App2.txt;App3.txt`

Varsayılan davranışı değiştirmek istiyorsanız kendi ayırıcıınızı belirtebilirsiniz. Öğe listesi ayırıcısını belirtmek için sözdizimi şöyledir:

`@(ItemListName, '<separator>')`

Ayırıcı tek bir karakter veya dize olabilir ve tek tırnak içine alınmalıdır.

#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Öğeler arasına virgül ve boşluk eklemek için

- Aşağıdakine benzer öğe gösterimini kullanın:

    `@(TXTFile, ', ')`

## <a name="example"></a>Örnek

Bu örnekte, [Exec](../msbuild/exec-task.md) görevi dosyada belirtilen metin dizelerini bulmak için Findstr aracını çalıştırır *Phrases.txt*. Findstr komutunda, değişmez değer arama dizeleri **/c:** anahtarıyla gösterilir, bu nedenle öğe ayırıcısı öğe ` /c:` listesindeki öğeler arasına eklenir `@(Phrase)` .

Bu örnek için, eşdeğer komut satırı komutu:

`findstr /i /c:hello /c:world /c:msbuild phrases.txt`

```xml
<Project DefaultTargets = "Find"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <ItemGroup>
        <Phrase Include="hello"/>
        <Phrase Include="world"/>
        <Phrase Include="msbuild"/>
    </ItemGroup>

    <Target Name = "Find">
        <!-- Find some strings in a file -->
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Öğeler](../msbuild/msbuild-items.md)
