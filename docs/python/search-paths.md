---
title: Python arama yollarının uygulanma şekli
description: Visual Studio, sistem genelindeki değişkenleri kullanmaktan kaçınmak için ortamlar ve projeler için arama yolları belirtmek üzere daha özel bir yol sağlar.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 10430c6eba57c97dd46a706d0ec2f532cd08d4f3
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801171"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Visual Studio, Python arama yollarını nasıl kullanır?

Tipik Python kullanımıyla, `PYTHONPATH` ortam değişkeni (veya `IRONPYTHONPATH` , vb.) modül dosyaları için varsayılan arama yolunu sağlar. Diğer bir deyişle, `from <name> import...` veya `import <name>` Ifadesini kullandığınızda Python, eşleşen bir ad için aşağıdaki konumları arar:

1. Python 'un yerleşik modülleri.
1. Çalıştırmakta olduğunuz Python kodunu içeren klasör.
1. Geçerli ortam değişkeni tarafından tanımlanan "modül arama yolu". (Çekirdek Python belgelerindeki [Modül arama yoluna](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) ve [ortam değişkenlerine](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) bakın.)

Ancak, tüm sistem için değişken ayarlanmış olsa bile, Visual Studio arama yolu ortam değişkenini yoksayar. Tam olarak tüm sistem için ayarlandığı ve bu nedenle otomatik olarak yanıtlanamayan belirli sorulara sahip *olduğu* için, aslında göz ardı edilir: Python 2,7 veya Python 3.6 + için başvurulan modüller. Standart Kitaplık modüllerini geçersiz kılabilir mi? Geliştirici bu davranışın farkındadır mi veya kötü amaçlı bir ele geçirme girişimi mi?

Böylece Visual Studio, arama yollarını doğrudan hem ortamlarda hem de projelerde belirtmek için bir yol sağlar. Visual Studio 'da çalıştırdığınız veya hata ayıklamanın bir kodu, `PYTHONPATH` (ve diğer eşdeğer değişkenler) değerinde arama yolları alır. Arama yolları ekleyerek, Visual Studio bu konumlardaki kitaplıkları inceler ve gerektiğinde IntelliSense veritabanları oluşturur (Visual Studio 2017 sürüm 15,5 ve daha önceki bir sürümü), veritabanını oluşturmak, kitaplıkların sayısına bağlı olarak biraz zaman alabilir.

Bir arama yolu eklemek için **Çözüm Gezgini**gidin, proje düğümünüz ' ı genişletin, **arama yolları**' na sağ tıklayın ve **arama yolunda klasör ekle**' yi seçin:

::: moniker range="vs-2017"
![Çözüm Gezgini arama yollarında arama yolu komutuna klasör ekle](media/search-paths-command.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Çözüm Gezgini arama yollarında arama yolu komutuna klasör ekle](media/search-paths-command-2019.png)
::: moniker-end

Bu komut, daha sonra dahil edilecek klasörü seçebileceğiniz bir tarayıcı görüntüler.

`PYTHONPATH`Ortam değişkeniniz istediğiniz klasörü (ler) zaten içeriyorsa, uygun bir kısayol olarak **arama eklemek Için PYTHONPATH Ekle** seçeneğini kullanın.

Klasörler arama yollarına eklendikten sonra, Visual Studio bu yolları projeyle ilişkili tüm ortamlar için kullanır. (Ortam Python 3 ' ü temel alıyorsa ve Python 2,7 modüllerine bir arama yolu eklemeye çalıştığınızda hata görebilirsiniz.)

*. Zip* veya *. Egg* uzantılı dosyalar, arama yolu olarak, **arama yolu olarak ZIP arşivi Ekle** komutuyla da eklenebilir. Klasörlerde olduğu gibi, bu dosyaların içeriği taranır ve IntelliSense için kullanılabilir hale getirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar için requirements.txt kullanma](managing-required-packages-with-requirements-txt.md)
- [Python ortamları penceresi başvurusu](python-environments-window-tab-reference.md)
