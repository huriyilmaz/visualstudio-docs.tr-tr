---
title: Paket bağımlılıklarını requirements.txt
description: Bir requirements.txt dosyası projenin bağımlılıklarını açıklar. Bir dosya içeren bir proje requirements.txt, bu bağımlılıkları tek adımda kolayca yükleyebilirsiniz.
ms.date: 03/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 46d687b0684472300511ca9d6ff17dcbf34c925e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636974"
---
# <a name="manage-required-packages-with-requirementstxt"></a>Gerekli paketleri requirements.txt

Bir projeyi başkalarla paylaşıyorsanız, derleme sistemi kullanıyorsanız veya projeyi ortamı geri yüklemeniz gereken başka bir konuma kopyalamayı planlıyorsanız, projenin gerektirdiği dış paketleri belirtmeniz gerekir. Önerilen yaklaşım, bağımlı [ paketlerin gerekli sürümlerini yük](https://pip.readthedocs.org/en/latest/user_guide.html#requirements-files)requirements.txt pip komutlarının listesini içeren birrequirements.txt dosyası (readthedocs.org) kullanmaktır. En yaygın komut, `pip freeze > requirements.txt` ortamın geçerli paket listesini ** requirements.txt.

Teknik olarak, herhangi bir dosya adı gereksinimleri izlemek için kullanılabilir (bir paket yüklerken kullanarak) ancak Visual Studio için özel `-r <full path to file>` *destekrequirements.txt:*

- *requirements.txt* içeren bir proje yüklemiş ve bu dosyada listelenen tüm paketleri yüklemek isterseniz, **Çözüm Gezgini'daki** **Python** Ortamları düğümünü genişletin, ardından bir ortam düğümüne sağ tıklayın ve requirements.txt'den **yükle'yi seçin:**

    ![requirements.txt'dan yükleme](media/environments/environments-requirements-txt-install.png)

- Bağımlılıkları bir sanal ortama yüklemek için önce bu ortamı oluşturun ve etkinleştirin, ardından Install **from requirements.txt** komutunu kullanın. Sanal ortam oluşturma hakkında daha fazla bilgi için [bkz. Sanal ortamları kullanma.](selecting-a-python-environment-for-a-project.md#use-virtual-environments)

- Bir ortamda gerekli tüm paketler zaten yüklüyse, gerekli dosyayı oluşturmak  için Çözüm Gezgini'de bu ortama sağ tık requirements.txt **Oluştur'u** seçin. Dosya zaten varsa, dosyanın nasıl güncelleştiril burasıyla ilgili bir istem görüntülenir:

    ![Güncelleştirme requirements.txt güncelleştirme](media/environments/environments-requirements-txt-replace.png)

  - **Dosyanın tamamını** değiştir seçeneği mevcut olan tüm öğeleri, yorumları ve seçenekleri kaldırır.
  - **Mevcut girdileri yenileme** paket gereksinimlerini algılar ve sürüm belirleyicilerini şu anda yüklü olan sürümle eşlenecek şekilde günceller.
  - **Güncelleştirme ve ekleme girişleri** bulunan tüm gereksinimleri yeniler ve diğer tüm paketleri dosyanın sonuna ekler.

Tüm *requirements.txt* bir ortamın gereksinimlerini dondurmaya yönelik olduğundan, yüklü tüm paketler kesin sürümlerle yazılır. Hassas sürümleri kullanmak, ortamınızı başka bir bilgisayarda kolayca yeniden oluşturamanızı sağlar. Paketler bir sürüm aralığıyla, başka bir paketin bağımlılığı olarak veya pip dışında bir yükleyiciyle yüklenmiş olsalar bile dahil edilir.

Bir paket pip tarafından yüklenemezse ve bir paket *requirements.txt* görünüyorsa, yüklemenin tamamı başarısız olur. Bu durumda, bu paketi dışlamak veya paketin yüklü bir sürümüne başvurmak için [pip'in](https://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) seçeneklerini kullanmak için dosyayı el ile düzenleyin. Örneğin, bir bağımlılığı derlemek için kullanmayı ve seçeneğini kullanarak [`pip wheel`](https://pip.readthedocs.org/en/latest/reference/pip_wheel.html) `--find-links <path>`requirements.txt: **

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

- [Python ortamlarını Visual Studio](managing-python-environments-in-visual-studio.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Arama yolları](search-paths.md)
- [Python Ortamları pencere başvurusu](python-environments-window-tab-reference.md)
