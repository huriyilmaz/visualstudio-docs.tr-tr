---
title: Visual Studio 2019'da Git ve Takım Gezgini yan yana karşılaştırması
titleSuffix: ''
description: Kaynak denetimi yönetmek için yeni Git deneyiminin nasıl Takım Gezgini Visual Studio karşılaştırma.
ms.date: 11/08/2021
ms.topic: how-to
author: Taysser-Gherfal
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
monikerRange: <=vs-2019
ms.openlocfilehash: 0869ea999132694d06871aa2b7c39cea37463d19
ms.sourcegitcommit: dc12d3d0ca2ec3601cb9de7c22e61ecf22c7c514
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2021
ms.locfileid: "132264174"
---
# <a name="side-by-side-comparison-of-git-and-team-explorer"></a>Git ve Takım Gezgini'nin yan yana karşılaştırması

Visual Studio 2019 sürüm [16.8'de](/visualstudio/releases/2019/release-notes/)yeni bir Git deneyiminin ilk sürümünü başlattık. Bu yeni deneyim, yaygın Git görevlerini içeren basit bir **Git Değişiklikleri penceresiyle** bağlam değiştirmenin azaltılmasına yardımcı olur. Ayrıca dal yönetimi ve depoya **göz atma** gibi daha gelişmiş Git işlemleri için ekran genelinde git deposu penceresi de içerir.

Daha önce Takım Gezgini, yeni Git deneyimini nasıl kullanabileceğiniz hakkında bilgi edinen adım adım bir kılavuza göz atabilirsiniz.

> [!NOTE]
> Aşağıdaki bölümde, bir tablonun sütunlarına sığacak şekilde boyutlandırilen ekran görüntüleri yer alır. Daha büyük bir sürümünü görüntülemek için her ekran görüntüsüne tıklayın. (Dokunmatik ekranlı bir cihaz kullanıyorsanız ekran görüntülerine dokunarak daha büyük bir sürümünü görüntüebilirsiniz.)

## <a name="get-started"></a>başlarken

|         |Ekip Gezgini  |Yeni Git deneyimi |
|---------|---------|---------|
|**Bir repo kopyalama** | :::image type="content" source="media/clone-repo-team-explorer-sml.png" alt-text="Bağlan 2019'Takım Gezgini 'bir Visual Studio klonla' yordamı katmanlanmış şekilde ekran görüntüsü." lightbox="media/clone-repo-team-explorer-lrg.png":::  </p>1. **Bağlan** açın. <br> 2. Bağlantıları **Yönet'i genişletin.** <br> 3. Öğesini **Bağlan seçeneğini Project.** | :::image type="content" source="media/clone-repo-new-git-sml.png" alt-text="Visual Studio 2019'da 'depo klonla' yordam katmanlanmış Git menüsünün ekran görüntüsü." lightbox="media/clone-repo-new-git-lrg.png":::  </p> 1. **Git menüsünü** açın. <br>2. **Depoyu Kopyala'yi seçin.** <br><br> |
|**Repos arasında geçiş**  | :::image type="content" source="media/switch-repos-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'Bağlan değiştirme' yordamı katmanla Takım Gezgini için ekran görüntüsü." lightbox="media/switch-repos-team-explorer-lrg.png":::  </p>1. **Bağlan** açın. <br>2. Yerel Depolar **listesinden bir depo** seçin. | :::image type="content" source="media/switch-repos-new-git-sml.png" alt-text="Visual Studio 2019'daki Yerel Depolar menü öğesinin ekran görüntüsü ve 'depoyu klonla' yordamı katmanlanmış." lightbox="media/switch-repos-new-git-lrg.png"::: </p> 1. **Git menüsünü** açın. <br>2. Yerel Depolar **listesinden bir depo** seçin.  |
|**Çözüm açma**  |  :::image type="content" source="media/open-solution-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'çözüm aç' yordamı katmanla birlikte, Takım Gezgini için Giriş penceresinin ekran görüntüsü." lightbox="media/open-solution-team-explorer-lrg.png":::</p>1. Giriş **sayfasını** **Takım Gezgini.** <br>2. Çözüm listesinden bir çözüm seçin.  |  :::image type="content" source="media/open-solution-new-git-sml.png" alt-text="'Çözüm Çözüm Gezgini' yordam Visual Studio 2019'daki örnek olaylarının ekran görüntüsü." lightbox="media/open-solution-new-git-lrg.png":::</p>1. Görünüm **değiştir sayfasını** Çözüm Gezgini.  <br>2. Çözüm listesinden bir çözüm seçin.  |
|**Kaynak denetimine çözüm ekleme ve yeni depo oluşturma**  | :::image type="content" source="media/source-control-team-explorer-sml.png" alt-text="Visual Studio 2019'daki Takım Gezgini seçeneklerinin ekran görüntüsü, Kaynak Denetimine Ekle - Repo oluştur yordam katmanla." lightbox="media/source-control-team-explorer-lrg.png":::</p>1. Kaynak Denetimine **Ekle durum çubuğu menüsünden** **Git'i** seçin. <br>2. **Yayımla'yı seçin.**  | :::image type="content" source="media/source-control-new-git-sml.png" alt-text="Visual Studio 2019'da 'kaynak denetimine ekle - depo oluştur' yordam katmanla Git seçeneklerinin ekran görüntüsü." lightbox="media/source-control-new-git-lrg.png":::</p>1. Kaynak **Denetimine** Ekle durum çubuğu menüsünden **Git'i** seçin veya üst düzey menü çubuğundan   >  **Git** Git Deposu Visual Studio seçin. <br>2. Oluştur ve **It'i seçin.** </p> **Not:** Kodunuzu depolamaya eklemek için mevcut uzak seçeneği Azure DevOps. Bu durumda, önce bir Azure DevOps oluşturmanız gerekir. |
> [!TIP]
> Yeni [Git deneyimi,](git-with-visual-studio.md) açtığınız depoya veya Azure DevOps doğru depoya otomatik olarak bağlanacaktır. Bununla birlikte, bir repoya el ile bağlanmanız gerekirse, bunu yine de Takım Gezgini. Bağlantı Visual Studio çubuğundan, Bağlantıları Yönet **seçeneğini**  >    >  **Takım Gezgini'yi**  >  **Bağlan.**

## <a name="git-changes"></a>Git değişiklikleri

|         |Ekip Gezgini  |Yeni Git deneyimi |
|---------|---------|---------|
|**Yürütme ve aşama** | :::image type="content" source="media/commit-stage-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'işleme ve aşama' yordam katmanla Takım Gezgini için Değişiklikler penceresinin ekran görüntüsü." lightbox="media/commit-stage-team-explorer-lrg.png":::  </p>1. Bir işleme iletisi girin. <br>2. Hepsini **İşle'yi seçin.** <br>3. Belirli dosyaları aşamaya eklemek için, dosyalara sağ tıklayın ve ardından Aşama'yı **seçin.**  | :::image type="content" source="media/commit-stage-new-git-sml.png" alt-text="Visual Studio 2019'daki Git Değişiklikleri penceresinin ekran görüntüsü, 'işleme ve aşama' yordam katmanla." lightbox="media/commit-stage-new-git-lrg.png"::: </p>1. Bir işleme iletisi girin. <br>2. Hepsini **İşle'yi seçin.** <br>3. Belirli dosyaları aşamak için üzerine gelin ve " **+** " simgesine tıklayın. |
|**Bir işlemeyi değiştirme** |  :::image type="content" source="media/amend-commit-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'işlemeyi düzelt' yordamı katmanla birlikte Takım Gezgini için Değişiklikler penceresinin ekran görüntüsü." lightbox="media/amend-commit-team-explorer-lrg.png":::</p>1. Eylemler **açılan** listesinden tıklayın. <br>2. Önceki **Yürütmeyi Düzelt'i seçin.** | :::image type="content" source="media/amend-commit-new-git-sml.png" alt-text="Visual Studio 2019'daki Git Değişiklikleri penceresinin ekran görüntüsü, 'işlemeyi değiştirme' yordamı katmanla." lightbox="media/amend-commit-new-git-lrg.png"::: </p>1. Düzelt **onay** kutusuna tıklayın. <br>2. Güncelleştirmelerinizi **işlemek için Hepsini** Işle'ye tıklayın.  |
|**Değişikliği gizli olarak saklama** | :::image type="content" source="media/stash-change-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'değişiklik hazırla' yordamı katmanla birlikte Takım Gezgini için Değişiklikler penceresinin ekran görüntüsü." lightbox="media/stash-change-team-explorer-lrg.png":::</p>1. Zula **açılan** açılan'a tıklayın. <br>2. İlgili Stash **seçeneğini** belirleyin. | :::image type="content" source="media/stash-change-new-git-sml.png" alt-text="Visual Studio 2019'daki Git Değişiklikleri penceresinin ekran görüntüsü, 'değişiklik ekleme' yordamı katmanla." lightbox="media/stash-change-new-git-lrg.png":::</p>1. Tüm Commit **All (TümLeri Işle) açılan** açılan listesinden tıklayın. <br>2. İlgili Stash **seçeneğini** belirleyin. |

## <a name="synchronization"></a>Eşitleme

|         |Ekip Gezgini  |Yeni Git deneyimi |
|---------|---------|---------|
|**Değişiklikleri getirme, çekme ve itme** | :::image type="content" source="media/fetch-pull-push-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'getirme, çekme ve itme' yordamı katmanla birlikte, Takım Gezgini için Eşitleme penceresinin ekran görüntüsü." lightbox="media/fetch-pull-push-team-explorer-lrg.png":::</p>1. Eşitleme **sayfasına** gidin. <br>2. İstediğiniz ağ işlemine tıklayın. | :::image type="content" source="media/fetch-pull-push-new-git-sml.png" alt-text="Visual Studio 2019'daki Git Değişiklikleri penceresinin ekran görüntüsü, 'getirme, çekme ve itme' yordam katmanlarını gösterir." lightbox="media/fetch-pull-push-team-new-git-lrg.png"::: </p>1. Git Değişiklikleri penceresinde getirme, çekme ve itme **düğmelerini** bulun. <br>2. İstediğiniz ağ işlemine tıklayın.|
|**Gelen ve Giden işlemeleri görüntüleme** | :::image type="content" source="media/view-commits-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'gelen ve giden işlemeleri görüntüle' yordamı katmanla birlikte, Takım Gezgini için Eşitleme penceresinin ekran görüntüsü." lightbox="media/view-commits-team-explorer-lrg.png"::: </p>1. Eşitleme **sayfasına** gidin. <br>2. Gelen ve giden listelerinizi görüntüleme. | :::image type="content" source="media/view-commits-new-git-sml.png" alt-text="Visual Studio 2019'daki Git Değişiklikleri penceresinin ve Git Deposu penceresinin ekran görüntüsü, 'gelen ve giden işlemeleri görüntüle' yordam katmanlarını gösterir." lightbox="media/view-commits-new-git-lrg.png":::</p>1. Git **Değişiklikleri penceresinde giden/gelen** **bağlantıya** tıklayın. <br>2. Git Deposu penceresinin üst kısmında yer alan grafik tablosunda yer alan simgeleri kullanarak gelen ve giden **işlemelerinizi** görüntüleyin. |

## <a name="branches"></a>Dallar

|         |Ekip Gezgini  |Yeni Git deneyimi |
|---------|---------|---------|
|**Dal oluşturma** |  :::image type="content" source="media/create-branch-team-explorer-sml.png" alt-text="Takım Gezgini 2019'da 'yeni bir dal oluştur' yordam Visual Studio için Dallar penceresinin ekran görüntüsü." lightbox="media/create-branch-team-explorer-lrg.png":::</p>1. Dallar **penceresine** gidin. <br> 2. Yeni **Dal'a tıklayın.** | :::image type="content" source="media/create-branch-new-git-sml.png" alt-text="Visual Studio 2019'daki Git Değişiklikleri penceresinin ekran görüntüsü, 'yeni bir dal oluştur' yordam katmanla." lightbox="media/create-branch-new-git-lrg.png"::: </p>1. **Git Değişiklikleri penceresinde** dal açılan listesine tıklayın. <br>2. Yeni **Dal'a tıklayın.** |
|**Uzak daldan en son değişiklikleri al** | :::image type="content" source="media/sync-remote-team-explorer-sml.png" alt-text="Visual Studio 2019 ' deki Takım Gezgini için dallar penceresinin ekran görüntüsü, &quot;uzak daldan son değişiklikler al&quot; yordam kaplamasıyla birlikte." lightbox="media/sync-remote-team-explorer-lrg.png"::: </p>1. **dallar sayfasına** gidin. <br>2. uzak dala sağ tıklayın ve ' **den Birleştir** veya yeniden **temellendir**' ı seçin.  | :::image type="content" source="media/sync-remote-new-git-sml.png" alt-text="Visual Studio 2019 ' deki Git değişiklikleri penceresinin ekran görüntüsü, ' uzak daldan son değişiklikler al ' yordam yer işaretiyle birlikte." lightbox="media/sync-remote-new-git-lrg.png":::</p>1. dal açılan listesine tıklayın. <br>2 **. uzak dala** tıklayın ve **güncel dalı Birleştir** ' i seçin veya **güncel dalı yeniden temellendirin**.  |
|**Dalları Yönet** | :::image type="content" source="media/manage-branches-team-explorer-sml.png" alt-text="Visual Studio 2019 ' deki Takım Gezgini için dallar penceresinin ekran görüntüsü, ' dalları yönet ' yordam kaplaması ile." lightbox="media/manage-branches-team-explorer-lrg.png"::: </p>1. **dallar** penceresine gidin. <br>2. yönetmek istediğiniz dala sağ tıklayın. <br>3. yürütmelerin yönetilmesi için dalların **geçmişini** görüntüleyin. | :::image type="content" source="media/manage-branches-new-git-sml.png" alt-text="Visual Studio 2019 ' deki dalları yönetmek için kaç tane kullanıcı arabirimi seçeneğinin kullanılacağını gösteren ekran görüntüsü collajı." lightbox="media/manage-branches-new-git-lrg.png"::: </p>1. aşağıdaki giriş noktalarından birini kullanarak git deposu penceresine gidin: <br><br>a. üst düzey Visual Studio menüsünden **Git**  >  **Manage Branches**' ı seçin.<br> b.   >  **Gelen/giden** git değişikliklerini seçin. <br>c. Sağ alt köşedeki durum çubuğu menüsünden **dalları Yönet**' i seçin.<br> <br> 2. üst düzey **Git**  >  **Yönet dallar** menüsünde aşağıdaki eylemlerden birini yapın: <br><br>A. Dallara sağ tıklayın.<br>B. Yönetmek istediğiniz işlemeleri çoklu seçin. |

## <a name="conflict-resolution"></a>Çakışma çözümü

|         |Ekip Gezgini  |Yeni git deneyimi |
|---------|---------|---------|
|**Çakışmalar içeren dosya listesine erişme** | :::image type="content" source="media/resolve-conflicts-team-explorer-sml.png" alt-text="değişiklikler penceresinin ekran görüntüsü ve Visual Studio 2019 ' deki Takım Gezgini için bir yordam yer paylaşımı ile çakışmalar çözümle penceresi." lightbox="media/resolve-conflicts-team-explorer-lrg.png":::</p>1. **Çakışmalar** bağlantısına tıklayarak **Çakışmaları Çöz** penceresine gidin. <br> 2. birleştirme çakışmalarını çözmek için **Çakışmalar** listesini kullanın. | :::image type="content" source="media/resolve-conflicts-new-git-sml.png" alt-text="Visual Studio 2019 ' deki Git değişiklikleri penceresinin ekran görüntüsü, ' çakışmaları çözümle ' yordam kaplaması ile." lightbox="media/resolve-conflicts-new-git-lrg.png"::: </p>1. **birleştirme işleminin çakışmalar ile devam** ettiğini doğrulayın. <br>2. birleştirme çakışması olan dosyaların listesi **Git değişiklikleri** penceresinin **Birleştirilmemiş değişiklikler** bölümünde görünür. <br>Çakışmaları çözün. |

## <a name="next-steps"></a>Sonraki adımlar

yeni Git deneyimi hakkında daha fazla bilgi için, YouTube 'da [Visual Studio 2019 ' de Git ile çalışmaya](https://www.youtube.com/watch?v=GCZ9x3yqkyc)başlama son videosunu inceleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 2019 ' deki yeni Git deneyimi](git-with-visual-studio.md?view=vs-2019&preserve-view=true)
- [Visual Studio Git ve GitHub ile Başlarken](/learn/modules/visual-studio-github-push/)
- [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)