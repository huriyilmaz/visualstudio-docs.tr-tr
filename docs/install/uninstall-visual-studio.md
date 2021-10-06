---
title: Visual Studio'yu kaldırma
titleSuffix: ''
description: Adım adım Visual Studio kaldırmayı öğrenin.
ms.date: 10/12/2020
ms.custom: seodec18
ms.topic: how-to
f1_keywords:
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: deed1f2f145888567679adacfd28b74a057a556c
ms.sourcegitcommit: d63ba1eff845d41ca095efb14b499ea96c4b6eba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "129561009"
---
# <a name="uninstall-visual-studio"></a>Visual Studio'yu kaldırma

Bu sayfa, geliştiriciler için tümleşik Visual Studio araç paketimiz olan uygulamanın kaldırılmasında size yol sunar.

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Mac için Visual Studio.](/visualstudio/mac/uninstall)

> [!TIP]
> Örnekle ilgili sorun Visual Studio Onarım **aracını** deneyin. Daha fazla bilgi için bkz. [Visual Studio.](../install/repair-visual-studio.md) 
>
> Bazı dosya dosyalarının konumunu değiştirmek Visual Studio, geçerli örneğinizi kaldırmadan bunu yapmak mümkündür. Daha fazla bilgi için, [bkz. Select the installation locations in Visual Studio](../install/change-installation-locations.md).
>
> Genel sorun giderme ipuçları için [bkz. Yükleme Visual Studio yükseltme sorunlarını giderme.](../install/troubleshooting-installation-issues.md)

::: moniker range="vs-2017"

1. Bilgisayarınızda Visual Studio Yükleyicisi'ı bulun.

     Örneğin, Yıldönümü Güncelleştirmesi veya Windows 10 çalıştıran bir bilgisayarda  Başlat'ı seçin ve **V** harfine kaydırın; burada bu harf **Visual Studio Yükleyicisi.**

     ![Visual Studio Yükleyicisi](media/locate-the-visual-studio-installer.png "Microsoft Visual Studio Yükleyicisini bulma")

   > [!NOTE]
   > Bazı bilgisayarlarda, Visual Studio Yükleyicisi yükleyicisi olarak **"M"** harfi altında **Microsoft Visual Studio olabilir.**<br/><br/> Alternatif olarak, Visual Studio Yükleyicisi aşağıdaki konumda bulabilirsiniz:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Yükleyicide, yüklü Visual Studio sürümünü ara. Ardından **Diğer'i ve** ardından Kaldır'ı **seçin.**

     ![2017'Visual Studio kaldırma](media/uninstall-visual-studio.png "2017'Visual Studio kaldırma")

1. Seçiminizi **onaylamak** için Tamam'a tıklayın.

Daha sonra fikirlerinizi değiştirir ve 2017'Visual Studio yüklemek Visual Studio Yükleyicisi yeniden başlatarak seçim  ekranından Yükle'yi seçin.

## <a name="uninstall-visual-studio-installer"></a>Kaldırma Visual Studio Yükleyicisi

Visual Studio 2017 ve Visual Studio Yükleyicisi yüklemelerini makineden tamamen kaldırmak için, & Özellikler'den kaldırın.

1. Bu Windows 10 veya sonraki bir sonraki bir **kutuya** "Aramak için buraya yazın" kutusuna Uygulamalar ve Özellikler yazın.
1. **2017 Microsoft Visual Studio** (veya **2017 Visual Studio) bulun.**
1. **Kaldır'ı seçin.**
1. Ardından, **yükleyiciyi Microsoft Visual Studio bulun.**
1. **Kaldır'ı seçin.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Bilgisayarınızda **Visual Studio Yükleyicisi'ı** bulun.

     Bu Windows Başlat menüsü "yükleyici" için arama da vesnesini arayabilirsiniz.

     ![Visual Studio Yükleyicisi](media/vs-2019/visual-studio-installer.png "Arama Visual Studio Yükleyicisi")

     > [!NOTE]
     > Aşağıdaki konumda Visual Studio Yükleyicisi da bulabilirsiniz:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekir. Öyleyse, istemleri izleyin.

1. Yükleyicide, yüklü Visual Studio sürümünü ara. Ardından **Diğer'i ve** ardından Kaldır'ı **seçin.**

     ![2019 Visual Studio kaldırma](media/vs-2019/vs-installer-uninstall.png "2019 Visual Studio kaldırma")

1. Seçiminizi **onaylamak** için Tamam'a tıklayın.

     ![Kaldırma Visual Studio onayı](media/vs-2019/uninstall-visualstudio-confirm.png "2019'da Visual Studio onaylayın")

Daha sonra fikirlerinizi değiştirir ve Visual Studio 2019 veya 2022'yi yeniden yüklemek için  Visual Studio Yükleyicisi'yi yeniden başlatmak, Kullanılabilir sekmesini seçin, yüklemek istediğiniz Visual Studio sürümünü seçin ve ardından Yükle'yi **seçin.**

## <a name="uninstall-visual-studio-installer"></a>Kaldırma Visual Studio Yükleyicisi

Visual Studio 2019, Visual Studio 2022 ve Visual Studio Yükleyicisi yüklemelerini makineden kaldırmak için, & Özellikler'den kaldırın.

1. Bu Windows 10 veya sonraki bir sonraki bir **kutuya** "Aramak için buraya yazın" kutusuna Uygulamalar ve Özellikler yazın.
1. **2019 Visual Studio 2022** **Visual Studio bulun.**
1. **Kaldır'ı seçin.**
1. Ardından, **yükleyiciyi Microsoft Visual Studio bulun.**
1. **Kaldır'ı seçin.**

::: moniker-end

## <a name="remove-all-files"></a>Tüm dosyaları kaldırma

Yıkıcı bir hatayla karşılaştınız ve önceki yönergeleri kullanarak Visual Studio kaldıramazsanız, bunun yerine kullanmayı düşünebilirsiniz "son seçenek" seçeneğiniz vardır. Tüm yükleme dosyalarını ve ürün bilgilerini tamamen Visual Studio hakkında daha fazla bilgi için [Bkz. Visual Studio](remove-visual-studio.md) kaldırma.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio’yu değiştirme](modify-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
