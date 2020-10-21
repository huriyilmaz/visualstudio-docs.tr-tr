---
title: Visual Studio’da yeni Git deneyimi (Önizleme)
titleSuffix: ''
description: Visual Studio 2019 'de yeni tümleşik git deneyimi hakkında bilgi edinin
ms.date: 10/13/2020
ms.topic: conceptual
ms.author: tglee
author: prnadago
ms.manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: ad75fcff26365afdbc4fb4b02975d7c3211fa79b
ms.sourcegitcommit: 4450abc99453ccaf8936449bbff437c5b9efa022
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92334213"
---
# <a name="new-git-experience-in-visual-studio-preview"></a>Visual Studio’da yeni Git deneyimi (Önizleme)

[Sürüm 16,6](/visualstudio/releases/2019/release-notes-v16.6)' den başlayarak, Visual Studio 2019 artık IDE 'den git kullanmayı kolaylaştıran yeni bir git deneyimi içermektedir. Git, en yaygın olarak kullanılan modern sürüm denetim sistemidir. bu nedenle, profesyonel bir geliştirici olun veya nasıl kod kullanacağınızı öğreniyor olun, git size çok faydalı olabilir.

> [!TIP]
> Git 'i yeni kullanıyorsanız, https://git-scm.com/ Web sitesi başlamak için iyi bir yerdir. Burada, popüler bir çevrimiçi kitap, git temel bilgileri Videoları ve en fazla sayfa bulabilirsiniz.

## <a name="how-to-start-using-git-in-visual-studio"></a>Visual Studio 'da git 'i kullanmaya başlama

Yeni git deneyimini değiştirmek için, **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **Önizleme özellikleri** ' ne gidin ve ardından **Yeni git Kullanıcı deneyimi** onay kutusunu seçin.

:::image type="content" source="media/git-opt-new-user-experience.png" alt-text="Visual Studio 'da Seçenekler iletişim kutusunun Önizleme özellikleri bölümünün ekran görüntüsü ":::

Visual Studio 2019 ' de git kullanmanın üç yolu vardır:

- [Var olan bir Git deposunu açın](#open-an-existing-local-repository). Kodunuz zaten makinenizde ise, **Dosya**  >  **Aç**  >  **Proje/çözüm** (veya **klasör**) kullanarak dosyayı açabilir ve Visual Studio başlatılmış bir git deposu olup olmadığını otomatik olarak algılar.
- [Yeni bir git deposu oluşturun](#create-a-new-git-repository). Kodunuz git ile ilişkili değilse, yeni bir git deposu oluşturabilirsiniz.
- [Var olan bir Git deposunu kopyalayın](#clone-an-existing-git-repository). Üzerinde çalışmak istediğiniz kod makinenizde yoksa, var olan uzak depoları kopyalayabilirsiniz.

## <a name="create-a-new-git-repository"></a>Yeni bir git deposu oluşturun

Kodunuz git ile ilişkili değilse, yeni bir git deposu oluşturarak başlayabilirsiniz. Bunu yapmak için, menü çubuğundan **Git**  >  **deposu oluştur** ' u seçin. Ardından, **Git deposu oluştur** iletişim kutusunda bilgilerinizi girin.

:::image type="content" source="media/git-create-repository.png" alt-text="Visual Studio 'da Seçenekler iletişim kutusunun Önizleme özellikleri bölümünün ekran görüntüsü ":::

**Git deposu oluştur** iletişim kutusu, yeni deponuzu GitHub 'a itmenizi kolaylaştırır. Varsayılan olarak, yeni deponuz özeldir ve bu, kendisine erişebilen tek bir tane olduğu anlamına gelir. Kutunun işaretini kaldırırsanız, deponuz herkese açık hale gelir, yani GitHub 'daki herkes tarafından görüntülenebilir.

> [!TIP]
> Deponuzun ortak veya özel olup olmadığı, bir ekip ile çalışmasanız bile, kodunuzun bir uzak yedeğinin GitHub 'da güvenli bir şekilde depolanmasını sağlamak en iyisidir. Bu Ayrıca, kullandığınız bilgisayar ne olduğuna bakılmaksızın kodunuzun sizin için kullanılabilir olmasını sağlar.

**Yalnızca yerel** ' i kullanarak yerel bir git deposu oluşturmayı tercih edebilirsiniz. Ya da, **var olan uzak** seçeneğini kullanarak, deponuzu herhangi bir başka git sağlayıcısında mevcut bir boş uzak depoya bağlayabilirsiniz.

## <a name="clone-an-existing-git-repository"></a>Var olan bir Git deposunu Kopyala

Visual Studio basit bir kopyalama deneyimi içerir. Kopyalamak istediğiniz deponun URL 'sini biliyorsanız, **Depo konumu** bölümüne URL 'yi yapıştırabilir ve sonra Visual Studio 'nun klonlanmasını istediğiniz disk konumunu seçebilirsiniz.

:::image type="content" source="media/git-clone-repository.png" alt-text="Visual Studio 'da Seçenekler iletişim kutusunun Önizleme özellikleri bölümünün ekran görüntüsü ":::

Depo URL 'sini bilmiyorsanız, Visual Studio mevcut GitHub veya Azure DevOps deponuzu ve daha sonra klonlamanızı kolaylaştırır.

### <a name="open-an-existing-local-repository"></a>Mevcut bir yerel depoyu aç

Bir depoyu kopyaladıktan veya bir tane oluşturduktan sonra, Visual Studio Git deposunu algılar ve Git menüsünde **yerel depolar** listenize ekler. Buradan git depolarınız arasında hızlı bir şekilde erişebilir ve geçiş yapabilirsiniz.

:::image type="content" source="media/git-local-repositories.png" alt-text="Visual Studio 'da Seçenekler iletişim kutusunun Önizleme özellikleri bölümünün ekran görüntüsü ":::

## <a name="view-files-in-solution-explorer"></a>Çözüm Gezgini dosyaları görüntüleme

Bir depoyu kopyaladığınızda veya yerel bir depoyu açtığınızda, Visual Studio daha önce açık olan tüm çözümleri ve projeleri kaydederek ve kapatarak bu git bağlamına geçiş yapar. Çözüm Gezgini git deposunun kökündeki klasörü yükler ve herhangi bir görünüm dosyası için dizin ağacını tarar. Bunlar, CMakeLists.txt veya. sln dosya uzantısına sahip olanlar gibi dosyaları içerir.

Visual Studio, Çözüm Gezgini ' de yüklediğiniz görünüm dosyasını temel alarak görünümünü ayarlar:

- Tek bir. sln dosyası içeren bir depoyu klonladığınızda, Çözüm Gezgini bu çözümü doğrudan sizin için yükler.
- Çözüm Gezgini deponuzdaki herhangi bir. sln dosyasını algılamazsa, varsayılan olarak klasör görünümünü yükler.
- Deponuzda birden fazla. sln dosyası varsa Çözüm Gezgini, aralarından seçim yapabileceğiniz kullanılabilir görünümlerin listesini gösterir.

Çözüm Gezgini araç çubuğundaki **görünümleri Değiştir** düğmesini kullanarak şu anda açık olan görünüm ve görünüm listesi arasında geçiş yapabilirsiniz.

:::image type="content" source="media/git-solution-explorer-views.png" alt-text="Visual Studio 'da Seçenekler iletişim kutusunun Önizleme özellikleri bölümünün ekran görüntüsü ":::

## <a name="git-changes-window"></a>Git değişiklikleri penceresi

Git, çalışmanız sırasında deponuzdaki dosya değişikliklerini izler ve deponuzdaki dosyaları üç kategoriye ayırır. Bu değişiklikler, komut satırına komutu girerken göreceğiniz şekilde eşdeğerdir `git status` :

- **Değiştirilmemiş dosyalar**: Bu dosyalar son işlemenizden bu yana değişmemiştir.
- **Değiştirilen dosyalar**: Bu dosyalar son işlemenizden sonra değişir, ancak henüz bir sonraki yürütmede hazırlanmadınız.
- **Hazırlanmış dosyalar**: Bu dosyalar bir sonraki işlemeye eklenecek değişiklikler olur.

İşinizi yaparken, Visual Studio **Git değişiklikleri** penceresinin **değişiklikler** bölümünde dosya değişikliklerini projenizde izler.

:::image type="content" source="media/git-changes-window.png" alt-text="Visual Studio 'da Seçenekler iletişim kutusunun Önizleme özellikleri bölümünün ekran görüntüsü ":::

Değişiklikleri aşamalandırmaya hazırsanız, hazırlamak istediğiniz her bir **+** dosyanın (artı) düğmesine tıklayın veya bir dosyaya sağ tıklayıp **aşama**' ü seçin. Ayrıca, **+** **değişiklikler** bölümünün en üstünde bulunan tümü (artı) düğmesini kullanarak, değiştirdiğiniz tüm dosyaları tek tıklamayla de taşıyabilirsiniz.

Bir değişiklik gerçekleştirdiğinizde, Visual Studio **hazırlanmış bir değişiklikler** bölümü oluşturur. Yalnızca **hazırlanan değişiklikler** bölümündeki değişiklikler, **hazırlanan Yürüt**' i seçerek yapabileceğiniz bir sonraki işlemeye eklenir. Değişiklikler ayrıca **–** (eksi) düğmesine tıklanarak de hazırlanarak çalıştırılabilir. Bu eylem için eşdeğer komut `git commit -m "Your commit message"` .

Ayrıca, hazırlama alanını atlayarak, değiştirilen dosyaları aşamalandırmasını da tercih edebilirsiniz. Bu durumda, Visual Studio, yaptığınız değişiklikleri doğrudan yürütmelerine gerek kalmadan uygulamanıza olanak tanır. Yalnızca tamamlama iletinizi girin ve ardından **Tümünü Kaydet**' i seçin. Bu eylem için eşdeğer komut `git commit -a` .

Visual Studio Ayrıca, **Tümünü Kaydet ve** **Tümünü Yürüt ve Tümünü Kaydet ve Tümünü Yürüt** kısayollarını kullanarak tek bir tıklama ile kaydetmeyi ve eşitlemeyi kolaylaştırır. **Değişiklikler** ve **hazırlanan değişiklikler** bölümlerindeki herhangi bir dosyayı çift tıklattığınızda, dosyanın değiştirilmemiş sürümüyle bir satır satır karşılaştırması görebilirsiniz.

:::image type="content" source="media/git-file-version-compare.png" alt-text="Visual Studio 'da Seçenekler iletişim kutusunun Önizleme özellikleri bölümünün ekran görüntüsü " karakterini kullanarak Azure DevOps iş öğesini bir COMMIT ile ilişkilendirebilirsiniz. **Takım Gezgini**  >  **bağlantıları yönetmek**için Azure DevOps deponuzu bağlayabilirsiniz.

### <a name="select-an-existing-branch"></a>Mevcut bir dalı seçin

Visual Studio, **Git değişiklikleri** penceresinin en üstündeki seçicideki geçerli dalı görüntüler.

:::image type="content" source="media/git-changes-current-branch-selector.png" alt-text="Visual Studio 'da Seçenekler iletişim kutusunun Önizleme özellikleri bölümünün ekran görüntüsü ":::

Geçerli dal, Visual Studio IDE 'nin sağ alt köşesindeki durum çubuğunda da mevcuttur.

:::image type="content" source="media/git-changes-current-branch-status-bar.png" alt-text="Visual Studio 'da Seçenekler iletişim kutusunun Önizleme özellikleri bölümünün ekran görüntüsü ":::

Her iki konumdan de mevcut dallar arasında geçiş yapabilirsiniz.

### <a name="create-a-new-branch"></a>Yeni dal oluştur

Ayrıca, yeni bir dal oluşturabilirsiniz. Bu eylem için eşdeğer komut `git checkout <branchname>` .

Yeni bir dal oluşturmak, dal adını girip mevcut bir dala dayandırmak kadar basittir.

:::image type="content" source="media/git-changes-create-new-branch.png" alt-text="Visual Studio 'da Seçenekler iletişim kutusunun Önizleme özellikleri bölümünün ekran görüntüsü ":::

Temel olarak var olan bir yerel veya uzak dalı seçebilirsiniz. **Kullanıma alma dalı** onay kutusu otomatik olarak yeni oluşturulan dala geçiş yapar. Bu eylem için eşdeğer komut `git checkout -b <new-branch><existing-branch>` .

## <a name="git-repository-window"></a>Git deposu penceresi

Visual Studio, tüm dallar, uzaktan kumandalar ve tamamlama geçmişlerini dahil olmak üzere Deponuzdaki tüm ayrıntıların birleştirilmiş bir görünümü olan yeni bir **Git deposu** penceresi içerir. Bu pencereye doğrudan menü çubuğundaki veya durum çubuğundan **Git** ya da **Görünüm** 'den erişebilirsiniz.

### <a name="manage-branches"></a>Dalları Yönet

**Git** menüsünden **dalları Yönet** ' i seçtiğinizde, **Git deposu** penceresinde dallar ağacı görünümünü görürsünüz. Sol bölmeden, dalları kullanıma almak, yeni dallar oluşturmak, birleştirmek, yeniden temellendir, tek tek seçmek ve daha fazlasını yapmak için sağ tıklama bağlam menüsünü kullanabilirsiniz. Dala tıkladığınızda, sağ bölmedeki tamamlama geçmişinin önizlemesini görebilirsiniz.

### <a name="incoming-and-outgoing-commits"></a>Gelen ve giden işlemeler

Bir dalı getirirken, **Git değişiklikleri** penceresinde, uzak daldaki çekolmayan işlemeler sayısını görüntüleyen dal açılan penceresinin altında bir gösterge bulunur. Bu gösterge Ayrıca, gönderilen yerel işlemelerin sayısını gösterir.

:::image type="content" source="media/git-repo-drop-down-indicator.png" alt-text="Visual Studio 'da Seçenekler iletişim kutusunun Önizleme özellikleri bölümünün ekran görüntüsü ":::

Gösterge Ayrıca **Git deposu** penceresinde bu dalın tamamlama geçmişine gidebileceğiniz bir bağlantı olarak çalışır. Geçmiş en üst kısmında, bu gelen ve giden işlemelerin ayrıntıları görüntülenir. Buradan, yürütmeleri çekme veya gönderim de yapabilirsiniz.

:::image type="content" source="media/git-branch-commit-history.png" alt-text="Visual Studio 'da Seçenekler iletişim kutusunun Önizleme özellikleri bölümünün ekran görüntüsü ":::

#### <a name="commit-details"></a>Kayıt ayrıntıları

Bir **yürütmeyi**çift tıklattığınızda, Visual Studio ayrıntılarını ayrı bir araç penceresinde açar. Buradan işlemeyi geri alabilir, işlemeyi sıfırlayabilir, tamamlama iletisini değiştirebilir veya yürütmede bir etiket oluşturabilirsiniz. İşlemede değiştirilen bir dosyaya tıkladığınızda, Visual Studio, yürütmenin ve onun üst öğesinin yan yana **fark** görünümünü açar.

:::image type="content" source="media/git-branch-commit-details.png" alt-text="Visual Studio 'da Seçenekler iletişim kutusunun Önizleme özellikleri bölümünün ekran görüntüsü ":::

## <a name="handle-merge-conflicts"></a>Birleştirme çakışmalarını işle

İki geliştirici bir dosyadaki aynı satırları değiştirmiyorsa ve git 'in doğru olduğunu otomatik olarak tanımadığı bir birleştirme sırasında çakışmalar meydana gelebilir. Git, birleştirme işlemini ve çakışan bir durumda olduğunu bildirir.

Visual Studio, birleştirme çakışmasını belirlemeyi ve çözümlemeyi kolaylaştırır. İlk olarak, **Git deposu** penceresinde pencerenin üst kısmında bir altın bilgi çubuğu görüntülenir.

:::image type="content" source="media/git-merge-conflict-gold-bar.png" alt-text="Visual Studio 'da Seçenekler iletişim kutusunun Önizleme özellikleri bölümünün ekran görüntüsü ":::

**Git değişiklikleri** penceresi ayrıca, bu dosyanın altındaki ayrı bölümünde birleştirilmemiş dosyalar içeren bir '*birleştirme, çakışmalar ile devam ediyor*' iletisiyle birlikte görüntülenir.

:::image type="content" source="media/git-merge-progress-conflicts-message.png" alt-text="Visual Studio 'da Seçenekler iletişim kutusunun Önizleme özellikleri bölümünün ekran görüntüsü ":::

Ancak, bu pencerelerin hiçbiri açık değilse ve bunun yerine birleştirme çakışması olan dosyaya giderseniz, aşağıdaki metni aramanız gerekmez:

```bash
    <<<<<<< HEAD
    =======
    >>>>>>> main
```

Bunun yerine, Visual Studio sayfanın üst kısmında, açılan dosyanın çakışmalar olduğunu gösteren bir altın bilgi çubuğu görüntüler. Ardından, **birleştirme düzenleyicisini**açmak için bağlantıya tıklayabilirsiniz.

:::image type="content" source="media/git-merge-conflict-gold-info-bar.png" alt-text="Visual Studio 'da Seçenekler iletişim kutusunun Önizleme özellikleri bölümünün ekran görüntüsü ":::

### <a name="the-merge-editor"></a>Birleştirme Düzenleyicisi

Visual Studio 'daki birleştirme Düzenleyicisi, gelen değişiklikleri, geçerli değişikliklerinizi ve birleştirmenin sonucunu görüntüleyen üç yönlü bir birleştirme aracıdır. Dosya içinde çakışmalar ve otomatik birleştirme farkları arasında gezinmek için, **birleştirme düzenleyicisinin** en üst düzeyinde araç çubuğunu kullanabilirsiniz.

:::image type="content" source="media/git-merge-editor.png" alt-text="Visual Studio 'da Seçenekler iletişim kutusunun Önizleme özellikleri bölümünün ekran görüntüsü ":::

Ayrıca, farkları göstermek/gizlemek, sözcük farklarını göstermek/gizlemek ve düzeni özelleştirmek için geçiş tuşlarını da kullanabilirsiniz. Her bir kenarın üstünde, tüm değişiklikleri tek bir tarafa veya diğerine almak için kullanabileceğiniz onay kutuları vardır. Ancak tek tek değişiklikler yapmak için, her iki taraftaki çakışan satırların solundaki onay kutularına tıklayabilirsiniz. Son olarak, çakışmaları çözümlemeyi bitirdiğinizde birleştirme düzenleyicisinde **birleştirmeyi kabul et** düğmesini seçebilirsiniz. Daha sonra bir kayıt iletisi yazın ve çözümü tamamlamak için değişiklikleri işleyin.

## <a name="personalize-your-git-settings"></a>Git ayarlarınızı kişiselleştirin

Git ayarlarınızı bir depo düzeyinde ve genel düzeyde kişiselleştirmek ve özelleştirmek için, menü çubuğunda **Git**  >  **ayarları** ' na veya menü çubuğundaki **Araçlar**  >  **Seçenekler**  >  **kaynak denetimi** ' ne gidin. Sonra istediğiniz seçenekleri belirleyin.

:::image type="content" source="media/git-options-settings.png" alt-text="Visual Studio 'da Seçenekler iletişim kutusunun Önizleme özellikleri bölümünün ekran görüntüsü ":::

## <a name="whats-next"></a>Sırada ne var?

Ayarlanmış olun; Visual Studio 2019 ' deki yeni git deneyimini iyileştirmeye devam ettiğimiz için bu sayfayı güncelleştireceğiz.

> [!IMPORTANT]
> Bizimle ilgili bir öneriniz varsa lütfen bize bildirin! [**Geliştirici topluluk**](https://aka.ms/vs-suggest) portalı aracılığıyla tasarım kararları almak için sizinle ilgili bir fırsat sunuyoruz.

## <a name="see-also"></a>Ayrıca bkz.

- Channel 9 ve [YouTube](https://www.youtube.com/watch?v=ZiQ2LXtAJ6I&feature=youtu.be) 'Da [Yeni git deneyimi](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/The-New-Git-Experience) videosu
- [Visual Studio blog gönderisine git deneyimine heyecan verici yeni güncelleştirmeler](https://devblogs.microsoft.com/visualstudio/exciting-new-updates-to-the-git-experience-in-visual-studio/)
- [Visual Studio 2019 blog gönderisine gelişmiş git deneyimi](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/)
- [Visual Studio 2019 sürüm notları](/visualstudio/releases/2019/release-notes)
