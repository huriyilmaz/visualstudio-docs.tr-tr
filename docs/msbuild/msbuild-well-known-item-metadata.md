---
title: MSBuild İyi Bilinen Öğe Metadata | Microsoft Dokümanlar
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
ms.openlocfilehash: 6e9320525d770344f131d9e3f04b357de43b5e73
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633102"
---
# <a name="msbuild-well-known-item-metadata"></a>MSBuild iyi bilinen öğe meta verileri

Aşağıdaki tabloda, oluşturulduktan sonra her öğeye atanan meta veriler açıklanmaktadır. Her örnekte, projeye *C:\MyProject\Source\Program.cs* dosyasını eklemek için aşağıdaki madde bildirimi kullanılmıştır.

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|Madde meta verileri|Açıklama|
|-------------------|-----------------|
|%(FullPath)|Öğenin tam yolunu içerir. Örnek:<br /><br /> *C:\MyProject\Kaynak\Program.cs*|
|%(RootDir)|Öğenin kök dizini içerir. Örnek:<br /><br /> *C:\\*|
|%(Dosya adı)|Uzantı olmadan öğenin dosya adını içerir. Örnek:<br /><br /> *Program*|
|%(Uzantı)|Öğenin dosya adı uzantısını içerir. Örnek:<br /><br /> *Cs*|
|%(RelativeDir)|Öznitelikte `Include` belirtilen yolu, son ters eğik\\çizgiye kadar ( ) içerir. Örnek:<br /><br /> *Kaynak\\*<br /><br /> `Include` Öznitelik tam bir yol `%(RelativeDir)` ise, kök dizini `%(RootDir)`ile başlar.  Örnek: <br /><br /> *C:\MyProject\Kaynak\\*|
|%(Dizin)|Kök dizini olmadan öğenin dizinini içerir. Örnek:<br /><br /> *MyProject\\Kaynak\\*|
|%(RecursiveDir)|`Include` Öznitelik joker karakter \* \*içeriyorsa, bu meta veri joker kartın yerine giden yolun bölümünü belirtir. Joker karakterler hakkında daha fazla bilgi için [bkz.](../msbuild/how-to-select-the-files-to-build.md)<br /><br /> *C:\MySolution\MyProject\Source\\ * klasörü *Program.cs*dosyayı içeriyorsa ve proje dosyasında bu öğe varsa:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> sonra değeri `%(MyItem.RecursiveDir)` *MySolution\MyProject\Source\\*olacaktır.|
|%(Kimlik)|Öznitelikte `Include` belirtilen öğe. Örnek:<br /><br /> *Kaynak\Program.cs*|
|%(Modifiye Süresi)|Öğenin en son değiştirildiğindeki zaman damgasını içerir. Örnek:<br /><br /> `2004-07-01 00:21:31.5073316`|
|%(CreatedTime)|Öğenin oluşturulduğu zamana ait zaman damgasını içerir. Örnek:<br /><br /> `2004-06-25 09:26:45.8237425`|
|%(AccessedTime)|Öğeye en son erişilen zamana ait zaman damgasını içerir.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>Ayrıca bkz.

- [Öğeler](../msbuild/msbuild-items.md)
- [İşlem grubu oluşturma](../msbuild/msbuild-batching.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
