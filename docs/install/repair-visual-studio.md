---
title: Visual Studio’yu onarın
titleSuffix: ''
description: Visual Studio 2017 yüklemesini onarmak hakkında bilgi edinin
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
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114741"
---
# <a name="repair-visual-studio"></a>Visual Studio’yu onarın

::: moniker range="vs-2017"

Bazı durumlarda Visual Studio yüklemenizin zarar görmüş veya bozulmuş olur. Bir onarım bunu düzeltebilirsiniz.

1. Bilgisayarınızda **Visual Studio yükleyicisi** bulun.

     Örneğin, Windows 10 Yıldönümü güncelleştirmesi bir bilgisayarda çalışan veya daha sonra **Başlat**ve harfi kaydırın **V**, olarak listelenen burada **Visual Studio yükleyicisi**.

   > [!NOTE]
   > Bazı bilgisayarlarda, Visual Studio yükleyicisi harfi altında listelenebilir **"M"** olarak **Microsoft Visual Studio yükleyicisi**.
   >
   > Alternatif olarak, Visual Studio yükleyicisi şu konumda bulabilirsiniz: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Yükleyiciyi açın, **daha fazla**' yı seçin ve ardından **Onar**' ı seçin.

    ![Visual Studio Yükleyicisi Visual Studio 'Yu onarın](media/repair-visual-studio.png "Visual Studio Yükleyicisi Visual Studio 'Yu onarın")

   > [!NOTE]
   > Visual Studio 'Yu onarmak ortamı sıfırlar. Yükselme, Kullanıcı ayarları ve profiller olmadan yüklenen Kullanıcı başına uzantılar gibi yerel özelleştirmeler kaldırılır. Temalar, renkler, anahtar bağlamaları gibi eşitlenmiş ayarlarınız geri yüklenecek.
   >

   > [!TIP]
   > **Onarma** seçeneği yalnızca Visual Studio 'nun yüklü örnekleri için görünür. **Onar** seçeneğini görmüyorsanız, Visual Studio yükleyicisi listelenen bir sürümde "yüklü" yerine "kullanılabilir" olarak **daha fazla** seçim yapmış olursunuz.

::: moniker-end

::: moniker range="vs-2019"

1. Bilgisayarınızda Visual Studio yükleyicisi bulun.

     Örneğin, Windows 10 çalıştıran bir bilgisayarda seçin **Başlat**ve harfi kaydırın **V**, olarak listelenen burada **Visual Studio yükleyicisi**.

     ![Visual Studio Yükleyicisi açın](media/vs-2019/vs-installer-windows-start.png "Visual Studio Yükleyicisi açın")

     > [!NOTE]
     > Aşağıdaki konumda Visual Studio Yükleyicisi de bulabilirsiniz:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Bu durumda, istemleri izleyin.

1. Yükleyicide, yüklediğiniz Visual Studio sürümünü arayın. Daha sonra, **daha fazla**' yı ve ardından **Onar**' ı seçin.

     ![Visual Studio 2019 'yi onarma](media/vs-2019/vs-installer-repair.png "Visual Studio 2019 'yi onarma")

   > [!NOTE]
   > Visual Studio 'Yu onarmak ortamı sıfırlar. Yükselme, Kullanıcı ayarları ve profiller olmadan yüklenen Kullanıcı başına uzantılar gibi yerel özelleştirmeler kaldırılır. Temalar, renkler, anahtar bağlamaları gibi eşitlenmiş ayarlarınız geri yüklenecek.
   >

   > [!TIP]
   > **Onarma** seçeneği yalnızca Visual Studio 'nun yüklü örnekleri için görünür. **Onar** seçeneğini görmüyorsanız, Visual Studio yükleyicisi listelenen bir sürümde "yüklü" yerine "kullanılabilir" olarak **daha fazla** seçim yapmış olursunuz.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleyin](install-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
* [Visual Studio yükleme ve yükseltme sorunlarını giderme](troubleshooting-installation-issues.md)
