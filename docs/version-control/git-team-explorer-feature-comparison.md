---
title: Git ve Takım Gezgini karşılaştırması Visual Studio
titleSuffix: ''
description: Kaynak denetimi yönetmek için yeni Git deneyiminin nasıl Takım Gezgini Visual Studio karşılaştırma.
ms.date: 04/01/2021
ms.topic: how-to
ms.author: tglee
author: TerryGLee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 7f2f8b8bca781e53ab49d34e32a2c0d5ea846ae1
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729339"
---
# <a name="side-by-side-comparison-of-git-and-team-explorer"></a>Git ve Takım Gezgini'nin yan yana karşılaştırması

Visual Studio 2019 sürüm [16.8'de](/visualstudio/releases/2019/release-notes/)yeni bir Git deneyiminin ilk sürümünü başlattık. Bu yeni deneyim, yaygın Git görevlerini içeren basit bir **Git Değişiklikleri penceresiyle** bağlam değiştirmenin azaltılmasına yardımcı olur. Ayrıca dal yönetimi ve depoya **göz atma** gibi daha gelişmiş Git işlemleri için ekran genelinde git deposu penceresi de içerir.

Daha önce Takım Gezgini, yeni Git deneyimini nasıl kullanabileceğiniz hakkında bilgi edinen adım adım bir kılavuza göz atabilirsiniz.

> [!NOTE]
> Aşağıdaki bölümde, bir tablonun sütunlarına sığacak şekilde boyutlandırilen ekran görüntüleri yer alır. Daha büyük bir sürümünü görüntülemek için her ekran görüntüsüne tıklayın. (Dokunmatik ekranlı bir cihaz kullanıyorsanız ekran görüntülerine dokunarak daha büyük bir sürümünü görüntüebilirsiniz.)

## <a name="get-started"></a>başlarken

|         |Ekip Gezgini  |Yeni Git deneyimi |
|---------|---------|---------|
|**Bir repo kopyalama** | :::image type="content" source="media/clone-repo-team-explorer-sml.png" alt-text="Takım Gezgini 2019'da 'bir Visual Studio klonla' yordam katmanlı Bağlantı penceresinin ekran görüntüsü." lightbox="media/clone-repo-team-explorer-lrg.png":::  </p>1. Bağlan **sayfasını** açın. <br> 2. Bağlantıları **Yönet'i genişletin.** <br> 3. Projeye **Bağlan'ı seçin.** | :::image type="content" source="media/clone-repo-new-git-sml.png" alt-text="Visual Studio 2019'da 'depo klonla' yordam katmanlanmış Git menüsünün ekran görüntüsü." lightbox="media/clone-repo-new-git-lrg.png":::  </p> 1. **Git menüsünü** açın. <br>2. **Depoyu Kopyala'yi seçin.** <br><br> |
|**Repos arasında geçiş**  | :::image type="content" source="media/switch-repos-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de Takım Gezgini için bağlanma penceresinin ekran görüntüsü, bir ' Repos arasında geçiş yapma ' yordamı kaplaması ile." lightbox="media/switch-repos-team-explorer-lrg.png":::  </p>1. **Bağlan** sayfasını açın. <br>2. **yerel depolar** listesinden bir depo seçin. | :::image type="content" source="media/switch-repos-new-git-sml.png" alt-text="Visual Studio 2019 ' de yerel depolar menü öğesinin, ' bir depoyu Kopyala ' yordamı kaplaması ile ekran görüntüsü." lightbox="media/switch-repos-new-git-lrg.png"::: </p> 1. **Git** menüsünü açın. <br>2. **yerel depolar** listesinden bir depo seçin.  |
|**Bir çözüm açın**  |  :::image type="content" source="media/open-solution-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de Takım Gezgini için ana pencerenin ekran görüntüsü, bir ' çözüm aç ' yordam yer işaretiyle birlikte." lightbox="media/open-solution-team-explorer-lrg.png":::</p>1. **Takım Gezgini** **giriş** sayfasını açın. <br>2. çözüm listesinden bir çözüm seçin.  |  :::image type="content" source="media/open-solution-new-git-sml.png" alt-text="Visual Studio 2019 ' deki Çözüm Gezgini ekran görüntüsü, bir ' çözüm aç ' yordam yer işaretiyle birlikte." lightbox="media/open-solution-new-git-lrg.png":::</p>1. **Çözüm Gezgini**' de **görünümleri Değiştir** sayfasını açın. <br>2. çözüm listesinden bir çözüm seçin.  |
|**Kaynak denetimine bir çözüm ekleyin ve yeni bir depo oluşturun**  | :::image type="content" source="media/source-control-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de Takım Gezgini seçeneklerinin ekran görüntüsü collajı, kaynak denetimine Ekle-depo oluşturma yordam yer paylaşımına sahiptir." lightbox="media/source-control-team-explorer-lrg.png":::</p>1. **kaynak denetimine Ekle** durum çubuğu menüsünden **Git** ' i seçin. <br>2. **Yayımla**' yı seçin.  | :::image type="content" source="media/source-control-new-git-sml.png" alt-text="Visual Studio 2019 ' de git seçeneklerinin ekran görüntüsü birlikte bulunan ve ' kaynak denetimine Ekle-depo oluşturma ' yordamının kaplaması ile." lightbox="media/source-control-new-git-lrg.png":::</p>1. **kaynak denetimine Ekle** durum çubuğu menüsünden **Git** ' i seçin veya   >  üst düzey Visual Studio menü çubuğundan git **Oluştur** ' u seçin. <br>2. **Oluştur ve Gönder '** i seçin. </p> **Not:** Kodunuzu depolamaya eklemek için mevcut uzak seçeneği Azure DevOps. Bu durumda, önce bir Azure DevOps oluşturmanız gerekir. |
> [!TIP]
> Yeni [Git deneyimi,](git-with-visual-studio.md) açtığınız depoya veya Azure DevOps doğru depoya otomatik olarak bağlanacaktır. Bununla birlikte, bir repoya el ile bağlanmanız gerekirse, bunu yine de Takım Gezgini. Bağlantı Visual Studio çubuğundan Bağlantıları Yönet **Bağlantısı'Takım Gezgini'ı**  >    >    >  **seçin.**

## <a name="git-changes"></a>Git değişiklikleri

|         |Ekip Gezgini  |Yeni Git deneyimi |
|---------|---------|---------|
|**Yürütme ve aşama** | :::image type="content" source="media/commit-stage-team-explorer-sml.png" alt-text="'Commit and stage' yordam Takım Gezgini 2019'da Visual Studio için Değişiklikler penceresinin ekran görüntüsü." lightbox="media/commit-stage-team-explorer-lrg.png":::  </p>1. Bir işleme iletisi girin. <br>2. Hepsini **İşle'yi seçin.** <br>3. Belirli dosyaları aşamaya eklemek için, dosyalara sağ tıklayın ve ardından Aşama'yı **seçin.**  | :::image type="content" source="media/commit-stage-new-git-sml.png" alt-text="Visual Studio 2019'daki Git Değişiklikleri penceresinin ekran görüntüsü, 'işleme ve aşama' yordam katmanla." lightbox="media/commit-stage-new-git-lrg.png"::: </p>1. Bir işleme iletisi girin. <br>2. Hepsini **İşle'yi seçin.** <br>3. Belirli dosyaları aşamak için üzerine gelin ve " **+** " simgesine tıklayın. |
|**Bir işlemeyi değiştirme** |  :::image type="content" source="media/amend-commit-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'işlemeyi düzelt' yordamı katmanla birlikte Takım Gezgini için Değişiklikler penceresinin ekran görüntüsü." lightbox="media/amend-commit-team-explorer-lrg.png":::</p>1. Eylemler **açılan** listesinden tıklayın. <br>2. Önceki **Yürütmeyi Düzelt'i seçin.** | :::image type="content" source="media/amend-commit-new-git-sml.png" alt-text="Visual Studio 2019 ' deki git değişiklikleri penceresinin ekran görüntüsü, bir ' düzeltme ' a COMMIT ' yordam kaplamasıyla birlikte." lightbox="media/amend-commit-new-git-lrg.png"::: </p>1. **Düzeltme** onay kutusuna tıklayın. <br>2. güncelleştirmelerinizi yürütmek için **Tümünü Yürüt** ' e tıklayın.  |
|**Bir değişikliği hazırlama** | :::image type="content" source="media/stash-change-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de Takım Gezgini için değişiklikler penceresinin ekran görüntüsü" lightbox="media/stash-change-team-explorer-lrg.png":::</p>1. **Stash** açılır düğmesine tıklayın. <br>2. ilgili **hazırlama** seçeneğini belirleyin. | :::image type="content" source="media/stash-change-new-git-sml.png" alt-text="Visual Studio 2019 ' deki git değişiklikleri penceresinin ekran görüntüsü, bir ' Stash a Change ' yordam kaplamasıyla birlikte." lightbox="media/stash-change-new-git-lrg.png":::</p>1. **Tümünü Kaydet** açılan düğmesine tıklayın. <br>2. ilgili **hazırlama** seçeneğini belirleyin. |

## <a name="synchronization"></a>Eşitleme

|         |Ekip Gezgini  |Yeni git deneyimi |
|---------|---------|---------|
|**Getirme, çekme ve gönderme değişiklikleri** | :::image type="content" source="media/fetch-pull-push-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de bir ' Fetch, pull ve push ' yordam kaplaması ile Takım Gezgini eşitleme penceresinin ekran görüntüsü." lightbox="media/fetch-pull-push-team-explorer-lrg.png":::</p>1. **eşitleme** sayfasına gidin. <br>2. tercih ettiğiniz ağ işlemine tıklayın. | :::image type="content" source="media/fetch-pull-push-new-git-sml.png" alt-text="Visual Studio 2019 ' de git değişiklikleri penceresinin ekran görüntüsü, bir ' Fetch, pull ve push ' yordam kaplamasıyla birlikte." lightbox="media/fetch-pull-push-team-new-git-lrg.png"::: </p>1. **Git değişiklikleri** penceresinde Fetch, pull ve push düğmelerini bulun. <br>2. tercih ettiğiniz ağ işlemine tıklayın.|
|**Gelen ve giden işlemeleri görüntüleme** | :::image type="content" source="media/view-commits-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de Takım Gezgini için eşitleme penceresinin ekran görüntüsü, bir ' gelen ve giden işlemeler görüntüle ' yordamı yer imiyle." lightbox="media/view-commits-team-explorer-lrg.png"::: </p>1. Eşitleme **sayfasına** gidin. <br>2. Gelen ve giden listelerinizi görüntüleme. | :::image type="content" source="media/view-commits-new-git-sml.png" alt-text="Visual Studio 2019'daki Git Değişiklikleri penceresinin ve Git Deposu penceresinin ekran görüntüsü. 'Gelen ve giden işlemeleri görüntüleme' yordamı katman." lightbox="media/view-commits-new-git-lrg.png":::</p>1. Git **Değişiklikleri penceresinde giden/gelen** **bağlantıya** tıklayın. <br>2. Git Deposu penceresinin üst kısmında yer alan grafik tablosunda bulunan simgeleri kullanarak gelen ve giden **commit'lerinizi** görüntüleyin. |

## <a name="branches"></a>Dallar

|         |Ekip Gezgini  |Yeni Git deneyimi |
|---------|---------|---------|
|**Dal oluşturma** |  :::image type="content" source="media/create-branch-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'yeni dal oluştur' yordam katmanlarını kullanarak Takım Gezgini için Dallar penceresinin ekran görüntüsü." lightbox="media/create-branch-team-explorer-lrg.png":::</p>1. Dallar **penceresine** gidin. <br> 2. Yeni **Dal'a tıklayın.** | :::image type="content" source="media/create-branch-new-git-sml.png" alt-text="Visual Studio 2019'daki Git Değişiklikleri penceresinin ekran görüntüsü ve 'yeni bir dal oluştur' yordamı katmanla." lightbox="media/create-branch-new-git-lrg.png"::: </p>1. **Git Değişiklikleri penceresinde** dal açılan listesine tıklayın. <br>2. Yeni **Dal'a tıklayın.** |
|**Uzak daldan en son değişiklikleri al** | :::image type="content" source="media/sync-remote-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'uzak daldan son değişiklikleri al' yordam katmanını kullanarak Takım Gezgini için Dallar penceresinin ekran görüntüsü." lightbox="media/sync-remote-team-explorer-lrg.png"::: </p>1. Dallar **sayfasına gidin.** <br>2. Uzak dala sağ tıklayın ve Birleştir veya Üzerine **Yeniden Temeli** **Ekle'yi seçin.**  | :::image type="content" source="media/sync-remote-new-git-sml.png" alt-text="Visual Studio 2019'daki Git Değişiklikleri penceresinin ekran görüntüsü. 'Uzak daldan son değişiklikleri al' yordamı katman." lightbox="media/sync-remote-new-git-lrg.png":::</p>1. Dal açılan listesine tıklayın. <br>2. Uzaklar **sekmesinin altında** uzak dala tıklayın ve Güncel Dalı'de **Birleştir'i veya** **Güncel Dalı'yi seçin.**  |
|**Dalları yönetme** | :::image type="content" source="media/manage-branches-team-explorer-sml.png" alt-text="Visual Studio 2019 ' deki Takım Gezgini için dallar penceresinin ekran görüntüsü, ' dalları Yönet ' yordam yer imiyle." lightbox="media/manage-branches-team-explorer-lrg.png"::: </p>1. **dallar** penceresine gidin. <br>2. yönetmek istediğiniz dala sağ tıklayın. <br>3. yürütmelerin yönetilmesi için dalların **geçmişini** görüntüleyin. | :::image type="content" source="media/manage-branches-new-git-sml.png" alt-text="Visual Studio 2019 ' de dalları yönetmek için kaç tane Kullanıcı arabirimi seçeneğinin kullanılacağını gösteren ekran görüntüsü collajı." lightbox="media/manage-branches-new-git-lrg.png"::: </p>1. aşağıdaki giriş noktalarından birini kullanarak git deposu penceresine gidin: <br><br>a. Üst düzey Visual Studio menüsünden **Git**  >  **Manage Branches**' ı seçin.<br> b.   >  **Gelen/giden** git değişikliklerini seçin. <br>c. Sağ alt köşedeki durum çubuğu menüsünden **dalları Yönet**' i seçin.<br> <br> 2. üst düzey **Git**  >  **Yönet dallar** menüsünde aşağıdaki eylemlerden birini yapın: <br><br>A. Dallara sağ tıklayın.<br>B. Yönetmek istediğiniz işlemeleri çoklu seçin. |

## <a name="conflict-resolution"></a>Çakışma çözümü

|         |Ekip Gezgini  |Yeni git deneyimi |
|---------|---------|---------|
|**Çakışmalar içeren dosya listesine erişme** | :::image type="content" source="media/resolve-conflicts-team-explorer-sml.png" alt-text="Visual Studio 2019 ' de bir yordam birlikte Takım Gezgini için değişiklikler penceresinin ve çakışmaları çöz penceresinin ekran görüntüsü collajı." lightbox="media/resolve-conflicts-team-explorer-lrg.png":::</p>1. **Çakışmalar** bağlantısına tıklayarak **Çakışmaları Çöz** penceresine gidin. <br> 2. birleştirme çakışmalarını çözmek için **Çakışmalar** listesini kullanın. | :::image type="content" source="media/resolve-conflicts-new-git-sml.png" alt-text="Visual Studio 2019 ' deki git değişiklikleri penceresinin ekran görüntüsü, ' Çakışmaları Çözümle ' yordam kaplaması ile." lightbox="media/resolve-conflicts-new-git-lrg.png"::: </p>1. **birleştirme işleminin çakışmalar ile devam** ettiğini doğrulayın. <br>2. birleştirme çakışması olan dosyaların listesi **Git değişiklikleri** penceresinin **Birleştirilmemiş değişiklikler** bölümünde görünür. <br>Çakışmaları çözümleme. |

## <a name="next-steps"></a>Sonraki adımlar

Yeni Git deneyimi hakkında daha fazla bilgi için YouTube'daki Visual Studio'de [Git ile çalışmaya](https://www.youtube.com/watch?v=GCZ9x3yqkyc)başlama adlı en son videoya bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki yeni Git deneyimi](git-with-visual-studio.md)
- [Başla Git ve GitHub ile Visual Studio](/learn/modules/visual-studio-github-push/)
- [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)