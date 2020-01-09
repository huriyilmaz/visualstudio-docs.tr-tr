---
title: 'Nasıl yapılır: virgülle ayrılmış bir öğe listesini görüntüleme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 677278d08e3223f759afc64692481311bfba3356
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596339"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Nasıl yapılır: virgülle ayrılmış bir öğe listesini görüntüleme
[!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) içindeki öğe listeleriyle çalışırken, bu öğe listelerinin içeriğini okunması kolay bir şekilde göstermek bazen yararlı olur. Ya da özel bir ayırıcı dizesiyle ayrılan öğelerin listesini alan bir göreviniz olabilir. Bu iki durumda da, bir öğe listesi için bir ayırıcı dize belirtebilirsiniz.

## <a name="separate-items-in-a-list-with-commas"></a>Listedeki öğeleri virgülle ayırın
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], varsayılan olarak, listedeki öğeleri ayırmak için noktalı virgül kullanır. Örneğin, aşağıdaki değere sahip bir `Message` öğesini düşünün:

`<Message Text="This is my list of TXT files: @(TXTFile)"/>`

`@(TXTFile)` öğe listesi *app1. txt*, *app2. txt*ve *App3. txt*öğelerini içerdiğinde ileti şu şekilde olur:

`This is my list of TXT files: App1.txt;App2.txt;App3.txt`

Varsayılan davranışı değiştirmek istiyorsanız kendi ayırıcıınızı belirtebilirsiniz. Öğe listesi ayırıcısını belirtmek için sözdizimi şöyledir:

`@(ItemListName, '<separator>')`

Ayırıcı tek bir karakter veya dize olabilir ve tek tırnak içine alınmalıdır.

#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Öğeler arasına virgül ve boşluk eklemek için

- Aşağıdakine benzer öğe gösterimini kullanın:

    `@(TXTFile, ', ')`

## <a name="example"></a>Örnek
Bu örnekte, [Exec](../msbuild/exec-task.md) görevi, belirtilen metin dizelerini dosya, *tümcecikler. txt*dosyasında bulmak için Findstr aracını çalıştırır. Findstr komutunda, değişmez değer arama dizeleri **-c:** anahtarıyla belirtilir, bu nedenle öğe ayırıcısı, `-c:` `@(Phrase)` öğesi listesindeki öğeler arasına eklenir.

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
