---
title: Veri Bilimi ve Analitik Uygulamalar iş yükü
description: Bu Visual Studio iş yükü Python, F# ve Anaconda dahil olmak üzere ilgili çalışma zamanı dağıtımlarını bir araya getirir. (R, yalnızca 2017 Visual Studio dahil edilir.)
ms.date: 07/28/2021
ms.topic: overview
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 10e557b940b40ebe2a32a4a75663a0af8ea4fd99
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970457"
---
# <a name="install-data-science-support-in-visual-studio"></a>Veri bilimi desteğini Visual Studio

Visual Studio yükleyicisi aracılığıyla seçerek yük devrederek veri bilimi ve analitik uygulamalar iş yükü, çeşitli dilleri ve bunların ilgili çalışma zamanı dağıtımlarını bir araya getirir:

::: moniker range="vs-2017"
- [Python ve Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [.NET framework ile F#](/dotnet/fsharp/)
- [R ve Microsoft R Client](../rtvs/index.md)
::: moniker-end

::: moniker range="vs-2019"
- [Python](../python/overview-of-python-tools-for-visual-studio.md)
- [.NET framework ile F#](/dotnet/fsharp/)
::: moniker-end

![Veri Bilimi ve Analiz Uygulamaları iş yükü Visual Studio yükleme](media/workload/data-science-workload.png)

::: moniker range="vs-2017"
Python ve R, veri bilimi için kullanılan birincil betik dillerinin ikisidir. Her iki dili de öğrenmek kolaydır ve zengin bir paket ekosistemi tarafından de destekler. Bu paketler veri alımı, temizleme, model eğitimi, dağıtım ve çizim gibi çok çeşitli senaryolara hitap ediyor. F# ayrıca çok çeşitli veri işleme görevleri için uygun olan, işlevsel ve ilk .NET dilidir.
::: moniker-end

::: moniker range=">=vs-2019"
Python, veri bilimi için kullanılan birincil betik dilidir. Python öğrenmesi kolaydır ve zengin bir paket ekosistemi tarafından de destekler. Bu paketler veri alımı, temizleme, model eğitimi, dağıtım ve çizim gibi çok çeşitli senaryolara hitap ediyor. F# ayrıca çok çeşitli veri işleme görevleri için uygun, işlevsel ve ilk .NET dilidir.)
::: moniker-end

<!--Note link on the image because this one is large -->
[![R, Python ve F Visual Studio ekran görüntüleri #](media/workload/data-science-workload-screens.png)](media/workload/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>İş yükü seçenekleri

Varsayılan olarak, iş yükü yükleyicisinde iş yükünün özet bölümünde değiştirebilirsiniz aşağıdaki Visual Studio yüklenir:

::: moniker range=">=vs-2019"
- F# masaüstü dili desteği
- Python:
  - Python dil desteği
  - Python web desteği
::: moniker-end

::: moniker range="vs-2017"
- F# dil desteği
- Python:
  - Python dil desteği
  - [Anaconda3 64 bit](https://anaconda.com), kapsamlı veri bilimi kitaplıkları ve Python yorumlayıcı içeren bir Python distro's.
  - Python web desteği
  - Cookiecutter şablon desteği
- R:
  - R dili desteği
  - R geliştirme araçları için çalışma zamanı desteği
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) düğümlerde veya kümelerde daha hızlı hesaplama için Microsoft'un scaleR kitaplıkları ile tam olarak uyumlu, topluluk tarafından desteklenen R yorumlayıcı. AYRıCA CRAN'den herhangi bir [R'yi de kullanabilirsiniz.)](https://cran.r-project.org/)
::: moniker-end

## <a name="sql-server-integration"></a>SQL Server tümleştirmesi

::: moniker range="vs-2017"
SQL Server, hem Python hem de R kullanarak doğrudan uygulamanın içinde gelişmiş analiz SQL Server. R desteği, SQL Server 2016 ve sonraki bir 2016'ya dahildir; Python desteği 2017 CTP 2.0 ve sonraki SQL Server kullanılabilir.
::: moniker-end

::: moniker range=">=vs-2019"
SQL Server, python kullanarak doğrudan uygulamanın içinde gelişmiş analiz SQL Server. Python desteği 2017 CTP 2.0 ve sonraki SQL Server kullanılabilir.
::: moniker-end

Kodunuzu verilerinizin zaten bulunduğu yerde çalıştırarak aşağıdaki avantajlardan keyif alasiniz:

- **Veri taşımanın ortadan** kaldırılması: Veritabanındaki verileri uygulamanıza veya modelinize taşıma yerine veritabanında uygulamalar derlemeniz gerekir. Bu özellik, muazzam miktarlardaki verileri taşımayla ilgili güvenlik, uyumluluk, idare, bütünlük ve benzer sorunların bir çok engelini ortadan kaldırıyor. Ayrıca, istemci makinenin belleğine sığmayan veri kümelerini de tüketebilirsiniz.

- **Kolay dağıtım:** Hazır bir modele sahip olduktan sonra modeli üretime dağıtmak, modeli T-SQL betiğine eklemektir. Herhangi SQL yazılmış herhangi bir istemci uygulaması, saklı yordam çağrısı aracılığıyla modellerden ve zekadan faydalanabilir. Belirli bir dil tümleştirmesi gerekli değildir.

- **Enterprise düzeyde** performans ve ölçek: SQL Server'nin bellek içinde tablo ve sütun deposu dizinleri gibi gelişmiş özelliklerini RevoScale paketlerinde yüksek performanslı ölçeklenebilir API'lerle kullanabilirsiniz. Veri taşımanın ortadan kaldırılması, verileriniz büyüdükçe veya uygulamanın performansını artırmak istediğiniz için istemci belleği kısıtlamalarından kaçınmanız anlamına da gelir.

- **Zengin genişletilebilirlik:** SQL Server'da çok büyük miktarlarda veri üzerinde derin öğrenme ve AI uygulamaları oluşturmak için SQL Server. Bir paketi SQL Server yerel makinenize yüklemek kadar kolaydır.

- **Ek ücret ödemeden geniş kullanılabilirlik:** Express sürümü dahil olmak üzere SQL Server 2017 ve sonraki sürümleriyle dil tümleştirmeleri kullanılabilir.

Bu tümleştirmeden tam SQL Server yararlanmak için Visual Studio yükleyicisini kullanarak  veri depolama ve işleme iş yükünü SQL Server Veri Araçları **yükleyin.** İkinci seçenek IntelliSense SQL, söz dizimi vurgulama ve dağıtım için kullanılabilirlik sağlar.

![Veri depolama ve işleme iş yükü](media/workload/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Veri depolama ve işleme iş yükü seçenekleri](media/workload/data-storage-workload-options.png)

Daha fazla bilgi için:

::: moniker range="vs-2017"
- [SQL Server ve R ile çalışma](../rtvs/integrating-sql-server-with-r.md)
- [SQL Server 2016'da R ile veritabanı içinde Gelişmiş Analiz (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
::: moniker-end
- [SQL Server 2017'de Python: gelişmiş veritabanı içinde makine öğrenmesi (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Ek hizmetler ve SDK'lar

Veri Bilimi ve Analiz Uygulamaları iş yükünde doğrudan nelerin yer alanlarına ek olarak, Azure Notebooks hizmeti ve Python için Azure SDK da veri bilimi için yararlıdır.

Python için Azure SDK, Microsoft Azure, Mac ve Linux üzerinde çalışan uygulamalardan Windows ve yönetmeyi kolaylaştırır. Daha fazla bilgi için bkz. [Python için Azure SDK.](/azure/python/)

Azure Notebooks (şu anda önizlemede) bulutta çalışan Jupyter not defterlerine ücretsiz çevrimiçi erişim Microsoft Azure. Hizmeti, başlamaya başlamaya için Python, R ve F# dilinde örnek not defterleri içerir. web [sitesini notebooks.azure.com.](https://notebooks.azure.com/)

<!--Note link on the image because this one is large -->
[![R örneğine Azure Notebooks ekran görüntüleri](media/workload/data-science-workload-notebooks.png)](media/workload/data-science-workload-notebooks.png#lightbox)
