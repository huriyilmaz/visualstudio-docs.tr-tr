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
ms.openlocfilehash: 9843b47e38d5d33a25c455efe619dfcc033fb334
ms.sourcegitcommit: 9f6f63a2d76c6e579b4b67a96ec86faba99ad1df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71933432"
---
## <a name="discover-and-view-tests"></a>Testleri görüntülemek ve keşfedin

Kural gereği, Visual Studio ile başlayın, adları yöntemler olarak testleri belirler `test`. Bu davranışı görmek için aşağıdakileri yapın:

1. Açık bir [Python projesi](../../managing-python-projects-in-visual-studio.md) yüklü. Visual Studio'da, projenize sağ tıklayın, **Ekle** > **yeni öğe**, ardından **Test Jednotky Pythonu**  ardından **Ekle**.

1. Bu eylem oluşturur bir *test1.py* standart aktaran kod dosyasıyla `unittest` modülü, bir test sınıftan türetilen `unittest.TestCase`ve çağıran `unittest.main()` betiği doğrudan çalıştırırsanız:

    ```python

    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Gerekli ve açık değilse dosyayı kaydetmek **Test Gezgini** ile **Test** > **Windows** > **Test Gezgini**menü komutu.

1. **Test Gezgini** projeniz için testleri arar ve aşağıda gösterildiği gibi görüntüler. Bir testi çift kaynak dosyası açılır.

    ![Test Gezgini gösteren varsayılan test_A](../../media/unit-test-A.png)

1. Daha fazla test projenize eklemek gibi görünümde düzenleyebilirsiniz **Test Gezgini** kullanarak **gruplandırma ölçütü** araç çubuğundaki menüyü:

    ![Test Gezgini araç çubuğu menüsü grupla](../../media/unit-test-group-menu.png)

1. Bir metin de girebilirsiniz **arama** testleri adına göre filtrelemek için alan.

@No__t-0 modülü ve test yazma hakkında daha fazla bilgi için bkz. [python 2,7 belgeleri](https://docs.python.org/2/library/unittest.html) veya [Python 3,7 belgeleri](https://docs.python.org/3/library/unittest.html) (Python.org).

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

Hata Ayıklamayı Başlat, kodunuzda ilk bir kesme noktası ayarlayın ve ardından test (veya bir seçim) sağ **Test Gezgini** seçip **seçilen Testlerde Hata Ayıkla**. Uygulama kodu için yaptığınız gibi visual Studio Python hata ayıklayıcıyı başlatır.

![Test hata ayıklama](../../media/unit-test-debugging.png)

Ayrıca **Seçili testler Için kod kapsamını analiz et**' i de kullanabilirsiniz. Daha fazla bilgi için [ne kadar kod test belirlemek için kod kapsamı kullanın](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

### <a name="known-issues"></a>Bilinen sorunlar

- Hata ayıklama başlatıldığında, Visual Studio'yu başlatmak ve hata ayıklamayı durdurmak için görünür ve yeniden başlatın. Bu davranış beklenmektedir.
- Birden çok test hata ayıklaması yaparken, hata ayıklama oturumunu kesintiye uğratır her biri bağımsız olarak çalıştırılır.
- Visual Studio hata ayıklama sırasında bir testi başlatmak zaman zaman başarısız olur. Normalde, testi tekrar hata ayıklamaya çalışmadan başarılı olur.
- Hata ayıklama sırasında bir teste dışında adım filtrelenebilir `unittest` uygulaması. Normalde, sonraki adım, programın sonuna kadar çalışır ve hata ayıklamayı durdurur.
