---
title: Python Visual Studio öğretici adım 3, interaktif REPL
titleSuffix: ''
description: Python Interactive REPL penceresini kapsayan Visual Studio'daki Python yeteneklerinin temel izninin 3.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 51723d22cd72de8333fca9b83c1643117a7413e5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "72986221"
---
# <a name="step-3-use-the-interactive-repl-window"></a>Adım 3: İnteraktif REPL penceresini kullanma

**Önceki adım: [Kod yazma ve çalıştırma](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

Python için Visual Studio **Interactive** penceresi, olağan edit-yap-hata ayıklama döngüsünü büyük ölçüde kısaltan zengin bir okuma-değerlendirme-yazdırma-döngü (REPL) deneyimi sağlar. **Etkileşimli** pencere Python komut satırının REPL deneyiminin tüm özelliklerini sağlar. Ayrıca, visual studio düzenleyicisindeki kaynak dosyalarla kod alışverişini de kolaylaştırır, aksi takdirde komut satırı ile hantaldır.

> [!NOTE]
> REPL ile ilgili sorunlar için, paketlerin yüklü olduğundan `ipython` ve `ipykernel` paket yüklemeye yardımcı olun, Python [ortamları paketleri sekmesine](/en-us/visualstudio/python/python-environments-window-tab-reference#packages-tab)bakın.

1. **Solution Explorer'da** (daha önceki bir grafikte gösterilen **Python 3.6 (32 bit)** gibi) projenin Python ortamını sağ tıklatarak ve Etkileşimli Pencereaç'ı açarak **Etkileşimli** **pencereyi**açın. Ana Visual Studio menüsünden**Diğer Windows** > **Python Etkileşimli Windows'u** **Görüntüle'yi** > dönüşümlü olarak seçebilirsiniz.

1. **Etkileşimli** pencere standart **>>>** Python REPL istemi ile düzenleyicinin altında açılır. **Ortam** açılır listesi, çalışmak için belirli bir yorumlayıcı seçmenize olanak tanır. Çoğu zaman, ayırıcıyı iki pencere arasında sürükleyerek yapabileceğiniz **Etkileşimli** pencereyi daha büyük yapmak da istersiniz:

    ![Python etkileşimli pencere ve yeniden boyutlandırma sürükleme](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Kenarlık ayırıcıları sürükleyerek Visual Studio'daki tüm pencereleri yeniden boyutlandırabilirsiniz. Ayrıca, pencereleri Visual Studio çerçevesinden bağımsız olarak sürükleyebilir ve çerçeve içinde istediğiniz gibi yeniden düzenleyebilirsiniz. Tüm ayrıntılar için [bkz.](../ide/customizing-window-layouts-in-visual-studio.md)

1. Hemen sonuç görmek `print("Hello, Visual Studio")` gibi `123/456` birkaç ifade ve ifadeler girin:

    ![Python etkileşimli pencere anında sonuçlar](media/vs-getting-started-python-12-interactive2.png)

1. Bir işlev tanımı gibi çok satırlı bir deyim yazmaya başladığınızda, **Etkileşimli** pencere Python'un **...** komut satırı REPL'nin aksine otomatik girintisi sağlayan devam eden satırlar için istemini gösterir:

    ![Deyim devamı ile Python etkileşimli pencere](media/vs-getting-started-python-13-interactive3.png)

1. **Etkileşimli** pencere, girdiğiniz her şeyin tam bir geçmişini sağlar ve çok satırlı geçmiş öğeleriyle komut satırı REPL'yi geliştirir. Örneğin, işlevin tüm tanımını `f` tek bir birim olarak kolayca hatırlayabilir `make_double`ve işlevi satır satır yeniden oluşturmak yerine adı kolayca "olarak" olarak değiştirebilirsiniz.

1. Visual Studio, düzenleyici penceresinden **Etkileşimli** pencereye birden çok kod satırı gönderebilir. Bu özellik, bir kaynak dosyada kodu korumanızı ve belirli bölümlerini **Etkileşimli** pencereye kolayca göndermenizi sağlar. Daha sonra tüm programı çalıştırmak zorunda yerine hızlı REPL ortamında bu tür kod parçaları ile çalışabilirsiniz. Bu özelliği görmek için, `for` önce *PythonApplication1.py* dosyasındaki döngüyü aşağıdakilerle değiştirin:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. *.py* `from`dosyasındaki `make_dot_string` `import`, ve işlev ifadelerini sağ tıklatın ve **Etkileşimli'ye Gönder'i** seçin (veya **Ctrl**+**Enter**tuşuna basın). Kod parçası hemen **Etkileşimli** pencereye yapıştırılır ve çalıştırılır. Kod bir işlev tanımladığı için, bu işlevi birkaç kez arayarak hızlı bir şekilde sınayabilirsiniz:

    ![Etkileşimli pencereye kod gönderme ve test etme](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > **Ctrl**+**Enter'u** seçiş *im olmadan* yaziide kullanımını kullanmak **Interactive** penceresindeki geçerli kod satırını çerler ve caret' i otomatik olarak bir sonraki satıra yerleşdir. Bu özellik sayesinde **Ctrl**+**Enter** tuşuna tekrar tekrar basarak kodunuzda yalnızca Python komut satırı ile mümkün olmayan bir adım atmanın uygun bir yolunu sağlar. Ayrıca hata ayıklayıcı çalıştırmadan ve mutlaka başından programınızı başlatmadan kodunuzu adım sağlar.

1. Ayrıca, Python komut satırı REPL ile yapmak zor olan aşağıdaki parçacık gibi herhangi bir kaynaktan **Etkileşimli** pencereye birden çok kod satırı kopyalayıp yapıştırabilirsiniz. Yapıştırıldığında, **Etkileşimli** pencere bu kodu siz yazmışsınız gibi çalıştırılır:

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Gönderme Etkileşimli'yi kullanarak birden çok kod satırı yapıştırma](media/vs-getting-started-python-15-interactive5.png)

1. Gördüğünüz gibi, bu kod iyi çalışıyor ama çıktısı çok ilham verici değil. `for` Döngüdeki farklı bir adım değeri daha fazla kosinüs dalgasını gösterir. Neyse ki, `for` tüm döngü tek bir birim olarak REPL geçmişinde olduğundan, geri dönmek ve istediğiniz değişiklikleri yapmak ve sonra işlevi yeniden test etmek kolaydır. Döngüyü hatırlamak için yukarı `for` oktuşuna basın. Ardından kodda gezinmeye başlamak için sol veya sağ oklara basın (bunu yaptığınızda yukarı ve aşağı oklar tarih boyunca döngüye devam eder). Gidin ve belirtimi `range(0, 360, 12)`' yi ' olarak değiştirin `range` Ardından tüm ifadeyi yeniden çalıştırmak için **Ctrl**+**Enter** tuşuna basın (kodun herhangi bir yerinde)

    ![Etkileşimli pencerede önceki bir ifadeyi düzenleme](media/vs-getting-started-python-16-interactive6.png)

1. En beğendiğiniz değeri bulana kadar farklı adım ayarlarını denemek için işlemi yineleyin. Ayrıca, örneğin aralığı uzatarak dalgayı `range(0, 1800, 12)`tekrarlayabilirsiniz.

1. **İnteraktif** pencerede yazdığınız koddan memnun olduğunuzda, kodu seçin, Sağ tıklayın ve **Kopya Kodu** 'nu **(Ctrl**+**Shift**+**C)** seçin ve ardından düzenleyiciye yapıştırın. Visual Studio'nun bu özelliğinin herhangi bir çıktıyı ve `>>>` `...` istemleri otomatik olarak nasıl atlayış ettiğine dikkat edin. Örneğin, aşağıdaki resim, istemleri ve çıktıyı içeren bir seçimde **Kopya Kodu** komutunu kullanarak gösterilmektedir:

    ![İstemleri ve çıktıları olan bir seçimde etkileşimli pencere kopyalama kodu komutu](media/vs-getting-started-python-17-interactive7.png)

    Editöre yapıştırdığınızda, yalnızca kodu alırsınız:

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    İstemler ve çıktı lar da dahil olmak üzere **Etkileşimli** pencerenin tam içeriğini kopyalamak istiyorsanız, standart **Kopyala** komutunu kullanmanız gereken bir şey.

1. Az önce yaptığınız şey, küçük bir kod parçasının ayrıntılarını çözmek için **Etkileşimli** pencerenin hızlı REPL ortamını kullanmak, ardından bu kodu projenizin kaynak dosyasına uygun bir şekilde eklediniz. Şimdi **kodu Ctrl**+**F5** (veya**Hata Ayıklama olmadan**Hata >  **Ayıklama)** ile yeniden çalıştırdığınızda, tam olarak istediğiniz sonuçları görürsünüz.

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Hata ayıklayıcıda kodu çalıştırma](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Daha derine inin

- [Etkileşimli pencereyi kullanma](python-interactive-repl-in-visual-studio.md)
- [IPython REPL kullanın](interactive-repl-ipython.md)
