---
title: Birim testi Python kodu
description: Visual Studio 'da Python kodu için birim testi ayarlamak, test Gezgini özelliklerinden yararlanarak testleri bulmaya, çalıştırmaya ve hata ayıklamanıza yönelik tüm avantajlardan yararlanır.
ms.date: 09/18/2019
ms.topic: include
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e84b9de4eca681812209eb17f492d5e07522d3b5
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85292101"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Python projesi için test çerçevesini seçme

Visual Studio, Python, [UnitTest](https://docs.python.org/3/library/unittest.html) ve [pytest](https://pytest.org/en/latest/) için iki test çerçevesini destekler (visual Studio 2019 sürüm 16,3 ' den itibaren kullanılabilir). Varsayılan olarak, bir Python projesi oluşturduğunuzda hiçbir Framework seçilmemiş. Bir Framework belirtmek için Çözüm Gezgini içindeki proje adına sağ tıklayın ve **Özellikler** seçeneğini belirleyin. Bu, **Test** sekmesi aracılığıyla testleri yapılandırmanıza olanak sağlayan proje Tasarımcısını açar. Bu sekmede, projeniz için kullanmak istediğiniz test çerçevesini seçebilirsiniz. 

* **UnitTest** çerçevesi için, projenin kök dizini test bulma için kullanılır. Bu konum ve testlerin belirlenmesi için metin deseninin, **Test** sekmesinde Kullanıcı tarafından belirtilen değerler için değiştirilmesi de değiştirilebilir.
* **Pytest** çerçevesi için, test konumu ve dosya adı desenleri gibi test seçenekleri standart pytest. ini yapılandırma dosyası kullanılarak belirtilir. Daha fazla bilgi için [pytest başvuru belgelerine](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) bakın.

Çerçeve seçiminizi ve ayarlarını kaydettikten sonra test bulma işlemi Test Gezgini 'nde başlatılır. Test Gezgini penceresi zaten açık değilse, araç çubuğuna gidin ve **Test**  >  **Test Gezgini**' ni seçin.

## <a name="configure-testing-for-python-without-a-project"></a>Proje olmadan Python için testi yapılandırma
Visual Studio, Python kodu içeren [bir klasör açarak](../../quickstart-05-python-visual-studio-open-folder.md) mevcut Python kodunu bir proje olmadan çalıştırmanıza ve test etmenize olanak tanır. Bu koşullarda, testi yapılandırmak için bir **PythonSettings.js** dosyası kullanmanız gerekir. 
1. **Yerel klasör aç** seçeneğini kullanarak mevcut Python kodunuzu açın. 

   ![Visual Studio başlangıç ekranı](../../media/quickstart-open-folder/01-open-local-folder.png)

1. Çözüm Gezgini penceresinde, geçerli klasördeki tüm dosyaları göstermek için **tüm dosyaları göster** simgesine tıklayın.

   ![Tüm dosyaları göster düğmesi](../../media/unit-test-show-files.png)

1. **Yerel ayarlar** klasörü içindeki **PythonSettings.js** dosyasına gidin. Bu dosyayı **yerel ayarlar** klasöründe görmüyorsanız, el ile oluşturun.
   
1. **Testframework** alanını ayarlar dosyasına ekleyin ve kullanmak istediğiniz test çerçevesine bağlı olarak **pytest** veya **UnitTest** olarak ayarlayın.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > **UnitTest** Framework Için, **Unittestrootdirectory** ve **unittestmodel** alanları dosyada PythonSettings.jsbelirtilmemişse, sırasıyla "." ve "test *. Kopyala" varsayılan değerleri eklenir ve atanır.

1. Klasörünüz, testlerinizi içeren klasörden ayrı bir **src** dizini içeriyorsa, dosyadaki **PythonSettings.js** **SearchPaths** alanını kullanarak **src** klasörünün yolunu belirtin.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Belirtilen çerçeve için test bulmayı başlatmak üzere değişikliklerinizi dosyada PythonSettings.jskaydedin. 
   > [!Note]
   > Test Gezgini penceresi zaten **CTRL**  +  **R açıksa, bir** de bulmayı tetikler.

## <a name="discover-and-view-tests"></a>Testleri bulma ve görüntüleme

Varsayılan olarak, Visual Studio **UnitTest** ve **pytest** testlerini adları ile başlayan yöntemler olarak tanımlar `test` . Test bulmayı görmek için aşağıdakileri yapın:

1. Bir [Python projesi](../../managing-python-projects-in-visual-studio.md)açın.

1. Proje Visual Studio 'Ya yüklendikten sonra, Çözüm Gezgini ' de projenize sağ tıklayın ve Özellikler **Test** sekmesinden **UnitTest** veya **pytest** çerçevesini seçin.
   > [!Note]
   > Pytest çerçevesini kullanırsanız, standart pytest. ini yapılandırma dosyasını kullanarak test konumu ve dosya adı desenleri belirtebilirsiniz. Varsayılan olarak, çalışma alanı/proje klasörü, ve bir düzeniyle kullanılır `test_*py` `*_test.py` . Daha fazla bilgi için [pytest başvuru belgelerine](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) bakın.

1. Framework seçildikten sonra projeye tekrar sağ tıklayın ve **Add**  >  **Yeni öğe**Ekle ' yi seçin ve ardından **Ekle**' **yi seçin** .

1. Bu eylem, standart *test_1.py* modülünü içeri aktaran `unittest` , öğesinden bir test sınıfı türetilen `unittest.TestCase` ve `unittest.main()` komut dosyasını doğrudan çalıştırırsanız çağıran kod ile bir test_1. bir dosyası oluşturur:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Gerekirse dosyayı kaydedin **ve test** **Test Explorer**  >  **Test Gezgini** menü komutuyla test Gezgini ' ni açın.

1. **Test Gezgini** projenizde testler için arama yapar ve bunları aşağıda gösterildiği gibi görüntüler. Bir teste çift tıklamak, kaynak dosyasını açar.

    ![Varsayılan test_A gösteren test Gezgini](../../media/unit-test-a-2.png) 

1. Projenize daha fazla test eklediğinizde, araç çubuğundaki **grupla** menüsünü kullanarak **Test Gezgini** 'nde görünümü düzenleyebilirsiniz:

    ![Araç çubuğu menüsü Ile gezgin grubunu sınar](../../media/unit-test-group-menu-2.png) 

1. Testleri ada göre filtrelemek için **arama** alanına da metin girebilirsiniz.

Modül ve test yazma hakkında daha fazla bilgi için `unittest` bkz. [Python 2,7 belgeleri](https://docs.python.org/2/library/unittest.html) veya [python 3,7 belgeleri](https://docs.python.org/3/library/unittest.html) (Python.org).

## <a name="run-tests"></a>Testleri çalıştırma

**Test Gezgini** 'nde testleri çeşitli yollarla çalıştırabilirsiniz:

- **Tümünü Çalıştır** tüm gösterilen testleri açıkça çalıştırır (filtrelere tabidir).
- **Çalıştır** menüsü, bir grup olarak başarısız, geçti veya Çalıştır testleri çalıştırma komutları sağlar.
- Bir veya daha fazla test seçebilir, sağ tıklayıp **Seçili Testleri Çalıştır**' ı seçebilirsiniz.

Arka planda çalıştırılan testler ve **Test Gezgini** , tamamlandığında her testin durumunu güncelleştirir:

- Testleri geçirmek yeşil bir onay işareti ve testi çalıştırmak için geçen süreyi gösterir:

    ![test_A geçti durumu](../../media/unit-test-A-pass.png)

- Başarısız testler, konsol çıkışını ve Test çalıştırmasında çıktıyı gösteren bir **Çıkış** bağlantısı ile kırmızı bir çapraz bir çarpı gösterir `unittest` :

    ![başarısız test_A durumu](../../media/unit-test-A-fail.png)

    ![test_A neden ile başarısız oldu](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Hata ayıklama testleri

Birim testleri kod parçaları olduğundan, diğer tüm kodlar gibi hatalara tabidir ve bazen bir hata ayıklayıcıda çalıştırılması gerekir. Hata ayıklayıcıda kesme noktaları ayarlayabilir, değişkenleri inceleyebilir ve koddaki adımları izleyebilirsiniz. Visual Studio, birim testleri için de tanılama araçları sağlar.

> [!Note]
> Varsayılan olarak, test hata ayıklaması, Visual Studio 2017 için ptvsd 4 hata ayıklayıcısını kullanır (15,8 ve üzeri sürümler) ve Visual Studio 2019 için hata ayıklayıcı GPY (sürümler 16,5 ve üzeri). Bunun yerine ptvsd 3 kullanmak isterseniz, **Araçlar**seçenekler Python hata ayıklama üzerinde **eski hata ayıklayıcı kullan** seçeneğini belirleyebilirsiniz  >  **Options**  >  **Python**  >  **Debugging**. 

Hata ayıklamayı başlatmak için kodunuzda bir başlangıç kesme noktası ayarlayın ve **Test Gezgini** 'nde teste (veya bir seçime) sağ tıklayın ve **Seçili testlerin hatalarını ayıkla**' yı seçin. Visual Studio, Python hata ayıklayıcısını uygulama kodu gibi başlatır.

![Bir testte hata ayıklama](../../media/unit-test-debugging.png)

Ayrıca **Seçili testler Için kod kapsamını analiz et**' i de kullanabilirsiniz. Daha fazla bilgi için bkz. kod [kapsamını kullanarak ne kadar kodun test edildiğini belirleme](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).
