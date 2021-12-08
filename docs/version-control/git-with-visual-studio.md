---
title: Visual Studio'da Git deneyimi
titleSuffix: ''
description: Visual Studio'daki yeni tümleşik Git deneyiminin daha üretken çalışmanıza nasıl yardımcı olacağını öğrenin.
ms.date: 12/06/2021
ms.topic: overview
author: Taysser-Gherfal
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 9ef19894ffd48b5cba05ce05754e7881745ed1be
ms.sourcegitcommit: 64d6c5cf93984bbb22812577af17128cd2239f79
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2021
ms.locfileid: "134366962"
---
# <a name="git-experience-in-visual-studio"></a>Visual Studio'da Git deneyimi

::: moniker range=">=vs-2022"

Git, uygulamanın varsayılan sürüm denetimi Visual Studio. Özellik kümesi derlemeye ve geri bildiriminize göre bu kümeyi yeniden derlemeye devam edeceğiz. Son özellik güncelleştirmesi hakkında daha fazla bilgi ve bu güncelleştirmeyle ilgili geri bildiriminizi paylaşabilirsiniz anket bağlantısı için bkz. Çoklu Visual Studio [blog](https://devblogs.microsoft.com/visualstudio/multi-repo-support-in-visual-studio/) gönderisi.

## <a name="learn-more-about-git"></a>Git hakkında daha fazla bilgi

Git en yaygın olarak kullanılan modern sürüm denetimi sistemidir, bu nedenle profesyonel bir geliştirici olun veya kod kodla ilgili bilgi edinseniz Git sizin için çok yararlı olabilir. Git'i yeni başladıysanız, [https://git-scm.com/](https://git-scm.com/) web sitesi başlamak için iyi bir yerdir. Açık kaynak projeleriyle GitHub ve Visual Studio hakkında bilgi edinmek için Visual Studio'de Git öğrenme serisine kaydolarak GitHub [daha iyi bir şekilde](https://visualstudio.microsoft.com/vs/github/) öğrenin.

## <a name="start-with-git-in-visual-studio"></a>Git ile Visual Studio

Daha üretken olmak için Git'i Visual Studio üç yol vardır:

- [Yeni bir Git deposu oluşturun.](git-create-repository.md) Zaten Git ile ilişkilendirilen bir kodunuz varsa yeni bir Git deposu oluşturarak başlayabilirsiniz.
- [Var olan bir Git deposunu klonlama.](git-clone-repository.md) Üzerinde çalışmak için kullanmak üzere kod makineniz üzerinde değilse, mevcut uzak depoları kopyaabilirsiniz.
- [Var olan bir depoyu açın.](git-clone-repository.md#open-an-existing-local-repository) Kodunuz makinede zaten varsa, Dosya Aç   >    >  **Project/Çözüm** (veya Klasör) kullanarak açabilir ve Visual Studio başlatılmış bir Git deposu olup Visual Studio otomatik olarak algılar.

> [!NOTE]
> Visual Studio tamamen tümleşik bir hesap GitHub deneyimi içerir. Anahtarlık hesabınıza hem GitHub hem de GitHub Enterprise eklemekle birlikte, Aynı Microsoft hesaplarıyla olduğu gibi bunları da kullanabilirsiniz. Daha fazla bilgi için [bkz. GitHub hesaplarla çalışma Visual Studio.](../ide/work-with-github-accounts.md)

> [!TIP]
> GitHub hesabınız yoksa, GitHub hesabı oluşturma sayfasında açıklanan adımları [Visual Studio.](git-create-github-account.md)

## <a name="view-files-in-solution-explorer"></a>Dosyaları Çözüm Gezgini

Bir depoyu kopyalasanız veya yerel bir depoyu Visual Studio, önceden açılmış olan tüm çözümleri ve projeleri kaydetmek ve kapatmak istiyorsanız yeni Git bağlamına geçişler. Çözüm Gezgini Git deposunun köküne klasörü yükler ve değiştirilebilir dosyalar için dizin ağacını tarar. Bunlar, dosya adı CMakeLists.txt .sln dosya uzantısına sahip dosyaları içerir.

Daha fazla bilgi için, [Projeyi bir Çözüm Gezgini](../get-started/tutorial-open-project-from-repo.md#view-files-in-solution-explorer) açma [öğreticisi'nin Dosyalarda dosyaları](../get-started/tutorial-open-project-from-repo.md) görüntüleme bölümüne bakın.

## <a name="day-to-day-workflow"></a>Günlük iş akışı

Git, kullanıcılara birden çok görev için destek sağlar ve dallar aracılığıyla kodlarıyla denemeler sağlar. Siz veya takımınız aynı anda birden çok özellik üzerinde çalışıyorsanız veya çalışma kodunuzu etkilemeden fikirleri keşfetmek için çalışıyorsanız, dallama çok yararlı olabilir. Önerilen Git iş akışı, üzerinde çalışmakta olan her özellik veya düzeltme için yeni bir dal kullanır. Yeni dallar oluşturma hakkında daha fazla bilgi Visual Studio için Dal oluşturma [sayfasına](git-create-branch.md) bakın.

Yeni bir dal oluşturduk ve bu dala geçiş yapıldıktan sonra mevcut dosyaları değiştirerek veya yenilerini ekleyerek ve sonra çalışmamızı depoya işerek çalışmaya başlayabiliriz. Git'te bir işlemeyi Visual Studio ve Git'te dosya durumları daha iyi anlamak için, Commit yapma [sayfasına](git-make-commit.md) bakın.

Git dağıtılmış bir sürüm denetim sistemidir, yani şu ana kadar yapılan tüm değişiklikler yalnızca yerel değişikliklerdir. Bu değişiklikleri uzak depoya katkıda bulunmak için yerel commit'lerimizi itmemiz gerekir. Bir uzak sunucuya uzak Visual Studio daha fazla bilgi edinmek için Uzak sayfaya [itme sayfasına](git-push-remote.md) bakın.

Bir ekipte çalışıyorsanız veya farklı makineler kullanıyorsanız, uzak depoda sürekli olarak yeni değişiklikler getirmeniz ve çekmeniz de gerekir. Uygulama içinde Git ağ işlemlerini yönetme hakkında daha fazla Visual Studio için [Getirme, çekme, itme ve eşitleme sayfasına](git-fetch-pull-sync.md) bakın.

## <a name="browse-and-manage-git-repositories"></a>Git depolarına göz atma ve depoları yönetme

Günlük Git iş akışınız için Visual Studio koddan uzaklaşarak kod yazmanıza gerek kalmadan Git ile etkileşim kurmanın sorunsuz bir yolunu sağlar. Örneğin, dallar oluşturabilir ve bunlar arasında geçiş yapabilirsiniz. Ayrıca, kodunuz üzerinde çalışırken değişikliklerinizi işabilir, hazırlar ve itebilirsiniz. Ancak bazen Git depona odaklanmanın daha anlamlı olduğu zamanlar olur. Örneğin, takımınız üzerinde çalıştığı şeyler hakkında iyi bir fikir sahibi olmak veya farklı bir daldan bir işleme kopyalamak ya da yalnızca giden commit'lerinizi temizlemek için ihtiyacınız olabilir.

Git deponıza odaklanmanıza yardımcı olmak için Visual Studio yerel ve uzak dallar ve işleme geçmişi dahil olmak üzere depo tüm ayrıntıların birleştirilmiş bir görünümü olan **Git** Deposu penceresi vardır. Bu pencereye doğrudan menü **çubuğundaki Git** veya **Görünüm'den** veya durum çubuğundan erişebilirsiniz.

Git depona göz atmak ve depoyu yönetmek için Git Deposu penceresini nasıl kullanabileceğiniz hakkında daha fazla bilgi edinmek için aşağıdaki sayfalara bakın:

- [Visual Studio'de bir repoya göz atma](git-browse-repository.md)
- [Bir Visual Studio'de bir Visual Studio](git-manage-repository.md)

## <a name="handle-merge-conflicts"></a>Birleştirme çakışmalarını işleme

İki geliştirici bir dosyada aynı satırları değiştirirse ve Git hangisinin doğru olduğunu otomatik olarak bilmiyorsa birleştirme sırasında çakışmalar oluşabilir. Git birleştirmeyi durdurarak çakışmalı durumda olduğunu size bildirecektir.

Birleştirme çakışmaları ve bunları işleme hakkında daha fazla bilgi edinmek için Birleştirme [çakışmalarını çözümleme sayfasına](git-resolve-conflicts.md) bakın.

## <a name="personalize-your-git-settings"></a>Git ayarlarınızı kişiselleştirme

Git ayarlarınızı hem depo düzeyinde hem de genel düzeyde kişiselleştirmek ve özelleştirmek için menü çubuğunda **Git** Ayarlar'ye veya menü çubuğundaKimlik Seçenekleri Kaynak  >     >    >   Denetimi'ne gidin. Ardından istediğiniz [seçenekleri](git-settings.md) belirleyin.

:::image type="content" source="media/git-options-settings.png" alt-text="IDE'de kişiselleştirme ve özelleştirme ayarlarını seçebilirsiniz Seçenekler Visual Studio kutusu.":::

## <a name="whats-next"></a>Sırada ne var?

Visual Studio'da Git deneyimini geliştirmek için yeni özellikler eklemeye devam Visual Studio. Son özellik güncelleştirmesi hakkında daha fazla bilgi ve bununla ilgili geri bildiriminizi paylaşabilirsiniz bir ankete bağlantı için, Visual Studio blog gönderisinde [Multi-repo](https://devblogs.microsoft.com/visualstudio/multi-repo-support-in-visual-studio/) desteğine bakın. Bir Önizleme yayında Git deneyimine yapılan yeni güncelleştirmeleri kontrol etmek için, bunu [Visual Studio 2022 Preview sayfasından indirip yükleyebilirsiniz.](https://visualstudio.microsoft.com/vs/preview/)

> [!IMPORTANT]
> Bize bir öneriniz varsa lütfen bize haber ver! Geliştirici portalı üzerinden tasarım kararları alma fırsatınız için [**Community.**](https://aka.ms/vs-suggest)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio & GitHub: Birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)
- [Visual Studio 2022 sürüm notları](/visualstudio/releases/2022/release-notes)

::: moniker-end

::: moniker range="<=vs-2019"

Git artık Visual Studio **2019'da varsayılan sürüm denetimi deneyimidir.** Sürüm [16.6'dan](/visualstudio/releases/2019/release-notes-v16.6)bu yana, geri bildiriminize göre özellik kümesi üzerinde çalışmalara ve bu küme üzerinde bir kez daha çalışmalara çalıştık. Sürüm [16.8'de](/visualstudio/releases/2019/release-notes-v16.8)herkes için varsayılan sürüm denetimi deneyimi haline geldi.

> [!NOTE]
> [2022'de](/visualstudio/releases/2022/release-notes-preview)de Git özellik kümesinde derlemeye ve Visual Studio devam edeceğiz. Son özellik güncelleştirmesi hakkında daha fazla bilgi edinmek için, Visual Studio blog gönderisinde Çoklu [Visual Studio](https://devblogs.microsoft.com/visualstudio/multi-repo-support-in-visual-studio/) bakın.

## <a name="learn-more-about-git"></a>Git hakkında daha fazla bilgi

Git en yaygın olarak kullanılan modern sürüm denetimi sistemidir, bu nedenle profesyonel bir geliştirici olun veya kod kodla ilgili bilgi edinseniz Git sizin için çok yararlı olabilir. Git'i yeni başladıysanız, [https://git-scm.com/](https://git-scm.com/) web sitesi başlamak için iyi bir yerdir. Burada bilgi sayfaları, popüler bir çevrimiçi kitap ve Git Temel Bilgileri videoları bulabilirsiniz.

## <a name="start-with-git-in-visual-studio-2019"></a>Visual Studio 2019'da Git ile başlama

Visual Studio'da yeni Git deneyimini nasıl kullanabileceğiniz hakkında size yol göstermemiz gerekir, ancak önce hızlı bir tura olmak için aşağıdaki videoya göz atabilirsiniz: <br><br>*Video uzunluğu: 5,27 dakika*

> [!VIDEO https://www.youtube.com/embed/UHrAg3iKoe0]

Daha üretken olmak için Git'i Visual Studio üç yol vardır:

- [Yeni bir Git deposu oluşturun.](#create-a-new-git-repository-in-visual-studio-2019) Zaten Git ile ilişkilendirilen bir kodunuz varsa yeni bir Git deposu oluşturarak başlayabilirsiniz.
- [Var olan bir Git deposunu klonlama.](#clone-an-existing-git-repository-in-visual-studio-2019) Üzerinde çalışmak için kullanmak üzere kod makineniz üzerinde değilse, mevcut uzak depoları kopyaabilirsiniz.
- [Var olan bir Git deposunu açın.](#open-an-existing-local-repository-in-visual-studio-2019) Kodunuz makinede zaten varsa, Dosya Aç   >    >  **Project/Çözüm** (veya Klasör) kullanarak açabilir ve Visual Studio başlatılmış bir Git deposu olup Visual Studio otomatik olarak algılar.

> [!NOTE]
> 2019 Visual Studio [16.8](/visualstudio/releases/2019/release-notes-v16.8)sürümünden başlayarak, tamamen tümleşik bir GitHub deneyimi sağlıyoruz. Artık hem GitHub hem de GitHub Enterprise hesaplarını anahtarlık üzerine ekebilirsiniz. Microsoft hesaplarıyla olduğu gibi bunları da ekleyebilir ve kullanabilirsiniz. Bu sayede farklı hesaplarda GitHub daha kolay Visual Studio. Daha fazla bilgi için [bkz. GitHub hesaplarla çalışma Visual Studio.](../ide/work-with-github-accounts.md)

> [!TIP]
> GitHub hesabınız yoksa, GitHub hesabı oluşturma sayfasında açıklanan adımları [Visual Studio.](git-create-github-account.md)

## <a name="create-a-new-git-repository-in-visual-studio-2019"></a>Visual Studio 2019'da yeni bir Git deposu oluşturma

Kodunuz Git ile ilişkili değilse yeni bir Git deposu oluşturarak başlayabilirsiniz. Bunu yapmak için menü  >  **çubuğundan Git Git Deposu** Oluştur'a tıklayın. Ardından Git **deposu oluştur iletişim** kutusuna bilginizi girin.

:::image type="content" source="media/git-create-repository.png" alt-text="Git Deposu Oluştur iletişim kutusu Visual Studio.":::

**Git deposu oluştur iletişim kutusu,** yeni depoyu depoya kolayca GitHub. Varsayılan olarak, yeni deponuz özeldir ve bu da depoya erişen tek deponun siz olduğu anlamına gelir. Kutunun işaretini kaldırsanız, depo genel olur ve bu durumda depoyu GitHub sızabilirsiniz.

> [!TIP]
> Deponun genel veya özel olup olmadığı, bir ekiple çalışmasanız bile kodunuzun uzaktan yedeklerinin güvenli bir GitHub depoya sahip olmak en iyisidir. Bu sayede hangi bilgisayarı kullanıyor olursanız olun kodunuzun kullanımınıza hazır olur.

Yalnızca yerel git deposu oluşturmak için Yalnızca yerel seçeneğini **kullanabilirsiniz.** Ya da Mevcut Uzak seçeneğini kullanarak yerel projenizi Azure DevOps veya başka bir Git sağlayıcısında var olan boş bir uzak **depoyla bağlantı oluşturabilirsiniz.**

## <a name="clone-an-existing-git-repository-in-visual-studio-2019"></a>Visual Studio 2019'da mevcut git deposunu kopyalama

Visual Studio, basit bir kopyalama deneyimi içerir. Klonlamak istediğiniz deponun URL'sini biliyorsanız, URL'yi Depo  konumu bölümüne yapıştırabilirsiniz ve ardından klonlamak istediğiniz disk Visual Studio seçebilirsiniz.

:::image type="content" source="media/git-clone-repository.png" alt-text="Git Deposu Kopyala iletişim kutusu Visual Studio.":::

Depo URL'sini bilmiyorsanız Visual Studio depoya göz atmanızı ve mevcut depoyu kopyalamanızı GitHub Azure DevOps sağlar.

## <a name="open-an-existing-local-repository-in-visual-studio-2019"></a>Visual Studio 2019'da mevcut bir yerel depoyu açma

Depoyu klonladikten veya oluşturduktan sonra Visual Studio Git deposunu algılar ve Git menüsündeki  Yerel Depolar listenize ekler.

Buradan Git depolarına hızlıca erişin ve bu depolar arasında geçişe geçin.

:::image type="content" source="media/git-local-repositories.png" alt-text="Visual Studio'daki Git menüsündeki Yerel Depolar Visual Studio ":::

## <a name="view-files-in-solution-explorer-in-visual-studio-2019"></a>Visual Studio 2019'da Çözüm Gezgini dosyaları görüntüleme

Bir depoyu kopyaladığınız veya yerel bir depoyu Visual Studio, önceden açık olan çözümleri ve projeleri kaydederek ve kapatarak sizi bu Git bağlamına açar. Çözüm Gezgini Git deposunun köküne klasörü yükler ve değiştirilebilir dosyalar için dizin ağacını tarar. Bunlar, dosya adı CMakeLists.txt .sln dosya uzantısına sahip dosyaları içerir.

Visual Studio, görünümde hangi dosyayı yükley istediğinize göre Çözüm Gezgini:

- Tek bir .sln dosyası içeren bir depoyu kopyalarsanız, Çözüm Gezgini doğrudan yüklersiniz.
- Depo Çözüm Gezgini herhangi bir .sln dosyası algılamazsa, varsayılan olarak Klasör Görünümü'dür.
- Depoda birden fazla .sln dosyası varsa, Çözüm Gezgini seçebilirsiniz kullanılabilir Görünümler listesini gösterir.

Açık olan Görünüm ile Görünümler listesi arasında geçiş yapmak için araç çubuğundaki Görünümleri **Değiştir** düğmesini Çözüm Gezgini ekleyebilirsiniz.

:::image type="content" source="media/git-solution-explorer-views.png" alt-text="Çözüm Gezgini'da Görünümleri Değiştir düğmesi seçili Visual Studio.":::

Daha fazla bilgi için, [Projeyi bir Çözüm Gezgini](../get-started/tutorial-open-project-from-repo.md#view-files-in-solution-explorer) açma [öğreticisi'nin Dosyalarda dosyaları](../get-started/tutorial-open-project-from-repo.md?view=vs-2019&preserve-view=true) görüntüleme bölümüne bakın.

## <a name="git-changes-window-in-visual-studio-2019"></a>Visual Studio 2019'da Git Değişiklikleri penceresi

Git, siz çalışırken depoda yapılan dosya değişikliklerini izler ve depoda yer alan dosyaları üç kategoriye ayırıyor. Bu değişiklikler, komut satırına komutu girerken `git status` göreceğiniz değişikliklerle eşdeğerdir:

- **Değiştirilmemiş dosyalar:** Bu dosyalar son işlemeden bu yana değişmemiştir.
- **Değiştirilen dosyalar:** Bu dosyalarda son işlemeden bu yana değişiklikler vardır, ancak bunları henüz bir sonraki işleme için hazırlanmadınız.
- **Aşamalı dosyalar:** Bu dosyalar, sonraki işlemeye eklenecek değişikliklere sahip olur.

Çalışmanızı yaptığınız gibi Visual Studio Git Değişiklikleri penceresinin Değişiklikler bölümünde projenize **yapılan** dosya **değişikliklerini takip** edin.

:::image type="content" source="media/git-changes-window.png" alt-text="Git Değişiklikleri penceresi Visual Studio.":::

Değişiklikleri aşamaya hazırsanız, aşamaya almak istediğiniz her dosyada (artı) düğmesine tıklayın veya bir dosyaya sağ tıklar ve ardından **+** Aşama'yı **seçin.** Ayrıca Değişiklikler bölümünün üst kısmında yer alan stage all (plus) düğmesini kullanarak değiştirilen tüm dosyalarınızı **+** tek tıklamayla **da sıralayabilirsiniz.**

Bir değişikliği aşamaya Visual Studio bir **Aşamalı Değişiklikler bölümü** oluşturur. Bir sonraki **işlemeye yalnızca** Aşamalı Değişiklikler bölümündeki değişiklikler eklenir ve Bunu, Commit Staged (İşle Aşamalı) **öğesini seçerek yapabilirsiniz.** Bu eylemin eşdeğer komutu şu `git commit -m "Your commit message"` şekildedir: . Değişiklikler , – (eksi) düğmesine tıklayarak **dastaged** olabilir. Bu eylemin eşdeğer komutu, tek `git reset <file_path>` bir dosyanın hazırlanmamış veya bir dizinde yer alan tüm dosyaların `git reset <directory_path>` hazırsız olarak hazırlanmamıştır.

Ayrıca, hazırlama alanı atlayarak değiştirilen dosyalarınızı hazırlamamayı da seçebilirsiniz. Bu durumda Visual Studio doğrudan işlemenize olanak sağlar. Yalnızca işleme iletinizi girin ve Ardından Hepsini **İşle'yi seçin.** Bu eylemin eşdeğer komutu şu `git commit -a` şekildedir: .

Visual Studio, Hepsini Commit ve Push ve Commit All ve  Sync kısayollarını kullanarak tek tıklamayla işlemeyi ve **eşitlemeyi de** kolaylaştırır. Değişiklikler ve Aşamalı değişiklikler bölümlerindeki herhangi  bir dosyaya çift tıklarsanız, dosyanın değiştirilmemiş sürümüyle satır satır karşılaştırması yapabilirsiniz. 

:::image type="content" source="media/git-file-version-compare.png" alt-text="Visual Studio'de dosya sürümlerinin satır satır karşılaştırması ":::

> [!TIP]
> Depoya bağlı Azure DevOps "#" karakterini kullanarak bir iş öğesini bir işlemeyle Azure DevOps. Bağlantıları Yönet'i Azure DevOps kullanarak **Takım Gezgini**  >  **bağlanabilirsiniz.**

### <a name="select-an-existing-branch-in-visual-studio-2019"></a>Visual Studio 2019'da var olan bir dalı seçme

Visual Studio Git Değişiklikleri penceresinin üst kısmında seçicide geçerli **dalı** görüntüler.

:::image type="content" source="media/git-changes-current-branch-selector.png" alt-text="Aşağıdaki git değişiklikleri seçicinin üst kısmında yer alan seçiciyi kullanarak görüntü Visual Studio ":::

Geçerli dal, IDE'nin sağ alt köşesindeki durum çubuğunda Visual Studio kullanılabilir.

:::image type="content" source="media/git-changes-current-branch-status-bar.png" alt-text="IDE'nin sağ alt köşesindeki durum çubuğunu kullanarak görüntüleyebilirsiniz geçerli dallar Visual Studio.":::

Her iki konumdan da mevcut dallar arasında geçiş yapılabilir.

### <a name="create-a-new-branch-in-visual-studio-2019"></a>Visual Studio 2019'da yeni dal oluşturma

Ayrıca yeni bir dal da oluşturabilirsiniz. Bu eylemin eşdeğer komutu şu `git checkout -b <branchname>` şekildedir: .

Yeni bir dal oluşturmak, dal adını girmek ve mevcut bir daldan değiştirmek kadar kolaydır.

:::image type="content" source="media/git-changes-create-new-branch.png" alt-text="Yeni Dal Oluştur iletişim kutusu Visual Studio ":::

Temel olarak mevcut bir yerel veya uzak dalı seçebilirsiniz. Teslim **alma dalı** onay kutusu sizi otomatik olarak yeni oluşturulan dala geçiştir. Bu eylemin eşdeğer komutu şu `git checkout -b <new-branch><existing-branch>` şekildedir: .

## <a name="git-repository-window-in-visual-studio-2019"></a>Visual Studio 2019'da Git Deposu penceresi

Visual Studio tüm dallar, uzak depolar ve işleme histories dahil olmak üzere depo tüm ayrıntıların birleştirilmiş bir görünümü olan yeni bir **Git** Deposu penceresi vardır. Bu pencereye doğrudan menü **çubuğundaki Git** veya **Görünüm'den** veya durum çubuğundan erişebilirsiniz.

### <a name="manage-branches-in-visual-studio-2019"></a>Visual Studio 2019'da dalları yönetme

**Git** **menüsünden Dalları** Yönet'i seçerek Git Deposu penceresinde dallar ağaç **görünümünü** görebilirsiniz. Sol bölmede sağ tıklama bağlam menüsünü kullanarak dalları tamamlar, yeni dallar oluşturabilir, birleştirebilirsiniz, yeniden temeli oluşturabilir, tek tek seçebilirsiniz ve daha fazlasını yapabilirsiniz. Dala tıklarken sağ bölmede işleme geçmişinin önizlemesini görebilirsiniz.

### <a name="incoming-and-outgoing-commits-in-visual-studio-2019"></a>Visual Studio 2019'da gelen ve giden işlemeler

Bir dalı getirebilirsiniz. **Git Değişiklikleri** penceresinde, dal açılan listesinde uzak daldan gelen işlanmamış işlemelerin sayısını gösteren bir gösterge vardır. Bu gösterge ayrıca size, işlenmiş olmayan yerel işlemelerin sayısını gösterir.

:::image type="content" source="media/git-repo-drop-down-indicator.png" alt-text="Uygulamanın içinde gösterge açılan kullanıcı arabirimi öğesini gösteren Git Değişiklikleri Visual Studio ":::

Gösterge ayrıca sizi Git Deposu penceresinde bu dalın işleme geçmişine götüren bir **bağlantı olarak da** işlev gösterir. Geçmişin en üstünde artık bu gelen ve giden işlemelerin ayrıntıları görüntülenir. Buradan işlemeleri çekme veya itme kararlarını da vesersiniz.

:::image type="content" source="media/git-branch-commit-history.png" alt-text="Git Deposundaki bir dalın işleme geçmişini gösteren git deposu Visual Studio ":::

#### <a name="commit-details-in-visual-studio-2019"></a>Visual Studio 2019'da Commit Details

Bir Commit 'e çift **tıklar** Visual Studio ayrıntılarını ayrı bir araç penceresinde açar. Buradan işlemeyi geri döndürebilirsiniz, işlemeyi sıfırlayabilirsiniz, işleme iletiyi düzeltebilirsiniz veya işlemede bir etiket oluşturabilirsiniz. Yürütmede değiştirilen bir dosyaya tıklarsanız, Visual Studio ve üst öğesinin yan yana Fark görünümünü açar. 

:::image type="content" source="media/git-branch-commit-details.png" alt-text="Visual Studio'daki Commit Details iletişim Visual Studio ":::

## <a name="handle-merge-conflicts-in-visual-studio-2019"></a>Visual Studio 2019'da birleştirme çakışmalarını işleme

İki geliştirici bir dosyada aynı satırları değiştirirse ve Git hangisinin doğru olduğunu otomatik olarak bilmiyorsa birleştirme sırasında çakışmalar oluşabilir. Git birleştirmeyi durdurarak çakışmalı durumda olduğunu size bildirecektir.

Visual Studio birleştirme çakışmalarını tanımlamayı ve çözmeyi kolaylaştırır. İlk olarak **Git Deposu penceresinde** pencerenin en üstünde altın bir bilgi çubuğu gösterilir.

:::image type="content" source="media/git-merge-conflict-gold-bar.png" alt-text="Visual Studio'de 'Birleştirme çakışmalarla tamamlandı' Visual Studio ":::

Git **Değişiklikleri penceresinde** ayrıca *'* Birleştirme devam ediyor çakışmalar ile devam ediyor' iletisi görüntülenir ve altındaki ayrı bölümde birleştirlanmamış dosyalar görüntülenir.

:::image type="content" source="media/git-merge-progress-conflicts-message.png" alt-text="Visual Studio'de 'Birleştirme devam ediyor çakışmalarla birleştirildi' Visual Studio ":::

Ancak bu pencerelerden hiçbiri açık değilse ve bunun yerine birleştirme çakışmaları olan dosyaya gidersiniz, aşağıdaki metni aramanız zorunda olmayacaktır:

```bash
    <<<<<<< HEAD
    =======
    >>>>>>> main
```

Bunun Visual Studio üst kısmında açılan dosyanın çakışmaları olduğunu belirten altın bilgi çubuğu görüntülenir. Ardından bağlantıya tıklayarak Birleştirme **Düzenleyicisi'ni açabilirsiniz.**

:::image type="content" source="media/git-merge-conflict-gold-info-bar.png" alt-text="Dosyada 'Dosya birleştirme çakışmaları içeriyor' iletisi Visual Studio ":::

### <a name="the-merge-editor-in-visual-studio-2019"></a>Visual Studio 2019'da Birleştirme Düzenleyicisi

Visual Studio'daki Birleştirme Düzenleyicisi gelen değişiklikleri, geçerli değişikliklerinizi ve birleştirmenin sonucu görüntüleyen üç yoldan bir birleştirme aracıdır. Dosyada çakışmalar ve otomatik olarak  birleştirilen farklar arasında gezinmek için Birleştirme Düzenleyicisi'nin en üst düzeyindeki araç çubuğunu kullanabilirsiniz.

:::image type="content" source="media/git-merge-editor.png" alt-text="Visual Studio'da Birleştirme Düzenleyicisi ":::

Ayrıca, farklılıkları göstermek/gizlemek, sözcük farklarını göstermek/gizlemek ve düzeni özelleştirmek için de iki durumlu düğmeyi kullanabilirsiniz. Her iki tarafta da tüm değişiklikleri bir taraftan veya diğer taraftan almak için kullanabileceğiniz onay kutuları vardır. Ancak tek tek değişiklikleri yapmak için, her iki tarafta da çakışan satırların sol tarafındaki onay kutularına tık edebilirsiniz. Son olarak, çakışmaları çözmeyi bitirerek Birleştirme **Düzenleyicisi'nde** Birleştirmeyi Kabul Et düğmesini seçin. Daha sonra bir kayıt iletisi yazın ve çözümü tamamlamak için değişiklikleri işleyin.

## <a name="personalize-your-git-settings-in-visual-studio-2019"></a>Visual Studio 2019 ' de Git ayarlarınızı kişiselleştirin

git ayarlarınızı bir depo düzeyinde ve genel düzeyde kişiselleştirmek ve özelleştirmek için, menü çubuğunda **git**  >  **Ayarlar** veya menü çubuğundaki **araçlar**  >  **seçenekler**  >  **kaynak denetimi** ' ne gidin. Sonra istediğiniz [seçenekleri](git-settings.md) belirleyin.

:::image type="content" source="media/git-options-settings.png" alt-text="Visual Studio ıde 'de kişiselleştirme ve özelleştirme ayarlarını seçebileceğiniz seçenekler iletişim kutusu.":::

## <a name="how-to-use-the-full-team-explorer-experience-in-visual-studio-2019"></a>Visual Studio 2019 ' de tam Takım Gezgini deneyimini kullanma

yeni Git deneyimi, [sürüm 16,8](/visualstudio/releases/2019/release-notes/) ' den sonraki Visual Studio 2019 ' de varsayılan sürüm denetim sistemidir. Ancak, devre dışı bırakmak istiyorsanız, kullanabilirsiniz. **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **Önizleme özellikleri** ' ne gidin ve ardından **Yeni git Kullanıcı deneyimi** onay kutusunu açıp git için Takım Gezgini geri dönebilirsiniz.

:::image type="content" source="media/git-opt-new-user-experience.png" alt-text="Visual Studio Seçenekler iletişim kutusunun Önizleme özellikleri bölümü ":::

## <a name="whats-next"></a>Sırada ne var?

Visual Studio 2019 kullanıyorsanız, ancak sonraki sürümümüzde Git deneyimine yönelik yeni güncelleştirmeleri kullanıma almak isterseniz, [Visual Studio 2022 ' deki](../ide/whats-new-visual-studio-2022.md) yenilikler sayfasındaki & yükleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- Microsoft Learn üzerinde [Visual Studio 2019 öğreticisindeki Git ve GitHub Başlarken](/learn/modules/visual-studio-github-push/)
- [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)
- [Visual Studio 2019 sürüm notları](/visualstudio/releases/2019/release-notes)

::: moniker-end
