---
title: Uzaktan hata ayıklayıcı indirme
description: Uzaktan hata ayıklayıcı için bağlantıları indirin
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: e207a3e52b61ca7da896a3c3531884c3e5a833d244815eb9b041d0009c5346be
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "122058334"
---
Visual Studio makine yerine, hata ayıklamak istediğiniz uzak cihazda veya sunucuda, aşağıdaki tablodaki bağlantılardan uzak araçların doğru sürümünü indirip yükleyin.

- Visual Studio sürümünüz için en son uzak araçları indirin. en son uzak araçlar sürümü önceki Visual Studio sürümlerle uyumludur, ancak önceki uzak araçlar sürümleri daha sonra Visual Studio sürümleriyle uyumlu değildir. (örneğin, Visual Studio 2017 kullanıyorsanız, Visual Studio 2017 için uzak araçların en son güncelleştirmesini indirin. bu senaryoda Visual Studio 2019 için uzak araçları indirmeyin.)
- Yüklediğiniz makineyle aynı mimariye sahip uzak araçları indirin. Örneğin, 64-bit işletim sistemi çalıştıran uzak bir bilgisayarda 32 bitlik bir uygulamada hata ayıklamak istiyorsanız, 64 bit uzak araçları ' nı yükleyebilirsiniz.

::: moniker range=">=vs-2019"

|Sürüm|Bağlantı|Notlar|
|-|-|-|
|Visual Studio 2019|[Uzak araçlar](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019)|tüm Visual Studio 2019 sürümleriyle uyumludur. Cihazınızın işletim sistemi (x86, x64 veya ARM64) ile eşleşen sürümü indirin. Windows sunucuda, uzak araçları indirme konusunda yardım için bkz. [dosya indirme engelini kaldırma](../../debugger/remote-debugging-unblock-file-download.md) .|
|Visual Studio 2017|[Uzak araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|tüm Visual Studio 2017 sürümleriyle uyumludur. Cihazınızın işletim sistemi (x86, x64 veya ARM64) ile eşleşen sürümü indirin. Windows sunucuda, uzak araçları indirme konusunda yardım için bkz. [dosya indirme engelini kaldırma](../../debugger/remote-debugging-unblock-file-download.md) .|
|Visual Studio 2015|[Uzak araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Visual Studio 2015 için uzak araçlar My.VisualStudio.com adresinden edinilebilir. istenirse, ücretsiz [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) programına katılarak veya Visual Studio abonelik kimliğinizle oturum açın. Windows sunucuda, uzak araçları indirme konusunda yardım için bkz. [dosya indirme engelini kaldırma](../../debugger/remote-debugging-unblock-file-download.md) .|
|Visual Studio 2013|[Uzak araçlar](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Visual Studio 2013 belgelerine indirme sayfası|
|Visual Studio 2012|[Uzak araçlar](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Visual Studio 2012 belgelerinde indirme sayfası|

::: moniker-end

::: moniker range="vs-2017"

|Sürüm|Bağlantı|Notlar|
|-|-|-|
|Visual Studio 2017|[Uzak araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|tüm Visual Studio 2017 sürümleriyle uyumludur. Cihazınızın işletim sistemi (x86, x64 veya ARM64) ile eşleşen sürümü indirin. Windows sunucuda, uzak araçları indirme konusunda yardım için bkz. [dosya indirme engelini kaldırma](../../debugger/remote-debugging-unblock-file-download.md) . uzak araçların en son sürümü için [Visual Studio 2019 belgesini](../../debugger/remote-debugging.md?view=vs-2019&preserve-view=true)açın.|
|Visual Studio 2015|[Uzak araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Visual Studio 2015 için uzak araçlar My.VisualStudio.com adresinden edinilebilir. istenirse, ücretsiz [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) programına katılarak veya Visual Studio abonelik kimliğinizle oturum açın. Windows sunucuda, uzak araçları indirme konusunda yardım için bkz. [dosya indirme engelini kaldırma](../../debugger/remote-debugging-unblock-file-download.md) .|
|Visual Studio 2013|[Uzak araçlar](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Visual Studio 2013 belgelerine indirme sayfası|
|Visual Studio 2012|[Uzak araçlar](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Visual Studio 2012 belgelerinde indirme sayfası|

::: moniker-end

Uzak araçları yüklemek yerine *msvsmon.exe* uzak bilgisayara kopyalayarak uzaktan hata ayıklayıcıyı çalıştırabilirsiniz. Ancak, uzaktan hata ayıklayıcı yapılandırma Sihirbazı (*rdbgwiz.exe*) yalnızca uzak araçları yüklediğinizde kullanılabilir. Uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırmak istiyorsanız, yapılandırma için sihirbazı kullanmanız gerekebilir. Daha fazla bilgi için, bkz. [(Isteğe bağlı) uzaktan hata ayıklayıcıyı bir hizmet olarak yapılandırma](../../debugger/remote-debugging.md#bkmk_configureService).

>[!NOTE]
>- ARM cihazlarında Windows 10 uygulamalarda hata ayıklamak için, uzak araçların en son sürümüyle kullanılabilen ARM64 kullanın.
>- Windows RT cihazlarda Windows 10 uygulamalarda hata ayıklamak için, yalnızca Visual Studio 2015 uzak araç indirme sürümünde bulunan ARM 'yi kullanın.
