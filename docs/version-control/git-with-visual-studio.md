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
ms.openlocfilehash: 7e8f428ea82fb36abf944b06c22e73f1b9ca9fb6
ms.sourcegitcommit: 113b7df611583307d3965984233a33355d6b0318
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2021
ms.locfileid: "112126571"
---
# <a name="git-experience-in-visual-studio"></a>Visual Studio'de Git deneyimi

Git artık Visual Studio 2019'da varsayılan sürüm denetimi deneyimidir. Sürüm [16.6'dan](/visualstudio/releases/2019/release-notes-v16.6)bu yana, geri bildiriminize göre özellik kümesi üzerinde çalışmalara ve bu küme üzerinde bir kez daha çalışmalara çalıştık. Yeni Git deneyimi, sürüm [16.8](/visualstudio/releases/2019/release-notes/)sürümüne sahip herkes için varsayılan olarak açıktır.

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
> [16.8](/visualstudio/releases/2019/release-notes/)sürümünden itibaren, Visual Studio 2019 tamamen tümleşik bir GitHub hesabı deneyimi içerir. Artık hem GitHub hem de GitHub Enterprise anahtarlık hesabınıza indirebilirsiniz. Microsoft hesaplarıyla olduğu gibi bunları da ekabilecek ve bunlardan yararlanabileceksiniz. Başka bir ifadeyle gitHub kaynaklarınıza erişmek için daha kolay bir Visual Studio. Daha fazla bilgi için [bkz. GitHub hesaplarıyla çalışma Visual Studio.](../ide/work-with-github-accounts.md)

## <a name="create-a-new-git-repository"></a>Yeni git deposu oluşturma

Kodunuz Git ile ilişkili değilse yeni bir Git deposu oluşturarak başlayabilirsiniz. Bunu yapmak için menü  >  **çubuğundan Git Git Deposu** Oluştur'a tıklayın. Ardından Git **deposu oluştur iletişim** kutusuna bilginizi girin.

:::image type="content" source="media/git-create-repository.png" alt-text="Git Deposu Oluştur iletişim kutusu Visual Studio.":::

**Git deposu oluştur iletişim kutusu,** yeni depoyu GitHub'a kolayca itmenizi sağlar. Varsayılan olarak, yeni deponuz özeldir ve bu da depoya erişen tek deponun siz olduğu anlamına gelir. Kutunun işaretini kaldırsanız depo genel olarak görünür ve gitHub'daki herkes tarafından sızabilirsiniz.

> [!TIP]
> Deponun genel veya özel olup olmadığı, bir ekiple çalışmasanız bile kodunuzun uzaktan yedeklerinin GitHub'da güvenli bir şekilde depolanmış olarak depolanmış olarak saklanması en iyisidir. Bu sayede hangi bilgisayarı kullanıyor olursanız olun kodunuzun kullanımınıza hazır olur.

Yalnızca yerel git deposu oluşturmak için Yalnızca yerel seçeneğini **kullanabilirsiniz.** Ya da Mevcut Uzak seçeneğini kullanarak yerel projenizi Azure DevOps veya başka bir Git sağlayıcısında var olan boş bir uzak **depoyla bağlantı oluşturabilirsiniz.**

## <a name="clone-an-existing-git-repository"></a>Mevcut git deposunu kopyalama

Visual Studio, basit bir kopya deneyimi içerir. Klonlamak istediğiniz deponun URL'sini biliyorsanız, URL'yi Depo  konumu bölümüne yapıştırabilirsiniz ve ardından klonlamak istediğiniz disk Visual Studio seçebilirsiniz.

:::image type="content" source="media/git-clone-repository.png" alt-text="Git Deposu Kopyala iletişim kutusu Visual Studio.":::

Depo URL'sini bilmiyorsanız Visual Studio github'ınıza veya depoyu kopyalamanıza Azure DevOps.

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
- **Değiştirilen dosyalar:** Bu dosyalarda son işlemeden bu yana değişiklikler vardır, ancak bunları henüz bir sonraki işleme için hazırlanmadınız.
- **Aşamalı dosyalar:** Bu dosyalar, sonraki işlemeye eklenecek değişikliklere sahip olur.

Siz yaptığınız gibi, Visual Studio Git Değişiklikleri penceresinin Değişiklikler bölümünde projenize **yapılan** dosya **değişikliklerini takip** edin.

:::image type="content" source="media/git-changes-window.png" alt-text="Git Değişiklikleri penceresi Visual Studio.":::

Değişiklikleri aşamaya hazırsanız, aşamaya almak istediğiniz her dosyada (artı) düğmesine tıklayın veya bir dosyaya sağ tıklar ve ardından **+** Aşama'yı **seçin.** Ayrıca Değişiklikler bölümünün üst kısmında yer alan stage all (plus) düğmesini kullanarak değiştirilen tüm dosyalarınızı **+** tek tıklamayla **da sıralayabilirsiniz.**

Bir değişikliği aşamaya Visual Studio bir **Aşamalı Değişiklikler bölümü** oluşturur. Bir sonraki **işlemeye yalnızca** Aşamalı Değişiklikler bölümündeki değişiklikler eklenir ve Bunu, Commit Staged (İşle Aşamalı) **öğesini seçerek yapabilirsiniz.** Bu eylemin eşdeğer komutu şu `git commit -m "Your commit message"` şekildedir: . Değişiklikler , – (eksi) düğmesine tıklayarak **dastaged** olabilir. Bu eylemin eşdeğer komutu, tek `git reset <file_path>` bir dosyanın hazırlanmamış veya bir dizinde yer alan tüm dosyaların `git reset <directory_path>` hazırsız olarak hazırlanmamıştır.

Ayrıca, hazırlama alanı atlayarak değiştirilen dosyalarınızı hazırlamamayı da seçebilirsiniz. Bu durumda, Visual Studio doğrudan işlemenize olanak sağlar. Yalnızca işleme iletinizi girin ve Ardından Hepsini **İşle'yi seçin.** Bu eylemin eşdeğer komutu şu `git commit -a` şekildedir: .

Visual Studio, Hepsini Commit ve Push ve Commit All ve  Sync kısayollarını kullanarak tek tıklamayla işlemeyi ve **eşitlemeyi de** kolaylaştırır. Değişiklikler ve Aşamalı değişiklikler bölümlerindeki herhangi  bir dosyaya çift tıklarsanız, dosyanın değiştirilmemiş sürümüyle satır satır karşılaştırması yapabilirsiniz. 

:::image type="content" source="media/git-file-version-compare.png" alt-text="Visual Studio'daki dosya sürümlerinin satır satır karşılaştırması ":::

> [!TIP]
> Depoya bağlı Azure DevOps "#" karakterini kullanarak bir iş öğesini bir işlemeyle Azure DevOps. Bağlantıları Yönet'Azure DevOps kullanarak Takım Gezgini   >  **bağlanabilirsiniz.**

### <a name="select-an-existing-branch"></a>Mevcut bir dalı seçme

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

Bir dalı getirebilirsiniz. **Git Değişiklikleri** penceresinde, dal açılan listesinde uzak daldan gelen işlanmamış işlemelerin sayısını gösteren bir gösterge vardır. Bu gösterge ayrıca size, işlenmiş olmayan yerel işlemelerin sayısını gösterir.

:::image type="content" source="media/git-repo-drop-down-indicator.png" alt-text="Uygulamanın içinde gösterge açılan kullanıcı arabirimi öğesini gösteren Git Değişiklikleri Visual Studio ":::

Gösterge ayrıca sizi Git Deposu penceresinde bu dalın işleme geçmişine götüren bir **bağlantı olarak da** işlev gösterir. Geçmişin en üstünde artık bu gelen ve giden işlemelerin ayrıntıları görüntülenir. Buradan işlemeleri çekme veya itme kararlarını da vesersiniz.

:::image type="content" source="media/git-branch-commit-history.png" alt-text="Git Deposundaki bir dalın işleme geçmişini gösteren git deposu Visual Studio ":::

#### <a name="commit-details"></a>Commit Details

Bir Commit 'e çift **tıklar** Visual Studio ayrıntılarını ayrı bir araç penceresinde açar. Buradan işlemeyi geri döndürebilirsiniz, işlemeyi sıfırlayabilirsiniz, işleme iletiyi düzeltebilirsiniz veya işlemede bir etiket oluşturabilirsiniz. Yürütmede değiştirilen bir dosyaya tıklarsanız, Visual Studio ve üst  öğesinin yan yana Fark görünümünü açar.

:::image type="content" source="media/git-branch-commit-details.png" alt-text="Visual Studio'daki Commit Details iletişim Visual Studio ":::

## <a name="handle-merge-conflicts"></a>Birleştirme çakışmalarını işleme

İki geliştirici bir dosyada aynı satırları değiştirirse ve Git hangisinin doğru olduğunu otomatik olarak bilmiyorsa birleştirme sırasında çakışmalar oluşabilir. Git birleştirmeyi durdurarak çakışmalı durumda olduğunu size bildirecektir.

Visual Studio birleştirme çakışmalarını tanımlamayı ve çözmeyi kolaylaştırır. İlk olarak **Git Deposu penceresinde** pencerenin en üstünde altın bir bilgi çubuğu gösterilir.

:::image type="content" source="media/git-merge-conflict-gold-bar.png" alt-text="Visual Studio'de 'Birleştirme çakışmalarla tamamlandı' Visual Studio ":::

Git **Değişiklikleri penceresinde** ayrıca *'* Birleştirme devam ediyor çakışmalar ' iletisiyle birlikte, altındaki ayrı bölümde birleştirlanmamış dosyalar görüntülenir.

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

Git ayarlarınızı hem depo düzeyinde hem de genel düzeyde kişiselleştirmek ve özelleştirmek için menü çubuğunda **Git** Ayarları'ya veya menü çubuğundaKi Araçlar Seçenekler Kaynak  >     >    >   Denetimi'ne gidin. Ardından istediğiniz [seçenekleri](git-settings.md) belirleyin.

:::image type="content" source="media/git-options-settings.png" alt-text="IDE'de kişiselleştirme ve özelleştirme ayarlarını seçebilirsiniz Seçenekler Visual Studio kutusu ":::

## <a name="how-to-use-the-full-team-explorer-experience-in-visual-studio"></a>Visual Studio'de tam Takım Gezgini deneyimi Visual Studio

Yeni Git deneyimi, [16.8](/visualstudio/releases/2019/release-notes/) ve Visual Studio 2019'daki varsayılan sürüm denetimi sistemidir. Ancak, kapatmak istediğiniz zaman bunu da kapatmış oluruz. Araçlar Seçenekler  >  **Ortam**  >  **Önizleme**  >  **Özellikleri'ne**  gidin ve Yeni Git kullanıcı deneyimi onay kutusunu açıp kapatarak Git için Takım Gezgini geçiş yapabilirsiniz.

:::image type="content" source="media/git-opt-new-user-experience.png" alt-text="Visual Studio'daki Seçenekler iletişim kutusunun Önizleme Özellikleri Visual Studio ":::

## <a name="whats-next"></a>Sırada ne var?

Yeni Git deneyimi artık Visual Studio 2019 sürüm [16.8'de](/visualstudio/releases/2019/release-notes/)varsayılan olarak açıkken, deneyimi geliştirmek için yeni özellikler eklemeye devam edeceğiz. Bir Önizleme yayında Git deneyimine yapılan yeni güncelleştirmeleri kontrol etmek için, önizleme sayfasından indirip [Visual Studio Preview](https://aka.ms/vspreview/) edinebilirsiniz.

> [!IMPORTANT]
> Bize bir öneriniz varsa lütfen bize haber ver! Geliştirici Topluluğu portal aracılığıyla tasarım kararlarını alma [**fırsatınız**](https://aka.ms/vs-suggest) için teşekkür edersiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Başla git ve GitHub](/learn/modules/visual-studio-github-push/) ile Visual Studio öğreticisinde Microsoft Learn
- [YouTube'daki Visual Studio Git](https://www.youtube.com/watch?v=GCZ9x3yqkyc) ile çalışmaya başlama
- Visual Studio blog [gönderisinde Git Deneyiminin Yayımlanma](https://devblogs.microsoft.com/visualstudio/announcing-the-release-of-the-git-experience-in-visual-studio/) Tarihi
- [YouTube'da yeni Git deneyimi](https://www.youtube.com/watch?v=UHrAg3iKoe0&t) videosunu başlatma
- [Visual Studio Toolbox serisi şunları sunar:](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/The-New-Git-Experience) Channel 9 ve [YouTube'da](https://www.youtube.com/watch?v=ZiQ2LXtAJ6I&feature=youtu.be) yeni Git deneyimi videosu
- Visual Studio blog [gönderisinde Git deneyimine heyecan verici](https://devblogs.microsoft.com/visualstudio/exciting-new-updates-to-the-git-experience-in-visual-studio/) yeni güncelleştirmeler
- [Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/) blog gönderisinde Geliştirilmiş Git Deneyimi
- [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)
- [Visual Studio 2019 sürüm notları](/visualstudio/releases/2019/release-notes)
