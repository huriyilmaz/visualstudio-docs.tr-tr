---
title: Veri bilimi ve analitik uygulamalar iş yükü
description: "bu Visual Studio iş yükü, anaconda dahil olmak üzere Python, F # ve ilgili çalışma zamanı dağıtımlarını birlikte getirir. (R yalnızca Visual Studio 2017 ' ye de dahildir.)"
ms.date: 07/28/2021
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: d33a33cacd1c5fb6c2d7cd4c45a14fa32d2cc1bc
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636998"
---
# <a name="install-data-science-support-in-visual-studio"></a>Visual Studio veri bilimi desteğini yükler

Visual Studio yükleyicisi aracılığıyla seçtiğiniz ve yüklediğiniz veri bilimi ve analitik uygulamalar iş yükü, birkaç dili ve ilgili çalışma zamanı dağıtımlarını birlikte getirir:

::: moniker range="vs-2017"
- [Python ve Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [.NET Framework ile F #](/dotnet/fsharp/)
- [R ve Microsoft R Client](../rtvs/index.md)
::: moniker-end

::: moniker range="vs-2019"
- [Python](../python/overview-of-python-tools-for-visual-studio.md)
- [.NET Framework ile F #](/dotnet/fsharp/)
::: moniker-end

![Visual Studio yükleyicisinde veri bilimi ve analitik uygulamalar iş yükü](media/workload/data-science-workload.png)

::: moniker range="vs-2017"
Python ve R, veri bilimi için kullanılan birincil komut dosyası dillerinin ikikleridir. Her iki dilin de öğrenilmesi kolaydır ve bu paketlerin zengin ekosistemi tarafından desteklenir. Bu paketler, veri alma, Temizleme, model eğitimi, dağıtım ve çizim gibi çok çeşitli senaryolar ele alıalardır. F #, çok çeşitli veri işleme görevlerine uygun olan güçlü bir işlevsel ilk .NET dilidir.
::: moniker-end

::: moniker range=">=vs-2019"
Python, veri bilimi için kullanılan birincil bir komut dosyası dilidir. Python kolayca öğrenilmesi ve paketlerin zengin ekosistemi tarafından desteklenilmesi kolaydır. Bu paketler, veri alma, Temizleme, model eğitimi, dağıtım ve çizim gibi çok çeşitli senaryolar ele alıalardır. F #, çok çeşitli veri işleme görevlerine uygun olan güçlü bir işlevsel ilk .NET dilidir.)
::: moniker-end

<!--Note link on the image because this one is large -->
[![R, Python ve F ile Visual Studio ekran görüntüleri #](media/workload/data-science-workload-screens.png)](media/workload/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>İş yükü seçenekleri

varsayılan olarak, iş yükü Visual Studio yükleyicisindeki iş yükünün özet bölümünde değiştirebileceğiniz aşağıdaki seçenekleri yüklenir:

::: moniker range=">=vs-2019"
- F # masaüstü dil desteği
- Python:
  - Python dil desteği
  - Python web desteği
::: moniker-end

::: moniker range="vs-2017"
- F # dil desteği
- Python:
  - Python dil desteği
  - [Anaconda3 64-bit](https://anaconda.com), kapsamlı veri bilimi kitaplıkları ve bir Python yorumlayıcı Içeren bir Python.
  - Python web desteği
  - Cookiecutter şablonu desteği
- Sağ
  - R dil desteği
  - R geliştirme araçları için çalışma zamanı desteği
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (Microsoft 'un, tek düğümlerde veya kümelerde daha hızlı hesaplama için scaler kitaplıklarıyla tamamen uyumlu, topluluk tarafından desteklenen R yorumlayıcısı. [Cran](https://cran.r-project.org/)'ın herhangi bir R 'yi de kullanabilirsiniz.)
::: moniker-end

## <a name="sql-server-integration"></a>SQL Server tümleştirmesi

::: moniker range="vs-2017"
SQL Server, doğrudan SQL Server içinde gelişmiş analizler yapmak için Python ve R kullanımını destekler. R desteği SQL Server 2016 ve üzeri sürümlerde bulunur; Python desteği SQL Server 2017 CTP 2,0 ve üzeri sürümlerde kullanılabilir.
::: moniker-end

::: moniker range=">=vs-2019"
SQL Server, doğrudan SQL Server içinde gelişmiş analizler yapmak için Python kullanmayı destekler. Python desteği SQL Server 2017 CTP 2,0 ve üzeri sürümlerde kullanılabilir.
::: moniker-end

Verilerinizin zaten yaşadığı kodunuzu çalıştırarak aşağıdaki avantajlardan yararlanabilirsiniz:

- **Veri hareketini eleme**: veritabanından uygulamanıza veya modelinize veri taşımak yerine, veritabanında uygulamalar oluşturabilirsiniz. Bu özellik güvenlik, uyumluluk, idare, bütünlük ve çok miktarda veri taşıma ile ilgili benzer sorunların bir ana bilgisayarının sınırlamalarını ortadan kaldırır. Ayrıca, bir istemci makine belleğine sığmayan veri kümelerini de kullanabilirsiniz.

- **kolay dağıtım**: bir modeli hazırladıktan sonra, bunu üretime dağıtmak T SQL betiğine eklemek çok basit bir işlemdir. herhangi bir dilde yazılmış herhangi bir SQL istemci uygulaması, saklı yordam çağrısı aracılığıyla modellerden ve zekanın avantajlarından yararlanabilir. Belirli bir dil tümleştirmeleri gerekli değildir.

- **Enterprise sınıf performansı ve ölçeği**: SQL Server, bellek içi tablo ve sütun depolama dizinleri gibi gelişmiş özelliklerini, iptal edilmiş paketlerde yüksek performanslı ölçeklenebilir apı 'ler ile kullanabilirsiniz. Veri taşımayı eleme, verileriniz büyüdükçe istemci Bellek kısıtlamalarından kaçınmanıza ya da uygulamanın performansını artırmak istediğinizde anlamına gelir.

- **zengin genişletilebilirlik**: SQL Server çok büyük miktarlarda veri üzerinde derin öğrenme ve aı uygulamaları oluşturmak için SQL Server ' deki en son açık kaynak paketlerini yükleyebilir ve çalıştırabilirsiniz. SQL Server bir paketi yükleme, yerel makinenize bir paket yüklemek kadar basittir.

- **ek ücret ödemeden geniş kullanılabilirlik**: dil tümleştirmeleri, Express sürümü de dahil olmak üzere tüm SQL Server 2017 ve üzeri sürümlerde kullanılabilir.

SQL Server tümleştirmesinin tam avantajlarından yararlanabilmek için Visual Studio yükleyicisini kullanarak **veri depolama ve işleme** iş yükünü **SQL Server Veri Araçları** seçeneğiyle çalıştırın. ikinci seçenek SQL ıntellisense, sözdizimi vurgulama ve dağıtım seçeneklerini sunar.

![Veri depolama ve işleme iş yükü](media/workload/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Veri depolama ve işleme iş yükü seçenekleri](media/workload/data-storage-workload-options.png)

Daha fazla bilgi için:

::: moniker range="vs-2017"
- [SQL Server ve R ile çalışma](../rtvs/integrating-sql-server-with-r.md)
- [SQL Server 2016 ' de R ile veritabanı içi gelişmiş analiz (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
::: moniker-end
- [SQL Server 2017 ' de Python: gelişmiş veritabanı içi makine öğrenimi (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Ek hizmetler ve SDK 'lar

Veri bilimi ve analitik uygulamalar iş yükündeki yeniliklere ek olarak, Azure Notebooks hizmeti ve Python için Azure SDK, veri bilimi için de yardımcı olur.

Python için Azure SDK, Windows, Mac ve Linux üzerinde çalışan uygulamalardan Microsoft Azure hizmetlerini kolayca kullanmanıza ve yönetmenize olanak sağlar. Daha fazla bilgi için bkz. [Python Için Azure SDK](/azure/python/).

Azure Notebooks (Şu anda önizlemede), Microsoft Azure bulutta çalışan jupi not defterlerine ücretsiz çevrimiçi erişim sağlar. Hizmet, başlamanıza başlamak için Python, R ve F # ' daki örnek not defterlerini içerir. [Notebooks.Azure.com](https://notebooks.azure.com/)adresini ziyaret edin.

<!--Note link on the image because this one is large -->
[![R örneğine giriş ile Azure Notebooks ekran görüntüleri](media/workload/data-science-workload-notebooks.png)](media/workload/data-science-workload-notebooks.png#lightbox)
