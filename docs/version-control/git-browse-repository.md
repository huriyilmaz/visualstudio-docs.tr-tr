---
title: Visual Studio'de bir Visual Studio
titleSuffix: ''
description: Git Deposu penceresini kullanarak Visual Studio herhangi bir Git deposuna göz atma.
ms.date: 11/10/2021
ms.topic: how-to
author: Taysser-Gherfal
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 729667f27e9cbe95e9fe6990916ce7c11bd1f22d
ms.sourcegitcommit: dc12d3d0ca2ec3601cb9de7c22e61ecf22c7c514
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2021
ms.locfileid: "132264015"
---
# <a name="browse-git-repositories-in-visual-studio"></a>Visual Studio'da Git depolarına göz atma

Git Değişiklikleri penceresi, kodunuzdan geçiş yapmak zorunda kalmadan kod yazma sırasında Git ile etkileşim kurmanın sorunsuz bir yolunu sağlar; ancak bazen Git depona odaklanmanın daha anlamlı olduğu zamanlar olur. Örneğin, takımınız üzerinde çalıştığı şeyi iyi bir şekilde incelemeniz veya bir hatayı araştırmak için iki işlemeyi karşılaştırmanız gerekir.

## <a name="browse-local-and-remote-branches"></a>Yerel ve uzak dallara göz atma

Çalışmaya başlama için Görünüm menüsünde Git Deposu'na **tıklayarak Git Deposu** penceresini açın. Git değişiklikleri penceresindeki **giden/gelen** bağlantılara ve durum çubuğuna tıklayarak Git Deposu penceresine de erişebilirsiniz.

:::image type="content" source="media/vs-2022/git-repository-browse-ui.png" alt-text="Git Deposu penceresinin anatomisini gösteren ekran görüntüsü." lightbox="media/vs-2022/git-repository-browse-ui.png":::

Git deposu penceresi, önceki ekran görüntüsünde numara olarak yer alan üç ana bölüm içerir:

1. **Dallar:** Git, kullanıcılara birden çok görev için destek sağlar ve dallar aracılığıyla kodlarıyla denemeler sağlar. Aynı anda birden çok özellik üzerinde çalışıyorsanız veya çalışma kodunuzu etkileyemeden fikirleri keşfetmek için çalışıyorsanız, dallama çok yararlı olabilir.
1. **Git Graph:** Git grafiği bölümü dalnizin durumunu görselleştirin. Üç farklı bölümden oluşur: gelen, giden ve yerel geçmiş. Gelen bölümde, takımınız tarafından katkıda bulunan gelen işlemeler, giden bölümde hala gönderip uygulamamış olmadığınız yerel işlemeler ve yerel geçmiş yerel depo tarafından izleniyor olan diğer işlemeler de yer almaktadır.
1. **Commit Details:** Git Graph bölümünde herhangi bir işlemeye tıklanmışsa, işlemelerin ayrıntılarını gösteren işleme ayrıntıları kullanıcı arabirimi açılır. Fark gösterecek olan işlemelere tıklayarak değişiklikleri kontrol edin. Örneğin, önceki ekran görüntüsünde, bir işlemenin Files.csproj dosyasına tanıtan değişikliklerini görüntüleyemizi görebilirsiniz.

Dalını değiştirmek zorunda kalmadan herhangi bir yerel veya uzak dala göz atabilirsiniz ve odaklanmak  istediğiniz bir işlemeyi bulurken, işlemeyi farklı bir sekmede açmak veya burada gösterildiği gibi farklı bir ekranda ekranı kaplamak için Yeni Sekmede Aç düğmesine tıklamanız gerekir.

:::image type="content" source="media/vs-2022/git-repository-open-new-tab.png" alt-text="Yeni sekmede açma ekran görüntüsü." lightbox="media/vs-2022/git-repository-open-new-tab.png":::

:::image type="content" source="media/vs-2022/git-repository-details-tab.png" alt-text="Commit details (işleme ayrıntıları) sekmesinin ekran görüntüsü." lightbox="media/vs-2022/git-repository-details-tab.png":::

> [!TIP]
> Commit'inizi tam ekranda görüntülemek için işleme sekmenizi ayırın ve ekranı kapla düğmesini kullanarak işleme penceresini ekranı **kaplayın.** Ayrıca, Fark Yapılandırma Dişlisi'ne tıklayarak sık kullanılan **fark yapılandırmanızı da seçin.**
>:::image type="content" source="media/vs-2022/git-repository-commit-details-full-screen.png" alt-text="Fark yapılandırmaları içeren tam ekran Commit Details ekran görüntüsü." lightbox="media/vs-2022/git-repository-commit-details-full-screen.png":::

## <a name="compare-commits"></a>Commit'leri karşılaştırma

Dalınıza yapılan iki işlemeyi karşılaştırmak için klavyenizde **Ctrl** tuşunu kullanarak karşılaştırmak istediğiniz iki işlemeyi seçin. Ardından bunlardan bir tanesine sağ tıklayın ve **Commit'leri Karşılaştır seçeneğini** belirleyin.

:::image type="content" source="media/vs-2022/git-repository-compare-commits-option.png" alt-text="İki işleme arasında karşılaştırmanın ekran görüntüsü." lightbox="media/vs-2022/git-repository-compare-commits-option.png":::

:::image type="content" source="media/vs-2022/git-repository-compare-commits-ui.png" alt-text="Yürütmeleri karşılaştır kullanıcı arabiriminin ekran görüntüsü." lightbox="media/vs-2022/git-repository-compare-commits-ui.png":::

> [!TIP]
>Commit Details'e benzer şekilde, Commit Kullanıcı Arabirimini Farklı bir sekmede karşılaştırmak veya farklı bir ekranda ekranı kapla'ya çıkarmak için Yeni Sekmede Aç düğmesini kullanabilirsiniz. 

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğunuza devam etmek için Git [Depolarını Yönetme sayfasında Visual Studio](git-manage-repository.md) ziyaret edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Git deneyimi](../ide/git-with-visual-studio.md)
- [Visual Studio & GitHub: Birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)