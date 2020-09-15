---
title: requirements.txt ile paket bağımlılıklarını yönetme
description: Bir requirements.txt dosyası projenin bağımlılıklarını açıklar. Bir requirements.txt dosyası içeren bir proje alıyorsanız, bu bağımlılıkları tek bir adımda kolayca yükleyebilirsiniz.
ms.date: 03/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: b65072e7a9ffa5d3767a5ff66fda25b231c622ef
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90100545"
---
# <a name="manage-required-packages-with-requirementstxt"></a>Gerekli paketleri requirements.txt ile yönetme

Bir projeyi başkalarıyla paylaşıyorsanız, bir yapı sistemi kullanıyorsanız veya projeyi geri yüklemeniz gereken başka bir konuma kopyalamayı planlıyorsanız, projenin gerektirdiği harici paketleri belirtmeniz gerekir. Önerilen yaklaşım, bağımlı paketlerin gerekli sürümlerini yükleyen PIP komutlarının bir listesini içeren bir [requirements.txt dosyası](https://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org) kullanmaktır. En yaygın komut, `pip freeze > requirements.txt` bir ortamın geçerli paket listesini *requirements.txt*olarak kaydeder.

Teknik olarak, gereksinimleri izlemek için herhangi bir dosya adı kullanılabilir ( `-r <full path to file>` bir paket yüklenirken kullanılarak), ancak Visual Studio *requirements.txt*için özel destek sağlar:

- *requirements.txt* içeren bir proje yüklediyseniz ve bu dosyada listelenen tüm paketleri yüklemek istiyorsanız, **Çözüm Gezgini**' de **Python ortamları** düğümünü genişletin, ardından bir ortam düğümüne sağ tıklayıp **requirements.txt'den Install **' u seçin:

    ![requirements.txt şuradan yüklensin](media/environments/environments-requirements-txt-install.png)

- Bağımlılıkları bir sanal ortama yüklemek istiyorsanız önce bu ortamı oluşturup etkinleştirin, ardından **requirements.txt'Den Install ** komutunu kullanın. Sanal ortam oluşturma hakkında daha fazla bilgi için bkz. [sanal ortamları kullanma](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Bir ortama zaten gerekli olan tüm paketler varsa, **Çözüm Gezgini** bu ortama sağ tıklayıp gerekli dosyayı oluşturmak Için **requirements.txtoluştur ** ' u seçebilirsiniz. Dosya zaten varsa, güncelleştirme hakkında bir istem görünür:

    ![requirements.txt seçeneklerini Güncelleştir](media/environments/environments-requirements-txt-replace.png)

  - Tüm **dosyanın yerini değiştirme** , var olan tüm öğeleri, açıklamaları ve seçenekleri kaldırır.
  - **Mevcut girdileri Yenile** paket gereksinimlerini algılar ve sürüm belirticilerini Şu anda yüklü olan sürümle eşleşecek şekilde güncelleştirir.
  - **Girişleri güncelleştirme ve ekleme** , bulunan tüm gereksinimleri yeniler ve diğer tüm paketleri dosyanın sonuna ekler.

*requirements.txt* dosyaları bir ortamın gereksinimlerini dondurmak için düşünülbildiğinden, yüklenmiş tüm paketler kesin sürümlerle yazılır. Kesin sürümlerin kullanılması, ortamınızı başka bir bilgisayarda kolayca yeniden üretmenizi sağlar. Paketler, bir sürüm aralığıyla yüklenseler bile, başka bir paketin bağımlılığı olarak veya PIP dışında bir yükleyiciyle birlikte dahil edilir.

Bir paket, PIP tarafından yüklenemezse ve bir *requirements.txt* dosyasında görünürse, tüm yükleme başarısız olur. Bu durumda, bu paketi hariç tutmak için dosyayı el ile düzenleyin veya paketin yüklenebilir bir sürümüne başvurmak için [PIP 'nin seçeneklerini](https://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) kullanın. Örneğin, [`pip wheel`](https://pip.readthedocs.org/en/latest/reference/pip_wheel.html) bir bağımlılığı derlemek verequirements.txtseçeneği eklemek için kullanmayı tercih edebilirsiniz `--find-links <path>` : * *

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Arama yolları](search-paths.md)
- [Python ortamları penceresi başvurusu](python-environments-window-tab-reference.md)
