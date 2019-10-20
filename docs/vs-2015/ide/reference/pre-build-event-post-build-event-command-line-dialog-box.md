---
title: Oluşturma öncesi olay-oluşturma sonrası olay komut satırı Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b42c219620a669a8fa27a7ce847dc571a4075288
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662161"
---
# <a name="pre-build-eventpost-build-event-command-line-dialog-box"></a>Oluşturma Öncesi Olay/Oluşturma Sonrası Olay Komut Satırı İletişim Kutusu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[Derleme olayları sayfası, proje TasarımcısıC#()](../../ide/reference/build-events-page-project-designer-csharp.md) için doğrudan düzenleme kutusuna derleme öncesi veya sonrası olay yazabilir veya kullanılabilir makrolar listesinden ön ve derleme sonrası makrolar seçebilirsiniz.

> [!NOTE]
> Proje güncel değilse ve derleme tetikleniyorsa, ön derleme olayları çalışmaz.

## <a name="ui-element-list"></a>UI öğe listesi
 **Komut satırı düzenleme kutusu** Oluşturma öncesi ya da derleme sonrası için çalıştırılacak olayları içerir.

> [!NOTE]
> . Bat dosyalarını çalıştıran tüm derleme sonrası komutları önüne bir `call` ekstresi ekleyin. Örneğin, `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat`.

 **Makrolar** Komut satırı düzenleme kutusuna eklenecek makroların listesini göstermek için düzenleme kutusunu genişletir.

 **Makro tablosu** Kullanılabilir makroları ve değerini listeler. Her birinin açıklaması için aşağıdaki makroları inceleyin. Komut satırı düzenleme kutusuna eklemek için tek seferde yalnızca bir makro seçebilirsiniz.

 **Ekle** Makro tablosunda seçilen makro komut satırı düzenleme kutusuna ekler.

### <a name="macros"></a>Makrolar
 Bu makroların herhangi birini dosya konumları belirtmek için veya birden çok seçim durumunda giriş dosyasının gerçek adını almak için kullanabilirsiniz. Bu makrolar büyük/küçük harfe duyarlı değildir.

|Makroya|Açıklama|
|-----------|-----------------|
|`$(ConfigurationName)`|Geçerli proje yapılandırmasının adı, örneğin "Debug".|
|`$(OutDir)`|Proje dizinine göre çıkış dosyası dizininin yolu. Bu, çıkış dizini özelliğinin değerini çözümler. Sondaki ters eğik çizgi ' \\ ' içerir.|
|`$(DevEnvDir)`|Visual Studio yükleme dizini (sürücü ve yol ile tanımlanır); Sondaki ters eğik çizgi ' \\ ' içerir.|
|`$(PlatformName)`|Şu anda hedeflenen platformun adı. Örneğin, "AnyCPU".|
|`$(ProjectDir)`|Projenin dizini (sürücü ve yol ile tanımlanır); Sondaki ters eğik çizgi ' \\ ' içerir.|
|`$(ProjectPath)`|Projenin mutlak yol adı (sürücü, yol, taban adı ve dosya uzantısıyla tanımlanır).|
|`$(ProjectName)`|Projenin temel adı.|
|`$(ProjectFileName)`|Projenin dosya adı (taban adı ve dosya uzantısıyla tanımlanır).|
|`$(ProjectExt)`|Projenin dosya uzantısı. Dosya uzantısından önce '. ' içerir.|
|`$(SolutionDir)`|Çözümün dizini (sürücü ve yol ile tanımlanır); Sondaki ters eğik çizgi ' \\ ' içerir.|
|`$(SolutionPath)`|Çözümün mutlak yol adı (sürücü, yol, taban adı ve dosya uzantısıyla tanımlanır).|
|`$(SolutionName)`|Çözümün temel adı.|
|`$(SolutionFileName)`|Çözümün dosya adı (taban adı ve dosya uzantısıyla tanımlanır).|
|`$(SolutionExt)`|Çözümün dosya uzantısı. Dosya uzantısından önce '. ' içerir.|
|`$(TargetDir)`|Derleme için birincil çıkış dosyasının dizini (sürücü ve yol ile tanımlanır). Sondaki ters eğik çizgi ' \\ ' içerir.|
|`$(TargetPath)`|Derleme için birincil çıkış dosyasının mutlak yol adı (sürücü, yol, taban adı ve dosya uzantısıyla tanımlanır).|
|`$(TargetName)`|Derleme için birincil çıkış dosyasının temel adı.|
|`$(TargetFileName)`|Derleme için birincil çıkış dosyasının dosya adı (temel ad ve dosya uzantısı olarak tanımlanır).|
|`$(TargetExt)`|Derleme için birincil çıkış dosyasının dosya uzantısı. Dosya uzantısından önce '. ' içerir.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio derleme olayları sayfasında özel derleme olaylarını belirtme](../../ide/specifying-custom-build-events-in-visual-studio.md) [, proje Tasarımcısı (C#)](../../ide/reference/build-events-page-project-designer-csharp.md) [nasıl yapılır: derleme olaylarını belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md) [nasıl yapılır: derleme olaylarını belirtme (C#)](../../ide/how-to-specify-build-events-csharp.md)
