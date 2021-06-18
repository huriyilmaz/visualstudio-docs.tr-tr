---
title: İş Visual Studio, bileşen ve dil & değiştirme
titleSuffix: ''
description: Adım adım Visual Studio değiştirmeyi öğrenin.
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
ms.openlocfilehash: 638ec555a6fbef53d19a15c8a6cde26ff121aa0e
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306988"
---
# <a name="modify-visual-studio-workloads-components-and-language-packs"></a>İş Visual Studio, bileşenler ve dil paketlerini değiştirme

::: moniker range=">=vs-2019"

Yalnızca istediğiniz Visual Studio, istediğiniz zaman dahil etmek için bu ayarları değiştirebilirsiniz. Bunu yapmak için iş yüklerini ve Visual Studio Yükleyicisi eklemek veya kaldırmak için uygulamanın açık olduğu sayfayı açın.

::: moniker-end

::: moniker range="vs-2017"

Yalnızca gerçekleştirmek istediğiniz görevlerle eşleşmesi için Visual Studio özelleştirmenizi kolaylaştırmanızı değil, aynı zamanda Visual Studio özelleştirmeyi de kolaylaştıracağız. Bunu yapmak için yeni Visual Studio Yükleyicisi açın ve istediğiniz değişiklikleri yapın.

::: moniker-end

## <a name="prerequisites"></a>Önkoşullar

+ Bir hesabı yüklemek, güncelleştirmek Visual Studio değiştirmek için yönetici izinlerine sahip bir hesap ile oturum açabilirsiniz. Daha fazla bilgi için [bkz. Kullanıcı izinleri ve Visual Studio.](../ide/user-permissions-and-visual-studio.md)

+ Aşağıdaki yordamlar, bir İnternet bağlantınız olduğunu varsaymanızı sağlar. Visual Studio'nin önceden oluşturulmuş çevrimdışı [](create-an-offline-installation-of-visual-studio.md) yüklemesini değiştirme hakkında daha fazla bilgi için hem [Visual Studio'nin](update-a-network-installation-of-visual-studio.md) ağ tabanlı yüklemesini güncelleştirme sayfasına hem de Ağ tabanlı dağıtımlarda [güncelleştirmeleri denetleme Visual Studio](controlling-updates-to-visual-studio-deployments.md) bakın.

## <a name="launch-the-installer"></a>Yükleyiciyi başlatın

Yüklemeniz üzerinde değişiklik yapmak için, yükleme yükleyicisini Visual Studio gerekir.

::: moniker range="vs-2017"

1. Bilgisayarınızda Visual Studio Yükleyicisi'ı bulun.

     Örneğin, Windows 10 çalıştıran bir bilgisayarda Başlat'ı seçin ve ardından **V** harfine kaydırın ve burada dosya adı **olarak Visual Studio Yükleyicisi.** 

     ![Visual Studio Yükleyicisi](media/locate-the-visual-studio-installer.png "Microsoft Visual Studio Yükleyicisini bulma")

     >[!TIP]
     >Bazı bilgisayarlarda, Visual Studio Yükleyicisi yükleyicisi olarak **"M"** harfi altında **Microsoft Visual Studio olabilir.**<br/><br/> Alternatif olarak, aşağıdaki Visual Studio Yükleyicisi aşağıdaki konumda bulabilirsiniz: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Yükleyiciyi açın ve Değiştir'i **seçin.**

     ![Uygulamayı başlatma veya Visual Studio](media/modify-visual-studio.png "Visual Studio 2017'yi Değiştirme")

     > [!IMPORTANT]
     > Bekleyen bir güncelleştirmeniz varsa Değiştir düğmesi farklı bir yerdedir. Bu şekilde, güncelleştirmeden Visual Studio veya kullanmayı tercih ediyor olabilir. Diğer **'e** tıklayın ve ardından **Değiştir'i seçin.**
     >
     > ![Güncelleştirme veya değiştirme Visual Studio](media/modify-or-update-visual-studio.png "2017'Visual Studio güncelleştirme veya değiştirme")

::: moniker-end

::: moniker range=">=vs-2019"

1. Bilgisayarınızda **Visual Studio Yükleyicisi'ı** bulun.

     Windows Başlat menüsü", "yükleyici" için arama da kullanabilirsiniz.

     ![Visual Studio Yükleyicisi](media/vs-2019/visual-studio-installer.png "Arama Visual Studio Yükleyicisi")

     > [!NOTE]
     > Aşağıdaki konumda Visual Studio Yükleyicisi da bulabilirsiniz:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekir. Öyleyse, istemleri izleyin.

1. Yükleyicide, yüklü olan Visual Studio sürümünü ve ardından Değiştir'i **seçin.**

     ![Bir Visual Studio seçin ve sonra da değiştirme](media/vs-2019/vs-installer-modify.png "2019 Visual Studio'ı seçin ve ardından değiştir")

     > [!IMPORTANT]
     > Bekleyen bir güncelleştirmeniz varsa Değiştir düğmesi farklı bir yerdedir. Bu şekilde, Visual Studio güncelleştirmeden değiştirebilirsiniz. Diğer **'i** ve ardından **Değiştir'i seçin.**
     >
     > ![Güncelleştirme veya değiştirme Visual Studio](media/vs-2019/modify-update-visual-studio.png "2019'Visual Studio güncelleştirme veya değiştirme")

::: moniker-end

## <a name="change-workloads-or-individual-components"></a>İş yüklerini veya tek tek bileşenleri değiştirme

::: moniker range="vs-2017"

 [İş yükleri,](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) kullanmakta olduğunu programlama dili veya platform için ihtiyacınız olan özellikleri içerir. İş yüklerini kullanarak Visual Studio yapmak istediğiniz işi ( istediğiniz zaman) desteklesin.

1. Aşağıdaki Visual Studio Yükleyicisi İş Yükleri **sekmesini** seçin ve ardından istediğiniz iş yüklerini seçin veya seçimi kaldırın.

   Alternatif olarak, iş yüklerini kullanarak Visual Studio yüklemenizi özelleştirmek istemiyorsanız, Bağımsız  Bileşenler sekmesini seçin ve istediğiniz bileşenleri seçin ve ardından istemleri izleyin.

    ![Visual Studio 2017 kurulum iletişim kutusu](media/modify-workloads.png "Visual Studio 2019'da iş yükü seçme")

1. İndirme sırasında varsayılan Yükle seçeneğini mi yoksa **Hepsini indir** ve yükle seçeneğini mi kabul **etmek istediğinizi** seçin.

    ![Visual Studio 2017 kurulum seçenekleri](media/vs-2019/vs-installer-choose-install-or-download.png "İndirme sırasında yükleme veya ilk olarak indirmeyi ve daha sonra yüklemeyi seçin")

    İlk olarak indirip daha sonra yüklemek için "Hepsini indir, sonra yükle" seçeneği kullanışlıdır.

1. **Değiştir'i seçin.**

1. İsterseniz İş Yükleri **sekmesini** seçin ve ardından istediğiniz iş yüklerini seçin veya seçimi kaldırın.

1. Yeni iş yükleri yüklendikten sonra, yeni **iş** yüklerini açmak için Visual Studio Yükleyicisi Başlat'ı Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

 İş yükleri, kullanmakta olduğunu programlama dili veya platform için ihtiyacınız olan özellikleri içerir. İş yüklerini kullanarak Visual Studio yapmak istediğiniz işi ( istediğiniz zaman) desteklesin.

 > [!TIP]
>Geliştirme için hangi araç ve bileşen paketlerine ihtiyacınız olduğu hakkında daha fazla bilgi için [bkz. Visual Studio iş yükleri.](https://visualstudio.microsoft.com/vs/#workloads)

1. Aşağıdaki Visual Studio Yükleyicisi İş Yükleri **sekmesini** seçin ve ardından istediğiniz iş yüklerini seçin veya seçimi kaldırın.

    ![Visual Studio 2019 kurulumu iletişim kutusu](media/vs-2019/vs-installer-modify-workloads.png "Visual Studio 2019'da iş yükü seçme")

1. İndirme sırasında varsayılan Yükle seçeneğini mi yoksa **Hepsini indir** ve yükle seçeneğini mi kabul **etmek istediğinizi** seçin.

    ![Visual Studio 2019 kurulum seçenekleri](media/vs-2019/vs-installer-choose-install-or-download.png "İndirme sırasında yükleme veya ilk olarak indirmeyi ve daha sonra yüklemeyi seçin")

    İlk olarak indirip daha sonra yüklemek için "Hepsini indir, sonra yükle" seçeneği kullanışlıdır.

1. **Değiştir'i seçin.**

1. Yeni iş yükleri yüklendikten sonra, yeni **iş** yüklerini açmak için Visual Studio Yükleyicisi Başlat'ı Visual Studio.

::: moniker-end

>[!TIP]
> SQL Server Veri Araçları (SSDT) bileşeni hakkında bilgi için bkz. Visual Studio için [SSDT'yi indirme ve yükleme.](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15&preserve-view=true)

## <a name="modify-language-packs"></a>Dil paketlerini değiştirme

Varsayılan olarak, yükleyici ilk kez çalıştırılana işletim sisteminin diliyle eşler. Ancak dili istediğiniz zaman değiştirebilirsiniz. 

Bunun için:

1. Giriş sekmesinde **Dil** paketleri sekmesini Visual Studio Yükleyicisi.
1. İstediğiniz dili seçin.
1. İstenen işlemleri gerçekleştirin.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Bileşen Visual Studio iş & listesi](workload-and-component-ids.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
