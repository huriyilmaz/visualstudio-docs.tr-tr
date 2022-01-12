---
title: Python paket bağımlılıklarını yönetme
description: Pip freeze > requirements.txt python paketi bağımlılıklarını yönetme Visual Studio.
ms.date: 12/11/2021
ms.custom: devdivchpfy22
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 67eca5ffd74b630af90f55a0e631c2f09fad7351
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135805110"
---
# <a name="manage-required-python-packages-with-requirementstxt"></a>Gerekli Python paketlerini requirements.txt

Projeyi başkalarla paylaşıyorsanız, derleme sistemi kullanıyorsanız veya projeyi ortamı geri yüklemeniz gereken başka bir konuma kopyalamayı planlıyorsanız, projenin gerektirdiği dış paketleri belirtmeniz gerekir. Önerilen yaklaşım, bağımlı [ paketlerin gerekli sürümlerinirequirements.txt](https://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) pip komutlarının listesini içeren birrequirements.txt dosyası (readthedocs.org) kullanmaktır. En yaygın komut, `pip freeze > requirements.txt` ortamın geçerli paket listesini ** requirements.txt.

Teknik olarak, herhangi bir dosya adı gereksinimleri izlemek için kullanılabilir (bir paket yüklerken kullanarak) ancak Visual Studio için belirli `-r <full path to file>` *requirements.txt:*

- *requirements.txt* içeren bir proje yüklemiş ve bu dosyada listelenen tüm paketleri yüklemek isterseniz, **Çözüm Gezgini'daki** **Python** Ortamları düğümünü genişletin, ardından bir ortam düğümüne sağ tıklayın ve requirements.txt'den **yükle'yi seçin:**

    :::moniker range=">=vs-2019"
    ![requirements.txt-2019'dan yükleme](media/environments/environments-requirements-txt-install.png)
    :::moniker-end

- Bağımlılıkları bir sanal ortama yüklemek için önce bu ortamı oluşturun ve etkinleştirin, ardından Install **from requirements.txt** komutunu kullanın. Sanal ortam oluşturma hakkında daha fazla bilgi için [bkz. Sanal ortamları kullanma.](selecting-a-python-environment-for-a-project.md#use-virtual-environments)

- Bir ortamda gerekli tüm paketler zaten yüklüyse, gerekli dosyayı oluşturmak  için Çözüm Gezgini'da bu ortama sağ tık requirements.txt **Oluştur'u** seçin. Dosya zaten varsa, dosyanın nasıl güncelleştiril burasıyla ilgili bir istem görüntülenir:

    :::moniker range=">=vs-2022"
    ![Yeni requirements.txt](media/environments/environments-requirements-txt-install-2022.png)
    :::moniker-end

    :::moniker range="<=vs-2019"
    ![Yeni requirements.txt](media/environments/environments-requirements-txt-install.png)
    :::moniker-end

    ![Güncelleştirme requirements.txt güncelleştirme](media/environments/environments-requirements-txt-replace.png)

  - **Dosyanın tamamını** değiştir seçeneği mevcut olan tüm öğeleri, yorumları ve seçenekleri kaldırır.
  - **Mevcut girdileri yenileme** paket gereksinimlerini algılar ve sürüm belirleyicilerini şu anda yüklü olan sürümle eşlenecek şekilde günceller.
  - **Güncelleştirme ve ekleme girişleri** bulunan tüm gereksinimleri yeniler ve diğer tüm paketleri dosyanın sonuna ekler.

Bu *requirements.txt* tüm yüklü paketlerin kesin sürümlerini içerir ve bu dosyaları kullanarak bir ortamın gereksinimlerini dondurabilirsiniz. Hassas sürümleri kullanarak ortamınızı başka bir bilgisayarda kolayca yeniden üretebilirsiniz. Gereksinimler dosyaları, bir sürüm aralığıyla, başka bir paketin bağımlılığı olarak veya pip dışında bir yükleyiciyle yüklenmiş olsalar bile paketleri içerir.

pip bir paket yüklemezse ve paket bir requirements.txtgörünürse, yüklemenin tamamı başarısız olur. Bu durumda, bu paketi dışlamak veya paketin yüklü bir sürümüne başvurmak için [pip'in](https://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) seçeneklerini kullanmak için dosyayı el ile düzenleyin. Örneğin, bir bağımlılığı derlemek için kullanmayı ve seçeneğini [`pip wheel`](https://pip.readthedocs.org/en/latest/reference/pip_wheel.html) `--find-links <path>`requirements.txt: **

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
