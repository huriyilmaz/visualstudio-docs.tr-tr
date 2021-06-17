---
title: Python için Azure bulut hizmeti proje şablonu
description: Visual Studio rol dağıtımı, bağımlılıklar ve sorun giderme dahil olmak üzere Python'da yazılmış Azure bulut hizmetleri için şablonlar sağlar.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
monikerRange: vs-2017
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 2de0f255da54d5bd8abf865f6534041d88bbbca3
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254842"
---
# <a name="azure-cloud-service-projects-for-python"></a>Python için Azure bulut hizmeti projeleri

Visual Studio, Python kullanarak yeni şablon oluşturmaya başlamanıza yardımcı Azure Cloud Services şablonlar sağlar.

Bulut [hizmeti,](/azure/cloud-services/) her biri  kavramsal olarak ayrı bir görev gerçekleştiren ancak ölçeklendirme için gerektiğinde sanal makineler arasında ayrı çoğaltılabilir olan herhangi bir sayıda çalışan rolü ve *web* rolüne sahip olur. Web rolleri, ön uç web uygulamaları için barındırma sağlar. Python söz konusu olduğunda, böyle bir uygulama yazmak için WSGI destekleyen tüm web çerçeveleri kullanılabilir (Web proje şablonu [tarafından desteklemektedir).](python-web-application-project-templates.md) Çalışan rolleri, kullanıcılarla doğrudan etkileşim kurmadan uzun süre çalışan işlemlere yöneliktir. Genellikle ile birlikte yüklü olan "azure" paketi içindeki paketleri [`pip install azure`](https://pypi.org/project/azure) kullanır.

Bu makale, 2017 ve sonraki sürümlerde proje şablonu ve diğer Visual Studio (önceki sürümler benzer, ancak bazı farklarla birlikte) hakkında ayrıntılar içerir. Python'dan Azure ile çalışma hakkında daha fazla bilgi için [Azure Python Geliştirici Merkezi'ne ziyaret edin.](/azure/python/)

## <a name="create-a-project"></a>Proje oluşturma

1. Bulut hizmeti şablonunu kullanmak için gereken Visual Studio için [Azure .NET](https://visualstudio.microsoft.com/vs/azure-tools/)SDK'sı yükleyin.
1. Yeni Visual Studio **Proje'yi** seçin, ardından "Azure Python" araması ve  >    >  listeden Azure **Bulut Hizmeti'ne** tıklayın:

    ![Python için Azure Bulut Projesi şablonu](media/template-azure-cloud-project.png)

1. Dahil etmek istediğiniz bir veya daha fazla rol seçin. Bulut projeleri farklı dillerde yazılmış rolleri birleştirebilir, bu nedenle uygulamanın her bir bölümünü en uygun dilde kolayca yazabilirsiniz. Bu iletişim kutusu tamamladıktan sonra projeye yeni roller  eklemek için, Çözüm Gezgini'de **Roller'e** sağ tıklayın ve Ekle'nin altındaki öğelerden birini **seçin.**

    ![Azure Bulut Projesi şablonuna rol ekleme](media/template-azure-cloud-service-project-wizard.png)

1. Tek tek rol projeleri oluşturulurken, bunlardan birini kullanan bir rol seçtiyebilirsiniz; Django, Bottle veya Flask çerçeveleri gibi ek Python paketlerini yüklemeniz istendiğinde.

1. Projenize yeni bir rol ekledikten sonra yapılandırma yönergeleri görüntülenir. Yapılandırma değişiklikleri genellikle gereksizdir, ancak gelecekteki projelerinizi özelleştirmeniz için yararlı olabilir. Aynı anda birden çok rol eklerken yalnızca son role ilişkin yönergelerin açık olduğunu unutmayın. Ancak, rolün kökünde veya bin klasöründe bulunan ilgili *readme.mht* dosyalarında diğer rollere yönelik yönergeleri ve sorun giderme *ipuçlarını bulabilirsiniz.*

1. Projenin bin *klasörü ayrıca* Python'u yükleme, projenize herhangi birrequirements.txtdosyası yükleme ve [](#dependencies) gerekirse IIS'yi ayarlama da dahil olmak üzere uzak sanal makineyi yapılandırmak için kullanılan bir veya iki PowerShell betikleri içerir. Bu dosyaları dağıtımınız için istediğiniz şekilde düzenleyebilirsiniz, ancak en yaygın seçenekler farklı şekillerde yönetilebilir (aşağıdaki Rol dağıtımını [yapılandırma).](#configure-role-deployment) Bu dosyaların kaldırılmasını önermez çünkü dosyalar kullanılamıyorsa eski bir yapılandırma betiği kullanılır.

    ![Çalışan Rolü Destek Dosyaları](media/template-azure-cloud-service-worker-role-support-files.png)

    Bu yapılandırma betiklerini yeni bir projeye eklemek için projeye sağ tıklayın, Yeni Öğe Ekle'yi seçin ve Web Rolü Destek Dosyaları'nın veya Çalışan Rolü Destek  >   **Dosyaları'nın birini seçin.** 

## <a name="configure-role-deployment"></a>Rol dağıtımını yapılandırma

Rol projesinin bin klasöründeki  PowerShell betikleri, bu rolün dağıtımını kontrol altına alın ve yapılandırmayı özelleştirmek için düzenlenebilir:

- *ConfigureCloudService.ps1,* genellikle bağımlılıkları yüklemek, yapılandırmak ve Python sürümünü ayarlamak için web ve çalışan rolleri için kullanılır.
- *LaunchWorker.ps1* yalnızca çalışan rolleri için kullanılır ve başlangıç davranışını değiştirmek, komut satırı bağımsız değişkenleri eklemek veya ortam değişkenleri eklemek için kullanılır.

Her iki dosya da özelleştirme yönergeleri içerir. Ayrıca, ana bulut hizmeti *projesinin ServiceDefinition.csdef* dosyasına başka bir görev ekleyerek, değişkeni yüklüpython.exe(veya eşdeğeri) yoluna ayarleyerek kendi Python `PYTHON` *sürümünü* yükleyebilirsiniz. Ayar `PYTHON` olduğunda, Python NuGet'den yüklenmez.

Ek yapılandırma aşağıdaki gibi gerçeklenebilir:

1. Projenizin kök `pip` dizininde *requirements.txt* dosyasını güncelleştirerek paketleri yükleyin. ConfigureCloudService.ps1 betiği bu dosyayı dağıtıma yüklür.
1. web.configdosyanızı (web *rolleri)* veya `Runtime` *ServiceDefinition.csdef* dosyanız (çalışan rolleri) bölümünü değiştirerek ortam değişkenlerini ayarlayın.
1. `Runtime/EntryPoint` *ServiceDefinitions.csdef* dosyanız bölümündeki komut satırı değiştirerek bir çalışan rolü için kullanmak üzere betiği ve bağımsız değişkenleri belirtin.
1. Bir web rolü için ana işleyici betiği, *web.config* ayarlayın.

## <a name="test-role-deployment"></a>Rol dağıtımını test etmek

Rollerinizi yazarken Bulut Hizmeti Öykünücüsü'ünü kullanarak bulut projenizi yerel olarak test edin. Öykünücü, Azure SDK Tools dahil edilir ve bulut hizmetiniz Azure'da yayımlanırken kullanılan ortamın sınırlı bir sürümüdür.

Öykünücüye başlamak için öncelikle sağ tıklar ve Başlangıç projesi olarak ayarla'ya tıklayarak bulut projenizin **çözümünüzde başlangıç projesi olduğundan emin olur.** Ardından Hata **AyıklamaYı Başlat Hata** Ayıklama ( F5 ) veya Hata Ayıklama Olmadan Başlat  >   (   >   **Ctrl** F5 ) + **seçeneğini seçin.**

Öykünücüde yer alan sınırlamalar nedeniyle Python kodunda hata ayıklamanın mümkün olmadığını unutmayın. Bu nedenle, rolleri bağımsız olarak çalıştırarak rollerin hata ayıklaması ve yayımlamadan önce tümleştirme testi için öykünücü kullanmaları önerilir.

## <a name="deploy-a-role"></a>Rol dağıtma

Yayımla **sihirbazını** açmak için,  Çözüm Gezgini projesinde rol projesini seçin ve ana menüden Yayımla'yı seçin veya projeye sağ  >   tıklar ve Yayımla'yı **seçin.**

Yayımlama işlemi iki aşama içerir. İlk Visual Studio, bulut hizmetiniz için tüm rolleri içeren tek bir paket oluşturur. Bu paket, Her rol için bir veya daha fazla sanal makine başlatan ve kaynağı dağıtan Azure'a dağıtılan pakettir.

Her sanal makine etkinleştirildikten sonra,ConfigureCloudService.ps1 *betiği* yürütür ve tüm bağımlılıkları yüklenir. Bu betik varsayılan olarak [NuGet'den](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) Python'ın son sürümünü ve bir python dosyasında belirtilen *requirements.txt* yüklenir.

Son olarak, çalışan rolleri *LaunchWorker.ps1* python betiğinizi çalıştırmaya başlar; web rolleri IIS'yi başlatıyor ve web isteklerini işlemeye başlıyor.

## <a name="dependencies"></a>Bağımlılıklar

Bu Cloud Services, *ConfigureCloudService.ps1* Python `pip` bağımlılıkları kümesi yüklemek için kullanır. Bağımlılıklar,requirements.txt *adlı* bir dosyada belirtilmelidir *(ConfigureCloudService.ps1).* Dosya, başlatmanın `pip install -r requirements.txt` bir parçası olarak ile yürütülür.

Bulut hizmeti örnekleri C derleyicilerini içermez, bu nedenle C uzantılarına sahip tüm kitaplıkların önceden derlenmiş ikili dosyalar sağlamaları gerekir.

pip ve bağımlılıkları ile birlikterequirements.txt ** paketleri otomatik olarak indirilir ve ücrete bağlı bant genişliği kullanımı olarak kabul edilebilir. Veri [dosyalarını yönetme hakkında](managing-required-packages-with-requirements-txt.md) ayrıntılı bilgi için bkz. Gerekli *requirements.txt* yönetme.

## <a name="troubleshooting"></a>Sorun giderme

Dağıtımdan sonra web veya çalışan rolünüz doğru şekilde davranamasa, şunları denetleyin:

- Python projeniz ile bir *bin \\* klasörü içerir (en azından):

  - *ConfigureCloudService.ps1*
  - *LaunchWorker.ps1* (çalışan rolleri için)
  - *ps.cmd*

- Python projeniz, *tümrequirements.txt* (veya alternatif olarak bir tekerlek dosyası koleksiyonu) listeli bir dosya içerir.
- Bulut hizmetiniz üzerinde Uzak Masaüstü'leri etkinleştirin ve günlük dosyalarını araştırın.
- Günlükler *ConfigureCloudService.ps1* *LaunchWorker.ps1* *C:\Resources\Directory \% RoleId% dizininde depolanır. Uzak bilgisayarda DiagnosticStore\LogFiles* klasörü.
- Web rolleri, appSetting'te yolu ** web.configbir yola ek `WSGI_LOG` günlükler yazabilir. Çoğu normal IIS veya FastCGI günlüğü de çalışır.
- Şu anda *LaunchWorker.ps1.log* dosyası, Python çalışan rolünüz tarafından görüntülenen çıkışı veya hataları görüntülemenin tek yolu.
