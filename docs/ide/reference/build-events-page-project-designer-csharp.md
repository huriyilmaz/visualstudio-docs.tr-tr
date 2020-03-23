---
title: Derleme Olayları Sayfası, Proje Tasarımcısı (C#)
ms.date: 10/17/2019
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6629f41657a546ffb5fb48e0b6efb5f4f0dd50cb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596885"
---
# <a name="build-events-page-project-designer-c"></a>Derleme Olayları Sayfası, Proje Tasarımcısı (C#)

Yapı yapılandırma yönergelerini belirtmek için **Proje Tasarımcısı'nın** **Yapı Olayları** sayfasını kullanın. Ayrıca, yapı sonrası olayların hangi koşullar altında çalıştırılan koşulları da belirtebilirsiniz. Daha fazla bilgi için [bkz: Yapı Olaylarını (C#) Belirtin](../../ide/how-to-specify-build-events-csharp.md) ve [Nasıl Yapılır: Yapı Olayları (Visual Basic) belirtin.](../../ide/how-to-specify-build-events-visual-basic.md)

## <a name="uielement-list"></a>UIElement Listesi

**Yapılandırma**

Bu denetim bu sayfada denetlenemez. Bu denetimin açıklaması için Bkz. [Build Page, Project Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Platform**

Bu denetim bu sayfada denetlenemez. Bu denetimin açıklaması için Bkz. [Build Page, Project Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Önceden oluşturma olay komut satırı**

Yapı başlamadan önce yürütülecek komutları belirtir. Uzun komutlar yazmak için, [Önceden Yapılan Olay/Post-build Olay Komut Satırı İletişim Kutusu'nu](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)görüntülemek için **Ön Yapıyı** Düzenle'yi tıklatın.

> [!NOTE]
> Proje güncelse ve hiçbir yapı tetiklenmiyorsa, önceden yapı olayları çalışmaz.

**Oluşturma sonrası olay komut satırı**

Yapı sona erdikten sonra yürütülecek komutları belirtir. Uzun komutlar yazmak için, **Önceden Yapılan Olay/Post-build Olay Komut Satırı İletişim Kutusu'nu**görüntülemek için **Post-build'i** düzenle'yi tıklatın.

> [!NOTE]
> .bat `call` dosyalarını çalıştıran tüm yapı sonrası komutlardan önce bir deyim ekleyin. Örneğin `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat` olabilir.

**Oluşturma sonrası etkinliği çalıştırma**

Aşağıdaki tabloda gösterildiği gibi, yapı sonrası olayın çalışması için aşağıdaki koşulları belirtir.

|Seçenek|Sonuç|
|------------|------------|
|**Her zaman**|Yapı sonrası olay, yapının başarılı olup olmadığına bakılmaksızın çalışır.|
|**Başarılı yapıda**|Yapı başarılı olursa, yapı sonrası olay çalışacaktır. Böylece, oluşturma başarılı olduğu sürece, olay güncel bir proje için bile çalışacaktır.|
|**Yapı proje çıktısını güncellediğinde**|Yapı sonrası olay yalnızca derleyicinin çıktı dosyası (.exe veya .dll) önceki derleyici çıktı dosyasından farklı olduğunda çalışır. Bu nedenle, bir proje güncelse, yapı sonrası olay çalıştırılmez.|

## <a name="in-the-project-file"></a>Proje dosyasında

Visual Studio'nun önceki sürümlerinde, IDE'deki **PreBuildEvent** veya **PostBuildEvent** ayarını değiştirdiğinizde, Visual Studio proje dosyasına bir `PreBuildEvent` özellik veya `PostBuildEvent` özellik ekler. Örneğin, IDE'deki **PreBuildEvent** komut satırı ayarınız aşağıdaki gibiyse:

```input
"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"
```

sonra proje dosyası ayarı:

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

.NET Core projeleri için Visual Studio 2019 (ve visual studio 2017 daha `PreBuild` `PostBuild` yeni güncellemelerde) PreBuildEvent ve **PostBuildEvent** ayarları için bir **MSBuild** hedefi ekler. Bu hedefler, MSBuild'in tanıdığı **BeforeTargets** ve **AfterTargets** özniteliklerini kullanır. Örneğin, önceki örnekiçin Visual Studio şimdi aşağıdaki kodu oluşturur:

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>
```

Yapı sonrası bir olay için, `PostBuild` adı kullanın `AfterTargets` ve `PostBuildEvent`özniteliği ' ne ayarlayın.

```xml
<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
> Bu proje dosyası değişiklikleri SDK tarzı projeleri desteklemek için yapılmıştır. Bir proje dosyasını eski biçimden SDK stili biçimine el ile geçiş `PreBuildEvent` iyorsanız, önceki kodda gösterildiği gibi bunları ve `PostBuildEvent` özelliklerini silmeniz ve bunları değiştirmeniz `PreBuild` `PostBuild` gerekir. Projenizin SDK tarzı bir proje olup olmadığını öğrenmek için [bkz.](/nuget/resources/check-project-format)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Yapı Olaylarını Belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Nasıl Yapılır: Yapı Olaylarını Belirtme (C#)](../../ide/how-to-specify-build-events-csharp.md)
- [Proje Özellikleri Başvurusu](../../ide/reference/project-properties-reference.md)
- [Derleme ve Oluşturma](../../ide/compiling-and-building-in-visual-studio.md)
