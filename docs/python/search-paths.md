---
title: Python arama yollarının uygulanma şekli
description: Visual Studio, sistem genelindeki değişkenleri kullanmaktan kaçınmak için ortamlar ve projeler için arama yolları belirtmek üzere daha belirli bir yol sağlar.
ms.date: 03/13/2019
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: d19506ab58e2003c5f0ae3b880dcdfa615c8f514
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972849"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Visual Studio Python arama yollarını nasıl kullanır

Tipik Python kullanımıyla, `PYTHONPATH` ortam değişkeni (veya `IRONPYTHONPATH` , vb.) modül dosyaları için varsayılan arama yolunu sağlar. Diğer bir deyişle, `from <name> import...` veya `import <name>` Ifadesini kullandığınızda Python, eşleşen bir ad için aşağıdaki konumları arar:

1. Python 'un yerleşik modülleri.
1. Çalıştırmakta olduğunuz Python kodunu içeren klasör.
1. Geçerli ortam değişkeni tarafından tanımlanan "modül arama yolu". (Çekirdek Python belgelerindeki [Modül arama yoluna](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) ve [ortam değişkenlerine](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) bakın.)

Visual Studio, tüm sistem için değişken ayarlanmış olsa bile, arama yolu ortam değişkenini yoksayar. Tam olarak tüm sistem için ayarlandığı ve bu nedenle otomatik olarak yanıtlanamayan belirli sorulara sahip *olduğu* için, aslında göz ardı edilir: Python 2,7 veya Python 3.6 + için başvurulan modüller. Standart Kitaplık modüllerini geçersiz kılabilir mi? Geliştirici bu davranışın farkındadır mi veya kötü amaçlı bir ele geçirme girişimi mi?

Visual Studio bu nedenle, arama yollarını doğrudan hem ortamlarda hem de projelerde belirtmek için bir yol sağlar. Visual Studio çalıştırdığınız veya hata ayıklamanın bir kodu, `PYTHONPATH` (ve diğer eşdeğer değişkenler) değerinde arama yolları alır. arama yolları ekleyerek Visual Studio, bu konumlardaki kitaplıkları inceler ve gerektiğinde ıntellisense veritabanlarını (Visual Studio 2017 sürüm 15,5 ve önceki bir sürümü) oluşturur. veritabanını oluşturmak, kitaplıkların sayısına bağlı olarak biraz zaman alabilir.

Bir arama yolu eklemek için **Çözüm Gezgini** gidin, proje düğümünüz ' ı genişletin, **arama yolları**' na sağ tıklayın ve **arama yolunda klasör ekle**' yi seçin:

::: moniker range="vs-2017"
![Çözüm Gezgini arama yollarında arama yolu komutuna klasör ekle](media/search-paths-command.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Çözüm Gezgini arama yollarında arama yolu komutuna klasör ekle](media/search-paths-command-2019.png)
::: moniker-end

Bu komut, daha sonra dahil edilecek klasörü seçebileceğiniz bir tarayıcı görüntüler.

`PYTHONPATH`Ortam değişkeniniz istediğiniz klasörü (ler) zaten içeriyorsa, uygun bir kısayol olarak **arama eklemek Için PYTHONPATH Ekle** seçeneğini kullanın.

klasörler arama yollarına eklendikten sonra, Visual Studio bu yolları projeyle ilişkili tüm ortamlar için kullanır. (Ortam Python 3 ' ü temel alıyorsa ve Python 2,7 modüllerine bir arama yolu eklemeye çalıştığınızda hata görebilirsiniz.)

*.zip* veya *. yumurg* uzantılı dosyalar, arama yolu olarak, **arama yolu olarak da ZIP arşivi Ekle** komutuna seçilerek de eklenebilir. Klasörlerde olduğu gibi, bu dosyaların içeriği taranır ve IntelliSense için kullanılabilir hale getirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar için requirements.txt kullanma](managing-required-packages-with-requirements-txt.md)
- [Python ortamları penceresi başvurusu](python-environments-window-tab-reference.md)
