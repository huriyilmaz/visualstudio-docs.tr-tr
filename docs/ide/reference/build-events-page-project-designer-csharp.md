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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4842a5a08de96cd40a45d0765d427cc74cbf5432
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73714380"
---
# <a name="build-events-page-project-designer-c"></a>Derleme Olayları Sayfası, Proje Tasarımcısı (C#)

Yapı yapılandırma yönergelerini belirtmek için **Proje Tasarımcısı** ' nın **Olayları oluştur** sayfasını kullanın. Ayrıca, herhangi bir oluşturma sonrası olayının çalıştırıldığı koşulları belirtebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: derleme olaylarını belirtmeC#()](../../ide/how-to-specify-build-events-csharp.md) ve [nasıl yapılır: derleme olaylarını belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

## <a name="uielement-list"></a>UIElement Listesi

**Yapılandırma**

Bu denetim bu sayfada düzenlenebilir değildir. Bu denetimin açıklaması için bkz. [derleme sayfası, proje Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Platformunun**

Bu denetim bu sayfada düzenlenemez. Bu denetimin açıklaması için bkz. [derleme sayfası, proje Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Oluşturma öncesi olay komut satırı**

Yapı başlamadan önce yürütülecek komutları belirtir. Uzun komutları yazmak için, oluşturma öncesi [olay/oluşturma sonrası olay komut satırı Iletişim kutusunu](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)göstermek Için **derleme ön yapısını Düzenle** ' ye tıklayın.

> [!NOTE]
> Proje güncel değilse ve derleme tetikleniyorsa, ön derleme olayları çalışmaz.

**Oluşturma sonrası olay komut satırı**

Yapı bittikten sonra yürütülecek komutları belirtir. Uzun komutları yazmak için derleme sonrası **olay/oluşturma sonrası olay komut satırı Iletişim kutusunu**göstermek üzere **derlemeyi Düzenle** ' ye tıklayın.

> [!NOTE]
> . Bat dosyalarını çalıştıran tüm derleme sonrası komutları önüne bir `call` ekstresi ekleyin. Örneğin, `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat`.

**Oluşturma sonrası olayını Çalıştır**

Aşağıdaki tabloda gösterildiği gibi, oluşturma sonrası olayının çalışması için aşağıdaki koşulları belirtir.

|Seçenek|Sonuç|
|------------|------------|
|**Her**|Oluşturma sonrası olay, yapılandırmanın başarılı olup olmamasına bakılmaksızın çalışacaktır.|
|**Başarılı derleme üzerinde**|Oluşturma sonrası olay, derleme başarılı olursa çalışır. Bu nedenle, derleme başarılı olduğu sürece olay, güncel olan bir proje için de çalışır.|
|**Derleme proje çıkışını güncelleştirdiğinde**|Oluşturma sonrası olay, yalnızca derleyicinin çıkış dosyası (. exe veya. dll) önceki derleyici çıkış dosyasından farklı olduğunda çalışır. Bu nedenle, bir proje güncel ise, derleme sonrası bir olay çalıştırılmaz.|

## <a name="in-the-project-file"></a>Proje dosyasında

Visual Studio 'nun önceki sürümlerinde, IDE 'deki **PreBuildEvent** veya **PostBuildEvent** ayarını değiştirdiğinizde, Visual studio proje dosyasına bir `PreBuildEvent` veya `PostBuildEvent` özelliği ekler. Örneğin, IDE 'deki **PreBuildEvent** komut satırı ayarınız aşağıdaki gibidir:

```input
"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"
```

ardından proje dosyası ayarı:

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

.NET Core projeleri için, Visual Studio 2019 (ve daha yeni güncelleştirmelerde Visual Studio 2017) **PreBuildEvent** ve **PostBuildEvent** ayarları için `PreBuild` veya `PostBuild` adlı bir MSBuild hedefi ekler. Bu hedefler, MSBuild 'in tanıdığı **BeforeTargets** ve **AfterTargets** özniteliklerini kullanır. Örneğin, önceki örnekte, Visual Studio artık aşağıdaki kodu oluşturuyor:

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>
```

Oluşturma sonrası bir olay için `PostBuild` adını kullanın ve öznitelik `AfterTargets` `PostBuildEvent`olarak ayarlayın.

```xml
<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
> Bu proje dosyası değişiklikleri SDK stili projelerini desteklemek için yapılmıştır. Eski biçimden bir proje dosyasını SDK stili biçimine el ile geçiriyorsanız, `PreBuildEvent` ve `PostBuildEvent` özelliklerini silip önceki kodda gösterildiği gibi `PreBuild` ve `PostBuild` hedeflerle değiştirmelisiniz. Projenizin SDK stili bir proje olup olmadığını nasıl söyleyeceğinizi öğrenmek için bkz. [Proje biçimini denetle](/nuget/resources/check-project-format).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Derleme Olayları Belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Nasıl Yapılır: Derleme Olayları Belirtme (C#)](../../ide/how-to-specify-build-events-csharp.md)
- [Proje Özellikleri Başvurusu](../../ide/reference/project-properties-reference.md)
- [Derleme ve Oluşturma](../../ide/compiling-and-building-in-visual-studio.md)