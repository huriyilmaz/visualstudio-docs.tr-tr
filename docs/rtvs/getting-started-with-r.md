---
title: R Tutorial ile başlarken
description: Visual Studio'da proje oluşturma, etkileşimli pencere, kod düzenleme ve hata ayıklama dahil olmak üzere R kullanmanın bir walkthrough'u.
ms.date: 06/29/2017
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: df46a2731f9923d85a16082f96c44947099db592
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "63000545"
---
# <a name="get-started-with-r-tools-for-visual-studio"></a>Visual Studio için R Tools ile başlayın

Visual Studio için R Tools (RTVS) yüklendikten sonra [(kuruluma](installing-r-tools-for-visual-studio.md)bakın), bu araçların sağladığı deneyimin tadına hızlıca bakabilirsiniz.

## <a name="create-an-r-project"></a>R projesi oluşturma

1. Visual Studio'yu açın.
1. **Dosya** > **Yeni** > **Proje** seçin (**Ctrl**+**Shift**+**N**)
1. **Şablonlar** > **R**altından "R Project"i seçin, projeye bir ad ve konum verin ve **Tamam'ı**seçin:

   ![Visual Studio'da R için Yeni Proje iletişim kutusu (VS2017'de RTVS)](media/getting-started-01-new-project.png)

1. Proje oluşturulduktan sonra aşağıdaki pencereleri görürsünüz:

    - Sağtarafta Visual Studio Solution Explorer, burada bir içeren *çözüm*içinde projenizi görmek. (Çözümler farklı türde sayıda proje içerebilir; ayrıntılar için [Projeler'e](r-projects-in-visual-studio.md) bakın.
    - Sol üstte, Visual Studio'nun tüm düzenleme özellikleriyle kaynak kodunu düzenleyebileceğiniz yeni bir R dosyası`script.R`yer almaktadır.
    - Sol altta, etkileşimli olarak geliştirebileceğiniz ve kodu test edebileceğiniz **R Interactive** penceresi yer alan pencere yer.

> [!Note]
> **R Interactive** penceresini, herhangi bir proje açık olmadan ve farklı bir proje türü yüklense bile kullanabilirsiniz. İstediğiniz zaman **R Tools** > **Windows** > **R Interactive'i** seçin.

## <a name="explore-the-interactive-window-and-intellisense"></a>İnteraktif Pencere ve IntelliSense'i keşfedin

1. Etkileşimli pencerenin yazarak çalıştığını `3 + 4` test edin ve sonucu görmek için **enter:**

    ![Visual Studio 2017'de R Interactive penceresi (VS2017)](media/getting-started-02-interactive1.png)

1. Biraz daha karmaşık `ds <- c(1.5, 6.7, 8.9) * 1:12`bir şey girin `ds` ve sonra sonucu görmek için girin:

    ![Visual Studio'da R için ek etkileşimli örnek](media/getting-started-03-interactive2.png)

1. Yazın `mean(ds)` ama en kısa sürede `m` yazın `me`veya, Visual Studio IntelliSense otomatik tamamlama seçenekleri sağlar dikkat edin. Listede istediğiniz tamamlanma seçildiğinde, eklemek için **Sekme'ye** basın; ok tuşları veya fare ile seçimi değiştirebilirsiniz.

    ![Code girerken intelliSense görünen](media/getting-started-04-intellisense1.png)

1. Tamamladıktan `mean`sonra, açılış parantezini yazın `(` ve IntelliSense'in işlev için size nasıl satır içinde yardım verdiğini not edin:

    ![IntelliSense bir işlev için yardım gösteren](media/getting-started-05-intellisense2.png)

1. Satırı `mean(ds)` tamamlayın ve sonucu görmek`[1] 39.51667`için Enter tuşuna basın ( ).

1. Etkileşimli pencere yardımla entegre olduğundan, `?mean` Visual Studio'daki R **Help** penceresinde bu işlev için ekranlar yardımcı olur. Ayrıntılar için Visual [Studio için R Tools'a yardım için](getting-started-help.md)bkz.

    ![Visual Studio'da R Yardım penceresi](media/getting-started-06-help.png)

1. Çıktı doğrudan etkileşimli `plot(1:100)`pencerede görüntülenemezken Visual Studio'da yeni bir pencere açmak gibi bazı komutlar:

    ![Visual Studio'da bir arsanın görüntülenmesi](media/getting-started-07-plot-window.png)

Etkileşimli pencere ayrıca geçmişinizi gözden geçirmenize, çalışma alanlarınızı yüklemenize ve kaydetmenize, hata ayıklayıcıya eklemenize ve kopyala yapıştır kullanmak yerine kaynak kod dosyalarıyla etkileşimkurmanıza olanak tanır. Ayrıntılar için [R Interactive Window ile Çalışma'ya](interactive-repl-for-r-in-visual-studio.md) bakın.

## <a name="experience-code-editing-features"></a>Deneyim kodu düzenleme özellikleri

Etkileşimli pencere ile kısaca çalışmak, kod düzenleyicisinde de çalışan IntelliSense gibi temel düzenleme özelliklerini gösterir. Öncekiyle aynı kodu girerseniz, aynı otomatik tamamlama ve IntelliSense istemlerini görürsünüz, ancak çıktıyı görmezsiniz.

Kod yazmak bir *. R* dosyası, tüm kodunuzu aynı anda görmenizi sağlar ve küçük değişiklikler yapmanızı ve ardından etkileşimli pencerede kodu çalıştırarak sonucu hızlı bir şekilde görmenizi kolaylaştırır. Ayrıca, bir projede istediğiniz kadar dosyanız da olabilir. Kod bir dosyada olduğunda, hata ayıklayıcıda (bu makalede daha sonra tartışılan) adım adım çalıştırabilirsiniz. Bu özellikler, bir veya daha fazla veri kümesini işlemek için hesaplama algoritmaları ve kod yazarken, özellikle de tüm ara sonuçları incelemek istediğinizde yararlıdır.

Örnek olarak, aşağıdaki adımlar [Merkezi Sınır Teoremi'ni](https://en.wikipedia.org/wiki/Central_limit_theorem) (Vikipedi) keşfetmek için küçük bir kod oluşturur. (Bu örnek Paul Teetor tarafından *R Yemek Kitabı* uyarlanmıştır.)

1. Düzenleyicide `script.R` aşağıdaki kodu girin:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. Sonuçları hızlı bir şekilde görmek için tüm kodu **(Ctrl**+**A)** seçin, ardından **Ctrl**+**Enter** tuşuna basın veya sağ tıklatın ve **Etkileşimli Yürüt'ü**seçin. Seçili kodun tümü etkileşimli pencerede, sonucu bir çizim penceresinde göstererek doğrudan yazargibi çalıştırılır:

    ![Visual Studio'da bir arsanın görüntülenmesi](media/getting-started-08-plot1.png)

1. Tek bir satır için, etkileşimli pencerede bu satırı çalıştırmak için İstediğin zaman **Ctrl**+**Enter** tuşuna basmaniz gerekiyor.

> [!Tip]
> Kodu hızlı bir şekilde çalıştırmak için **ctrl**+**Enter** tuşuna basarak (veya **Ctrl**+**A** ile her şeyi seçip **ctrl**+**enter**tuşuna basarak) kod oluşturma desenini öğrenin. Bunu yapmak, fareyi aynı işlemler için kullanmaktan çok daha verimlidir.
>
> Buna ek olarak, çizim penceresini Visual Studio çerçevesinin dışına sürükleyebilir ve düşürebilir ve ekranınızda istediğiniz zaman yerleştirebilirsiniz. Daha sonra çizim penceresini istediğiniz boyutlara yeniden boyutlandırAbilir ve ardından bir resim veya PDF dosyasına kaydedebilirsiniz.

1. İkinci bir çizim eklemek için birkaç satır daha kod ekleyin:

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    lines(density(samp.means))
    ```

1. Kodu çalıştırmak için **Ctrl**+**A** ve **Ctrl**+**Enter** tuşuna basın ve aşağıdaki sonucu üretin:

    ![Visual Studio'da güncelleştirilmiş çift arsa](media/getting-started-09-plot2.png)

1. Sorun, ilk çizimdikey ölçeği belirler, bu nedenle ikinci `lines`çizim (ile) uymuyor olmasıdır. Bu sorunu gidermek için, `ylim` `plot` aramadaki parametreyi ayarlamamız gerekir, ancak bunu en yüksek dikey değeri hesaplamak için kod eklememiz gerekir. Bu satırı etkileşimli pencerede yapmak sakıncalıdır, çünkü kodu aramadan `samp.means` `plot`önce kullanmak üzere yeniden düzenlememiz gerekir. Ancak bir kod dosyasında, uygun kodları kolayca yapabiliriz:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)

    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    max.samp.means <- max(density(samp.means)$y)

    plot(density(pop), main = "Population Density",
        ylim = c(0, max.samp.means),
        xlab = "X", ylab = "")
    lines(density(samp.means))
    ```

1. **Sonucu**+görmek için Ctrl**A** ve **Ctrl**+tekrar**girin:**

    ![Visual Studio'da güncellenen çift çizim, doğru ölçeklendirildi](media/getting-started-10-plot3.png)

Editörde yapabileceğin daha çok şey var. Ayrıntılar için, Bkz. [R kodu,](editing-r-code-in-visual-studio.md) [IntelliSense](r-intellisense.md)ve [Kod parçacıkları.](code-snippets-for-r.md)

## <a name="debug-your-code"></a>Kodunuzda hata ayıklama

Visual Studio'nun en önemli güçlerinden biri hata ayıklama ui'si. RTVS bu güçlü temel üzerine inşa ve [Değişken Explorer](variable-explorer.md)gibi yenilikçi ui ekler. Burada, hata ayıklama ilk bakışta bir göz atalım.

1. Başlangıç olarak, **R Tools** > **Session** > **Reset** menü komutunu kullanarak şimdiye kadar yaptığınız her şeyi temizlemek için geçerli çalışma alanını sıfırlayın. Varsayılan olarak, etkileşimli pencerede yaptığınız her şey, hata ayıklama tarafından da kullanılan geçerli oturuma tahakkuk eder. Oturumu sıfırlayarak, hata ayıklama oturumunun önceden varolan veriler olmadan başlatılmasını sağlarsınız. Ancak **Sıfırla** komutu *komutunuzu etkilemez. R* kaynak dosyası, çünkü bu yönetilen ve çalışma alanı dışında kaydedilir.

1. *Senaryoyla birlikte. *Önceki bölümde oluşturulan R dosyası, bu satıra caret `pop <-` yerleştirerek ve sonra **F9**basarak başlayan satırüzerinde bir kesme noktası ayarlayın , veya **Hata Ayıklama** > **Breakpoint** menü komutunu seçerek. Alternatif olarak, kırmızı kırılma noktası noktasının göründüğü satır için sol kenar boşluğuna (veya olukta) tıklamanız yeterlidir:

    ![Düzenleyicide bir kesme noktası ayarlama](media/getting-started-11-debug1.png)

1. Komut dosyasındaki kodla hata ayıklayıcıyı *başlatın. R* araç çubuğundaki **Kaynak başlangıç dosyası** düğmesini seçerek, Hata **Ayıklama** > **Kaynak başlangıç dosyası** menü öğelerini seçerek veya **F5 tuşuna**basarak. Visual Studio hata ayıklama moduna girer ve kodu çalıştırmaya başlar. Ancak, kesme noktasını ayarladığınız satırda durur:

    ![Visual Studio hata ayıklama bir kesme noktasında durdurma](media/getting-started-12-debug2.png)

1. Hata ayıklama sırasında Visual Studio, kodunuzu satır satır geçme olanağı sağlar. Ayrıca işlevlere adım atabilir, bunların üzerine adım atabilir veya çağrı bağlamına adım atabilirsiniz. Bu özellikler, diğerleriyle birlikte **Hata Ayıklama** menüsünde, düzenleyicideki sağ tıklatma bağlam menüsünde ve Hata Ayıklama araç çubuğunda bulunabilir:

    ![Visual Studio'da hata ayıklama araç çubuğu](media/getting-started-13-debug3.png)

1. Bir kesme noktasında durdurulduğunda, değişkenlerin değerlerini inceleyebilirsiniz. Visual Studio'da **Otomatikler** penceresini bulun ve alttaki **Yerel Ler**adlı sekmeyi seçin. **Yerel ler** penceresi, programın geçerli noktasındayerel değişkenleri gösterir. Kesme noktası kümesinde daha önce durdurulursanız, `pop` değişkenin henüz tanımlanmadığını görürsünüz. Şimdi **Hata Ayıklama** > **Adım Üstü** komutunu **(F10)** kullanın ve `pop` görünen değeri görürsünüz:

    ![Visual Studio'da yerel halk penceresi](media/getting-started-14-debug4.png)

1. Genel kapsam ve paket kapsamları da dahil olmak üzere farklı kapsamlarda değişkenleri incelemek için [Değişken Gezgini'ni](variable-explorer.md)kullanın. Değişken Gezgin, sıralanabilir sütunlarla bir tabular görünüme geçme nizi ve verileri Bir CSV dosyasına dışa aktarmanızı da sağlar.

    ![Değişken Gezginin genişletilmiş görünümü](media/variable-explorer-expanded-results.png)

1. Program da satır satır adım atmaya devam edebilir veya tamamlamaya (veya bir sonraki kesme noktasına) çalıştırmak için **Continue** **(F5)** seçeneğini belirleyebilirsiniz.

Daha derine inmek için Hata [Ayıklama](debugging-r-in-visual-studio.md) ve [Değişken Gezgin'e](variable-explorer.md)bakın.

## <a name="next-steps"></a>Sonraki adımlar

Bu gözden geçirme de, Visual Studio'da etkileşimli pencereyi, kod düzenlemeyi ve hata ayıklamayı kullanarak R projelerinin temellerini öğrendiniz. Daha fazla yetenek keşfetmeye devam etmek için aşağıdaki makalelere ve içindekiler tablosunda gösterilen makalelere bakın:

- [Örnek projeler](getting-started-samples.md)
- [Kodu düzenleme](editing-r-code-in-visual-studio.md)
- [Hata ayıklama](debugging-r-in-visual-studio.md)
- [Çalışma Alanları](r-workspaces-in-visual-studio.md)
- [Verileri görselleştirme](visualizing-data-with-r-in-visual-studio.md)
