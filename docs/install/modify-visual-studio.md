---
title: Visual Studio’yu değiştirme
titleSuffix: ''
description: Visual Studio, adım adım değiştirme hakkında bilgi edinin.
ms.date: 02/10/2019
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 57aa5531eb6d6517b520991ababefc38b25a9a2d
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77125357"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>İş yüklerini ve bileşenleri ekleyerek veya kaldırarak Visual Studio 'Yu değiştirme

::: moniker range="vs-2019"

Visual Studio 'Yu, istediğinizde yalnızca istediğiniz şeyi içerecek şekilde değiştirmek kolaydır. Bunu yapmak için, iş yüklerini ve bileşenleri eklemek veya kaldırmak üzere Visual Studio Yükleyicisi açın.

::: moniker-end

::: moniker range="vs-2017"

Sadece biz bunu daha da kolaylaştırdık gerçekleştirmek istediğiniz görevleri eşleştirmek için Visual Studio kişiselleştirmek için Ayrıca, Visual Studio, çok özelleştirmek daha kolay hale getirdik. Bunu yapmak için yeni Visual Studio Yükleyicisi açın ve istediğiniz değişiklikleri yapın.

::: moniker-end

İşte nasıl.

>[!IMPORTANT]
>Yüklemek, güncelleştirmek veya Visual Studio değiştirmek için yönetici izinleri olan bir hesapla oturum açmalısınız. Daha fazla bilgi için bkz. [Kullanıcı izinleri ve Visual Studio](../ide/user-permissions-and-visual-studio.md).

>[!NOTE]
> Aşağıdaki yordamlarda bir internet bağlantınız olduğunu varsaymaktadır.
>
> Daha önce oluşturulmuş bir Visual Studio [yüklemesinin](create-an-offline-installation-of-visual-studio.md) nasıl değiştirileceği hakkında daha fazla bilgi için bkz. [Visual Studio 'nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md) sayfası ve [ağ tabanlı Visual Studio dağıtımları için güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md) sayfası.

## <a name="open-the-visual-studio-installer"></a>Visual Studio Yükleyicisi açın

::: moniker range="vs-2017"

1. Bilgisayarınızda Visual Studio yükleyicisi bulun.

     Örneğin, Windows 10 çalıştıran bir bilgisayarda **Başlat**' ı seçin ve ardından **Visual Studio yükleyicisi**olarak listelendiği **V**harfine gidin.

     ![Visual Studio Yükleyicisi](media/locate-the-visual-studio-installer.png "Microsoft Visual Studio yükleyicisini bulun")

     >[!TIP]
     >Bazı bilgisayarlarda Visual Studio Yükleyicisi, **Microsoft Visual Studio yükleyicisi**olarak **"d"** harfi altında listelenmiş olabilir.<br/><br/> Alternatif olarak, Visual Studio Yükleyicisi şu konumda bulabilirsiniz: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Yükleyiciyi açın ve ardından **Değiştir**' i seçin.

     ![Visual Studio 'Yu başlatma veya değiştirme](media/modify-visual-studio.png "Visual Studio 2017 'yi değiştirme")

     > [!IMPORTANT]
     > Bekleyen bir güncelleştirme varsa, Değiştir düğmesine içinde farklı bir yerdir. Bu şekilde, Visual Studio, güncelleştirmeden Bunu yapmak seçmelidir değiştirebilirsiniz. **Daha fazla**' ya tıklayın ve ardından **Değiştir**' i seçin.
     >
     > ![Visual Studio 'Yu güncelleştirme veya değiştirme](media/modify-or-update-visual-studio.png "Visual Studio 2017 'yi güncelleştirme veya değiştirme")

::: moniker-end

::: moniker range="vs-2019"

1. Bilgisayarınızda Visual Studio yükleyicisi bulun.

     Örneğin, Windows 10 çalıştıran bir bilgisayarda **Başlat**' ı seçin ve ardından **Visual Studio yükleyicisi**olarak listelendiği **V**harfine gidin.

     ![Visual Studio Yükleyicisi Windows 'tan açın](media/vs-2019/vs-installer-windows-start.png "Visual Studio Yükleyicisi açın")

     > [!NOTE]
     > Aşağıdaki konumda Visual Studio Yükleyicisi de bulabilirsiniz:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Bu durumda, istemleri izleyin.

1. Yükleyicide, yüklediğiniz Visual Studio sürümünü bulun ve ardından **Değiştir**' i seçin.

     ![Visual Studio 'Yu güncelleştirme veya değiştirme](media/vs-2019/vs-installer-modify.png "Visual Studio 2019 'yi güncelleştirme veya değiştirme")

     > [!IMPORTANT]
     > Bekleyen bir güncelleştirme varsa, Değiştir düğmesine içinde farklı bir yerdir. Bu şekilde, Visual Studio 'Yu güncelleştirme olmadan değiştirebilirsiniz, isterseniz. **Daha fazla**' yı seçin ve ardından **Değiştir**' i seçin.
     >
     > ![Visual Studio 'Yu güncelleştirme veya değiştirme](media/vs-2019/modify-update-visual-studio.png "Visual Studio 2019 'yi güncelleştirme veya değiştirme")

::: moniker-end

## <a name="modify-workloads"></a>İş yüklerini değiştirme

::: moniker range="vs-2017"

 [Iş yükleri](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) , kullanmakta olduğunuz programlama dili veya platformu için gereken özellikleri içerir. Bunu yapmak istediğiniz zaman, istediğiniz iş destekler, böylece Visual Studio değiştirmek için iş yüklerini kullanın.

1. Visual Studio Yükleyicisi, **Iş yükleri** sekmesini seçin ve ardından istediğiniz iş yüklerini seçin veya seçimini kaldırın.

    ![Visual Studio 2017 kurulum iletişim kutusu](media/modify-workloads.png "Visual Studio 2019 'de iş yükü seçme")

1. **İndirme sırasında varsayılan yüklemeyi** kabul etmek mi yoksa **Tümünü indir ve yükle** seçeneğini belirleyin.

    ![Visual Studio 2017 kurulum seçenekleri](media/vs-2019/vs-installer-choose-install-or-download.png "İlk kez karşıdan yükleme veya indirme sırasında yüklemeyi seçin ve daha sonra yükleyin")

    Önce indirmek ve sonra yüklemek istiyorsanız "tümünü Indir ve Yükle" seçeneği kullanışlıdır.

1. **Değiştir**'i seçin.

1. Yeni iş yükleri yüklendikten sonra Visual Studio 'Yu açmak için Visual Studio Yükleyicisi **Başlat** ' ı seçin.

::: moniker-end

::: moniker range="vs-2019"

 İş yükleri, kullanmakta olduğunuz programlama dili veya platformu için gereken özellikleri içerir. Bunu yapmak istediğiniz zaman, istediğiniz iş destekler, böylece Visual Studio değiştirmek için iş yüklerini kullanın.

 > [!TIP]
>Geliştirme için ihtiyaç duyduğunuz araç ve bileşen paketleri hakkında daha fazla bilgi için bkz. [Visual Studio iş yükleri](https://visualstudio.microsoft.com/vs/#workloads).

1. Visual Studio Yükleyicisi içinde, **Iş yükleri** sekmesini seçin ve ardından istediğiniz iş yüklerini seçin veya seçimini kaldırın.

    ![Visual Studio 2019 kurulum iletişim kutusu](media/vs-2019/vs-installer-modify-workloads.png "Visual Studio 2019 'de iş yükü seçme")

1. **İndirme sırasında varsayılan yüklemeyi** kabul etmek mi yoksa **Tümünü indir ve yükle** seçeneğini belirleyin.

    ![Visual Studio 2019 kurulum seçenekleri](media/vs-2019/vs-installer-choose-install-or-download.png "İlk kez karşıdan yükleme veya indirme sırasında yüklemeyi seçin ve daha sonra yükleyin")

    Önce indirmek ve sonra yüklemek istiyorsanız "tümünü Indir ve Yükle" seçeneği kullanışlıdır.

1. **Değiştir**'i seçin.

1. Yeni iş yükleri yüklendikten sonra Visual Studio 'Yu açmak için Visual Studio Yükleyicisi **Başlat** ' ı seçin.

::: moniker-end

## <a name="modify-individual-components"></a>Tek tek bileşenler değiştirme

Visual Studio yüklemenizi özelleştirmek için iş yüklerini kullanmak istemiyorsanız, Visual Studio Yükleyicisi **bireysel bileşenler** sekmesini seçin, istediğiniz bileşenleri seçin ve ardından istemleri izleyin.

>[!TIP]
> SQL Server Veri Araçları (SSDT) bileşeni hakkında daha fazla bilgi için bkz. [Visual Studio IÇIN SSDT indirme ve yükleme](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15).

## <a name="modify-language-packs"></a>Dil paketlerini değiştirme

Varsayılan olarak, yükleyici ilk kez çalıştırıldığında işletim sisteminin diliyle eşleşir. Ancak, dili istediğiniz zaman değiştirebilirsiniz. Bunu yapmak için Visual Studio Yükleyicisi **dil paketleri** sekmesini seçin, tercih ettiğiniz dili seçin ve ardından istemleri izleyin.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio iş yükünün & bileşen kimliklerinin listesi](workload-and-component-ids.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
* [Bakım temeliyle Visual Studio 'Yu güncelleştirme](update-servicing-baseline.md)
* [Ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
