---
title: Visual Studio'yu kaldırma
titleSuffix: ''
description: Visual Studio'u adım adım nasıl kaldırarak kaldırabilirsiniz öğrenin.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fd21f01f89cb4fe4507775670968496cbb5f99f5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115008"
---
# <a name="uninstall-visual-studio"></a>Visual Studio'yu kaldırma

Bu sayfa, geliştiriciler için entegre üretkenlik araç paketimiz olan Visual Studio'nun kurulumuna kadar size yol gösteriyor.

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio [için, Mac için Visual Studio'yı Kaldır'a](/visualstudio/mac/uninstall)bakın.

::: moniker range="vs-2017"

1. Bilgisayarınızda Visual Studio Yükleyicisini bulun.

     Örneğin, Windows 10 Anniversary Update veya daha sonra çalıştıran bir bilgisayarda **Başlat'ı** seçin ve **Visual Studio Installer**olarak listelendiği **V**harfine gidin.

     ![Visual Studio Yükleyicisi](media/locate-the-visual-studio-installer.png "Microsoft Visual Studio Yükleyicisini Bulun")

   > [!NOTE]
   > Bazı bilgisayarlarda, Visual Studio Installer **Microsoft Visual Studio Installer**olarak **"M"** harfi altında listelenmiş olabilir.<br/><br/> Alternatif olarak, Visual Studio Yükleyicisini aşağıdaki konumda bulabilirsiniz:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Yükleyicide, yüklediğiniz Visual Studio sürümünü arayın. Ardından, **Daha Fazla**'yi seçin ve ardından **Kaldır'ı**seçin.

     ![Visual Studio 2017'yi Kaldır](media/uninstall-visual-studio.png "Visual Studio 2017'yi Kaldır")

1. Seçiminizi onaylamak için **Tamam'ı** tıklatın.

Daha sonra fikrinizi değiştirir ve Visual Studio 2017'yi yeniden yüklemek isterseniz Visual Studio Installer'ı yeniden başlatın ve seçim ekranından **Yükle'yi** seçin.

## <a name="uninstall-visual-studio-installer"></a>Visual Studio Yükleyici'yi Kaldır

Visual Studio 2017 ve Visual Studio Installer'ın tüm kurulumlarını makinenizden tamamen kaldırmak için, Apps & Özellikler'den kaldırın.

1. Windows 10'da, **"Aramak** için buraya yazın" kutusuna Uygulamalar ve Özellikler yazın.
1. **Microsoft Visual Studio 2017'yi** bulun (veya Visual Studio **2017).**
1. **Kaldır'ı**seçin.
1. Ardından, **Microsoft Visual Studio Installer'ı**bulun.
1. **Kaldır'ı**seçin.

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

1. Yükleyicide, yüklediğiniz Visual Studio sürümünü arayın. Ardından, **Daha Fazla**'yi seçin ve ardından **Kaldır'ı**seçin.

     ![Visual Studio 2019'u Kaldır](media/vs-2019/vs-installer-uninstall.png "Visual Studio 2019'u Kaldır")

1. Seçiminizi onaylamak için **Tamam'ı** tıklatın.

     ![Visual Studio onayLarını kaldır](media/vs-2019/uninstall-visualstudio-confirm.png "Visual Studio 2019'u kaldırmak istediğinizi onaylayın")

Daha sonra fikrinizi değiştirir ve Visual Studio 2019'u yeniden yüklemek istiyorsanız Visual Studio Installer'ı yeniden başlatın, **Kullanılabilir** sekmesini seçin, yüklemek istediğiniz Visual Studio sürümünü seçin ve sonra **Yükle'yi**seçin.

## <a name="uninstall-visual-studio-installer"></a>Visual Studio Yükleyici'yi Kaldır

Visual Studio 2019 ve Visual Studio Installer'ın tüm kurulumlarını makinenizden kaldırmak için, Apps & Özellikler'den kaldırın.

1. Windows 10'da, **"Aramak** için buraya yazın" kutusuna Uygulamalar ve Özellikler yazın.
1. **Visual Studio 2019**bul .
1. **Kaldır'ı**seçin.
1. Ardından, **Microsoft Visual Studio Installer'ı**bulun.
1. **Kaldır'ı**seçin.

::: moniker-end

## <a name="remove-all-files"></a>Tüm dosyaları kaldırma

Felaket bir hatayla karşılaşırsanız ve önceki yönergeleri kullanarak Visual Studio'yu kaldıramıyorsanız, bunun yerine kullanmayı düşünebileceğiniz bir "son çare" seçeneği vardır. Tüm Visual Studio yükleme dosyalarını ve ürün bilgilerini tamamen nasıl kaldırabilirsiniz hakkında daha fazla bilgi için [Visual Studio'yu Kaldır](remove-visual-studio.md) sayfasına bakın.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio’yu değiştirme](modify-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
