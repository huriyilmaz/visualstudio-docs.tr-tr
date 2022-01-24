---
title: Visual Studio bir depoya git
titleSuffix: ''
description: git deposu penceresini kullanarak Visual Studio git deposuna gözatamazsınız.
ms.date: 01/21/2022
ms.topic: how-to
author: Taysser-Gherfal
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 92b5f346a35a57707763eeed1edaed13dfb31fef
ms.sourcegitcommit: 7d319435c35075d4cec021b7b667666a81c02435
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "137650413"
---
# <a name="browse-git-repositories-in-visual-studio"></a>Visual Studio git depolarına gözatmaya

**Git değişiklikleri** penceresi, kodunuzun dışında geçiş yapmak zorunda kalmadan, kodlarken git ile etkileşimde bulunmak için sorunsuz bir yol sağlar. Ancak git deponuza odaklanmak için daha mantıklı bir zaman vardır. Örneğin, takımınızın üzerinde ne kadar çalıştığı hakkında iyi bir resim almanız veya bir hatayı araştırmak için iki işlemeyi karşılaştırmanız gerekebilir.

## <a name="browse-through-local-and-remote-branches"></a>Yerel ve uzak dallara göz at

Başlamak için, **Görünüm** menüsünde **Git deposu** ' nu seçerek **Git deposu** penceresini açın. Git **deposu** penceresine **Git değişiklikleri** penceresinde ve durum çubuğunda **giden/gelen** bağlantıları seçerek de erişebilirsiniz.

:::image type="content" source="media/vs-2022/git-repository-browse-ui.png" alt-text="Git deposu penceresinin anatomi gösteren ekran görüntüsü." lightbox="media/vs-2022/git-repository-browse-ui.png":::

**Git deposu** penceresi, önceki ekran görüntüsünde numaralandırıldığı gibi üç ana bölüm içerir:

1. **Dallar**: git, kullanıcıları birden çok görev ve kendi kod dallarına göre denemeye karşı güçler. Aynı anda birden çok özellik üzerinde çalışıyorsanız veya çalışma kodunuzu etkilemeden fikirleri araştırmak istiyorsanız, dallandırma yararlı olabilir.
1. **Graph**: bu bölüm, dalınızın durumunu görselleştirir. Üç alt bölümleri vardır:

   - **Gelen** , takımınızın katkıda bulunduğu gelen işlemeleri gösterir.
   - **Giden** , henüz gönderdiğiniz yerel İşlemelerinizi gösterir.
   - **Yerel geçmiş** , yerel havuzunuz tarafından izlenen işlemelerin geri kalanını gösterir.
1. **kaydet**: **Graph** bölümünde herhangi bir yürütmeyi seçme, ayrıntılarını açar. Bir işlemenin tanıtılmasıyla ilgili değişiklikleri, bir farkı gösteren, seçerek kontrol edebilirsiniz. Örneğin, önceki ekran görüntüsünde, bir kaydetmenin *Files. csproj* dosyasına tanıtılan değişiklikler gösterilir.

Dalınızı değiştirmek zorunda kalmadan herhangi bir yerel veya uzak dala de gidebilirsiniz. Odaklanmak istediğiniz bir kayıt bulduğunuzda, yürütmeyi farklı bir sekmede açmak için **Yeni sekme aç** düğmesini seçin.

:::image type="content" source="media/vs-2022/git-repository-open-new-tab.png" alt-text="Yeni bir sekmede bir kaydetmenin nasıl açılacağı ekran görüntüsü." lightbox="media/vs-2022/git-repository-open-new-tab.png":::

:::image type="content" source="media/vs-2022/git-repository-details-tab.png" alt-text="Kayıt ayrıntıları sekmesinin ekran görüntüsü." lightbox="media/vs-2022/git-repository-details-tab.png":::

> [!TIP]
> İşlememeyi tam ekranda göstermek için, **tamamlama** sekmelerinizi ayırın ve **en üst düzeye çıkarma** düğmesini kullanarak **tamamlama** penceresini en üst düzeye çıkarın. Ayrıca, **fark yapılandırması** ' nı (dişli simgesi) seçerek en sevdiğiniz fark yapılandırmasını seçebilirsiniz.
>
>:::image type="content" source="media/vs-2022/git-repository-commit-details-full-screen.png" alt-text="Fark yapılandırmalarına sahip tam ekran kayıt ayrıntılarının ekran görüntüsü." lightbox="media/vs-2022/git-repository-commit-details-full-screen.png":::

## <a name="compare-commits"></a>İşlemeleri Karşılaştır

Dalınızdaki herhangi iki işlemeyi karşılaştırmak için, karşılaştırmak istediğiniz iki işlemeyi seçmek üzere **CTRL** tuşunu kullanın. Ardından, bunlardan birine sağ tıklayın ve **Işlemeleri Karşılaştır**' ı seçin.

:::image type="content" source="media/vs-2022/git-repository-compare-commits-option.png" alt-text="İki işlemesinin nasıl karşılaştırılacağı ekran görüntüsü." lightbox="media/vs-2022/git-repository-compare-commits-option.png":::

:::image type="content" source="media/vs-2022/git-repository-compare-commits-ui.png" alt-text="Karşılaştırılan işlemelerin ekran görüntüsü." lightbox="media/vs-2022/git-repository-compare-commits-ui.png":::

> [!TIP]
>**Kayıt ayrıntılarına** benzer şekilde, karşılaştırmayı farklı bir sekmede açmak veya ekranda en üst düzeye çıkarmak Için **Yeni sekme aç** düğmesini kullanabilirsiniz.

## <a name="create-a-branch-from-a-commit"></a>İşlemeden dal oluşturma

Visual Studio, önceki işlemelerden dallar oluşturmak için **git deposu** penceresinde **git Graph** bölmesini kullanabilirsiniz. Bunu yapmak için, yeni bir dal oluşturmak istediğiniz yürütmeye sağ tıklayın ve sonra **[yeni dal](git-create-branch.md)**' ı seçin.

:::image type="content" source="media/vs-2022/git-create-branch-from-commit.png" alt-text="git deposu penceresinin git Graph bölmesinin ekran görüntüsü.":::

> [!NOTE]
> Bu eylem için eşdeğer komut `git branch <branchname> [<commit-id>]` .

> [!TIP]
> 2022 Visual Studio [önizleme](/visualstudio/releases/2022/release-notes-preview) sürümünün işlemelerin kullanıma alınmasını nasıl kolaylaştırdığını öğrenmek için, [yeni Git özelliklerinin Visual Studio 2022](https://devblogs.microsoft.com/visualstudio/introducing-new-git-features-to-visual-studio-2022/#checkout-commits) web günlüğü gönderisine yönelik "kullanıma alma" bölümüne bakın.

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğa devam etmek için [Visual Studio Git depolarını yönetme](git-manage-repository.md)bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio git deneyimi](git-with-visual-studio.md)
- [Visual Studio ve GitHub: birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)
