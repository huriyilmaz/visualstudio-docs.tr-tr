---
title: Visual Studio'yu kaldırma
titleSuffix: ''
description: Adım adım Visual Studio 'Yu nasıl kaldıracağınızı öğrenin.
ms.date: 10/12/2020
ms.custom: seodec18
ms.topic: how-to
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
ms.openlocfilehash: e924ead1b8796089242ef20c7f5a3070833b68ba
ms.sourcegitcommit: 172aaf05596a9d8ded298b7b104569c1cce6160e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92007151"
---
# <a name="uninstall-visual-studio"></a>Visual Studio'yu kaldırma

Bu sayfada, geliştiriciler için tümleşik üretkenlik araçları takımımız olan Visual Studio 'Yu kaldırma işlemi adım adım açıklanmaktadır.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Mac için Visual Studio kaldır](/visualstudio/mac/uninstall).

> [!TIP]
> Visual Studio örneğinizle ilgili sorun yaşıyorsanız **onarım** aracını deneyin. Daha fazla bilgi için bkz. [Visual Studio 'Yu onarma](../install/repair-visual-studio.md). 
>
> Visual Studio dosyalarınızın bir kısmının konumunu değiştirmek istiyorsanız, geçerli örneğinizi kaldırmadan bunu yapmak mümkündür. Daha fazla bilgi için bkz. [Visual Studio 'da yükleme konumlarını seçme](../install/change-installation-locations.md).
>
> Genel sorun giderme ipuçları için bkz. [Visual Studio yüklemesinde sorun giderme ve yükseltme sorunları](../install/troubleshooting-installation-issues.md).

::: moniker range="vs-2017"

1. Bilgisayarınızda Visual Studio Yükleyicisi bulun.

     Örneğin, Windows 10 yıldönümü güncelleştirmesi veya sonraki bir sürümünü çalıştıran bir bilgisayarda **Başlat** ' ı seçin ve **Visual Studio yükleyicisi**olarak listelendiği **V**harfine gidin.

     ![Visual Studio Yükleyicisi](media/locate-the-visual-studio-installer.png "Microsoft Visual Studio yükleyicisini bulun")

   > [!NOTE]
   > Bazı bilgisayarlarda Visual Studio Yükleyicisi, **Microsoft Visual Studio yükleyicisi**olarak **"d"** harfi altında listelenmiş olabilir.<br/><br/> Alternatif olarak, Visual Studio Yükleyicisi aşağıdaki konumda bulabilirsiniz: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Yükleyicide, yüklediğiniz Visual Studio sürümünü arayın. Daha sonra, **daha fazla**' yı ve ardından **Kaldır**' ı seçin.

     ![Visual Studio 2017 'yi kaldırma](media/uninstall-visual-studio.png "Visual Studio 2017 'yi kaldırma")

1. Seçiminizi onaylamak için **Tamam** ' ı tıklatın.

Daha sonra fikrinizi değiştirirseniz ve Visual Studio 2017 ' i yeniden yüklemek istiyorsanız, Visual Studio Yükleyicisi yeniden başlatın ve ardından seçim ekranından **Yükle** ' yi seçin.

## <a name="uninstall-visual-studio-installer"></a>Visual Studio Yükleyicisi kaldır

Visual Studio 2017 ve Visual Studio Yükleyicisi tüm yüklemelerini makinenizden tamamen kaldırmak için, uygulamalardan & özelliklerden kaldırın.

1. Windows 10 ' da, "aramak için buraya yazın" kutusuna **uygulamalar ve Özellikler** yazın.
1. **Microsoft Visual Studio 2017** (veya **Visual Studio 2017**) bulun.
1. **Kaldır**' ı seçin.
1. Ardından **Microsoft Visual Studio yükleyiciyi**bulun.
1. **Kaldır**' ı seçin.

::: moniker-end

::: moniker range="vs-2019"

1. Bilgisayarınızda **Visual Studio yükleyicisi** bulun.

     Windows Başlat menüsünde, "yükleyici" için arama yapabilirsiniz.

     ![Visual Studio Yükleyicisi](media/vs-2019/visual-studio-installer.png "Visual Studio Yükleyicisi arayın")

     > [!NOTE]
     > Aşağıdaki konumda Visual Studio Yükleyicisi de bulabilirsiniz:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Bu durumda, istemleri izleyin.

1. Yükleyicide, yüklediğiniz Visual Studio sürümünü arayın. Daha sonra, **daha fazla**' yı ve ardından **Kaldır**' ı seçin.

     ![Visual Studio 2019 'yi kaldırma](media/vs-2019/vs-installer-uninstall.png "Visual Studio 2019 'yi kaldırma")

1. Seçiminizi onaylamak için **Tamam** ' ı tıklatın.

     ![Visual Studio onayını kaldır](media/vs-2019/uninstall-visualstudio-confirm.png "Visual Studio 2019 ' i kaldırmak istediğinizi onaylayın")

Daha sonra fikrinizi değiştirirseniz ve Visual Studio 2019 ' i yeniden yüklemek istiyorsanız Visual Studio Yükleyicisi yeniden başlatın, **kullanılabilir** sekmesini seçin, yüklemek Istediğiniz Visual Studio sürümünü seçin ve ardından **Yükle**' yi seçin.

## <a name="uninstall-visual-studio-installer"></a>Visual Studio Yükleyicisi kaldır

Visual Studio 2019 ve Visual Studio Yükleyicisi tüm yüklemelerini makinenizden kaldırmak için, uygulamalardan & özelliklerden kaldırın.

1. Windows 10 ' da, "aramak için buraya yazın" kutusuna **uygulamalar ve Özellikler** yazın.
1. **Visual Studio 2019**' i bulun.
1. **Kaldır**' ı seçin.
1. Ardından **Microsoft Visual Studio yükleyiciyi**bulun.
1. **Kaldır**' ı seçin.

::: moniker-end

## <a name="remove-all-files"></a>Tüm dosyaları Kaldır

Çok önemli bir hata yaşarsanız ve önceki yönergeleri kullanarak Visual Studio 'Yu kaldıramıyorsanız, kullanmayı düşünebileceğiniz bir "son çare" seçeneği vardır. Tüm Visual Studio yükleme dosyalarını ve ürün bilgilerini tamamen kaldırma hakkında daha fazla bilgi için bkz. [Visual Studio 'Yu kaldırma](remove-visual-studio.md) sayfası.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio’yu değiştirme](modify-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
