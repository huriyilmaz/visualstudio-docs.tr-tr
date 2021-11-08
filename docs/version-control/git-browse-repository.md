---
title: Visual Studio bir depoya git
titleSuffix: ''
description: git deposu penceresini kullanarak Visual Studio git deposuna gözatamazsınız.
ms.date: 11/05/2021
ms.topic: how-to
author: Taysser-Gherfal
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: ad071fefa6d6069f35401ca777cdad07eb74ff36
ms.sourcegitcommit: 67dc39e93c86ba50eb5ca877b0471fb8ab8475ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2021
ms.locfileid: "132002563"
---
# <a name="browse-git-repositories-in-visual-studio"></a>Visual Studio git depolarına gözatmaya

Git değişiklikleri penceresi, kodunuzun dışında geçiş yapmak zorunda kalmadan, kodlarken git ile etkileşimde bulunmak için sorunsuz bir yol sağlar; Ancak, git deponuza odaklanmak için daha mantıklı bir zaman vardır. Örneğin, takımınızın üzerinde ne kadar çalıştığı hakkında iyi bir resim almanız veya bir hatayı araştırmak için iki işlemeyi karşılaştırmanız gerekebilir.

## <a name="browse-local-and-remote-branches"></a>Yerel ve uzak dallara gözatmaya

Başlamak için, Görünüm menüsünde **Git deposu** ' na tıklayarak git deposu penceresini açın. Git değişiklikleri penceresinde ve durum çubuğunda **giden/gelen** bağlantılara tıklayarak git deposu penceresine de erişebilirsiniz.

:::image type="content" source="media/vs-2022/git-repository-browse-ui.png" alt-text="Git deposu penceresinin anatomumu gösteren ekran görüntüsü":::

Git deposu penceresi, önceki ekran görüntüsünde gösterilen 3 ana bölüm içerir:
1. **Dallar:** Git, kullanıcıları birden çok görevle güçlendirmenize ve bunların dallarına göre kendi kodlarını denemenize olanak sağlar. Aynı anda birden çok özellik üzerinde çalışıyorsanız veya çalışma kodunuzu etkilemeden fikirleri araştırmak isterseniz, dallandırma çok faydalı olabilir.
1. **Git Graph:** Git Graph bölümü, dalınızın durumunu görselleştirir. Üç farklı bölüme sahiptir: gelen, giden ve yerel geçmişi. Gelen bölümünde, takımınızın katkıda bulunduğu gelen işlemeler gösterilir, giden bölümünde henüz gönderilmemiş olan yerel yürütmeleriniz gösterilir ve yerel geçmiş, yerel havuzunuz tarafından izlenen işlemelerin geri kalanını gösterir.
1. **işleme ayrıntıları:** Git Graph bölümünde herhangi bir işlemeyi tıklatmak, işlemelerin ayrıntılarını gösteren işleme ayrıntıları kullanıcı arabirimini açar. İşlemeler tarafından tanıtılan değişiklikleri, bunlara tıklayarak, fark gösterecek şekilde denetleyebilirsiniz. Örneğin, önceki ekran görüntüsünde, tek bir kaydın dosyalar. csproj dosyasına tanıtılan değişiklikleri görüntülediğimiz hakkında bilgi alabilirsiniz.

Dalınızı değiştirmek zorunda kalmadan herhangi bir yerel veya uzak dala gözatabilir ve odaklanmak istediğiniz bir kayıt bulduğunuzda, farklı **bir sekmede kaydet** ' e tıklayarak veya burada gösterildiği gibi farklı bir ekranda ekranı kaplamasını sağlayabilirsiniz.

:::image type="content" source="media/vs-2022/git-repository-open-new-tab.png" alt-text="Yeni sekmede nasıl açılacağı ekran görüntüsü":::

:::image type="content" source="media/vs-2022/git-repository-details-tab.png" alt-text="Kayıt ayrıntıları sekmesinin ekran görüntüsü":::

> [!TIP]
> Çalışmanızı tam ekranda göstermek için, tamamlama sekmelerinizi ayırın ve **en üst düzeye çıkarma düğmesini** kullanarak tamamlama penceresini en üst düzeye çıkarın. **Fark yapılandırması dişli**' ye tıklayarak en sevdiğiniz fark yapılandırmasını da seçebilirsiniz.
>:::image type="content" source="media/vs-2022/git-repository-commit-details-full-screen.png" alt-text="Fark yapılandırmalarına sahip tam ekran tamamlama ayrıntılarının ekran görüntüsü":::

## <a name="compare-commits"></a>İşlemeleri Karşılaştır

Dalınızdaki iki yürütme arasında karşılaştırmak için, karşılaştırmak istediğiniz iki işlemeyi seçmek üzere klavyenizdeki **CTRL tuşunu** kullanın. Ardından, bunlardan birine sağ tıklayıp **Işlemeleri Karşılaştır** seçeneğini tercih edin.

:::image type="content" source="media/vs-2022/git-repository-compare-commits-option.png" alt-text="İki işleme arasında nasıl karşılaştırılacağı ekran görüntüsü":::

:::image type="content" source="media/vs-2022/git-repository-compare-commits-ui.png" alt-text="İşleme işlemlerini karşılaştırma Kullanıcı arabiriminin ekran görüntüsü":::

> [!TIP]
>Kayıt ayrıntılarına benzer şekilde, farklı bir sekmede Compare COMMIT ARABIRIMINI açmak veya farklı bir ekranda en üst düzeye çıkarmak için **Yeni sekme aç** düğmesini kullanabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

yolculuğa devam etmek için [Visual Studio Git depolarını yönet](git-manage-repository.md) sayfasını ziyaret edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio git deneyimi](../ide/git-with-visual-studio.md)