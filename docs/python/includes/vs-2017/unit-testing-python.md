---
title: Birim testi Python kodu
description: Visual Studio 'da Python kodu için birim testi ayarlamak, test Gezgini özelliklerinden yararlanarak testleri bulmaya, çalıştırmaya ve hata ayıklamanıza yönelik tüm avantajlardan yararlanır.
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 032732f19855b9ba5c97c2e5281e8385f9ace3be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535349"
---
## <a name="discover-and-view-tests"></a>Testleri bulma ve görüntüleme

Kurala göre, Visual Studio Testleri adları ile başlayan yöntemler olarak tanımlar `test` . Bu davranışı görmek için aşağıdakileri yapın:

1. Visual Studio 'da yüklü bir [Python projesi](../../managing-python-projects-in-visual-studio.md) açın, projenize sağ tıklayın, **Add**  >  **Yeni öğe**Ekle ' yi seçin, sonra **Python birim testi** ' ni ve ardından **Ekle**' yi seçin.

1. Bu eylem, standart *test1.py* modülünü içeri aktaran `unittest` , öğesinden bir test sınıfı türetilen `unittest.TestCase` ve `unittest.main()` betiği doğrudan çalıştırırsanız çağıran bir test1.py dosyası oluşturur:

    ```python

    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Gerekirse dosyayı kaydedin ve test **Gezgini** ' **ni test**  >  **Windows**  >  **Gezgini** menü komutuyla açın.

1. **Test Gezgini** projenizde testler için arama yapar ve bunları aşağıda gösterildiği gibi görüntüler. Bir teste çift tıklamak, kaynak dosyasını açar.

    ![Varsayılan test_A gösteren test Gezgini](../../media/unit-test-A.png)

1. Projenize daha fazla test eklediğinizde, araç çubuğundaki **grupla** menüsünü kullanarak **Test Gezgini** 'nde görünümü düzenleyebilirsiniz:

    ![Araç çubuğu menüsü Ile gezgin grubunu sınar](../../media/unit-test-group-menu.png)

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

Hata ayıklamayı başlatmak için kodunuzda bir başlangıç kesme noktası ayarlayın ve **Test Gezgini** 'nde teste (veya bir seçime) sağ tıklayın ve **Seçili testlerin hatalarını ayıkla**' yı seçin. Visual Studio, Python hata ayıklayıcısını uygulama kodu gibi başlatır.

![Bir testte hata ayıklama](../../media/unit-test-debugging.png)

Ayrıca **Seçili testler Için kod kapsamını analiz et**' i de kullanabilirsiniz. Daha fazla bilgi için bkz. kod [kapsamını kullanarak ne kadar kodun test edildiğini belirleme](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

### <a name="known-issues"></a>Bilinen sorunlar

- Hata ayıklama başlatılırken, Visual Studio başlatma ve hata ayıklamayı durdurma gibi görünür ve sonra yeniden başlatılır. Bu beklenen bir davranıştır.
- Birden çok teste hata ayıklarken, her biri bağımsız olarak çalıştırılır ve hata ayıklama oturumunu keser.
- Hata ayıklama sırasında Visual Studio zaman zaman bir test başlatamaz. Normal olarak, testi yeniden ayıklamaya çalışırken başarılı olur.
- Hata ayıklarken, uygulamaya bir test dışına geçmek mümkündür `unittest` . Normalde, sonraki adım programın sonuna kadar çalışır ve hata ayıklamayı sonlandırır.
