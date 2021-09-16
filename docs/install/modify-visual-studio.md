---
title: Visual Studio iş yüklerini, bileşenleri & dil paketlerini değiştirme
titleSuffix: ''
description: Visual Studio, adım adım nasıl değiştirileceğini öğrenin.
ms.date: 09/14/2021
ms.topic: how-to
ms.custom: vs-acquisition
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 692b1aedf5c55d2162a28e96ae9cdbdadd9529e6
ms.sourcegitcommit: 811e4ee80311433fefbe6d6223bf72c431008403
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2021
ms.locfileid: "127890656"
---
# <a name="modify-visual-studio-workloads-components-and-language-packs"></a>Visual Studio iş yüklerini, bileşenleri ve dil paketlerini değiştirme

::: moniker range=">=vs-2019"

Visual Studio, istediğinizde yalnızca istediğiniz şeyi içerecek şekilde değiştirmek kolaydır. bunu yapmak için Visual Studio Yükleyicisi açın ve sonra iş yükleri, bileşenler ve dil paketleri ekleyin veya kaldırın.

::: moniker-end

::: moniker range="vs-2017"

yalnızca Visual Studio, gerçekleştirmek istediğiniz görevlerle eşleşecek şekilde kişiselleştirmek daha kolay hale getirdik. ayrıca, Visual Studio da özelleştirmeyi daha kolay hale getirdik. bunu yapmak için yeni Visual Studio Yükleyicisi açın ve istediğiniz değişiklikleri yapın.

::: moniker-end

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio yüklemek, değiştirmek veya güncelleştirmek için Visual Studio Yükleyicisi yönetici olarak çalıştırmanız gerekir. Visual Studio tipik bir kullanıcı olarak değiştirmeye çalışırsanız, yönetici kimlik bilgileri isteyip istemediğinizi soran bir kullanıcı hesabı denetimi bildirimi alırsınız. Daha fazla bilgi için bkz. [Kullanıcı izinleri ve Visual Studio](../ide/user-permissions-and-visual-studio.md).

- Aşağıdaki yordamlarda bir internet bağlantınız olduğunu varsaymaktadır. daha önce oluşturulmuş bir Visual Studio [çevrimdışı yüklemesinin](create-an-offline-installation-of-visual-studio.md) nasıl değiştirileceği hakkında daha fazla bilgi için bkz.:
  - [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
  - [ağ tabanlı Visual Studio dağıtımlarında güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)

## <a name="launch-the-installer-to-modify-your-installation"></a>Yüklemenizi değiştirmek için yükleyiciyi başlatın

Visual Studio yüklemenizi değiştirmek için önce Visual Studio Yükleyicisi başlatmanız ve sonra değiştirmek için bir Visual Studio yüklemesi seçmeniz gerekir.

::: moniker range="vs-2017"

1. bilgisayarınızda Visual Studio Yükleyicisi bulun.

     örneğin, Windows 10 çalıştıran bir bilgisayarda **başlat**' ı seçin ve sonra da **Visual Studio Yükleyicisi** olarak listelendiği **V** harfine gidin.

     ![Windows 10 Başlat menüsü Visual Studio Yükleyicisi girişi gösteren ekran görüntüsü.](media/locate-the-visual-studio-installer.png "Microsoft Visual Studio yükleyicisini bulun")

     >[!TIP]
     >bazı bilgisayarlarda Visual Studio Yükleyicisi, **Microsoft Visual Studio yükleyicisi** olarak **"d"** harfi altında listelenmiş olabilir.<br/><br/> alternatif olarak, Visual Studio Yükleyicisi aşağıdaki konumda bulabilirsiniz:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Yükleyiciyi açın ve ardından **Değiştir**' i seçin.

     ![Visual Studio Yükleyicisi değiştirme düğmesini gösteren ekran görüntüsü.](media/modify-visual-studio.png "Visual Studio 2017'yi Değiştirme")

     > [!IMPORTANT]
     > Bekleyen bir güncelleştirmeniz varsa Değiştir düğmesi farklı bir yerdir. bu şekilde, Visual Studio bunu güncelleştirmeden değiştirebilirsiniz, bunu yapmanız gerekir. **Daha fazla**' ya tıklayın ve ardından **Değiştir**' i seçin.
     >
     > ![bir güncelleştirme beklendiğinde daha fazla açılan menüde bulunan Visual Studio Yükleyicisi değiştir düğmesini gösteren ekran görüntüsü.](media/modify-or-update-visual-studio.png "Visual Studio güncelleştirin veya değiştirin 2017")

::: moniker-end

::: moniker range="vs-2019"

1. bilgisayarınızda **Visual Studio Yükleyicisi** bulun.

     Windows Başlat menüsü, "yükleyici" için arama yapabilirsiniz.

     ![Visual Studio Yükleyicisi için Başlat menüsü aramasının sonucunu gösteren ekran görüntüsü.](media/vs-2019/visual-studio-installer.png "Arama Visual Studio Yükleyicisi")

     > [!NOTE]
     > aşağıdaki konumda Visual Studio Yükleyicisi de bulabilirsiniz:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Bu durumda, istemleri izleyin.

1. yükleyicide, yüklediğiniz Visual Studio sürümünü bulun ve ardından **değiştir**' i seçin.

     ![Visual Studio Yükleyicisi Visual Studio yüklemelerinin listesini gösteren ekran görüntüsü.](media/vs-2019/vs-installer-modify.png "2019 Visual Studio'ı seçin ve ardından değiştir")

     > [!IMPORTANT]
     > Bekleyen bir güncelleştirmeniz varsa Değiştir düğmesi farklı bir yerdir. bu şekilde, Visual Studio güncelleştirmek zorunda kalmadan değişiklik yapabilirsiniz. **Daha fazla**' yı seçin ve ardından **Değiştir**' i seçin.
     >
     > ![bir güncelleştirme beklendiğinde daha fazla açılan menüde bulunan Visual Studio Yükleyicisi değiştir düğmesini gösteren ekran görüntüsü.](media/vs-2019/modify-update-visual-studio.png "2019'Visual Studio güncelleştirme veya değiştirme")

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio Yükleyicisi açmak için birçok yol vardır:

   - Windows Başlat menüsü, "yükleyici" araması yapabilir ve sonra sonuçlardan **Visual Studio Yükleyicisi** ' u seçebilirsiniz.

     ![Visual Studio Yükleyicisi için Başlat menüsü aramasının sonucunu gösteren ekran görüntüsü.](media/vs-2022/vs-installer.png "Arama Visual Studio Yükleyicisi")

   - bu yolda bulunan Visual Studio Yükleyicisi çalıştırılabilir dosyasını çalıştırın:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   - Visual Studio açıksa **araçlar** > **ve özellikler al**' ı seçin. Visual Studio Yükleyicisi açan araçlar... seçeneğini belirleyin.

     ![Visual Studio 2022 araçlar menüsünü gösteren ekran görüntüsü.](media/vs-2022/vs-tools-menu.png "Visual Studio 2022 araçları menüsü")

   devam etmeden önce Visual Studio Yükleyicisi güncelleştirmeniz istenebilir. Bu durumda, istemleri izleyin.

1. Visual Studio Yükleyicisi, değiştirmek istediğiniz Visual Studio yüklemeyi bulun ve **değiştir** düğmesini seçin.

     ![Visual Studio Yükleyicisi Visual Studio yüklemelerinin listesini gösteren ekran görüntüsü.](media/vs-2022/vs-installer-modify.png "Değiştirecek Visual Studio bir yükleme seçin")

::: moniker-end

## <a name="change-workloads-or-individual-components"></a>İş yüklerini veya ayrı bileşenleri değiştirme

::: moniker range="vs-2017"

 [Iş yükleri](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) , kullanmakta olduğunuz programlama dili veya platformu için gereken özellikleri içerir. Visual Studio değiştirmek için iş yüklerini kullanın, böylece yapmak istediğiniz iş işini destekler.

1. Visual Studio Yükleyicisi, **iş yükleri** sekmesini seçin ve ardından istediğiniz iş yüklerini seçin veya seçimini kaldırın.

   alternatif olarak, Visual Studio yüklemenizi özelleştirmek için iş yüklerini kullanmak istemiyorsanız, **tek tek bileşenler** sekmesini seçin ve istediğiniz bileşenleri seçin ve ardından istemleri izleyin.

    ![Visual Studio Yükleyicisi iş yükleri sekmesini gösteren ekran görüntüsü.](media/modify-workloads.png "Visual Studio 2017'de iş yükü seçme")

1. **İndirme sırasında varsayılan yüklemeyi** kabul etmek mi yoksa **Tümünü indir ve yükle** seçeneğini belirleyin.

    ![Visual Studio Yükleyicisi indirme ve yükleme seçeneklerini gösteren ekran görüntüsü.](media/vs-2019/vs-installer-choose-install-or-download.png "İndirme sırasında yükleme veya ilk olarak indirmeyi ve daha sonra yüklemeyi seçin")

    Önce indirmek ve sonra yüklemek istiyorsanız "tümünü Indir ve Yükle" seçeneği kullanışlıdır.

1. **Değiştir**'i seçin.

1. İsterseniz, **Iş yükleri** sekmesini seçin ve ardından istediğiniz iş yüklerini seçin veya seçimini kaldırın.

1. yeni iş yükleri yüklendikten sonra, Visual Studio açmak için Visual Studio Yükleyicisi **başlat** ' ı seçin.

::: moniker-end

::: moniker range="vs-2019"

 İş yükleri, kullanmakta olduğunuz programlama dili veya platformu için gereken özellikleri içerir. Visual Studio değiştirmek için iş yüklerini kullanın, böylece yapmak istediğiniz iş işini destekler.

 > [!TIP]
>geliştirme için ihtiyaç duyduğunuz araç ve bileşen paketleri hakkında daha fazla bilgi için bkz. [Visual Studio iş yükleri](https://visualstudio.microsoft.com/vs/#workloads).

1. Visual Studio Yükleyicisi, **iş yükleri** sekmesini seçin ve ardından istediğiniz iş yüklerini seçin veya seçimini kaldırın.

    ![Visual Studio Yükleyicisi iş yükleri sekmesini gösteren ekran görüntüsü.](media/vs-2019/vs-installer-modify-workloads.png "Visual Studio 2019'da iş yükü seçme")

1. **İndirme sırasında varsayılan yüklemeyi** kabul etmek mi yoksa **Tümünü indir ve yükle** seçeneğini belirleyin.

    ![Visual Studio Yükleyicisi indirme ve yükleme seçeneklerini gösteren ekran görüntüsü.](media/vs-2019/vs-installer-choose-install-or-download.png "İndirme sırasında yükleme veya ilk olarak indirmeyi ve daha sonra yüklemeyi seçin")

    Önce indirmek ve sonra yüklemek istiyorsanız "tümünü Indir ve Yükle" seçeneği kullanışlıdır.

1. **Değiştir**'i seçin.

1. yeni iş yükleri yüklendikten sonra, Visual Studio açmak için Visual Studio Yükleyicisi **başlat** ' ı seçin.

::: moniker-end

::: moniker range=">=vs-2022"

İş yükleri, kullanmakta olduğunuz programlama dili veya platformu için gereken bileşenleri içerir. Visual Studio değiştirmek için iş yüklerini kullanın, böylece yapmak istediğiniz iş işini destekler.

> [!TIP]
> geliştirme için ihtiyaç duyduğunuz araç ve bileşen paketleri hakkında daha fazla bilgi için bkz. [Visual Studio iş yükleri](https://visualstudio.microsoft.com/vs/#workloads).

1. Visual Studio Yükleyicisi, **iş yükleri** sekmesini seçin ve ardından istediğiniz iş yüklerini seçin veya seçimini kaldırın.

    ![Visual Studio Yükleyicisi iş yükleri sekmesini gösteren ekran görüntüsü.](media/vs-2022/vs-installer-modify-workloads.png "İş yüklerini Visual Studio Yükleyicisi")

1. Bir iş yükü yüklemesine göre daha fazla bileşen eklemek için, **tek tek bileşenler** sekmesini seçin ve istediğiniz bileşenleri seçin veya seçimi kaldırın.

    ![Visual Studio Yükleyicisi bireysel bileşenler sekmesini gösteren ekran görüntüsü.](media/vs-2022/vs-installer-individual-components.png "Sistem içinde tek tek bileşenleri Visual Studio Yükleyicisi")

1. Yükleme veya Indirme **sırasında yüklemek** isteyip istemediğinizi seçin **, sonra yükleyin**. **İndirme sırasında** varsayılan seçenek olan yükleme, daha önce yüklemeyi başlatarak genel saati kaydeder.

    ![Visual Studio Yükleyicisi indirme ve yükleme seçeneklerini gösteren ekran görüntüsü.](media/vs-2022/vs-installer-choose-install-or-download.png "Uygulamanın içinde sıra seçeneklerini indirme ve Visual Studio Yükleyicisi")

1. **Değiştir**'i seçin.

1. değiştirilen iş yükleri veya bileşenler yüklendikten sonra, Visual Studio Yükleyicisi Visual Studio 2022 önizlemesi 'ni açmak için **başlat** ' ı seçin.

::: moniker-end

> [!TIP]
> SQL Server Veri Araçları (ssdt) bileşeni hakkında daha fazla bilgi için bkz. [ssdt 'yi indirme ve yükleme Visual Studio](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15&preserve-view=true).

## <a name="modify-language-packs"></a>Dil paketlerini değiştirme

Visual Studio Yükleyicisi, işletim sisteminin diliyle eşleşen Visual Studio için varsayılan bir dil paketi seçer. Bununla birlikte, varsayılan dili istediğiniz zaman değiştirebilirsiniz.

Bunun için:

1. Visual Studio Yükleyicisi **dil paketleri** sekmesini seçin.
1. Tercih ettiğiniz dili seçin.
1. İstenen işlemleri gerçekleştirin.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [bileşen kimlikleri & Visual Studio iş yükü listesi](workload-and-component-ids.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
