---
title: MSBuild Iyi bilinen öğe meta verileri | Microsoft Docs
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c810e166ef6f04befdbf7a5d18fe20bb65b8a299
ms.sourcegitcommit: dda98068c0f62ccd1a19fdfde4bdb822428d0125
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2020
ms.locfileid: "87425387"
---
# <a name="msbuild-well-known-item-metadata"></a>MSBuild tanınmış öğe meta verileri

Öğe meta verileri öğelere eklenmiş değerlerdir. Bazıları öğeler oluşturulduğunda öğelere MSBuild tarafından atanır, ancak ihtiyacınız olan meta verileri de tanımlayabilirsiniz. Kullanıcı tanımlı bazı meta veri değerlerinin MSBuild, belirli görev görevleri veya .NET SDK gibi SDK 'lar için anlamı vardır.

Bu makaledeki ilk tablo, oluşturma sırasında her öğeye atanan meta verileri tanımlar. Sonraki tabloda, yapı davranışını denetlemek için tanımlayabileceğiniz MSBuild için anlamı olan bazı isteğe bağlı meta veriler gösterilmektedir. Her örnekte, projede *C:\myproject\source\program.cs* dosyasını eklemek için aşağıdaki öğe bildirimi kullanılmıştır.

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|Öğe meta verileri|Description|
|-------------------|-----------------|
|% (FullPath)|Öğenin tam yolunu içerir. Örneğin:<br /><br /> *C:\MyProject\Source\Program.cs*|
|% (RootDir)|Öğenin kök dizinini içerir. Örneğin:<br /><br /> *,\\*|
|% (Dosya adı)|Uzantı olmadan öğenin dosya adını içerir. Örneğin:<br /><br /> *Program*|
|% (Uzantı)|Öğenin dosya adı uzantısını içerir. Örneğin:<br /><br /> *.cs*|
|% (RelativeDir)|`Include`En son ters eğik çizgi () kadar özniteliğinde belirtilen yolu içerir \\ . Örneğin:<br /><br /> *Kaynak\\*<br /><br /> `Include`Öznitelik bir tam yol ise `%(RelativeDir)` kök diziniyle başlar `%(RootDir)` .  Örneğin: <br /><br /> *C:\MyProject\Source\\*|
|% (Dizin)|Kök dizin olmadan öğenin dizinini içerir. Örneğin:<br /><br /> *MyProject \\ kaynağı\\*|
|%(RecursiveDir)|`Include`Öznitelik joker karakterini içeriyorsa \* \* , bu meta veri, yolun joker karakter yerine geçen kısmını belirtir. Joker karakterler hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturulacak dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> * \\ C:\solution\myproject\source* klasörü *program.cs*dosyasını içeriyorsa ve proje dosyası bu öğeyi içeriyorsa:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> Bundan sonra değeri `%(MyItem.RecursiveDir)` * \\ Mysolution\myproject\source*olacaktır.|
|% (Kimlik)|Öznitelikte belirtilen öğe `Include` . Örneğin:<br /><br /> *Source\Program.cs*|
|% (ModifiedTime)|Öğenin son değiştirildiği zamandan gelen zaman damgasını içerir. Örneğin:<br /><br /> `2004-07-01 00:21:31.5073316`|
|% (CreatedTime)|Öğenin oluşturulduğu zaman damgasını içerir. Örneğin:<br /><br /> `2004-06-25 09:26:45.8237425`|
|% (AccessedTime)|Öğenin en son erişildiği zaman damgasını içerir.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>Ayrıca bkz.

- [Ortak MSBuild öğe meta verileri](common-msbuild-item-metadata.md)
- [Öğeler](../msbuild/msbuild-items.md)
- [Toplu İşleme](../msbuild/msbuild-batching.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
