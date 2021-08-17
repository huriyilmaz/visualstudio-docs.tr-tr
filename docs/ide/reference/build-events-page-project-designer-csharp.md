---
title: Derleme Olayları Sayfası, Proje Tasarımcısı (C#)
description: Yapı yapılandırma yönergelerini belirtmeyi öğrenin. Ayrıca, herhangi bir oluşturma sonrası olayının çalıştırıldığı koşulları belirtebilirsiniz.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 54d84e792a9cb2833b34191f0760606a9b61eed5f1eac731f6a79a3efd1a86cd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121430921"
---
# <a name="build-events-page-project-designer-c"></a>Derleme Olayları Sayfası, Proje Tasarımcısı (C#)

yapı yapılandırma yönergelerini belirtmek için **Project tasarımcısı** 'nın **olayları oluştur** sayfasını kullanın. Ayrıca, herhangi bir oluşturma sonrası olayının çalıştırıldığı koşulları belirtebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: derleme olayları belirtme (C#)](../../ide/how-to-specify-build-events-csharp.md) ve [nasıl yapılır: derleme olaylarını belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

## <a name="uielement-list"></a>UIElement Listesi

**Yapılandırma**

Bu denetim bu sayfada düzenlenebilir değildir. bu denetimin açıklaması için bkz. [derleme sayfası, Project tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Platform**

Bu denetim bu sayfada düzenlenemez. bu denetimin açıklaması için bkz. [derleme sayfası, Project tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Oluşturma öncesi olay komut satırı**

Yapı başlamadan önce yürütülecek komutları belirtir. Uzun komutları yazmak için, oluşturma öncesi [olay/oluşturma sonrası olay komut satırı Iletişim kutusunu](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)göstermek Için **derleme ön yapısını Düzenle** ' ye tıklayın.

> [!NOTE]
> Proje güncel değilse ve derleme tetikleniyorsa, ön derleme olayları çalışmaz.

**Oluşturma sonrası olay komut satırı**

Yapı bittikten sonra yürütülecek komutları belirtir. Uzun komutları yazmak için derleme sonrası **olay/oluşturma sonrası olay komut satırı Iletişim kutusunu** göstermek üzere **derlemeyi Düzenle** ' ye tıklayın.

> [!NOTE]
> `call`.bat dosyaları çalıştıran tüm derleme sonrası komutlarınız önüne bir ifade ekleyin. Örneğin `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat` olabilir.

**Oluşturma sonrası olayını Çalıştır**

Aşağıdaki tabloda gösterildiği gibi, oluşturma sonrası olayının çalışması için aşağıdaki koşulları belirtir.

|Seçenek|Sonuç|
|------------|------------|
|**Her zaman**|Oluşturma sonrası olay, yapılandırmanın başarılı olup olmamasına bakılmaksızın çalışacaktır.|
|**Başarılı derleme üzerinde**|Oluşturma sonrası olay, derleme başarılı olursa çalışır. Bu nedenle, derleme başarılı olduğu sürece olay, güncel olan bir proje için de çalışır.|
|**Derleme proje çıkışını güncelleştirdiğinde**|Oluşturma sonrası olay, yalnızca derleyicinin çıkış dosyası (.exe veya .dll) önceki derleyici çıkış dosyasından farklı olduğunda çalıştırılır. Bu nedenle, bir proje güncel ise, derleme sonrası bir olay çalıştırılmaz.|

## <a name="in-the-project-file"></a>Proje dosyasında

Visual Studio önceki sürümlerinde, ıde 'deki **PreBuildEvent** veya **PostBuildEvent** ayarını değiştirdiğinizde Visual Studio `PreBuildEvent` `PostBuildEvent` proje dosyasına bir veya özelliği ekler. Örneğin, IDE 'deki **PreBuildEvent** komut satırı ayarınız aşağıdaki gibidir:

```input
"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"
```

ardından proje dosyası ayarı:

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

.net Core projeleri için, Visual Studio 2019 (ve daha son güncelleştirmelerde Visual Studio 2017), `PreBuild` `PostBuild` **PreBuildEvent** ve **PostBuildEvent** ayarları için veya adında bir MSBuild hedefi ekler. bu hedefler, MSBuild algıladığı **beforetargets** ve **aftertargets** özniteliklerini kullanır. örneğin, yukarıdaki örnek için Visual Studio şimdi aşağıdaki kodu üretir:

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>
```

Oluşturma sonrası bir olay için, adını kullanın `PostBuild` ve özniteliğini `AfterTargets` olarak ayarlayın `PostBuildEvent` .

```xml
<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
> Bu proje dosyası değişiklikleri SDK stili projelerini desteklemek için yapılmıştır. Eski biçimden bir proje dosyasını SDK stili biçimine el ile geçiriyorsanız, `PreBuildEvent` ve `PostBuildEvent` özelliklerini silmeniz ve `PreBuild` `PostBuild` Önceki kodda gösterildiği gibi bunları ve hedefleri ile değiştirmeniz gerekir. Projenizin SDK stili bir proje olup olmadığını nasıl söyleyeceğinizi öğrenmek için bkz. [Proje biçimini denetle](/nuget/resources/check-project-format).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Yapı Olaylarını Belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Nasıl Yapılır: Yapı Olaylarını Belirtme (C#)](../../ide/how-to-specify-build-events-csharp.md)
- [Proje Özellikleri Başvurusu](../../ide/reference/project-properties-reference.md)
- [Derleme ve Oluşturma](../../ide/compiling-and-building-in-visual-studio.md)
