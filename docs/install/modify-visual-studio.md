---
title: Visual Studio’yu değiştirme
titleSuffix: ''
description: Visual Studio'da adım adım nasıl değiştiriliz öğrenin.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77125357"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>İş yüklerini ve bileşenleri ekleyerek veya kaldırarak Visual Studio'da değişiklik

::: moniker range="vs-2019"

Visual Studio'yı yalnızca istediğiniz ie'yi, istediğiniz zaman içerecek şekilde değiştirmek kolaydır. Bunu yapmak için iş yüklerini ve bileşenleri eklemek veya kaldırmak için Visual Studio Yükleyici'yi açın.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio'yu gerçekleştirmek istediğiniz görevlere uyacak şekilde kişiselleştirmenizi kolaylaştırmakla kalmadık, Visual Studio'yu da özelleştirmeyi kolaylaştırdık. Bunu yapmak için yeni Visual Studio Yükleyicisini açın ve istediğiniz değişiklikleri yapın.

::: moniker-end

Aşağıdaki adımları uygulayın:

>[!IMPORTANT]
>Visual Studio'yı yüklemek, güncellemek veya değiştirmek için yönetim izinleri olan bir hesapla oturum açmanız gerekir. Daha fazla bilgi için [Kullanıcı izinlerine ve Visual Studio'ya](../ide/user-permissions-and-visual-studio.md)bakın.

>[!NOTE]
> Aşağıdaki yordamlar bir internet bağlantınız olduğunu varsayar.
>
> Visual Studio'nun önceden oluşturulmuş [çevrimdışı yüklemesini](create-an-offline-installation-of-visual-studio.md) nasıl değiştirebilirsiniz hakkında daha fazla bilgi için, hem [Visual Studio sayfasının ağ tabanlı yüklemesini](update-a-network-installation-of-visual-studio.md) güncelleştir'e hem de [ağ tabanlı Visual Studio dağıtımları sayfasındadenetim güncelleştirmelerine](controlling-updates-to-visual-studio-deployments.md) bakın.

## <a name="open-the-visual-studio-installer"></a>Visual Studio Yükleyicisini Açın

::: moniker range="vs-2017"

1. Bilgisayarınızda Visual Studio Yükleyicisini bulun.

     Örneğin, Windows 10 çalıştıran bir bilgisayarda **Başlat'ı**seçin ve ardından Visual **Studio Installer**olarak listelenen **V**harfine gidin.

     ![Visual Studio Yükleyicisi](media/locate-the-visual-studio-installer.png "Microsoft Visual Studio Yükleyicisini Bulun")

     >[!TIP]
     >Bazı bilgisayarlarda, Visual Studio Installer **Microsoft Visual Studio Installer**olarak **"M"** harfi altında listelenmiş olabilir.<br/><br/> Alternatif olarak, Visual Studio Yükleyicisini aşağıdaki konumda bulabilirsiniz:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Yükleyiciyi açın ve sonra **Değiştir'i**seçin.

     ![Visual Studio'u başlatın veya değiştirin](media/modify-visual-studio.png "Visual Studio 2017'yi Değiştirme")

     > [!IMPORTANT]
     > Bekleyen bir güncelleştirmeniz varsa, Değiştir düğmesi farklı bir yerdedir. Bu şekilde, visual studio'u güncellemeden değiştirebilirsiniz, bunu yapmayı seçerseniz. **Daha Fazla'yı**tıklatın ve sonra **Değiştir'i**seçin.
     >
     > ![Visual Studio'yı güncelleştirin veya değiştirin](media/modify-or-update-visual-studio.png "Visual Studio 2017'yi güncelleştirin veya değiştirin")

::: moniker-end

::: moniker range="vs-2019"

1. Bilgisayarınızda Visual Studio Yükleyicisini bulun.

     Örneğin, Windows 10 çalıştıran bir bilgisayarda **Başlat'ı**seçin ve ardından Visual **Studio Installer**olarak listelenen **V**harfine gidin.

     ![Windows'tan Visual Studio Yükleyicisini Açın](media/vs-2019/vs-installer-windows-start.png "Visual Studio Yükleyicisini Açın")

     > [!NOTE]
     > Visual Studio Yükleyicisini aşağıdaki konumda da bulabilirsiniz:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Öyleyse, istemleri izleyin.

1. Yükleyicide, yüklediğiniz Visual Studio sürümünü arayın ve ardından **Değiştir'i**seçin.

     ![Visual Studio'yı güncelleştirin veya değiştirin](media/vs-2019/vs-installer-modify.png "Visual Studio 2019'u güncelleyin veya değiştirin")

     > [!IMPORTANT]
     > Bekleyen bir güncelleştirmeniz varsa, Değiştir düğmesi farklı bir yerdedir. Bu şekilde, Visual Studio'u güncellemeden değiştirebilirsiniz. **Daha Fazlasını**seçin ve sonra **Değiştir'i**seçin.
     >
     > ![Visual Studio'yı güncelleştirin veya değiştirin](media/vs-2019/modify-update-visual-studio.png "Visual Studio 2019'u güncelleyin veya değiştirin")

::: moniker-end

## <a name="modify-workloads"></a>İş yüklerini değiştirme

::: moniker range="vs-2017"

 [İş yükleri,](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) kullanmakta olduğunuz programlama dili veya platformu için gereksinim duyduğunuz özellikleri içerir. Visual Studio'yu yapmak istediğiniz işi ne zaman yapmak istediğinizi destekleecek şekilde değiştirmek için iş yüklerini kullanın.

1. Visual Studio Yükleyici'de **İş Yükleri** sekmesini seçin ve ardından istediğiniz iş yüklerini seçin veya seçin.

    ![Visual Studio 2017 kurulum iletişim kutusu](media/modify-workloads.png "Visual Studio 2019'da bir iş yükü seçin")

1. İndirme seçeneğini veya Tümlerini **İndiri'yi** karşılarken varsayılan Yükle'yi kabul etmek isteyip istemediğinizi seçin **ve ardından seçeneğini yükleyin.**

    ![Visual Studio 2017 kurulum seçenekleri](media/vs-2019/vs-installer-choose-install-or-download.png "İndirirken yüklemeyi veya önce indirmeyi ve daha sonra yüklemeyi seçin")

    Önce indirip sonra yüklemek istiyorsanız "Tümlerini indirin, sonra yükle" seçeneği kullanışlıdır.

1. **Değiştir'i**seçin.

1. Yeni iş yükleri yüklendikten sonra Visual Studio Installer'dan **Visual** Studio Installer'ı başlat'ı seçin.

::: moniker-end

::: moniker range="vs-2019"

 İş yükleri, kullanmakta olduğunuz programlama dili veya platformu için gereksinim duyduğunuz özellikleri içerir. Visual Studio'yu yapmak istediğiniz işi ne zaman yapmak istediğinizi destekleecek şekilde değiştirmek için iş yüklerini kullanın.

 > [!TIP]
>Geliştirme için hangi araç ve bileşen paketlerine ihtiyacınız olduğu hakkında daha fazla bilgi için [Visual Studio iş yüklerine](https://visualstudio.microsoft.com/vs/#workloads)bakın.

1. Visual Studio Installer'da, **İş Yükleri** sekmesini seçin ve ardından istediğiniz iş yüklerini seçin veya seçin.

    ![Visual Studio 2019 kurulum iletişim kutusu](media/vs-2019/vs-installer-modify-workloads.png "Visual Studio 2019'da bir iş yükü seçin")

1. İndirme seçeneğini veya Tümlerini **İndiri'yi** karşılarken varsayılan Yükle'yi kabul etmek isteyip istemediğinizi seçin **ve ardından seçeneğini yükleyin.**

    ![Visual Studio 2019 kurulum seçenekleri](media/vs-2019/vs-installer-choose-install-or-download.png "İndirirken yüklemeyi veya önce indirmeyi ve daha sonra yüklemeyi seçin")

    Önce indirip sonra yüklemek istiyorsanız "Tümlerini indirin, sonra yükle" seçeneği kullanışlıdır.

1. **Değiştir'i**seçin.

1. Yeni iş yükleri yüklendikten sonra Visual Studio Installer'dan **Visual** Studio Installer'ı başlat'ı seçin.

::: moniker-end

## <a name="modify-individual-components"></a>Tek tek bileşenleri değiştirme

Visual Studio yüklemenizi özelleştirmek için iş yüklerini kullanmak istemiyorsanız, Visual Studio Installer'daki **Tek Tek Bileşenler** sekmesini seçin, istediğiniz bileşenleri seçin ve ardından istemleri izleyin.

>[!TIP]
> SQL Server Veri Araçları (SSDT) bileşeni hakkında bilgi için [Visual Studio için SSDT'yi indirip yükleyin.](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15)

## <a name="modify-language-packs"></a>Dil paketlerini değiştirme

Varsayılan olarak, yükleyici ilk kez çalıştığında işletim sisteminin diliyle eşleşir. Ancak, dili istediğiniz zaman değiştirebilirsiniz. Bunu yapmak için Visual Studio Installer'daki **Dil paketleri** sekmesini seçin, tercih ettiğiniz dili seçin ve ardından istemleri izleyin.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio iş yükü & bileşen itlemi listesi](workload-and-component-ids.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
* [Bakım temeli sırasında Visual Studio’yu güncelleştirme](update-servicing-baseline.md)
* [Ağ tabanlı Visual Studio dağıtımlarında denetim güncelleştirmeleri](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
