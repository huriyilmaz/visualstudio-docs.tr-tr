---
title: MSBuild İyi Bilinen Öğe Meta Verileri | Microsoft Docs
description: Oluşturma sırasında MSBuild öğeye atanan meta verileri ve derleme davranışını denetlemeye MSBuild isteğe bağlı meta veriler hakkında bilgi öğrenin.
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
ms.openlocfilehash: da48ecf879478be22c3a8e2db9bb6a3700390869
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093690"
---
# <a name="msbuild-well-known-item-metadata"></a>MSBuild tanınmış öğe meta verileri

Öğe meta verileri, öğelere eklenmiş değerlerdir. Bazıları, öğeler MSBuild öğelere özel olarak atanır, ancak ihtiyacınız olan tüm meta verileri de tanımlayabilirsiniz. Bazı kullanıcı tanımlı meta veri değerleri, MSBuild görevleri veya .NET SDK gibi SDK'ları ifade eder.

Bu makaledeki ilk tabloda, oluşturma sırasında her öğeye atanan meta veriler açıklanmıştır. Sonraki tabloda, derleme davranışını kontrol etmek için tanımladığınız MSBuild bazı isteğe bağlı meta veriler yer alır. Her örnekte, aşağıdaki öğe bildirimi projeye *C:\MyProject\Source\Program.cs* dosyasını eklemek için kullanılmıştır.

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|Öğe meta verileri|Açıklama|
|-------------------|-----------------|
|%(FullPath)|Öğenin tam yolunu içerir. Örnek:<br /><br /> *C:\MyProject\Source\Program.cs*|
|%(RootDir)|Öğenin kök dizinini içerir. Örnek:<br /><br /> *C:\\*|
|%(Dosya adı)|Uzantı olmadan öğenin dosya adını içerir. Örnek:<br /><br /> *Program*|
|%(Uzantı)|Öğenin dosya adı uzantısını içerir. Örnek:<br /><br /> *Cs*|
|%(RelativeDir)|Son ters eğik `Include` çizgiye ( ) kadar özniteliğinde belirtilen yolu \\ içerir. Örnek:<br /><br /> *Kaynak\\*<br /><br /> Öznitelik `Include` tam bir yol ise, `%(RelativeDir)` kök diziniyle `%(RootDir)` başlar.  Örnek: <br /><br /> *C:\MyProject\Source\\*|
|%(Dizin)|Kök dizin olmadan öğenin dizinini içerir. Örnek:<br /><br /> *MyProject \\ Kaynağı\\*|
|%(RecursiveDir)|özniteliği joker karakter içeriyorsa, bu meta veriler yolun joker `Include` \* \* karakterin yerini alan bölümünü belirtir. Joker karakterler hakkında daha fazla bilgi için [bkz. Nasıl kullanılır: Derlemek için dosyaları seçme.](../msbuild/how-to-select-the-files-to-build.md)<br /><br /> *C:\MySolution\MyProject\Source \\* klasörü *Program.cs* dosyasını içeriyorsa ve proje dosyası şu öğeyi içeriyorsa:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> değeri `%(MyItem.RecursiveDir)` *MySolution\MyProject\Source olur. \\*|
|%(Kimlik)|özniteliğinde belirtilen `Include` öğe. Örnek:<br /><br /> *Source\Program.cs*|
|%(ModifiedTime)|Öğenin son değiştirilme zaman damgasını içerir. Örnek:<br /><br /> `2004-07-01 00:21:31.5073316`|
|%(CreatedTime)|Öğenin oluşturulma zaman damgasını içerir. Örnek:<br /><br /> `2004-06-25 09:26:45.8237425`|
|%(AccessedTime)|Öğeye son erişilen zaman damgasını içerir.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>Ayrıca bkz.

- [Yaygın MSBuild öğesi meta verileri](common-msbuild-item-metadata.md)
- [Öğeler](../msbuild/msbuild-items.md)
- [Toplu İşleme](../msbuild/msbuild-batching.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
