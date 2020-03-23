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
ms.openlocfilehash: 9843b47e38d5d33a25c455efe619dfcc033fb334
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71933432"
---
## <a name="discover-and-view-tests"></a>Testleri keşfedin ve görüntüleyin

Visual Studio, sözleşmeye göre testleri adları `test`ile başlayan yöntemler olarak tanımlar. Bu davranışı görmek için aşağıdakileri yapın:

1. Visual Studio'da yüklü bir [Python projesi](../../managing-python-projects-in-visual-studio.md) açın, projenize sağ tıklayın,**Yeni Öğe** **Ekle'yi** > seçin, ardından **Python Birim Testi'ni** seçin ve ardından **Ekle'yi**seçin.

1. Bu eylem, standart `unittest` modülü içeri aktaran, test sınıfı `unittest.TestCase`türeten ve komut `unittest.main()` dosyasını doğrudan çalıştırdığınızda çağıran kodlu *test1.py* bir dosya oluşturur:

    ```python

    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Gerekirse dosyayı kaydedin ve ardından**Test Windows** > **Test Gezgini** menüsü komutuyla Sına **Test** >  **Gezgini'ni** açın.

1. **Test Explorer** testiçin projenizde arama lar ve bunları aşağıda gösterildiği gibi görüntüler. Bir testi çift tıklatma, kaynak dosyasını açar.

    ![Varsayılan test_A gösteren Test Gezgini](../../media/unit-test-A.png)

1. Projenize daha fazla test ekledikçe, araç çubuğundaki menüye **göre Grup'u** kullanarak Test **Gezgini'ndeki** görünümü düzenleyebilirsiniz:

    ![Explorer Grubunu Araç Çubuğu menüsüne göre sınar](../../media/unit-test-group-menu.png)

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

Hata ayıklamaya başlamak için, kodunuzda bir başlangıç kesme noktası ayarlayın, ardından Test **Gezgini'nde** testi (veya seçimi) sağ tıklatın ve **Hata Ayıklama Seçili Testleri**seçin. Visual Studio, python hata ayıklayıcısını uygulama kodunda olduğu gibi başlatır.

![Testin hata ayıklama](../../media/unit-test-debugging.png)

**Ayrıca, Seçili Testler için Analiz Kodu Kapsamını**da kullanabilirsiniz. Daha fazla bilgi için [bkz.](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)

### <a name="known-issues"></a>Bilinen sorunlar

- Hata ayıklamaya başlarken, Visual Studio hata ayıklamayı başlatmak ve durdurmak için görünür ve sonra yeniden başlar. Bu beklenen bir davranıştır.
- Birden çok testhatayaparken, her biri bağımsız olarak çalıştırılır ve bu da hata ayıklama oturumunu kesintiye uğratır.
- Visual Studio hata ayıklama yaparken zaman zaman bir test başlatmak için başarısız olur. Normalde, testi yine hata ayıklama girişimi başarılı olur.
- Hata ayıklama yaparken, bir testten uygulamaya çıkmak `unittest` mümkündür. Normalde, bir sonraki adım programın sonuna kadar çalışır ve hata ayıklama durur.
