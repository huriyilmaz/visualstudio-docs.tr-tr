---
title: Birim testi Python kodu
description: Birim testi için Visual Studio'da Python kodu ayarlama tam Testlerde Hata Ayıkla bulmak ve çalıştırmak için Test Gezgini özelliklerinden yararlanır.
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
ms.sourcegitcommit: 9f6f63a2d76c6e579b4b67a96ec86faba99ad1df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71933475"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Python projesi için test çerçevesini seçme

Visual Studio, Python, [UnitTest](https://docs.python.org/3/library/unittest.html) ve [pytest](https://pytest.org/en/latest/) için iki test çerçevesini destekler (visual Studio 2019 sürüm 16,3 ' den itibaren kullanılabilir). Varsayılan olarak, bir Python projesi oluşturduğunuzda hiçbir Framework seçilmemiş. Bir Framework belirtmek için Çözüm Gezgini içindeki proje adına sağ tıklayın ve **Özellikler** seçeneğini belirleyin. Bu, **Test** sekmesi aracılığıyla testleri yapılandırmanıza olanak sağlayan proje Tasarımcısını açar. Bu sekmede, projeniz için kullanmak istediğiniz test çerçevesini seçebilirsiniz. 

* **UnitTest** çerçevesi için, projenin kök dizini test bulma için kullanılır. Bu konum ve testlerin belirlenmesi için metin deseninin, **Test** sekmesinde Kullanıcı tarafından belirtilen değerler için değiştirilmesi de değiştirilebilir.
* **Pytest** çerçevesi için, test konumu ve dosya adı desenleri gibi test seçenekleri standart pytest. ini yapılandırma dosyası kullanılarak belirtilir. Daha fazla bilgi için [pytest başvuru belgelerine](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) bakın.

Çerçeve seçiminizi ve ayarlarını kaydettikten sonra test bulma işlemi Test Gezgini 'nde başlatılır. Test Gezgini penceresi zaten açık değilse, araç çubuğuna gidin ve **test > test** **Gezgini**' ni seçin.

## <a name="configure-testing-for-python-without-a-project"></a>Proje olmadan Python için testi yapılandırma
Visual Studio, Python kodu içeren [bir klasör açarak](../../quickstart-05-python-visual-studio-open-folder.md) mevcut Python kodunu bir proje olmadan çalıştırmanıza ve test etmenize olanak tanır. Bu koşullarda, testi yapılandırmak için bir **PythonSettings. JSON** dosyası kullanmanız gerekir. 
1. **Yerel klasör aç** seçeneğini kullanarak mevcut Python kodunuzu açın. 

   ![Visual Studio başlangıç ekranı](../../media/quickstart-open-folder/01-open-local-folder.png)

1. Çözüm Gezgini penceresinde, geçerli klasördeki tüm dosyaları göstermek için **tüm dosyaları göster** simgesine tıklayın.

   ![Tüm dosyaları göster düğmesi](../../media/unit-test-show-files.png)

1. **Yerel ayarlar** klasörü içindeki **PythonSettings. JSON** dosyasına gidin. Bu dosyayı **yerel ayarlar** klasöründe görmüyorsanız, el ile oluşturun.
   
1. **Testframework** alanını ayarlar dosyasına ekleyin ve kullanmak istediğiniz test çerçevesine bağlı olarak **pytest** veya **UnitTest** olarak ayarlayın.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > **UnitTest** Framework Için, **Unittestrootdirectory** ve **unittestmodel** alanları PythonSettings. json dosyasında belirtilmemişse, bunlar eklenir ve varsayılan değerleri sırasıyla "." ve "test *. Kopyala" atanır.

1. Klasörünüz, testlerinizi içeren klasörden ayrı bir **src** dizini Içeriyorsa, **PythonSettings. JSON** dosyanızdaki **SearchPaths** alanını kullanarak **src** klasörünün yolunu belirtin.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Belirtilen çerçeve için test bulmayı başlatmak üzere değişikliklerinizi PythonSettings. JSON dosyasına kaydedin. 
   > [!Note]
   > Test Gezgini penceresi zaten **CTRL** + R 'ye açık Ise **, bir** de bulmayı tetikler.

## <a name="discover-and-view-tests"></a>Testleri görüntülemek ve keşfedin

Varsayılan olarak, Visual Studio **UnitTest** ve **pytest** testlerini adları `test`ile başlayan yöntemler olarak tanımlar. Test bulmayı görmek için aşağıdakileri yapın:

1. Bir [Python projesi](../../managing-python-projects-in-visual-studio.md)açın.

1. Proje Visual Studio 'Ya yüklendikten sonra, Çözüm Gezgini ' de projenize sağ tıklayın ve Özellikler **Test** sekmesinden **UnitTest** veya **pytest** çerçevesini seçin.
   > [!Note]
   > Pytest çerçevesini kullanırsanız, standart pytest. ini yapılandırma dosyasını kullanarak test konumu ve dosya adı desenleri belirtebilirsiniz. Varsayılan olarak, çalışma alanı/proje klasörü, `test_*py` ve `*_test.py`bir düzeniyle kullanılır. Daha fazla bilgi için [pytest başvuru belgelerine](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) bakın.

1. Framework seçildikten sonra projeye tekrar sağ tıklayın ve > **Yeni öğe** **Ekle** ' yi seçin ve ardından **Ekle**' **yi seçin.**

1. Bu eylem, standart `unittest` modülünü içeri aktaran, `unittest.TestCase`bir test sınıfı türetilen ve betiği doğrudan çalıştırırsanız `unittest.main()` çağıran bir *test_1.* bir dosya oluşturur:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Gerekirse dosyayı **kaydedin ve test > test** **Gezgini** menü komutuyla **Test Gezgini** ' ni açın.

1. **Test Gezgini** projeniz için testleri arar ve aşağıda gösterildiği gibi görüntüler. Bir testi çift kaynak dosyası açılır.

    ![Test Gezgini gösteren varsayılan test_A](../../media/unit-test-a-2.png) 

1. Projenize daha fazla test eklediğinizde, araç çubuğundaki **grupla** menüsünü kullanarak **Test Gezgini** 'nde görünümü düzenleyebilirsiniz:

    ![Test Gezgini araç çubuğu menüsü grupla](../../media/unit-test-group-menu-2.png) 

1. Bir metin de girebilirsiniz **arama** testleri adına göre filtrelemek için alan.

`unittest` modülü ve test yazma hakkında daha fazla bilgi için bkz. [python 2,7 belgeleri](https://docs.python.org/2/library/unittest.html) veya [Python 3,7 belgeleri](https://docs.python.org/3/library/unittest.html) (Python.org).

## <a name="run-tests"></a>Testleri çalıştırma

İçinde **Test Gezgini** çeşitli şekillerde testleri çalıştırabilirsiniz:

- **Tümünü Çalıştır** açıkça (tabi filtreleri) gösterilen tüm testleri çalıştırır.
- **Çalıştırma** menüsü başarısız, geçirilen veya çalıştırılmadı testleri bir grup olarak çalıştırmak için komutlar sağlar.
- Bir veya daha fazla test, seçtiğiniz sağ tıklatın ve seçin **seçili Testleri Çalıştır**.

Arka planda testleri çalıştırmak ve **Test Gezgini** tamamladıkça güncelleştirmeleri her testin durumu:

- Yeşil bir onay ve testi çalıştırmak için geçen süreyi testlerini geçme göster:

    ![Durum geçirilen test_A](../../media/unit-test-A-pass.png)

- Başarısız testleri Göster kırmızı çarpı işareti olan bir **çıkış** konsol çıktısı gösteren bir bağlantı ve `unittest` test çalıştırmasından çıktı:

    ![test_A durumu ile başarısız oldu.](../../media/unit-test-A-fail.png)

    ![test_A nedeniyle başarısız oldu](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Testlerde Hata Ayıkla

Birim testleri parçaları kod olduğundan, herhangi bir kod gibi hatalar tabidir ve bazen bir hata ayıklayıcıda çalıştırılması gerekir. Hata ayıklayıcıda kesme noktaları ayarlayın, değişkenleri inceleyebilir ve kodunuz içinde adım adım. Visual Studio tanılama araçları için birim testleri de sağlar.

> [!Note]
> Varsayılan olarak, test hata ayıklaması ptvsd 4 hata ayıklayıcısını kullanır. Bunun yerine ptvsd 3 kullanmak isterseniz, **araçlar** > **Seçenekler** ' de **eski hata ayıklayıcı kullan** seçeneğini seçerek **Python** > **hata ayıklama** > . 

Hata Ayıklamayı Başlat, kodunuzda ilk bir kesme noktası ayarlayın ve ardından test (veya bir seçim) sağ **Test Gezgini** seçip **seçilen Testlerde Hata Ayıkla**. Uygulama kodu için yaptığınız gibi visual Studio Python hata ayıklayıcıyı başlatır.

![Test hata ayıklama](../../media/unit-test-debugging.png)

Ayrıca **Seçili testler Için kod kapsamını analiz et**' i de kullanabilirsiniz. Daha fazla bilgi için [ne kadar kod test belirlemek için kod kapsamı kullanın](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).
