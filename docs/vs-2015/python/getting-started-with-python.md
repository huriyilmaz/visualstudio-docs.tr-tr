---
title: Python ile Başlarken | Microsoft Dokümanlar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 97d60fe31f838c4cc497701f4560dc426ebc1cc9
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543970"
---
# <a name="getting-started-with-python"></a>Python’ı Kullanmaya Başlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Python Tools for Visual Studio (PTVS), Visual Studio için güçlü bir Python geliştirme deneyimi olan ücretsiz, [açık kaynak](https://github.com/Microsoft/ptvs) eklentisidir.  
  
## <a name="python-the-language"></a>Python Dil
  
Python, uygulamalar, web siteleri ve bulut hizmetleri üzerinde çalışan birçok üniversite, bilim adamı, uygulama komut dosyası, gündelik geliştiriciler ve profesyonel geliştiriciler tarafından kullanılan popüler bir programlama dilidir.

Bir programlama dili olarak Python:
  
- Güvenilir.
- Genellikle hızlı programlar, uygulama komut dosyası oluşturma, masaüstü uygulamaları, web sunucuları, web hizmetleri ve bilimsel bilgi işlem için yararlıdır.
- Öğrenmesi kolay ve iyi kodlamayı teşvik etmek için iyi bir tasarıma sahiptir (birçok üniversite bunu giriş programlama kursları için kullanır).
- Esnek, destekleyici zorunlu, işlevsel ve nesne yönelimli programlama stilleri.
- Özgür ve açık kaynak.
- Tüm büyük işletim sistemlerinde iyi çalışır.  
- Birçok ücretsiz, kullanışlı ve iyi tasarlanmış kütüphaneler tarafından desteklenir.  
- Birçok belge, örnek ve güçlü bir geliştirici topluluğu tarafından desteklenir.  

Dil hakkında daha fazla bilgi edinmek için, python.org'da [Yeni Başlayanlar için Python](https://www.python.org/about/gettingstarted/) ile başlayın.

Python'u yüklemek [https://www.python.org/download/](https://www.python.org/download/)için .

## <a name="python-tools-for-visual-studio"></a>Visual Studio için Python Araçları
  
[visualstudio.com](https://www.visualstudio.com/explore/python-vs)yükleyebileceğiniz Visual Studio için Python Araçları aşağıdaki özellikleri sağlar:  
  
- Birden fazla yorumlayıcı için destek: CPython, IronPython ve IPython'un çeşitli sürümleri  
- Python kodunun bir klasör yapısını zımni olarak alan ve uygulama kodunu, test kodunu, web sayfalarını, JavaScript'i, yapı komut dosyalarını ve benzerlerini tanımlayabilmeniz için açık denetime olanak tanıyan bir proje sistemi.  
- Konsol, web, Azure, veri bilimi ve diğer proje türleri için proje şablonları.    
- Python için Azure SDK (aşağıya bakın)    
- Sözdizimi boyama, tüm kod ve kitaplıklar arasında otomatik olarak tam olarak tamamlanması, imza yardımı, sınıf görünümü, Tanıma Git, Tüm Başvuruları Bul, yeniden düzenleme ve daha fazlasını içeren zengin düzenleme ve kod anlama özellikleri.    
- Etkileşimli (REPL) Penceresi
- Veri görselleştirmeleri ile IPython.
- IronPython ve .NET/WPF desteği.    
- Visual Studio projesi olmadan zengin hata ayıklama, mevcut bir çalıştırılabilir, karma mod hata ayıklama, Windows/Linux/Mac'e uzaktan hata ayıklama ve Etkileşimli Pencere içinde hata ayıklama yeteneği.   
- Profil oluşturma araçları.  
- Test araçları.  
  
Aşağıdaki kaynaklar başlamanıza yardımcı olur:

- [Yükleme kılavuzu](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [Başlarken ve derin dalış kısa videolar](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
- Kurulum ve özellikleri demo (27 dk)](https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Belgeler](https://github.com/Microsoft/PTVS/wiki)  

Visual Studio'nun şu anda Python kullanarak tek başına yürütülebilir bir uygulama oluşturma nın mümkün olmadığını unutmayın, bu da aslında gömülü Python yorumlayıcısı olan bir program anlamına gelir. Ancak, [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency)açıklandığı gibi bunu yapmak için Python topluluk içinde çeşitli araçlar vardır. CPython da yerel bir uygulama içinde gömülü olmayı destekler, blog yazısı açıklandığı gibi, [CPython's Embeddable Zip Dosyasını kullanarak](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/).
  
## <a name="building-ui-with-python"></a>Python ile UI Oluşturma  

Python ile bir UI oluşturmak için ana teklif [Qt Projesi](https://www.qt.io/qt-for-application-development/), [Python pyside (resmi bağlama)](https://wiki.qt.io/PySide) olarak bilinen ciltler (ayrıca [PySide indirme](https://download.qt.io/official_releases/pyside/.)bakınız ) ve [PyQt](https://wiki.python.org/moin/PyQt). Şu anda Visual Studio'daki Python desteği, UI geliştirme için belirli araçlar içermez.

## <a name="azure-sdk-for-python"></a>Python için Azure SDK
  
Windows, Mac ve Linux'u destekleyen Python için Azure SDK, Microsoft Azure Hizmetlerini tüketmeyi ve yönetmeyi kolaylaştırır. Ayrıntılar için aşağıdaki kaynaklara bakın: 

- SDK'yı yüklemek için [Python Paket Dizini'ni](https://pypi.python.org/pypi/azure) kullanın veya Azure belgelerinde [Python ve SDK'yı yükleyin'i](/azure/developer/python/azure-sdk-install) izleyin. 
- [Python Geliştirici Merkezi için Azure SDK,](https://azure.microsoft.com/develop/python/) yüklemeden belgelere kadar öğreticilerle çok sayıda yardıma sahiptir.  Bazı önemli noktalar şunlardır:  
- Nasıl Yapılır Kılavuzları:
  - [Depolama Blobu](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [Depolama Kuyruğu](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Depolama Tablosu](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Servis Veri Otobüsü Kuyrukları](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Servis Otobüsü Konuları/Abonelikleri](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Hizmet Yönetimi](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>Bilimsel Bilgi İşlem

Tüm Python veri bilimci kitaplıklarına ek olarak, Visual Studio için Python Araçları, Azure'da barındırılabilen IPython ve IPython Not Defterlerini destekler.

Biz IPython ve bilimsel bilgisayar kütüphaneleri (matplotlib, scipy, numpy, vb) [University of California, Irvine](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack)edinmenizi öneririz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  

[PTVS ile Başlarken: PTVS](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
ile Visual Studio Başlarken Başlarken Görsel Studio Kurma:[PTVS ile Başlarken](../python/getting-started-with-ptvs-editing-code.md)
[Kodlama (Projeler)](../python/getting-started-with-ptvs-start-coding-projects.md)
Başlarken: Düzenleme Kodu[PTVS ile Başlarken:](../python/getting-started-with-ptvs-debugging.md)
Hata Ayıklama[PTVS ile Başlarken: İnteraktif Python](../python/getting-started-with-ptvs-interactive-python.md)
[PTVS ile Başlarken: Azure'da Bir Web Sitesi Oluşturma](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
