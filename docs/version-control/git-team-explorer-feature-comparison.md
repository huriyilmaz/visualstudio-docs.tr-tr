---
title: Visual Studio 'da git ve Takım Gezgini yan yana karşılaştırması
titleSuffix: ''
description: Kaynak denetimini yönetmek için Visual Studio 'daki Takım Gezgini ve yeni git deneyiminin nasıl kullanılacağını karşılaştırın.
ms.date: 04/01/2021
ms.topic: how-to
ms.author: tglee
author: TerryGLee
ms.manager: jmartens
ms.openlocfilehash: 6ae09069e021ee9ff5699641bbe8662bf84ad327
ms.sourcegitcommit: 5fb684ff8729eb118aa91ce9f049c79eeb9747b1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2021
ms.locfileid: "107917948"
---
# <a name="side-by-side-comparison-of-git-and-team-explorer"></a>Git ve Takım Gezgini yan yana karşılaştırması

Visual Studio 2019 [sürüm 16,8](/visualstudio/releases/2019/release-notes/)' de yeni bir git deneyiminin ilk sürümü başlatıldık. Bu yeni deneyim, yaygın git görevlerinin bulunduğu basit bir **Git değişiklikleri** penceresiyle bağlam geçişinin azaltılmasına yardımcı olur. Ayrıca, dal yönetimi ve depo taraması gibi daha gelişmiş git işlemlerine yönelik ekran genelindeki bir **Git deposu** penceresi de bulunur.

Takım Gezgini kullanıyorsanız, yeni git deneyimini nasıl kullanabileceğinizi açıklayan adım adım bir kılavuz aşağıda verilmiştir.

> [!NOTE]
> Aşağıdaki bölüm, bir tablonun sütunlarına sığacak şekilde boyutlandırılmış ekran görüntüleri içerir. Daha büyük bir sürümünü görüntülemek için her bir ekran görüntüsüne tıklayın. (Dokunmatik bir cihaz kullanıyorsanız, daha büyük bir sürümünü görüntülemek için her bir ekran görüntüsüne dokunun.)

## <a name="get-started"></a>başlarken

|         |Ekip Gezgini  |Yeni git deneyimi |
|---------|---------|---------|
|**Depoyu kopyalama** | :::image type="content" source="media/clone-repo-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de Takım Gezgini için bağlanma penceresinin ekran görüntüsü, ' bir depoyu Kopyala ' yordamı yer imiyle." lightbox="media/clone-repo-team-explorer-lrg.png":::  </p>1. **Bağlan** sayfasını açın. <br> 2. **Bağlantıları Yönet**' i genişletin. <br> 3. **Projeye Bağlan**' ı seçin. | :::image type="content" source="media/clone-repo-new-git-sml.png" alt-text="Visual Studio 2019 ' deki git menüsünün ekran görüntüsü, ' bir depoyu Kopyala ' yordam yer işaretiyle birlikte." lightbox="media/clone-repo-new-git-lrg.png":::  </p> 1. **Git** menüsünü açın. <br>2. **Kopya depoyu** seçin. <br><br> |
|**Depoları 'lar arasında geçiş yap**  | :::image type="content" source="media/switch-repos-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de Takım Gezgini için bağlanma penceresinin ekran görüntüsü, bir ' Repos arasında geçiş yapma ' yordamı kaplaması ile." lightbox="media/switch-repos-team-explorer-lrg.png":::  </p>1. **Bağlan** sayfasını açın. <br>2. **yerel depolar** listesinden bir depo seçin. | :::image type="content" source="media/switch-repos-new-git-sml.png" alt-text="Visual Studio 2019 ' de yerel depolar menü öğesinin, ' bir depoyu Kopyala ' yordamı kaplaması ile ekran görüntüsü." lightbox="media/switch-repos-new-git-lrg.png"::: </p> 1. **Git** menüsünü açın. <br>2. **yerel depolar** listesinden bir depo seçin.  |
|**Bir çözüm açın**  |  :::image type="content" source="media/open-solution-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de Takım Gezgini için ana pencerenin ekran görüntüsü, bir ' çözüm aç ' yordam yer işaretiyle birlikte." lightbox="media/open-solution-team-explorer-lrg.png":::</p>1. **Takım Gezgini** **giriş** sayfasını açın. <br>2. çözüm listesinden bir çözüm seçin.  |  :::image type="content" source="media/open-solution-new-git-sml.png" alt-text="Visual Studio 2019 ' deki Çözüm Gezgini ekran görüntüsü, bir ' çözüm aç ' yordam yer işaretiyle birlikte." lightbox="media/open-solution-new-git-lrg.png":::</p>1. **Çözüm Gezgini**' de **görünümleri Değiştir** sayfasını açın. <br>2. çözüm listesinden bir çözüm seçin.  |
|**Kaynak denetimine bir çözüm ekleyin ve yeni bir depo oluşturun**  | :::image type="content" source="media/source-control-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de Takım Gezgini seçeneklerinin ekran görüntüsü collajı, kaynak denetimine Ekle-depo oluşturma yordam yer paylaşımına sahiptir." lightbox="media/source-control-team-explorer-lrg.png":::</p>1. **kaynak denetimine Ekle** durum çubuğu menüsünden **Git** ' i seçin. <br>2. **Yayımla**' yı seçin.  | :::image type="content" source="media/source-control-new-git-sml.png" alt-text="Visual Studio 2019 ' de git seçeneklerinin ekran görüntüsü birlikte bulunan ve ' kaynak denetimine Ekle-depo oluşturma ' yordamının kaplaması ile." lightbox="media/source-control-new-git-lrg.png":::</p>1. **kaynak denetimine Ekle** durum çubuğu menüsünden **Git** ' i seçin veya   >  üst düzey Visual Studio menü çubuğundan git **Oluştur** ' u seçin. <br>2. **Oluştur ve Gönder '** i seçin. </p> **Note**: kodunuzu Azure DevOps 'a eklemek istiyorsanız mevcut uzak seçeneğini kullanın. Bu durumda, önce bir Azure DevOps deposu oluşturmanız gerekir. |
> [!TIP]
> [Yeni git deneyimi](git-with-visual-studio.md) , açtığınız depoya veya çözüme göre doğru Azure DevOps deposuna otomatik olarak bağlanmalıdır. Ancak, depoya el ile bağlanmanız gerekiyorsa Takım Gezgini kullanarak bunu yapabilirsiniz. Visual Studio menü çubuğunda **görüntüle**  >  **Takım Gezgini**  >  **Bağlantıları Yönet**  >  **bağlantısını seçin**.

## <a name="git-changes"></a>Git değişiklikleri

|         |Ekip Gezgini  |Yeni git deneyimi |
|---------|---------|---------|
|**Yürüt ve aşama** | :::image type="content" source="media/commit-stage-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de Takım Gezgini için değişiklikler penceresinin ekran görüntüsü, ' COMMIT ve Stage ' yordam yer işaretiyle birlikte." lightbox="media/commit-stage-team-explorer-lrg.png":::  </p>1. bir kayıt iletisi girin. <br>2. **Tümünü Kaydet**' i seçin. <br>3. belirli dosyaları hazırlamak için, sağ tıklayın ve ardından **aşama**' ı seçin.  | :::image type="content" source="media/commit-stage-new-git-sml.png" alt-text="Visual Studio 2019 ' de git değişiklikleri penceresinin ekran görüntüsü, ' COMMIT ve Stage ' yordam yer işaretiyle birlikte." lightbox="media/commit-stage-new-git-lrg.png"::: </p>1. bir kayıt iletisi girin. <br>2. **Tümünü Kaydet**' i seçin. <br>3. belirli dosyaları hazırlamak için üzerine gelin ve " **+** " simgesine tıklayın. |
|**Bir işlemeyi Düzeltme** |  :::image type="content" source="media/amend-commit-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de Takım Gezgini için değişiklikler penceresinin ekran görüntüsü, ' düzeltme a COMMIT ' yordam yer imiyle." lightbox="media/amend-commit-team-explorer-lrg.png":::</p>1. **Eylemler** açılan düğmesine tıklayın. <br>2. **önceki Işlemeyi düzeltme** seçeneğini belirleyin. | :::image type="content" source="media/amend-commit-new-git-sml.png" alt-text="Visual Studio 2019 ' deki git değişiklikleri penceresinin ekran görüntüsü, bir ' düzeltme ' a COMMIT ' yordam kaplamasıyla birlikte." lightbox="media/amend-commit-new-git-lrg.png"::: </p>1. **Düzeltme** onay kutusuna tıklayın. <br>2. güncelleştirmelerinizi yürütmek için **Tümünü Yürüt** ' e tıklayın.  |
|**Bir değişikliği hazırlama** | :::image type="content" source="media/stash-change-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de Takım Gezgini için değişiklikler penceresinin ekran görüntüsü" lightbox="media/stash-change-team-explorer-lrg.png":::</p>1. **Stash** açılır düğmesine tıklayın. <br>2. ilgili **hazırlama** seçeneğini belirleyin. | :::image type="content" source="media/stash-change-new-git-sml.png" alt-text="Visual Studio 2019 ' deki git değişiklikleri penceresinin ekran görüntüsü, bir ' Stash a Change ' yordam kaplamasıyla birlikte." lightbox="media/stash-change-new-git-lrg.png":::</p>1. **Tümünü Kaydet** açılan düğmesine tıklayın. <br>2. ilgili **hazırlama** seçeneğini belirleyin. |

## <a name="synchronization"></a>Eşitleme

|         |Ekip Gezgini  |Yeni git deneyimi |
|---------|---------|---------|
|**Getirme, çekme ve gönderme değişiklikleri** | :::image type="content" source="media/fetch-pull-push-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de bir ' Fetch, pull ve push ' yordam kaplaması ile Takım Gezgini eşitleme penceresinin ekran görüntüsü." lightbox="media/fetch-pull-push-team-explorer-lrg.png":::</p>1. **eşitleme** sayfasına gidin. <br>2. tercih ettiğiniz ağ işlemine tıklayın. | :::image type="content" source="media/fetch-pull-push-new-git-sml.png" alt-text="Visual Studio 2019 ' de git değişiklikleri penceresinin ekran görüntüsü, bir ' Fetch, pull ve push ' yordam kaplamasıyla birlikte." lightbox="media/fetch-pull-push-team-new-git-lrg.png"::: </p>1. **Git değişiklikleri** penceresinde Fetch, pull ve push düğmelerini bulun. <br>2. tercih ettiğiniz ağ işlemine tıklayın.|
|**Gelen ve giden işlemeleri görüntüleme** | :::image type="content" source="media/view-commits-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de Takım Gezgini için eşitleme penceresinin ekran görüntüsü, bir ' gelen ve giden işlemeler görüntüle ' yordamı yer imiyle." lightbox="media/view-commits-team-explorer-lrg.png"::: </p>1. **eşitleme** sayfasına gidin. <br>2. gelen ve giden listelerinizi görüntüleyin. | :::image type="content" source="media/view-commits-new-git-sml.png" alt-text="Git değişiklikleri penceresinin ve Visual Studio 2019 ' deki git deposu penceresinin ekran görüntüsü, ' gelen ve giden yürütmelerin görünümü ' yordam kaplamasıyla birlikte." lightbox="media/view-commits-new-git-lrg.png":::</p>1. **Git değişiklikleri** penceresinde **giden/gelen** bağlantısına tıklayın. <br>2. **Git deposu** penceresinin en üstündeki grafik tablosunda bulunan simgeleri kullanarak gelen ve giden İşlemelerinizi görüntüleyin. |

## <a name="branches"></a>Dallar

|         |Ekip Gezgini  |Yeni git deneyimi |
|---------|---------|---------|
|**Dal oluşturma** |  :::image type="content" source="media/create-branch-team-explorer-sml.png" alt-text="Visual Studio 2019 ' deki Takım Gezgini için dallar penceresinin ekran görüntüsü, ' yeni dal oluştur ' yordamı ile birlikte." lightbox="media/create-branch-team-explorer-lrg.png":::</p>1. **dallar** penceresine gidin. <br> 2. **yeni dal** öğesine tıklayın. | :::image type="content" source="media/create-branch-new-git-sml.png" alt-text="Visual Studio 2019 ' deki git değişiklikleri penceresinin ekran görüntüsü, ' yeni dal oluştur ' yordamı ile birlikte." lightbox="media/create-branch-new-git-lrg.png"::: </p>1. **Git değişiklikleri** penceresinde, dal açılan listesine tıklayın. <br>2. **yeni dal** öğesine tıklayın. |
|**Uzak daldan en son değişiklikleri al** | :::image type="content" source="media/sync-remote-team-explorer-sml.png" alt-text="Visual Studio 2019 ' deki Takım Gezgini için dallar penceresinin ekran görüntüsü, &quot;uzak daldan son değişiklikler al&quot; yordam yer işaretiyle birlikte." lightbox="media/sync-remote-team-explorer-lrg.png"::: </p>1. **dallar sayfasına** gidin. <br>2. uzak dala sağ tıklayın ve ' **den Birleştir** veya yeniden **temellendir**' ı seçin.  | :::image type="content" source="media/sync-remote-new-git-sml.png" alt-text="Visual Studio 2019 ' deki git değişiklikleri penceresinin ekran görüntüsü, ' uzak daldan son değişiklikler Al ' yordam kaplamasıyla birlikte." lightbox="media/sync-remote-new-git-lrg.png":::</p>1. dal açılan listesine tıklayın. <br>2 **. uzak dala** tıklayın ve **güncel dalı Birleştir** ' i seçin veya **güncel dalı yeniden temellendirin**.  |
|**Dalları Yönet** | :::image type="content" source="media/manage-branches-team-explorer-sml.png" alt-text="Visual Studio 2019 ' deki Takım Gezgini için dallar penceresinin ekran görüntüsü, ' dalları Yönet ' yordam yer imiyle." lightbox="media/manage-branches-team-explorer-lrg.png"::: </p>1. **dallar** penceresine gidin. <br>2. yönetmek istediğiniz dala sağ tıklayın. <br>3. yürütmelerin yönetilmesi için dalların **geçmişini** görüntüleyin. | :::image type="content" source="media/manage-branches-new-git-sml.png" alt-text="Visual Studio 2019 ' de dalları yönetmek için kaç tane Kullanıcı arabirimi seçeneğinin kullanılacağını gösteren ekran görüntüsü collajı." lightbox="media/manage-branches-new-git-lrg.png"::: </p>1. aşağıdaki giriş noktalarından birini kullanarak git deposu penceresine gidin: <br><br>a. Üst düzey Visual Studio menüsünden **Git**  >  **Manage Branches**' ı seçin.<br> b.   >  **Gelen/giden** git değişikliklerini seçin. <br>c. Sağ alt köşedeki durum çubuğu menüsünden **dalları Yönet**' i seçin.<br> <br> 2. üst düzey **Git**  >  **Yönet dallar** menüsünde aşağıdaki eylemlerden birini yapın: <br><br>A. Dallara sağ tıklayın.<br>B. Yönetmek istediğiniz işlemeleri çoklu seçin. |

## <a name="conflict-resolution"></a>Çakışma çözümü

|         |Ekip Gezgini  |Yeni git deneyimi |
|---------|---------|---------|
|**Çakışmalar içeren dosya listesine erişme** | :::image type="content" source="media/resolve-conflicts-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de bir yordam birlikte Takım Gezgini için değişiklikler penceresinin ve çakışmaları çöz penceresinin ekran görüntüsü collajı." lightbox="media/resolve-conflicts-team-explorer-lrg.png":::</p>1. **Çakışmalar** bağlantısına tıklayarak **Çakışmaları Çöz** penceresine gidin. <br> 2. birleştirme çakışmalarını çözmek için **Çakışmalar** listesini kullanın. | :::image type="content" source="media/resolve-conflicts-new-git-sml.png" alt-text="Visual Studio 2019 ' deki git değişiklikleri penceresinin ekran görüntüsü, ' Çakışmaları Çözümle ' yordam kaplaması ile." lightbox="media/resolve-conflicts-new-git-lrg.png"::: </p>1. **birleştirme işleminin çakışmalar ile devam** ettiğini doğrulayın. <br>2. birleştirme çakışması olan dosyaların listesi **Git değişiklikleri** penceresinin **Birleştirilmemiş değişiklikler** bölümünde görünür. <br>Çakışmaları çözün. |

## <a name="next-steps"></a>Sonraki adımlar

Yeni git deneyimi hakkında daha fazla bilgi edinmek için bkz. [Visual Studio 'Da git ile çalışmaya](https://www.youtube.com/watch?v=GCZ9x3yqkyc)başlama, YouTube 'da en son video.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da yeni git deneyimi](git-with-visual-studio.md)
- [Visual Studio 'da git ve GitHub ile çalışmaya başlama](/learn/modules/visual-studio-github-push/)
- [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)