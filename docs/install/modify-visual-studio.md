---
title: Visual Studio’yu değiştirme
titleSuffix: ''
description: Visual Studio, adım adım değiştirme hakkında bilgi edinin.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 12/03/2019
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 23e44479bedfdb44b2375baae9f342f47b38700b
ms.sourcegitcommit: c222052906362bf1a3762ec4d4623170e4e06702
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810065"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>İş yüklerini ve bileşenleri ekleyerek veya kaldırarak Visual Studio 'Yu değiştirme

::: moniker range="vs-2019"

Visual Studio 'Yu, istediğinizde yalnızca istediğiniz şeyi içerecek şekilde değiştirmek kolaydır. Bunu yapmak için, iş yüklerini ve bileşenleri eklemek veya kaldırmak üzere Visual Studio Yükleyicisi açın.

::: moniker-end

::: moniker range="vs-2017"

Sadece biz bunu daha da kolaylaştırdık gerçekleştirmek istediğiniz görevleri eşleştirmek için Visual Studio kişiselleştirmek için Ayrıca, Visual Studio, çok özelleştirmek daha kolay hale getirdik. Bunu yapmak için yeni Visual Studio Yükleyicisi'ni başlatın ve istediğiniz değişiklikleri yapın.

::: moniker-end

İşte nasıl.

>[!IMPORTANT]
>Yüklemek, güncelleştirmek veya Visual Studio değiştirmek için yönetici izinleri olan bir hesapla oturum açmalısınız. Daha fazla bilgi için bkz. [Kullanıcı izinleri ve Visual Studio](../ide/user-permissions-and-visual-studio.md).

## <a name="modify-workloads"></a>İş yüklerini değiştirme

::: moniker range="vs-2017"

 [Iş yükleri](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) , kullanmakta olduğunuz programlama dili veya platformu için gereken özellikleri içerir. Bunu yapmak istediğiniz zaman, istediğiniz iş destekler, böylece Visual Studio değiştirmek için iş yüklerini kullanın.

::: moniker-end

::: moniker range="vs-2019"

 İş yükleri, kullanmakta olduğunuz programlama dili veya platformu için gereken özellikleri içerir. Bunu yapmak istediğiniz zaman, istediğiniz iş destekler, böylece Visual Studio değiştirmek için iş yüklerini kullanın.

::: moniker-end

>[!NOTE]
> Aşağıdaki yordamda bir internet bağlantınız olduğunu varsaymaktadır.
>
> Daha önce oluşturulmuş bir Visual Studio [yüklemesinin](create-an-offline-installation-of-visual-studio.md) nasıl değiştirileceği hakkında daha fazla bilgi için bkz. [Visual Studio 'nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md) sayfası ve [ağ tabanlı Visual Studio dağıtımları için güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md) sayfası.

::: moniker range="vs-2017"

1. Bilgisayarınızda Visual Studio yükleyicisi bulun.

     Örneğin, Windows 10 çalıştıran bir bilgisayarda seçin **Başlat**ve harfi kaydırın **V**, olarak listelenen burada **Visual Studio yükleyicisi**.

     ![Visual Studio Yükleyicisi](media/locate-the-visual-studio-installer.png "Microsoft Visual Studio yükleyicisini bulun")

     >[!TIP]
     >Bazı bilgisayarlarda, Visual Studio yükleyicisi harfi altında listelenebilir **"M"** olarak **Microsoft Visual Studio yükleyicisi**.<br/><br/> Alternatif olarak, Visual Studio yükleyicisi şu konumda bulabilirsiniz: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. ' A tıklayın veya yükleyiciyi başlatmak için dokunun ve ardından **Değiştir**.

     ![Visual Studio 'Yu başlatma veya değiştirme](media/modify-visual-studio.png "Visual Studio 2017 'yi değiştirme")

     Bekleyen bir güncelleştirme varsa, Değiştir düğmesine içinde farklı bir yerdir. Bu şekilde, Visual Studio, güncelleştirmeden Bunu yapmak seçmelidir değiştirebilirsiniz. Tıklayın **daha fazla**ve ardından **Değiştir**.

     ![Visual Studio 'Yu güncelleştirme veya değiştirme](media/modify-or-update-visual-studio.png "Visual Studio 2017 'yi güncelleştirme veya değiştirme")

1. Gelen **iş yükleri** ekran seçin veya yüklemek veya kaldırmak istediğiniz iş yüklerini seçimini kaldırın.

    ![Visual Studio 2017 kurulum Iletişim kutusu](media/modify-workloads.png "Visual Studio 2017 'de iş yükü seçme")

1. Seçin **Değiştir** yeniden.

1. Yeni iş yükleri ve bileşenler yüklendikten sonra seçin **başlatma**.

::: moniker-end

::: moniker range="vs-2019"

1. Bilgisayarınızda Visual Studio yükleyicisi bulun.

     Örneğin, Windows 10 çalıştıran bir bilgisayarda seçin **Başlat**ve harfi kaydırın **V**, olarak listelenen burada **Visual Studio yükleyicisi**.

     ![Visual Studio Yükleyicisi Windows 'tan açın](media/vs-2019/vs-installer-windows-start.png "Visual Studio Yükleyicisi açın")

     > [!NOTE]
     > Aşağıdaki konumda Visual Studio Yükleyicisi de bulabilirsiniz:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Bu durumda, istemleri izleyin.

1. Yükleyicide, yüklediğiniz Visual Studio sürümünü bulun ve ardından **Değiştir**' i seçin.

     ![Visual Studio 'Yu güncelleştirme veya değiştirme](media/vs-2019/vs-installer-modify.png "Visual Studio 2019 'yi güncelleştirme veya değiştirme")

1. **Iş yükleri** sekmesinde, yüklemek veya kaldırmak istediğiniz iş yüklerini seçin veya seçimini kaldırın.

    ![Visual Studio 2019 kurulum iletişim kutusu](media/vs-2019/vs-installer-modify-workloads.png "Visual Studio 2019 'de iş yükü seçme")

1. **İndirme sırasında varsayılan yüklemeyi** kabul etmek mi yoksa **Tümünü indir ve yükle** seçeneğini belirleyin.

    ![Visual Studio 2019 kurulum seçenekleri](media/vs-2019/vs-installer-choose-install-or-download.png "İlk kez karşıdan yükleme veya indirme sırasında yüklemeyi seçin ve daha sonra yükleyin")

    Önce indirmek ve sonra yüklemek istiyorsanız "tümünü Indir ve Yükle" seçeneği kullanışlıdır.

1. **Değiştir**'i seçin.

1. Yeni iş yükleri ve bileşenler yüklendikten sonra Visual Studio Yükleyicisi **Başlat** ' ı seçin.

::: moniker-end

## <a name="modify-individual-components"></a>Tek tek bileşenler değiştirme

Visual Studio yüklemenizi özelleştirmek için iş yüklerini yüklemek istemiyorsanız, Visual Studio Yükleyicisi **bireysel bileşenler** sekmesini seçin, istediğiniz öğeleri seçin ve ardından istemleri izleyin.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio iş yükünün & bileşen kimliklerinin listesi](workload-and-component-ids.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
* [Bakım temeliyle Visual Studio 'Yu güncelleştirme](update-servicing-baseline.md)
* [Ağ tabanlı Visual Studio dağıtımlarına yönelik güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
