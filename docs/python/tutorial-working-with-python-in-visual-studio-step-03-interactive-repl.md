---
title: Python in Visual Studio öğreticisi 3. adım, etkileşimli REPL
titleSuffix: ''
description: Python Etkileşimli REPL penceresini kapsayan temel Python Visual Studio adım 3. adım.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7d2d8684759b56b577402840ee4a748e618e6a39
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076132"
---
# <a name="step-3-use-the-interactive-repl-window"></a>3. Adım: Etkileşimli REPL penceresini kullanma

**Önceki adım: [Kod yazma ve çalıştırma](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

Python Visual Studio **Etkileşimli** penceresi, normal düzenleme-derleme-hata ayıklama döngüsünü büyük ölçüde kısaltan zengin bir okuma-değerlendirme-yazdırma döngüsü (REPL) deneyimi sağlar. Etkileşimli **pencere,** Python komut satırı repl deneyiminin tüm özelliklerini sağlar. Ayrıca, komut satırıyla çok zahmetli olan Visual Studio düzenleyicide kaynak dosyalarla kod değişimini çok kolaylaştırır.

> [!NOTE]
> REPL ile ilgili sorunlar için ve paketlerinin yüklü olduğundan emin olun ve paketleri yükleme yardımı `ipython` `ipykernel` için [bkz. Python ortamları paketleri sekmesi.](./python-environments-window-tab-reference.md#packages-tab)

1. **Çözüm Gezgini'da** projenin Python ortamına sağ tıklayarak (önceki grafikte gösterilen **Python 3.6 (32 bit) gibi)** ve Etkileşimli Pencere Aç'ı seçerek Etkileşimli pencereyi **açın.**  Alternatif olarak ana **menüden** Diğer  >  **Windows**  >  **Python Interactive Windows'ı** Visual Studio seçebilirsiniz.

1. Etkileşimli **pencere,** standart Python REPL istemiyle **>>>** düzenleyicinin altında açılır. Ortam **açılan** listesi, üzerinde çalışacak belirli bir yorumlayıcıyı seçmenize olanak sağlar. Çoğu zaman etkileşimli pencereyi daha **büyük hale** de almak ve bunu yapmak için iki pencere arasında ayırıcıyı sürükleyebilirsiniz:

    ![Python etkileşimli penceresi ve yeniden boyutlandırmak için sürükleme](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Kenarlık ayırıcılarını sürükleyerek Visual Studio tüm pencereleri yeniden boyutlandırabilirsiniz. Ayrıca, pencereleri çerçevenin içinde istediğiniz Visual Studio sürükleyip yeniden düzenleyebilirsiniz. Tüm ayrıntılar için [bkz. Pencere düzenlerini özelleştirme.](../ide/customizing-window-layouts-in-visual-studio.md)

1. Hemen sonuçları görmek için gibi `print("Hello, Visual Studio")` ve ifadeleri `123/456` gibi birkaç deyim girin:

    ![Python etkileşimli penceresi hemen sonuçları](media/vs-getting-started-python-12-interactive2.png)

1. İşlev tanımı gibi çok satırlı bir deyim  yazmaya başlanırken Etkileşimli pencerede Python'ın devam eden **satırlar** için komut satırı REPL'den farklı olarak otomatik girintileme sağlayan ... istemi gösterilir. Yeni bir ... satırı **eklemek** için tuşuna `Shift+Enter` basın:

    ![Deyimin devamlılığı ile Python etkileşimli penceresi](media/vs-getting-started-python-13-interactive3.png)

1. Etkileşimli **pencere,** girdiğiniz her şeyin tam geçmişini sağlar ve çok satırlı geçmiş öğeleriyle komut satırı REPL'sinde iyiler. Örneğin, işlevin tanımının tamamını tek bir birim olarak kolayca geri çağırabilir ve işlevi satır satır yeniden oluşturmak yerine adını `f` `make_double` kolayca olarak değiştirebilirsiniz.

1. Visual Studio bir düzenleyici penceresinden Etkileşimli pencereye birden çok kod satırı **gönderebilirsiniz.** Bu özellik, bir kaynak dosyada kodu korumanız ve bunun belirli bölümlerini Etkileşimli pencereye kolayca **göndermenizi** sağlar. Daha sonra bu tür kod parçalarıyla programın tamamını çalıştırmak zorunda kalmadan hızlı REPL ortamında çalışabilirsiniz. Bu özelliği görmek için önce PythonApplication1.py `for` *dosyasındaki* döngüyü aşağıdakiyle değiştirin:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. `import` `from` .py dosyasındaki `make_dot_string` , ve işlev *deyimlerini* seçin. Seçili metne sağ tıklayın ve Etkileşimliye **Gönder'i** seçin (veya Ctrl Enter **tuşuna** + **basın).** Kod parçası hemen Etkileşimli pencereye **yapıştırıldı ve** çalıştırıldı. Kod bir işlev tanımladı olduğundan, birkaç kez çağırarak bu işlevi hızlıca test etmek için:

    ![Etkileşimli pencereye kod gönderme ve test etme](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > Düzenleyicide **Ctrl** Enter tuşlarına basın ve seçim olmadan etkileşimli pencerede geçerli kod satırı çalıştırılır ve giriş tuşu otomatik +  olarak bir sonraki satıra  eklenir.  Bu özellik sayesinde, **Ctrl** Enter tuşlarına tekrar tekrar basarak yalnızca Python komut satırıyla kodunda adım adım geçiş yapmak için +  kullanışlı bir yol sağlar. Ayrıca, hata ayıklayıcıyı çalıştırmadan ve programınızı en baştan başlatmadan kodunuzu adım çalıştırmanıza da olanak sağlar.

1. Ayrıca, Python komut satırı REPL  ile yapmak zordur, aşağıdaki kod parçacığı gibi herhangi bir kaynaktan Etkileşimli pencereye birden çok kod satırı kopyalayıp yapıştırabilirsiniz. Yapıştırıldıklarında **Etkileşimli** pencere, kodu şu şekilde çalıştırır:

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Etkileşimli Gönderme kullanarak birden çok kod satırı yapıştırma](media/vs-getting-started-python-15-interactive5.png)

1. Gördüğünüz gibi bu kod iyi çalışıyor ancak çıkışı çok ilham verici değil. Döngüde farklı bir adım `for` değeri daha fazla kosinüs dalgası gösterir. Neyse ki döngülerin tamamı tek bir birim olarak REPL geçmişinde olduğundan geri dönüp istediğiniz değişiklikleri yapmak ve ardından işlevi yeniden test etmek `for` kolaydır. İlk olarak döngüyü geri çağıracak şekilde yukarı oka `for` basın. Ardından kodda gezinmeye başlamak için sol veya sağ oklara basın (siz bunu yapmayana kadar, yukarı ve aşağı oklar geçmiş boyunca döngüye devam eder). 'a gidin ve belirtimi `range` olarak `range(0, 360, 12)` değiştirebilirsiniz. Ardından **deyimin tamamını yeniden** çalıştırmak için Ctrl Enter (kodun herhangi +  bir yerinde) tuşlarına basın:

    ![Etkileşimli pencerede önceki deyimi düzenleme](media/vs-getting-started-python-16-interactive6.png)

1. En çok istediğiniz değeri bulana kadar farklı adım ayarlarıyla deneme yapmak için işlemi tekrarlayın. Aralığı uzatarak da dalgayı yinelersiniz, örneğin `range(0, 1800, 12)` .

1. Etkileşimli pencerede yazdığın koddan **memnunsanız** seçin. Ardından, koda sağ tıklayın ve Kodu Kopyala **(** **Ctrl Shift** C ) + **öğesini** + **seçin.** Son olarak, seçilen kodu düzenleyiciye yapıştırın. Bu özel özellik Visual Studio ve istemlerinin otomatik olarak çıkışları `>>>` `...` atlar. Örneğin, aşağıdaki görüntüde, **istemler ve çıkış** içeren bir seçimde Kod Kopyala komutunun kullanımı gösterilmiştir:

    ![Etkileşimli penceresi istemleri ve çıkışı olan bir seçimde kod kopyalama komutunu seçin](media/vs-getting-started-python-17-interactive7.png)

    Düzenleyiciye yapıştırarak yalnızca kodu alırsiniz:

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    İstemler ve çıkışlar da dahil olmak üzere **Etkileşimli** pencerenin tam içeriğini kopyalamak için standart Kopyala komutunu **kullanın.**

1. Az önce etkileşimli pencerenin hızlı REPL ortamını  kullanarak küçük bir kod parçasının ayrıntılarının üzerinde çalışmak ve ardından bu kodu projenizin kaynak dosyasına rahatça eklediniz. Şimdi kodu **Ctrl** F5 (veya Hata Ayıklama Olmadan Başlat) ile yeniden +    >  çalıştırarak istediğiniz sonuçları tam olarak görüyorsunuz.

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Hata ayıklayıcıda kod çalıştırma](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Daha derine gitme

- [Etkileşimli penceresi](python-interactive-repl-in-visual-studio.md)
- [IPython REPL kullanma](interactive-repl-ipython.md)