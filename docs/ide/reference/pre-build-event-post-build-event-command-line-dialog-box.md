---
title: Derleme Öncesi Olay-Derleme Sonrası Olay Komut Satırı İletişim Kutusu
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEventsBuilder
- vb.ProjectPropertiesBuildEventsBuilder
helpviewer_keywords:
- $(SolutionExt)
- $(ProjectDir)
- $(TargetPath)
- $(ProjectExt)
- $(TargetFileName)
- $(PlatformName)
- $(SolutionName)
- macros, build events
- $(SolutionPath)
- $(ProjectPath)
- $(ProjectFileName)
- $(DevEnvDir)
- $(TargetName)
- $(TargetDir)
- $(SolutionDir)
- $(TargetExt)
- $(OutDir)
- $(ConfigurationName)
- $(SolutionFileName)
- $(ProjectName)
- build events, macros
ms.assetid: d49b2c57-24bf-4fb2-8351-5c4b6cca938f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38712c25718670ea15324e3daf6fadc138cb08a6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567924"
---
# <a name="pre-build-eventpost-build-event-command-line-dialog-box"></a>Önceden oluşturma olayı/post-build olay komut satırı iletişim kutusu

[Yapı Olayları Sayfası, Proje Tasarımcısı (C#)](../../ide/reference/build-events-page-project-designer-csharp.md) için yapı öncesi veya sonrası olayları doğrudan edit kutusuna yazabilir veya kullanılabilir makrolar listesinden yapı öncesi ve sonrası makroları seçebilirsiniz.

> [!NOTE]
> Proje güncelse ve hiçbir yapı tetiklenmiyorsa, önceden yapı olayları çalışmaz.

## <a name="ui-element-list"></a>UI Öğe Listesi

**Komut satırı düzenkutusu**

Önceden inşa veya post-build için çalışacak olayları içerir.

> [!NOTE]
> .bat `call` dosyalarını çalıştıran tüm yapı sonrası komutlardan önce bir deyim ekleyin. Örneğin `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat` olabilir.

**Makrolar**

Komut satırı düzenkutusuna eklemek için makroların listesini görüntülemek için düzen kutusunu genişletir.

**Makro tablosu**

Kullanılabilir makroları ve değerini listeler. Her birinin açıklaması için aşağıdaki Makrolar'a bakın. Komut satırı düzenkutusuna eklemek için aynı anda yalnızca bir makro seçebilirsiniz.

**Ekle**

Makro tablosunda seçilen makroyu komut satırı düzenkutusuna ekler.

### <a name="macros"></a>Makrolar

Bu makrolardan herhangi birini, dosyaların konumlarını belirtmek veya birden çok seçim durumunda giriş dosyasının gerçek adını almak için kullanabilirsiniz. Bu makrolar büyük/küçük harf duyarlı değildir.

|Makro|Açıklama|
|-----------|-----------------|
|`$(ConfigurationName)`|Geçerli proje yapılandırmasının adı, örneğin, "Hata Ayıklama".|
|`$(OutDir)`|Proje dizinine göre çıktı dosyası dizinine giden yol. Bu, Çıktı Dizini özelliğinin değerine gider. Bu sondalı backslash\\'içerir.|
|`$(DevEnvDir)`|Visual Studio'nun kurulum dizini (sürücü ve yol ile tanımlanır); '' '.\\|
|`$(PlatformName)`|Şu anda hedeflenen platformun adı. Örneğin, "AnyCPU".|
|`$(ProjectDir)`|Projenin dizini (sürücü ve yol ile tanımlanır); '' '.\\|
|`$(ProjectPath)`|Projenin mutlak yol adı (sürücü, yol, temel ad ve dosya uzantısı ile tanımlanır).|
|`$(ProjectName)`|Projenin temel adı.|
|`$(ProjectFileName)`|Projenin dosya adı (temel ad ve dosya uzantısı ile tanımlanır).|
|`$(ProjectExt)`|Projenin dosya uzantısı. Dosya uzantısından önce '.' içerir.|
|`$(SolutionDir)`|Çözümün dizini (sürücü ve yol ile tanımlanır); '' '.\\|
|`$(SolutionPath)`|Çözümün mutlak yol adı (sürücü, yol, temel ad ve dosya uzantısı ile tanımlanır).|
|`$(SolutionName)`|Çözümün temel adı.|
|`$(SolutionFileName)`|Çözümün dosya adı (temel ad ve dosya uzantısı ile tanımlanır).|
|`$(SolutionExt)`|Çözümün dosya uzantısı. Dosya uzantısından önce '.' içerir.|
|`$(TargetDir)`|Yapı için birincil çıktı dosyasının dizini (sürücü ve yol ile tanımlanır). Bu sondalı backslash\\'içerir.|
|`$(TargetPath)`|Yapı için birincil çıktı dosyasının mutlak yol adı (sürücü, yol, temel ad ve dosya uzantısı ile tanımlanır).|
|`$(TargetName)`|Yapı için birincil çıktı dosyasının temel adı.|
|`$(TargetFileName)`|Yapı için birincil çıktı dosyasının dosya adı (temel ad ve dosya uzantısı olarak tanımlanır).|
|`$(TargetExt)`|Yapı için birincil çıktı dosyasının dosya uzantısı. Dosya uzantısından önce '.' içerir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Özel Derleme Olayları Belirtme](../../ide/specifying-custom-build-events-in-visual-studio.md)
- [Derleme Olayları Sayfası, Proje Tasarımcısı (C#)](../../ide/reference/build-events-page-project-designer-csharp.md)
- [Nasıl Yapılır: Yapı Olaylarını Belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Nasıl Yapılır: Yapı Olaylarını Belirtme (C#)](../../ide/how-to-specify-build-events-csharp.md)
