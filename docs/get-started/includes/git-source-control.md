---
ms.date: 08/30/2021
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: tglee
author: TerryGLee
manager: jmartens
ms.topic: include
ms.openlocfilehash: e045d40958e339d497cea8509110618769649182
ms.sourcegitcommit: 559c662b2d60048300b76ea6ed3defaa2a259492
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2021
ms.locfileid: "127833356"
---
::: moniker range=">=vs-2019"

## <a name="add-git-source-control"></a>Git kaynak denetimi ekleme

Artık bir uygulama oluşturduğunuza göre, uygulamayı git deposuna eklemek iyi olabilir. Size yardımcı olabiliriz. Visual Studio doğrudan IDE'den kullanabileceğiniz Git araçlarıyla bu işlemi kolaylaştırır.

> [!TIP]
> Git en yaygın olarak kullanılan modern sürüm denetimi sistemidir, bu nedenle profesyonel bir geliştirici olun veya kod kodla ilgili bilgi edinseniz de Git çok yararlı olabilir. Git'i yeni başladıysanız, [https://git-scm.com/](https://git-scm.com/) web sitesi başlamak için iyi bir yerdir. Burada bilgi sayfaları, popüler bir çevrimiçi kitap ve Git Temel Bilgileri videoları bulabilirsiniz.

Kodunuzu Git ile ilişkilendirmek için, kodunuzun bulunduğu yeni bir Git deposu oluşturarak başlarsiniz. Aşağıdaki adımları uygulayın:

1. Dosyanın sağ alt köşesindeki durum çubuğunda Kaynak Denetimine Visual Studio'yi ve ardından **Git'i seçin.** 

    :::image type="content" source="../media/vs-2022/git-add-source-control.png" alt-text="Çözüm Gezgini bölmesinin altındaki Git kaynak denetimi düğmelerinin ekran görüntüsü, Kaynak Denetimine Ekle düğmesi vurgulanmış.":::

1. Git **deposu oluştur iletişim kutusunda,** git deposunda GitHub.

    :::image type="content" source="../media/vs-2022/git-create-repo.png" alt-text="Git Deposunda Oturum Aç iletişim penceresinin ekran görüntüsü. Bu pencerede oturum GitHub.":::

    Depo adı, klasör konumunuz temel alarak otomatik olarak tamamlar. Varsayılan olarak, yeni deponuz özeldir, yani depoya yalnızca siz erişesiniz.

    > [!TIP]
    > Deponun genel veya özel olup olmadığı, kodunuzun uzaktan yedeklerinin depolanmış bir depoda güvenli bir şekilde depolanmış GitHub. Bir ekiple çalışmıyorsanız bile, uzak depo kodunuzu herhangi bir bilgisayardan size sağlar.

1. Oluştur ve **It'i seçin.**

    Depoyu oluşturdukta durum çubuğunda durum ayrıntılarını bulabilirsiniz.

    :::image type="content" source="../media/vs-2022/git-new-private-repo-status-details.png" alt-text="Visual Studio'da, Çözüm Gezgini bölmesinin altındaki Visual Studio.":::

    Okları olan ilk simge, geçerli dalda kaç tane giden/gelen işleme olduğunu gösterir. Bu simgeyi kullanarak tüm gelen işlemeleri çekebilir veya giden işlemeleri gönderebilirsiniz. İlk olarak bu işlemeleri görüntülemeyi de seçebilirsiniz. Bunu yapmak için simgesini seçin ve ardından **Giden/Gelen'i Görüntüle'yi seçin.**

    Kalemle birlikte ikinci simge, kodunda yapılan ve işlanmamış değişikliklerin sayısını gösterir. Bu değişiklikleri Git Değişiklikleri penceresinde görüntülemek için bu **simgeyi seçin.**

Git'i uygulamanıza nasıl kullanabileceğiniz hakkında daha fazla bilgi edinmek için Visual Studio [belgelerine bakın.](../../version-control/index.yml)

::: moniker-end