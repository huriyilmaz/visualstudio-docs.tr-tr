---
title: Veri Bilimi ve Analitik Uygulamalar iş yükü
description: Bu Visual Studio iş yükü Python, F#, ve Anaconda dahil olmak üzere kendi çalışma zamanı dağıtımları bir araya getiriyor. (R ayrıca visual studio 2017'ye dahildir.)
ms.date: 02/28/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 44906d70be05891fe52096adec2f61f2261b5db5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "70154887"
---
# <a name="install-data-science-support-in-visual-studio"></a>Visual Studio'da veri bilimi desteği yükleyin

Visual Studio yükleyicisi aracılığıyla seçtiğiniz ve yüklediğiniz Veri Bilimi ve Analitik Uygulamalar iş yükü, çeşitli dilleri ve bunların çalışma zamanı dağıtımlarını bir araya getirir:

::: moniker range="vs-2017"
- [Python ve Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [.NET çerçevesi ile F#](/dotnet/fsharp/)
- [R ve Microsoft R İstemci](../rtvs/index.md)
::: moniker-end

::: moniker range="vs-2019"
- [Python](../python/overview-of-python-tools-for-visual-studio.md)
- [.NET çerçevesi ile F#](/dotnet/fsharp/)
::: moniker-end

![Visual Studio yükleyicisinde Veri Bilimi ve Analitik Uygulamaları iş yükü](media/workload/data-science-workload.png)

::: moniker range="vs-2017"
Python ve R, veri bilimi için kullanılan birincil komut dosyası dillerinden ikisidir. Her iki dilde de öğrenmesi kolaydır ve zengin bir paket ekosistemi tarafından desteklenir. Bu paketler veri toplama, temizleme, model eğitimi, dağıtım ve çizim gibi çok çeşitli senaryoları ele alır. F# aynı zamanda çok çeşitli veri işleme görevleri için uygun olan güçlü bir işlevsel ilk .NET dilidir.
::: moniker-end

::: moniker range="vs-2019"
Python, veri bilimi için kullanılan birincil bir komut dosyası dilidir. Python öğrenmesi kolaydır ve zengin bir paket ekosistemi tarafından desteklenir. Bu paketler veri toplama, temizleme, model eğitimi, dağıtım ve çizim gibi çok çeşitli senaryoları ele alır. F# aynı zamanda çok çeşitli veri işleme görevleri için uygun olan güçlü bir işlevsel ilk .NET dilidir. (R dili için [Azure Dizüstü Bilgisayarları](https://notebooks.azure.com)öneririz.)
::: moniker-end

<!--Note link on the image because this one is large -->
[![R, Python ve F ile Visual Studio ekran görüntüleri #](media/workload/data-science-workload-screens.png)](media/workload/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>İş yükü seçenekleri

Varsayılan olarak, iş yükü, Visual Studio yük leyicisindeki iş yükü için özet bölümünde değiştirebileceğiniz aşağıdaki seçenekleri yükler:

::: moniker range="vs-2019"
- F# masaüstü dil desteği
- Python:
  - Python dil desteği
  - Python web desteği
::: moniker-end

::: moniker range="vs-2017"
- F# dil desteği
- Python:
  - Python dil desteği
  - [Anaconda3 64-bit](https://www.continuum.io), kapsamlı veri bilimi kitaplıkları ve python yorumlayıcısı içeren bir Python dağıtım.
  - Python web desteği
  - Cookiecutter şablon desteği
- R:
  - R dil desteği
  - R geliştirme araçları için çalışma zamanı desteği
  - [Microsoft R İstemci](/machine-learning-server/r-client/what-is-microsoft-r-client) (Microsoft'un, tek düğümveya kümelerde daha hızlı hesaplama için ScaleR kitaplıklarına sahip tam uyumlu, topluluk destekli R yorumlayıcısı. Ayrıca [CRAN](https://cran.r-project.org/)herhangi bir R kullanabilirsiniz .)
::: moniker-end

## <a name="sql-server-integration"></a>SQL Server tümleştirmesi

::: moniker range="vs-2017"
SQL Server, doğrudan SQL Server içinde gelişmiş analizler yapmak için hem Python hem de R'yi kullanmayı destekler. R desteği SQL Server 2016 ve sonrası ile birlikte verilir; Python desteği SQL Server 2017 CTP 2.0 ve sonraki yıllarda kullanılabilir.
::: moniker-end

::: moniker range=">=vs-2019"
SQL Server, Python'u kullanarak doğrudan SQL Server içinde gelişmiş analizler yapmayı destekler. Python desteği SQL Server 2017 CTP 2.0 ve sonraki yıllarda kullanılabilir.
::: moniker-end

Verilerinizin zaten bulunduğu yerde kodunuzu çalıştırarak aşağıdaki avantajlardan yararlanırsınız:

- **Veri hareketinin ortadan kaldırılması**: Verileri veritabanından uygulamanıza veya modelinize taşımak yerine, veritabanında uygulamalar oluşturabilirsiniz. Bu özellik, güvenlik, uyumluluk, yönetişim, bütünlük ve büyük miktarda verinin taşınmasıyla ilgili benzer konuların önündeki engelleri ortadan kaldırır. İstemci makinesinin belleğine sığamayan veri kümelerini de tüketebilirsiniz.

- **Kolay dağıtım**: Bir modeli hazır hale aldıktan sonra, onu üretime dağıtmak basit bir t-SQL komut dosyasına yerleştirmektir. Herhangi bir dilde yazılmış herhangi bir SQL istemci uygulaması daha sonra saklanan yordam çağrısı ile modelleri ve istihbarat yararlanabilir. Belirli bir dil tümleştirmesi gerekli değildir.

- **Kurumsal düzeyde performans ve ölçek**: SQL Server'ın bellek içi tablo ve sütun deposu dizinleri gibi gelişmiş özelliklerini RevoScale paketlerindeki yüksek performanslı ölçeklenebilir API'lerle kullanabilirsiniz. Veri hareketinin ortadan kaldırılması, verileriniz büyüdükçe veya uygulamanın performansını artırmak istediğinizde istemci bellek kısıtlamalarından kaçınmanız anlamına da gelir.

- **Zengin genişletilebilirlik**: SQL Server'da büyük miktarda veri üzerinde derin öğrenme ve AI uygulamaları oluşturmak için EN son açık kaynak paketlerinden herhangi birini yükleyebilir ve çalıştırabilirsiniz. SQL Server'a paket yüklemek, yerel makinenize paket yüklemek kadar kolaydır.

- **Ek ücret ödemeden geniş kullanılabilirlik**: Language entegrasyonları, Express sürümü de dahil olmak üzere SQL Server 2017 ve sonraki tüm sürümlerinde kullanılabilir.

SQL Server tümleştirmesi'nden tam olarak yararlanmak için Visual Studio yükleyicisini kullanarak Sql **Server Veri Araçları** seçeneğiyle Veri depolama ve iş yükünü **yükleyin.** İkinci seçenek SQL IntelliSense, sözdizimi vurgulama ve dağıtım sağlar.

![Veri depolama ve işleme iş yükü](media/workload/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Veri depolama ve işleme iş yükü seçenekleri](media/workload/data-storage-workload-options.png)

Daha fazla bilgi için:

::: moniker range="vs-2017"
- [SQL Server ve R ile çalışma](../rtvs/integrating-sql-server-with-r.md)
- [SQL Server 2016'da R ile Veritabanı İçi Gelişmiş Analitik (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
::: moniker-end
- [Python IN SQL Server 2017: gelişmiş veritabanı içi makine öğrenimi (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Ek hizmetler ve SDK'lar

Veri Bilimi ve Analitik Uygulamaları'ndaki iş yükünün yanı sıra, Azure Notebook hizmeti ve Python için Azure SDK de veri bilimi için yararlıdır.

Python için Azure SDK, Windows, Mac ve Linux'ta çalışan uygulamalardan Microsoft Azure hizmetlerini tüketmeyi ve yönetmeyi kolaylaştırır. Daha fazla bilgi için [Python için Azure SDK'ya](/azure/python/)bakın.

Azure Dizüstü Bilgisayarlar (şu anda önizlemede) Microsoft Azure'da bulutta çalışan Jupyter dizüstü bilgisayarlara ücretsiz çevrimiçi erişim sağlar. Hizmet, başlamak için Python, R ve F# örnek not defterlerini içerir. [notebooks.azure.com'ı ziyaret edin.](https://notebooks.azure.com/)

<!--Note link on the image because this one is large -->
[![R örneğine Giriş ile Azure Dizüstü Bilgisayarekranlarının ekran görüntüleri](media/workload/data-science-workload-notebooks.png)](media/workload/data-science-workload-notebooks.png#lightbox)
