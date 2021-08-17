---
title: Python Visual Studio öğretici adım 4, hata ayıklama
titleSuffix: ''
description: Visual Studio, hata ayıklayıcıda python kodunun nasıl çalıştırılacağını kapsayan, python özelliklerine yönelik temel bir izlenecek yolun 4. adımı.
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
ms.openlocfilehash: 6957e0e5d8e53475a929673919a78f153c871401fc36c87b5e9754a57947b9fc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121229396"
---
# <a name="step-4-run-code-in-the-debugger"></a>4. Adım: hata ayıklayıcıda kodu çalıştırma

**Önceki adım: [ETKILEŞIMLI REPL penceresini kullanma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)**

projeleri yönetmeye ek olarak, zengin bir düzenleme deneyimi ve **etkileşimli** pencere Visual Studio, Python kodu için tam özellikli hata ayıklama sağlar. Hata ayıklayıcıda, bir döngünün her yinelemesi dahil olmak üzere adım adım adımları gerçekleştirebilirsiniz. Ayrıca, belirli koşullar doğru olduğunda programı da duraklatabilirsiniz. Herhangi bir noktada, program hata ayıklayıcıda duraklatıldığında, tüm program durumunu inceleyebilir ve değişkenlerin değerini değiştirebilirsiniz. Bu eylemler, program hatalarının izlenmesi için gereklidir ve ayrıca tam program akışını dikkatle izleyerek çok faydalı yardımlıklar sağlar.

1. *PythonApplication1.py* dosyasındaki kodu aşağıdaki kodla değiştirin. Kodun bu çeşitlemesi, `make_dot_string` hata ayıklayıcıda kendi ayrık adımlarını incelemenize olanak sağlayacak şekilde genişler. Ayrıca, `for` döngüyü bir `main` işleve koyar ve bu işlevi çağırarak açıkça çalıştırır:

    ```python
    from math import cos, radians

    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        rad = radians(x)                             # cos works with radians
        numspaces = int(20 * cos(rad) + 20)          # scale to 0-40 spaces
        st = ' ' * numspaces + 'o'                   # place 'o' after the spaces
        return st

    def main():
        for i in range(0, 1800, 12):
            s = make_dot_string(i)
            print(s)

    main()
    ```

1. **F5** tuşuna basarak veya **hata**  >  **ayıklamayı Başlat** menü komutunu seçerek kodun düzgün çalışıp çalışmadığını denetleyin. Bu komut, hata ayıklayıcıdaki kodu çalıştırır, ancak programı çalışırken duraklatmayı tamamlamadığınız için, yalnızca birkaç yineleme için bir dalga deseninin yazdırılmasını sağlar. Çıkış penceresini kapatmak için herhangi bir tuşa basın.

    > [!Tip]
    > Program tamamlandığında çıkış penceresini otomatik olarak kapatmak için, **Araçlar**  >  **Seçenekler** menü komutunu seçin, **Python** düğümünü genişletin, **hata ayıklama**' yi seçin ve ardından **işlem normal bir şekilde çıktığında giriş için bekle** seçeneğini temizleyin:
    >
    > ![Normal programda çıkış penceresini kapatmak için Python hata ayıklama seçeneği](media/vs-getting-started-python-22-debugging5.png)
    >
    > Betik ve yorumlayıcı bağımsız değişkenlerinin nasıl ayarlanacağı gibi görevler de dahil olmak üzere hata ayıklama hakkında daha fazla bilgi için bkz. [Python kodunuzda hata ayıklama](debugging-python-in-visual-studio.md).

1. `for`Bu satıra göre gri kenar boşluğunda bir kez tıklayarak veya giriş işaretini bu satıra yerleştirip **hata ayıklama**  >  **kesme noktasını aç** komutunu (**F9**) kullanarak deyimde bir kesme noktası ayarlayın. Bir kırmızı nokta, kesme noktasını göstermek için gri kenar boşluğunda görünür (aşağıdaki okla belirtilen şekilde):

    ![Kesme noktası ayarlama](media/vs-getting-started-python-18-debugging1.png)

1. Hata ayıklayıcıyı yeniden başlatın (**F5**) ve kodu çalıştırmanın bu kesme noktasına sahip satırda durduğunu görün. Burada çağrı yığınını inceleyebilir ve değişkenleri inceleyebilirsiniz. Kapsam içinde olan değişkenler, tanımlandıklarında, **oto** penceresinde görünür; ayrıca, geçerli kapsamda (işlevler dahil) bulduğu tüm Visual Studio değişkenleri, tanımlanmadan önce bile göstermek için söz konusu pencerenin altındaki **yereller** görünümüne geçiş yapabilirsiniz:

    ![Python için kesme noktası Kullanıcı arabirimi deneyimi](media/vs-getting-started-python-19-debugging2b.png)

1. Visual Studio penceresinin üst kısmında hata ayıklama araç çubuğunu (aşağıda gösterilen) gözlemleyin. Bu araç çubuğu, en yaygın hata ayıklama komutlarına ( **hata ayıklama** menüsünde de bulunabilir) hızlı erişim sağlar:

    ![Önemli hata ayıklama araç çubuğu düğmeleri](media/vs-getting-started-python-20-debugging3.png)

    Soldan sağa doğru düğmeler şunlardır:
    - **Devam et** (**F5**) programı bir sonraki kesme noktasına veya program tamamlanana kadar çalıştırır.
    - **Tümünü kes** (**CTRL** + **alt** + **kesme**) uzun süre çalışan bir programı duraklatır.
    - **Hata ayıklamayı Durdur** (**SHIFT** + **F5**) programı nerede olursa olsun durdurur ve hata ayıklayıcıdan çıkar.
    - **Yeniden Başlat** (**CTRL** + **SHIFT** + **F5**) programı olduğu her yerde sonlandırır ve hata ayıklayıcının başından itibaren yeniden başlatır.
    - **Sonraki ifadeyi göster** (**alt** + **num** **&#42;**), çalıştırılacak sonraki kod satırına geçer. Bu, hata ayıklama oturumu sırasında kodunuzun içinde gezindiğinizde ve hata ayıklayıcının duraklatıldığı noktaya hızlıca geri dönmek istediğinizde yararlı olur.
    - **Adımla** (**F11**), çağrılan işlevlere girerek sonraki kod satırını çalıştırır.
    - **Adımlama** (**F10**), çağrılan işlevlere girmeden sonraki kod satırını çalıştırır.
    - **Dışarı adımla** (**SHIFT** + **F11**) geçerli işlevin geri kalanını çalıştırır ve çağıran kodda duraklatılır.

1. `for` **Adım adım** kullanarak deyimin üzerine adımlayın. *Adımlama* , hata ayıklayıcının herhangi bir işlev çağrısı dahil olmak üzere geçerli kod satırını çalıştırdığı ve ardından hemen durakladığında oluşur. Değişkenin `i` artık **Yereller** ve **oto** pencerelerinde nasıl tanımlandığına dikkat edin.

1. Çağıran ve duraklayıp izleyen kod satırının üzerinde ilerleyin `make_dot_string` . **Burada,** hata ayıklayıcının bütün olarak çalıştırıldığı `make_dot_string` ve döndürdüğü süre durakladıkları anlamına gelir. Hata ayıklayıcı, burada ayrı bir kesme noktası bulunmadığı takdirde bu işlevin içinde durmaz.

1. Kodu birkaç kez daha çalıştırmaya devam edin ve **Locals** veya **oto** penceresindeki değerlerin nasıl değiştiğini gözlemleyin.

1. **Yereller** veya **oto** penceresinde,  `i` `s` değeri düzenlemek için ya da değişkenleri için değer sütununa çift tıklayın. Değişiklikleri uygulamak için **ENTER** tuşuna basın veya bu değerin dışındaki herhangi bir alana tıklayın.

1. **Adımlamayı** kullanarak koddan çalışmaya devam edin. **Içine adımla** , hata ayıklayıcının, gibi hata ayıklama bilgileri olan herhangi bir işlev çağrısının içine girdiği anlamına gelir `make_dot_string` . İçinde bir kez, `make_dot_string` yerel değişkenlerini inceleyebilir ve özel olarak kendi kodunda ilerleyebileceğiniz.

1. **Adımla** çalışmaya devam edin ve öğesinin sonuna ulaştığınızda, bir `make_dot_string` sonraki adımın, `for` değişkende yeni dönüş değeri ile döngüye geri döndüğünü unutmayın `s` . Deyimde bir kez daha adım adım `print` ,  `print` Bu işleve girmediğine dikkat edin. Bunun nedeni, `print` Python 'da yazılmamakta ancak Python çalışma zamanı içinde yerel koddur.

1. Bir kez daha yeniden gelinceye kadar **adım** kullanmaya devam edin `make_dot_string` . Ardından, **Step Out** kullanın ve döngüye döntiğine dikkat edin `for` . **Adımla**, hata ayıklayıcı işlevin geri kalanını çalıştırır ve ardından çağıran kodda otomatik olarak duraklatılır. Bu, hata ayıklamak istediğiniz uzun bir işlevin bir bölümünü işlediyseniz, ancak geri dönmek ve çağıran kodda açık bir kesme noktası ayarlamak istememeniz durumunda çok yararlı olur.

1. Sonraki kesme noktasına ulaşılana kadar programı çalıştırmaya devam etmek için **devam** ' ı (**F5**) kullanın. Döngüde bir kesme noktasına sahip olduğunuzdan `for` , bir sonraki yineleme üzerinde durgulayorsunuz.

1. bir döngünün yüzlerce yinelemesine adımlamak sıkıcı olabilir, bu nedenle Visual Studio kesme noktasına *koşul* eklemenizi sağlar. Hata ayıklayıcı daha sonra yalnızca koşul karşılandığında programı kesme noktasında duraklatır. Örneğin, `for` yalnızca değeri 1600 ' i aştığında duraklamasını sağlamak için ifadede kesme noktasıyla bir koşul kullanabilirsiniz `i` . Bu durumu ayarlamak için kırmızı kesme noktası noktasına sağ tıklayıp **koşullar** ' ı (**alt** + **F9**  >  **C**) seçin. görüntülenen **kesme noktası Ayarlar** açılan pencerede, `i > 1600` ifade olarak girin ve **kapat**' ı seçin. Devam etmek için **F5** tuşuna basın ve programın bir sonraki kesmenin önüne çok sayıda yineleme çalıştığını gözlemleyin.

    ![Kesme noktası koşulu ayarlama](media/vs-getting-started-python-21-debugging4.png)

1. Programı tamamlamak üzere çalıştırmak için kenar boşluğunda noktaya sağ tıklayıp **kesme noktasını devre dışı bırak** (**CTRL** + **F9**) seçeneğini belirleyerek kesme noktasını devre dışı bırakın. Sonra **devam** ' ı seçin (veya **F5** tuşuna basarak) programı çalıştırın. program sona erdiğinde, Visual Studio hata ayıklama oturumunu durdurduktan sonra kendi düzen moduna geri döner. Ayrıca, noktasını seçerek veya noktaya sağ tıklayıp **kesme noktasını sil**' i seçerek kesme noktasını da silebileceğinizi unutmayın, ancak bu, ayarlamış olduğunuz koşulu da siler.

> [!Tip]
> Python yorumlayıcı 'nın kendisini başlatma hatası gibi bazı durumlarda, çıkış penceresi yalnızca kısa bir süre içinde görünebilir ve sonra herhangi bir hata iletisi görmeniz için bir şans vermeden otomatik olarak kapatılabilir. Bu durumda **Çözüm Gezgini**' de projeye sağ tıklayın, **Özellikler**' i seçin, **Hata Ayıkla** sekmesini seçin ve ardından `-i` **yorumlayıcı bağımsız değişkenleri** alanına ekleyin. Bu bağımsız değişken, bir program tamamlandıktan sonra yorumlayıcı 'nın etkileşimli moda geçmesine neden olur, böylece  + çıkmak için CTRL **Z**  >  **ENTER** tuşuna girene kadar pencereyi açık tutun.

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Python ortamınıza paket yükler](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)

## <a name="go-deeper"></a>Daha derin git

- [Hata Ayıklama](debugging-python-in-visual-studio.md)
- [Visual Studio 'de hata ayıklama](../debugger/debugger-feature-tour.md) Visual Studio hata ayıklama özelliklerinin tam belgelerini sağlar.
