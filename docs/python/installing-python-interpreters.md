---
title: Python yorumlayıcılarını seçin ve yükleyin
description: Visual Studio'da desteklenen python yorumlayıcılarının tam listesi ve yükleyicilerini nerede bulacakları hakkında kısa talimatlar.
ms.date: 06/05/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 13290aef7acfe599c7693af4be771c625e713596
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75735824"
---
# <a name="install-python-interpreters"></a>Python yorumlayıcılarını yükleme

Varsayılan olarak, Visual Studio 2017'de Python geliştirme iş yükünü yükler ve daha sonra Python 3'ü (64 bit) yükler. Python 2 ve Python 3'ün 32 bit ve 64 bit sürümlerini, Miniconda (Visual Studio 2019) veya Anaconda 2/Anaconda 3 (Visual Studio 2017) ile birlikte [yüklemede](installing-python-support-in-visual-studio.md)açıklandığı şekilde yüklemeyi tercih edebilirsiniz.

::: moniker range=">=vs-2019"
Alternatif olarak, **Çevre Ekle** iletişim kutusundan standart python yorumlayıcıları yükleyebilirsiniz. **Python Ortamları** penceresinde veya Python araç çubuğunda **Ortam Ekle** komutunu seçin, **Python yükleme** sekmesini seçin, hangi yorumlayıcıları yükleyeceklerini belirtin ve **Yükle'yi**seçin.
::: moniker-end

Ayrıca, aşağıdaki tabloda listelenen tercümanlardan herhangi birini Visual Studio yükleyicisinin dışına el ile yükleyebilirsiniz. Örneğin, Visual Studio'yu yüklemeden önce Anaconda 3'ü yüklediyseniz, Visual Studio yükleyicisi aracılığıyla yeniden yüklemeniz gerekmez. Örneğin, Visual Studio yükleyicisinde henüz görünmeyen daha yeni bir kullanılabilir sürümü varsa, bir tercümanı el ile de yükleyebilirsiniz.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio Python sürüm 2.7'nin yanı sıra sürüm 3.5 ve daha büyük olan sürümleri destekler. Python'un diğer sürümlerinde yazılan kodu yeniden kullanmak için Visual Studio'yu kullanmak mümkün olsa da, bu sürümler resmi olarak desteklenmez ve IntelliSense ve hata ayıklama gibi özellikler çalışmayabilir.
::: moniker-end

**Visual Studio 2015 ve daha önce**için, çevirmenlerden birini el ile yüklemeniz gerekir.

Visual Studio (tüm sürümler) otomatik olarak pep 514 göre kayıt defteri kontrol ederek yüklü Python tercüman ve çevre algılar [- Windows kayıt defterinde Python kaydı.](https://www.python.org/dev/peps/pep-0514/) Python yüklemeleri genellikle **HKEY_LOCAL_MACHINE\SOFTWARE\Python** (32-bit) ve **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python** (64-bit) altında, daha sonra **PythonCore** (CPython) ve **ContinuumAnalytics** (Anaconda) gibi dağıtım düğümleri içinde bulunur.

Visual Studio yüklü bir ortamı algılamazsa, [bkz.](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)

Visual [**Studio, Python Ortamları**](managing-python-environments-in-visual-studio.md#the-python-environments-window) penceresinde bilinen tüm ortamları gösterir ve varolan yorumlayıcıların güncelleştirmelerini otomatik olarak algılar.

| Yorumlayıcı | Açıklama |
| --- | --- |
| [CPython](https://www.python.org/) | 32 bit ve 64 bit sürümlerinde (32 bit önerilir) "yerel" ve en sık kullanılan yorumlayıcı. En son dil özelliklerini, maksimum Python paket uyumluluğunu, tam hata ayıklama desteğini ve [IPython](https://ipython.org/)ile interop'u içerir. Ayrıca bakınız: [Python 2 veya Python 3 kullanmalı mıyım?](https://wiki.python.org/moin/Python2orPython3) Visual Studio 2015 ve önceki sürümleri desteklemediğini ve **Desteklenmeyen python sürüm 3.6**gibi hatalar yapabileceğini unutmayın. Bunun yerine Python 3.5 veya daha erken kullanın. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | 32 bit ve 64 bit sürümlerinde kullanılabilen Python'un .NET uygulaması, C#/F#/Visual Basic interop'una erişim, .NET API'lerine erişim, standart Python hata ayıklama (c++ karışık mod hata ayıklama ve karışık IronPython/C# hata ayıklama. Ancak IronPython sanal ortamları desteklemez. |
| [Anaconda](https://www.continuum.io) | Python tarafından desteklenen açık veri bilimi platformu, CPython'un en son sürümünü ve yüklenmesi zor paketlerin çoğunu içerir. Başka türlü karar veremezseniz tavsiye ediyoruz. |
| [Pypy](https://www.pypy.org/) | Python'un performans sorunlarını tanımladığınız ancak başka çözümler bulamadığınız uzun soluklu programlar ve durumlar için iyi olan Yüksek performanslı JIT uygulamasını izleme. Visual Studio ile çalışır ancak gelişmiş hata ayıklama özellikleri için sınırlı destek ile. |
| [Jython](https://www.jython.org/) | Java Sanal Makine (JVM) Python bir uygulama. IronPython'a benzer şekilde, Jython'da çalışan kod Java sınıfları ve kitaplıklarıyla etkileşime girebiliyor, ancak CPython için tasarlanmış birçok kitaplık kullanamayabilir. Visual Studio ile çalışır ancak gelişmiş hata ayıklama özellikleri için sınırlı destek ile. |

Python ortamları için yeni algılama biçimleri sağlamak isteyen geliştiriciler, [Bkz. PTVS Çevre Algılama](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (github.com).

## <a name="move-an-interpreter"></a>Bir tercümanı taşıma

Dosya sistemini kullanarak varolan bir yorumciyi yeni bir konuma taşırsanız, Visual Studio değişikliği otomatik olarak algılamaz.

- Gönderenin konumunu **Python Ortamları** penceresinden ilk olarak belirttiyseniz, yeni konumu tanımlamak için bu penceredeki **Yapılaşı** sekmesini kullanarak ortamını tıklatın. Bkz. [Varolan bir ortamı El ile tanımlayın.](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)

- Bir yükleyici programı kullanarak yorumlayıcıyı yüklediyseniz, yorumlayıcıyı yeni konumda yeniden yüklemek için aşağıdaki adımları kullanın:

  1. Python yorumlayıcısını özgün konumuna geri yükleyin.
  2. Kayıt defteri girişlerini temizleyen yükleyicisini kullanarak yorumlayıcıyı kaldırın.
  3. İstenilen yere tercümanı yeniden yükleyin.
  4. Eski konumun yerine yeni konumu otomatik olarak algılaması gereken Visual Studio'yu yeniden başlatın.

Bu işlem den sonra, Visual Studio'nun kullandığı yorumlayıcının konumunu tanımlayan kayıt defteri girişlerinin düzgün bir şekilde güncelleştirilmesini sağlar. Bir yükleyici kullanarak da var olabilir diğer yan etkileri işler.

## <a name="see-also"></a>Ayrıca bkz.

- [Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar için requirements.txt kullanın](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
- [Python Ortamları pencere başvurusu](python-environments-window-tab-reference.md)
