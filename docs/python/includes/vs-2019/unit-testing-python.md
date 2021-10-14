---
title: Birim testi Python kodu
description: Visual Studio'da Python kodu için birim testi Visual Studio testleri keşfetmek, çalıştırmak ve hata ayıklamak için Test Gezgini özelliklerinden tam olarak faydalanabilir.
ms.date: 09/18/2019
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 67397ac209d282458e78b4ddecb903858506129d
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129968338"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Python projesi için test çerçevesini seçme

Visual Studio Python, [unittest](https://docs.python.org/3/library/unittest.html) ve [pytest](https://pytest.org/en/latest/) için iki test çerçevesini destekler (sürüm 16.3'Visual Studio 2019'da kullanılabilir). Varsayılan olarak, Bir Python projesi 7.000.00000000000000000000000000000 Çerçeve belirtmek için, proje adı'Çözüm Gezgini tıklayın ve Özellikler **seçeneğini** belirleyin. Bu işlem, Test sekmesinden testleri yapılandırmaya olanak sağlayan proje **tasarımcısını** açar. Bu sekmeden projeniz için kullanmak istediğiniz test çerçevesini seçin. 

* **Unittest çerçevesi** için, test bulma için projenin kök dizini kullanılır. Bu konum ve testleri tanımlamaya yönelik metin deseni, **Test** sekmesinde kullanıcı tarafından belirtilen değerlerle değiştirilebilir.
* **pytest çerçevesi için** test konumu ve dosya adı desenleri gibi test seçenekleri standart pytest .ini belirtilir. Diğer ayrıntılar [için pytest başvuru](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) belgelerine bakın.

Çerçeve seçiminizi ve ayarlarınızı kaydeden test bulma, Test Gezgini'nde başlatılır. Test Gezgini penceresi henüz açık değilse araç çubuğuna gidin ve **Test**  >  **Gezgini'ni seçin.**

## <a name="configure-testing-for-python-without-a-project"></a>Proje olmadan Python için test yapılandırma
Visual Studio, Python kodu içeren bir klasör açarak mevcut Python kodunu proje olmadan [çalıştırabilir ve](../../quickstart-05-python-visual-studio-open-folder.md) test edin. Bu koşullar altında testi yapılandırmak için **PythonSettings.json** dosyası kullansanız iyi olur. 
1. Yerel Klasör Aç seçeneğini kullanarak mevcut Python **kodunuzu** açın. 

   ![Visual Studio başlangıç ekranı](../../media/quickstart-open-folder/01-open-local-folder.png)

1. Yeni Çözüm Gezgini penceresinde Tüm Dosyaları **Göster simgesine** tıklar ve geçerli klasördeki tüm dosyaları gösterir.

   ![Tüm dosyaları göster düğmesi](../../media/unit-test-show-files.png)

1. **Local Ayarlar** **klasöründeki PythonSettings.json** dosyasına gidin. Bu dosyayı Local Ayarlar klasöründe **görmüyorsanız** el ile oluşturun.
   
1. **TestFramework** alanını ayarlar dosyasına ekleyin ve kullanmak istediğiniz test çerçevesine bağlı olarak **pytest** veya **unittest** olarak ayarlayın.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > **unittest** framework için **UnitTestRootDirectory** ve **UnitTestPattern** alanları PythonSettings.json dosyasında belirtilmezse, sırasıyla "." ve "test*.py" varsayılan değerleri eklenir ve atanır.

1. Klasörünüz, testlerinizi içeren klasörden ayrı bir **src** dizini içeriyorsa **PythonSettings.json** dosyanız **içinde SearchPaths** alanını kullanarak **src** klasörünün yolunu belirtin.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Belirtilen çerçeve için test bulma başlatmak üzere PythonSettings.json dosyasında yaptığınız değişiklikleri kaydedin. 
   > [!Note]
   > Test Gezgini penceresi zaten açıksa **CTRL**  +  **R,A bulmayı** da tetikler.

## <a name="discover-and-view-tests"></a>Testleri bulma ve görüntüleme

Varsayılan olarak, Visual Studio **ve** **pytest** testlerini, adları ile başlarken yöntemler olarak `test` tanımlar. Test bulmayı görmek için şunları yapın:

1. Bir [Python projesi açın.](../../managing-python-projects-in-visual-studio.md)

1. Proje Visual Studio yüklendi Çözüm Gezgini projenize sağ tıklayın ve Özellikler Testi **sekmesinden unittest** veya **pytest** **çerçevesini** seçin.
   > [!Note]
   > pytest çerçevesini kullanıyorsanız, standart pytest ve dosya adı yapılandırma dosyasını kullanarak test konumu ve .ini belirtebilirsiniz. Varsayılan olarak, çalışma alanı/proje klasörü ve deseniyle `test_*py` birlikte `*_test.py` kullanılır. Diğer ayrıntılar [için pytest başvuru](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) belgelerine bakın.

1. Çerçeve seçildikten sonra projeye yeniden sağ tıklayın ve Yeni Öğe Ekle'yi seçin, ardından Python Birim  >   **Testi'nin ardından** Ekle'yi **seçin.**

1. Bu eylem, standart modülü içeri aktaran, 'den bir test sınıfı türeten ve betiği doğrudan çalıştırıyorsanız çağıran bir *test_1.py* `unittest` `unittest.TestCase` dosyası `unittest.main()` oluşturur:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Gerekirse dosyayı kaydedin ve Test **Gezgini'ni Test** Gezgini **menü**  >  **komutuyla** açın.

1. **Test Gezgini,** projenizi testler için arar ve aşağıda gösterildiği gibi görüntüler. Bir teste çift tıklarsanız kaynak dosyası açılır.

    ![Varsayılan ayarları gösteren Test Gezgini test_A](../../media/unit-test-a-2.png) 

1. Projenize daha fazla test eklerken, araç çubuğundaki **Grupla** menüsünü kullanarak Test **Gezgini'nde** görünümü düzenleyebilirsiniz:

    ![Testler Gezgini Grupla araç çubuğu menüsü](../../media/unit-test-group-menu-2.png) 

1. Testleri adlarına göre filtrelemek **için Arama** alanına metin de girebilirsiniz.

Modül ve test yazma `unittest` hakkında daha fazla bilgi için Python [2.7](https://docs.python.org/2/library/unittest.html) belgelerine veya [Python 3.7](https://docs.python.org/3/library/unittest.html) belgelerine (python.org).

## <a name="run-tests"></a>Testleri çalıştırma

**Test Gezgini'nde** testleri çeşitli yollarla çalıştırabilirsiniz:

- **Hepsini Çalıştır,** gösterilen tüm testleri net bir şekilde çalıştırır (filtrelere tabi).
- Çalıştır **menüsü** başarısız, başarılı veya grup olarak test çalıştırmama komutlarını verir.
- Bir veya daha fazla test seçin, sağ tıklayın ve Seçili Testleri **Çalıştır'ı seçin.**

Testler arka planda çalışır ve **Test Gezgini** tamamlandığında her testin durumunu günceller:

- Testleri geçirme, yeşil bir onay işareti ve testi çalıştırmak için geçen zamanı gösterir:

    ![test_A durumu geçti](../../media/unit-test-A-pass.png)

- Başarısız testler, konsol çıkışını ve test **çalıştırması çıktısını** gösteren Çıkış `unittest` bağlantısıyla kırmızı çarpı gösterir:

    ![test_A durumu](../../media/unit-test-A-fail.png)

    ![test_A nedeniyle başarısız oldu](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Testlerde hata ayıklama

Birim testleri kod parçaları olduğundan, aynı diğer kodlar gibi hatalara maruz olur ve bazen bir hata ayıklayıcısında çalıştırılaları gerekir. Hata ayıklayıcısında kesme noktaları ayarlayıcıda değişkenleri inceleyebilirsiniz ve kodda adım adım yol kullanabilirsiniz. Visual Studio birim testleri için tanılama araçları da sağlar.

> [!Note]
> Varsayılan olarak, test hata ayıklaması Visual Studio 2017 (sürüm 15.8 ve sonrası) için ptvsd 4 hata ayıklayıcısını ve Visual Studio 2019 (sürüm 16.5 ve sonraki sürümler) için hata ayıklamayı kullanır. Bunun yerine ptvsd 3 kullanmak için Araçlar  Seçenekler Python Hata Ayıklama'da Eski Hata Ayıklayıcıyı **Kullan**  >    >    >  **seçeneğini kullanabilirsiniz.** 

Hata ayıklamayı başlatmak için kodunda bir başlangıç kesme noktası ayarlayın, ardından Test Gezgini'nde teste (veya seçime) sağ **tıklayın** ve Seçili Testlerde Hata **Ayıkla'yı seçin.** Visual Studio kodu için olduğu gibi Python hata ayıklayıcısını başlatır.

![Testte hata ayıklama](../../media/unit-test-debugging.png)

Seçilen Testler için Kod Kapsamı **Analiz Etme'i de kullanabilirsiniz.** Daha fazla bilgi için [bkz. Ne kadar kodun test olduğunu belirlemek için kod kapsamı kullanma.](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
