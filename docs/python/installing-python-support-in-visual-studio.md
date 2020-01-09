---
title: Python desteğini yükleme
description: Python Tools için Visual Studio (PTVS) Visual Studio 2017, 2015, 2013, 2012 ve 2010, seçeneklerini ve yükleme konumlarını dahil olmak üzere kurulur.
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
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75398430"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Windows üzerinde Visual Studio'da Python desteğini yükleme

(PTVS ya da Visual Studio için Python araçları olarak da bilinir) Visual Studio için Python desteği yüklemek için Visual Studio sürümünüzle eşleşen bölümünde yer alan yönergeleri izleyin:

- [Visual Studio 2017 ve Visual Studio 2019](#visual-studio-2017-and-2019)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 veya önceki](#visual-studio-2013-and-earlier)

Hızlı bir şekilde yükleme adımlarını izleyerek sonra Python desteği test etmek için açık **Python etkileşimli** tuşuna basarak pencere **Alt**+**miyim** ve girme`2+2`. Çıkışı görmüyorsanız `4`, adımlarınızı yeniden denetleyin.

> [!Tip]
> Python iş yükü şablonları keşfedin, şablon seçeneklerini giriş ve projeleri ve dosyaları oluşturmak için bir grafik kullanıcı arabirimi sağlayan yararlı bir Cookiecutter uzantısını içerir. Ayrıntılar için bkz [kullanım Cookiecutter](using-python-cookiecutter-templates.md).

> [!Note]
> Python desteği, Mac için Visual Studio şu anda mevcut değildir, ancak Mac ve Linux'ta Visual Studio Code ile kullanılabilir. Bkz: [sorularını ve yanıtlarını](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="visual-studio-2017-and-2019"></a>
## <a name="visual-studio-2019-and-visual-studio-2017"></a>Visual Studio 2019 ve Visual Studio 2017

1. En son Visual Studio yükleyicisini indirip çalıştırın. Visual Studio zaten yüklüyse, Visual Studio Yükleyicisi'ni çalıştırın, seçin **Değiştir** seçeneği (bkz [değiştirme Visual Studio](../install/modify-visual-studio.md)) ve 2. adıma geçin.

    > [!div class="nextstepaction"]
    > [Visual Studio 2019 Community 'yi yükler](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Topluluk sürümü bireysel geliştiriciler, sınıfta öğrenim ortamı, akademik araştırma ve açık kaynak geliştirme için ' dir. Diğer kullanımlar için, [Visual studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) veya [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)'ı yükler.

1. Yükleyici belirli geliştirme alanlar için ilgili seçenekleri gruplarıdır iş yüklerinin bir listesini sunar. Python için seçin **Python geliştirme** iş yükü.

    ![Python geliştirme iş yüküyle Visual Studio](media/installation-python-workload.png)

    ::: moniker range="vs-2017"
    İsteğe bağlı: veri bilimi ile çalışıyorsanız, ayrıca düşünün **veri bilimi ve analitik uygulamalar** iş yükü. Bu iş yükü Python, R ve F# diller için destek içerir. Daha fazla bilgi için [veri bilimi ve analitik uygulamalar iş yükü](data-science-and-analytical-applications-workload.md).

    > [!Note]
    > Python ve veri bilimi iş yükleri ve üzeri yalnızca Visual Studio 2017 sürüm 15.2 ile kullanılabilir.

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    İsteğe bağlı: veri bilimi ile çalışıyorsanız, ayrıca düşünün **veri bilimi ve analitik uygulamalar** iş yükü. Bu iş yükü Python ve F# diller için destek içerir. Daha fazla bilgi için [veri bilimi ve analitik uygulamalar iş yükü](data-science-and-analytical-applications-workload.md).
    ::: moniker-end

1. Yükleyici sağ tarafında, istenirse ek seçenekler seçtiniz. Varsayılan seçenekleri kabul etmek için bu adımı atlayın.

    ::: moniker range="vs-2017"
    ![Visual Studio Yükleyicisi'nde Python geliştirme seçenekleri](media/installation-python-options.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    ![Visual Studio 2019 yükleyicisinde Python geliştirme seçenekleri](media/installation-python-options-2019.png)
    ::: moniker-end

    ::: moniker range="<=vs-2017"
    | Seçenek | Açıklama |
    | --- | --- |
    | Python dağıtımları | Birlikte çalışmayı planladığınız Python 2, Python 3, Miniconda, Anaconda2 ve Anaconda3 dağıtımlarının 32-bit ve 64-bit çeşitleri gibi kullanılabilir seçeneklerin herhangi bir birleşimini seçin. Her dağıtım'ın Yorumlayıcı, çalışma zamanı ve kitaplıkları içerir. Anaconda'yı özellikle çok çeşitli önceden yüklenmiş paketler içeren bir açık veri bilimi platformudur. (Dağıtımları eklemek veya kaldırmak için dilediğiniz zaman Visual Studio yükleyicisine dönebilirsiniz.)  **Note**: Visual Studio yükleyicisi dışında bir dağıtım yüklediyseniz, burada eşdeğer seçeneği denetlemeniz gerekmez. Visual Studio, mevcut Python yüklemeleri otomatik olarak algılar. Bkz: [Python ortamları penceresi](managing-python-environments-in-visual-studio.md#the-python-environments-window). Ayrıca, daha yeni bir Python sürümü olup olmadığını ne gösterilmemektedir Yükleyicisi'nde Visual Studio bunu algılar ve bu sürümü ayrı olarak yükleyebilirsiniz. |
    | **Cookiecutter şablonu desteği** | Şablonları keşfedin, şablon seçeneklerini giriş ve projeleri ve dosyaları oluşturma Cookiecutter grafik kullanıcı arabirimini yükler. Bkz: [Cookiecutter uzantısını kullanma](using-python-cookiecutter-templates.md). |
    | **Python web desteği** | HTML, CSS ve JavaScript desteği, Bottle, Flask ve Django çerçeveleri kullanarak projeleri şablonları yanı sıra düzenleme dahil olmak üzere web geliştirme araçları yükler. Bkz: [Python web projesi şablonları](python-web-application-project-templates.md). |
    | **Python IOT desteği** | Python kullanarak Windows IOT Core geliştirme destekler. |
    | **Python yerel geliştirme araçları** | C++ derleyicisi ve Python için yerel uzantılar geliştirmek için gereken diğer bileşenleri yükler. Bkz: [Python için C++ uzantısı oluşturma](working-with-c-cpp-python-in-visual-studio.md). Ayrıca yükleme **C++ ile masaüstü geliştirme** tam C++ desteği için iş yükü. |
    | **Azure Cloud Services temel araçları** | Azure bulut hizmetlerinde Python geliştirici için ek destek sağlar. Bkz: [Azure bulut hizmeti projeleri](python-azure-cloud-service-project-template.md). |
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    | Seçenek | Açıklama |
    | --- | --- |
    | Python dağıtımları | Birlikte çalışmayı planladığınız Python 2, Python 3, Miniconda, Anaconda2 ve Anaconda3 dağıtımlarının 32-bit ve 64-bit çeşitleri gibi kullanılabilir seçeneklerin herhangi bir birleşimini seçin. Her dağıtım'ın Yorumlayıcı, çalışma zamanı ve kitaplıkları içerir. Anaconda'yı özellikle çok çeşitli önceden yüklenmiş paketler içeren bir açık veri bilimi platformudur. (Dağıtımları eklemek veya kaldırmak için dilediğiniz zaman Visual Studio yükleyicisine dönebilirsiniz.)  **Note**: Visual Studio yükleyicisi dışında bir dağıtım yüklediyseniz, burada eşdeğer seçeneği denetlemeniz gerekmez. Visual Studio, mevcut Python yüklemeleri otomatik olarak algılar. Bkz: [Python ortamları penceresi](managing-python-environments-in-visual-studio.md#the-python-environments-window). Ayrıca, daha yeni bir Python sürümü olup olmadığını ne gösterilmemektedir Yükleyicisi'nde Visual Studio bunu algılar ve bu sürümü ayrı olarak yükleyebilirsiniz. |
    | **Cookiecutter şablonu desteği** | Şablonları keşfedin, şablon seçeneklerini giriş ve projeleri ve dosyaları oluşturma Cookiecutter grafik kullanıcı arabirimini yükler. Bkz: [Cookiecutter uzantısını kullanma](using-python-cookiecutter-templates.md). |
    | **Python web desteği** | HTML, CSS ve JavaScript desteği, Bottle, Flask ve Django çerçeveleri kullanarak projeleri şablonları yanı sıra düzenleme dahil olmak üzere web geliştirme araçları yükler. Bkz: [Python web projesi şablonları](python-web-application-project-templates.md). |
    | **Python yerel geliştirme araçları** | C++ derleyicisi ve Python için yerel uzantılar geliştirmek için gereken diğer bileşenleri yükler. Bkz: [Python için C++ uzantısı oluşturma](working-with-c-cpp-python-in-visual-studio.md). Ayrıca yükleme **C++ ile masaüstü geliştirme** tam C++ desteği için iş yükü. |
    | **Azure Cloud Services temel araçları** | Azure bulut hizmetlerinde Python geliştirici için ek destek sağlar. Bkz: [Azure bulut hizmeti projeleri](python-azure-cloud-service-project-template.md). |
    ::: moniker-end

1. Yükleme sonrasında, yükleyici değiştirmek, başlatma, onarın veya Visual Studio'yu kaldırmak için seçenekler sağlar. **Değiştir** düğmesi değişiklikleri **güncelleştirme** ne zaman Visual Studio güncelleştirmelerinin yüklü bileşenler için kullanılabilir. ( **Değiştir** seçeneği daha sonra açılan menüden kullanılabilir.) Ayrıca, "Visual Studio" üzerine arayarak Visual Studio ve yükleyiciyi Windows **Başlat** menüsünden de başlatabilirsiniz.

    ![Başlatma, değiştirme, değiştirme veya Visual Studio Yükleyicisi'nden kaldırılıyor](media/installation-vs-launch.png)

### <a name="troubleshooting"></a>Sorun giderme

Yüklerken veya Visual Studio'da Python çalıştırırken sorunlarla karşılaşırsanız, aşağıdakileri deneyin:

- Python CLI'yı kullanarak diğer bir deyişle, çalışan aynı hata oluşup oluşmadığını belirlemek *python.exe* bir komut isteminden.
- Kullanım [ **onarım** ](../install/repair-visual-studio.md) Visual Studio Yükleyicisi'nde seçeneği.
- Onarmak ya da Python aracılığıyla yeniden **ayarları** > **uygulamalar ve Özellikler** Windows içinde.

**Örnek hata**: etkileşimli işlem başlatılamadı: System.ComponentModel.Win32Exception (0x80004005): Bilinmeyen hata (0xc0000135) Microsoft.PythonTools.Repl.PythonInteractiveEvaluator.d__43.MoveNext().

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Visual Studio Yükleyicisi'ni çalıştırın **Denetim Masası > Programlar ve Özellikler**u seçerek **Microsoft Visual Studio 2015** ardından **değişiklik**.

1. Yükleyicide **Değiştir**.

1. Seçin **programlama dilleri** > **Visual Studio için Python Araçları** ardından **sonraki**:

    ![Visual Studio 2015 yükleyicisi PTVS seçeneği](media/installation-vs2015.png)

1. Visual Studio Kurulum tamamlandıktan sonra [tercih ettiğiniz bir Python yorumlayıcısını yükleyerek](installing-python-interpreters.md). Visual Studio 2015 yalnızca Python 3.5 ve önceki destekler; sonraki sürüm oluşturma gibi bir ileti **desteklenmeyen Python 3.6 sürümünü**). Bir yorumlayıcı yüklü ve Visual Studio zaten yüklüyse olmayan otomatik olarak algıla bkz [el ile bir ortamı tanımlamanız](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 veya önceki

1. Python Araçları'nün uygun sürümüne, Visual Studio için Visual Studio sürümünüz için yükleyin:

    - Visual Studio 2013: [Visual Studio 2013 Için PTV 2.2.2](https://github.com/Microsoft/PTVS/releases/v2.2.2). **Dosya** > **yeni proje** iletişim Visual Studio 2013'te, size bir kısayol için bu işlemi.
    - Visual Studio 2010 ve 2012: [PTV 2.1.1 for Visual studio 2010 ve 2012](https://github.com/Microsoft/PTVS/releases/v2.1.1)

1. [Tercih ettiğiniz bir Python yorumlayıcısını yükleyerek](installing-python-interpreters.md). Bir yorumlayıcı yüklü ve Visual Studio zaten yüklüyse olmayan otomatik olarak algıla bkz [el ile bir ortamı tanımlamanız](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="install-locations"></a>Yükleme konumları

Varsayılan olarak, Python desteği, bir bilgisayardaki tüm kullanıcılar için yüklenir.

Visual Studio 2019 ve Visual Studio 2017 ' de, Python iş yükü *% ProgramFiles (x86)% \ Microsoft Visual Studio\\< VS_version >\\< VS_edition* 2017 2019 > &lt;ve VS_version&gt; &lt;Community, Professional veya Enterprise olur.

Ve önceki sürümleri, Visual Studio 2015 için yükleme yolu aşağıdaki gibidir:

- 32 bit:
  - Yol: *% Program dosyaları (x86) %\Microsoft Visual Studio \<VS_ver > Visual Studio için \Common7\IDE\Extensions\Microsoft\Python Araçları\\< PTVS_ver >*
  - Kayıt defteri konumu yolu: **HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\\< VS_ver > \InstallDir**
- 64 bit:
  - Yol: *% Program Files%\Microsoft Visual Studio \<VS_ver > Visual Studio için \Common7\IDE\Extensions\Microsoft\Python Araçları\\< PTVS_ver >*
  - Kayıt defteri konumu yolu: **HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\\< VS_ver > \InstallDir**

burada:

- &lt;VS_ver&gt; olan:
  - Visual Studio 2015 için 14.0
  - Visual Studio 2013 için 12.0
  - Visual Studio 2012 için 11.0
  - Visual Studio 2010 için 10.0
- &lt;PTVS_ver&gt;, 2.2.2, 2.1.1, 2,0, 1,5, 1,1 veya 1,0 gibi bir sürüm numarasıdır.

### <a name="user-specific-installations-15-and-earlier"></a>Kullanıcıya özgü yüklemeleri (1.5 ve öncesi)

İzin yükleme yalnızca geçerli kullanıcı için Python araçları Visual Studio 1.5 ve önceki sürümler, bu durumda yükleme yolu *%LocalAppData%\Microsoft\VisualStudio\\< VS_ver > \Extensions\Microsoft\Python araçları Visual Studio için\\< PTVS_ver >* burada &lt;VS_ver&gt; ve &lt;PTVS_ver&gt; yukarıda açıklanan adıyla aynıdır.
