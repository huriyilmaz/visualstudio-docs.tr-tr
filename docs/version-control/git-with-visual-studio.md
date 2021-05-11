---
title: Visual Studio 2019'da Git deneyimi
titleSuffix: ''
description: Visual Studio 2019'daki yeni tümleşik Git deneyiminin daha üretken çalışmanıza nasıl yardımcı olacağını öğrenin.
ms.date: 04/01/2021
ms.topic: overview
ms.author: tglee
author: TerryGLee
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.manager: jmartens
ms.openlocfilehash: 7ca09edada7715b9e7be754dbec22e1654288df8
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729318"
---
# <a name="git-experience-in-visual-studio"></a>Visual Studio'de Git deneyimi

Git artık Visual Studio 2019'da varsayılan sürüm denetimi deneyimidir. Sürüm [16.6'dan](/visualstudio/releases/2019/release-notes-v16.6)bu yana, geri bildiriminize göre özellik kümesi üzerinde çalışma ve bu küme üzerinde bir kez daha çalışmamız oldu. Yeni Git deneyimi, sürüm [16.8](/visualstudio/releases/2019/release-notes/)sürümüne sahip herkes için varsayılan olarak açıktır.

> [!TIP]
> Git en yaygın olarak kullanılan modern sürüm denetimi sistemidir, bu nedenle profesyonel bir geliştirici olun veya kod kodla ilgili bilgi edinseniz Git sizin için çok yararlı olabilir. Git'i yeni başladıysanız, https://git-scm.com/ web sitesi başlamak için iyi bir yerdir. Burada bilgi sayfaları, popüler bir çevrimiçi kitap ve Git Temel Bilgileri videoları bulabilirsiniz.

## <a name="how-to-use-git-in-visual-studio"></a>Git'i Visual Studio

Visual Studio 2019'da yeni Git deneyimini nasıl kullanabileceğiniz adım adım açıklanacak ancak önce hızlı bir tura olmak için aşağıdaki videoya göz atabilirsiniz: <br><br>*Video uzunluğu: 5,27 dakika*

> [!VIDEO https://www.youtube.com/embed/UHrAg3iKoe0]

Daha üretken olmak için Git'i Visual Studio üç yol vardır:

- [Var olan bir Git deposunu açın.](#open-an-existing-local-repository) Kodunuz makinede zaten varsa, Dosya Aç   >    >  **Proje/Çözüm** (veya Klasör) kullanarak açabilir ve Visual Studio başlatılmış bir Git deposu olup Visual Studio otomatik olarak algılar.
- [Yeni bir Git deposu oluşturun.](#create-a-new-git-repository) Kodunuz Git ile ilişkili değilse yeni bir Git deposu oluşturabilirsiniz.
- [Var olan bir Git deposunu klonlama.](#clone-an-existing-git-repository) Üzerinde çalışmak için kullanmak üzere kod makineniz üzerinde yoksa, mevcut uzak depoları kopyaabilirsiniz.

> [!NOTE]
> [16.8](/visualstudio/releases/2019/release-notes/)sürümünden itibaren, Visual Studio 2019 tamamen tümleşik bir GitHub hesabı deneyimi içerir. Artık anahtarınıza GitHub ve GitHub kurumsal hesaplarını ekleyebilirsiniz. Microsoft hesapları ile yaptığınız gibi bunları ekleyebilir ve bu kişilere de atayabilirsiniz. Bu, GitHub kaynaklarınıza Visual Studio üzerinden erişmenin daha kolay bir zaman olacağı anlamına gelir. Daha fazla bilgi için bkz. [Visual Studio 'Da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md) sayfası.

## <a name="create-a-new-git-repository"></a>Yeni bir git deposu oluşturun

Kodunuz git ile ilişkili değilse, yeni bir git deposu oluşturarak başlayabilirsiniz. Bunu yapmak için, menü çubuğundan **Git**  >  **deposu oluştur** ' u seçin. Ardından, **Git deposu oluştur** iletişim kutusunda bilgilerinizi girin.

:::image type="content" source="media/git-create-repository.png" alt-text="Visual Studio 'da git deposu oluşturma iletişim kutusu.":::

**Git deposu oluştur** iletişim kutusu, yeni deponuzu GitHub 'a itmenizi kolaylaştırır. Varsayılan olarak, yeni deponuz özeldir ve bu, kendisine erişebilen tek bir tane olduğu anlamına gelir. Kutunun işaretini kaldırırsanız, deponuz herkese açık hale gelir, yani GitHub 'daki herkes tarafından görüntülenebilir.

> [!TIP]
> Deponuzun ortak veya özel olup olmadığı, bir ekip ile çalışmasanız bile, kodunuzun bir uzak yedeğinin GitHub 'da güvenli bir şekilde depolanmasını sağlamak en iyisidir. Bu Ayrıca, kullandığınız bilgisayar ne olduğuna bakılmaksızın kodunuzun sizin için kullanılabilir olmasını sağlar.

**Yalnızca yerel** ' i kullanarak yerel bir git deposu oluşturmayı tercih edebilirsiniz. Ya da **mevcut uzak** seçeneği kullanarak yerel projenizi Azure DevOps veya başka bir git sağlayıcısı üzerinde var olan bir boş uzak depoya bağlayabilirsiniz.

## <a name="clone-an-existing-git-repository"></a>Var olan bir Git deposunu Kopyala

Visual Studio basit bir kopyalama deneyimi içerir. Kopyalamak istediğiniz deponun URL 'sini biliyorsanız, **Depo konumu** bölümüne URL 'yi yapıştırabilir ve sonra Visual Studio 'nun klonlanmasını istediğiniz disk konumunu seçebilirsiniz.

:::image type="content" source="media/git-clone-repository.png" alt-text="Visual Studio 'da Git deposunu Kopyala iletişim kutusu.":::

Depo URL 'sini bilmiyorsanız, Visual Studio mevcut GitHub veya Azure DevOps deponuzu ve daha sonra klonlamanızı kolaylaştırır.

### <a name="open-an-existing-local-repository"></a>Mevcut bir yerel depoyu açma

Depoyu klonladikten veya oluşturduktan sonra Visual Studio Git deposunu algılar ve Git menüsündeki  Yerel Depolar listenize ekler. Buradan Git depolarına hızlıca erişin ve bu depolar arasında geçişe geçin.

:::image type="content" source="media/git-local-repositories.png" alt-text="Visual Studio'daki Git menüsündeki Yerel Depolar Visual Studio ":::

## <a name="view-files-in-solution-explorer"></a>Dosyaları Çözüm Gezgini

Bir depoyu kopyaladığınız veya yerel bir depoyu Visual Studio, önceden açık olan çözümleri ve projeleri kaydederek ve kapatarak sizi bu Git bağlamına açar. Çözüm Gezgini Git deposunun köküne klasörü yükler ve tüm Görünüm dosyaları için dizin ağacını tarar. Bunlar, dosya adı CMakeLists.txt .sln dosya uzantısına sahip dosyaları içerir.

Visual Studio, görünümde hangi Görünüm dosyasını yükley istediğinize göre Çözüm Gezgini:

- Tek bir .sln dosyası içeren bir depoyu kopyalarsanız, Çözüm Gezgini doğrudan sizin için yükler.
- Depo Çözüm Gezgini herhangi bir .sln dosyası algılamazsa, varsayılan olarak Klasör Görünümü'dür.
- Depoda birden fazla .sln dosyası varsa, Çözüm Gezgini seçebilirsiniz kullanılabilir Görünümler listesini gösterir.

Açık olan Görünüm ile Görünümler listesi arasında geçiş yapmak için araç çubuğundaki Görünümleri **Değiştir** düğmesini Çözüm Gezgini ekleyebilirsiniz.

:::image type="content" source="media/git-solution-explorer-views.png" alt-text="Çözüm Gezgini'da Görünümleri Değiştir düğmesi seçili Visual Studio.":::

## <a name="git-changes-window"></a>Git Değişiklikleri penceresi

Git, siz çalışırken depoda yapılan dosya değişikliklerini izler ve depoda yer alan dosyaları üç kategoriye ayırıyor. Bu değişiklikler, komut satırına komutu girerken `git status` göreceğiniz değişikliklerle eşdeğerdir:

- **Değiştirilmemiş dosyalar:** Bu dosyalar son işlemeden bu yana değişmemiştir.
- **Değiştirilen dosyalar:** Bu dosyalarda son işlemeden bu yana değişiklikler vardır, ancak bunları henüz sonraki işleme için hazırlanmadınız.
- **Aşamalı dosyalar:** Bu dosyalar, sonraki işlemeye eklenecek değişikliklere sahip olur.

İşinizi yaparken, Visual Studio **Git değişiklikleri** penceresinin **değişiklikler** bölümünde dosya değişikliklerini projenizde izler.

:::image type="content" source="media/git-changes-window.png" alt-text="Visual Studio 'daki git değişiklikleri penceresi.":::

Değişiklikleri aşamalandırmaya hazırsanız, hazırlamak istediğiniz her bir **+** dosyanın (artı) düğmesine tıklayın veya bir dosyaya sağ tıklayıp **aşama**' ü seçin. Ayrıca, **+** **değişiklikler** bölümünün en üstünde bulunan tümü (artı) düğmesini kullanarak, değiştirdiğiniz tüm dosyaları tek tıklamayla de taşıyabilirsiniz.

Bir değişiklik gerçekleştirdiğinizde, Visual Studio **hazırlanmış bir değişiklikler** bölümü oluşturur. Yalnızca **hazırlanan değişiklikler** bölümündeki değişiklikler, **hazırlanan Yürüt**' i seçerek yapabileceğiniz bir sonraki işlemeye eklenir. Bu eylem için eşdeğer komut `git commit -m "Your commit message"` . Değişiklikler, **–** (eksi) düğmesine tıklanarak de hazırlanarak çalıştırılabilir. Bu eylem için eşdeğer komut, `git reset <file_path>` tek bir dosyayı aşamalandırmaktır veya `git reset <directory_path>` bir dizindeki tüm dosyaların aşamasını kaldırır.

Ayrıca, hazırlama alanını atlayarak, değiştirilen dosyaları aşamalandırmasını da tercih edebilirsiniz. Bu durumda, Visual Studio, yaptığınız değişiklikleri doğrudan yürütmelerine gerek kalmadan uygulamanıza olanak tanır. Yalnızca tamamlama iletinizi girin ve ardından **Tümünü Kaydet**' i seçin. Bu eylem için eşdeğer komut `git commit -a` .

Visual Studio Ayrıca, **Tümünü Kaydet ve** **Tümünü Yürüt ve Tümünü Kaydet ve Tümünü Yürüt** kısayollarını kullanarak tek bir tıklama ile kaydetmeyi ve eşitlemeyi kolaylaştırır. **Değişiklikler** ve **hazırlanan değişiklikler** bölümlerindeki herhangi bir dosyayı çift tıklattığınızda, dosyanın değiştirilmemiş sürümüyle bir satır satır karşılaştırması görebilirsiniz.

:::image type="content" source="media/git-file-version-compare.png" alt-text="Visual Studio 'da dosya sürümlerinin satır içindeki karşılaştırması ":::

> [!TIP]
> Azure DevOps deposuna bağlıysanız, "#" karakterini kullanarak bir Azure DevOps iş öğesini bir işlemeye ilişkilendirebilirsiniz. **Takım Gezgini**  >  **bağlantıları yönetmek** için Azure DevOps deponuzu bağlayabilirsiniz.

### <a name="select-an-existing-branch"></a>Mevcut bir dalı seçin

Visual Studio Git Değişiklikleri penceresinin üst kısmında seçicide geçerli **dalı** görüntüler.

:::image type="content" source="media/git-changes-current-branch-selector.png" alt-text="Uygulamanın Git Değişiklikleri seçicisi üst kısmında yer alan seçiciyi kullanarak görüntü Visual Studio ":::

Geçerli dal, IDE'nin sağ alt köşesindeki durum çubuğunda Visual Studio kullanılabilir.

:::image type="content" source="media/git-changes-current-branch-status-bar.png" alt-text="IDE'nin sağ alt köşesindeki durum çubuğunu kullanarak görüntüleyebilirsiniz geçerli dallar Visual Studio. ":::

Her iki konumdan da mevcut dallar arasında geçiş yapılabilir.

### <a name="create-a-new-branch"></a>Yeni dal oluşturma

Ayrıca yeni bir dal da oluşturabilirsiniz. Bu eylemin eşdeğer komutu şu `git checkout -b <branchname>` şekildedir: .

Yeni bir dal oluşturmak, dal adını girmek ve mevcut bir daldan değiştirmek kadar kolaydır.

:::image type="content" source="media/git-changes-create-new-branch.png" alt-text="Yeni Dal Oluştur iletişim kutusu Visual Studio ":::

Temel olarak mevcut bir yerel veya uzak dalı seçebilirsiniz. Teslim **alma dalı** onay kutusu sizi otomatik olarak yeni oluşturulan dala geçiştir. Bu eylemin eşdeğer komutu şu `git checkout -b <new-branch><existing-branch>` şekildedir: .

## <a name="git-repository-window"></a>Git Deposu penceresi

Visual Studio tüm dallar, uzak depolar ve işleme histories dahil olmak üzere depo tüm ayrıntıların birleştirilmiş bir görünümü olan yeni bir **Git** Deposu penceresi vardır. Bu pencereye doğrudan menü **çubuğundaki Git** veya **Görünüm'den** veya durum çubuğundan erişebilirsiniz.

### <a name="manage-branches"></a>Dalları yönetme

**Git** **menüsünden Dalları** Yönet'i seçerek Git Deposu penceresinde dallar ağaç **görünümünü** görebilirsiniz. Sol bölmede sağ tıklama bağlam menüsünü kullanarak dalları tamamlar, yeni dallar oluşturabilir, birleştirebilirsiniz, yeniden temeli oluşturabilir, tek tek seçebilirsiniz ve daha fazlasını yapabilirsiniz. Dala tıklarken sağ bölmede işleme geçmişinin önizlemesini görebilirsiniz.

### <a name="incoming-and-outgoing-commits"></a>Gelen ve giden işlemeler

Bir dalı getirirken, **Git değişiklikleri** penceresinde, uzak daldaki çekolmayan işlemeler sayısını görüntüleyen dal açılan penceresinin altında bir gösterge bulunur. Bu gösterge Ayrıca, gönderilen yerel işlemelerin sayısını gösterir.

:::image type="content" source="media/git-repo-drop-down-indicator.png" alt-text="Visual Studio 'da gösterge açılan Kullanıcı arabirimi öğesini gösteren git değişiklikleri penceresi ":::

Gösterge Ayrıca **Git deposu** penceresinde bu dalın tamamlama geçmişine gidebileceğiniz bir bağlantı olarak çalışır. Geçmiş en üst kısmında, bu gelen ve giden işlemelerin ayrıntıları görüntülenir. Buradan, yürütmeleri çekme veya gönderim de yapabilirsiniz.

:::image type="content" source="media/git-branch-commit-history.png" alt-text="Visual Studio 'da bir dalın tamamlama geçmişini gösteren git deposu penceresi ":::

#### <a name="commit-details"></a>Kayıt ayrıntıları

Bir **yürütmeyi** çift tıklattığınızda, Visual Studio ayrıntılarını ayrı bir araç penceresinde açar. Buradan işlemeyi geri alabilir, işlemeyi sıfırlayabilir, tamamlama iletisini değiştirebilir veya yürütmede bir etiket oluşturabilirsiniz. İşlemede değiştirilen bir dosyaya tıkladığınızda, Visual Studio, yürütmenin ve onun üst öğesinin yan yana **fark** görünümünü açar.

:::image type="content" source="media/git-branch-commit-details.png" alt-text="Visual Studio 'daki kayıt ayrıntıları iletişim kutusu ":::

## <a name="handle-merge-conflicts"></a>Birleştirme çakışmalarını işle

İki geliştirici bir dosyadaki aynı satırları değiştirmiyorsa ve git 'in doğru olduğunu otomatik olarak tanımadığı bir birleştirme sırasında çakışmalar meydana gelebilir. Git, birleştirme işlemini ve çakışan bir durumda olduğunu bildirir.

Visual Studio, birleştirme çakışmasını belirlemeyi ve çözümlemeyi kolaylaştırır. İlk olarak, **Git deposu** penceresinde pencerenin üst kısmında bir altın bilgi çubuğu görüntülenir.

:::image type="content" source="media/git-merge-conflict-gold-bar.png" alt-text="Visual Studio 'da ' Merge WITH Conflicts tamamlandı ' iletisi ":::

**Git değişiklikleri** penceresi ayrıca, bu dosyanın altındaki ayrı bölümünde birleştirilmemiş dosyalar içeren bir '*birleştirme, çakışmalar ile devam ediyor*' iletisiyle birlikte görüntülenir.

:::image type="content" source="media/git-merge-progress-conflicts-message.png" alt-text="Dosyada 'Çakışmalarla birleştirme devam ediyor' Visual Studio ":::

Ancak bu pencerelerden hiçbiri açık değilse ve bunun yerine birleştirme çakışmaları olan dosyaya gidersiniz, aşağıdaki metni aramanız zorunda olmayacaktır:

```bash
    <<<<<<< HEAD
    =======
    >>>>>>> main
```

Bunun Visual Studio sayfanın üst kısmında açılan dosyanın çakışmaları olduğunu belirten altın bilgi çubuğu görüntülenir. Ardından bağlantıya tıklayarak Birleştirme **Düzenleyicisi'ni açabilirsiniz.**

:::image type="content" source="media/git-merge-conflict-gold-info-bar.png" alt-text="Dosyada 'Dosya birleştirme çakışmaları içeriyor' iletisi Visual Studio ":::

### <a name="the-merge-editor"></a>Birleştirme Düzenleyicisi

Visual Studio'daki Birleştirme Düzenleyicisi gelen değişiklikleri, geçerli değişikliklerinizi ve birleştirmenin sonucu görüntüleyen üç yoldan bir birleştirme aracıdır. Dosyada çakışmalar ve otomatik olarak  birleştirilen farklar arasında gezinmek için Birleştirme Düzenleyicisi'nin en üst düzeyindeki araç çubuğunu kullanabilirsiniz.

:::image type="content" source="media/git-merge-editor.png" alt-text="Visual Studio'de Birleştirme Düzenleyicisi ":::

Ayrıca, farklılıkları göstermek/gizlemek, sözcük farklarını göstermek/gizlemek ve düzeni özelleştirmek için de iki durumlu düğmeyi kullanabilirsiniz. Her iki tarafta da tüm değişiklikleri bir taraftan veya diğer taraftan almak için kullanabileceğiniz onay kutuları vardır. Ancak tek tek değişiklikleri yapmak için, her iki tarafta da çakışan satırların sol tarafındaki onay kutularına tık edebilirsiniz. Son olarak, çakışmaları çözmeyi bitirerek Birleştirme **Düzenleyicisi'nde** Birleştirmeyi Kabul Et düğmesini seçin. Ardından bir işleme iletisi yazar ve çözümü tamamlamak için değişiklikleri işlersiniz.

## <a name="personalize-your-git-settings"></a>Git ayarlarınızı kişiselleştirme

Git ayarlarınızı hem depo düzeyinde hem de genel düzeyde kişiselleştirmek ve özelleştirmek için menü çubuğunda **Git** Ayarları'ya veya menü çubuğundaKi Araçlar Seçenekler Kaynak  >     >    >   Denetimi'ne gidin. Ardından istediğiniz seçenekleri belirleyin.

:::image type="content" source="media/git-options-settings.png" alt-text="IDE'de kişiselleştirme ve özelleştirme ayarlarını seçebilirsiniz Seçenekler Visual Studio kutusu ":::

## <a name="how-to-use-the-full-team-explorer-experience-in-visual-studio"></a>Visual Studio'de tam Takım Gezgini deneyimi Visual Studio

Yeni Git deneyimi, [16.8](/visualstudio/releases/2019/release-notes/) ve Visual Studio 2019'daki varsayılan sürüm denetimi sistemidir. Ancak, devre dışı bırakmak istiyorsanız, kullanabilirsiniz. **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **Önizleme özellikleri** ' ne gidin ve ardından **Yeni git Kullanıcı deneyimi** onay kutusunu açıp git için Takım Gezgini geri dönebilirsiniz.

:::image type="content" source="media/git-opt-new-user-experience.png" alt-text="Visual Studio 'daki Seçenekler iletişim kutusunun Önizleme özellikleri bölümü ":::

## <a name="whats-next"></a>Sırada ne var?

Yeni git deneyimi artık Visual Studio 2019 [sürüm 16,8](/visualstudio/releases/2019/release-notes/)' de varsayılan olarak açık olsa da, deneyimi iyileştirmek için yeni özellikler eklemeye devam ediyoruz. Bir önizleme sürümünde git deneyimine yönelik yeni güncelleştirmeleri kullanıma almak isterseniz, [Visual Studio önizleme](https://aka.ms/vspreview/) sayfasından indirebilir ve yükleyebilirsiniz.

> [!IMPORTANT]
> Bizimle ilgili bir öneriniz varsa lütfen bize bildirin! [**Geliştirici topluluk**](https://aka.ms/vs-suggest) portalı aracılığıyla tasarım kararları almak için sizinle ilgili bir fırsat sunuyoruz.

## <a name="see-also"></a>Ayrıca bkz.

- Microsoft Learn [Visual Studio 'Da git ve GitHub Ile çalışmaya başlama](/learn/modules/visual-studio-github-push/) öğreticisi
- YouTube 'da [Visual Studio videosunda git ile çalışmaya](https://www.youtube.com/watch?v=GCZ9x3yqkyc) başlama
- [Visual Studio blog gönderisine git deneyiminin yayını duyurusu](https://devblogs.microsoft.com/visualstudio/announcing-the-release-of-the-git-experience-in-visual-studio/)
- YouTube 'da [Yeni git deneyimi videosunu başlatma](https://www.youtube.com/watch?v=UHrAg3iKoe0&t)
- [Visual Studio araç kutusu serisi şunları sunar:](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/The-New-Git-Experience) Channel 9 ve [YouTube](https://www.youtube.com/watch?v=ZiQ2LXtAJ6I&feature=youtu.be) 'da yeni git deneyimi videosu
- [Visual Studio blog gönderisine git deneyimine heyecan verici yeni güncelleştirmeler](https://devblogs.microsoft.com/visualstudio/exciting-new-updates-to-the-git-experience-in-visual-studio/)
- [Visual Studio 2019 blog gönderisine gelişmiş git deneyimi](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/)
- [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)
- [Visual Studio 2019 sürüm notları](/visualstudio/releases/2019/release-notes)
