---
title: Python yorumlayıcıları seçme ve bunları yüklemesi
description: Visual Studio sürümünde desteklenen Python yorumlayıcıları 'nın, yükleyicilerinin nerede bulabilecekleri hakkında kısa yönergeler içeren, kapsamlı bir listesi.
ms.date: 07/28/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 4ab809ea4aced244ecccd2ba04e7e3f0dbbda162
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106880"
---
# <a name="install-python-interpreters"></a>Python yorumlayıcılarını yükleme

varsayılan olarak, python geliştirme iş yükünün Visual Studio 2017 ve sonraki sürümlerinde yüklenmesi python 3 ' ü (64 bit) de yüklüyor. isterseniz, [yükleme](installing-python-support-in-visual-studio.md)bölümünde açıklandığı gibi, python 2 ve python 3 ' ün 32-bit ve 64-bit sürümlerini, miniconda (Visual Studio 2019) veya anaconda 2/anaconda 3 (Visual Studio 2017) ile birlikte yüklemeyi tercih edebilirsiniz.

::: moniker range=">=vs-2019"
Alternatif olarak, **ortam ekle** iletişim kutusundan standart Python yorumlayıcıları yükleyebilirsiniz. **Python ortamları** penceresinde veya Python araç çubuğunda **ortam ekle** komutunu seçin, **Python yükleme** sekmesini seçin, hangi yorumlayıcılara yükleneceğini belirtin ve **yükleme**' yi seçin.
::: moniker-end

ayrıca, aşağıdaki tabloda listelenen yorumlayıcıları Visual Studio yükleyicinin dışında el ile yükleyebilirsiniz. örneğin, Visual Studio yüklemeden önce anaconda 3 ' ü yüklediyseniz, Visual Studio yükleyicisi aracılığıyla yeniden yüklemeniz gerekmez. örneğin, daha önce Visual Studio yükleyicisinde görünmeyen daha yeni bir sürümü olan bir yorumlayıcı el ile de yükleyebilirsiniz.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio Python sürüm 2,7 ' i ve sürümüne 3,7 3,5 sürümünü destekler. Python 'un diğer sürümlerinde yazılmış kodu düzenlemek için Visual Studio kullanmak mümkün olsa da, bu sürümler resmi olarak desteklenmez ve ıntellisense ve hata ayıklama gibi özellikler çalışmayabilir.
::: moniker-end

**Visual Studio 2015 ve önceki sürümlerde**, yorumlayıcıdan birini el ile yüklemelisiniz.

> [!Note]
> anaconda dağıtımını yüklemek için Visual Studio, ancak, anaconda deposundan dağıtım ve ek paketler, [anaconda hizmet koşullarına](https://www.anaconda.com/terms-of-service)göre bağlanır. Bu koşullar, bazı kuruluşların ticari bir lisans için Anaconda ödeme yapılmasını gerektirebilir veya diğer bir depoya erişmek için araçları yapılandırabilir. Daha fazla bilgi için bkz. [Conda Channels belgeleri](https://docs.conda.io/projects/conda/en/latest/user-guide/concepts/channels.html) .

Visual Studio (tüm sürümler), [Windows kayıt defterindeki pep 514-Python kaydına](https://www.python.org/dev/peps/pep-0514/)göre kayıt defterini denetleyerek, yüklenen her Python yorumlayıcısını ve ortamını otomatik olarak algılar. Python yüklemeleri genellikle **HKEY_LOCAL_MACHINE\SOFTWARE\Python** (32-bit) ve **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** (64-bit) altında bulunur, daha sonra **PythonCore** (Cpetthon) ve **devamlıanaliz** (Anaconda) gibi dağıtım için düğümler içinde bulunur.

Visual Studio yüklü bir ortamı algılamazsa, bkz. [var olan bir ortamı el ile saptama](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

Visual Studio, [**Python ortamları**](managing-python-environments-in-visual-studio.md#the-python-environments-window) penceresinde bilinen tüm ortamları gösterir ve mevcut yorumlayıcılara yönelik güncelleştirmeleri otomatik olarak algılar.

| Sından | Açıklama |
| --- | --- |
| [CPython](https://www.python.org/) | 32-bit ve 64 bit sürümlerde kullanılabilen "yerel" ve en yaygın olarak kullanılan yorumlayıcı (32-bit önerilir). En son dil özelliklerini, en yüksek Python paketi uyumluluğunu, tam hata ayıklama desteğini ve [IPython](https://ipython.org/)ile birlikte çalışabilirliği içerir. Ayrıca bkz: [Python 2 veya Python 3 mi kullanmalıyım?](https://wiki.python.org/moin/Python2orPython3). Visual Studio 2015 ve önceki sürümleri Python 3.6 + ' yı desteklemediğine ve **desteklenmeyen Python sürümü 3,6** gibi hatalara sahip olabileceğini unutmayın. Bunun yerine Python 3,5 veya önceki bir sürümünü kullanın. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | 32 bit ve 64 bit sürümlerde kullanılabilen, .net apı 'leri, standart Python hata ayıklama (ancak C++ karışık mod hata ayıklama) ve karışık ıronpython/C# hata ayıklama Visual Basic sağlayan bir Python .net uygulamasıdır. Ancak IronPython, sanal ortamları desteklemez. |
| [Anaconda](https://anaconda.com) | Python tarafından desteklenen açık bir veri bilimi platformu, en son Cpne Thon sürümü ve çok sayıda yüklemeyi zor olan paketleri içerir. Aksi takdirde karar vermeniz önerilir. |
| [PyPy](https://www.pypy.org/) | Uzun süre çalışan programlar ve performans sorunlarını tanımlayabileceğiniz ancak diğer çözümleri bulamadığınız durumlar için iyi olan, Python 'un yüksek performanslı izleme JıT uygulamasıdır. Visual Studio ile birlikte çalışarak gelişmiş hata ayıklama özellikleri için sınırlı destek sağlar. |
| [Jyıthon](https://www.jython.org/) | Java Sanal Makinesi (JVM) üzerinde Python 'un bir uygulamasıdır. IronPython 'a benzer şekilde, Jithon 'da çalışan kod Java sınıfları ve kitaplıkları ile etkileşime geçebilir, ancak Cpithon için tasarlanan birçok kitaplığı kullanmayabilir. Visual Studio ile birlikte çalışarak gelişmiş hata ayıklama özellikleri için sınırlı destek sağlar. |

Python ortamları için yeni algılama biçimleri sağlamak isteyen geliştiriciler, bkz. [PTV ortamı algılama](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (GitHub.com).

## <a name="move-an-interpreter"></a>Yorumlayıcı taşıma

varolan yorumlayıcı dosya sistemini kullanarak yeni bir konuma taşırsanız, Visual Studio değişikliği otomatik olarak algılamaz.

- Başlangıçta **Python ortamları** penceresi aracılığıyla yorumlayıcı konumunu belirttiyseniz, yeni konumu belirlemek için bu penceredeki **Yapılandır** sekmesini kullanarak ortamını düzenleyin. Bkz. [var olan bir ortamı el ile tanımla](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

- Yorumlayıcı 'yı bir yükleyici programı kullanarak yüklediyseniz, yorumlayıcı yeni konuma yeniden yüklemek için aşağıdaki adımları kullanın:

  1. Python yorumlayıcı 'yı özgün konumuna geri yükleyin.
  2. Kayıt defteri girdilerini temizleyen yükleyicisini kullanarak yorumlayıcı 'yı kaldırın.
  3. Yorumlayıcı 'yı istenen konuma yeniden yükleyin.
  4. eski konumun yerine yeni konumu otomatik olarak algılaması gereken Visual Studio yeniden başlatın.

bu işlemin ardından, yorumlayıcı konumunu tanımlayan kayıt defteri girişlerinin Visual Studio tarafından düzgün şekilde güncelleştirildiğini sağlar. Bir yükleyicinin kullanılması, mevcut olabilecek diğer yan etkileri de işler.

## <a name="see-also"></a>Ayrıca bkz.

- [Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar için requirements.txt kullanma](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
- [Python ortamları penceresi başvurusu](python-environments-window-tab-reference.md)
