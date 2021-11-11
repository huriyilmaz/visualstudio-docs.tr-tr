---
title: Visual Studio git deneyimi
titleSuffix: ''
description: Visual Studio yeni tümleşik Git deneyiminin daha üretken olmanıza nasıl yardımcı olabileceğini öğrenin.
ms.date: 11/10/2021
ms.topic: overview
author: Taysser-Gherfal
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: c5427de953c424fb3b1b2ab8b14a8da84f0e5381
ms.sourcegitcommit: dc12d3d0ca2ec3601cb9de7c22e61ecf22c7c514
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2021
ms.locfileid: "132264121"
---
# <a name="git-experience-in-visual-studio"></a>Git deneyimi Visual Studio

::: moniker range=">=vs-2022"

Git, Visual Studio varsayılan sürüm denetimi deneyimidir. Özellik kümesini oluşturmaya devam ediyoruz ve geri bildirimlerinize göre bunu yineliyoruz. son kullanılan bir özellik güncelleştirmesi hakkında daha fazla bilgi için, geri bildiriminizi sizinle paylaşabileceğiniz bir anketin bağlantısı ile birlikte [Visual Studio](https://devblogs.microsoft.com/visualstudio/multi-repo-support-in-visual-studio/) blog gönderisine bakın.

::: moniker-end

::: moniker range="<=vs-2019"

Git artık Visual Studio 2019 ' de varsayılan sürüm denetimi deneyimidir. [Sürüm 16,6](/visualstudio/releases/2019/release-notes-v16.6)' den itibaren, özellik kümesini oluşturmaya ve geri bildiriminiz doğrultusunda bu uygulamayı yineleme konusunda çalıştık. [Sürüm 16,8](/visualstudio/releases/2019/release-notes-v16.8)' de, herkes için varsayılan sürüm denetimi deneyimi haline gelir.

> [!NOTE]
> [Visual Studio 2022](/visualstudio/releases/2022/release-notes-preview)' deki Git özelliğini oluşturmaya ve denemeye devam ediyoruz. yeni bir özellik güncelleştirmesi hakkında daha fazla bilgi edinmek için [Visual Studio](https://devblogs.microsoft.com/visualstudio/multi-repo-support-in-visual-studio/) blog gönderisine bakın.

::: moniker-end

## <a name="learn-more-about-git"></a>Git hakkında daha fazla bilgi

Git, en yaygın olarak kullanılan modern sürüm denetim sistemidir. bu nedenle, profesyonel bir geliştirici olun veya nasıl kod kullanacağınızı öğreniyor olun, git size çok faydalı olabilir. Git 'i yeni kullanıyorsanız, [https://git-scm.com/](https://git-scm.com/) Web sitesi başlamak için iyi bir yerdir. Burada, en çok sayfaları, popüler bir çevrimiçi kitabı ve git temel videoları hakkında bilgi edinebilirsiniz.

## <a name="how-to-use-git-in-visual-studio"></a>Visual Studio 'da git 'i kullanma

::: moniker range="<=vs-2019"

Visual Studio yeni Git deneyiminin nasıl kullanılacağı konusunda size kılavuzluk edeceğiz, ancak ilk olarak hızlı bir tura katılmak istiyorsanız aşağıdaki videoya göz atın: <br><br>*Video uzunluğu: 5,27 dakika*

> [!VIDEO https://www.youtube.com/embed/UHrAg3iKoe0]

::: moniker-end

daha üretken olmak için Visual Studio Git kullanmaya başlamanın üç yolu vardır:

- [Yeni bir git deposu oluşturun](#create-a-new-git-repository). Kodunuz git ile ilişkili değilse, yeni bir git deposu oluşturabilirsiniz.
- [Var olan bir Git deposunu kopyalayın](#clone-an-existing-git-repository). Üzerinde çalışmak istediğiniz kod makinenizde yoksa, var olan uzak depoları kopyalayabilirsiniz.
- [Var olan bir Git deposunu açın](#open-an-existing-local-repository). kodunuz zaten makinenizde ise, **dosya**  >  **aç**  >  **Project/solution** (veya **Folder**) kullanarak açabilir ve Visual Studio başlatılmış bir Git deposu olup olmadığını otomatik olarak algılar.

::: moniker range="<=vs-2019"

> [!NOTE]
> Visual Studio 2019 [sürüm 16,8](/visualstudio/releases/2019/release-notes-v16.8)' den başlayarak, tam olarak tümleşik bir GitHub hesabı deneyimi ekledik. artık anahtarınıza hem GitHub hem de GitHub Enterprise hesapları ekleyebilirsiniz. Microsoft hesapları ile yaptığınız gibi bunları ekleyebilir ve kullanabilirsiniz. bu, GitHub kaynaklarınıza Visual Studio bir zaman daha kolay erişim sağlayabilmeniz anlamına gelir. daha fazla bilgi için Visual Studio sayfasında [GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md) bölümüne bakın.

::: moniker-end

::: moniker range="vs-2022"

> [!NOTE]
> Visual Studio, tam olarak tümleşik bir GitHub hesabı deneyimi içerir. anahtarınıza hem GitHub hem de GitHub Enterprise hesabı ekleyelim, ancak Microsoft hesaplarıyla yaptığınız gibi bunlardan de yararlanabilirsiniz. daha fazla bilgi için Visual Studio sayfasında [GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md) bölümüne bakın.

::: moniker-end

## <a name="create-a-new-git-repository"></a>Yeni bir git deposu oluşturun

::: moniker range="vs-2022"

Kodunuz git ile ilişkili değilse, yeni bir git deposu oluşturarak başlayabilirsiniz. tüm ayrıntılar için [Visual Studio depoyu oluşturma](git-create-repository.md) sayfasına bakın.

::: moniker-end

::: moniker range="<=vs-2019"

Kodunuz git ile ilişkili değilse, yeni bir git deposu oluşturarak başlayabilirsiniz. Bunu yapmak için, menü çubuğundan **Git**  >  **deposu oluştur** ' u seçin. Ardından, **Git deposu oluştur** iletişim kutusunda bilgilerinizi girin.

:::image type="content" source="media/git-create-repository.png" alt-text="Visual Studio git deposu oluştur iletişim kutusu.":::

**Git deposu oluştur** iletişim kutusu, yeni deponuzu GitHub gönderimi kolaylaştırır. Varsayılan olarak, yeni deponuz özeldir ve bu, kendisine erişebilen tek bir tane olduğu anlamına gelir. kutunun işaretini kaldırırsanız, deponuz herkese açık olacaktır, bu da GitHub herkesin görüntüleyebileceği anlamına gelir.

> [!TIP]
> deponuzun ortak veya özel olup olmadığı, bir ekip ile çalışmasanız bile, kodunuzun bir uzak yedeğinin GitHub güvenli bir şekilde depolanmasını sağlamak en iyisidir. Bu Ayrıca, kullandığınız bilgisayar ne olduğuna bakılmaksızın kodunuzun sizin için kullanılabilir olmasını sağlar.

**Yalnızca yerel** ' i kullanarak yerel bir git deposu oluşturmayı tercih edebilirsiniz. ya da, **mevcut uzak** seçeneği kullanarak yerel projenizi Azure DevOps veya başka bir Git sağlayıcısı üzerinde var olan bir boş uzak depoya bağlayabilirsiniz.

::: moniker-end

## <a name="clone-an-existing-git-repository"></a>Var olan bir Git deposunu Kopyala

::: moniker range="vs-2022"

Visual Studio, basit bir kopyalama deneyimi içerir. adım adım kılavuz için, [Visual Studio bir depoyu kopyalama](git-clone-repository.md) sayfasına bakın.

::: moniker-end

::: moniker range="<=vs-2019"

Visual Studio, basit bir kopyalama deneyimi içerir. kopyalamak istediğiniz deponun url 'sini biliyorsanız, **depo konumu** bölümüne url 'yi yapıştırabilir ve sonra Visual Studio kopyalamak istediğiniz disk konumunu seçebilirsiniz.

:::image type="content" source="media/git-clone-repository.png" alt-text="Visual Studio Git deposunu Kopyala iletişim kutusu.":::

depo URL 'sini bilmiyorsanız Visual Studio mevcut GitHub veya Azure DevOps deponuza gidip klonlamanızı kolaylaştırır.

::: moniker-end

## <a name="open-an-existing-local-repository"></a>Mevcut bir yerel depoyu aç

bir depoyu kopyaladıktan veya oluşturduktan sonra, Visual Studio git deposunu algılar ve git menüsündeki **yerel depolar** listenize ekler.

::: moniker range="<=vs-2019"

Buradan git depolarınız arasında hızlı bir şekilde erişebilir ve geçiş yapabilirsiniz.

:::image type="content" source="media/git-local-repositories.png" alt-text="Visual Studio Git menüsünde yerel depolar seçeneği ":::

::: moniker-end

## <a name="view-files-in-solution-explorer"></a>Çözüm Gezgini dosyaları görüntüleme

bir depoyu klonlarken veya yerel bir depoyu açtığınızda, daha önce açık olan tüm çözümleri ve projeleri kaydederek ve kapatarak bu Git bağlamına geçiş Visual Studio. Çözüm Gezgini git deposunun kökündeki klasörü yükler ve tüm görüntülenebilir dosyalar için dizin ağacını tarar. Bunlar, CMakeLists.txt veya. sln dosya uzantısına sahip olanlar gibi dosyaları içerir.

::: moniker range="vs-2022"

Daha fazla bilgi için [bir depoyu bir depodan açma](../get-started/tutorial-open-project-from-repo.md?view=vs-2022&preserve-view=true) öğreticisindeki açık olan [Çözüm Gezgini dosyaları görüntüleme](../get-started/tutorial-open-project-from-repo.md#view-files-in-solution-explorer) bölümüne bakın.

::: moniker-end

::: moniker range="<=vs-2019"

Visual Studio, Çözüm Gezgini ' de yüklediğiniz dosyayı temel alarak görünümünü ayarlar:

- Tek bir. sln dosyası içeren bir depoyu klonladığınızda, Çözüm Gezgini bu çözümü doğrudan sizin için yükler.
- Çözüm Gezgini deponuzdaki herhangi bir. sln dosyasını algılamazsa, varsayılan olarak klasör görünümünü yükler.
- Deponuzda birden fazla. sln dosyası varsa Çözüm Gezgini, aralarından seçim yapabileceğiniz kullanılabilir görünümlerin listesini gösterir.

Çözüm Gezgini araç çubuğundaki **görünümleri Değiştir** düğmesini kullanarak şu anda açık olan görünüm ve görünüm listesi arasında geçiş yapabilirsiniz.

:::image type="content" source="media/git-solution-explorer-views.png" alt-text="Visual Studio ' de görünümleri Değiştir düğmesi seçili Çözüm Gezgini.":::

::: moniker-end

## <a name="git-changes-window"></a>Git değişiklikleri penceresi

Git, çalışmanız sırasında deponuzdaki dosya değişikliklerini izler ve deponuzdaki dosyaları üç kategoriye ayırır. Bu değişiklikler, komut satırına komutu girerken göreceğiniz şekilde eşdeğerdir `git status` :

- **Değiştirilmemiş dosyalar**: Bu dosyalar son işlemenizden bu yana değişmemiştir.
- **Değiştirilen dosyalar**: Bu dosyalar son işlemenizden sonra değişir, ancak henüz bir sonraki yürütmede hazırlanmadınız.
- **Hazırlanmış dosyalar**: Bu dosyalar bir sonraki işlemeye eklenecek değişiklikler olur.

işinizi yaparken Visual Studio **Git değişiklikleri** penceresinin **değişiklikler** bölümünde projenizdeki dosya değişikliklerinin izini devam eder.

::: moniker range="<=vs-2019"

:::image type="content" source="media/git-changes-window.png" alt-text="Git değişiklikleri penceresi Visual Studio.":::

::: moniker-end

Değişiklikleri aşamalandırmaya hazırsanız, hazırlamak istediğiniz her bir **+** dosyanın (artı) düğmesine tıklayın veya bir dosyaya sağ tıklayıp **aşama**' ü seçin. Ayrıca, **+** **değişiklikler** bölümünün en üstünde bulunan tümü (artı) düğmesini kullanarak, değiştirdiğiniz tüm dosyaları tek tıklamayla de taşıyabilirsiniz.

bir değişiklik gerçekleştirdiğinizde Visual Studio **hazırlanmış bir değişiklikler** bölümü oluşturulur. Yalnızca **hazırlanan değişiklikler** bölümündeki değişiklikler, **hazırlanan Yürüt**' i seçerek yapabileceğiniz bir sonraki işlemeye eklenir. Bu eylem için eşdeğer komut `git commit -m "Your commit message"` . Değişiklikler, **–** (eksi) düğmesine tıklanarak de hazırlanarak çalıştırılabilir. Bu eylem için eşdeğer komut, `git reset <file_path>` tek bir dosyayı aşamalandırmaktır veya `git reset <directory_path>` bir dizindeki tüm dosyaların aşamasını kaldırır.

Ayrıca, hazırlama alanını atlayarak, değiştirilen dosyaları aşamalandırmasını da tercih edebilirsiniz. bu durumda Visual Studio, yaptığınız değişiklikleri doğrudan yürütmelerine gerek kalmadan uygulamanıza izin verir. Yalnızca tamamlama iletinizi girin ve ardından **Tümünü Kaydet**' i seçin. Bu eylem için eşdeğer komut `git commit -a` .

Visual Studio ayrıca, **tümünü kaydet ve tümünü gönder** ve **tümünü kaydet ve tümünü yürüt** kısayollarını kullanarak tek bir tıklama ile kaydetmeyi ve eşitlemeyi kolaylaştırır. **Değişiklikler** ve **hazırlanan değişiklikler** bölümlerindeki herhangi bir dosyayı çift tıklattığınızda, dosyanın değiştirilmemiş sürümüyle bir satır satır karşılaştırması görebilirsiniz.

::: moniker range="<=vs-2019"

:::image type="content" source="media/git-file-version-compare.png" alt-text="Visual Studio dosya sürümlerinin satır içindeki karşılaştırması ":::

::: moniker-end

::: moniker range="vs-2022"

> [!TIP]
> Azure DevOps deposuna bağlıysanız "#" karakterini kullanarak bir Azure DevOps iş öğesini bir işlemeye ilişkilendirebilirsiniz.

::: moniker-end

::: moniker range="<=vs-2019"

> [!TIP]
> Azure DevOps deposuna bağlıysanız "#" karakterini kullanarak bir Azure DevOps iş öğesini bir işlemeye ilişkilendirebilirsiniz. Azure DevOps deponuzu bağlantı **Takım Gezgini**  >  **yönet** aracılığıyla bağlayabilirsiniz.

::: moniker-end

### <a name="select-an-existing-branch"></a>Mevcut bir dalı seçin

Visual Studio **Git değişiklikleri** penceresinin en üstündeki seçicideki geçerli dalı görüntüler.

::: moniker range="<=vs-2019"

:::image type="content" source="media/git-changes-current-branch-selector.png" alt-text="Visual Studio içindeki Git değişiklikleri seçicinin en üstünde yer alan seçiciyi kullanarak görüntüleyebileceğiniz geçerli dallar ":::

::: moniker-end

geçerli dal, Visual Studio ıde 'nin sağ alt köşesindeki durum çubuğunda de mevcuttur.

::: moniker range="<=vs-2019"

:::image type="content" source="media/git-changes-current-branch-status-bar.png" alt-text="Visual Studio ıde 'de sağ alt köşedeki durum çubuğunu kullanarak görüntüleyebileceğiniz geçerli dallar":::

::: moniker-end

Her iki konumdan de mevcut dallar arasında geçiş yapabilirsiniz.

### <a name="create-a-new-branch"></a>Yeni dal oluştur

Ayrıca yeni bir dal da oluşturabilirsiniz. Bu eylemin eşdeğer komutu şu `git checkout -b <branchname>` şekildedir: .

Yeni bir dal oluşturmak, dal adını girmek ve mevcut bir daldan değiştirmek kadar kolaydır.

::: moniker range="<=vs-2019"

:::image type="content" source="media/git-changes-create-new-branch.png" alt-text="Yeni Dal Oluştur iletişim kutusu Visual Studio ":::

::: moniker-end

Temel olarak mevcut bir yerel veya uzak dalı seçebilirsiniz. Teslim **alma dalı** onay kutusu sizi otomatik olarak yeni oluşturulan dala geçiştir. Bu eylemin eşdeğer komutu şu `git checkout -b <new-branch><existing-branch>` şekildedir: .

## <a name="git-repository-window"></a>Git Deposu penceresi

Visual Studio tüm dallar, uzak depolar ve işleme histories dahil olmak üzere depo tüm ayrıntıların birleştirilmiş bir görünümü olan yeni bir **Git** Deposu penceresi vardır. Bu pencereye doğrudan menü **çubuğundaki Git** veya **Görünüm'den** veya durum çubuğundan erişebilirsiniz.

### <a name="manage-branches"></a>Dalları yönetme

**Git** **menüsünden Dalları** Yönet'i seçerek Git Deposu penceresinde dallar ağaç **görünümünü** görebilirsiniz. Sol bölmede sağ tıklama bağlam menüsünü kullanarak dalları tamamlar, yeni dallar oluşturabilir, birleştirebilirsiniz, yeniden temeli oluşturabilir, tek tek seçebilirsiniz ve daha fazlasını yapabilirsiniz. Dala tıklarken sağ bölmede işleme geçmişinin önizlemesini görebilirsiniz.

### <a name="incoming-and-outgoing-commits"></a>Gelen ve giden işlemeler

Bir dalı getirebilirsiniz. **Git Değişiklikleri** penceresinde, dal açılan listesinde uzak daldan gelen işlanmamış işlemelerin sayısını gösteren bir gösterge vardır. Bu gösterge ayrıca size, işlenmiş olmayan yerel işlemelerin sayısını gösterir.

::: moniker range="<=vs-2019"

:::image type="content" source="media/git-repo-drop-down-indicator.png" alt-text="Uygulamanın içinde gösterge açılan kullanıcı arabirimi öğesini gösteren Git Değişiklikleri Visual Studio ":::

::: moniker-end

Gösterge ayrıca sizi Git Deposu penceresinde bu dalın işleme geçmişine götüren bir **bağlantı olarak da** işlev gösterir. Geçmişin en üstünde artık bu gelen ve giden işlemelerin ayrıntıları görüntülenir. Buradan işlemeleri çekme veya itme kararlarını da vesersiniz.

::: moniker range="<=vs-2019"

:::image type="content" source="media/git-branch-commit-history.png" alt-text="Git Deposundaki bir dalın işleme geçmişini gösteren git deposu Visual Studio ":::

::: moniker-end

#### <a name="commit-details"></a>Commit Details

Bir Commit 'e çift **Visual Studio,** ayrıntılarını ayrı bir araç penceresinde açar. Buradan işlemeyi geri döndürebilirsiniz, işlemeyi sıfırlayabilirsiniz, işleme iletiyi düzeltebilirsiniz veya işlemede bir etiket oluşturabilirsiniz. Yürütmede değiştirilen bir dosyaya tıklarsanız, Visual Studio ve üst  öğesinin yan yana Fark görünümünü açar.

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

:::image type="content" source="media/git-merge-conflict-gold-bar.png" alt-text="'Birleştirme çakışmalarla tamamlandı' iletisi Visual Studio ":::

Git **Değişiklikleri penceresinde** ayrıca *'* Birleştirme devam ediyor çakışmalar ile devam ediyor' iletisi görüntülenir ve altındaki ayrı bölümde birleştirlanmamış dosyalar görüntülenir.

:::image type="content" source="media/git-merge-progress-conflicts-message.png" alt-text="Visual Studio'de 'Birleştirme devam ediyor çakışmalarla birleştirildi' Visual Studio ":::

Ancak bu pencerelerden hiçbiri açık değilse ve bunun yerine birleştirme çakışmaları olan dosyaya gidersiniz, aşağıdaki metni aramanız zorunda olmayacaktır:

```bash
    <<<<<<< HEAD
    =======
    >>>>>>> main
```

Bunun Visual Studio üst kısmında açılan dosyanın çakışmaları olduğunu belirten altın bilgi çubuğu görüntülenir. Ardından bağlantıya tıklayarak Birleştirme **Düzenleyicisi'ni açabilirsiniz.**

:::image type="content" source="media/git-merge-conflict-gold-info-bar.png" alt-text="Dosyada 'Dosya birleştirme çakışmaları içeriyor' iletisi ekran Visual Studio ":::

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

Yeni Git deneyimi artık varsayılan olarak Visual Studio 2019 sürüm [16.8'den](/visualstudio/releases/2019/release-notes/)başlayarak açıkken, deneyimi geliştirmek için yeni özellikler eklemeye devam edeceğiz. Bir Önizleme yayında Git deneyimine yapılan yeni güncelleştirmeleri kontrol etmek için, Visual Studio [2022 Preview sayfasından](https://aka.ms/vspreview/) indirip yükleyebilirsiniz.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio'da Git deneyimini geliştirmek için yeni özellikler eklemeye devam Visual Studio. Son özellik güncelleştirmesi hakkında daha fazla bilgi ve geri bildiriminizi paylaşabilirsiniz anket bağlantısı için bkz. Çok Visual Studio [blog](https://devblogs.microsoft.com/visualstudio/multi-repo-support-in-visual-studio/) gönderisi.

::: moniker-end

> [!IMPORTANT]
> Bize bir öneriniz varsa lütfen bize haber ver! Geliştirici portalı üzerinden tasarım kararları alma fırsatınız [**Community.**](https://aka.ms/vs-suggest)

## <a name="see-also"></a>Ayrıca bkz.

::: moniker range="<=vs-2019"

- [Başlarken 2019 GitHub'Visual Studio Git](/learn/modules/visual-studio-github-push/) ve Microsoft Learn
- [YouTube'daki Visual Studio Git](https://www.youtube.com/watch?v=GCZ9x3yqkyc) ile çalışmaya başlama
- Visual Studio blog [gönderisinde Git Deneyiminin Yayımlanma](https://devblogs.microsoft.com/visualstudio/announcing-the-release-of-the-git-experience-in-visual-studio/) Tarihi
- [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)
- [Visual Studio 2019 sürüm notları](/visualstudio/releases/2019/release-notes)
- [Visual Studio 2022 sürüm notları](/visualstudio/releases/2022/release-notes)

::: moniker-end

::: moniker range="vs-2022"

- [Visual Studio & GitHub: Birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)
- [Visual Studio 2022 sürüm notları](/visualstudio/releases/2022/release-notes)

::: moniker-end
