---
title: 'Nasıl Yapılsın: Virgülle Ayrılmış Öğe Listesini Görüntüleme | Microsoft Dokümanlar'
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
ms.openlocfilehash: 5493d3b95f7e9c0aa08ed3b06a99108e15697349
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633908"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Nasıl yapılsın: Virgülle ayrılmış bir öğe listesini görüntüleme

Microsoft Build Engine'deki (MSBuild) öğe listeleriyle çalışırken, bu öğe listelerinin içeriğini okunması kolay bir şekilde görüntülemek bazen yararlıdır. Veya, özel bir ayırıcı dize ile ayrılmış öğelerin listesini alan bir görev olabilir. Bu iki durumda da, bir öğe listesi için ayırıcı dize belirtebilirsiniz.

## <a name="separate-items-in-a-list-with-commas"></a>Virgüliçeren bir listedeki ayrı öğeler

Varsayılan olarak, MSBuild bir listedeki öğeleri ayırmak için yarı iki nokta üst üste kullanır. Örneğin, aşağıdaki `Message` değere sahip bir öğe düşünün:

`<Message Text="This is my list of TXT files: @(TXTFile)"/>`

Öğe listesi *App1.txt*, *App2.txt*ve *App3.txt*öğelerini içeriyorsa, ileti: `@(TXTFile)`

`This is my list of TXT files: App1.txt;App2.txt;App3.txt`

Varsayılan davranışı değiştirmek istiyorsanız, kendi ayırıcınızı belirtebilirsiniz. Madde listesi ayırıcısını belirtmek için sözdizimi:

`@(ItemListName, '<separator>')`

Ayırıcı tek bir karakter veya dize olabilir ve tek tırnak içinde eklenmelidir.

#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Virgül ve öğeler arasında boşluk eklemek için

- Aşağıdakilere benzer öğe gösterimi kullanın:

    `@(TXTFile, ', ')`

## <a name="example"></a>Örnek

Bu örnekte, [Exec](../msbuild/exec-task.md) görev dosyada belirtilen metin dizeleri bulmak için findstr aracıçalışır, *Phrases.txt*. Findstr komutunda, gerçek arama dizeleri **-c:** switch ile gösterilir, `-c:` böylece öğe ayırıcısı `@(Phrase)` madde listesindeki öğeler arasına eklenir.

Bu örnekte, eşdeğer komut satırı komutu:

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
