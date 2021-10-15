---
title: İş Visual Studio, bileşen ve dil & değiştirme
titleSuffix: ''
description: Adım adım Visual Studio değiştirmeyi öğrenin.
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
ms.openlocfilehash: 845355d71670c98952b414ebe7b5f04901823ebf
ms.sourcegitcommit: 72f8ce4992cc62c4833e6dcb0f79febb328c44be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2021
ms.locfileid: "130011269"
---
# <a name="modify-visual-studio-workloads-components-and-language-packs"></a>İş Visual Studio, bileşenler ve dil paketlerini değiştirme

::: moniker range=">=vs-2019"

Yalnızca istediğiniz Visual Studio, istediğiniz zaman dahil etmek için bu ayarları değiştirebilirsiniz. Bunu yapmak için, Visual Studio Yükleyicisi ve ardından iş yüklerini, bileşenleri ve dil paketlerini ekleyin veya kaldırın.

::: moniker-end

::: moniker range="vs-2017"

Yalnızca gerçekleştirmek istediğiniz görevlerle eşleşmesi için Visual Studio özelleştirmenizi kolaylaştırmakla birlikte, aynı zamanda Visual Studio özelleştirebilirsiniz. Bunu yapmak için yeni Visual Studio Yükleyicisi açın ve istediğiniz değişiklikleri yapın.

::: moniker-end

## <a name="prerequisites"></a>Önkoşullar

- Bu bilgileri yüklemek, değiştirmek Visual Studio güncelleştirmek için yönetici olarak Visual Studio Yükleyicisi çalıştırmanız gerekir. Normal bir kullanıcı olarak Visual Studio değiştirmeyi denerseniz, sizden yönetici kimlik bilgileri isteminde bir Kullanıcı Hesabı Denetimi bildirimi alırsınız. Daha fazla bilgi için [bkz. Kullanıcı izinleri ve Visual Studio.](../ide/user-permissions-and-visual-studio.md)

- Aşağıdaki yordamlar bir İnternet bağlantınız olduğunu varsaymanızı sağlar. Önceden oluşturulmuş bir çevrimdışı yüklemesini değiştirme hakkında daha [fazla bilgi için](create-an-offline-installation-of-visual-studio.md) Visual Studio:
  - [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
  - [Ağ tabanlı dağıtımlarda güncelleştirmeleri Visual Studio denetleme](controlling-updates-to-visual-studio-deployments.md)

## <a name="launch-the-installer-to-modify-your-installation"></a>Yüklemenizi değiştirmek için yükleyiciyi başlatın

Uygulama yüklemenizi Visual Studio için önce Visual Studio Yükleyicisi başlatmanız ve ardından değiştirerek bir Visual Studio seçmeniz gerekir.

::: moniker range="vs-2017"

1. Bilgisayarınızda Visual Studio Yükleyicisi'ı bulun.

     Örneğin, veya sonraki bir Windows 10 çalıştıran bir bilgisayarda Başlat'ı seçin ve **ardından V** harfine kaydırın ve burada dosya adı **olarak Visual Studio Yükleyicisi.**

     ![Giriş giriş Visual Studio Yükleyicisi gösteren ekran Windows 10 Başlat menüsü.](media/locate-the-visual-studio-installer.png "Microsoft Visual Studio Yükleyicisini bulma")

     >[!TIP]
     >Bazı bilgisayarlarda, Visual Studio Yükleyicisi Yükleyicisi olarak **"M"** harfi altında **Microsoft Visual Studio olabilir.**<br/><br/> Alternatif olarak, Visual Studio Yükleyicisi aşağıdaki konumda bulabilirsiniz:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Yükleyiciyi açın ve Değiştir'i **seçin.**

     ![Dosyanın içinde Değiştir düğmesini gösteren Visual Studio Yükleyicisi.](media/modify-visual-studio.png "Visual Studio 2017'yi Değiştirme")

     > [!IMPORTANT]
     > Bekleyen bir güncelleştirmeniz varsa Değiştir düğmesi farklı bir yerdedir. Bu şekilde, güncelleştirmeden Visual Studio değişiklik de (tercih etmek zorunda kalmadan) değiştirebilirsiniz. Diğer **'e** tıklayın ve ardından **Değiştir'i seçin.**
     >
     > ![Güncelleştirme beklemede olduğunda diğer Visual Studio Yükleyicisi menüsünde bulunan Değişiklik düğmesini gösteren ekran görüntüsü.](media/modify-or-update-visual-studio.png "2017'Visual Studio güncelleştirme veya değiştirme")

::: moniker-end

::: moniker range="vs-2019"

1. Bilgisayarınızda **Visual Studio Yükleyicisi'ı** bulun.

     Bu Windows Başlat menüsü "yükleyici" için arama da ve ardından.

     ![Bir uygulamanın, Başlat menüsü aramanın sonuçlarını gösteren Visual Studio Yükleyicisi.](media/vs-2019/visual-studio-installer.png "Arama Visual Studio Yükleyicisi")

     > [!NOTE]
     > Aşağıdaki konumda Visual Studio Yükleyicisi da bulabilirsiniz:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekir. Öyleyse, istemleri izleyin.

1. Yükleyicide, yüklü olan Visual Studio sürümünü ve ardından Değiştir'i **seçin.**

     ![Visual Studio Yükleyicisi'daki Visual Studio listesini gösteren ekran Visual Studio Yükleyicisi.](media/vs-2019/vs-installer-modify.png "2019 Visual Studio'ı seçin ve ardından değiştir")

     > [!IMPORTANT]
     > Bekleyen bir güncelleştirmeniz varsa Değiştir düğmesi farklı bir yerdedir. Bu şekilde, Visual Studio güncelleştirmeden değiştirebilirsiniz. **Diğer'i** ve ardından Değiştir'i **seçin.**
     >
     > ![Güncelleştirme beklemede olduğunda diğer Visual Studio Yükleyicisi menüsünde bulunan Değişiklik düğmesini gösteren ekran görüntüsü.](media/vs-2019/modify-update-visual-studio.png "2019'Visual Studio güncelleştirme veya değiştirme")

::: moniker-end

::: moniker range=">=vs-2022"

1. Bu dosyayı açmanın birçok yolu Visual Studio Yükleyicisi:

   - Bu Windows Başlat menüsü "yükleyici" araması ve ardından sonuçlardan **Visual Studio Yükleyicisi'yi** seçin.

     ![Bir uygulamanın, Başlat menüsü aramanın sonuçlarını gösteren Visual Studio Yükleyicisi.](media/vs-2022/vs-installer.png "Arama Visual Studio Yükleyicisi")

   - Şu yolda Visual Studio Yükleyicisi dosya yürütülebilir dosyasını çalıştırın:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   - Açık olan Visual Studio Araçlar Araçları  ve Özellikleri Al... öğesini > **seçin.** Bu seçim, Visual Studio Yükleyicisi.

     ![Visual Studio 2022 araçları menüsünü gösteren ekran görüntüsü.](media/vs-2022/vs-tools-menu.png "Visual Studio 2022 araçları menüsü")

   Devam etmeden önce güncelleştirmeniz Visual Studio Yükleyicisi istendiğinde. Öyleyse, istemleri izleyin.

1. Aşağıdaki Visual Studio Yükleyicisi, değiştirmek istediğiniz Visual Studio yüklemesini ve ardından Değiştir **düğmesini** seçin.

     ![Visual Studio Yükleyicisi'daki Visual Studio listesini gösteren ekran Visual Studio Yükleyicisi.](media/vs-2022/vs-installer-modify.png "Değiştirecek Visual Studio bir yükleme seçin")

::: moniker-end

## <a name="change-workloads-or-individual-components"></a>İş yüklerini veya tek tek bileşenleri değiştirme

::: moniker range="vs-2017"

 [İş yükleri,](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) kullanmakta olduğu programlama dili veya platform için ihtiyacınız olan özellikleri içerir. İş yüklerini kullanarak Visual Studio, yapmak istediğiniz işi ne zaman yapmak istediğinize yardımcı olacak şekilde değiştirebilirsiniz.

1. Aşağıdaki Visual Studio Yükleyicisi İş Yükleri **sekmesini** seçin ve ardından istediğiniz iş yüklerini seçin veya seçimi kaldırın.

   Alternatif olarak, Visual Studio yüklemenizi özelleştirmek için iş yüklerini kullanmak istemiyorsanız  Bağımsız Bileşenler sekmesini seçin ve istediğiniz bileşenleri seçin ve ardından yönergeleri izleyin.

    ![Uygulamanın İş Yükleri sekmesini gösteren Visual Studio Yükleyicisi.](media/modify-workloads.png "Visual Studio 2017'de iş yükü seçme")

1. İndirme sırasında varsayılan Yükle seçeneğini mi yoksa **Hepsini indir** ve yükle seçeneğini mi kabul **etmek istediğinizi** seçin.

    ![Uygulamanın yükleme ve indirme seçeneklerini gösteren Visual Studio Yükleyicisi.](media/vs-2019/vs-installer-choose-install-or-download.png "İndirme sırasında yükleme veya ilk olarak indirmeyi ve daha sonra yüklemeyi seçin")

    İlk olarak indirip daha sonra yüklemek için "Hepsini indir, sonra yükle" seçeneği kullanışlıdır.

1. **Değiştir'i seçin.**

1. İsterseniz İş Yükleri **sekmesini** seçin ve ardından istediğiniz iş yüklerini seçin veya seçimi kaldırın.

1. Yeni iş yükleri yüklendikten sonra, yeni **iş** yüklerini açmak için Visual Studio Yükleyicisi Başlat'ı Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

 İş yükleri, kullanmakta olduğu programlama dili veya platform için ihtiyacınız olan özellikleri içerir. İş yüklerini kullanarak Visual Studio, yapmak istediğiniz işi ne zaman yapmak istediğinize yardımcı olacak şekilde değiştirebilirsiniz.

 > [!TIP]
>Geliştirme için hangi araç ve bileşen paketlerine ihtiyacınız olduğu hakkında daha fazla bilgi için [bkz. Visual Studio.](https://visualstudio.microsoft.com/vs/#workloads).

1. Aşağıdaki Visual Studio Yükleyicisi İş Yükleri **sekmesini** seçin ve ardından istediğiniz iş yüklerini seçin veya seçimi kaldırın.

    ![Uygulamanın İş Yükleri sekmesini gösteren Visual Studio Yükleyicisi.](media/vs-2019/vs-installer-modify-workloads.png "Visual Studio 2019'da iş yükü seçme")

1. İndirme sırasında varsayılan Yükle seçeneğini mi yoksa **Hepsini indir** ve yükle seçeneğini mi kabul **etmek istediğinizi** seçin.

    ![Uygulamanın yükleme ve indirme seçeneklerini gösteren Visual Studio Yükleyicisi.](media/vs-2019/vs-installer-choose-install-or-download.png "İndirme sırasında yükleme veya ilk olarak indirmeyi ve daha sonra yüklemeyi seçin")

    İlk olarak indirip daha sonra yüklemek için "Hepsini indir, sonra yükle" seçeneği kullanışlıdır.

1. **Değiştir'i seçin.**

1. Yeni iş yükleri yüklendikten sonra, yeni **iş** yüklerini açmak için Visual Studio Yükleyicisi Başlat'ı Visual Studio.

::: moniker-end

::: moniker range=">=vs-2022"

İş yükleri, kullanmakta olduğu programlama dili veya platform için ihtiyacınız olan bileşenleri içerir. İş yüklerini kullanarak Visual Studio, yapmak istediğiniz işi ne zaman yapmak istediğinize yardımcı olacak şekilde değiştirebilirsiniz.

> [!TIP]
> Geliştirme için hangi araçlara ve bileşen paketlerine ihtiyacınız olduğu hakkında daha fazla bilgi için [bkz. Visual Studio iş yükleri.](https://visualstudio.microsoft.com/vs/#workloads)

1. Aşağıdaki Visual Studio Yükleyicisi İş Yükleri **sekmesini** seçin ve ardından istediğiniz iş yüklerini seçin veya seçimi kaldırın.

    ![Uygulamanın İş Yükleri sekmesini gösteren Visual Studio Yükleyicisi.](media/vs-2022/vs-installer-modify-workloads.png "İş yüklerini Visual Studio Yükleyicisi")

1. Bir iş yükünden daha fazla bileşen eklemek için Tek bileşenler sekmesini **seçin** ve ardından istediğiniz bileşenleri seçin veya seçimi kaldırın.

    ![Uygulamanın Bağımsız bileşenler sekmesini gösteren Visual Studio Yükleyicisi.](media/vs-2022/vs-installer-individual-components.png "Tek tek bileşenleri Visual Studio Yükleyicisi")

1. İndirme sırasında Yükle veya **Hepsini indir'i** **seçin, sonra yükleyin.** Varsayılan seçenek olan **yükleme indirirken yükle** seçeneği, yüklemeyi daha önce başlatarak genel zamandan tasarruf sağlar.

    ![Uygulamanın yükleme ve indirme seçeneklerini gösteren Visual Studio Yükleyicisi.](media/vs-2022/vs-installer-choose-install-or-download.png "Uygulamanın içinde sıra seçeneklerini indirme ve Visual Studio Yükleyicisi")

1. **Değiştir'i seçin.**

1. Değiştirilen iş yükleri veya bileşenler yüklendikten  sonra, 2022 RC'yi Visual Studio Yükleyicisi için Visual Studio'ı seçin.

::: moniker-end

> [!TIP]
> SQL Server Veri Araçları (SSDT) bileşeni hakkında bilgi için bkz. Visual Studio için [SSDT'yi indirme ve yükleme.](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15&preserve-view=true)

## <a name="modify-language-packs"></a>Dil paketlerini değiştirme

Bu Visual Studio Yükleyicisi, işletim sisteminin diliyle eşleşen Visual Studio için varsayılan dil paketini seçer. Ancak, varsayılan dili istediğiniz zaman değiştirebilirsiniz.

Bunun için:

1. Giriş **sekmesinde Dil** paketleri sekmesini Visual Studio Yükleyicisi.
1. İstediğiniz dili seçin.
1. İstenen işlemleri gerçekleştirin.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Bileşen Visual Studio iş & listesi](workload-and-component-ids.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
