---
title: Python desteğini yükleme
description: Visual Studio 2017, 2015, 2013, 2012 ve 2010'da seçenekler ve yükleme konumları dahil olmak üzere Python Araçlar Görsel Stüdyo için (PTVS) nasıl yüklenir?
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 15869119ea867e41d3b91a1f046d1ffb995cd4e4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75398430"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Windows'da Visual Studio'da Python desteği nasıl yüklenir?

Visual Studio için Python desteğini (Visual Studio veya PTVS için Python Araçları olarak da bilinir) yüklemek için Visual Studio'nun sizin sürümünüzle eşleşen bölümdeki yönergeleri izleyin:

- [Visual Studio 2017 ve Visual Studio 2019](#visual-studio-2017-and-2019)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 ve daha önce](#visual-studio-2013-and-earlier)

Yükleme adımlarını izledikten sonra Python desteğini hızlı bir şekilde test etmek `2+2`için **Alt**+**I** tuşuna basarak **ve** . Çıktısını `4`görmüyorsanız, adımlarınızı yeniden denetleyin.

> [!Tip]
> Python iş yükü, şablonları, giriş şablonseçeneklerini keşfetmek ve proje ve dosya oluşturmak için grafiksel bir kullanıcı arabirimi sağlayan yararlı Cookiecutter uzantısını içerir. Ayrıntılar için Bkz. [Cookiecutter'ı kullan.](using-python-cookiecutter-templates.md)

> [!Note]
> Python desteği şu anda Visual Studio for Mac'te mevcut değildir, ancak Visual Studio Code aracılığıyla Mac ve Linux'ta kullanılabilir. [Sorular ve yanıtlara](overview-of-python-tools-for-visual-studio.md#questions-and-answers)bakın.

<a name="visual-studio-2017-and-2019"></a>
## <a name="visual-studio-2019-and-visual-studio-2017"></a>Visual Studio 2019 ve Visual Studio 2017

1. En son Visual Studio yükleyicisini indirin ve çalıştırın. Visual Studio zaten yüklüyse, Visual Studio Installer'ı çalıştırın, **Değiştir** seçeneğini seçin [(Bkz. Görsel Stüdyoyu Değiştir)](../install/modify-visual-studio.md)ve adım 2'ye gidin.

    > [!div class="nextstepaction"]
    > [Visual Studio 2019 Topluluğu'nu Yükleyin](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Topluluk sürümü bireysel geliştiriciler, sınıf öğrenimi, akademik araştırma ve açık kaynak geliştirme içindir. Diğer kullanımlar için [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) veya Visual Studio [2019 Enterprise'ı](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)yükleyin.

1. Yükleyici, belirli geliştirme alanları için ilgili seçenek grupları olan iş yüklerinin bir listesini sunar. Python için **Python geliştirme** iş yükünü seçin.

    ![Visual Studio yükleyicisinde Python geliştirme iş yükü](media/installation-python-workload.png)

    ::: moniker range="vs-2017"
    İsteğe bağlı: Veri bilimi yle çalışıyorsanız, **Veri bilimi ve analitik uygulamalar** iş yükünü de göz önünde bulundurun. Bu iş yükü Python, R ve F# dilleri için destek içerir. Daha fazla bilgi için [bkz: Veri bilimi ve analitik uygulamalar iş yükü.](data-science-and-analytical-applications-workload.md)

    > [!Note]
    > Python ve Data Science iş yükleri yalnızca Visual Studio 2017 sürüm 15.2 ve sonraki sürümlerde kullanılabilir.

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    İsteğe bağlı: Veri bilimi yle çalışıyorsanız, **Veri bilimi ve analitik uygulamalar** iş yükünü de göz önünde bulundurun. Bu iş yükü Python ve F# dilleri için destek içerir. Daha fazla bilgi için [bkz: Veri bilimi ve analitik uygulamalar iş yükü.](data-science-and-analytical-applications-workload.md)
    ::: moniker-end

1. Yükleyicinin sağ tarafında, istenirse ek seçenekler seçti. Varsayılan seçenekleri kabul etmek için bu adımı atlayın.

    ::: moniker range="vs-2017"
    ![Visual Studio yükleyicisinde Python geliştirme seçenekleri](media/installation-python-options.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    ![Visual Studio 2019 yükleyicisinde Python geliştirme seçenekleri](media/installation-python-options-2019.png)
    ::: moniker-end

    ::: moniker range="<=vs-2017"
    | Seçenek | Açıklama |
    | --- | --- |
    | Python dağılımları | Python 2, Python 3, Miniconda, Anaconda2 ve Anaconda3 dağıtımlarının 32 bit ve 64 bit varyantları gibi kullanılabilir seçeneklerin herhangi bir birleşimini seçin. Her biri dağıtımın yorumlayıcısını, çalışma saatini ve kitaplıklarını içerir. Anaconda, özellikle, önceden yüklenmiş paketler geniş bir yelpazede içeren açık bir veri bilimi platformudur. (Dağıtımeklemek veya kaldırmak için istediğiniz zaman Visual Studio yükleyicisine dönebilirsiniz.)  **Not**: Visual Studio yükleyicisinin dışına bir dağıtım yüklediyseniz, buradaki eşdeğer seçeneği denetlemenize gerek yoktur. Visual Studio, varolan Python yüklemelerini otomatik olarak algılar. [Bkz. Python Ortamları penceresi.](managing-python-environments-in-visual-studio.md#the-python-environments-window) Ayrıca, Python'un yükleyicide gösterilenden daha yeni bir sürümü varsa, bu sürümü ayrı olarak yükleyebilirsiniz ve Visual Studio bunu algılar. |
    | **Cookiecutter şablon desteği** | Şablonları, giriş şablonseçeneklerini keşfetmek ve proje ve dosya oluşturmak için Cookiecutter grafik arabirimi'ni yükler. Bkz. [Çerez Kesici uzantısını kullanın.](using-python-cookiecutter-templates.md) |
    | **Python web desteği** | HTML, CSS ve JavaScript düzenleme desteğinin yanı sıra Şişe, Flask ve Django çerçevelerini kullanan projeler için şablonlar da dahil olmak üzere web geliştirme için araçlar yükler. [Bkz. Python web proje şablonları.](python-web-application-project-templates.md) |
    | **Python IoT desteği** | Python'u kullanarak Windows IoT Core geliştirmeyi destekler. |
    | **Python yerel geliştirme araçları** | Python için yerel uzantıları geliştirmek için C++ derleyicisini ve diğer gerekli bileşenleri yükler. Bkz. [Python için C++ uzantısı oluştur.](working-with-c-cpp-python-in-visual-studio.md) Ayrıca tam C++ desteği için C++ iş **yüküne sahip Masaüstü geliştirmeyi** yükleyin. |
    | **Azure Bulut Hizmetleri temel araçları** | Python'daki geliştirici Azure Bulut Hizmetleri için ek destek sağlar. Bkz. [Azure bulut hizmeti projeleri.](python-azure-cloud-service-project-template.md) |
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    | Seçenek | Açıklama |
    | --- | --- |
    | Python dağılımları | Python 2, Python 3, Miniconda, Anaconda2 ve Anaconda3 dağıtımlarının 32 bit ve 64 bit varyantları gibi kullanılabilir seçeneklerin herhangi bir birleşimini seçin. Her biri dağıtımın yorumlayıcısını, çalışma saatini ve kitaplıklarını içerir. Anaconda, özellikle, önceden yüklenmiş paketler geniş bir yelpazede içeren açık bir veri bilimi platformudur. (Dağıtımeklemek veya kaldırmak için istediğiniz zaman Visual Studio yükleyicisine dönebilirsiniz.)  **Not**: Visual Studio yükleyicisinin dışına bir dağıtım yüklediyseniz, buradaki eşdeğer seçeneği denetlemenize gerek yoktur. Visual Studio, varolan Python yüklemelerini otomatik olarak algılar. [Bkz. Python Ortamları penceresi.](managing-python-environments-in-visual-studio.md#the-python-environments-window) Ayrıca, Python'un yükleyicide gösterilenden daha yeni bir sürümü varsa, bu sürümü ayrı olarak yükleyebilirsiniz ve Visual Studio bunu algılar. |
    | **Cookiecutter şablon desteği** | Şablonları, giriş şablonseçeneklerini keşfetmek ve proje ve dosya oluşturmak için Cookiecutter grafik arabirimi'ni yükler. Bkz. [Çerez Kesici uzantısını kullanın.](using-python-cookiecutter-templates.md) |
    | **Python web desteği** | HTML, CSS ve JavaScript düzenleme desteğinin yanı sıra Şişe, Flask ve Django çerçevelerini kullanan projeler için şablonlar da dahil olmak üzere web geliştirme için araçlar yükler. [Bkz. Python web proje şablonları.](python-web-application-project-templates.md) |
    | **Python yerel geliştirme araçları** | Python için yerel uzantıları geliştirmek için C++ derleyicisini ve diğer gerekli bileşenleri yükler. Bkz. [Python için C++ uzantısı oluştur.](working-with-c-cpp-python-in-visual-studio.md) Ayrıca tam C++ desteği için C++ iş **yüküne sahip Masaüstü geliştirmeyi** yükleyin. |
    | **Azure Bulut Hizmetleri temel araçları** | Python'daki geliştirici Azure Bulut Hizmetleri için ek destek sağlar. Bkz. [Azure bulut hizmeti projeleri.](python-azure-cloud-service-project-template.md) |
    ::: moniker-end

1. Yüklemeden sonra yükleyici Visual Studio'yu değiştirme, başlatma, onarma veya kaldırma seçenekleri sunar. Değiştirilen **düğmesi,** yüklenen bileşenler için Visual Studio güncellemeleri kullanılabilir olduğunda **Güncelleştirme** düğmesini değiştirir. (Değiştir **Modify** seçeneği daha sonra açılır menüde kullanılabilir.) Ayrıca Visual Studio ve yükleyiciyi Windows **Başlat** menüsünden "Visual Studio"da arama yaparak başlatabilirsiniz.

    ![Visual Studio'yu yükleyiciden başlatma, değiştirme, değiştirme veya kaldırma](media/installation-vs-launch.png)

### <a name="troubleshooting"></a>Sorun giderme

Visual Studio'da Python'u yüklerken veya çalıştırabiliyorsanız aşağıdakileri deneyin:

- Python CLI kullanarak aynı hatanın oluşup oluşmadığını, yani *python.exe'yi* komut isteminden çalıştırıp çalıştırmayacağını belirleyin.
- Visual Studio yükleyicisinde [**Onarım**](../install/repair-visual-studio.md) seçeneğini kullanın.
- **Windows'daki Ayarlar** > **Uygulamaları & özellikleri** aracılığıyla Python'u onarın veya yeniden yükleyin.

**Örnek hata**: İnteraktif işlemi başlatamadı: System.ComponentModel.Win32Exception (0x80004005): Microsoft.PythonTools.Repl.PythonInteractiveEvaluator.d__43.MoveNext() adresinde bilinmeyen hata (0xc00000135).

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. **Microsoft Visual Studio 2015'i** seçerek Ve ardından **Değiştir'i**seçerek Visual Studio yükleyicisini Denetim Masası > Programları **ve Özellikleri**ile çalıştırın.

1. Yükleyicide **Değiştir'i**seçin.

1. Visual Studio için **Programlama Dilleri** > **Python Araçları** seçin ve sonra **Sonraki:**

    ![Visual Studio 2015 yükleyicisinde PTVS seçeneği](media/installation-vs2015.png)

1. Visual Studio kurulumu tamamlandıktan sonra, [seçtiğiniz bir Python tercümanı yükleyin.](installing-python-interpreters.md) Visual Studio 2015 sadece Python 3.5 ve daha önce destekler; sonraki sürümler **desteklenmeyen Python sürüm 3.6**gibi bir ileti oluşturur). Zaten yüklü bir yorumcunuz varsa ve Visual Studio bunu otomatik olarak algılamıyorsa, [bkz.](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 ve daha önce

1. Visual Studio sürümünüz için Visual Studio için Python Tools uygun sürümünü yükleyin:

    - Visual Studio 2013: [Visual Studio için PTVS 2.2.2 2013](https://github.com/Microsoft/PTVS/releases/v2.2.2). Visual Studio 2013'teki **Dosya** > **Yeni Proje** iletişim kutusu, bu işlem için size bir kısayol sağlar.
    - Visual Studio 2010 ve 2012: [Görsel Stüdyo 2010 ve 2012 için PTVS 2.1.1](https://github.com/Microsoft/PTVS/releases/v2.1.1)

1. [Seçtiğiniz bir Python yorumlayıcısı yükleyin.](installing-python-interpreters.md) Zaten yüklü bir yorumcunuz varsa ve Visual Studio bunu otomatik olarak algılamıyorsa, [bkz.](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)

## <a name="install-locations"></a>Konumları yükleme

Varsayılan olarak, Python desteği bilgisayardaki tüm kullanıcılar için yüklenir.

Visual Studio 2019 ve Visual Studio 2017 için Python iş yükü % ProgramFiles(x86)%\Microsoft Visual &lt;Studio&gt; &lt;&gt;<VS_version><VS_edition VS_version VS_version VS_version VS_version VS_version VS_version VS_version VS_version VS_version VS_version>*\\ Common7\IDE\Extensions\Microsoft\Python nerede VS_version 2019 veya 2017 ve VS_edition Topluluk, Profesyonel veya \\ * Kurumsal.

Visual Studio 2015 ve daha önceki için kurulum yolları aşağıdaki gibidir:

- 32 bit:
  - Yol: *%Program Files(x86)%\Microsoft \<Visual Studio VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\\<PTVS_ver>*
  - Yolun kayıt defteri konumu: **HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\\ VS_ver>\InstallDir<**
- 64 bit:
  - Yol: *%Program Dosyaları%\Microsoft \<Visual Studio VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\\<PTVS_ver>*
  - Yolun kayıt defteri konumu: **HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\\<VS_ver>\InstallDir**

burada:

- &lt;VS_ver:&gt;
  - Visual Studio 2015 için 14.0
  - Visual Studio 2013 için 12.0
  - Visual Studio 2012 için 11.0
  - Visual Studio 2010 için 10.0
- &lt;PTVS_ver&gt; 2.2.2, 2.1.1, 2.0, 1.5, 1.1 veya 1.0 gibi bir sürüm numarasıdır.

### <a name="user-specific-installations-15-and-earlier"></a>Kullanıcıya özel yüklemeler (1,5 ve öncesi)

Visual Studio 1.5 için Python Tools 1.5 ve daha önce yalnızca geçerli kullanıcı için yüklemeye izin verilir, bu durumda yükleme yolu *%LocalAppData%\Microsoft\VisualStudio\\<VS_ver>\Extensions\Microsoft\Python Tools for Visual\\ Studio<PTVS_ver VS_ver* &gt; ve &lt;PTVS_ver&gt; yukarıda açıklandığı gibi aynı olduğu &lt;>.
