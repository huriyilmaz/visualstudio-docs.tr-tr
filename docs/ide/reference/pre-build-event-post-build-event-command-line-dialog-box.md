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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 594d885228de68ecf34e0644cbbe6c6899397fad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85419204"
---
# <a name="pre-build-eventpost-build-event-command-line-dialog-box"></a>Oluşturma öncesi olay/oluşturma sonrası olay komut satırı iletişim kutusu

[Derleme olayları sayfası, proje Tasarımcısı (C#)](../../ide/reference/build-events-page-project-designer-csharp.md) için doğrudan düzenleme kutusuna derleme öncesi veya sonrası olayları yazabilir veya kullanılabilir makrolar listesinden ön ve derleme sonrası makroları seçebilirsiniz.

> [!NOTE]
> Proje güncel değilse ve derleme tetikleniyorsa, ön derleme olayları çalışmaz.

## <a name="ui-element-list"></a>UI Öğe Listesi

**Komut satırı düzenleme kutusu**

Oluşturma öncesi ya da derleme sonrası için çalıştırılacak olayları içerir.

> [!NOTE]
> `call`. Bat dosyalarını çalıştıran tüm derleme sonrası komutlarının önüne bir ifade ekleyin. Örneğin `call C:\MyFile.bat` veya `call C:\MyFile.bat call C:\MyFile2.bat` olabilir.

**Makrolar**

Komut satırı düzenleme kutusuna eklenecek makroların listesini göstermek için düzenleme kutusunu genişletir.

**Makro tablosu**

Kullanılabilir makroları ve değerini listeler. Her birinin açıklaması için aşağıdaki makroları inceleyin. Komut satırı düzenleme kutusuna eklemek için tek seferde yalnızca bir makro seçebilirsiniz.

**Ekle**

Makro tablosunda seçilen makro komut satırı düzenleme kutusuna ekler.

### <a name="macros"></a>Makrolar

Bu makroların herhangi birini dosya konumları belirtmek için veya birden çok seçim durumunda giriş dosyasının gerçek adını almak için kullanabilirsiniz. Bu makrolar büyük/küçük harfe duyarlı değildir.

|Makroya|Description|
|-----------|-----------------|
|`$(ConfigurationName)`|Geçerli proje yapılandırmasının adı, örneğin "Debug".|
|`$(OutDir)`|Proje dizinine göre çıkış dosyası dizininin yolu. Bu, çıkış dizini özelliğinin değerini çözümler. ' ' Sonunda ters eğik çizgi içeriyor \\ .|
|`$(DevEnvDir)`|Visual Studio yükleme dizini (sürücü ve yol ile tanımlanır); ' ' sonunda ters eğik çizgi içerir \\ .|
|`$(PlatformName)`|Şu anda hedeflenen platformun adı. Örneğin, "AnyCPU".|
|`$(ProjectDir)`|Projenin dizini (sürücü ve yol ile tanımlanır); ' ' sonunda ters eğik çizgi içerir \\ .|
|`$(ProjectPath)`|Projenin mutlak yol adı (sürücü, yol, taban adı ve dosya uzantısıyla tanımlanır).|
|`$(ProjectName)`|Projenin temel adı.|
|`$(ProjectFileName)`|Projenin dosya adı (taban adı ve dosya uzantısıyla tanımlanır).|
|`$(ProjectExt)`|Projenin dosya uzantısı. Dosya uzantısından önce '. ' içerir.|
|`$(SolutionDir)`|Çözümün dizini (sürücü ve yol ile tanımlanır); ' ' sonunda ters eğik çizgi içerir \\ .|
|`$(SolutionPath)`|Çözümün mutlak yol adı (sürücü, yol, taban adı ve dosya uzantısıyla tanımlanır).|
|`$(SolutionName)`|Çözümün temel adı.|
|`$(SolutionFileName)`|Çözümün dosya adı (taban adı ve dosya uzantısıyla tanımlanır).|
|`$(SolutionExt)`|Çözümün dosya uzantısı. Dosya uzantısından önce '. ' içerir.|
|`$(TargetDir)`|Derleme için birincil çıkış dosyasının dizini (sürücü ve yol ile tanımlanır). ' ' Sonunda ters eğik çizgi içeriyor \\ .|
|`$(TargetPath)`|Derleme için birincil çıkış dosyasının mutlak yol adı (sürücü, yol, taban adı ve dosya uzantısıyla tanımlanır).|
|`$(TargetName)`|Derleme için birincil çıkış dosyasının temel adı.|
|`$(TargetFileName)`|Derleme için birincil çıkış dosyasının dosya adı (temel ad ve dosya uzantısı olarak tanımlanır).|
|`$(TargetExt)`|Derleme için birincil çıkış dosyasının dosya uzantısı. Dosya uzantısından önce '. ' içerir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Özel Derleme Olayları Belirtme](../../ide/specifying-custom-build-events-in-visual-studio.md)
- [Derleme Olayları Sayfası, Proje Tasarımcısı (C#)](../../ide/reference/build-events-page-project-designer-csharp.md)
- [Nasıl Yapılır: Yapı Olaylarını Belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Nasıl Yapılır: Yapı Olaylarını Belirtme (C#)](../../ide/how-to-specify-build-events-csharp.md)
