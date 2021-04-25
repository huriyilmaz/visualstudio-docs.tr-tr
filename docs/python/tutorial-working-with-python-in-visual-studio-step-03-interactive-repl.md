---
title: Visual Studio 'da Python öğretici adım 3, etkileşimli REPL
titleSuffix: ''
description: Python etkileşimli REPL penceresini kapsayan, Visual Studio 'da Python özelliklerine yönelik temel bir izlenecek adım 3.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e82073b77231f84452ba51402f407904142bbf8e
ms.sourcegitcommit: 925db7adb9cb554b081c7e727d09680d4863feed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2021
ms.locfileid: "107941103"
---
# <a name="step-3-use-the-interactive-repl-window"></a>3. Adım: etkileşimli REPL penceresini kullanma

**Önceki adım: [kodu yazma ve çalıştırma](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

Python için Visual Studio **etkileşimli** penceresi, olağan düzenleme-oluşturma-hata ayıklama döngüsünü büyük ölçüde kısaltan bir zengin okuma-değerlendirme-yazdırma döngüsü (REPL) deneyimi sağlar. **Etkileşimli** pencere, Python komut satırının REPL deneyiminin tüm yeteneklerini sağlar. Ayrıca, Visual Studio düzenleyicisinde kaynak dosyalarla birlikte kod alışverişi yapmak çok kolay hale gelir. Bu, başka bir deyişle, komut satırı ile biraz daha fazla.

> [!NOTE]
> REPL ile ilgili sorunlar için, `ipython` ve `ipykernel` paketlerinin yüklü olduğundan ve paketlerin yüklenmesiyle ilgili yardım için bkz. [Python ortamları paketleri sekmesi](./python-environments-window-tab-reference.md#packages-tab).

1. **Çözüm Gezgini** (önceki bir grafikte gösterilen **python 3,6 (32-bit)** gibi) ve **etkileşimli pencereyi aç** seçeneğini belirleyerek, projenin Python ortamına sağ tıklayıp **etkileşimli** pencereyi açın. Alternatif olarak   >  ,**diğer Windows**  >  **Python etkileşimli pencerelerini** ana Visual Studio menüsünden görüntüle ' yi seçebilirsiniz.

1. **Etkileşimli** pencere, standart Python REPL istemiyle birlikte düzenleyicinin altında açılır **>>>** . **Ortam** açılan listesi, ile çalışmak için belirli bir yorumlayıcı seçmenize olanak sağlar. Ayrıca, iki pencere arasında ayırıcıyı sürükleyerek yapabileceğiniz **etkileşimli** pencereyi daha büyük hale getirmek isteyebilirsiniz:

    ![Python etkileşimli penceresi ve yeniden boyutlandırmak için sürükleme](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Bordering ayırıcılarını sürükleyerek Visual Studio 'daki tüm pencereleri yeniden boyutlandırabilirsiniz. Ayrıca, Windows 'u Visual Studio çerçevesindeki bağımsız olarak sürükleyebilir ve çerçeve içinde istediğiniz gibi yeniden düzenleyebilirsiniz. Tüm ayrıntılar için bkz. [pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md).

1. `print("Hello, Visual Studio")`Hemen sonuçları görmek için gibi birkaç ifadeyi ve ifadesini girin `123/456` :

    ![Python etkileşimli penceresi anlık sonuçları](media/vs-getting-started-python-12-interactive2.png)

1. Bir işlev tanımı gibi çok satırlı bir ifade yazmaya başladığınızda **etkileşimli** pencere, Python 'un **..** . satırına devam etmek için komut satırı REPL 'un aksine otomatik girintileme sağlar. Yeni bir **...** satırı eklemek için şunu basın `Shift+Enter` :

    ![Deyimle devam eden Python etkileşimli penceresi](media/vs-getting-started-python-13-interactive3.png)

1. **Etkileşimli** pencere, girdiğiniz her şeyin tam bir geçmişini sağlar ve çok satırlı geçmiş öğeleriyle komut satırı REPL üzerinde geliştirilir. Örneğin, işlevin tüm tanımını `f` tek bir birim olarak kolayca geri alabilir ve `make_double` işlev satırını satıra göre yeniden oluşturmak yerine adı kolayca olarak değiştirebilirsiniz.

1. Visual Studio, bir düzenleyici penceresinden **etkileşimli** pencereye birden çok satır kodu gönderebilir. Bu özellik, kodu kaynak dosyada korumanıza ve **etkileşimli** pencereye kolayca seçim parçalarını gönderemenize olanak tanır. Daha sonra, tüm programı çalıştırmak yerine hızlı REPL ortamında bu kod parçaları ile çalışabilirsiniz. Bu özelliği görmek için önce `for` *PythonApplication1.py* dosyasındaki döngüyü aşağıdaki kodla değiştirin:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. `import` `from` `make_dot_string` *. Kopyala* dosyasındaki, ve işlev deyimlerini seçin. Seçili metne sağ tıklayın ve **etkileşimli gönder** ' i seçin (veya **CTRL** + **ENTER** tuşuna basın). Kod parçası hemen **etkileşimli** pencereye yapıştırılır ve çalışır. Kod bir işlevi tanımladığından, bu işlevi birkaç kez çağırarak hızlıca test edebilirsiniz:

    ![Etkileşimli pencereye kod gönderme ve test etme](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    >  + Bir seçim *olmadan* düzenleyicide CTRL **ENTER** kullanılması, **etkileşimli** pencerede geçerli kod satırını çalıştırır ve giriş işaretini bir sonraki satıra otomatik olarak koyar. Bu özellikle, **CTRL** tuşuna basmak, +  kodunuzda yalnızca Python komut satırıyla mümkün olmayan kolay bir yol sağlar. Ayrıca, hata ayıklayıcıyı çalıştırmadan ve programınızı baştan başlatmaya gerek kalmadan kodunuzda ilerlemenizi sağlar.

1. Ayrıca, Python komut satırı REPL ile yapılması zor olan, aşağıdaki kod parçacığı gibi herhangi bir kaynaktaki **etkileşimli** pencereye birden çok satır kodu kopyalayabilir ve yapıştırabilirsiniz. Yapıştırıldığında, **etkileşimli** pencere bu kodu içine yazmış gibi çalıştırır:

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Etkileşimli gönderme kullanarak birden çok satırı kodla yapıştırma](media/vs-getting-started-python-15-interactive5.png)

1. Görebileceğiniz gibi, bu kod sorunsuz bir şekilde çalışıyor ancak çıktısı çok büyük değildir. Döngüdeki farklı bir adım değeri, `for` kosinüs dalgasının daha fazlasını gösterir. Neyse ki, tüm `for` döngü REPL geçmişinde tek bir birim olarak olduğundan, geri dönüp istediğiniz değişiklikleri yapmak ve sonra işlevi yeniden test etmek kolaydır. İlk olarak döngüyü geri çekmek için yukarı oka basın `for` . Ardından, kodda gezinmeye başlamak için sol veya sağ ok tuşlarına basın (böylece, yukarı ve aşağı okları geçmiş boyunca geçiş yapmaya devam eder). Öğesine gidin ve `range` belirtimini olarak değiştirin `range(0, 360, 12)` . Sonra  + tüm ifadeyi yeniden çalıştırmak için CTRL **ENTER** (kodun herhangi bir yerinde) tuşuna basın:

    ![Etkileşimli pencerede önceki bir ifadeyi Düzenle](media/vs-getting-started-python-16-interactive6.png)

1. En iyi şekilde istediğiniz değeri bulana kadar, farklı adım ayarlarıyla denemeler yapmak için işlemi tekrarlayın. Ayrıca, örneğin, aralığı uzaleyerek (örneğin,) bir dalga yineleme de yapabilirsiniz `range(0, 1800, 12)` .

1. **Etkileşimli** pencerede yazdığınız kodu memnun kaldığınızda, seçin. Ardından, koda sağ tıklayın ve **kodu kopyala** ' yı (**CTRL** + **SHIFT** + **C**) seçin. Son olarak, seçili kodu düzenleyiciye yapıştırın. Visual Studio 'nun bu özel özelliğinin, `>>>` ve istemlerinin yanı sıra herhangi bir çıktıyı otomatik olarak nasıl atladığına dikkat edin `...` . Örneğin, aşağıdaki görüntüde, komut istemlerini ve çıktıyı içeren bir seçimde **kodu kopyala** komutunun kullanımı gösterilmektedir:

    ![Etkileşimli pencere bir seçime komut istemi ve çıkış ile kod Kopyala](media/vs-getting-started-python-17-interactive7.png)

    Düzenleyiciye yapıştırdığınızda yalnızca kod alırsınız:

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    **Etkileşimli** pencerenin tam içeriğini, istemler ve çıkış dahil olmak üzere kopyalamak istiyorsanız, yalnızca standart **kopyalama** komutunu kullanın.

1. Az önce yaptığınız şey, küçük bir kod parçasının ayrıntılarını denemek için **etkileşimli** PENCERENIN hızlı çoğaltma ortamını kullanın, daha sonra bu kodu projenizin kaynak dosyasına kolayca eklediniz. Artık kodu **CTRL** + **F5** (veya   >  **hata ayıklama olmadan Başlat**) ile yeniden çalıştırdığınızda, istediğiniz sonuçları tam olarak görürsünüz.

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Hata ayıklayıcıda kodu çalıştırma](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Daha derin git

- [Etkileşimli pencereyi kullanma](python-interactive-repl-in-visual-studio.md)
- [IPython REPL kullanma](interactive-repl-ipython.md)