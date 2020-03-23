---
title: Visual Studio’yu onarın
titleSuffix: ''
description: Visual Studio 2017 kurulumunu nasıl onarın
ms.date: 07/31/2019
ms.custom: seodec18
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 368ca6619a2fcff48cc3bcc7eb70913247b631b2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114741"
---
# <a name="repair-visual-studio"></a>Visual Studio’yu onarın

::: moniker range="vs-2017"

Bazen Visual Studio yüklemeniz zarar görür veya bozulur. Bir onarım bunu düzeltebilir.

1. Bilgisayarınızda **Visual Studio Yükleyicisini** bulun.

     Örneğin, Windows 10 Anniversary Update veya daha sonra çalıştıran bir bilgisayarda **Başlat'ı**seçin ve ardından **Visual Studio Installer**olarak listelenen **V**harfine gidin.

   > [!NOTE]
   > Bazı bilgisayarlarda, Visual Studio Installer **Microsoft Visual Studio Installer**olarak **"M"** harfi altında listelenmiş olabilir.
   >
   > Alternatif olarak, Visual Studio Yükleyicisini aşağıdaki konumda bulabilirsiniz:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Yükleyiciyi açın, **Daha Fazla**'yi seçin ve sonra **Onarım'ı**seçin.

    ![Visual Studio Installer'dan Visual Studio'yu Tamir Edin](media/repair-visual-studio.png "Visual Studio Installer'dan Visual Studio'yu Tamir Edin")

   > [!NOTE]
   > Visual Studio'yu onarmak ortamı sıfırlar. Yükseklik olmadan yüklenen kullanıcı başına uzantılar, kullanıcı ayarları ve profiller gibi yerel özelleştirmeler kaldırılır. Temalar, renkler, anahtar bağlamaları gibi senkronize ayarlarınız geri yüklenir.
   >

   > [!TIP]
   > **Onarım** seçeneği yalnızca Visual Studio'nun yüklü örnekleri için görüntülenir. **Onarım** seçeneğini görmüyorsanız, Visual Studio Installer'da listelenen bir sürümde **"Yüklü"** yerine "Kullanılabilir" olarak daha fazlasını seçmiş olma olasılığınız yüksektir.

::: moniker-end

::: moniker range="vs-2019"

1. Bilgisayarınızda Visual Studio Yükleyicisini bulun.

     Örneğin, Windows 10 çalıştıran bir bilgisayarda **Başlat'ı**seçin ve ardından Visual **Studio Installer**olarak listelenen **V**harfine gidin.

     ![Visual Studio Yükleyicisini Açın](media/vs-2019/vs-installer-windows-start.png "Visual Studio Yükleyicisini Açın")

     > [!NOTE]
     > Visual Studio Yükleyicisini aşağıdaki konumda da bulabilirsiniz:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Öyleyse, istemleri izleyin.

1. Yükleyicide, yüklediğiniz Visual Studio sürümünü arayın. Ardından, **Daha fazla**seçin ve sonra **Onarım**seçin.

     ![Onarım Görsel Stüdyo 2019](media/vs-2019/vs-installer-repair.png "Onarım Görsel Stüdyo 2019")

   > [!NOTE]
   > Visual Studio'yu onarmak ortamı sıfırlar. Yükseklik olmadan yüklenen kullanıcı başına uzantılar, kullanıcı ayarları ve profiller gibi yerel özelleştirmeler kaldırılır. Temalar, renkler, anahtar bağlamaları gibi senkronize ayarlarınız geri yüklenir.
   >

   > [!TIP]
   > **Onarım** seçeneği yalnızca Visual Studio'nun yüklü örnekleri için görüntülenir. **Onarım** seçeneğini görmüyorsanız, Visual Studio Installer'da listelenen bir sürümde **"Yüklü"** yerine "Kullanılabilir" olarak daha fazlasını seçmiş olma olasılığınız yüksektir.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio yükleme](install-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
* [Sorun Giderme Visual Studio yükleme ve yükseltme sorunları](troubleshooting-installation-issues.md)
