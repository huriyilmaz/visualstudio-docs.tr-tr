---
title: Gereksinimler.txt dosyasıyla paket bağımlılıklarını yönetme
description: requirements.txt dosyası, projenin bağımlılıklarını açıklar. Gereksinimleri.txt dosyası içeren bir proje alırsanız, bu bağımlılıkları kolayca tek bir adımda yükleyebilirsiniz.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a1853df63354801ebf0413d3c8707135cb9bb800
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62535729"
---
# <a name="manage-required-packages-with-requirementstxt"></a>Gerekli paketleri gereksinimleri ile yönetin.txt

Bir projeyi başkalarıyla paylaşıyorsanız, bir yapı sistemi kullanıyorsanız veya projeyi ortamı geri yüklemeniz gereken başka bir konuma kopyalamayı planlıyorsanız, projenin gerektirdiği dış paketleri belirtmeniz gerekir. Önerilen yaklaşım, bağlı paketlerin gerekli sürümlerini yükleyen pip için komutların listesini içeren bir [requirements.txt dosyası](https://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org) kullanmaktır. En yaygın komut, bir ortamın geçerli paket listesini `pip freeze > requirements.txt` *requirements.txt'ye*kaydeden komutdur.

Teknik olarak, herhangi bir dosya adı gereksinimleri `-r <full path to file>` izlemek için kullanılabilir (bir paket yüklerken kullanarak), ancak Visual Studio *requirements.txt*için özel destek sağlar:

- *gereksinimleri.txt* içeren bir proje yüklediyseniz ve bu dosyada listelenen tüm paketleri yüklemek istiyorsanız, Solution **Explorer'da Python Ortamları** düğümünü genişletmek istiyorsanız, bir ortam düğümüne sağ tıklayın ve **requirements.txt'den Yükle'yi**seçin: **Solution Explorer**

    ![requirements.txt'den yükleyin](media/environments/environments-requirements-txt-install.png)

- Bağımlılıkları sanal bir ortama yüklemek istiyorsanız, önce bu ortamı oluşturun ve etkinleştirin, ardından **requirements.txt komutunu** yükleyin. Sanal ortam oluşturma hakkında daha fazla bilgi için [bkz.](selecting-a-python-environment-for-a-project.md#use-virtual-environments)

- Bir ortamda zaten gerekli tüm paketler yüklüyse, **Solution Explorer'da** bu ortama sağ tıklayabilir ve gerekli dosyayı oluşturmak için **requirements.txt** oluştur'u seçebilirsiniz. Dosya zaten varsa, dosyanın nasıl güncelleştirilene ne kadar güncelleştirilene göre bir istem görüntülenir:

    ![gereksinimleri güncelleştirin.txt seçenekleri](media/environments/environments-requirements-txt-replace.png)

  - **Dosyanın tamamını değiştirin,** var olan tüm öğeleri, açıklamaları ve seçenekleri kaldırır.
  - **Varolan girişleri yenilemek** paket gereksinimlerini algılar ve sürüm belirteçlerini şu anda yüklediğiniz sürümle eşleşecek şekilde güncelleştirir.
  - **Güncelleştirme ve ekleme girişleri** bulunan gereksinimleri yeniler ve dosyanın sonuna diğer tüm paketleri ekler.

*requirements.txt* dosyaları bir ortamın gereksinimlerini dondurmayı amaçladığından, yüklenen tüm paketler kesin sürümlerle yazılır. Hassas sürümleri kullanmak, ortamınızı başka bir bilgisayarda kolayca yeniden oluşturabilmesini sağlar. Paketler, başka bir paketin bağımlılığı olarak veya pip dışında bir yükleyiciyle bir sürüm aralığıyla yüklenseler bile dahildir.

Bir paket pip tarafından yüklenemezse ve *requirements.txt* dosyasında görünürse, tüm yükleme başarısız olur. Bu durumda, bu paketi hariç tutmak veya paketin yüklenebilir bir sürümüne başvurmak için [pip seçeneklerini](https://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) kullanmak için dosyayı el ile edin. Örneğin, bir bağımlılık derlemek ve gereksinimlerinize [`pip wheel`](https://pip.readthedocs.org/en/latest/reference/pip_wheel.html) `--find-links <path>` seçeneği eklemek için kullanmayı tercih edebilirsiniz.txt : *requirements.txt*

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

- [Visual Studio'da Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Arama yolları](search-paths.md)
- [Python Ortamları pencere başvurusu](python-environments-window-tab-reference.md)
