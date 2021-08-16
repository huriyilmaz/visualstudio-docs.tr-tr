---
title: MSBuild İyi bilinen öğe meta verileri | Microsoft Docs
description: oluşturma sırasında her öğeye atanan MSBuild meta verileri ve yapı davranışını denetlemek için tanımlayabileceğiniz bazı isteğe bağlı MSBuild meta verileri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 61cef1a4b6fc8d7db78cda6f034d5a897aebc3874b3e27282b6927ef2c3288e7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397351"
---
# <a name="msbuild-well-known-item-metadata"></a>MSBuild tanınmış öğe meta verileri

Öğe meta verileri öğelere eklenmiş değerlerdir. bazıları öğeleri oluştururken öğelere MSBuild atanır, ancak ihtiyacınız olan meta verileri de tanımlayabilirsiniz. kullanıcı tanımlı bazı meta veri değerlerinin MSBuild, belirli görev görevlerinin veya .net SDK gibi sdk 'ların anlamı vardır.

Bu makaledeki ilk tablo, oluşturma sırasında her öğeye atanan meta verileri tanımlar. sonraki tabloda, yapı davranışını denetlemek için tanımlayabileceğiniz MSBuild anlamı olan bazı isteğe bağlı meta veriler gösterilmektedir. Her örnekte, projede *C:\myproject\source\program.cs* dosyasını eklemek için aşağıdaki öğe bildirimi kullanılmıştır.

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|Öğe meta verileri|Açıklama|
|-------------------|-----------------|
|% (FullPath)|Öğenin tam yolunu içerir. Örnek:<br /><br /> *C:\MyProject\Source\Program.cs*|
|% (RootDir)|Öğenin kök dizinini içerir. Örnek:<br /><br /> *,\\*|
|% (Dosya adı)|Uzantı olmadan öğenin dosya adını içerir. Örnek:<br /><br /> *Program*|
|% (Uzantı)|Öğenin dosya adı uzantısını içerir. Örnek:<br /><br /> *.cs*|
|% (RelativeDir)|`Include`En son ters eğik çizgi () kadar özniteliğinde belirtilen yolu içerir \\ . Örnek:<br /><br /> *Kaynak\\*<br /><br /> `Include`Öznitelik bir tam yol ise `%(RelativeDir)` kök diziniyle başlar `%(RootDir)` .  Örnek: <br /><br /> *C:\MyProject\Source\\*|
|% (Dizin)|Kök dizin olmadan öğenin dizinini içerir. Örnek:<br /><br /> *MyProject \\ kaynağı\\*|
|%(RecursiveDir)|`Include`Öznitelik joker karakterini içeriyorsa \* \* , bu meta veri, yolun joker karakter yerine geçen kısmını belirtir. Joker karakterler hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturulacak dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> *C:\solution\myproject\source \\* klasörü dosya *program. cs* içeriyorsa ve proje dosyası bu öğeyi içeriyorsa:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> Bundan sonra değeri `%(MyItem.RecursiveDir)` *\\ Mysolution\myproject\source* olacaktır.|
|% (Kimlik)|Öznitelikte belirtilen öğe `Include` . Örnek:<br /><br /> *Source\Program.cs*|
|% (ModifiedTime)|Öğenin son değiştirildiği zamandan gelen zaman damgasını içerir. Örnek:<br /><br /> `2004-07-01 00:21:31.5073316`|
|% (CreatedTime)|Öğenin oluşturulduğu zaman damgasını içerir. Örnek:<br /><br /> `2004-06-25 09:26:45.8237425`|
|% (AccessedTime)|Öğenin en son erişildiği zaman damgasını içerir.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>Ayrıca bkz.

- [Yaygın MSBuild öğesi meta verileri](common-msbuild-item-metadata.md)
- [Öğeler](../msbuild/msbuild-items.md)
- [Toplu İşleme](../msbuild/msbuild-batching.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
