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
ms.openlocfilehash: 6e9320525d770344f131d9e3f04b357de43b5e73
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633102"
---
# <a name="msbuild-well-known-item-metadata"></a>MSBuild iyi bilinen öğe meta verileri

Aşağıdaki tabloda, oluşturma sırasında her öğeye atanan meta veriler açıklanmaktadır. Her örnekte, projede *C:\myproject\source\program.cs* dosyasını eklemek için aşağıdaki öğe bildirimi kullanılmıştır.

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|Öğe meta verileri|Açıklama|
|-------------------|-----------------|
|% (FullPath)|Öğenin tam yolunu içerir. Örnek:<br /><br /> *C:\MyProject\Source\Program.cs*|
|% (RootDir)|Öğenin kök dizinini içerir. Örnek:<br /><br /> *C:\\*|
|% (Dosya adı)|Uzantı olmadan öğenin dosya adını içerir. Örnek:<br /><br /> *Programda*|
|% (Uzantı)|Öğenin dosya adı uzantısını içerir. Örnek:<br /><br /> *.cs*|
|% (RelativeDir)|`Include` özniteliğinde, son ters eğik çizgiye (\\) kadar belirtilen yolu içerir. Örnek:<br /><br /> *Kaynak\\*<br /><br /> `Include` özniteliği bir tam yol ise, `%(RelativeDir)` kök dizin `%(RootDir)`başlar.  Örnek: <br /><br /> *C:\MyProject\Source\\*|
|% (Dizin)|Kök dizin olmadan öğenin dizinini içerir. Örnek:<br /><br /> *MyProject\\kaynak\\*|
|%(RecursiveDir)|`Include` özniteliği \*joker karakter \*içeriyorsa, bu meta veri, yolun joker karakteri yerine geçen kısmını belirtir. Joker karakterler hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturulacak dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> *C:\solution\myproject\source\\* klasörü *program.cs*dosyasını içeriyorsa ve proje dosyası bu öğeyi içeriyorsa:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> `%(MyItem.RecursiveDir)` değeri *Mysolution\myproject\source\\* olacaktır.|
|% (Kimlik)|`Include` özniteliğinde belirtilen öğe. Örnek:<br /><br /> *Source\Program.cs*|
|% (ModifiedTime)|Öğenin son değiştirildiği zamandan gelen zaman damgasını içerir. Örnek:<br /><br /> `2004-07-01 00:21:31.5073316`|
|% (CreatedTime)|Öğenin oluşturulduğu zaman damgasını içerir. Örnek:<br /><br /> `2004-06-25 09:26:45.8237425`|
|% (AccessedTime)|Öğenin en son erişildiği zaman damgasını içerir.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>Ayrıca bkz.

- [Öğeler](../msbuild/msbuild-items.md)
- [İşlem grubu oluşturma](../msbuild/msbuild-batching.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
