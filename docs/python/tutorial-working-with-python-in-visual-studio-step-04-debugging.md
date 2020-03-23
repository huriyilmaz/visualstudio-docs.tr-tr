---
title: Python Visual Studio öğretici adım 4, hata ayıklama
titleSuffix: ''
description: Visual Studio'daki Python özelliklerinin temel walkthrough'unun 4.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3f6464986cb94ffa3ab3cc9264ab818112046ea9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "63002839"
---
# <a name="step-4-run-code-in-the-debugger"></a>Adım 4: Hata ayıklayıcıda kodu çalıştırma

**Önceki adım: [İnteraktif REPL penceresini kullanma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)**

Visual Studio, projeleri yönetme, zengin bir düzenleme deneyimi ve **Etkileşimli** pencere sağlamanın yanı sıra Python kodu için tam özellikli hata ayıklama sağlar. Hata ayıklayıcıda, bir döngünün her yinelemesi de dahil olmak üzere kodunuzu adım adım çalıştırabilirsiniz. Belirli koşullar doğru olduğunda da programı duraklatabilirsiniz. Program hata ayıklama da duraklatılmış herhangi bir noktada, tüm program durumunu inceleyebilir ve değişkenlerin değerini değiştirebilirsiniz. Bu tür eylemler program hataları nın izlenmesi için gereklidir ve aynı zamanda tam program akışını dikkatle izlemek için çok yararlı yardımcılar sağlar.

1. *PythonApplication1.py* dosyasındaki kodu aşağıdakilerle değiştirin. Kodun bu varyasyonu, hata ayıklayıcıdaki ayrık adımlarını inceleyebilmeniz için genişletir. `make_dot_string` Ayrıca döngüyü `for` bir `main` işleve yerleştirir ve bu işlevi çağırarak açıkça çalıştırAbilir:

    ```python
    from math import cos, radians

    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        rad = radians(x)                             # cos works with radians
        numspaces = int(20 * cos(radians(x)) + 20)   # scale to 0-40 spaces
        st = ' ' * numspaces + 'o'                   # place 'o' after the spaces
        return st

    def main():
        for i in range(0, 1800, 12):
            s = make_dot_string(i)
            print(s)

    main()
    ```

1. **F5** tuşuna basarak veya **Hata** > **Ayıklama Hata Ayıklama** menüsü komutunu seçerek kodun düzgün çalışıp çalışmadığını denetleyin. Bu komut hata ayıklayıcıda kodu çalıştırır, ancak çalışırken programı duraklatmak için hiçbir şey yapmadığınız için, birkaç yineleme için bir dalga deseni yazdırır. Çıkış penceresini kapatmak için herhangi bir tuşa basın.

    > [!Tip]
    > Program tamamlandığında çıkış penceresini otomatik olarak kapatmak için **Araçlar** > **Seçenekleri** menü komutunu seçin, **Python** düğümünü genişletin, **Hata Ayıklama'yı**seçin ve işlem normal **çıktığınızda giriş için Bekle**seçeneğini temizleyin:
    >
    > ![Normal program çıkışında çıktı penceresini kapatmak için python hata ayıklama seçeneği](media/vs-getting-started-python-22-debugging5.png)

1. `for` Gri kenar boşluğuna bu satırla bir kez tıklayarak veya bu satıra ayırarak ve **Hata Ayıklama** > **Kesme Noktası** komutunu **(F9)** kullanarak deyimüzerinde bir kesme noktası ayarlayın. Kesme noktasını belirtmek için gri kenar boşluğunda kırmızı bir nokta belirir (aşağıdaki okunda belirtildiği gibi):

    ![Kesme noktası ayarlama](media/vs-getting-started-python-18-debugging1.png)

1. Hata ayıklayıcıyı **(F5)** yeniden başlatın ve kodu çalıştırmanın bu kesme noktasıyla satırda durduğunu görün. Burada çağrı yığınını inceleyebilir ve değişkenleri inceleyebilirsiniz. Kapsam içi değişkenler tanımlandıklarında **Otomatik ler** penceresinde görünür; Visual Studio'nun geçerli kapsamda bulduğu tüm değişkenleri (işlevler dahil) tanımlanmadan önce göstermek için bu pencerenin altındaki **Yerel görünüme** de geçebilirsiniz:

    ![Python için Breakpoint UI deneyimi](media/vs-getting-started-python-19-debugging2b.png)

1. Visual Studio penceresinin üst kısmındaki hata ayıklama araç çubuğunu (aşağıda gösterilmiştir) gözlemleyin. Bu araç çubuğu en yaygın hata ayıklama komutlarına **(Hata Ayıklama** menüsünde de bulunabilir) hızlı erişim sağlar:

    ![Temel hata ayıklama araç çubuğu düğmeleri](media/vs-getting-started-python-20-debugging3.png)

    Soldan sağa düğmeler aşağıdaki gibi:
    - **Continue** (**F5**) programı bir sonraki kesme noktasına veya program tamamlanına kadar çalıştırAr.
    - **Break All** **(Ctrl**+**Alt**+**Break)** uzun süren bir programı duraklatır.
    - **Hata Ayıklamayı Durdurun** **(Shift**+**F5)** programı olduğu her yerde durdurur ve hata ayıklamadan çıkar.
    - **Yeniden Başlatma** (**Ctrl**+**Shift**+**F5**) programı olduğu her yerde durdurur ve hata ayıklamada baştan başlatır.
    - **Sonraki Bildirimi Göster** (**Alt**+**Num** **&#42;**) çalıştırmak için bir sonraki kod satırına geçer. Bu, hata ayıklama oturumu sırasında kodunuzda gezinirken ve hata ayıklayıcının duraklatılmış olduğu noktaya hızla dönmek istediğinizde yararlıdır.
    - **Step Into** (**F11**) çağrılan işlevlere girerek bir sonraki kod satırını çalıştırıyor.
    - **Step Over** **(F10)** çağrılan işlevlere girmeden bir sonraki kod satırını çalıştırın.
    - **Step Out** (**Shift**+**F11**) geçerli işlevin geri kalanını çalıştırın ve arama kodunda duraklar.

1. Adım `for` **Adım'ı**kullanarak deyimin üzerine geçin. *Hata* ayıklayıcı, herhangi bir işlev çağrıları da dahil olmak üzere geçerli kod satırını çalıştırır ve ardından hemen yeniden duraklar anlamına gelir. Değişkenin `i` artık Yerel ler ve **Otomatikler** pencerelerinde nasıl tanımlandığına dikkat edin. **Autos**

1. Çağıran `make_dot_string` ve duraklatan bir sonraki kod satırına geçin. **Buraya adım** özellikle hata ayıklama nın tümünü çalıştırdığı `make_dot_string` ve döndüğünde duraklattığı anlamına gelir. Hata ayıklama, ayrı bir kesme noktası yoksa bu işlevin içinde durmaz.

1. Kodu birkaç kez daha aşmaya devam edin ve **Yerel veya** Otomatik **ler** penceresindeki değerlerin nasıl değiştiğini gözlemleyin.

1. Yerel **veya** **Otomatikler** penceresinde, değeri veya `s` değişkenleri için `i` **Değer** sütununa çift tıklayın. Değişiklikleri uygulamak için **Enter** tuşuna basın veya bu değerin dışına tıklayın.

1. **Adım Adım'ı**kullanarak kodda adım atmaya devam edin. **Adım Adım,** hata ayıklamanın hata ayıklama bilgisi olan herhangi bir işlev `make_dot_string`çağrısının içine girdiği anlamına gelir, örneğin . İçeri `make_dot_string` girdikten sonra yerel değişkenlerini inceleyebilir ve kodundan özel olarak geçebilirsiniz.

1. **Step Into** ile adım atmaya devam edin `make_dot_string`ve bir sonraki adımın `for` `s` değişkendeki yeni dönüş değeriyle döngüye döndüğünü fark edin. İfadeye `print` tekrar adım attığınızda, Adım `print` **Adım'ın** bu işleve girmediğini unutmayın. Bunun nedeni `print` Python'da yazılmaması, Python çalışma zamanı içinde yerel kod olmasıdır.

1. `make_dot_string`Adım **Adım'ı** kullanmaya devam edin. Sonra **Step Out'u** kullanın ve `for` döngüye geri döndüğünüzde dikkat edin. **Adım Dışarı**ile hata ayıklayıcı işlevin geri kalanını çalıştırır ve ardından arama kodunda otomatik olarak duraklar. Bu, hata ayıklamak istediğiniz, ancak geri kalanı için adım gerekmez ve arama kodunda açık bir kesme noktası ayarlamak istemiyorum uzun bir işlevin bir bölümünü adım attığınızda çok yararlıdır.

1. Bir sonraki kesme noktasına ulaşılana kadar programı çalıştırmaya devam etmek için **Continue** **(F5)** kullanın. Döngüde `for` bir kırılma noktası olduğu için, bir sonraki yinelemede kırılırsınız.

1. Bir döngünün yüzlerce yinelemesini aşmak sıkıcı olabilir, bu nedenle Visual Studio bir kesme noktasına bir *koşul* eklemenizi sağlar. Hata ayıklama, yalnızca durum karşılandığında, programı kesme noktasında duraklatır. Örneğin, ekstredeki `for` kesme noktası olan bir koşulu, yalnızca değeri 1600'ü `i` aştığında duraklatacak şekilde kullanabilirsiniz. Bu koşulu ayarlamak için kırmızı kesme noktası noktasını sağ tıklatın ve **Koşullar** **(Alt**+**F9** > **C)** seçin. Görünen **Kesme Noktası Ayarları** açılır penceresinde `i > 1600` ifade olarak girin ve **Kapat'ı**seçin. Devam etmek ve programın bir sonraki moladan önce birçok yineleme çalıştırdığını gözlemlemek için **F5** tuşuna basın.

    ![Kesme noktası koşulu ayarlama](media/vs-getting-started-python-21-debugging4.png)

1. Programı tamamlamaya çalıştırmak için, kesme noktasını sağ tıklatarak ve **devre dışı atmayı** seçerek kesme noktasını devre dışı bıraktı **(Ctrl**+**F9).** Ardından programı çalıştırmak için **Continue** (veya **F5**tuşuna basın) seçeneğini belirleyin. Program sona erdiğinde, Visual Studio hata ayıklama oturumunu durdurur ve düzenleme moduna geri döner. Noktasını tıklatarak kesme noktasını da silebileceğinizi, ancak bu durumun ayarladığınız tüm koşulları da silebilirsiniz.

> [!Tip]
> Python yorumlayıcısının başlatılamaması gibi bazı durumlarda, çıkış penceresi yalnızca kısa bir süre görüntülenebilir ve herhangi bir hata iletisini görme şansı vermeden otomatik olarak kapanabilir. Bu durumda, **Çözüm Gezgini'ndeki**projeyi sağ tıklatın, **Özellikler'i** `-i` seçin, Hata **Ayıklama** sekmesini seçin ve ardından **Yorumlayıcı Bağımsız Değişkenler** alanına ekleyin. Bu bağımsız değişken, bir program tamamlandıktan sonra yorumlayıcının etkileşimli moda geçmesine neden olur ve böylece çıkmak için **Ctrl**+**Z** > **Girin'i** girene kadar pencereyi açık tutar.

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Python ortamınıza paketleri yükleme](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)

## <a name="go-deeper"></a>Daha derine inin

- [Hata ayıklama](debugging-python-in-visual-studio.md)
- [Visual Studio'da hata ayıklama,](../debugger/debugger-feature-tour.md) Visual Studio'nun hata ayıklama özelliklerinin tam dokümantasyonuna sahiptir.
