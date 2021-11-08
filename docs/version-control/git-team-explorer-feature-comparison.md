---
title: Git ve Takım Gezgini Visual Studio 2019 ' de yan yana karşılaştırması
titleSuffix: ''
description: kaynak denetimini yönetmek için Visual Studio Takım Gezgini yeni Git deneyiminin nasıl kullanılacağını karşılaştırın ve karşılaştırın.
ms.date: 11/08/2021
ms.topic: how-to
ms.author: tglee
author: TerryGLee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 8275c57a3165a39653974a3368ddb07fab46148e
ms.sourcegitcommit: 67dc39e93c86ba50eb5ca877b0471fb8ab8475ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2021
ms.locfileid: "132001592"
---
# <a name="side-by-side-comparison-of-git-and-team-explorer"></a>Git ve Takım Gezgini yan yana karşılaştırması

yeni bir Git deneyiminin ilk sürümünü Visual Studio 2019 [sürüm 16,8](/visualstudio/releases/2019/release-notes/)' de başlattık. Bu yeni deneyim, yaygın git görevlerinin bulunduğu basit bir **Git değişiklikleri** penceresiyle bağlam geçişinin azaltılmasına yardımcı olur. Ayrıca, dal yönetimi ve depo taraması gibi daha gelişmiş git işlemlerine yönelik ekran genelindeki bir **Git deposu** penceresi de bulunur.

Takım Gezgini kullanıyorsanız, yeni git deneyimini nasıl kullanabileceğinizi açıklayan adım adım bir kılavuz aşağıda verilmiştir.

> [!NOTE]
> Aşağıdaki bölüm, bir tablonun sütunlarına sığacak şekilde boyutlandırılmış ekran görüntüleri içerir. Daha büyük bir sürümünü görüntülemek için her bir ekran görüntüsüne tıklayın. (Dokunmatik bir cihaz kullanıyorsanız, daha büyük bir sürümünü görüntülemek için her bir ekran görüntüsüne dokunun.)

## <a name="get-started"></a>başlarken

|         |Ekip Gezgini  |Yeni git deneyimi |
|---------|---------|---------|
|**Depoyu kopyalama** | :::image type="content" source="media/clone-repo-team-explorer-sml.png" alt-text="' bir depoyu kopyala ' yordamı ile Visual Studio 2019 ' de Takım Gezgini için Bağlan penceresinin ekran görüntüsü." lightbox="media/clone-repo-team-explorer-lrg.png":::  </p>1. **Bağlan** sayfasını açın. <br> 2. **Bağlantıları Yönet**' i genişletin. <br> 3. **Project için Bağlan** seçin. | :::image type="content" source="media/clone-repo-new-git-sml.png" alt-text="Visual Studio 2019 ' deki Git menüsünün ekran görüntüsü, ' bir depoyu kopyala ' yordam yer işaretiyle birlikte." lightbox="media/clone-repo-new-git-lrg.png":::  </p> 1. **Git** menüsünü açın. <br>2. **Kopya depoyu** seçin. <br><br> |
|**Depoları 'lar arasında geçiş yap**  | :::image type="content" source="media/switch-repos-team-explorer-sml.png" alt-text="Visual Studio 2019 ' deki Takım Gezgini için Bağlan pencerenin ekran görüntüsü, bir ' repos arasında geçiş yapma ' yordamı kaplaması ile." lightbox="media/switch-repos-team-explorer-lrg.png":::  </p>1. **Bağlan** sayfasını açın. <br>2. **yerel depolar** listesinden bir depo seçin. | :::image type="content" source="media/switch-repos-new-git-sml.png" alt-text="Visual Studio 2019 ' deki yerel depolar menü öğesinin ekran görüntüsü, ' bir depoyu kopyala ' yordam yer işaretiyle birlikte." lightbox="media/switch-repos-new-git-lrg.png"::: </p> 1. **Git** menüsünü açın. <br>2. **yerel depolar** listesinden bir depo seçin.  |
|**Bir çözüm açın**  |  :::image type="content" source="media/open-solution-team-explorer-sml.png" alt-text="Visual Studio 2019 'deki Takım Gezgini için ana pencerenin ekran görüntüsü, bir ' çözüm aç ' yordam yer işaretiyle birlikte." lightbox="media/open-solution-team-explorer-lrg.png":::</p>1. **Takım Gezgini** **giriş** sayfasını açın. <br>2. çözüm listesinden bir çözüm seçin.  |  :::image type="content" source="media/open-solution-new-git-sml.png" alt-text="Visual Studio 2019 'deki Çözüm Gezgini ekran görüntüsü, bir ' çözüm aç ' yordam yer işaretiyle birlikte." lightbox="media/open-solution-new-git-lrg.png":::</p>1. **Çözüm Gezgini**' de **görünümleri Değiştir** sayfasını açın. <br>2. çözüm listesinden bir çözüm seçin.  |
|**Kaynak denetimine bir çözüm ekleyin ve yeni bir depo oluşturun**  | :::image type="content" source="media/source-control-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de Takım Gezgini seçeneklerinin ekran görüntüsü collajı, kaynak denetimine ekle-depo oluşturma yordam yer paylaşımına sahiptir." lightbox="media/source-control-team-explorer-lrg.png":::</p>1. **kaynak denetimine Ekle** durum çubuğu menüsünden **Git** ' i seçin. <br>2. **Yayımla**' yı seçin.  | :::image type="content" source="media/source-control-new-git-sml.png" alt-text="Visual Studio 2019 ' de Git seçeneklerinin ekran görüntüsü birlikte bulunan ve ' kaynak denetimine ekle-depo oluşturma ' yordamının yer kaplaması ile." lightbox="media/source-control-new-git-lrg.png":::</p>1. **kaynak denetimine ekle** durum çubuğu menüsünden **git** ' i seçin veya   >  üst düzey Visual Studio menü çubuğundan git **oluştur** ' u seçin. <br>2. **Oluştur ve Gönder '** i seçin. </p> **Note**: kodunuzu Azure DevOps eklemek istiyorsanız mevcut uzak seçeneğini kullanın. bu durumda, önce bir Azure DevOps deposu oluşturmanız gerekir. |
> [!TIP]
> [yeni Git deneyimi](git-with-visual-studio.md) , açtığınız depoya veya çözüme göre doğru Azure DevOps depoya otomatik olarak bağlanmalıdır. Ancak, depoya el ile bağlanmanız gerekiyorsa Takım Gezgini kullanarak bunu yapabilirsiniz. Visual Studio menü çubuğundan, bağlantıları **görüntüle**  >  **Takım Gezgini**  >  **yönet**  >  **Bağlan**' i seçin.

## <a name="git-changes"></a>Git değişiklikleri

|         |Ekip Gezgini  |Yeni git deneyimi |
|---------|---------|---------|
|**Yürüt ve aşama** | :::image type="content" source="media/commit-stage-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de Takım Gezgini için değişiklikler penceresinin ekran görüntüsü, ' commıt ve stage ' yordam yer işaretiyle birlikte." lightbox="media/commit-stage-team-explorer-lrg.png":::  </p>1. bir kayıt iletisi girin. <br>2. **Tümünü Kaydet**' i seçin. <br>3. belirli dosyaları hazırlamak için, sağ tıklayın ve ardından **aşama**' ı seçin.  | :::image type="content" source="media/commit-stage-new-git-sml.png" alt-text="Visual Studio 2019 ' deki Git değişiklikleri penceresinin ekran görüntüsü, ' commıt ve stage ' yordam yer işaretiyle birlikte." lightbox="media/commit-stage-new-git-lrg.png"::: </p>1. bir kayıt iletisi girin. <br>2. **Tümünü Kaydet**' i seçin. <br>3. belirli dosyaları hazırlamak için üzerine gelin ve " **+** " simgesine tıklayın. |
|**Bir işlemeyi Düzeltme** |  :::image type="content" source="media/amend-commit-team-explorer-sml.png" alt-text="Visual Studio 2019 ' deki Takım Gezgini için değişiklikler penceresinin ekran görüntüsü, ' düzeltme d a commıt ' yordam yer işaretiyle birlikte." lightbox="media/amend-commit-team-explorer-lrg.png":::</p>1. **Eylemler** açılan düğmesine tıklayın. <br>2. **önceki Işlemeyi düzeltme** seçeneğini belirleyin. | :::image type="content" source="media/amend-commit-new-git-sml.png" alt-text="Visual Studio 2019 ' deki Git değişiklikleri penceresinin ekran görüntüsü, ' düzeltme d a commıt ' yordam kaplamasıyla birlikte." lightbox="media/amend-commit-new-git-lrg.png"::: </p>1. **Düzeltme** onay kutusuna tıklayın. <br>2. güncelleştirmelerinizi yürütmek için **Tümünü Yürüt** ' e tıklayın.  |
|**Bir değişikliği hazırlama** | :::image type="content" source="media/stash-change-team-explorer-sml.png" alt-text="Visual Studio 2019 ' deki Takım Gezgini için değişiklikler penceresinin ekran görüntüsü, bir ' stash a change ' yordamı yer imiyle." lightbox="media/stash-change-team-explorer-lrg.png":::</p>1. **Stash** açılır düğmesine tıklayın. <br>2. ilgili **hazırlama** seçeneğini belirleyin. | :::image type="content" source="media/stash-change-new-git-sml.png" alt-text="Visual Studio 2019 ' deki Git değişiklikleri penceresinin ekran görüntüsü, bir ' stash a change ' yordam kaplamasıyla birlikte." lightbox="media/stash-change-new-git-lrg.png":::</p>1. **Tümünü Kaydet** açılan düğmesine tıklayın. <br>2. ilgili **hazırlama** seçeneğini belirleyin. |

## <a name="synchronization"></a>Eşitleme

|         |Ekip Gezgini  |Yeni git deneyimi |
|---------|---------|---------|
|**Getirme, çekme ve gönderme değişiklikleri** | :::image type="content" source="media/fetch-pull-push-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de bir ' fetch, pull ve push ' yordam yer işaretiyle Takım Gezgini için eşitleme penceresinin ekran görüntüsü." lightbox="media/fetch-pull-push-team-explorer-lrg.png":::</p>1. **eşitleme** sayfasına gidin. <br>2. tercih ettiğiniz ağ işlemine tıklayın. | :::image type="content" source="media/fetch-pull-push-new-git-sml.png" alt-text="Visual Studio 2019 ' deki Git değişiklikleri penceresinin ekran görüntüsü, bir ' fetch, pull ve push ' yordam kaplamasıyla birlikte." lightbox="media/fetch-pull-push-team-new-git-lrg.png"::: </p>1. **Git değişiklikleri** penceresinde Fetch, pull ve push düğmelerini bulun. <br>2. tercih ettiğiniz ağ işlemine tıklayın.|
|**Gelen ve giden işlemeleri görüntüleme** | :::image type="content" source="media/view-commits-team-explorer-sml.png" alt-text="Visual Studio 2019 ' deki Takım Gezgini için eşitleme penceresinin ekran görüntüsü, ' gelen ve giden işlemeler görüntüle ' yordam yer imiyle." lightbox="media/view-commits-team-explorer-lrg.png"::: </p>1. **eşitleme** sayfasına gidin. <br>2. gelen ve giden listelerinizi görüntüleyin. | :::image type="content" source="media/view-commits-new-git-sml.png" alt-text="Visual Studio 2019 ' deki git değişiklikleri penceresinin ve git deposu penceresinin ekran görüntüsü, ' gelen ve giden yürütmelerin görünümü ' yordam kaplamasıyla birlikte." lightbox="media/view-commits-new-git-lrg.png":::</p>1. **Git değişiklikleri** penceresinde **giden/gelen** bağlantısına tıklayın. <br>2. **Git deposu** penceresinin en üstündeki grafik tablosunda bulunan simgeleri kullanarak gelen ve giden İşlemelerinizi görüntüleyin. |

## <a name="branches"></a>Dallar

|         |Ekip Gezgini  |Yeni git deneyimi |
|---------|---------|---------|
|**Dal oluşturma** |  :::image type="content" source="media/create-branch-team-explorer-sml.png" alt-text="Visual Studio 2019 ' deki Takım Gezgini için dallar penceresinin ekran görüntüsü, ' yeni dal oluştur ' yordamı ile birlikte." lightbox="media/create-branch-team-explorer-lrg.png":::</p>1. **dallar** penceresine gidin. <br> 2. **yeni dal** öğesine tıklayın. | :::image type="content" source="media/create-branch-new-git-sml.png" alt-text="Visual Studio 2019 ' deki Git değişiklikleri penceresinin ekran görüntüsü, ' yeni dal oluşturma ' yordamı ile birlikte." lightbox="media/create-branch-new-git-lrg.png"::: </p>1. **Git değişiklikleri** penceresinde, dal açılan listesine tıklayın. <br>2. **yeni dal** öğesine tıklayın. |
|**Uzak daldan en son değişiklikleri al** | :::image type="content" source="media/sync-remote-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'uzak daldan son değişiklikleri al' yordam katmanını kullanarak Takım Gezgini için Dallar penceresinin ekran görüntüsü." lightbox="media/sync-remote-team-explorer-lrg.png"::: </p>1. Dallar **sayfasına gidin.** <br>2. Uzak dala sağ tıklayın ve Birleştir veya Üzerine Yeniden **Temeli** **Ekle'yi seçin.**  | :::image type="content" source="media/sync-remote-new-git-sml.png" alt-text="Visual Studio 2019'da 'uzak daldan son değişiklikleri al' yordam katmanını kullanarak Git Değişiklikleri penceresinin ekran görüntüsü." lightbox="media/sync-remote-new-git-lrg.png":::</p>1. Dal açılan listesine tıklayın. <br>2. UzakLar **sekmesinin altında** uzak dala tıklayın ve Güncel Dalı'de **Birleştir'i veya** üzerine Güncel Dalı **seçin.**  |
|**Dalları yönetme** | :::image type="content" source="media/manage-branches-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'dalları yönet' yordamı katmanla birlikte, Takım Gezgini için Dallar penceresinin ekran görüntüsü." lightbox="media/manage-branches-team-explorer-lrg.png"::: </p>1. Dallar **penceresine** gidin. <br>2. Yönetmek istediğiniz dallara sağ tıklayın. <br>3. **Commit'leri** yönetmek için dalların geçmişini görüntüleme. | :::image type="content" source="media/manage-branches-new-git-sml.png" alt-text="2019'da dalları yönetmek için üç kullanıcı arabirimi Visual Studio ekran görüntüsü." lightbox="media/manage-branches-new-git-lrg.png"::: </p>1. Aşağıdaki giriş noktalarından birini kullanarak Git deposu penceresine gidin: <br><br>a. Üst düzey çalışma Visual Studio **Git** Dalları  >  **Yönet'i seçin.**<br> b. **Git**  >  **gelen/giden değişiklikleri'yi seçin.** <br>c. Sağ alttaki durum çubuğu menüsünden Dalları **Yönet'i seçin.**<br> <br> 2. Üst düzey **Git**  >  **Dalları Yönet** menüsünde aşağıdaki eylemlerden birini yapın: <br><br>A. Dallara sağ tıklayın.<br>B. Yönetmek istediğiniz işlemeleri çoklu seçin. |

## <a name="conflict-resolution"></a>Çakışma çözümü

|         |Ekip Gezgini  |Yeni Git deneyimi |
|---------|---------|---------|
|**Çakışmaları olan dosyaların listesine erişme** | :::image type="content" source="media/resolve-conflicts-team-explorer-sml.png" alt-text="Visual Studio 2019'daki Takım Gezgini için Değişiklikler penceresinin ve Çakışmaları Çözümle penceresinin ekran görüntüsü." lightbox="media/resolve-conflicts-team-explorer-lrg.png":::</p>1. Çakışmalar **bağlantısına** tıklayarak Çakışmaları Çözümle **penceresine** gidin. <br> 2. Birleştirme **çakışmalarınızı** çözmek için Çakışmalar listesini kullanın. | :::image type="content" source="media/resolve-conflicts-new-git-sml.png" alt-text="Visual Studio 2019'daki Git Değişiklikleri penceresinin ekran görüntüsü ve 'çakışmaları çözümleme' yordamı katmanlandı." lightbox="media/resolve-conflicts-new-git-lrg.png"::: </p>1. Çakışmalarla **birleştirme devam ediyor'ın görüntülendiğinden emin** olur. <br>2. Birleştirme çakışmaları olan dosyaların listesi Git Değişiklikleri **penceresinin** Birleştirlanmamış Değişiklikler **bölümünde** görünür. <br>Çakışmaları çözümleme. |

## <a name="next-steps"></a>Sonraki adımlar

Yeni Git deneyimi hakkında daha fazla bilgi için YouTube'daki [Visual Studio 2019'da Git](https://www.youtube.com/watch?v=GCZ9x3yqkyc)ile çalışmaya başlama adlı en son videoya bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 2019'daki yeni Git deneyimi](git-with-visual-studio.md?view=vs-2019&preserve-view=true)
- [Başlarken Git ve GitHub ile Visual Studio](/learn/modules/visual-studio-github-push/)
- [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)