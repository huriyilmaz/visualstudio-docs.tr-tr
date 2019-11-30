---
title: Visual Studio’yu değiştirme
titleSuffix: ''
description: Visual Studio 'Yu nasıl değiştireceğinizi adım adım öğrenin.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 08/23/2019
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
ms.openlocfilehash: 628d8fe5d8374d0cb203e6953f63bd63d77d0c58
ms.sourcegitcommit: 3ba2968a4b44643482aadad4d50e1a55bb36b136
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74566993"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>İş yüklerini ve bileşenleri ekleyerek veya kaldırarak Visual Studio 'Yu değiştirme

::: moniker range="vs-2019"

Visual Studio 'Yu, istediğinizde yalnızca istediğiniz şeyi içerecek şekilde değiştirmek kolaydır. Bunu yapmak için, iş yüklerini ve bileşenleri eklemek veya kaldırmak üzere Visual Studio Yükleyicisi açın.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 'yu, gerçekleştirmek istediğiniz görevlerle eşleşecek şekilde kişiselleştirmek için de daha kolay hale getirdik. Ayrıca, Visual Studio 'yu de özelleştirmeyi daha kolay hale getirdik. Bunu yapmak için yeni Visual Studio Yükleyicisi başlatın ve istediğiniz değişiklikleri yapın.

::: moniker-end

İşte.

>[!IMPORTANT]
>Visual Studio 'Yu yüklemek, güncelleştirmek ya da değiştirmek için yönetici izinlerine sahip bir hesapla oturum açmalısınız. Daha fazla bilgi için bkz. [Kullanıcı izinleri ve Visual Studio](../ide/user-permissions-and-visual-studio.md).

## <a name="modify-workloads"></a>İş yüklerini değiştirme

::: moniker range="vs-2017"

 [Iş yükleri](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) , kullanmakta olduğunuz programlama dili veya platformu için gereken özellikleri içerir. İş yüklerini kullanarak Visual Studio 'Yu, yapmak istediğiniz çalışmayı, yapmak istediğiniz işi destekleyecek şekilde değiştirin.

::: moniker-end

::: moniker range="vs-2019"

 İş yükleri, kullanmakta olduğunuz programlama dili veya platformu için gereken özellikleri içerir. İş yüklerini kullanarak Visual Studio 'Yu, yapmak istediğiniz çalışmayı, yapmak istediğiniz işi destekleyecek şekilde değiştirin.

::: moniker-end

>[!NOTE]
> Aşağıdaki yordamda bir internet bağlantınız olduğunu varsaymaktadır.
>
> Daha önce oluşturulmuş bir Visual Studio [yüklemesinin](create-an-offline-installation-of-visual-studio.md) nasıl değiştirileceği hakkında daha fazla bilgi için bkz. [Visual Studio 'nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md) sayfası ve [ağ tabanlı Visual Studio dağıtımları için güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md) sayfası.

::: moniker range="vs-2017"

1. Bilgisayarınızda Visual Studio Yükleyicisi bulun.

     Örneğin, Windows 10 çalıştıran bir bilgisayarda **Başlat**' ı seçin ve ardından **Visual Studio yükleyicisi**olarak listelendiği **V**harfine gidin.

     ![Visual Studio Yükleyicisi](media/vs2017-locate-the-visual-studio-installer.PNG "Microsoft Visual Studio yükleyicisini bulun")

     >[!TIP]
     >Bazı bilgisayarlarda Visual Studio Yükleyicisi, **Microsoft Visual Studio yükleyicisi**olarak **"d"** harfi altında listelenmiş olabilir.<br/><br/> Alternatif olarak, Visual Studio Yükleyicisi şu konumda bulabilirsiniz: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Yükleyiciyi başlatmak için tıklayın veya dokunun ve ardından **Değiştir**' i seçin.

     ![Visual Studio 'Yu başlatma veya değiştirme](media/modify-visual-studio.png "Visual Studio 2017 'yi değiştirme")

     Bekleyen bir güncelleştirmeniz varsa Değiştir düğmesi farklı bir yerdir. Bu şekilde, Visual Studio 'Yu güncelleştirme olmadan değiştirebilirsiniz, bunu yapmanız gerekir. **Daha fazla**' ya tıklayın ve ardından **Değiştir**' i seçin.

     ![Visual Studio 'Yu güncelleştirme veya değiştirme](media/modify-or-update-visual-studio.png "Visual Studio 2017 'yi güncelleştirme veya değiştirme")

1. **Iş yükleri** ekranından, yüklemek veya kaldırmak istediğiniz iş yüklerini seçin veya seçimini kaldırın.

    ![Visual Studio 2017 kurulum Iletişim kutusu](media/vs2017-modify-workloads.PNG "Visual Studio 2017 'de iş yükü seçme")

1. Yeniden **Değiştir** ' i seçin.

1. Yeni iş yükleri ve bileşenler yüklendikten sonra **Başlat**' ı seçin.

::: moniker-end

::: moniker range="vs-2019"

1. Bilgisayarınızda Visual Studio Yükleyicisi bulun.

     Örneğin, Windows 10 çalıştıran bir bilgisayarda **Başlat**' ı seçin ve ardından **Visual Studio yükleyicisi**olarak listelendiği **V**harfine gidin.

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

## <a name="modify-individual-components"></a>Ayrı bileşenleri Değiştir

Visual Studio yüklemenizi özelleştirmek için iş yüklerini yüklemek istemiyorsanız, Visual Studio Yükleyicisi **bireysel bileşenler** sekmesini seçin, istediğiniz öğeleri seçin ve ardından istemleri izleyin.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio iş yükünün & bileşen kimliklerinin listesi](workload-and-component-ids.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
* [Bakım temeliyle Visual Studio 'Yu güncelleştirme](update-servicing-baseline.md)
* [Ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
