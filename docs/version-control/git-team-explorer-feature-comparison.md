---
title: Visual Studio 2019'da Git ve Takım Gezgini yan yana karşılaştırması
titleSuffix: ''
description: Kaynak denetimi yönetmek için Git deneyiminin nasıl Takım Gezgini Visual Studio karşılaştırma.
ms.date: 11/08/2021
ms.topic: how-to
author: Taysser-Gherfal
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
monikerRange: vs-2019
---
# <a name="compare-the-git-experience-to-team-explorer-in-visual-studio-2019"></a>Git deneyimini Visual Studio 2019'da Takım Gezgini karşılaştırma

Visual Studio 2019 sürüm [16.8'de Git deneyiminin ilk sürümünü başlattık](/visualstudio/releases/2019/release-notes/). Bu deneyim, yaygın Git görevlerini içeren basit bir **Git Değişiklikleri penceresiyle** bağlam değiştirmenin azaltılmasına yardımcı olur. Ayrıca dal yönetimi ve depoya **göz atma** gibi daha gelişmiş Git işlemleri için ekran genelinde git deposu penceresi de içerir.

Daha önce Takım Gezgini, Git deneyimini nasıl kullanabileceğiniz hakkında bilgi edinen adım adım bir kılavuza göz atabilirsiniz.

> [!NOTE]
> Aşağıdaki bölümde, bir tablonun sütunlarına sığacak şekilde boyutlandırilen ekran görüntüleri yer alır. Daha büyük bir sürümünü görüntülemek için her ekran görüntüsüne tıklayın. (Dokunmatik ekranlı bir cihaz kullanıyorsanız ekran görüntülerine dokunarak daha büyük bir sürümünü görüntüebilirsiniz.)

## <a name="get-started"></a>Başlarken

|         |Ekip Gezgini  |Git deneyimi |
|---------|---------|---------|
|**Bir repo kopyalama** | :::image type="content" source="media/clone-repo-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'bir Bağlan klonla' yordamı katmanlanmış şekilde Takım Gezgini için ekran görüntüsü." lightbox="media/clone-repo-team-explorer-lrg.png":::  </p>1 **. Bağlan açın**. <br> 2. Bağlantıları **Yönet'i genişletin**. <br> 3. **Seçerek Bağlan'Project**. | :::image type="content" source="media/clone-repo-new-git-sml.png" alt-text="Visual Studio 2019'da 'depo klonla' yordam katmanlanmış Git menüsünün ekran görüntüsü." lightbox="media/clone-repo-new-git-lrg.png":::  </p> 1. **Git menüsünü** açın. <br>2. **Depoyu Kopyala'yi seçin**. <br><br> |
|**Repos arasında geçiş**  | :::image type="content" source="media/switch-repos-team-explorer-sml.png" alt-text="2019'Bağlan 'Takım Gezgini değiştirme' yordamı Visual Studio ekran görüntüsü." lightbox="media/switch-repos-team-explorer-lrg.png":::  </p>1 **. Bağlan açın**. <br>2. Yerel Depolar **listesinden bir depo** seçin. | :::image type="content" source="media/switch-repos-new-git-sml.png" alt-text="Visual Studio 2019'daki Yerel Depolar menü öğesinin ekran görüntüsü. 'Depoyu klonla' yordamı katmanlanmış." lightbox="media/switch-repos-new-git-lrg.png"::: </p> 1. **Git menüsünü** açın. <br>2. Yerel Depolar **listesinden bir depo** seçin.  |
|**Çözüm açma**  |  :::image type="content" source="media/open-solution-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'çözüm aç' yordamı katmanla birlikte, Takım Gezgini için Giriş penceresinin ekran görüntüsü." lightbox="media/open-solution-team-explorer-lrg.png":::</p>1. Giriş **sayfasını** **Takım Gezgini.** <br>2. Çözüm listesinden bir çözüm seçin.  |  :::image type="content" source="media/open-solution-new-git-sml.png" alt-text="'çözüm Çözüm Gezgini' yordam Visual Studio 2019'daki örnek olaylarının ekran görüntüsü." lightbox="media/open-solution-new-git-lrg.png":::</p>1. Görünüm **değiştir sayfasını** **Çözüm Gezgini.** <br>2. Çözüm listesinden bir çözüm seçin.  |
|**Kaynak denetimine çözüm ekleme ve yeni depo oluşturma**  | :::image type="content" source="media/source-control-team-explorer-sml.png" alt-text="Visual Studio 2019'daki Takım Gezgini seçeneklerinin ekran görüntüsü, Kaynak Denetimine Ekle - Repo oluştur yordam katmanla." lightbox="media/source-control-team-explorer-lrg.png":::</p>1. Kaynak Denetimine **Ekle durum çubuğu menüsünden** **Git'i** seçin. <br>2. **Yayımla'yı seçin**.  | :::image type="content" source="media/source-control-new-git-sml.png" alt-text="Visual Studio 2019'daki Git seçeneklerinin ekran görüntüsü. 'Kaynak denetimine ekle - depo oluştur' yordamı katman." lightbox="media/source-control-new-git-lrg.png":::</p>1. Kaynak Denetimine Ekle durum  çubuğu menüsünden **Git'i** seçin veya üst düzey menü çubuğundan **GitOlu** >  Visual Studio seçin. <br>2. Oluştur ve **It'i seçin**. </p> **Not**: Kodunuzu depolamaya eklemek için mevcut uzak seçeneği Azure DevOps. Bu durumda, önce bir Azure DevOps oluşturmanız gerekir. |
> [!TIP]
> [Git deneyimi,](git-with-visual-studio.md) açtığınız depoya veya Azure DevOps doğru depoya otomatik olarak bağlanacaktır. Bununla birlikte, bir repoya el ile bağlanmanız gerekirse, bunu yine de Takım Gezgini. Yeni menü Visual Studio Görünüm'Takım Gezgini  >  > **Bağlantıları** >  **Bağlan.**

## <a name="git-changes"></a>Git değişiklikleri

|         |Ekip Gezgini  |Git deneyimi |
|---------|---------|---------|
|**Yürütme ve aşama** | :::image type="content" source="media/commit-stage-team-explorer-sml.png" alt-text="Takım Gezgini 2019'da 'işleme ve aşama' yordamı katmanla birlikte Visual Studio için Değişiklikler penceresinin ekran görüntüsü." lightbox="media/commit-stage-team-explorer-lrg.png":::  </p>1. Bir işleme iletisi girin. <br>2. Hepsini **İşle'yi seçin**. <br>3. Belirli dosyaları aşamaya eklemek için, dosyalara sağ tıklayın ve Ardından Aşama'yı **seçin**.  | :::image type="content" source="media/commit-stage-new-git-sml.png" alt-text="Visual Studio 2019'daki Git Değişiklikleri penceresinin ekran görüntüsü, 'işleme ve aşama' yordam katmanla." lightbox="media/commit-stage-new-git-lrg.png"::: </p>1. Bir işleme iletisi girin. <br>2. Hepsini **İşle'yi seçin**. <br>3. Belirli dosyaları aşamak için üzerine gelin ve ardından "" simgesine **+** tıklayın. |
|**Bir işlemeyi değiştirme** |  :::image type="content" source="media/amend-commit-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'işlemeyi düzelt' yordamı katmanla birlikte Takım Gezgini için Değişiklikler penceresinin ekran görüntüsü." lightbox="media/amend-commit-team-explorer-lrg.png":::</p>1. Eylemler **açılan** listesinden tıklayın. <br>2. Önceki **Işlemeyi Düzelt'i seçin**. | :::image type="content" source="media/amend-commit-new-git-sml.png" alt-text="Visual Studio 2019'daki Git Değişiklikleri penceresinin ekran görüntüsü, 'işlemeyi değiştirme' yordamı katmanla." lightbox="media/amend-commit-new-git-lrg.png"::: </p>1. Düzelt **onay** kutusuna tıklayın. <br>2. Güncelleştirmelerinizi **işlemek için Hepsini** Işle'ye tıklayın.  |
|**Değişikliği gizli olarak saklama** | :::image type="content" source="media/stash-change-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'değişiklik hazırla' yordamı katmanla birlikte Takım Gezgini için Değişiklikler penceresinin ekran görüntüsü." lightbox="media/stash-change-team-explorer-lrg.png":::</p>1. Zula **açılan** açılan'a tıklayın. <br>2. İlgili Stash **seçeneğini** belirleyin. | :::image type="content" source="media/stash-change-new-git-sml.png" alt-text="Visual Studio 2019'daki Git Değişiklikleri penceresinin ekran görüntüsü, 'değişiklik ekleme' yordamı katmanla." lightbox="media/stash-change-new-git-lrg.png":::</p>1. Tüm Commit **All (TümLeri Işle) açılan** açılan listesinden tıklayın. <br>2. İlgili Stash **seçeneğini** belirleyin. |

## <a name="synchronization"></a>Eşitleme

|         |Ekip Gezgini  |Git deneyimi |
|---------|---------|---------|
|**Değişiklikleri getirme, çekme ve itme** | :::image type="content" source="media/fetch-pull-push-team-explorer-sml.png" alt-text="Takım Gezgini 2019'da 'getir, çek ve Visual Studio' yordam katmanla eşitleme penceresinin ekran görüntüsü." lightbox="media/fetch-pull-push-team-explorer-lrg.png":::</p>1. Eşitleme **sayfasına** gidin. <br>2. İstediğiniz ağ işlemine tıklayın. | :::image type="content" source="media/fetch-pull-push-new-git-sml.png" alt-text="Visual Studio 2019'da 'getirme, çekme ve itme' yordamı katmanla Git Değişiklikleri penceresinin ekran görüntüsü." lightbox="media/fetch-pull-push-team-new-git-lrg.png"::: </p>1. Git Değişiklikleri penceresinde getirme, çekme ve itme **düğmelerini** bulun. <br>2. İstediğiniz ağ işlemine tıklayın.|
|**Gelen ve Giden işlemeleri görüntüleme** | :::image type="content" source="media/view-commits-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'gelen ve giden işlemeleri görüntüle' yordamı katmanla birlikte, Takım Gezgini için Eşitleme penceresinin ekran görüntüsü." lightbox="media/view-commits-team-explorer-lrg.png"::: </p>1. Eşitleme **sayfasına** gidin. <br>2. Gelen ve giden listelerinizi görüntüleme. | :::image type="content" source="media/view-commits-new-git-sml.png" alt-text="Visual Studio 2019'daki Git Değişiklikleri penceresinin ve Git Deposu penceresinin ekran görüntüsü. 'Gelen ve giden işlemeleri görüntüleme' yordamı katman." lightbox="media/view-commits-new-git-lrg.png":::</p>1. Git **Değişiklikleri penceresinde giden/** gelen **bağlantıya** tıklayın. <br>2. Git Deposu penceresinin üst kısmında yer alan grafik tablosunda yer alan simgeleri kullanarak gelen ve giden **işlemelerinizi** görüntüleyin. |

## <a name="branches"></a>Dallar

|         |Ekip Gezgini  |Git deneyimi |
|---------|---------|---------|
|**Dal oluşturma** |  :::image type="content" source="media/create-branch-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'yeni bir dal oluştur' yordam katmanını kullanarak Takım Gezgini için Dallar penceresinin ekran görüntüsü." lightbox="media/create-branch-team-explorer-lrg.png":::</p>1. Dallar **penceresine** gidin. <br> 2. Yeni **Dal'a tıklayın**. | :::image type="content" source="media/create-branch-new-git-sml.png" alt-text="Visual Studio 2019'daki Git Değişiklikleri penceresinin ekran görüntüsü. 'Yeni dal oluştur' yordamı katmanla." lightbox="media/create-branch-new-git-lrg.png"::: </p>1. **Git Değişiklikleri penceresinde** dal açılan listesine tıklayın. <br>2. Yeni **Dal'a tıklayın**. |
|**Uzak daldan en son değişiklikleri al** | :::image type="content" source="media/sync-remote-team-explorer-sml.png" alt-text="Visual Studio 2019'da 'uzak daldan son değişiklikleri al' yordam katmanını kullanarak Takım Gezgini için Dallar penceresinin ekran görüntüsü." lightbox="media/sync-remote-team-explorer-lrg.png"::: </p>1. Dallar **sayfasına gidin**. <br>2. Uzak dala sağ tıklayın ve Birleştirme Kaynağı **veya Yeniden Temeli** **Üzerine'yi seçin**.  | :::image type="content" source="media/sync-remote-new-git-sml.png" alt-text="Visual Studio 2019'da 'uzak daldan son değişiklikleri al' yordam katmanını kullanarak Git Değişiklikleri penceresinin ekran görüntüsü." lightbox="media/sync-remote-new-git-lrg.png":::</p>1. Dal açılan listesine tıklayın. <br>2. Uzaklar **sekmesinin altında** uzak dala tıklayın ve Güncel Dalı'de **Birleştir'i veya** **Güncel Dalı'yi seçin**.  |
|**Dalları yönetme** | :::image type="content" source="media/manage-branches-team-explorer-sml.png" alt-text="Takım Gezgini 2019'da 'dalları yönet' yordamı katmanla birlikte Visual Studio için Dallar penceresinin ekran görüntüsü." lightbox="media/manage-branches-team-explorer-lrg.png"::: </p>1. Dallar **penceresine** gidin. <br>2. Yönetmek istediğiniz dallara sağ tıklayın. <br>3. **Commit'leri** yönetmek için dalların geçmişini görüntüleme. | :::image type="content" source="media/manage-branches-new-git-sml.png" alt-text="2019'da dalları yönetmek için üç kullanıcı arabirimi Visual Studio ekran görüntüsü." lightbox="media/manage-branches-new-git-lrg.png"::: </p>1. Aşağıdaki giriş noktalarından birini kullanarak Git deposu penceresine gidin: <br><br>a. Üst düzey üst düzey Visual Studio Git Dalları **İdare'yi** >  **seçin**.<br> b. Git **değişiklikleri gelecek** > **/giden'i seçin**. <br>c. Sağ alttaki durum çubuğu menüsünden Dalları **Yönet'i seçin**.<br> <br> 2. Üst düzey **GitManage** >  **Dalları** menüsünde aşağıdaki eylemlerden birini yapın: <br><br>A. Dallara sağ tıklayın.<br>B. Yönetmek istediğiniz işlemeleri çoklu seçin. |

## <a name="conflict-resolution"></a>Çakışma çözümü

|         |Ekip Gezgini  |Git deneyimi |
|---------|---------|---------|
|**Çakışmaları olan dosyaların listesine erişme** | :::image type="content" source="media/resolve-conflicts-team-explorer-sml.png" alt-text="Visual Studio 2019'daki Takım Gezgini için Değişiklikler penceresinin ve Çakışmaları Çözümle penceresinin ekran görüntüsü." lightbox="media/resolve-conflicts-team-explorer-lrg.png":::</p>1. Çakışmalar **bağlantısına** tıklayarak Çakışmaları Çözümle **penceresine** gidin. <br> 2. Birleştirme **çakışmalarınızı** çözmek için Çakışmalar listesini kullanın. | :::image type="content" source="media/resolve-conflicts-new-git-sml.png" alt-text="Visual Studio 2019'daki Git Değişiklikleri penceresinin ekran görüntüsü ve 'çakışmaları çözümleme' yordamı katmanlandı." lightbox="media/resolve-conflicts-new-git-lrg.png"::: </p>1. Çakışmalarla **birleştirme devam ediyor'ın görüntülendiğinden emin** olmak. <br>2. Birleştirme çakışmaları olan dosyaların listesi Git Değişiklikleri **penceresinin** Birleştirlanmamış Değişiklikler **bölümünde** görünür. <br>Çakışmaları çözümleme. |

## <a name="next-steps"></a>Sonraki adımlar

Git deneyimi hakkında daha fazla bilgi için YouTube'daki [Visual Studio 2019'da Git](https://www.youtube.com/watch?v=GCZ9x3yqkyc) ile çalışmaya başlama adlı en son videoya bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 2019'da Git deneyimi](git-with-visual-studio.md?view=vs-2019&preserve-view=true)
- [Başlarken Git ve GitHub ile Visual Studio](/learn/modules/visual-studio-github-push/)
- [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)
