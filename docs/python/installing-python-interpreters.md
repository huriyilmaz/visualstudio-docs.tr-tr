---
title: Python yorumlayıcılarını seçme ve yükleme
description: Uygulama içinde desteklenen Python yorumlayıcılarının tam listesi Visual Studio yükleyicilerinin nerede bulunarak ilgili kısa yönergelerle birlikte.
ms.date: 07/28/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 239a8f40aa669aa60853405621a0b335aabdcb3c
ms.sourcegitcommit: 879ba768364f3bfdaeb9004f740478489ab15c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114796170"
---
# <a name="install-python-interpreters"></a>Python yorumlayıcılarını yükleme

Varsayılan olarak, Python geliştirme iş yükünü Visual Studio 2017 ve sonraki bir sürümü de Python 3 (64 bit) yükler. İsteğe bağlı olarak, Yükleme altında açıklandığı gibi, Python 2 ve Python 3'un 32 bit ve 64 bit sürümlerini Miniconda (Visual Studio 2019) veya Anaconda 2/Anaconda 3 (Visual Studio 2017) ile birlikte [yükleyebilirsiniz.](installing-python-support-in-visual-studio.md)

::: moniker range=">=vs-2019"
Alternatif olarak, Ortam Ekle iletişim kutusundan standart python **yorumlayıcılarını yükleyebilirsiniz.** **Python** **Ortamları penceresinde veya** Python araç çubuğunda Ortam Ekle komutunu seçin, **Python** yükleme sekmesini seçin, hangi yorumlayıcıların yük kurulacaklarını belirtin ve Yükle'yi **seçin.**
::: moniker-end

Ayrıca, aşağıdaki tabloda listelenen yorumlayıcılardan herhangi birini yükleyicinin dışında el Visual Studio yükleyebilirsiniz. Örneğin, anaconda 3'ü Visual Studio yüklemeden önce yüklemiş olursanız, anaconda 3'ü Visual Studio yüklemenize gerek yok. Bir yorumlayıcıyı el ile de yükleyebilirsiniz. Örneğin, henüz yeni bir sürümü mevcutsa, bu sürüm yükleyicide Visual Studio yükleyebilirsiniz.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio Python sürüm 2.7'nin yanı sıra 3.5 ile 3.7 arasında bir sürümü destekler. Python'ın diğer Visual Studio yazılmış kodu düzenlemek için Visual Studio kullanmak mümkün ancak bu sürümler resmi olarak desteklenemez ve IntelliSense ve hata ayıklama gibi özellikler çalışmayabiliyor.
::: moniker-end

**2015 Visual Studio** önceki sürümler için yorumlayıcılardan birini el ile yüklemeniz gerekir.

> [!Note]
> Anaconda Visual Studio yükleme teklifi olsa da, Anaconda Deposu'nun dağıtımı ve ek paketleri kullanımınız [Anaconda Hizmet Koşulları'nın bağlı olduğu bir hizmettir.](https://www.anaconda.com/terms-of-service) Bu koşullar, bazı kuruluşların Anaconda'ya ticari lisans için ödemesi veya başka bir depoya erişmek için araçları yapılandırmasını gerekli olabilir. Daha fazla [bilgi için Conda kanalları](https://docs.conda.io/projects/conda/en/latest/user-guide/concepts/channels.html) belgelerine bakın.

Visual Studio (tüm sürümler), [pep 514 - Python](https://www.python.org/dev/peps/pep-0514/)kaydına göre kayıt defterini kontrol ederek yüklü olan her Python yorumlayıcısını ve ortamını otomatik Windows algılar. Python yüklemeleri genellikle **HKEY_LOCAL_MACHINE\SOFTWARE\Python** (32 bit) ve **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** (64 bit) altında ve ardından **PythonCore** (CPython) ve **ContinuumAnalytics** (Anaconda) gibi dağıtım düğümleri içinde bulunur.

Yüklü Visual Studio algılamazsanız bkz. Mevcut [bir ortamı el ile tanımlama.](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)

Visual Studio Python Ortamları penceresinde tüm bilinen [**ortamları**](managing-python-environments-in-visual-studio.md#the-python-environments-window) gösterir ve mevcut yorumlayıcılara yapılan güncelleştirmeleri otomatik olarak algılar.

| Yorumlayıcı | Description |
| --- | --- |
| [CPython](https://www.python.org/) | 32 bit ve 64 bit sürümlerde kullanılabilen "yerel" ve en yaygın kullanılan yorumlayıcı (32 bit önerilir). En son dil özelliklerini, maksimum Python paketi uyumluluğunu, tam hata ayıklama desteğini ve [IPython ile birlikte çalışabilirliği içerir.](https://ipython.org/) Ayrıca bkz. [Python 2 veya Python 3 kullanmalı musunuz?](https://wiki.python.org/moin/Python2orPython3). 2015 Visual Studio önceki sürümler Python 3.6+ sürümünü desteklemez ve Desteklenmeyen **Python sürüm 3.6** gibi hatalar ver. Bunun yerine Python 3.5 veya önceki bir sürüm kullanın. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | 32 bit ve 64 bit sürümlerde kullanılabilen, C#/F#/Visual Basic birlikte çalışma, .NET API'lerine erişim, standart Python hata ayıklama (ancak C++ karma mod hata ayıklaması değil) ve karışık IronPython/C# hata ayıklama sağlayan Bir .NET uygulaması. Ancak IronPython sanal ortamları desteklemez. |
| [Anaconda](https://anaconda.com) | Python tarafından desteklenen açık veri bilimi platformu, CPython'un en son sürümünü ve yüklemesi zor paketlerin çoğunu içerir. Aksi takdirde karar verediğiniz takdirde bunu öneririz. |
| [PyPy](https://www.pypy.org/) | Python'ın yüksek performanslı izleme JIT uygulaması, uzun süre çalışan programlar ve performans sorunlarını tanımlamanıza ama diğer çözümlerini bulamanıza neden olan durumlar için iyi bir uygulamadır. Gelişmiş hata Visual Studio için sınırlı destekle birlikte çalışır. |
| [Jython](https://www.jython.org/) | Python'ın Java Sanal Makinesi (JVM) uygulaması. IronPython'a benzer şekilde, Jython'da çalışan kod java sınıfları ve kitaplıkları ile etkileşime geçebilirsiniz, ancak CPython'a yönelik birçok kitaplık kullanamayabilirsiniz. Gelişmiş hata Visual Studio için sınırlı destekle birlikte çalışır. |

Python ortamları için yeni algılama biçimleri sağlamak isteyen geliştiriciler bkz. [PTVS Ortam Algılama](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (github.com).

## <a name="move-an-interpreter"></a>Yorumlayıcıyı taşıma

Dosya sistemini kullanarak mevcut yorumlayıcıyı yeni bir konuma taşımanız Visual Studio değişikliği otomatik olarak algılamaz.

- Python Ortamları penceresi aracılığıyla yorumlayıcının konumunu  belirttiydiniz, ardından yeni konumu tanımlamak için bu pencerede **Yapılandır** sekmesini kullanarak ortamını düzenleyin. Bkz. [Mevcut ortamı el ile tanımlama.](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)

- Yorumlayıcıyı bir yükleyici programı kullanarak yüklemişsanız, yorumlayıcıyı yeni konuma yeniden yüklemek için aşağıdaki adımları kullanın:

  1. Python yorumlayıcısını özgün konuma geri yükleme.
  2. Kayıt defteri girdilerini temiz alan yükleyicisini kullanarak yorumlayıcıyı kaldırın.
  3. Yorumlayıcıyı istenen konuma yeniden yükleyin.
  4. Yeni Visual Studio yeniden başlatın. Bu, eski konumun yerine yeni konumu otomatik olarak algılaması gerekir.

Bu işlemden sonra, yorumlayıcının konumunu (kullanıcı tarafından güncelleştirilir) Visual Studio kayıt defteri girdilerinin düzgün bir şekilde güncelleştirilmiş olması gerekir. Yükleyicinin kullanımı, mevcut olan diğer yan etkileri de işlemektedir.

## <a name="see-also"></a>Ayrıca bkz.

- [Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar requirements.txt kullanma](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
- [Python Ortamları pencere başvurusu](python-environments-window-tab-reference.md)
