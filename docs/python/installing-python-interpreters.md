---
title: Python yorumlayıcıları seçme ve bunları yüklemesi
description: Visual Studio 'da yükleyicilerinin nerede bulunacağı hakkında kısa yönergeler içeren Python yorumlayıcıları 'nın kapsamlı bir listesi.
ms.date: 06/05/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: fb1c657789e232307672d494710f330758780a67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540731"
---
# <a name="install-python-interpreters"></a>Python yorumlayıcılarını yükleme

Varsayılan olarak, Python geliştirme iş yükünü Visual Studio 2017 ve üzeri sürümlerde yüklemek Python 3 ' ü (64 bit) de yüklüyor. İsteğe bağlı olarak, [yükleme](installing-python-support-in-visual-studio.md)bölümünde açıklandığı gibi, Python 2 ve Python 3 ' ün 32-bit ve 64-bit sürümlerini, miniconda (visual Studio 2019) veya Anaconda 2/Anaconda 3 (visual Studio 2017) ile birlikte yüklemeyi tercih edebilirsiniz.

::: moniker range=">=vs-2019"
Alternatif olarak, **ortam ekle** iletişim kutusundan standart Python yorumlayıcıları yükleyebilirsiniz. **Python ortamları** penceresinde veya Python araç çubuğunda **ortam ekle** komutunu seçin, **Python yükleme** sekmesini seçin, hangi yorumlayıcılara yükleneceğini belirtin ve **yükleme**' yi seçin.
::: moniker-end

Ayrıca, Visual Studio yükleyicisi dışında aşağıdaki tabloda listelenen yorumlayıcıların herhangi birini el ile yükleyebilirsiniz. Örneğin, Visual Studio 'Yu yüklemeden önce Anaconda 3 ' ü yüklediyseniz, Visual Studio yükleyicisi aracılığıyla yeniden yüklemeniz gerekmez. Örneğin, daha önce Visual Studio yükleyicide görünmeyen daha yeni bir sürümü gibi, bir yorumlayıcı el ile de yükleyebilirsiniz.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio, Python sürüm 2,7 ' i ve sürüm 3,5 ve üstünü destekler. Python 'un diğer sürümlerinde yazılmış kodu düzenlemek için Visual Studio 'Yu kullanmak mümkün olsa da, bu sürümler resmi olarak desteklenmez ve IntelliSense ve hata ayıklama gibi özellikler çalışmayabilir.
::: moniker-end

**Visual Studio 2015 ve önceki sürümlerde**yorumlayıcıdan birini el ile yüklemelisiniz.

Visual Studio (tüm sürümler), [Windows kayıt defterinde Pep 514-Python kaydına](https://www.python.org/dev/peps/pep-0514/)göre kayıt defterini denetleyerek, yüklenen her Python yorumlayıcısını ve ortamını otomatik olarak algılar. Python yüklemeleri genellikle **HKEY_LOCAL_MACHINE \SOFTWARE\Python** (32-bit) ve **HKEY_LOCAL_MACHINE \SOFTWARE\WOW6432Node\Python** (64-bit) altında bulunur ve bu, **PythonCore** (Cpithon) ve **devamlıanaliz** (Anaconda) gibi dağıtım için düğümler içinde bulunur.

Visual Studio yüklü bir ortamı algılamazsa, bkz. [var olan bir ortamı el ile saptama](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

Visual Studio, [**Python ortamları**](managing-python-environments-in-visual-studio.md#the-python-environments-window) penceresinde bilinen tüm ortamları gösterir ve mevcut yorumlayıcılara yönelik güncelleştirmeleri otomatik olarak algılar.

| Sından | Description |
| --- | --- |
| [CPython](https://www.python.org/) | 32-bit ve 64 bit sürümlerde kullanılabilen "yerel" ve en yaygın olarak kullanılan yorumlayıcı (32-bit önerilir). En son dil özelliklerini, en yüksek Python paketi uyumluluğunu, tam hata ayıklama desteğini ve [IPython](https://ipython.org/)ile birlikte çalışabilirliği içerir. Ayrıca bkz: [Python 2 veya Python 3 mi kullanmalıyım?](https://wiki.python.org/moin/Python2orPython3). Visual Studio 2015 ve önceki sürümleri Python 3.6 + ' yı desteklemediğine ve **Desteklenmeyen Python sürümü 3,6**gibi hatalara olanak sunmadığını unutmayın. Bunun yerine Python 3,5 veya önceki bir sürümünü kullanın. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | 32-bit ve 64 bit sürümlerde kullanılabilen, .NET API 'Leri, standart Python hata ayıklama (C++ karışık mod hata ayıklama) ve karışık IronPython/C# hata ayıklama sağlayan bir Python .NET uygulamasıdır. Ancak IronPython, sanal ortamları desteklemez. |
| [Anaconda](https://www.continuum.io) | Python tarafından desteklenen açık bir veri bilimi platformu, en son Cpne Thon sürümü ve çok sayıda yüklemeyi zor olan paketleri içerir. Aksi takdirde karar vermeniz önerilir. |
| [PyPy](https://www.pypy.org/) | Uzun süre çalışan programlar ve performans sorunlarını tanımlayabileceğiniz ancak diğer çözümleri bulamadığınız durumlar için iyi olan, Python 'un yüksek performanslı izleme JıT uygulamasıdır. Visual Studio ile birlikte çalışarak gelişmiş hata ayıklama özellikleri için sınırlı destek sağlar. |
| [Jyıthon](https://www.jython.org/) | Java Sanal Makinesi (JVM) üzerinde Python 'un bir uygulamasıdır. IronPython 'a benzer şekilde, Jithon 'da çalışan kod Java sınıfları ve kitaplıkları ile etkileşime geçebilir, ancak Cpithon için tasarlanan birçok kitaplığı kullanmayabilir. Visual Studio ile birlikte çalışarak gelişmiş hata ayıklama özellikleri için sınırlı destek sağlar. |

Python ortamları için yeni algılama biçimleri sağlamak isteyen geliştiriciler, bkz. [PTV ortamı algılama](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (GitHub.com).

## <a name="move-an-interpreter"></a>Yorumlayıcı taşıma

Varolan bir yorumlayıcıyı dosya sistemini kullanarak yeni bir konuma taşırsanız, Visual Studio değişikliği otomatik olarak algılamaz.

- Başlangıçta **Python ortamları** penceresi aracılığıyla yorumlayıcı konumunu belirttiyseniz, yeni konumu belirlemek için bu penceredeki **Yapılandır** sekmesini kullanarak ortamını düzenleyin. Bkz. [var olan bir ortamı el ile tanımla](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

- Yorumlayıcı 'yı bir yükleyici programı kullanarak yüklediyseniz, yorumlayıcı yeni konuma yeniden yüklemek için aşağıdaki adımları kullanın:

  1. Python yorumlayıcı 'yı özgün konumuna geri yükleyin.
  2. Kayıt defteri girdilerini temizleyen yükleyicisini kullanarak yorumlayıcı 'yı kaldırın.
  3. Yorumlayıcı 'yı istenen konuma yeniden yükleyin.
  4. Eski konumun yerine yeni konumu otomatik olarak algılamamalıdır ve Visual Studio 'Yu yeniden başlatın.

Bu işlemin ardından, Visual Studio 'nun kullandığı yorumlayıcı konumunu tanımlayan kayıt defteri girdilerinin doğru şekilde güncelleştirildiğini sağlar. Bir yükleyicinin kullanılması, mevcut olabilecek diğer yan etkileri de işler.

## <a name="see-also"></a>Ayrıca bkz.

- [Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar için requirements.txt kullanma](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
- [Python ortamları penceresi başvurusu](python-environments-window-tab-reference.md)
