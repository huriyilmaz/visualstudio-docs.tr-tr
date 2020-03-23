---
title: Birim testi Python kodu
description: Visual Studio'da Python kodu için birim testini ayarlamak, test gezgini testlerini keşfetmek, çalıştırmak ve hata ayıklamak için tüm avantajlardan yararlanır.
ms.date: 09/18/2019
ms.topic: include
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8adce700524c4ade6c627aa91480460f8f2571f2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71933475"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Python projesi için test çerçevesini seçin

Visual Studio Python, [unittest](https://docs.python.org/3/library/unittest.html) ve [pytest](https://pytest.org/en/latest/) için iki test çerçevesini destekler (Visual Studio 2019 sürümü 16.3'ten başlayarak mevcuttur). Varsayılan olarak, python projesi oluşturduğunuzda hiçbir çerçeve seçili değildir. Bir çerçeve belirtmek için, Çözüm Gezgini'nde proje adına sağ tıklayın ve **Özellikler** seçeneğini seçin. Bu, test **sekmesi** aracılığıyla testleri yapılandırmanızı sağlayan proje tasarımcısını açar. Bu sekmeden, projeniz için kullanmak istediğiniz test çerçevesini seçebilirsiniz. 

* **Birimtest** çerçevesi için, projenin kök dizini test bulma için kullanılır. Bu konum ve testleri tanımlamak için metin deseni, **Test** sekmesinde kullanıcı tarafından belirtilen değerlere değiştirilebilir.
* **Pytest** çerçevesi için, test konumu ve dosya adı desenleri gibi test seçenekleri standart pytest .ini yapılandırma dosyası kullanılarak belirtilir. Daha fazla ayrıntı için [en pytest başvuru belgelerine](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) bakın.

Çerçeve seçiminizi ve ayarlarınızı kaydettikten sonra Test Gezgini'nde test bulma işlemi başlatılır. Test Gezgini penceresi zaten açık değilse, araç çubuğuna gidin ve **Test** > **Gezgini'ni**seçin.

## <a name="configure-testing-for-python-without-a-project"></a>Python için proje olmadan yapılandırın test
Visual Studio, Python koduna sahip bir klasör [açarak](../../quickstart-05-python-visual-studio-open-folder.md) varolan Python kodunu proje olmadan çalıştırmanızı ve test etmenizi sağlar. Bu koşullar altında, sınama yapılandırmak için bir **PythonSettings.json** dosyası kullanmanız gerekir. 
1. **Yerel Klasör Aç** seçeneğini kullanarak varolan Python kodunuzu açın. 

   ![Visual Studio başlangıç ekranı](../../media/quickstart-open-folder/01-open-local-folder.png)

1. Çözüm Gezgini penceresinde, geçerli klasördeki tüm dosyaları göstermek için **Tüm Dosyaları Göster** simgesini tıklatın.

   ![Tüm dosyaları göster düğmesini göster](../../media/unit-test-show-files.png)

1. **Yerel Ayarlar** klasöründeki **PythonSettings.json** dosyasına gidin. Bu dosyayı **Yerel Ayarlar** klasöründe görmüyorsanız, el ile oluşturun.
   
1. Alan **TestFramework'i** ayarlar dosyasına ekleyin ve kullanmak istediğiniz test çerçevesine bağlı olarak **pytest** veya **unittest** olarak ayarlayın.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > **Unittest** framework için, **UnitTestRootDirectory** ve **UnitTestPattern** alanları PythonSettings.json dosyasında belirtilmemişse, sırasıyla "." ve "test*.py" varsayılan değerleri eklenir ve atanır.

1. Klasörünüz testlerinizi içeren klasörden ayrı bir **src** dizini içeriyorsa, **PythonSettings.json** dosyanızdaki **SearchPaths** alanını kullanarak **src** klasörüne giden yolu belirtin.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Belirtilen çerçeve için test bulma başlatmak için PythonSettings.json dosyasına değişikliklerinizi kaydedin. 
   > [!Note]
   > Test Gezgini penceresi zaten **ctrl** + R açıksa,A da bulma tetikler.**R,A**

## <a name="discover-and-view-tests"></a>Testleri keşfedin ve görüntüleyin

Varsayılan olarak, Visual Studio **unittest** ve **pytest** testlerini adları ' ile `test`başlayan yöntemler olarak tanımlar. Test keşfini görmek için aşağıdakileri yapın:

1. Python [projesi](../../managing-python-projects-in-visual-studio.md)açın.

1. Proje Visual Studio'ya yüklendikten sonra Solution Explorer'da projenize sağ tıklayın ve Özellikler **Testi** sekmesinden **birimtest** veya **pytest** çerçevesini seçin.
   > [!Note]
   > Pytest çerçevesini kullanıyorsanız, standart pytest .ini yapılandırma dosyasını kullanarak test konumu ve dosya adı desenleri belirtebilirsiniz. Varsayılan olarak, çalışma alanı/proje klasörü kullanılır, `test_*py` `*_test.py`bir desen ve . Daha fazla ayrıntı için [en pytest başvuru belgelerine](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) bakın.

1. Çerçeve seçildikten sonra, projeyi yeniden sağ tıklatın ve**Yeni Öğe** **Ekle'yi** > seçin, ardından **Python Birim Testi'ni** seçin ve ardından **Ekle'yi**seçin.

1. Bu eylem, standart `unittest` modülü içeri aktaran, test sınıfı `unittest.TestCase`türeten ve komut dosyasını `unittest.main()` doğrudan çalıştırdığınızda çağıran kodlu bir *test_1.py* dosyası oluşturur:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Gerekirse dosyayı kaydedin ve **Test** > **Gezgini** menüsü komutuyla Test **Gezgini'ni** açın.

1. **Test Explorer** testiçin projenizde arama lar ve bunları aşağıda gösterildiği gibi görüntüler. Bir testi çift tıklatma, kaynak dosyasını açar.

    ![Varsayılan test_A gösteren Test Gezgini](../../media/unit-test-a-2.png) 

1. Projenize daha fazla test ekledikçe, araç çubuğundaki **Grup By** menüsünü kullanarak görünümü **Test Gezgini'nde** düzenleyebilirsiniz:

    ![Explorer Grubunu Araç Çubuğu menüsüne göre sınar](../../media/unit-test-group-menu-2.png) 

1. Testleri ada göre filtrelemek için **Arama** alanına metin de girebilirsiniz.

Modül ve yazma testleri hakkında daha fazla bilgi için [Python 2.7 belgelerine](https://docs.python.org/2/library/unittest.html) veya [Python 3.7 belgelerine](https://docs.python.org/3/library/unittest.html) (python.org) bakın. `unittest`

## <a name="run-tests"></a>Testleri çalıştırma

**Test Gezgini'nde** testleri çeşitli şekillerde çalıştırabilirsiniz:

- **Tüm** açıkça gösterilen testleri (filtrelere tabi) çalıştırın.
- **Çalıştır** menüsü, başarısız, geçmiş veya testleri grup olarak çalıştırmama komutları verir.
- Bir veya daha fazla test seçebilir, sağ tıklatabilir ve **Seçili Testleri Çalıştır'ı**seçebilirsiniz.

Testler arka planda çalışır ve **Test Gezgini** tamamladığı gibi her testin durumunu güncelleştirir:

- Geçen testler yeşil bir kene ve testi çalıştırmak için geçen süreyi gösterir:

    ![test_A geçti durumu](../../media/unit-test-A-pass.png)

- Başarısız testler, konsol çıktısını ve `unittest` test çalışmasından çıktıyı gösteren bir **Çıktı** bağlantısına sahip bir kırmızı çapraz gösterir:

    ![test_A başarısız durum](../../media/unit-test-A-fail.png)

    ![test_A akıl ile başarısız oldu](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Hata ayıklama testleri

Birim testleri kod parçaları olduğundan, diğer kodlar gibi hatalara maruz kalıyorlar ve bazen hata ayıklayıcıda çalıştırılması gerekir. Hata ayıklamada kesme noktaları ayarlayabilir, değişkenleri inceleyebilir ve kod üzerinden adım atabilirsiniz. Visual Studio ayrıca birim testleri için tanılama araçları sağlar.

> [!Note]
> Varsayılan olarak, test hata ayıklama ptvsd 4 hata ayıklama kullanır. Bunun yerine ptvsd 3 kullanmak istiyorsanız, **Araçlar** > **Seçenekleri** > **Python** > **Hata Ayıklama**üzerinde Kullanım Eski Hata **Ayıklama** seçeneğini seçebilirsiniz. 

Hata ayıklamaya başlamak için, kodunuzda bir başlangıç kesme noktası ayarlayın, ardından Test **Gezgini'nde** testi (veya seçimi) sağ tıklatın ve **Hata Ayıklama Seçili Testleri**seçin. Visual Studio, python hata ayıklayıcısını uygulama kodunda olduğu gibi başlatır.

![Testin hata ayıklama](../../media/unit-test-debugging.png)

**Ayrıca, Seçili Testler için Analiz Kodu Kapsamını**da kullanabilirsiniz. Daha fazla bilgi için [bkz.](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
