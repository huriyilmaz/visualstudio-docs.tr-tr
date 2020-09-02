---
title: MSBuild Iyi bilinen öğe meta verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1bb2e53102221194dc829df162c44bbf04378b28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154080"
---
# <a name="msbuild-well-known-item-metadata"></a>MSBuild Tanınmış Öğe Meta Verisi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aşağıdaki tabloda, oluşturma sırasında her öğeye atanan meta veriler açıklanmaktadır. Her örnekte, dosyayı projeye eklemek için aşağıdaki öğe bildirimi kullanılmıştır `C:\MyProject\Source\Program.cs` .  
  
```  
<ItemGroup>  
    <MyItem Include="Source\Program.cs" />  
</ItemGroup>  
```  
  
|Öğe meta verileri|Açıklama|  
|-------------------|-----------------|  
|% (FullPath)|Öğenin tam yolunu içerir. Örneğin:<br /><br /> `C:\MyProject\Source\Program.cs`|  
|% (RootDir)|Öğenin kök dizinini içerir. Örneğin:<br /><br /> `C:\`|  
|% (Dosya adı)|Uzantı olmadan öğenin dosya adını içerir. Örneğin:<br /><br /> `Program`|  
|% (Uzantı)|Öğenin dosya adı uzantısını içerir. Örneğin:<br /><br /> `.cs`|  
|% (RelativeDir)|`Include`En son ters eğik çizgi () kadar özniteliğinde belirtilen yolu içerir \\ . Örneğin:<br /><br /> `Source\`|  
|% (Dizin)|Kök dizin olmadan öğenin dizinini içerir. Örneğin:<br /><br /> `MyProject\Source\`|  
|%(RecursiveDir)|`Include`Öznitelik joker karakterini içeriyorsa \* \* , bu meta veri, yolun joker karakter yerine geçen kısmını belirtir. Joker karakterler hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturulacak dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> *C:\solution\myproject\source \\ * klasörü program.cs dosyasını içeriyorsa ve proje dosyası bu öğeyi içeriyorsa:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> Bundan sonra değeri `%(MyItem.RecursiveDir)` * \\ Mysolution\myproject\source*olacaktır.|  
|% (Kimlik)|Öznitelikte belirtilen öğe `Include` .. Örneğin:<br /><br /> `Source\Program.cs`|  
|% (ModifiedTime)|Öğenin son değiştirildiği zamandan gelen zaman damgasını içerir. Örneğin:<br /><br /> `2004-07-01 00:21:31.5073316`|  
|% (CreatedTime)|Öğenin oluşturulduğu zaman damgasını içerir. Örneğin:<br /><br /> `2004-06-25 09:26:45.8237425`|  
|% (AccessedTime)|Öğenin en son erişildiği zaman damgasını içerir.<br /><br /> `2004-08-14 16:52:36.3168743`|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğeler](../msbuild/msbuild-items.md)   
 [İşlem](../msbuild/msbuild-batching.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)
