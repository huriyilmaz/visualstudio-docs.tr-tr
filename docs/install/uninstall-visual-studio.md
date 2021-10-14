---
title: Visual Studio'yu kaldırma
titleSuffix: ''
description: Visual Studio nasıl kaldırılacağını öğrenin, adım adım.
ms.date: 10/12/2020
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
ms.openlocfilehash: d3e7171868a78f26433dbdc1f3ae8f08632c40e0
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972357"
---
# <a name="uninstall-visual-studio"></a>Visual Studio'yu kaldırma

bu sayfada, geliştiricilere yönelik tümleşik üretkenlik araçları takımımızı Visual Studio kaldırma işlemi adım adım açıklanmaktadır.

> [!NOTE]
> bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Mac için Visual Studio kaldır](/visualstudio/mac/uninstall).

> [!TIP]
> Visual Studio örneğinizle ilgili sorun yaşıyorsanız **onarım** aracını deneyin. Daha fazla bilgi için bkz. [Visual Studio onarma](../install/repair-visual-studio.md). 
>
> Visual Studio dosyalarınızın bir kısmının konumunu değiştirmek istiyorsanız, geçerli örneğinizi kaldırmadan bunu yapmak mümkündür. Daha fazla bilgi için bkz. [Visual Studio yükleme konumlarını seçme](../install/change-installation-locations.md).
>
> genel sorun giderme ipuçları için bkz. [Visual Studio yükleme ve yükseltme sorunlarını giderme](../install/troubleshooting-installation-issues.md).

::: moniker range="vs-2017"

1. bilgisayarınızda Visual Studio Yükleyicisi bulun.

     örneğin, Windows 10 yıldönümü güncelleştirmesi veya sonraki bir sürümünü çalıştıran bir bilgisayarda **başlat** ' ı seçin ve **Visual Studio Yükleyicisi** olarak listelendiği **V** harfine gidin.

     ![Visual Studio Yükleyicisi](media/locate-the-visual-studio-installer.png "Microsoft Visual Studio yükleyicisini bulun")

   > [!NOTE]
   > bazı bilgisayarlarda Visual Studio Yükleyicisi, **Microsoft Visual Studio yükleyicisi** olarak **"d"** harfi altında listelenmiş olabilir.<br/><br/> alternatif olarak, Visual Studio Yükleyicisi aşağıdaki konumda bulabilirsiniz:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. yükleyicide, yüklediğiniz Visual Studio sürümünü arayın. Daha sonra, **daha fazla**' yı ve ardından **Kaldır**' ı seçin.

     ![Visual Studio kaldırma 2017](media/uninstall-visual-studio.png "Visual Studio kaldırma 2017")

1. Seçiminizi onaylamak için **Tamam** ' ı tıklatın.

daha sonra fikrinizi değiştirirseniz ve 2017 Visual Studio yeniden yüklemek istiyorsanız Visual Studio Yükleyicisi yeniden başlatın ve sonra seçim ekranından **yükle** ' yi seçin.

## <a name="uninstall-visual-studio-installer"></a>Visual Studio Yükleyicisi kaldır

Visual Studio 2017 ' nin tüm yüklemelerini ve Visual Studio Yükleyicisi makinenizden tamamen kaldırmak için uygulama & özelliklerinden kaldırın.

1. Windows 10 veya sonraki sürümlerde, "aramak için buraya yazın" kutusuna **uygulamalar ve özellikler** yazın.
1. **Microsoft Visual Studio 2017** (veya **Visual Studio 2017**) bulun.
1. **Kaldır**' ı seçin.
1. ardından **Microsoft Visual Studio yükleyiciyi** bulun.
1. **Kaldır**' ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

1. bilgisayarınızda **Visual Studio Yükleyicisi** bulun.

     Windows Başlat menüsü, "yükleyici" için arama yapabilirsiniz.

     ![Visual Studio Yükleyicisi](media/vs-2019/visual-studio-installer.png "Visual Studio Yükleyicisi arayın")

     > [!NOTE]
     > aşağıdaki konumda Visual Studio Yükleyicisi de bulabilirsiniz:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Bu durumda, istemleri izleyin.

1. yükleyicide, yüklediğiniz Visual Studio sürümünü arayın. Daha sonra, **daha fazla**' yı ve ardından **Kaldır**' ı seçin.

     ![Visual Studio kaldırma 2019](media/vs-2019/vs-installer-uninstall.png "Visual Studio kaldırma 2019")

1. Seçiminizi onaylamak için **Tamam** ' ı tıklatın.

     ![Visual Studio onayını kaldır](media/vs-2019/uninstall-visualstudio-confirm.png "2019 Visual Studio kaldırmak istediğinizi onaylayın")

daha sonra fikrinizi değiştirirseniz ve 2019 veya 2022 Visual Studio yeniden yüklemek istiyorsanız Visual Studio Yükleyicisi yeniden başlatın, **kullanılabilir** sekmesini seçin, yüklemek istediğiniz Visual Studio sürümünü seçin ve ardından **yükle**' yi seçin.

## <a name="uninstall-visual-studio-installer"></a>Visual Studio Yükleyicisi kaldır

Visual Studio 2019, Visual Studio 2022 ' nin tüm yüklemelerini ve Visual Studio Yükleyicisi makinenizden kaldırmak için uygulama & özelliklerden kaldırın.

1. Windows 10 veya sonraki sürümlerde, "aramak için buraya yazın" kutusuna **uygulamalar ve özellikler** yazın.
1. **Visual Studio 2019** veya **Visual Studio 2022** bulun.
1. **Kaldır**' ı seçin.
1. ardından **Microsoft Visual Studio yükleyiciyi** bulun.
1. **Kaldır**' ı seçin.

::: moniker-end

## <a name="remove-all-files"></a>Tüm dosyaları Kaldır

çok önemli bir hata yaşarsanız ve önceki yönergeleri kullanarak Visual Studio kaldıramıyorsanız, kullanmayı düşünebileceğiniz bir "son çare" seçeneği vardır. tüm Visual Studio yükleme dosyalarını ve ürün bilgilerini tamamen kaldırma hakkında daha fazla bilgi için, [kaldırma Visual Studio](remove-visual-studio.md) sayfasına bakın.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio’yu değiştirme](modify-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
