---
title: Birim testi Python kodu
description: Visual Studio'da Python kodu için birim testi ayarlama, testleri bulmak, çalıştırmak ve hata ayıklamak için Test Gezgini özelliklerinden tam olarak faydalanabilir.
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 307a82b346f1fead5c78091544d0ccdfe8509e6c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156421"
---
## <a name="discover-and-view-tests"></a>Testleri bulma ve görüntüleme

Kural gereği, Visual Studio adları ile başlarken yöntemleri olarak `test` tanımlar. Bu davranışı görmek için şunları yapın:

1. Visual Studio'de yüklenen bir [Python](../../managing-python-projects-in-visual-studio.md) projesini açın, projenize sağ tıklayın, Yeni Öğe Ekle'yi ve ardından  >  Python **Birim Testi'ne** ve ardından Ekle'yi **seçin.**

1. Bu eylem, *standart test1.py* içeri aktaran, 'den bir test sınıfı türeten ve betiği doğrudan çalıştırıyorsanız çağıran bir dosya `unittest` `unittest.TestCase` `unittest.main()` oluşturur:

    ```python

    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Gerekirse dosyayı kaydedin, ardından **Test Gezgini'ni Test** Gezgini Windows   >    >  **komutuyla** açın.

1. **Test Gezgini** projenizi testler için arar ve aşağıda gösterildiği gibi görüntüler. Bir teste çift tıklarsanız kaynak dosyası açılır.

    ![Varsayılan ayarları gösteren Test Gezgini test_A](../../media/unit-test-A.png)

1. Projenize daha fazla test eklerken, araç çubuğundaki Grupla menüsünü kullanarak **Test** **Gezgini'nde** görünümü düzenleyebilirsiniz:

    ![Testler Gezgini Grupla araç çubuğu menüsü](../../media/unit-test-group-menu.png)

1. Testleri adlarına göre filtrelemek **için Arama** alanına metin de girebilirsiniz.

Modül ve test yazma `unittest` hakkında daha fazla bilgi için Python [2.7](https://docs.python.org/2/library/unittest.html) belgelerine veya [Python 3.7](https://docs.python.org/3/library/unittest.html) belgelerine (python.org).

## <a name="run-tests"></a>Testleri çalıştırma

**Test Gezgini'nde** testleri çeşitli yollarla çalıştırabilirsiniz:

- **Tüm Çalıştır açıkça** gösterilen tüm testleri çalıştırır (filtrelere tabi).
- Çalıştır **menüsü** başarısız, başarılı veya grup olarak test çalıştırmama komutlarını verir.
- Bir veya daha fazla test seçin, sağ tıklayın ve Seçili Testleri **Çalıştır'ı seçin.**

Testler arka planda çalışır ve **Test Gezgini** tamamlandığında her testin durumunu günceller:

- Testleri geçirme, yeşil bir onay işareti ve testi çalıştırmak için geçen zamanı gösterir:

    ![test_A durumu geçti](../../media/unit-test-A-pass.png)

- Başarısız testler, konsol çıkışını ve test **çalıştırması çıkışını** gösteren Çıkış `unittest` bağlantısıyla kırmızı çarpı gösterir:

    ![test_A durumu](../../media/unit-test-A-fail.png)

    ![test_A nedeniyle başarısız oldu](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Testlerde hata ayıklama

Birim testleri kod parçaları olduğundan, diğer kodlar gibi hatalara maruz olur ve bazen bir hata ayıklayıcısında çalıştırılaları gerekir. Hata ayıklayıcısında kesme noktaları ayarlayıcıda değişkenleri inceleyebilirsiniz ve kodda adım adım yol kullanabilirsiniz. Visual Studio birim testleri için tanılama araçları da sağlar.

Hata ayıklamayı başlatmak için kodunda bir başlangıç kesme noktası ayarlayın, ardından Test Gezgini'nde teste (veya seçime) sağ **tıklayın** ve Seçili Testlerde Hata **Ayıkla'yı seçin.** Visual Studio kodu için olduğu gibi Python hata ayıklayıcısını başlatır.

![Testte hata ayıklama](../../media/unit-test-debugging.png)

Seçilen Testler için Kod Kapsamı **Analiz Etme'i de kullanabilirsiniz.** Daha fazla bilgi için [bkz. Ne kadar kodun test olduğunu belirlemek için kod kapsamı kullanma.](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)

### <a name="known-issues"></a>Bilinen sorunlar

- Hata ayıklamayı başlatan Visual Studio başlat ve durdur gibi görünür ve sonra yeniden başlat. Bu beklenen bir davranıştır.
- Birden çok testte hata ayıklarken, her biri bağımsız olarak çalışır ve bu da hata ayıklama oturumunu kesintiye neden olur.
- Visual Studio hata ayıklama sırasında aralıklı olarak test başlatamaz. Normalde, testin hata ayıklaması yeniden başarılı olur.
- Hata ayıklama sırasında, uygulamaya bir test dışında adım `unittest` atılmalıdır. Normalde, sonraki adım programın sonuna kadar çalışır ve hata ayıklamayı durdurur.
