---
title: Python ile çalışmaya başlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 21e724e585f2a5bf0e1fe2a6b70f89c1bd5f5eec
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298191"
---
# <a name="getting-started-with-python"></a>Python’ı Kullanmaya Başlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio için Python Araçları (PTV), güçlü bir Python geliştirme deneyimi sunan, Visual Studio için ücretsiz, [Açık kaynaklı](https://github.com/Microsoft/ptvs) bir eklentisidir.  
  
## <a name="python-the-language"></a>Dili Python
  
Python pek çok üniversitenin, bilimcilerin, uygulama betiklerine, rastgele geliştiricilere ve profesyonel geliştiricilerle, uygulamalar, Web siteleri ve bulut hizmetlerinde çalışan popüler bir programlama dilidir.

Programlama dili olarak Python:
  
- Güvenilir.
- Hızlı programlar, uygulama betiği, masaüstü uygulamaları, Web sunucuları, Web Hizmetleri ve bilimsel bilgi işlem için genellikle yararlı olur.
- Kolayca öğrenilmesi ve iyi kodlamayı teşvik etmek için iyi bir tasarıma sahiptir (birçok üniversiteler bunu Tanıtım programlama kursları için kullanır).
- Esnek, işlevsel ve nesne odaklı programlama stillerinin desteklenmesi.
- Ücretsiz ve açık kaynak.
- Tüm önemli işletim sistemlerinde iyi çalışır.  
- Birçok ücretsiz, yararlı ve iyi tasarlanmış kitaplık tarafından desteklenir.  
- Birçok belge, örnek ve güçlü bir geliştirici topluluğu tarafından desteklenir.  

Dil hakkında daha fazla bilgi edinmek için python.org adresindeki [Yeni başlayanlar Için Python](https://www.python.org/about/gettingstarted/) ile başlayın.

Python 'u yüklemek için [https://www.python.org/download/](https://www.python.org/download/)ziyaret edin.

## <a name="python-tools-for-visual-studio"></a>Visual Studio için Python Araçları
  
[VisualStudio.com](https://www.visualstudio.com/explore/python-vs)adresinden yükleyebileceğiniz Visual Studio için Python araçları, aşağıdaki özellikleri sağlar:  
  
- Birden çok yorumlayıcılar için destek: çeşitli CPython, IronPython ve IPython sürümleri  
- Python kodunun bir klasör yapısını örtük olarak alan ve ayrıca uygulama kodu, test kodu, Web sayfaları, JavaScript, derleme betikleri ve benzerlerini belirleyebilmeniz için açık denetime izin veren bir proje sistemi.  
- Konsol, Web, Azure, veri bilimi ve diğer proje türleri için proje şablonları.    
- Python için Azure SDK (aşağıya bakın)    
- Sözdizimi renklendirme, tüm kod ve kitaplıklarınızda otomatik olarak tamamlanma, imza yardımı, sınıf görünümü, tanıma git, tüm başvuruları bul, yeniden düzenleme ve daha fazlasını içeren zengin düzenleme ve kod kavrama özellikleri.    
- Etkileşimli (REPL) bir pencere
- Veri görselleştirmeleri ile IPython.
- IronPython ve .NET/WPF desteği.    
- Visual Studio projesi olmadan zengin hata ayıklama, var olan bir yürütülebilir dosya, karışık modda hata ayıklama, Windows/Linux/Mac 'e uzaktan hata ayıklama ve etkileşimli pencere içinde hata ayıklama özelliği.   
- Profil oluşturma araçları.  
- Test araçları.  
  
Aşağıdaki kaynaklar başlamanıza yardımcı olur:

- [Yükleme kılavuzu](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [Başlarken ve derin videoları öğrenin](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
- Yükleme ve Özellikler tanıtımı (27 dk)] (https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Belgeler](https://github.com/Microsoft/PTVS/wiki)  

Visual Studio 'Nun mevcut olmadığı, Python kullanarak tek başına yürütülebilir bir dosya oluşturma, aslında katıştırılmış Python yorumlayıcı içeren bir program anlamına gelir. Ancak, [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency)' de açıklandığı gibi, Python topluluğu 'nda bunu yapmak için çeşitli araçlar vardır. Cpyıthon Ayrıca, [cpıthon 'un eklenebilir ZIP dosyası kullanılarak](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/)blog gönderisine göre yerel bir uygulama içine katıştırılmakta da desteklenir.
  
## <a name="building-ui-with-python"></a>Python ile Kullanıcı arabirimi oluşturma  

Python ile bir kullanıcı arabirimi oluşturmaya yönelik ana teklif, bir Python [projesi](https://www.qt.io/qt-for-application-development/)olan ( [resmi bağlama)](https://wiki.qt.io/PySide) (Ayrıca bkz. [Pysıde İndirmeleri](https://download.qt.io/official_releases/pyside/.)) ve [PyQt](https://wiki.python.org/moin/PyQt). Şu anda, herhangi belirli kullanıcı Arabirimi geliştirme araçları Visual Studio'da Python desteği içermez.

## <a name="azure-sdk-for-python"></a>Python için Azure SDK
  
Windows, Mac ve Linux destekleyen Python için Azure SDK, Microsoft Azure hizmetlerini kolayca kullanmanıza ve yönetmenize olanak sağlar. Ayrıntılar için aşağıdaki kaynaklara bakın: 

- SDK 'yı yüklemek için [Python paket dizinini](https://pypi.python.org/pypi/azure) kullanın veya Azure belgelerine [Python ve SDK 'yı yüklemeyi](https://docs.microsoft.com/azure/python/python-sdk-azure-install) izleyin. 
- [Python Için Azure SDK Geliştirici Merkezi](https://azure.microsoft.com/develop/python/) , eğitimlerle belgelere yüklemeden çok fazla yardım içerir.  Bazı önemli noktalar şunlardır:  
- Nasıl Yapılır Kılavuzları:
  - [Depolama Blobu](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [Depolama kuyruğu](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Depolama tablosu](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Service Bus kuyrukları](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Service Bus konuları/abonelikleri](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Hizmet yönetimi](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>Bilimsel bilgi Işlem

Visual Studio için Python Araçları, tüm Python veri bilimcst kitaplıklarına ek olarak, Azure 'da barındırılabilecek IPython ve IPython not defterlerini da destekler.

[University of California, Irvine](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack)'Dan IPython ve bilimsel bilgi işlem kitaplıklarını (Matplotlib, SciPy, sayısal tuş takımı, vb.) edinmeyi öneririz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  

[PTV 'leri kullanmaya başlama: Visual Studio 'Yu ayarlama](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[PTV](../python/getting-started-with-ptvs-start-coding-projects.md) 'leri kullanmaya başlama: ptv 'leri kullanmaya başlama
[: kodu Düzenle](../python/getting-started-with-ptvs-editing-code.md)
PTV 'leri kullanmaya başlama: [hata ayıklama](../python/getting-started-with-ptvs-debugging.md)
PTV 'Leri kullanmaya başlama: [etkileşimli
Python](../python/getting-started-with-ptvs-interactive-python.md) : [Azure 'da Web sitesi oluşturma](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
