---
title: Uzaktan hata ayıklayıcı indirme
description: Uzaktan hata ayıklayıcı bağlantılarını indirme
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 09/10/2021
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: e000a1d36ffa1e653511fb4f6a53f2d29e763d46
ms.sourcegitcommit: 72f8ce4992cc62c4833e6dcb0f79febb328c44be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2021
ms.locfileid: "130016035"
---
Hata ayıklamak istediğiniz uzak cihazda veya sunucuda, Visual Studio makinesi yerine aşağıdaki tabloda yer alan bağlantılardan uzak araçların doğru sürümünü indirip yükleyin.

- Uygulama sürümünüz için en son uzak araçları Visual Studio. En son uzak araçlar sürümü önceki uzak Visual Studio sürümleriyle uyumludur, ancak önceki uzak araçlar sonraki sürümlerle Visual Studio değildir. (Örneğin, Visual Studio 2017 kullanıyorsanız, Visual Studio 2017 için uzak araçların en son güncelleştirmesini indirin. Bu senaryoda, Visual Studio 2019 için uzak araçları indirmeyebilirsiniz.)
- Yüklemekte olduğu makineyle aynı mimariye sahip uzak araçları indirin. Örneğin, 64 bit işletim sistemi çalıştıran uzak bir bilgisayarda 32 bit uygulamada hata ayıklamak için 64 bit uzak araçları yükleyin.

::: moniker range=">=vs-2022"

|Sürüm|Bağlantı|Notlar|
|-|-|-|
|Visual Studio 2022 RC|[Önizleme için uzak araçlar](https://visualstudio.microsoft.com/vs/preview/)|Tüm 2022 Visual Studio ile uyumludur. Cihaz işletim sisteminize (x86, x64 veya ARM64) uyan sürümü indirin. Windows Server'da uzak [araçları indirme yardımı için](../../debugger/remote-debugging-unblock-file-download.md) bkz. Dosya indirme engelini kaldırma.|
|Visual Studio 2019|[Uzak araçlar](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019)|Tüm 2019 Visual Studio ile uyumludur. Cihaz işletim sisteminize (x86, x64 veya ARM64) uyan sürümü indirin. Windows Server'da uzak [araçları indirme yardımı için](../../debugger/remote-debugging-unblock-file-download.md) bkz. Dosya indirme engelini kaldırma.|
|Visual Studio 2017|[Uzak araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Tüm 2017 Visual Studio ile uyumludur. Cihaz işletim sisteminize (x86, x64 veya ARM64) uyan sürümü indirin. Windows Server'da uzak [araçları indirme yardımı için](../../debugger/remote-debugging-unblock-file-download.md) bkz. Dosya indirme engelini kaldırma.|
|Visual Studio 2015|[Uzak araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Visual Studio 2015 için uzak araçlar My.VisualStudio.com. İstendiğinde ücretsiz [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) katılın veya abonelik kimliğiniz Visual Studio oturum açın. Windows Server'da uzak [araçları indirme yardımı için](../../debugger/remote-debugging-unblock-file-download.md) bkz. Dosya indirme engelini kaldırma.|
|Visual Studio 2013|[Uzak araçlar](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Visual Studio 2013 belgelerinde indirme sayfası|
|Visual Studio 2012|[Uzak araçlar](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Visual Studio 2012 belgelerinde indirme sayfası|

::: moniker-end
::: moniker range="vs-2019"

|Sürüm|Bağlantı|Notlar|
|-|-|-|
|Visual Studio 2019|[Uzak araçlar](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019)|Tüm 2019 Visual Studio ile uyumludur. Cihaz işletim sisteminize (x86, x64 veya ARM64) uyan sürümü indirin. Windows Server'da uzak [araçları indirme yardımı için](../../debugger/remote-debugging-unblock-file-download.md) bkz. Dosya indirme engelini kaldırma.|
|Visual Studio 2017|[Uzak araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Tüm 2017 Visual Studio ile uyumludur. Cihaz işletim sisteminize (x86, x64 veya ARM64) uyan sürümü indirin. Windows Server'da uzak [araçları indirme yardımı için](../../debugger/remote-debugging-unblock-file-download.md) bkz. Dosya indirme engelini kaldırma.|
|Visual Studio 2015|[Uzak araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Visual Studio 2015 için uzak araçlar My.VisualStudio.com. İstendiğinde ücretsiz [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) katılın veya abonelik kimliğiniz Visual Studio oturum açın. Windows Server'da uzak [araçları indirme yardımı için](../../debugger/remote-debugging-unblock-file-download.md) bkz. Dosya indirme engelini kaldırma.|
|Visual Studio 2013|[Uzak araçlar](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Visual Studio 2013 belgelerinde indirme sayfası|
|Visual Studio 2012|[Uzak araçlar](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Visual Studio 2012 belgelerinde indirme sayfası|

::: moniker-end

::: moniker range="vs-2017"

|Sürüm|Bağlantı|Notlar|
|-|-|-|
|Visual Studio 2017|[Uzak araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Tüm 2017 Visual Studio ile uyumludur. Cihaz işletim sisteminize (x86, x64 veya ARM64) uyan sürümü indirin. Windows Server'da uzak [araçları indirme yardımı için](../../debugger/remote-debugging-unblock-file-download.md) bkz. Dosya indirme engelini kaldırma. Uzak araçların en son sürümü için, [2019 Visual Studio açın.](../../debugger/remote-debugging.md?view=vs-2019&preserve-view=true)|
|Visual Studio 2015|[Uzak araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Visual Studio 2015 için uzak araçlar My.VisualStudio.com. İstendiğinde ücretsiz [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) katılın veya abonelik kimliğiniz Visual Studio oturum açın. Windows Server'da uzak [araçları indirme yardımı için](../../debugger/remote-debugging-unblock-file-download.md) bkz. Dosya indirme engelini kaldırma.|
|Visual Studio 2013|[Uzak araçlar](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Visual Studio 2013 belgelerinde indirme sayfası|
|Visual Studio 2012|[Uzak araçlar](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Visual Studio 2012 belgelerinde indirme sayfası|

::: moniker-end

Uzak hata ayıklayıcıyı uzak araçları *yüklemekmsvsmon.exe* uzak bilgisayara kopyalayıp çalıştırabilirsiniz. Ancak, Uzaktan Hata Ayıklayıcı Yapılandırma Sihirbazı (*rdbgwiz.exe*) yalnızca uzak araçları yükleyebilirsiniz. Uzak hata ayıklayıcısını bir hizmet olarak çalıştırmak için yapılandırma sihirbazını kullanabilirsiniz. Daha fazla bilgi için [bkz. (İsteğe bağlı) Uzaktan hata ayıklayıcıyı hizmet olarak yapılandırma.](../../debugger/remote-debugging.md#bkmk_configureService)

>[!NOTE]
>- ARM cihaz Windows 10 hata ayıklamak için uzak araçların en son sürümüyle birlikte kullanılabilen ARM64'ü kullanın.
>- Windows 10 cihazlardaki Windows RT ayıklamak için, yalnızca Visual Studio 2015 uzak araçları indirmesinde kullanılabilen ARM'i kullanın.
