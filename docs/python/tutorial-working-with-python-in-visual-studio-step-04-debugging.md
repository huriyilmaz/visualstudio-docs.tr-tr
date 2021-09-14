---
title: Python in Visual Studio öğreticisi 4. adım, hata ayıklama
titleSuffix: ''
description: Hata ayıklayıcıda Python kodunu çalıştırmayı kapsayan, Visual Studio Python özelliklerine ait temel kılavuz 4. adım.
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
ms.openlocfilehash: d4ec2aacb6ba0eb06e6603928da623c7b5bb9d7c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636937"
---
# <a name="step-4-run-code-in-the-debugger"></a>4. Adım: Hata ayıklayıcıda kod çalıştırma

**Önceki adım: [Etkileşimli REPL penceresini kullanma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)**

Projeleri yönetmeye, zengin düzenleme deneyimi ve Etkileşimli  pencereye ek olarak, Visual Studio Python kodu için tam özellikli hata ayıklama da sağlar. Hata ayıklayıcısında, döngülerin her yinelemesi de dahil olmak üzere kodunuzu adım adım çalıştırabilirsiniz. Ayrıca, belirli koşullar doğru olduğunda programı duraklatabilirsiniz. Program hata ayıklayıcıda duraklatılırsa program durumunun tamamını inceleyebilirsiniz ve değişkenlerin değerini değiştirebilirsiniz. Bu tür eylemler program hatalarını izlemek için gereklidir ve aynı zamanda tam program akışını dikkatle izlemek için çok yararlı yardımlar sağlar.

1. *PythonApplication1.py* dosyasındaki kodu aşağıdakiyle değiştirin. Bu kod varyasyonu, `make_dot_string` hata ayıklayıcısındaki ayrık adımlarını inceleyecek şekilde genişler. Ayrıca döngüyü `for` bir işleve `main` yer verir ve bu işlevi çağırarak açıkça çalıştırır:

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

1. **F5** tuşuna basarak veya Hata Ayıklamayı Başlat hata ayıklama menü komutunu **seçerek**  >  **kodun düzgün çalıştığını** denetleyin. Bu komut, hata ayıklayıcısında kodu çalıştırır, ancak programı çalışırken duraklatmak için bir şey yapmadınız, yalnızca birkaç yineleme için dalga deseni yazdırır. Çıkış penceresini kapatmak için herhangi bir tuşa basın.

    > [!Tip]
    > Program tamamlandığında çıkış penceresini otomatik olarak kapatmak için Araçlar Seçenekler menü komutunu seçin, Python düğümünü genişletin, Hata Ayıklama'ya tıklayın ve ardından İşlem normal şekilde çıkışa geldiğinde girişi bekle  >   **seçeneğinin temizlemesini bekleyin:**  
    >
    > ![Normal program çıkışında çıkış penceresini kapatmak için Python hata ayıklama seçeneği](media/vs-getting-started-python-22-debugging5.png)
    >
    > Betik ve yorumlayıcı bağımsız değişkenlerini ayarlama gibi görevler de dahil olmak üzere hata ayıklama hakkında ek bilgi için bkz. [Python kodunuzun hatasını ayıklama.](debugging-python-in-visual-studio.md)

1. Deyiminde bir kesme noktası ayarlamak için bu satırın gri kenar boşluğuna bir kez tıklayın veya bu satıra nokta koyarak ve Hata Ayıklama Kesme Noktası GeçişIni Değiştir komutunu `for`   >   (**F9) kullanarak** ayarlayın. Kesme noktası belirtmek için gri kenar boşluğunda kırmızı bir nokta görünür (aşağıdaki okla belirtilmiştir):

    ![Kesme noktası ayarlama](media/vs-getting-started-python-18-debugging1.png)

1. Hata ayıklayıcıyı yeniden (**F5**) başlat ve kodu çalıştırmanın bu kesme noktasıyla satırda durduğuna bakın. Burada çağrı yığınını inceleyebilirsiniz ve değişkenleri inceleyebilirsiniz. Kapsam içinde olan değişkenler **tanımlandığı zaman** Otomatikler penceresinde görünür; Ayrıca, tanımlanmamış  olsalar bile geçerli kapsamda (işlevler dahil) Visual Studio tüm değişkenleri göstermek için bu pencerenin altındaki Yereller görünümüne geçebilirsiniz:

    ![Python için kesme noktası kullanıcı arabirimi deneyimi](media/vs-getting-started-python-19-debugging2b.png)

1. Hata ayıklama araç çubuğunun (aşağıda gösterilmiştir) hata ayıklama penceresinin üst Visual Studio bakın. Bu araç çubuğu en yaygın hata ayıklama komutlarına (Hata Ayıklama menüsünde de bulunabilir) **hızlı erişim** sağlar:

    ![Temel hata ayıklama araç çubuğu düğmeleri](media/vs-getting-started-python-20-debugging3.png)

    Soldan sağa düğmeleri aşağıdaki gibi:
    - **Devam** (**F5**) sonraki kesme noktası kadar veya program tamamlandıktan sonra programı çalıştırır.
    - **Hepsini Kır** (**Ctrl** + **Alt** + **Kesme**) uzun süre çalışan bir programı duraklatıyor.
    - **Hata Ayıklamayı** Durdur (**Shift** F5 ) nerede olursa olsun programı + durdurur ve hata ayıklayıcısından çıkar.
    - **Restart** (**Ctrl** Shift F5 ), programı nerede olursa olsun durdurur ve hata ayıklayıcıda +  + en baştan yeniden başlatın.
    - **Sonraki Deyimi Göster** (**Alt** + **Num** **&#42;**), çalıştıracak bir sonraki kod satırına geçişler. Bu, hata ayıklama oturumu sırasında kodunuzun içinde gezinerek hata ayıklayıcının duraklatılmış olduğu noktaya hızlıca dönmek istediğinizde yararlıdır.
    - **Step Into** (**F11**) bir sonraki kod satırı çalıştırır ve çağrılır işlevlere girer.
    - **Adım At** (**F10**), çağrılan işlevlere girmeden sonraki kod satırı çalıştırır.
    - **Step Out** (**Shift** + **F11**) geçerli işlevin geri kalanını çalıştırır ve çağrı kodunda duraklatılır.

1. Adım `for` At'ı kullanarak **deyiminin üzerinden geçin.** *Adımlama,* hata ayıklayıcının herhangi bir işlev çağrısı dahil geçerli kod satırı çalıştırarak hemen yeniden duraklatılması anlamına gelir. Değişkenin yereller `i` ve Otomatikler **pencerelerinde nasıl** **tanımlandığına dikkatin.**

1. Çağrısı yapılan ve duraklatan bir sonraki kod `make_dot_string` satırına geçin. **Buraya Adımla** özellikle hata ayıklayıcısının tamamını çalıştırarak geri `make_dot_string` döndüğünde duraklatma anlamına gelir. Ayrı bir kesme noktası mevcut olmadığı sürece hata ayıklayıcı bu işlevin içinde durmaz.

1. Kodun üzerinden birkaç kez daha adım atarak Yereller veya Otomatikler penceresindeki **değerlerin nasıl** **değiştiklerine** göz atabilirsiniz.

1. Yereller **veya** **Otomatikler** penceresinde, değeri düzenlemek  için veya değişkenlerinin Değer `i` `s` sütununa çift tıklayın. Değişiklikleri uygulamak için **Enter** tuşuna basın veya bu değerin dışındaki herhangi bir alana tıklayın.

1. Içine Adımla'ya geçerek kodda **adım adım çalışmaya devam edin.** **Içine Adımla,** hata ayıklayıcının hata ayıklama bilgilerine sahip olduğu herhangi bir işlev çağrısının içine girdiği anlamına `make_dot_string` gelir. İçeriye `make_dot_string` girdiktan sonra yerel değişkenlerini inceleyebilirsiniz ve kodunda özel olarak adım atabilirsiniz.

1. **AdımLa ile adımlama** devam edin ve değerinin sonuna ulaşabilirsiniz. Sonraki adım, değişkende yeni dönüş değeriyle `make_dot_string` `for` döngüye `s` döner. deyimine yeniden adım adım `print` ilerlerken, **Step Into** on `print` işlevinin içine girmez. Bunun nedeni `print` Python'da yazıldığı değil Python çalışma zamanının içinde yerel kod olmasıdır.

1. adımını **tekrar kullanana** kadar kullanmaya devam `make_dot_string` edin. Ardından **Step Out kullanın** ve döngüye geri `for` dönersiniz. Adım **At ile,** hata ayıklayıcı işlevin geri kalanını çalıştırır ve ardından çağıran kodda otomatik olarak duraklatılır. Bu, hata ayıklamak istediğiniz uzun bir işlevin bazı kısımlarında adım adım ilerlerken ama geri kalanı adım adım atarak çağırma kodunda açık bir kesme noktası ayarlamak istemeyebilirsiniz.

1. Sonraki kesme noktası ulaşıncaya kadar programı çalıştırmaya devam etmek için Devam ( F5 **)** **kullanın.** Döngüde bir kesme noktamız `for` olduğundan, sonraki yinelemede kesme noktası olur.

1. Bir döngüde yüzlerce yineleme adımlama sıkıcı olabilir, bu nedenle Visual Studio kesme noktalarına *koşul* eklemenize olanak sağlar. Ardından hata ayıklayıcı, programı kesme noktası üzerinde yalnızca koşul karşı geldiğinde duraklatıyor. Örneğin, yalnızca değeri `for` 1600'i aştında duraklatmak için deyimde kesme noktası olan bir `i` koşul kullanabilirsiniz. Bu koşulu ayarlamak için kırmızı kesme noktası noktaya sağ tıklayın ve Koşullar **(** **Alt** + **F9** C ) seçeneğini  >  **seçin.** Açılan **Kesme noktası Ayarlar** ifade olarak girin ve `i > 1600` Kapat'ı **seçin.** Devam **etmek için F5** tuşuna basın ve programın bir sonraki kesmeden önce birçok yineleme çalıştırarak bunu gözlemler.

    ![Kesme noktası koşulu ayarlama](media/vs-getting-started-python-21-debugging4.png)

1. Programı tamamlanacak şekilde çalıştırmak için kenar boşluğunda yer alan noktaya sağ tıklar ve Kesme noktası devre dışı bırak **(** **Ctrl** F9 ) seçeneğini kullanarak kesme noktası devre + **dışı bırakın.** Ardından **Devam'ı** seçin (veya **F5** tuşuna basın) programı çalıştırın. Program sona erdiğinde Visual Studio hata ayıklama oturumunu durdurur ve düzenleme moduna döner. Kesme noktası seçerek veya noktaya sağ tıklar ve Kesme noktası sil'i seçerek de kesme noktası silebilirsiniz. Ancak bu ayar, ayar herhangi bir koşulu da siler. 

> [!Tip]
> Python yorumlayıcısını başlatmama gibi bazı durumlarda çıkış penceresi yalnızca kısa bir süre görünebilir ve hata iletilerini görme fırsatı vermeden otomatik olarak kapatabilirsiniz. Bu durumda, Çözüm Gezgini'de projeye sağ **tıklayın,** Özellikler'i **seçin,** Hata Ayıkla sekmesini **seçin** ve yorumlayıcı `-i` Bağımsız Değişkenleri **alanına** ekleyin. Bu bağımsız değişken, program tamamlandıktan sonra yorumlayıcının etkileşimli moda geçişe neden olur ve çıkış için **Ctrl** Z Enter tuşlarına basarak +   >  **pencereyi** açık tutun.

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Python ortamınıza paket yükleme](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)

## <a name="go-deeper"></a>Daha derine gitme

- [Hata Ayıklama](debugging-python-in-visual-studio.md)
- [Visual Studio'da hata](../debugger/debugger-feature-tour.md) ayıklama özelliği, Visual Studio hata ayıklama özelliklerinin tam belgelerini sağlar.
