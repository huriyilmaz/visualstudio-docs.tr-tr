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
ms.openlocfilehash: 1e90a1d9e03892cf81bd2257d3dcc6e25ab36246
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89323651"
---
Visual Studio makinesi yerine hata ayıklamak istediğiniz uzak cihazda veya sunucuda, aşağıdaki tablodaki bağlantılardan uzak araçların doğru sürümünü indirip yükleyin.

- Visual Studio sürümünüz için en son uzak araçları indirin. En son uzak Araçlar sürümü, önceki Visual Studio sürümleriyle uyumludur, ancak önceki uzak Araçlar sürümleri daha sonra Visual Studio sürümleriyle uyumlu değildir. (Örneğin, Visual Studio 2017 kullanıyorsanız, Visual Studio 2017 için uzak araçların en son güncelleştirmesini indirin. Bu senaryoda, Visual Studio 2019 için uzak araçları indirmeyin.)
- Yüklediğiniz makineyle aynı mimariye sahip uzak araçları indirin. Örneğin, 64-bit işletim sistemi çalıştıran uzak bir bilgisayarda 32 bitlik bir uygulamada hata ayıklamak istiyorsanız, 64 bit uzak araçları ' nı yükleyebilirsiniz.

::: moniker range=">=vs-2019"

|Sürüm|Bağlantı|Notlar|
|-|-|-|
|Visual Studio 2019|[Uzak araçlar](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019)|Tüm Visual Studio 2019 sürümleriyle uyumludur. Cihazınızın işletim sistemi (x86, x64 veya ARM64) ile eşleşen sürümü indirin. Windows Server 'da, uzak araçları indirme konusunda yardım için bkz. [Dosya Indirme engelini kaldırma](../../debugger/remote-debugging-unblock-file-download.md) .|
|Visual Studio 2017|[Uzak araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Tüm Visual Studio 2017 sürümleriyle uyumludur. Cihazınızın işletim sistemi (x86, x64 veya ARM64) ile eşleşen sürümü indirin. Windows Server 'da, uzak araçları indirme konusunda yardım için bkz. [Dosya Indirme engelini kaldırma](../../debugger/remote-debugging-unblock-file-download.md) .|
|Visual Studio 2015|[Uzak araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Visual Studio 2015 için uzak Araçlar, My.VisualStudio.com adresinden edinilebilir. İstenirse, ücretsiz [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) programına katılarak veya Visual STUDIO abonelik Kimliğinizle oturum açın. Windows Server 'da, uzak araçları indirme konusunda yardım için bkz. [Dosya Indirme engelini kaldırma](../../debugger/remote-debugging-unblock-file-download.md) .|
|Visual Studio 2013|[Uzak araçlar](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Visual Studio 2013 belgelerine indirme sayfası|
|Visual Studio 2012|[Uzak araçlar](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Visual Studio 2012 belgelerinde karşıdan yükleme sayfası|

::: moniker-end

::: moniker range="vs-2017"

|Sürüm|Bağlantı|Notlar|
|-|-|-|
|Visual Studio 2017|[Uzak araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Tüm Visual Studio 2017 sürümleriyle uyumludur. Cihazınızın işletim sistemi (x86, x64 veya ARM64) ile eşleşen sürümü indirin. Windows Server 'da, uzak araçları indirme konusunda yardım için bkz. [Dosya Indirme engelini kaldırma](../../debugger/remote-debugging-unblock-file-download.md) . Uzak araçların en son sürümü için [Visual Studio 2019 belgesini](../../debugger/remote-debugging.md?view=vs-2019)açın.|
|Visual Studio 2015|[Uzak araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Visual Studio 2015 için uzak Araçlar, My.VisualStudio.com adresinden edinilebilir. İstenirse, ücretsiz [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) programına katılarak veya Visual STUDIO abonelik Kimliğinizle oturum açın. Windows Server 'da, uzak araçları indirme konusunda yardım için bkz. [Dosya Indirme engelini kaldırma](../../debugger/remote-debugging-unblock-file-download.md) .|
|Visual Studio 2013|[Uzak araçlar](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Visual Studio 2013 belgelerine indirme sayfası|
|Visual Studio 2012|[Uzak araçlar](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Visual Studio 2012 belgelerinde karşıdan yükleme sayfası|

::: moniker-end

Uzak araçları yüklemek yerine *msvsmon.exe* uzak bilgisayara kopyalayarak uzaktan hata ayıklayıcıyı çalıştırabilirsiniz. Ancak, uzaktan hata ayıklayıcı yapılandırma Sihirbazı (*rdbgwiz.exe*) yalnızca uzak araçları yüklediğinizde kullanılabilir. Uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırmak istiyorsanız, yapılandırma için sihirbazı kullanmanız gerekebilir. Daha fazla bilgi için, bkz. [(Isteğe bağlı) uzaktan hata ayıklayıcıyı bir hizmet olarak yapılandırma](../../debugger/remote-debugging.md#bkmk_configureService).

>[!NOTE]
>- ARM cihazlarda Windows 10 uygulamalarında hata ayıklamak için, uzak araçların en son sürümüyle kullanılabilen ARM64 kullanın.
>- Windows RT cihazlarında Windows 10 uygulamalarında hata ayıklamak için, yalnızca Visual Studio 2015 uzak Araçlar indirme sürümünde bulunan ARM 'yi kullanın.
