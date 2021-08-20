---
title: R öğreticisi ile çalışmaya başlama
description: proje oluşturma, etkileşimli pencere, kod düzenlemesi ve hata ayıklama dahil Visual Studio R 'yi kullanma kılavuzu.
ms.date: 06/29/2017
ms.prod: visual-studio-dev15
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 26a7c3ed6db4ceda5128bee93c607e45a0db3ef0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068689"
---
# <a name="get-started-with-r-tools-for-visual-studio"></a>Visual Studio için R Araçları kullanmaya başlayın

Visual Studio için R Araçları (rtvs) yüklendikten sonra (bkz. [yükleme](installing-r-tools-for-visual-studio.md)), bu araçların sağladığı deneyimin hızla bir listesini alabilirsiniz.

## <a name="create-an-r-project"></a>R projesi oluşturma

1. Visual Studio'yu açın.
1. **dosya**  >  **yeni**  >  **Project** seçin (**Ctrl** + **+ Shift** + **N**)
1. **şablonlar** R altında "R Project" seçeneğini belirleyin  >  , projeye bir ad ve konum verin ve **tamam**' ı seçin:

   ![Visual Studio R (VS2017 ' de rtvs) için yeni Project iletişim kutusu](media/getting-started-01-new-project.png)

1. Proje oluşturulduktan sonra, aşağıdaki pencereleri görürsünüz:

    - sağ tarafta, projenizi içeren bir *çözüm* içinde gördüğünüz Visual Studio Çözüm Gezgini. (Çözümler farklı türlerde birçok proje içerebilir; Ayrıntılar için bkz. [Projeler](r-projects-in-visual-studio.md) .
    - sol üst tarafta, `script.R` kaynak kodunu tüm Visual Studio düzenleme özellikleriyle düzenleyebileceğiniz yeni bir R dosyası ().
    - Sol alt tarafta, kodu etkileşimli olarak geliştirebileceğiniz ve test edebileceğiniz **R etkileşim** penceresidir.

> [!Note]
> **R etkileşim** penceresini herhangi bir proje açık olmadan ve farklı bir proje türü yüklendiğinde bile kullanabilirsiniz.   >    >  her zaman **R Etkileşim** Windows R araçları ' nı seçin.

## <a name="explore-the-interactive-window-and-intellisense"></a>Etkileşimli pencereyi ve IntelliSense 'i keşfet

1. Etkileşimli pencerenin çalışıp çalışmadığını test `3 + 4` edin ve sonucu görmek Için **yazın** :

    ![R Etkileşim pencere Visual Studio 2017 (VS2017)](media/getting-started-02-interactive1.png)

1. Biraz daha karmaşık bir şey girin `ds <- c(1.5, 6.7, 8.9) * 1:12` ve `ds` sonucu görmek için yazın:

    ![Visual Studio 'de R için ek etkileşimli örnek](media/getting-started-03-interactive2.png)

1. içine yazın `mean(ds)` ancak `m` `me` Visual Studio ıntellisense 'in otomatik tamamlama seçenekleri sağladığını unutmayın. İstediğiniz tamamlama listede seçildiğinde, eklemek için **Tab** tuşuna basın; Seçimi ok tuşları veya fare ile değiştirebilirsiniz.

    ![Kod girerken IntelliSense görünen](media/getting-started-04-intellisense1.png)

1. İşlemi tamamladıktan sonra `mean` , açma `(` parantezini yazın ve IntelliSense 'in işlev için satır içi yardım nasıl elde etmenizi aklınızda bulabilirsiniz:

    ![Bir işlev için yardım gösteren IntelliSense](media/getting-started-05-intellisense2.png)

1. `mean(ds)`Sonucu () görmek için satırı doldurun ve ENTER tuşuna basın `[1] 39.51667` .

1. Etkileşimli pencere, yardım 'la tümleşiktir, bu nedenle girildiğinde `?mean` Visual Studio **R yardım** penceresinde bu işlev için yardım görüntülenir. ayrıntılar için [Visual Studio için R Araçları yardımına](getting-started-help.md)bakın.

    ![Visual Studio R Yardım pencere](media/getting-started-06-help.png)

1. gibi bazı komutlar, `plot(1:100)` çıktı etkileşimli pencerede doğrudan görüntülenemediğinde Visual Studio yeni bir pencere açar:

    ![grafik işlev çizmesinin çıkışını görüntüleyen bir Visual Studio R çizim penceresinin ekran görüntüsü (1:100).](media/getting-started-07-plot-window.png)

Etkileşimli pencere Ayrıca geçmişinizi incelemenizi, çalışma alanlarını yüklemeyi ve kaydetmenizi, bir hata ayıklayıcıya iliştirmenizi ve Kopyala-Yapıştır kullanmak yerine kaynak kodu dosyalarıyla etkileşim kurmanızı sağlar. Ayrıntılar için bkz. [R etkileşim penceresiyle çalışma](interactive-repl-for-r-in-visual-studio.md) .

## <a name="experience-code-editing-features"></a>Deneyim kodu Düzenle özellikleri

Etkileşimli pencere ile kısa bir süre çalışmak, IntelliSense gibi kod Düzenleyicisi 'nde da çalışan temel düzenleme özelliklerini gösterir. Daha önce olduğu gibi aynı kodu girerseniz, aynı otomatik tamamlamayı ve IntelliSense istemlerini görürsünüz, ancak çıktıyı görmezsiniz.

İçinde kod yazma *. R* dosyası, tüm kodunuzu tek seferde görmenizi sağlar ve küçük değişiklikler yapmanızı kolaylaştırır ve sonra kodu etkileşimli pencerede çalıştırarak sonucu hızla görebilir. Bir projede istediğiniz kadar dosya da olabilir. Kod bir dosya içinde olduğunda, hata ayıklayıcıda adım adım (Bu makalenin ilerleyen kısımlarında ele alınmıştır) adımını da çalıştırabilirsiniz. Bu yetenekler, özellikle tüm ara sonuçları incelemek istediğinizde, hesaplama algoritmaları geliştirirken ve bir veya daha fazla veri kümesini işlemek için kod yazarken faydalıdır.

Örnek olarak, aşağıdaki adımlar [Merkezi Limit](https://en.wikipedia.org/wiki/Central_limit_theorem) (Vikipedi) için bir çok kod oluşturur. (Bu örnek, Paul Teetor tarafından *R tanıtım defterinden* uyarlanmıştır.)

1. `script.R`Düzenleyicide aşağıdaki kodu girin:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. Sonuçları hızlıca görmek için tüm kodu (**CTRL** + **A**) seçin ve ardından **CTRL** + **ENTER** tuşuna basın veya **etkileşimli olarak çalıştır**' ı seçin. Seçilen tüm kod, doğrudan yazdığınız gibi etkileşimli pencerede çalışır ve sonucu bir çizim penceresinde gösterir:

    ![bir Visual Studio R çizim penceresinin, bir popülasyon yoğunluğu grafiğini görüntüleyen ekran görüntüsü.](media/getting-started-08-plot1.png)

1. Tek bir çizgi için,  + Bu satırı etkileşimli pencerede çalıştırmak için dilediğiniz zaman CTRL **ENTER** tuşuna basmanız yeterlidir.

> [!Tip]
>  +   +   + Kodu hızlı bir şekilde çalıştırmak için düzenleme yapma ve CTRL + ENTER tuşlarına basma (ya da CTRL +**ENTER** tuşlarına basarak) stilini öğrenin. Bunun yapılması, aynı işlemler için fareyi kullanmaktan çok daha etkilidir.
>
> ayrıca, çizim penceresini Visual Studio çerçevesinin dışına sürükleyip bırakabilir ve daha sonra ekranda istediğiniz zaman yerleştirebilirsiniz. Daha sonra çizim penceresini istediğiniz boyutlara yeniden boyutlandırabilir ve sonra bir görüntüye veya PDF dosyasına kaydedebilirsiniz.

1. İkinci bir çizim eklemek için birkaç daha fazla kod satırı ekleyin:

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    lines(density(samp.means))
    ```

1. **CTRL** + **A** 'ya basın ve + kodu çalıştırmak için bir kez daha **yazın** ve aşağıdaki sonucu üretir:

    ![Visual Studio ikili çizim güncelleştirildi](media/getting-started-09-plot2.png)

1. Sorun ilk çizimin dikey ölçeklendirmeyi belirlediği, İkinci çizimin (ile `lines` ) sığmadığı bir sorundur. Bu sorunu düzeltmek için, `ylim` çağrıda parametresini ayarlamanız gerekir `plot` , ancak en fazla dikey değeri hesaplamak için kod eklememiz gerekir. Bu satırı etkileşimli pencerede yapmak, çağrılmadan önce kullanmak üzere kodu yeniden düzenlemeniz gerektiğinden kullanışlıdır `samp.means` `plot` . Ancak, bir kod dosyasında uygun düzenlemeleri kolayca yapabiliriz:

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

1. **CTRL** + **A** ve **CTRL tuşuna** bir + kez daha **girerek** sonucu görebilirsiniz:

    ![Visual Studio ikili çizim güncelleştirildi, doğru ölçeklendirildi](media/getting-started-10-plot3.png)

Düzenleyicide daha fazla yapabilirsiniz. Ayrıntılar için bkz. [R Code](editing-r-code-in-visual-studio.md), [IntelliSense](r-intellisense.md)ve [Code parçacıklarını](code-snippets-for-r.md)düzenleme.

## <a name="debug-your-code"></a>Kodunuzda hata ayıklama

Visual Studio anahtar güçlerinden biri, hata ayıklama kullanıcı arabiriminden biridir. RTVS, bu Strong Foundation üzerinde yapılar ve [değişken Gezgini](variable-explorer.md)gibi yenilikçi Kullanıcı arabirimini ekler. Burada, hata ayıklamaya yalnızca bir ilk göz atalım.

1. Başlamak için, **R araçları**  >  **oturum**  >  **sıfırlama** menü komutunu kullanarak yaptığınız her şeyi temizlemek için geçerli çalışma alanını sıfırlayın. Varsayılan olarak, etkileşimli pencerede yaptığınız her şey geçerli oturuma tahakkuk eder ve bu da hata ayıklayıcı tarafından da kullanılır. Oturumu sıfırlayarak, hata ayıklama oturumunun önceden varolan veriler olmadan başlamasını sağlar. Ancak **sıfırlama** komutu, *betiğinizi etkilemez. R* kaynak dosyası, yönetilen ve çalışma alanının dışında kaydedildiğinden.

1. Betiği ile *. R* dosyası önceki bölümde oluşturulur, giriş `pop <-` işaretini o satıra yerleştirip **F9** tuşuna basarak veya **hata ayıklama**  >  **kesme noktası geçişi** menü komutunu seçerek, ile başlayan satırda bir kesme noktası ayarlayın. Alternatif olarak, kırmızı kesme noktası noktasının göründüğü bu çizginin sol kenar boşluğuna (veya cilt payına) tıklayın:

    ![Düzenleyicide kesme noktası ayarlama](media/getting-started-11-debug1.png)

1. Komut dosyasındaki kodla hata ayıklayıcıyı başlatın *. R* araç çubuğunda **kaynak başlangıç dosyası** düğmesini seçip, **Hata Ayıkla**  >  **kaynak başlangıç dosyası** menü öğelerini seçerek veya **F5**'e basarak. Visual Studio, hata ayıklama moduna girer ve kodu çalıştırmaya başlar. Ancak, kesme noktasını ayarladığınız satırda durmaktadır:

    ![Visual Studio hata ayıklayıcısında kesme noktasında durdurma](media/getting-started-12-debug2.png)

1. hata ayıklama sırasında, Visual Studio kod satırlarınızın satıra göre nasıl ilerleyebilmesini sağlar. Ayrıca işlevleri de görebilir, bunların üzerinde adımla veya onları çağıran bağlamda dışına taşıyabilirsiniz. Diğer kişilerle birlikte bu yetenekler, **hata ayıklama** menüsünde, düzenleyicide sağ tıklama bağlam menüsünde ve hata ayıklama araç çubuğunda bulunabilir:

    ![Visual Studio hata ayıklama araç çubuğu](media/getting-started-13-debug3.png)

1. Bir kesme noktasında durdurulduğunda, değişkenlerin değerlerini inceleyebilirsiniz. Visual Studio içindeki **oto** penceresini bulun ve en alttaki **yereller** adlı üst kısımdaki sekmeyi seçin. **Yereller** penceresi, programın geçerli noktasındaki yerel değişkenleri gösterir. Daha önce ayarlanan kesme noktasında durdurulmuşsa, `pop` değişkenin henüz tanımlı olmadığını görürsünüz. Şimdi **hata ayıklama**  >  **adımı** komutunu (**F10**) kullanın ve görüntülenecek değeri görürsünüz `pop` :

    ![Visual Studio 'teki Yereller penceresi](media/getting-started-14-debug4.png)

1. Küresel kapsam ve paket kapsamları dahil olmak üzere farklı kapsamlardaki değişkenleri incelemek için [değişken Gezgini](variable-explorer.md)kullanın. Değişken Gezgini Ayrıca, sıralanabilir sütunlar içeren bir tablo görünümüne geçiş yapma ve bir CSV dosyasına veri aktarma olanağı sağlar.

    ![Değişken Gezgini genişletilmiş görünümü](media/variable-explorer-expanded-results.png)

1. Programa göre program satırı ile çalışmaya devam edebilir veya tamamlanarak (veya sonraki kesme noktasında) çalıştırmak için **devam et** (**F5**) seçeneğini belirleyebilirsiniz.

Daha ayrıntılı bilgi için bkz. [hata ayıklama](debugging-r-in-visual-studio.md) ve [değişken Gezgini](variable-explorer.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu kılavuzda, Visual Studio ' de etkileşimli pencereyi, kod düzenlemesini ve hata ayıklamayı kullanarak R projelerinin temel bilgilerini öğrendiniz. Daha fazla yetenek araştırmaya devam etmek için, içindekiler tablosunda gösterilen aşağıdaki makalelere ve makalelere bakın:

- [Örnek projeler](getting-started-samples.md)
- [Kod düzenleniyor](editing-r-code-in-visual-studio.md)
- [Hata Ayıklama](debugging-r-in-visual-studio.md)
- [Çalışma alanları](r-workspaces-in-visual-studio.md)
- [Verileri görselleştirme](visualizing-data-with-r-in-visual-studio.md)
