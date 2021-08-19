---
ms.date: 08/11/2021
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: tglee
author: TerryGLee
manager: jmartens
ms.topic: include
ms.openlocfilehash: 058bb38112e89ed77cc01eae59d16a827c88c11a
ms.sourcegitcommit: 51a01cc1f1feeac9432c7989db4578e30a573fa1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2021
ms.locfileid: "122274073"
---
::: moniker range=">=vs-2019"

## <a name="add-git-source-control"></a>Git kaynak denetimi ekleme

Artık uygulama oluşturduğunuza göre, bunu bir Git deposuna eklemek iyi olabilir. Size bu kapsamın altında bulunduk; Visual Studio doğrudan IDE'den kullanabileceğiniz Git araçlarıyla bu işlemi kolaylaştırır.

> [!TIP]
> Git en yaygın olarak kullanılan modern sürüm denetimi sistemidir, bu nedenle profesyonel bir geliştirici olun veya kod kodla ilgili bilgi edinseniz Git sizin için çok yararlı olabilir. Git'i yeni başladıysanız, [https://git-scm.com/](https://git-scm.com/) web sitesi başlamak için iyi bir yerdir. Burada bilgi sayfaları, popüler bir çevrimiçi kitap ve Git Temel Bilgileri videoları bulabilirsiniz.

Kodunuzu Git ile ilişkilendirmek için, kodunuzun bulunduğu yeni bir Git deposu oluşturarak başlarsiniz. Aşağıdaki adımları uygulayın:

1. Kaynak Denetimi'nin sağ alt köşesindeki durum Visual Studio Ekle **düğmesini** ve ardından **Git'i seçin.**

    :::image type="content" source="../media/vs-2022/git-add-source-control.png" alt-text="Çözüm Gezgini bölmesinin altındaki Git kaynak denetimi düğmelerinin ekran görüntüsü, Kaynak Denetimine Ekle düğmesi vurgulanmış.":::

1. Git **deposu oluştur iletişim kutusunda,** depoda oturum GitHub.

    :::image type="content" source="../media/vs-2022/git-create-repo.png" alt-text="Git Deposunda Oturum Aç iletişim penceresinin ekran görüntüsü. Bu pencerede oturum GitHub.":::

    Depo adı, klasör konumunuz temel alarak otomatik olarak doldurulur. Varsayılan olarak, yeni deponuz özeldir, yani depoya yalnızca siz erişesiniz.

    > [!TIP]
    > Deponun genel veya özel olup olmadığı, bir ekiple çalışmasanız bile kodunuzun uzaktan yedeklerinin güvenli bir GitHub depolanmış bir depoya sahip olmak en iyisidir. Bu sayede hangi bilgisayarı kullanıyor olursanız olun kodunuzun kullanımınıza hazır olur.

1. Oluştur ve **It'i seçin.**

    Depoyu oluşturduktan sonra durum çubuğunda durum ayrıntılarını bulabilirsiniz.

    :::image type="content" source="../media/vs-2022/git-new-private-repo-status-details.png" alt-text="Visual Studio'da yer alan bölmenin altındaki Çözüm Gezgini durum çubuğunun ekran Visual Studio.":::

    Okları olan ilk simge, geçerli dalda kaç tane giden/gelen işleme olduğunu gösterir. Bu simgeyi kullanarak tüm gelen işlemeleri çekebilir veya giden işlemeleri gönderebilirsiniz. İlk olarak bu işlemeleri de görüntülemeyi seçebilirsiniz. Bunu yapmak için simgeye tıklayın ve Ardından **Giden/Gelen'i Görüntüle'yi seçin.**

    Kalemle birlikte ikinci simge, kodunda yapılan ve işlanmamış değişikliklerin sayısını gösterir. Git Değişiklikleri penceresinde bu değişiklikleri görüntülemek için bu **simgeye tıkabilirsiniz.**

Git'i uygulamayla kullanma hakkında daha fazla bilgi edinmek için [Visual Studio denetim belgeleri sayfasına](../../version-control/index.yml) bakın.

::: moniker-end