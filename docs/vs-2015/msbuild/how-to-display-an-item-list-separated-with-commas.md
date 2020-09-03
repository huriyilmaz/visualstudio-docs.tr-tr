---
title: 'Nasıl yapılır: virgülle ayrılmış bir öğe listesini görüntüleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 93451d6d49082621df48c734de951e6a4bc7e281
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156634"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Nasıl Yapılır: Virgülle Ayrılmış Bir Öğe Listesini Görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

() İçindeki öğe listeleriyle çalışırken [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , bu öğe listelerinin içeriğini okunması kolay bir şekilde göstermek bazen yararlı olur. Ya da özel bir ayırıcı dizesiyle ayrılan öğelerin listesini alan bir göreviniz olabilir. Bu iki durumda da, bir öğe listesi için bir ayırıcı dize belirtebilirsiniz.  
  
## <a name="separating-items-in-a-list-with-commas"></a>Listedeki öğeleri virgülle ayırma  
 Varsayılan olarak, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] bir listedeki öğeleri ayırmak için noktalı virgül kullanır. Örneğin, `Message` aşağıdaki değere sahip bir öğe düşünün:  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 `@(TXTFile)`Öğe listesi App1.txt, App2.txt ve App3.txt öğelerini içerdiğinde ileti şu şekilde olur:  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 Varsayılan davranışı değiştirmek istiyorsanız kendi ayırıcıınızı belirtebilirsiniz. Öğe listesi ayırıcısını belirtmek için sözdizimi şöyledir:  
  
 `@(ItemListName, '<separator>')`  
  
 Ayırıcı tek bir karakter veya dize olabilir ve tek tırnak içine alınmalıdır.  
  
#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Öğeler arasına virgül ve boşluk eklemek için  
  
- Aşağıdakine benzer öğe gösterimini kullanın:  
  
     `@(TXTFile, ', ')`  
  
## <a name="example"></a>Örnek  
 Bu örnekte, [Exec](../msbuild/exec-task.md) görevi dosyada belirtilen metin dizelerini bulmak için Findstr aracını çalıştırır Phrases.txt. Findstr komutunda, değişmez değer arama dizeleri **/c:** anahtarıyla gösterilir, bu nedenle öğe ayırıcısı öğe `/c:` listesindeki öğeler arasına eklenir `@(Phrase)` .  
  
 Bu örnek için, eşdeğer komut satırı komutu:  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Öğeler](../msbuild/msbuild-items.md)
