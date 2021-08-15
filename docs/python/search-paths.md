---
title: Python arama yollarının uygulanması
description: Visual Studio, sistem genelindeki değişkenlerin kullanımından kaçınmak için ortamlar ve projeler için arama yolları belirtmek için daha belirli bir yol sağlar.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 613dd8d47d4b566f2f02256a4fd981575cf10fb1acb9e117d948695edac6f2c4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121244881"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Python Visual Studio yollarını nasıl kullanır?

Tipik Python kullanımında ortam `PYTHONPATH` değişkeni (veya `IRONPYTHONPATH` vb.) modül dosyaları için varsayılan arama yolunu sağlar. Yani, bir veya `from <name> import...` `import <name>` deyimini kullanırken Python eşleşen bir ad için aşağıdaki konumları arar:

1. Python'ın yerleşik modülleri.
1. Üzerinde çalışan Python kodunu içeren klasör.
1. İlgili ortam değişkeni tarafından tanımlanan "modül arama yolu". (Temel Python [belgelerinde Modül](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) [Arama Yolu ve](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) Ortam değişkenlerine bakın.)

Visual Studio, tüm sistem için ayarlanmış olsa bile arama yolu ortam değişkenlerini yoksayar. Sistemin tamamı için ayarlanmış olduğundan  ve bu nedenle otomatik olarak yanıtlanmayacak belirli sorularla karşılansa da bu durum göz ardı edilir: Başvurulan modüller Python 2.7 veya Python 3.6+ için mi yazılmış? Standart kitaplık modüllerini geçersiz kacak mı? Geliştirici bu davranışın farkında mı yoksa kötü amaçlı bir ele geçirim girişimi mi?

Visual Studio bu nedenle hem ortamlarda hem de projelerde arama yollarını belirtmek için bir yol sağlar. Bu kodda çalıştırarak veya hata Visual Studio ( ve diğer eşdeğer değişkenler) değerinde `PYTHONPATH` arama yollarını alır. Visual Studio, arama yolları ekleyerek bu konumlarda bulunan kitaplıkları inceler ve gerektiğinde bunlar için IntelliSense veritabanları oluşturur (Visual Studio 2017 sürüm 15.5 ve önceki sürümler; veritabanının yapısı kitaplık sayısına bağlı olarak biraz zaman alır).

Bir arama yolu eklemek için, **Çözüm Gezgini'a** gidin, proje düğümünü genişletin, Arama Yolları'ne sağ tıklayın ve Arama Yoluna Klasör **Ekle'yi seçin:**

::: moniker range="vs-2017"
![Çözüm Gezgini'de Arama Yollarında Arama Yoluna Klasör Ekle Çözüm Gezgini](media/search-paths-command.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Çözüm Gezgini'de Arama Yollarında Arama Yoluna Klasör Ekle Çözüm Gezgini](media/search-paths-command-2019.png)
::: moniker-end

Bu komut, daha sonra dahil etmek istediğiniz klasörü seçen bir tarayıcı görüntüler.

Ortam değişkeniniz istediğiniz klasörleri zaten varsa, kolay bir kısayol olarak Yolları Aramak için `PYTHONPATH` **PYTHONPATH** Ekle'yi kullanın.

Klasörler arama yollarına eklendiktan sonra Visual Studio projeyle ilişkilendirilmiş tüm ortamlar için bu yolları kullanır. (Ortam Python 3'ü temel alarak Python 2.7 modüllerine bir arama yolu eklemeye çalışıyorsanız hatalarla karşınıza çıktı.)

Dosya veya *.zip* *uzantılı dosyalar,* Arama Yoluna Zip Arşivi Ekle komutu seçerek arama **yolları olarak da** eklenebilir. Klasörlerde olduğu gibi, bu dosyaların içerikleri taranır ve IntelliSense tarafından kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Python ortamlarını Visual Studio](managing-python-environments-in-visual-studio.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar requirements.txt kullanma](managing-required-packages-with-requirements-txt.md)
- [Python Ortamları pencere başvurusu](python-environments-window-tab-reference.md)
