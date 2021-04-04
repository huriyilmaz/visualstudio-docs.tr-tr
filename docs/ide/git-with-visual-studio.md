---
title: Visual Studio 'da git deneyimi
titleSuffix: ''
description: Visual Studio 2019 ' de yeni tümleşik git deneyiminin daha üretken olmanıza nasıl yardımcı olabileceğini öğrenin.
ms.date: 04/01/2021
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: b58a60efbf2c602706eed6d9278574d1bf1fffcc
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216767"
---
# <a name="git-experience-in-visual-studio"></a>Visual Studio 'da git deneyimi

Git artık Visual Studio 2019 ' de varsayılan sürüm denetimi deneyimidir. [Sürüm 16,6](/visualstudio/releases/2019/release-notes-v16.6)' den itibaren, özellik kümesini oluşturmaya ve geri bildiriminiz doğrultusunda bu uygulamayı yineleme konusunda çalıştık. Yeni git deneyimi, [sürüm 16,8](/visualstudio/releases/2019/release-notes/)sürümüne sahip herkes için varsayılan olarak açıktır.

> [!TIP]
> Git, en yaygın olarak kullanılan modern sürüm denetim sistemidir. bu nedenle, profesyonel bir geliştirici olun veya nasıl kod kullanacağınızı öğreniyor olun, git size çok faydalı olabilir. Git 'i yeni kullanıyorsanız, https://git-scm.com/ Web sitesi başlamak için iyi bir yerdir. Burada, en çok sayfaları, popüler bir çevrimiçi kitabı ve git temel videoları hakkında bilgi edinebilirsiniz.

## <a name="how-to-use-git-in-visual-studio"></a>Visual Studio 'da git 'i kullanma

Visual Studio 2019 ' de yeni git deneyiminin nasıl kullanılacağı konusunda size kılavuzluk edeceğiz, ancak ilk olarak hızlı bir tura katılmak istiyorsanız aşağıdaki videoya göz atın: <br><br>*Video uzunluğu: 5,27 dakika*

> [!VIDEO https://www.youtube.com/embed/UHrAg3iKoe0]

Daha üretken olmak için Visual Studio ile git kullanmaya başlamanın üç yolu vardır:

- [Var olan bir Git deposunu açın](#open-an-existing-local-repository). Kodunuz zaten makinenizde ise, **Dosya**  >  **Aç**  >  **Proje/çözüm** (veya **klasör**) kullanarak dosyayı açabilir ve Visual Studio başlatılmış bir git deposu olup olmadığını otomatik olarak algılar.
- [Yeni bir git deposu oluşturun](#create-a-new-git-repository). Kodunuz git ile ilişkili değilse, yeni bir git deposu oluşturabilirsiniz.
- [Var olan bir Git deposunu kopyalayın](#clone-an-existing-git-repository). Üzerinde çalışmak istediğiniz kod makinenizde yoksa, var olan uzak depoları kopyalayabilirsiniz.

> [!NOTE]
> [Sürüm 16,8](/visualstudio/releases/2019/release-notes/)ile başlayarak, Visual Studio 2019 tamamen tümleşik bir GitHub hesabı deneyimi içerir. Artık anahtarınıza GitHub ve GitHub kurumsal hesaplarını ekleyebilirsiniz. Microsoft hesapları ile yaptığınız gibi bunları ekleyebilir ve bu kişilere de atayabilirsiniz. Bu, GitHub kaynaklarınıza Visual Studio üzerinden erişmenin daha kolay bir zaman olacağı anlamına gelir. Daha fazla bilgi için bkz. [Visual Studio 'Da GitHub hesaplarıyla çalışma](work-with-github-accounts.md) sayfası.

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

### <a name="open-an-existing-local-repository"></a>Mevcut bir yerel depoyu aç

Bir depoyu kopyaladıktan veya bir tane oluşturduktan sonra, Visual Studio Git deposunu algılar ve Git menüsünde **yerel depolar** listenize ekler. Buradan git depolarınız arasında hızlı bir şekilde erişebilir ve geçiş yapabilirsiniz.

:::image type="content" source="media/git-local-repositories.png" alt-text="Visual Studio 'daki Git menüsünde yerel depolar seçeneği ":::

## <a name="view-files-in-solution-explorer"></a>Çözüm Gezgini dosyaları görüntüleme

Bir depoyu kopyaladığınızda veya yerel bir depoyu açtığınızda, Visual Studio daha önce açık olan tüm çözümleri ve projeleri kaydederek ve kapatarak bu git bağlamına geçiş yapar. Çözüm Gezgini git deposunun kökündeki klasörü yükler ve herhangi bir görünüm dosyası için dizin ağacını tarar. Bunlar, CMakeLists.txt veya. sln dosya uzantısına sahip olanlar gibi dosyaları içerir.

Visual Studio, Çözüm Gezgini ' de yüklediğiniz görünüm dosyasını temel alarak görünümünü ayarlar:

- Tek bir. sln dosyası içeren bir depoyu klonladığınızda, Çözüm Gezgini bu çözümü doğrudan sizin için yükler.
- Çözüm Gezgini deponuzdaki herhangi bir. sln dosyasını algılamazsa, varsayılan olarak klasör görünümünü yükler.
- Deponuzda birden fazla. sln dosyası varsa Çözüm Gezgini, aralarından seçim yapabileceğiniz kullanılabilir görünümlerin listesini gösterir.

Çözüm Gezgini araç çubuğundaki **görünümleri Değiştir** düğmesini kullanarak şu anda açık olan görünüm ve görünüm listesi arasında geçiş yapabilirsiniz.

:::image type="content" source="media/git-solution-explorer-views.png" alt-text="Visual Studio 'da görünümleri Değiştir düğmesi seçili Çözüm Gezgini.":::

## <a name="git-changes-window"></a>Git değişiklikleri penceresi

Git, çalışmanız sırasında deponuzdaki dosya değişikliklerini izler ve deponuzdaki dosyaları üç kategoriye ayırır. Bu değişiklikler, komut satırına komutu girerken göreceğiniz şekilde eşdeğerdir `git status` :

- **Değiştirilmemiş dosyalar**: Bu dosyalar son işlemenizden bu yana değişmemiştir.
- **Değiştirilen dosyalar**: Bu dosyalar son işlemenizden sonra değişir, ancak henüz bir sonraki yürütmede hazırlanmadınız.
- **Hazırlanmış dosyalar**: Bu dosyalar bir sonraki işlemeye eklenecek değişiklikler olur.

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

Visual Studio, **Git değişiklikleri** penceresinin en üstündeki seçicideki geçerli dalı görüntüler.

:::image type="content" source="media/git-changes-current-branch-selector.png" alt-text="Visual Studio 'da git değişiklikleri seçicisinin en üstünde yer alan seçiciyi kullanarak görüntüleyebileceğiniz güncel dallar ":::

Geçerli dal, Visual Studio IDE 'nin sağ alt köşesindeki durum çubuğunda da mevcuttur.

:::image type="content" source="media/git-changes-current-branch-status-bar.png" alt-text="Visual Studio IDE 'de sağ alt köşedeki durum çubuğunu kullanarak görüntüleyebileceğiniz geçerli dallar ":::

Her iki konumdan de mevcut dallar arasında geçiş yapabilirsiniz.

### <a name="create-a-new-branch"></a>Yeni dal oluştur

Ayrıca, yeni bir dal oluşturabilirsiniz. Bu eylem için eşdeğer komut `git checkout -b <branchname>` .

Yeni bir dal oluşturmak, dal adını girip mevcut bir dala dayandırmak kadar basittir.

:::image type="content" source="media/git-changes-create-new-branch.png" alt-text="Visual Studio 'da yeni dal oluştur iletişim kutusu ":::

Temel olarak var olan bir yerel veya uzak dalı seçebilirsiniz. **Kullanıma alma dalı** onay kutusu otomatik olarak yeni oluşturulan dala geçiş yapar. Bu eylem için eşdeğer komut `git checkout -b <new-branch><existing-branch>` .

## <a name="git-repository-window"></a>Git deposu penceresi

Visual Studio, tüm dallar, uzaktan kumandalar ve tamamlama geçmişlerini dahil olmak üzere Deponuzdaki tüm ayrıntıların birleştirilmiş bir görünümü olan yeni bir **Git deposu** penceresi içerir. Bu pencereye doğrudan menü çubuğundaki veya durum çubuğundan **Git** ya da **Görünüm** 'den erişebilirsiniz.

### <a name="manage-branches"></a>Dalları Yönet

**Git** menüsünden **dalları Yönet** ' i seçtiğinizde, **Git deposu** penceresinde dallar ağacı görünümünü görürsünüz. Sol bölmeden, dalları kullanıma almak, yeni dallar oluşturmak, birleştirmek, yeniden temellendir, tek tek seçmek ve daha fazlasını yapmak için sağ tıklama bağlam menüsünü kullanabilirsiniz. Dala tıkladığınızda, sağ bölmedeki tamamlama geçmişinin önizlemesini görebilirsiniz.

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

:::image type="content" source="media/git-merge-progress-conflicts-message.png" alt-text="Visual Studio 'da ' çakışmalar ile devam ediyor ' iletisi ":::

Ancak, bu pencerelerin hiçbiri açık değilse ve bunun yerine birleştirme çakışması olan dosyaya giderseniz, aşağıdaki metni aramanız gerekmez:

```bash
    <<<<<<< HEAD
    =======
    >>>>>>> main
```

Bunun yerine, Visual Studio sayfanın üst kısmında, açılan dosyanın çakışmalar olduğunu gösteren bir altın bilgi çubuğu görüntüler. Ardından, **birleştirme düzenleyicisini** açmak için bağlantıya tıklayabilirsiniz.

:::image type="content" source="media/git-merge-conflict-gold-info-bar.png" alt-text="Visual Studio 'da ' dosya birleştirme çakışmaları içeriyor ' iletisinin ekran görüntüsü ":::

### <a name="the-merge-editor"></a>Birleştirme Düzenleyicisi

Visual Studio 'daki birleştirme Düzenleyicisi, gelen değişiklikleri, geçerli değişikliklerinizi ve birleştirmenin sonucunu görüntüleyen üç yönlü bir birleştirme aracıdır. Dosya içinde çakışmalar ve otomatik birleştirme farkları arasında gezinmek için, **birleştirme düzenleyicisinin** en üst düzeyinde araç çubuğunu kullanabilirsiniz.

:::image type="content" source="media/git-merge-editor.png" alt-text="Visual Studio 'da birleştirme Düzenleyicisi ":::

Ayrıca, farkları göstermek/gizlemek, sözcük farklarını göstermek/gizlemek ve düzeni özelleştirmek için geçiş tuşlarını da kullanabilirsiniz. Her bir kenarın üstünde, tüm değişiklikleri tek bir tarafa veya diğerine almak için kullanabileceğiniz onay kutuları vardır. Ancak tek tek değişiklikler yapmak için, her iki taraftaki çakışan satırların solundaki onay kutularına tıklayabilirsiniz. Son olarak, çakışmaları çözümlemeyi bitirdiğinizde birleştirme düzenleyicisinde **birleştirmeyi kabul et** düğmesini seçebilirsiniz. Daha sonra bir kayıt iletisi yazın ve çözümü tamamlamak için değişiklikleri işleyin.

## <a name="personalize-your-git-settings"></a>Git ayarlarınızı kişiselleştirin

Git ayarlarınızı bir depo düzeyinde ve genel düzeyde kişiselleştirmek ve özelleştirmek için, menü çubuğunda **Git**  >  **ayarları** ' na veya menü çubuğundaki **Araçlar**  >  **Seçenekler**  >  **kaynak denetimi** ' ne gidin. Sonra istediğiniz seçenekleri belirleyin.

:::image type="content" source="media/git-options-settings.png" alt-text="Visual Studio IDE 'de kişiselleştirme ve özelleştirme ayarları seçebileceğiniz Seçenekler iletişim kutusu ":::

## <a name="how-to-use-the-full-team-explorer-experience-in-visual-studio"></a>Visual Studio 'da tam Takım Gezgini deneyimini kullanma

Yeni git deneyimi, Visual Studio 2019 ' deki [sürüm 16,8](/visualstudio/releases/2019/release-notes/) ' den sonraki sürümlerde varsayılan sürüm denetim sistemidir. Ancak, devre dışı bırakmak istiyorsanız, kullanabilirsiniz. **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **Önizleme özellikleri** ' ne gidin ve ardından **Yeni git Kullanıcı deneyimi** onay kutusunu açıp git için Takım Gezgini geri dönebilirsiniz.

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
- [Visual Studio’da GitHub hesaplarıyla çalışma](work-with-github-accounts.md)
- [Visual Studio 2019 sürüm notları](/visualstudio/releases/2019/release-notes)
