---
title: Visual Studio'de bir repoya göz atma
titleSuffix: ''
description: Git Deposu penceresini kullanarak Visual Studio herhangi bir Git deposuna göz atma.
ms.date: 11/10/2021
ms.topic: how-to
author: Taysser-Gherfal
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 8d9b72cb308b73b2c95e0903c6f3f953127c0568
ms.sourcegitcommit: d38d1b083322019663fec7d1d85a4cda456aadca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135534362"
---
# <a name="browse-git-repositories-in-visual-studio"></a>Git depolarına göz Visual Studio

Git **Değişiklikleri penceresi,** kodunuzdan geçiş yapmak zorunda kalmadan kod yazma sırasında Git ile etkileşim kurmanın sorunsuz bir yolunu sağlar. Ancak bazen Git depona odaklanmanın daha anlamlı olduğu zamanlar olur. Örneğin, takımınız üzerinde çalıştığı şeyi iyi bir şekilde incelemeniz veya bir hatayı araştırmak için iki işlemeyi karşılaştırmanız gerekir.

## <a name="browse-through-local-and-remote-branches"></a>Yerel ve uzak dallara göz atma

Çalışmaya başlama için Görünüm menüsünde **Git Deposu'yü** **seçerek Git Deposu** **penceresini** açın. Git Değişiklikleri penceresinde ve **durum** çubuğunda **giden/gelen** bağlantıları seçerek **Git Deposu** penceresine de erişebilirsiniz.

:::image type="content" source="media/vs-2022/git-repository-browse-ui.png" alt-text="Git Deposu penceresinin anatomisini gösteren ekran görüntüsü." lightbox="media/vs-2022/git-repository-browse-ui.png":::

**Git Deposu penceresi,** önceki ekran görüntüsünde numara olarak yer alan üç ana bölüm içerir:

1. **Dallar:** Git, kullanıcıları birden çok görev üzerinde çalışma ve dallar aracılığıyla kodlarıyla deneme gücü sağlar. Aynı anda birden çok özellik üzerinde çalışıyorsanız veya çalışma kodunuzu etkilemeden fikirleri araştırmak için çalışıyorsanız, dallama yararlı olabilir.
1. **Graph:** Bu bölüm dalnizin durumunu görselleştirin. Üç alt bölüm vardır: 

   - **Gelen,** takımınız tarafından katkıda bulunan gelen işlemeleri gösterir. 
   - **Giden,** hala gönderip göndere olmadığınız yerel commit'lerinizi gösterir.
   - **Yerel Geçmiş,** yerel deponun takip eden geri kalan işlemelerini gösterir.
1. **Commit:** Graph **bölümünde herhangi bir işlemeyi** seçmek, işlemenin ayrıntılarını açar. Bir işlemenin neden olduğu değişiklikleri, fark gösteren seçerek kontrol edin. Örneğin, önceki ekran görüntüsünde, bir işlemenin *Files.csproj dosyasına tanıtan değişiklikleri görebilirsiniz.*

Dalını değiştirmek zorunda kalmadan herhangi bir yerel veya uzak dala göz atabilir. Odaklanmak istediğiniz bir işlemeyi bulurken Yeni Sekmede Aç düğmesini **seçerek** işlemeyi farklı bir sekmede açın.

:::image type="content" source="media/vs-2022/git-repository-open-new-tab.png" alt-text="Yeni bir sekmede işleme açma ekran görüntüsü." lightbox="media/vs-2022/git-repository-open-new-tab.png":::

:::image type="content" source="media/vs-2022/git-repository-details-tab.png" alt-text="Yürütme ayrıntıları sekmesinin ekran görüntüsü." lightbox="media/vs-2022/git-repository-details-tab.png":::

> [!TIP]
> Commit'inizi tam ekranda görüntülemek için, Commit **sekmenizi ayırın** ve Ekranı Kapla düğmesini **kullanarak** Commit penceresini ekranı **kaplayın.** Ayrıca, Fark Yapılandırması'ı (dişli simgesi) seçerek sık kullanılan **fark yapılandırmanızı** da seçin.
>
>:::image type="content" source="media/vs-2022/git-repository-commit-details-full-screen.png" alt-text="Fark yapılandırmaları içeren tam ekran işleme ayrıntılarının ekran görüntüsü." lightbox="media/vs-2022/git-repository-commit-details-full-screen.png":::

## <a name="compare-commits"></a>Commit'leri karşılaştırma

Dalınıza iki işlemeyi karşılaştırmak için **Ctrl** tuşunu kullanarak karşılaştırmak istediğiniz iki işlemeyi seçin. Ardından bunlardan birini sağ tıklatın ve Commit'leri **Karşılaştır'ı seçin.**

:::image type="content" source="media/vs-2022/git-repository-compare-commits-option.png" alt-text="İki işlemeyi karşılaştırma ekran görüntüsü." lightbox="media/vs-2022/git-repository-compare-commits-option.png":::

:::image type="content" source="media/vs-2022/git-repository-compare-commits-ui.png" alt-text="Karşılaştıran işlemelerin ekran görüntüsü." lightbox="media/vs-2022/git-repository-compare-commits-ui.png":::

> [!TIP]
>Commit **Details'e** benzer şekilde, karşılaştırmayı farklı bir sekmede açmak veya ekranda ekranı kaplaya çıkarmak için Yeni Sekmede Aç düğmesini kullanabilirsiniz. 

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğunuza devam etmek için [bkz. Visual Studio.](git-manage-repository.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'de Git deneyimi](git-with-visual-studio.md)
- [Visual Studio ve GitHub: Birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)
