---
title: Visual Studio iş yüklerini, bileşenlerini & dil paketlerini değiştirme
titleSuffix: ''
description: Visual Studio 'Yu nasıl değiştireceğinizi adım adım öğrenin.
ms.date: 10/12/2020
ms.topic: how-to
ms.custom: acquisition
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3f4040023dd023db351571482ac2a17c18b46e06
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112932"
---
# <a name="modify-visual-studio-workloads-components-and-language-packs"></a>Visual Studio iş yüklerini, bileşenlerini ve dil paketlerini değiştirme

::: moniker range="vs-2019"

Visual Studio 'Yu, istediğinizde yalnızca istediğiniz şeyi içerecek şekilde değiştirmek kolaydır. Bunu yapmak için, iş yüklerini ve bileşenleri eklemek veya kaldırmak üzere Visual Studio Yükleyicisi açın.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 'yu, gerçekleştirmek istediğiniz görevlerle eşleşecek şekilde kişiselleştirmek için de daha kolay hale getirdik. Ayrıca, Visual Studio 'yu de özelleştirmeyi daha kolay hale getirdik. Bunu yapmak için yeni Visual Studio Yükleyicisi açın ve istediğiniz değişiklikleri yapın.

::: moniker-end

## <a name="prerequisites"></a>Önkoşullar

+ Visual Studio 'Yu yüklemek, güncelleştirmek ya da değiştirmek için yönetici izinlerine sahip bir hesapla oturum açmalısınız. Daha fazla bilgi için bkz. [Kullanıcı izinleri ve Visual Studio](../ide/user-permissions-and-visual-studio.md).

+ Aşağıdaki yordamlarda bir internet bağlantınız olduğunu varsaymaktadır. Daha önce oluşturulmuş bir Visual Studio [yüklemesinin](create-an-offline-installation-of-visual-studio.md) nasıl değiştirileceği hakkında daha fazla bilgi için bkz. [Visual Studio 'nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md) sayfası ve [ağ tabanlı Visual Studio dağıtımları için güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md) sayfası.

## <a name="launch-the-installer"></a>Yükleyiciyi başlatın

Yüklemenizde değişiklikler yapmak için Visual Studio yükleyicisi 'ni başlatmanız gerekir.

::: moniker range="vs-2017"

1. Bilgisayarınızda Visual Studio Yükleyicisi bulun.

     Örneğin, Windows 10 çalıştıran bir bilgisayarda **Başlat**' ı seçin ve ardından **Visual Studio yükleyicisi** olarak listelendiği **V** harfine gidin.

     ![Visual Studio Yükleyicisi](media/locate-the-visual-studio-installer.png "Microsoft Visual Studio yükleyicisini bulun")

     >[!TIP]
     >Bazı bilgisayarlarda Visual Studio Yükleyicisi, **Microsoft Visual Studio yükleyicisi** olarak **"d"** harfi altında listelenmiş olabilir.<br/><br/> Alternatif olarak, Visual Studio Yükleyicisi aşağıdaki konumda bulabilirsiniz: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Yükleyiciyi açın ve ardından **Değiştir**' i seçin.

     ![Visual Studio 'Yu başlatma veya değiştirme](media/modify-visual-studio.png "Visual Studio 2017'yi Değiştirme")

     > [!IMPORTANT]
     > Bekleyen bir güncelleştirmeniz varsa Değiştir düğmesi farklı bir yerdir. Bu şekilde, Visual Studio 'Yu güncelleştirme olmadan değiştirebilirsiniz, bunu yapmanız gerekir. **Daha fazla**' ya tıklayın ve ardından **Değiştir**' i seçin.
     >
     > ![Visual Studio 'Yu güncelleştirme veya değiştirme](media/modify-or-update-visual-studio.png "Visual Studio 2017 'yi güncelleştirme veya değiştirme")

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

1. Yükleyicide, yüklediğiniz Visual Studio sürümünü bulun ve ardından **Değiştir**' i seçin.

     ![Visual Studio sürümünü seçin ve ardından Değiştir](media/vs-2019/vs-installer-modify.png "Visual Studio 2019 Edition ' ı seçin ve ardından değiştirin")

     > [!IMPORTANT]
     > Bekleyen bir güncelleştirmeniz varsa Değiştir düğmesi farklı bir yerdir. Bu şekilde, Visual Studio 'Yu güncelleştirme olmadan değiştirebilirsiniz, isterseniz. **Daha fazla**' yı seçin ve ardından **Değiştir**' i seçin.
     >
     > ![Visual Studio 'Yu güncelleştirme veya değiştirme](media/vs-2019/modify-update-visual-studio.png "Visual Studio 2019 'yi güncelleştirme veya değiştirme")

::: moniker-end

## <a name="change-workloads-or-individual-components"></a>İş yüklerini veya ayrı bileşenleri değiştirme

::: moniker range="vs-2017"

 [Iş yükleri](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) , kullanmakta olduğunuz programlama dili veya platformu için gereken özellikleri içerir. İş yüklerini kullanarak Visual Studio 'Yu, yapmak istediğiniz çalışmayı, yapmak istediğiniz işi destekleyecek şekilde değiştirin.

1. Visual Studio Yükleyicisi, **Iş yükleri** sekmesini seçin ve ardından istediğiniz iş yüklerini seçin veya seçimini kaldırın.

   Alternatif olarak, Visual Studio yüklemenizi özelleştirmek için iş yüklerini kullanmak istemiyorsanız, **bireysel bileşenler** sekmesini seçin ve istediğiniz bileşenleri seçin ve ardından istemleri izleyin.

    ![Visual Studio 2017 kurulum iletişim kutusu](media/modify-workloads.png "Visual Studio 2019 'de iş yükü seçme")

1. **İndirme sırasında varsayılan yüklemeyi** kabul etmek mi yoksa **Tümünü indir ve yükle** seçeneğini belirleyin.

    ![Visual Studio 2017 kurulum seçenekleri](media/vs-2019/vs-installer-choose-install-or-download.png "İlk kez karşıdan yükleme veya indirme sırasında yüklemeyi seçin ve daha sonra yükleyin")

    Önce indirmek ve sonra yüklemek istiyorsanız "tümünü Indir ve Yükle" seçeneği kullanışlıdır.

1. **Değiştir**'i seçin.

1. İsterseniz, **Iş yükleri** sekmesini seçin ve ardından istediğiniz iş yüklerini seçin veya seçimini kaldırın.


1. Yeni iş yükleri yüklendikten sonra Visual Studio 'Yu açmak için Visual Studio Yükleyicisi **Başlat** ' ı seçin.

::: moniker-end

::: moniker range="vs-2019"

 İş yükleri, kullanmakta olduğunuz programlama dili veya platformu için gereken özellikleri içerir. İş yüklerini kullanarak Visual Studio 'Yu, yapmak istediğiniz çalışmayı, yapmak istediğiniz işi destekleyecek şekilde değiştirin.

 > [!TIP]
>Geliştirme için ihtiyaç duyduğunuz araç ve bileşen paketleri hakkında daha fazla bilgi için bkz. [Visual Studio iş yükleri](https://visualstudio.microsoft.com/vs/#workloads).

1. Visual Studio Yükleyicisi, **Iş yükleri** sekmesini seçin ve ardından istediğiniz iş yüklerini seçin veya seçimini kaldırın.

    ![Visual Studio 2019 kurulum iletişim kutusu](media/vs-2019/vs-installer-modify-workloads.png "Visual Studio 2019 'de iş yükü seçme")

1. **İndirme sırasında varsayılan yüklemeyi** kabul etmek mi yoksa **Tümünü indir ve yükle** seçeneğini belirleyin.

    ![Visual Studio 2019 kurulum seçenekleri](media/vs-2019/vs-installer-choose-install-or-download.png "İlk kez karşıdan yükleme veya indirme sırasında yüklemeyi seçin ve daha sonra yükleyin")

    Önce indirmek ve sonra yüklemek istiyorsanız "tümünü Indir ve Yükle" seçeneği kullanışlıdır.

1. **Değiştir**'i seçin.

1. Yeni iş yükleri yüklendikten sonra Visual Studio 'Yu açmak için Visual Studio Yükleyicisi **Başlat** ' ı seçin.

::: moniker-end


>[!TIP]
> SQL Server Veri Araçları (SSDT) bileşeni hakkında daha fazla bilgi için bkz. [Visual Studio IÇIN SSDT indirme ve yükleme](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15&preserve-view=true).

## <a name="modify-language-packs"></a>Dil paketlerini değiştirme

Varsayılan olarak, yükleyici ilk kez çalıştırıldığında işletim sisteminin diliyle eşleşir. Ancak, dili istediğiniz zaman değiştirebilirsiniz. 

Bunun için:
1. Visual Studio Yükleyicisi **dil paketleri** sekmesini seçin.
2. Tercih ettiğiniz dili seçin.
3. İstenen işlemleri gerçekleştirin.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio iş yükünün & bileşen kimliklerinin listesi](workload-and-component-ids.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
