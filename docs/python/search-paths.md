---
title: Python arama yolları nasıl uygulanır?
description: Visual Studio, sistem genelindeki değişkenleri kullanmaktan kaçınmak için ortamlar ve projeler için arama yolları belirlemek için daha özel bir araç sağlar.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 37ce9d7b1853dfecc9e0ec33ca08c3c3fa0571e0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62428451"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Visual Studio Python arama yollarını nasıl kullanır?

Tipik Python kullanımında, ortam `PYTHONPATH` `IRONPYTHONPATH`değişkeni (veya, vb.) modül dosyaları için varsayılan arama yolunu sağlar. Diğer bir deyişle, `from <name> import...` bir `import <name>` veya deyim kullandığınızda, Python eşleşen bir ad için aşağıdaki konumları arar:

1. Python'un dahili modülleri.
1. Çalıştırdığınız Python kodunu içeren klasör.
1. "Modül arama yolu" olarak ilgili ortam değişkeni tarafından tanımlanır. (Temel Python belgelerindeki [Modül Arama Yolu](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) ve Çevre [değişkenlerine](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) bakın.)

Visual Studio, değişken tüm sistem için ayarlanmış olsa bile, arama yolu ortamı değişkenini yok sayar. Aslında tam *olarak* tüm sistem için ayarlandığı için göz ardı edilir ve böylece otomatik olarak yanıtlanamayan bazı soruları gündeme getirir: Başvurulan modüller Python 2.7 veya Python 3.6+ için midir? Standart kütüphane modüllerini geçersiz kılacaklar mı? Geliştirici bu davranışın farkında mı yoksa kötü amaçlı bir kaçırma girişimi mi?

Visual Studio böylece arama yollarını doğrudan hem ortamlarda hem de projelerde belirtmek için bir araç sağlar. Visual Studio'da çalıştırdığınız veya hata ayıkladığınız `PYTHONPATH` kod, (ve diğer eşdeğer değişkenler) değerindearama yolları alır. Visual Studio, arama yolları ekleyerek bu konumlardaki kitaplıkları inceler ve gerektiğinde onlar için IntelliSense veritabanları oluşturur (Visual Studio 2017 sürüm 15.5 ve daha önce; veritabanının oluşturulması kitaplık sayısına bağlı olarak biraz zaman alabilir).

Arama yolu eklemek **için, Çözüm Gezgini'ne**gidin, proje düğümünüzü genişletin, **Arama Yolları'na**sağ tıklayın, **Arama Yoluna Klasör Ekle'yi**seçin:

::: moniker range="vs-2017"
![Çözüm Gezgini'nde Arama Yollarında Arama Yolu komutuna Klasör ekleme](media/search-paths-command.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Çözüm Gezgini'nde Arama Yollarında Arama Yolu komutuna Klasör ekleme](media/search-paths-command-2019.png)
::: moniker-end

Bu komut, daha sonra eklemek için klasörü seçtiğiniz bir tarayıcı görüntüler.

Ortam `PYTHONPATH` değişkeniniz zaten istediğiniz klasör(ler)i içeriyorsa, **pythonpath'i arama yollarına** uygun bir kısayol olarak ekleyin'i kullanın.

Klasörler arama yollarına eklendikten sonra, Visual Studio bu yolları projeyle ilişkili herhangi bir ortam için kullanır. (Ortam Python 3'ü temel alıyorsa ve Python 2.7 modüllerine bir arama yolu eklemeye çalışıyorsanız hatalar görebilirsiniz.)

*.zip* veya *.egg* uzantılı dosyalar, **Arama Yolu'na Zip Arşivi Ekle** komutunu seçerek arama yolu olarak da eklenebilir. Klasörlerde olduğu gibi, bu dosyaların içeriği taranır ve IntelliSense'e sunulmuştur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar için requirements.txt kullanın](managing-required-packages-with-requirements-txt.md)
- [Python Ortamları pencere başvurusu](python-environments-window-tab-reference.md)
