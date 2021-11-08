---
title: Visual Studio'de Git deneyimi
titleSuffix: ''
description: Visual Studio'daki yeni tümleşik Git deneyiminin daha üretken çalışmanıza nasıl yardımcı olacağını öğrenin.
ms.date: 11/08/2021
ms.topic: overview
ms.author: tglee
author: TerryGLee
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.manager: jmartens
ms.openlocfilehash: c2e1d75347e3d10da0971fbf2da3d22148f0860b
ms.sourcegitcommit: 67dc39e93c86ba50eb5ca877b0471fb8ab8475ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2021
ms.locfileid: "132001072"
---
# <a name="git-experience-in-visual-studio"></a>Visual Studio'de Git deneyimi

::: moniker range=">=vs-2022"

Git, önceki sürümlerde varsayılan sürüm denetimi Visual Studio. Özellik kümesi derlemeye ve geri bildiriminize göre bu kümeyi yeniden derlemeye devam edeceğiz. Son özellik güncelleştirmesi hakkında daha fazla bilgi ve bununla ilgili geri bildiriminizi paylaşabilirsiniz anket bağlantısı için, Visual Studio blog gönderisinde [Multi-repo](https://devblogs.microsoft.com/visualstudio/multi-repo-support-in-visual-studio/) desteğine bakın.

::: moniker-end

::: moniker range="<=vs-2019"

Git artık Visual Studio 2019'da varsayılan sürüm denetimi deneyimidir. Sürüm [16.6'dan](/visualstudio/releases/2019/release-notes-v16.6)bu yana, geri bildiriminize göre özellik kümesi üzerinde çalışma ve bu küme üzerinde bir kez daha çalışmamız oldu. Sürüm [16.8'de](/visualstudio/releases/2019/release-notes-v16.8)herkes için varsayılan sürüm denetimi deneyimi haline geldi.

> [!NOTE]
> [2022'de](/visualstudio/releases/2022/release-notes-preview)de Git özellik kümesinde derlemeye ve Visual Studio devam edeceğiz. Son özellik güncelleştirmesi hakkında daha fazla bilgi edinmek için, Visual Studio blog gönderisinde Çoklu [Visual Studio](https://devblogs.microsoft.com/visualstudio/multi-repo-support-in-visual-studio/) bakın.

::: moniker-end

## <a name="learn-more-about-git"></a>Git hakkında daha fazla bilgi

Git en yaygın olarak kullanılan modern sürüm denetimi sistemidir, bu nedenle profesyonel bir geliştirici olun veya kod kodla ilgili bilgi edinseniz Git sizin için çok yararlı olabilir. Git'i yeni başladıysanız, [https://git-scm.com/](https://git-scm.com/) web sitesi başlamak için iyi bir yerdir. Burada bilgi sayfaları, popüler bir çevrimiçi kitap ve Git Temel Bilgileri videoları bulabilirsiniz.

## <a name="how-to-use-git-in-visual-studio"></a>Git'i Visual Studio

::: moniker range="<=vs-2019"

Visual Studio'de yeni Git deneyimini nasıl kullanabileceğiniz hakkında size yol göstermemiz gerekir, ancak önce hızlı bir tura olmak için aşağıdaki videoya göz atabilirsiniz: <br><br>*Video uzunluğu: 5,27 dakika*

> [!VIDEO https://www.youtube.com/embed/UHrAg3iKoe0]

::: moniker-end

Daha üretken olmak için Git'i Visual Studio üç yol vardır:

- [Yeni bir Git deposu oluşturun.](#create-a-new-git-repository) Kodunuz Git ile ilişkili değilse yeni bir Git deposu oluşturabilirsiniz.
- [Var olan bir Git deposunu klonlama.](#clone-an-existing-git-repository) Üzerinde çalışmak için kullanmak üzere kod makineniz üzerinde yoksa, mevcut uzak depoları kopyaabilirsiniz.
- [Var olan bir Git deposunu açın.](#open-an-existing-local-repository) Kodunuz makinede zaten varsa, Dosya Aç   >    >  **Project/Çözüm** (veya Klasör) kullanarak açabilir ve Visual Studio başlatılmış bir Git deposu olup Visual Studio otomatik olarak algılar.

::: moniker range="<=vs-2019"

> [!NOTE]
> 2019 Visual Studio [16.8](/visualstudio/releases/2019/release-notes-v16.8)sürümünden başlayarak, tamamen tümleşik bir GitHub deneyimi sağlıyoruz. Artık hem hesaplarınızı hem GitHub GitHub Enterprise anahtarlıklara ekebilirsiniz. Microsoft hesaplarıyla olduğu gibi bunları da ekleyebilir ve kullanabilirsiniz. Bu sayede farklı hesaplarda GitHub daha kolay Visual Studio. Daha fazla bilgi için Visual Studio sayfasında GitHub [hesaplarıyla](../ide/work-with-github-accounts.md) çalışma.

::: moniker-end

::: moniker range="vs-2022"

> [!NOTE]
> Visual Studio tamamen tümleşik bir hesap GitHub deneyimi içerir. Anahtarlık hesabınıza hem GitHub hem de GitHub Enterprise eklemekle birlikte, Aynı Microsoft hesaplarıyla olduğu gibi bunları da kullanabilirsiniz. Daha fazla bilgi için Visual Studio sayfasında GitHub [hesaplarıyla](../ide/work-with-github-accounts.md) çalışma.

::: moniker-end

## <a name="create-a-new-git-repository"></a>Yeni git deposu oluşturma

::: moniker range="vs-2022"

Kodunuz Git ile ilişkili değilse yeni bir Git deposu oluşturarak başlayabilirsiniz. Tüm [ayrıntılar için Visual Studio'da](git-create-repository.md) bir repo oluşturma sayfasına bakın.

::: moniker-end

::: moniker range="<=vs-2019"

Kodunuz Git ile ilişkili değilse yeni bir Git deposu oluşturarak başlayabilirsiniz. Bunu yapmak için menü  >  **çubuğundan Git Deposu Oluştur'a** tıklayın. Ardından Git **deposu oluştur iletişim** kutusuna bilginizi girin.

:::image type="content" source="media/git-create-repository.png" alt-text="Git Deposu Oluştur iletişim kutusu Visual Studio.":::

**Git deposu oluştur iletişim kutusu,** yeni depoyu depoya kolayca GitHub. Varsayılan olarak, yeni deponuz özeldir ve bu da depoya erişen tek deponun siz olduğu anlamına gelir. Kutunun işaretini kaldırsanız, depo genel olur ve bu durumda depoyu GitHub herkes süzebilirsiniz.

> [!TIP]
> Deponun genel veya özel olup olmadığı, bir ekiple çalışmasanız bile kodunuzun uzaktan yedeklerinin güvenli bir şekilde GitHub depolanmış bir depoya sahip olmak en iyisidir. Bu sayede hangi bilgisayarı kullanıyor olursanız olun kodunuzun kullanımınıza hazır olur.

Yalnızca yerel git deposu oluşturmak için Yalnızca yerel seçeneğini **kullanabilirsiniz.** Ya da Mevcut Uzak seçeneğini kullanarak yerel projenizi Azure DevOps veya başka bir Git sağlayıcısında var olan boş bir uzak **depoyla bağlantı oluşturabilirsiniz.**

::: moniker-end

## <a name="clone-an-existing-git-repository"></a>Mevcut git deposunu kopyalama

::: moniker range="vs-2022"

Visual Studio, basit bir kopyalama deneyimi içerir. Adım adım kılavuz için, Visual Studio sayfasındaki [Bir Visual Studio](git-clone-repository.md) bakın.

::: moniker-end

::: moniker range="<=vs-2019"

Visual Studio, basit bir kopyalama deneyimi içerir. Klonlamak istediğiniz deponun URL'sini biliyorsanız, URL'yi Depo  konumu bölümüne yapıştırabilirsiniz ve ardından klonlamak istediğiniz disk Visual Studio seçebilirsiniz.

:::image type="content" source="media/git-clone-repository.png" alt-text="Git Deposu Kopyala iletişim kutusu Visual Studio.":::

Depo URL'sini bilmiyorsanız Visual Studio depoya göz atmanızı ve mevcut depoyu kopyalamanızı GitHub Azure DevOps kolaylaştırır.

::: moniker-end

## <a name="open-an-existing-local-repository"></a>Mevcut bir yerel depoyu açma

Depoyu klonladikten veya oluşturduktan sonra Visual Studio Git deposunu algılar ve Git menüsündeki  Yerel Depolar listenize ekler.

::: moniker range="<=vs-2019"

Buradan Git depolarına hızlıca erişin ve bu depolar arasında geçişe geçin.

:::image type="content" source="media/git-local-repositories.png" alt-text="Visual Studio'daki Git menüsündeki Yerel Depolar Visual Studio ":::

::: moniker-end

## <a name="view-files-in-solution-explorer"></a>Dosyaları Çözüm Gezgini

Bir depoyu kopyaladığınız veya yerel bir depoyu Visual Studio, önceden açık olan çözümleri ve projeleri kaydederek ve kapatarak sizi bu Git bağlamına açar. Çözüm Gezgini Git deposunun köküne klasörü yükler ve değiştirilebilir dosyalar için dizin ağacını tarar. Bunlar, dosya adı CMakeLists.txt .sln dosya uzantısına sahip dosyaları içerir.

::: moniker range="vs-2022"

Daha fazla bilgi için, [Projeyi bir Çözüm Gezgini](../get-started/tutorial-open-project-from-repo.md#view-files-in-solution-explorer) açma [öğreticisi'nin Dosyalarda dosyaları](../get-started/tutorial-open-project-from-repo.md?view=vs-2022&preserve-view=true) görüntüleme bölümüne bakın.

::: moniker-end

::: moniker range="<=vs-2019"

Visual Studio, görünümde hangi dosyayı yükley istediğinize göre Çözüm Gezgini:

- Tek bir .sln dosyası içeren bir depoyu kopyalarsanız, Çözüm Gezgini doğrudan yüklersiniz.
- Depo Çözüm Gezgini herhangi bir .sln dosyası algılamazsa, varsayılan olarak Klasör Görünümü'dür.
- Depoda birden fazla .sln dosyası varsa, Çözüm Gezgini kullanılabilir Görünümler listesini gösterir.

Açık olan Görünümler ve Görünümler listesi arasında geçiş yapmak için araç çubuğundaki Görünümleri **Değiştir** düğmesini Çözüm Gezgini seçebilirsiniz.

:::image type="content" source="media/git-solution-explorer-views.png" alt-text="Çözüm Gezgini'da Görünümleri Değiştir düğmesi seçili Visual Studio.":::

::: moniker-end

## <a name="git-changes-window"></a>Git Değişiklikleri penceresi

Git, siz çalışırken depoda yapılan dosya değişikliklerini izler ve depoda yer alan dosyaları üç kategoriye ayırıyor. Bu değişiklikler, komut satırına komutu girerken `git status` göreceğiniz değişikliklerle eşdeğerdir:

- **Değiştirilmemiş dosyalar:** Bu dosyalar son işlemeden bu yana değişmemiştir.
- **Değiştirilen dosyalar:** Bu dosyalarda son işlemeden bu yana değişiklikler vardır, ancak bunları henüz bir sonraki işleme için hazırlanmadınız.
- **Aşamalı dosyalar:** Bu dosyalar, sonraki işlemeye eklenecek değişikliklere sahip olur.

Çalışmanızı yaptığınız gibi Visual Studio Git Değişiklikleri penceresinin Değişiklikler bölümünde projenize **yapılan** dosya **değişikliklerini takip** edin.

::: moniker range="<=vs-2019"

:::image type="content" source="media/git-changes-window.png" alt-text="Git Değişiklikleri penceresi Visual Studio.":::

::: moniker-end

Değişiklikleri aşamaya hazırsanız, aşamaya almak istediğiniz her dosyada (artı) düğmesine tıklayın veya bir dosyaya sağ tıklar ve ardından **+** Aşama'yı **seçin.** Ayrıca Değişiklikler bölümünün üst kısmında yer alan stage all (plus) düğmesini kullanarak değiştirilen tüm dosyalarınızı **+** tek tıklamayla da **aşamalayabilirsiniz.**

Bir değişikliği aşamaya Visual Studio bir **Aşamalı Değişiklikler bölümü** oluşturur. Bir sonraki **işlemeye yalnızca** Aşamalı Değişiklikler bölümündeki değişiklikler eklenir ve Bunu, Commit Staged (İşle Aşamalı) **öğesini seçerek yapabilirsiniz.** Bu eylemin eşdeğer komutu şu `git commit -m "Your commit message"` şekildedir: . Değişiklikler , – (eksi) düğmesine tıklayarak **dastaged** olabilir. Bu eylemin eşdeğer komutu, tek `git reset <file_path>` bir dosyanın hazırlanmamış veya bir dizinde yer alan tüm dosyaların `git reset <directory_path>` hazırsız olarak hazırlanmamıştır.

Ayrıca, hazırlama alanı atlayarak değiştirilen dosyalarınızı hazırlamamayı seçebilirsiniz. Bu durumda, Visual Studio doğrudan işlemenize olanak sağlar. Yalnızca işleme iletinizi girin ve Ardından Hepsini **İşle'yi seçin.** Bu eylemin eşdeğer komutu şu `git commit -a` şekildedir: .

Visual Studio, Hepsini Commit ve Push ve Commit All ve  Sync kısayollarını kullanarak tek tıklamayla işlemeyi ve **eşitlemeyi de** kolaylaştırır. Değişiklikler ve Aşamalı değişiklikler bölümlerindeki herhangi  bir dosyaya çift tıklarsanız, dosyanın değiştirilmemiş sürümüyle satır satır karşılaştırması yapabilirsiniz. 

::: moniker range="<=vs-2019"

:::image type="content" source="media/git-file-version-compare.png" alt-text="Visual Studio'daki dosya sürümlerinin satır satır karşılaştırması ":::

::: moniker-end

::: moniker range="vs-2022"

> [!TIP]
> Depoya Azure DevOps "#" karakterini kullanarak bir iş öğesini bir işlemeyle Azure DevOps.

::: moniker-end

::: moniker range="<=vs-2019"

> [!TIP]
> Depoya Azure DevOps "#" karakterini kullanarak bir iş öğesini bir işlemeyle Azure DevOps. Bağlantılarınızı Yönet Azure DevOps kullanarak Takım Gezgini   >  **bağlanabilirsiniz.**

::: moniker-end

### <a name="select-an-existing-branch"></a>Mevcut bir dalı seçme

Visual Studio Git Değişiklikleri penceresinin üst kısmında seçicide geçerli **dalı** görüntüler.

::: moniker range="<=vs-2019"

:::image type="content" source="media/git-changes-current-branch-selector.png" alt-text="Uygulamanın Git Değişiklikleri seçicisi üst kısmında yer alan seçiciyi kullanarak görüntü Visual Studio ":::

::: moniker-end

Geçerli dal, IDE'nin sağ alt köşesindeki durum çubuğunda Visual Studio kullanılabilir.

::: moniker range="<=vs-2019"

:::image type="content" source="media/git-changes-current-branch-status-bar.png" alt-text="Visual Studio IDE'nin sağ alt köşesindeki durum çubuğunu kullanarak görüntü Visual Studio.":::

::: moniker-end

Her iki konumdan da mevcut dallar arasında geçiş yapılabilir.

### <a name="create-a-new-branch"></a>Yeni dal oluşturma

Ayrıca yeni bir dal da oluşturabilirsiniz. Bu eylemin eşdeğer komutu şu `git checkout -b <branchname>` şekildedir: .

Yeni bir dal oluşturmak, dal adını girmek ve mevcut bir daldan değiştirmek kadar kolaydır.

::: moniker range="<=vs-2019"

:::image type="content" source="media/git-changes-create-new-branch.png" alt-text="Yeni Dal Oluştur iletişim kutusu Visual Studio ":::

::: moniker-end

Temel olarak mevcut bir yerel veya uzak dalı seçebilirsiniz. Teslim **alma dalı** onay kutusu sizi otomatik olarak yeni oluşturulan dala geçiştir. Bu eylemin eşdeğer komutu şu `git checkout -b <new-branch><existing-branch>` şekildedir: .

## <a name="git-repository-window"></a>Git Deposu penceresi

Visual Studio tüm dallar, uzak depolar ve commit histories dahil olmak üzere depo tüm ayrıntıların birleştirilmiş bir görünümü olan yeni **bir Git** Deposu penceresi vardır. Bu pencereye doğrudan menü **çubuğundaki Git** veya **Görünüm'den** veya durum çubuğundan erişebilirsiniz.

### <a name="manage-branches"></a>Dalları yönetme

**Git** **menüsünden Dalları** Yönet'i seçerek Git Deposu penceresinde dallar ağaç **görünümünü** görebilirsiniz. Sol bölmede sağ tıklama bağlam menüsünü kullanarak dalları tamamlar, yeni dallar oluşturabilir, birleştirebilirsiniz, yeniden temeli oluşturabilir, tek tek seçebilirsiniz ve daha fazlasını yapabilirsiniz. Dala tıklarken sağ bölmede işleme geçmişinin önizlemesini görebilirsiniz.

### <a name="incoming-and-outgoing-commits"></a>Gelen ve giden işlemeler

Bir dal getirebilirsiniz, **Git Değişiklikleri** penceresinde, dal açılan listesinde uzak daldan gelen işlanmamış işlemelerin sayısını gösteren bir gösterge vardır. Bu gösterge ayrıca size, işlenmiş olmayan yerel işlemelerin sayısını gösterir.

::: moniker range="<=vs-2019"

:::image type="content" source="media/git-repo-drop-down-indicator.png" alt-text="Kullanıcı arabiriminde gösterge açılan kullanıcı arabirimi öğesini gösteren Git Değişiklikleri Visual Studio ":::

::: moniker-end

Gösterge ayrıca sizi Git Deposu penceresinde bu dalın işleme geçmişine götüren bir **bağlantı olarak da** işlev gösterir. Geçmişin en üstünde artık bu gelen ve giden işlemelerin ayrıntıları görüntülenir. Buradan işlemeleri çekme veya itme kararlarını da vesersiniz.

::: moniker range="<=vs-2019"

:::image type="content" source="media/git-branch-commit-history.png" alt-text="Git Deposundaki bir dalın işleme geçmişini gösteren git deposu Visual Studio ":::

::: moniker-end

#### <a name="commit-details"></a>Commit Details

Bir Commit 'e çift **tıklar** Visual Studio ayrıntılarını ayrı bir araç penceresinde açar. Buradan işlemeyi geri döndürebilirsiniz, işlemeyi sıfırlayabilirsiniz, işleme iletiyi düzeltebilirsiniz veya işlemede bir etiket oluşturabilirsiniz. Yürütmede değiştirilen bir dosyaya tıklarsanız, Visual Studio ve üst  öğesinin yan yana Fark görünümünü açar.

::: moniker range="<=vs-2019"

:::image type="content" source="media/git-branch-commit-details.png" alt-text="Visual Studio'daki Commit Details iletişim Visual Studio ":::

::: moniker-end

## <a name="handle-merge-conflicts"></a>Birleştirme çakışmalarını işleme

İki geliştirici bir dosyada aynı satırları değiştirirse ve Git hangisinin doğru olduğunu otomatik olarak bilmiyorsa birleştirme sırasında çakışmalar oluşabilir. Git birleştirmeyi durdurarak çakışmalı durumda olduğunu size bildirecektir.

::: moniker range="vs-2022"

Birleştirme çakışmaları ve bunları işleme hakkında daha fazla bilgi edinmek için Birleştirme [çakışmalarını çözümleme sayfasına](git-resolve-conflicts.md) bakın.

::: moniker-end

::: moniker range="<=vs-2019"

Visual Studio birleştirme çakışmalarını tanımlamayı ve çözmeyi kolaylaştırır. İlk olarak **Git Deposu penceresinde** pencerenin en üstünde altın bir bilgi çubuğu gösterilir.

:::image type="content" source="media/git-merge-conflict-gold-bar.png" alt-text="Visual Studio'de 'Birleştirme çakışmalarla tamamlandı' Visual Studio ":::

Git **Değişiklikleri penceresinde** ayrıca *'* Birleştirme devam ediyor çakışmalar ile devam ediyor' iletisi görüntülenir ve altındaki ayrı bölümde birleştirlanmamış dosyalar görüntülenir.

:::image type="content" source="media/git-merge-progress-conflicts-message.png" alt-text="'Birleştirme devam ediyor çakışmalarla sürüyor' iletisi Visual Studio ":::

Ancak bu pencerelerden hiçbiri açık değilse ve bunun yerine birleştirme çakışmaları olan dosyaya gidersiniz, aşağıdaki metni aramanız zorunda olmayacaktır:

```bash
    <<<<<<< HEAD
    =======
    >>>>>>> main
```

Bunun Visual Studio üst kısmında açılan dosyanın çakışmaları olduğunu belirten altın bilgi çubuğu görüntülenir. Ardından bağlantıya tıklayarak Birleştirme **Düzenleyicisi'ni açabilirsiniz.**

:::image type="content" source="media/git-merge-conflict-gold-info-bar.png" alt-text="Dosyada 'Dosya birleştirme çakışmaları içeriyor' iletisi Visual Studio ":::

### <a name="the-merge-editor"></a>Birleştirme Düzenleyicisi

Visual Studio'daki Birleştirme Düzenleyicisi gelen değişiklikleri, geçerli değişikliklerinizi ve birleştirmenin sonucu görüntüleyen üç yoldan bir birleştirme aracıdır. Dosyada çakışmalar ve otomatik olarak  birleştirilen farklar arasında gezinmek için Birleştirme Düzenleyicisi'nin en üst düzeyindeki araç çubuğunu kullanabilirsiniz.

:::image type="content" source="media/git-merge-editor.png" alt-text="Visual Studio'de Birleştirme Düzenleyicisi ":::

Ayrıca, farklılıkları göstermek/gizlemek, sözcük farklarını göstermek/gizlemek ve düzeni özelleştirmek için de iki durumlu düğmeyi kullanabilirsiniz. Her iki tarafta da tüm değişiklikleri bir taraftan veya diğer taraftan almak için kullanabileceğiniz onay kutuları vardır. Ancak tek tek değişiklikleri yapmak için, her iki tarafta da çakışan satırların sol tarafındaki onay kutularına tık edebilirsiniz. Son olarak, çakışmaları çözmeyi bitirerek Birleştirme **Düzenleyicisi'nde** Birleştirmeyi Kabul Et düğmesini seçin. Ardından bir işleme iletisi yazar ve çözümü tamamlamak için değişiklikleri işlersiniz.

::: moniker-end

## <a name="personalize-your-git-settings"></a>Git ayarlarınızı kişiselleştirme

Git ayarlarınızı hem depo düzeyinde hem de genel düzeyde kişiselleştirmek ve özelleştirmek için menü çubuğunda **Git** Ayarlar'ye veya menü çubuğundaKimlik Seçenekleri Kaynak  >     >    >   Denetimi'ne gidin. Ardından istediğiniz [seçenekleri](git-settings.md) belirleyin.

:::image type="content" source="media/git-options-settings.png" alt-text="IDE'de kişiselleştirme ve özelleştirme ayarlarını seçebilirsiniz Seçenekler Visual Studio kutusu.":::

::: moniker range="<=vs-2019"

## <a name="how-to-use-the-full-team-explorer-experience-in-visual-studio"></a>Visual Studio'de tam Takım Gezgini deneyimi Visual Studio

Yeni Git deneyimi, [16.8](/visualstudio/releases/2019/release-notes/) ve Visual Studio 2019'daki varsayılan sürüm denetimi sistemidir. Ancak, kapatmak istediğiniz zaman bunu da kapatmış oluruz. Araçlar Seçenekler  >  **Ortam**  >  **Önizleme**  >  **Özellikleri'ne**  gidin ve Yeni Git kullanıcı deneyimi onay kutusunu açıp kapatarak Git için Takım Gezgini geçiş yapabilirsiniz.

:::image type="content" source="media/git-opt-new-user-experience.png" alt-text="Visual Studio'daki Seçenekler iletişim kutusunun Önizleme Özellikleri Visual Studio ":::

::: moniker-end

## <a name="whats-next"></a>Sırada ne var?

::: moniker range="<=vs-2019"

Yeni Git deneyimi artık Visual Studio 2019 sürüm [16.8'den](/visualstudio/releases/2019/release-notes/)itibaren varsayılan olarak açıkken, deneyimi geliştirmek için yeni özellikler eklemeye devam edeceğiz. Bir Önizleme yayında Git deneyimine yapılan yeni güncelleştirmeleri kontrol etmek için, Visual Studio [2022 Preview](https://aka.ms/vspreview/) sayfasından indirip yükleyebilirsiniz.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio'da Git deneyimini geliştirmek için yeni özellikler eklemeye devam Visual Studio. Son özellik güncelleştirmesi hakkında daha fazla bilgi ve bununla ilgili geri bildiriminizi paylaşabilirsiniz anket bağlantısı için, Visual Studio blog gönderisinde [Multi-repo](https://devblogs.microsoft.com/visualstudio/multi-repo-support-in-visual-studio/) desteğine bakın.

::: moniker-end

> [!IMPORTANT]
> Bize bir öneriniz varsa lütfen bize haber ver! Geliştirici portalı üzerinden tasarım kararları alma fırsatınız için [**Community.**](https://aka.ms/vs-suggest)

## <a name="see-also"></a>Ayrıca bkz.

::: moniker range="<=vs-2019"

- [Başlarken 2019 GitHub'Visual Studio Git](/learn/modules/visual-studio-github-push/) ve Microsoft Learn
- [YouTube'daki Visual Studio Git](https://www.youtube.com/watch?v=GCZ9x3yqkyc) ile çalışmaya başlama
- Visual Studio blog [gönderisinde Git Deneyiminin Yayımlanma](https://devblogs.microsoft.com/visualstudio/announcing-the-release-of-the-git-experience-in-visual-studio/) Tarihi
- [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)
- [Visual Studio 2019 sürüm notları](/visualstudio/releases/2019/release-notes)
- [Visual Studio 2022 RC ve Önizleme sürüm notları](/visualstudio/releases/2022/release-notes-preview)

::: moniker-end

::: moniker range="vs-2022"

- [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)
- [Visual Studio 2022 RC ve Önizleme sürüm notları](/visualstudio/releases/2022/release-notes-preview)

::: moniker-end
