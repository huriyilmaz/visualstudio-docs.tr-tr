---
title: Python projeleri için öğe şablonları
description: Visual Studio içinde > yeni öğe Ekle iletişim kutusu aracılığıyla kullanılabilen Python projesi için öğe şablonlarının başvuru listesi.
ms.date: 12/06/2018
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7effabe9323611685ef392820f4eb56f183a41d17245966b662ca7d1a2d3b63a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121367751"
---
# <a name="python-item-templates"></a>Python öğe şablonları

öğe şablonları, **Project**  >  **yeni öğe ekle** menü komutuyla veya   >  **Çözüm Gezgini** bağlam menüsünde **yeni öğe** ekle komutuyla kullanılabilir.

![Yeni öğe Ekle iletişim kutusu](media/project-item-templates.png)

Öğe için sağladığınız adı kullanarak, bir şablon genellikle projedeki Şu anda seçili olan klasörde bir veya daha fazla dosya ve klasör oluşturur (bağlam menüsünü açmak için bir klasörü sağ tıklatmak, klasörü otomatik olarak seçer). öğe eklendiğinde, Visual Studio projesine dahildir ve öğe **Çözüm Gezgini** görünür.

Aşağıdaki tablo, bir Python projesindeki her öğe şablonunun etkisini kısaca açıklar:

| Şablon | Şablon ne oluşturur |
| --- | --- |
| **Boş Python dosyası** | *. Köpek* uzantılı boş bir dosya. |
| **Python sınıfı** | Tek bir boş Python sınıfı tanımı içeren bir *. Kopyala* dosyası. |
| **Python paketi** | Bir *\_ \_ init \_ \_ . Kopyala* dosyası içeren bir klasör. |
| **Python birim testi** | Çerçeve tabanlı tek bir birim testine sahip bir *. Kopyala* dosyası `unittest` , `unittest.main()` dosyadaki testleri çalıştırmak için çağrısı ile birlikte. |
| **HTML sayfası** | Ve öğeden oluşan basit sayfa yapısına sahip bir *.html* dosyası `<head>` `<body>` . |
| **JavaScript** | Boş bir  *.js* dosyası. |
| **Stil sayfası** | İçin boş bir stil içeren bir *. css* dosyası `body` . |
| **Metin dosyası** | Boş bir *.txt* dosyası. |
| **Docgo 1,9 uygulaması**<br/>**Docgo 1,4 uygulaması** | bir docgo uygulamasının çekirdek dosyalarını içeren bir klasör, [Visual Studio docgo hakkında bilgi edinin,](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) docgo 1,9 için 2-2. adıma bakın. Docgo 1,4 için, *geçişler* klasörü, *admin.py* dosyası ve *Apps.py* dosyası dahil değildir. |
| **IronPython WPF penceresi** | İki yan yana dosyadan oluşan bir WPF penceresi: boş bir öğesi ile tanımlayan *. xaml* dosyası `<Window>` `<Grid>` ve kitaplığı kullanarak xaml dosyasını yükleyen ilişkili *. Kopyala* dosyası. `wpf` Genellikle IronPython proje şablonlarından biri kullanılarak oluşturulan bir proje içinde kullanılır. bkz. [Python projelerini yönetme-Project şablonları](managing-python-projects-in-visual-studio.md#project-templates). |
| **Web rolü destek dosyaları** | Proje kökündeki bir *bin* klasörü (projedeki seçili klasöre bakılmaksızın). Klasör, Azure Cloud Service Web rolleri için bir varsayılan dağıtım betiği ve bir *web.config* dosyası içerir. Şablon, ayrıntıları açıklayan bir *readme.html* dosyası da içerir. |
| **Çalışan rolü destek dosyaları** | Proje kökündeki bir *bin* klasörü (projedeki seçili klasöre bakılmaksızın). Klasör, Azure bulut hizmeti çalışan rolleri için bir *web.config* dosyası ile birlikte varsayılan dağıtım ve başlatma betiği içerir. Şablon, ayrıntıları açıklayan bir *readme.html* dosyası da içerir. |
| **Azure web.config (FastCGI)** | Gelen bağlantıları işlemek için bir [WSGI](https://wsgi.readthedocs.io/en/latest/) nesnesi kullanan uygulamalar için girişleri içeren bir *web.config* dosyası. Bu dosya genellikle IIS çalıştıran bir Web sunucusunun köküne dağıtılır. Daha fazla bilgi için bkz. [IIS için uygulama yapılandırma](configure-web-apps-for-iis-windows.md). |
| **Azure web.config (HttpPlatformHandler)** | Gelen bağlantılar için bir yuva üzerinde dinleme yapan uygulamalara ait girişleri içeren bir *web.config* dosyası. Bu dosya genellikle Azure App Service gibi IIS çalıştıran bir Web sunucusunun köküne dağıtılır. Daha fazla bilgi için bkz. [IIS için uygulama yapılandırma](configure-web-apps-for-iis-windows.md). |
| **Azure statik dosyaları web.config** | Bu klasör için Python işlemesini devre dışı bırakmak için genellikle *statik* bir klasöre (veya statik öğeler içeren başka bir klasöre) eklenen bir *web.config* dosyası. Bu yapılandırma dosyası yukarıdaki FastCGI veya HttpPlatformHandler yapılandırma dosyalarından biriyle birlikte çalışmaktadır. Daha fazla bilgi için bkz. [IIS için uygulama yapılandırma](configure-web-apps-for-iis-windows.md). |
| **Azure uzaktan hata ayıklama web.config** | kullanım dışı (artık desteklenmeyen Windows için Azure App Service uzaktan hata ayıklama için kullanılmıştır). |

## <a name="see-also"></a>Ayrıca bkz.

- [Python projelerini yönetme-Project şablonları](managing-python-projects-in-visual-studio.md#project-templates)
- [Python web projesi şablonları](python-web-application-project-templates.md)
- [Azure App Service’e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md)
