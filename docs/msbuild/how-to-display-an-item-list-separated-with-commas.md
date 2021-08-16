---
title: 'Nasıl kullanılır: Virgülle Ayrılmış Bir Öğe Listesi | Microsoft Docs'
description: Virgülle ayrılmış bir öğe MSBuild görüntülemek veya bir öğe listesi için diğer ayırıcı dizeleri belirtmek üzere bir öğe listesini nasıl kullanabileceğiniz hakkında bilgi edinebilirsiniz.
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
ms.openlocfilehash: 6f8105c28ad7b827f0b03d6e632ebceef1c83229aed3f4fb79bd41078c51d6a8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427788"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Nasıl kullanılır: Virgülle ayrılmış bir öğe listesi görüntüleme

Öğe listeleriyle çalışma Microsoft Build Engine (MSBuild), bazen bu öğe listelerinin içeriğini kolay okunan bir şekilde görüntülemek yararlı olabilir. Veya özel ayırıcı dizeyle ayrılmış bir öğe listesi alan bir göreviniz olabilir. Bu iki durumda da, bir öğe listesi için ayırıcı dize belirtebilirsiniz.

## <a name="separate-items-in-a-list-with-commas"></a>Bir listede öğeleri virgülle ayırma

Varsayılan olarak, MSBuild öğeleri ayırmak için noktalı virgül kullanır. Örneğin, aşağıdaki `Message` değere sahip bir öğeyi düşünün:

`<Message Text="This is my list of TXT files: @(TXTFile)"/>`

Öğe `@(TXTFile)` listesi ,App1.txt, *App2.txt* ** veApp3.txtöğelerini *içerdiğinde,* ileti şöyledir:

`This is my list of TXT files: App1.txt;App2.txt;App3.txt`

Varsayılan davranışı değiştirmek için kendi ayırıcınızı belirtabilirsiniz. Öğe listesi ayırıcısı belirtmek için söz dizimi şu şekildedir:

`@(ItemListName, '<separator>')`

Ayırıcı tek bir karakter veya dize olabilir ve tek tırnak içine alınarak olmalıdır.

#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Öğeler arasına virgül ve boşluk eklemek için

- Aşağıdakine benzer öğe notasyonu kullanın:

    `@(TXTFile, ', ')`

## <a name="example"></a>Örnek

Bu örnekte, [Exec](../msbuild/exec-task.md) görevi dosyada belirtilen metin dizelerini bulmak için findstr aracını çalıştırır ve *Phrases.txt.* findstr komutunda değişmez arama dizeleri **/c:** anahtarı tarafından belirtilmiştir; bu nedenle öğe ayırıcısı, öğe listesinde öğeler ` /c:` `@(Phrase)` arasına eklenir.

Bu örnekte eşdeğer komut satırı komutu şu şekildedir:

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
