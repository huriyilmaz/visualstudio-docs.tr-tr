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
ms.openlocfilehash: 93bbd0ab4ce0d27a270f3672e55173a1488e5910
ms.sourcegitcommit: f28172c78745d14570e733db5d424f5fae98d139
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/02/2020
ms.locfileid: "75606664"
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
|% (FullPath)|Öğenin tam yolunu içerir. Örneğin:<br /><br /> *C:\MyProject\Source\Program.cs*|
|% (RootDir)|Öğenin kök dizinini içerir. Örneğin:<br /><br /> *C:\\*|
|% (Dosya adı)|Uzantı olmadan öğenin dosya adını içerir. Örneğin:<br /><br /> *Programda*|
|% (Uzantı)|Öğenin dosya adı uzantısını içerir. Örneğin:<br /><br /> *.cs*|
|% (RelativeDir)|`Include` özniteliğinde, son ters eğik çizgiye (\\) kadar belirtilen yolu içerir. Örneğin:<br /><br /> *Kaynak\\*<br /><br /> `Include` özniteliği bir tam yol ise, `%(RelativeDir)` kök dizin `%(RootDir)`başlar.  Örneğin: <br /><br /> *C:\MyProject\Source\\*|
|% (Dizin)|Kök dizin olmadan öğenin dizinini içerir. Örneğin:<br /><br /> *MyProject\\kaynak\\*|
|%(RecursiveDir)|`Include` özniteliği \*joker karakter \*içeriyorsa, bu meta veri, yolun joker karakteri yerine geçen kısmını belirtir. Joker karakterler hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturulacak dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> *C:\solution\myproject\source\\* klasörü *program.cs*dosyasını içeriyorsa ve proje dosyası bu öğeyi içeriyorsa:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> `%(MyItem.RecursiveDir)` değeri *Mysolution\myproject\source\\* olacaktır.|
|% (Kimlik)|`Include` özniteliğinde belirtilen öğe. Örneğin:<br /><br /> *Source\Program.cs*|
|% (ModifiedTime)|Öğenin son değiştirildiği zamandan gelen zaman damgasını içerir. Örneğin:<br /><br /> `2004-07-01 00:21:31.5073316`|
|% (CreatedTime)|Öğenin oluşturulduğu zaman damgasını içerir. Örneğin:<br /><br /> `2004-06-25 09:26:45.8237425`|
|% (AccessedTime)|Öğenin en son erişildiği zaman damgasını içerir.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>Ayrıca bkz.
- [Öğeler](../msbuild/msbuild-items.md)
- [Toplu İşleme](../msbuild/msbuild-batching.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
