---
ms.date: 08/30/2021
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: tglee
author: TerryGLee
manager: jmartens
ms.topic: include
ms.openlocfilehash: e045d40958e339d497cea8509110618769649182
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128373191"
---
::: moniker range=">=vs-2019"

## <a name="add-git-source-control"></a>Git kaynak denetimi Ekle

Artık bir uygulama oluşturduğunuza göre, bunu bir git deposuna eklemek isteyebilirsiniz. Size yardımcı olabiliriz. Visual Studio, doğrudan ıde 'den kullanabileceğiniz Git araçlarından daha kolay bir işlem yapar.

> [!TIP]
> Git, en yaygın olarak kullanılan modern sürüm denetim sistemidir. bu nedenle, profesyonel bir geliştirici olun veya nasıl kod kullanacağınızı öğreniyor olun, git çok faydalı olabilir. Git 'e yeni başladıysanız, [https://git-scm.com/](https://git-scm.com/) Web sitesi başlamak için iyi bir yerdir. Buradan, popüler bir çevrimiçi kitap ve git temel bilgileri videoları bulabilirsiniz.

Kodunuzu git ile ilişkilendirmek için, kodunuzun bulunduğu yeni bir git deposu oluşturarak başlayın. Aşağıdaki adımları uygulayın:

1. Visual Studio sağ alt köşesindeki durum çubuğunda **kaynak denetimine ekle**' yi seçin ve **Git**' i seçin.

    :::image type="content" source="../media/vs-2022/git-add-source-control.png" alt-text="Çözüm Gezgini bölmesinin altındaki git kaynak denetimi düğmelerinin ekran görüntüsü, kaynak denetimi Ekle düğmesi vurgulanır.":::

1. **Git deposu oluştur** iletişim kutusunda GitHub ' de oturum açın.

    :::image type="content" source="../media/vs-2022/git-create-repo.png" alt-text="GitHub 'de oturum açmak için bir git deposu oluştur iletişim penceresinin ekran görüntüsü.":::

    Depo adı, klasör konumunuza göre otomatik olarak doldurulur. Varsayılan olarak, yeni deponuz özeldir. Bu, kendisine erişebilen tek bir tane olduğu anlamına gelir.

    > [!TIP]
    > Deponuzda genel veya özel olup olmadığı, kodunuzun güvenli bir şekilde bir uzak yedeğinin GitHub. Bir ekip ile çalışmasanız bile, uzak bir depo, kodunuzun herhangi bir bilgisayardan sizin için kullanılabilir olmasını sağlar.

1. **Oluştur ve Gönder '** i seçin.

    Deponuzu oluşturduktan sonra durum çubuğunda durum ayrıntılarını görürsünüz.

    :::image type="content" source="../media/vs-2022/git-new-private-repo-status-details.png" alt-text="Visual Studio Çözüm Gezgini bölmesinin altında bulunan depo durum çubuğunun ekran görüntüsü.":::

    Oklara sahip ilk simge, geçerli dalınızda kaç tane giden/gelen işleme olduğunu gösterir. Herhangi bir gelen işlemeyi çekmek veya giden tüm işlemeleri göndermek için bu simgeyi kullanabilirsiniz. Bu yürütmeleri önce da görüntülemeyi seçebilirsiniz. Bunu yapmak için, simgeyi seçin ve ardından **giden/gelen görüntüle**' yi seçin.

    Kalemle ikinci simge, kodunuzda kaydedilmemiş değişiklik sayısını gösterir. **Git değişiklikleri** penceresinde bu değişiklikleri görüntülemek için bu simgeyi seçebilirsiniz.

Git 'i uygulamanızla birlikte kullanma hakkında daha fazla bilgi için, [Visual Studio sürüm denetimi belgelerine](../../version-control/index.yml)bakın.

::: moniker-end