---
title: Python için Azure bulut hizmeti proje şablonu
description: Visual Studio, python'da yazılmış rol dağıtımı, bağımlılıklar ve sorun giderme gibi Azure bulut hizmetleri için şablonlar sağlar.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 4d205ee2bbc0a6e9c44c34f3b0487abb4f22283e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72983657"
---
# <a name="azure-cloud-service-projects-for-python"></a>Python için Azure bulut hizmeti projeleri

Visual Studio, Python'u kullanarak Azure Bulut Hizmetleri oluşturmaya başlamanıza yardımcı olacak şablonlar sağlar.

Bulut [hizmeti,](/azure/cloud-services/) her biri kavramsal olarak ayrı bir görev gerçekleştiren, ancak ölçekleme için gerektiğinde sanal makineler arasında ayrı ayrı çoğaltılabilen herhangi bir sayıda çalışan rolü ve *web rolünden*oluşur. *worker roles* Web rolleri ön uç web uygulamaları için barındırma sağlar. Python söz konusu olduğunda, WSGI destekleyen herhangi bir web çerçevesi böyle bir uygulama yazmak için kullanılabilir [(Web proje şablonu](python-web-application-project-templates.md)tarafından desteklenen). Çalışan rolleri, kullanıcılarla doğrudan etkileşime girmeden uzun süren işlemler için tasarlanmıştır. Genellikle "azure" paketi içinde paketleri kullanmak, hangi ile [`pip install azure`](https://pypi.org/project/azure)yüklenir.

Bu makalede, Visual Studio 2017 ve sonraki sürümlerde proje şablonu ve diğer destek le ilgili ayrıntılar bulunur (önceki sürümler benzerdir, ancak bazı farklılıklar vardır). Python'dan Azure ile çalışma hakkında daha fazla bilgi için [Azure Python Geliştirici Merkezi'ni](/azure/python/)ziyaret edin.

## <a name="create-a-project"></a>Proje oluşturma

1. Bulut hizmeti şablonunu kullanmak için gereken [Visual Studio için Azure .NET SDK'yı](https://visualstudio.microsoft.com/vs/azure-tools/)yükleyin.
1. Visual Studio'da **Dosya** > **Yeni** > **Projesi'ni**seçin, ardından "Azure Python"u arayın ve listeden Azure Bulut **Hizmeti'ni** seçin:

    ![Python için Azure Bulut Projesi şablonu](media/template-azure-cloud-project.png)

1. Eklemek için bir veya daha fazla rol seçin. Bulut projeleri farklı dillerde yazılmış rolleri birleştirebilir, böylece uygulamanızın her bölümünü en uygun dilde kolayca yazabilirsiniz. Bu iletişim kutusunu tamamladıktan sonra projeye yeni roller eklemek **için, Çözüm Gezgini'nde** **Roller'i** sağ tıklatın ve **Ekle'nin**altındaki öğelerden birini seçin.

    ![Azure Bulut Projesi şablonuna rol ekleme](media/template-azure-cloud-service-project-wizard.png)

1. Tek tek rol projeleri oluşturulduğunda, bunlardan birini kullanan bir rol seçtiyseniz, Django, Şişe veya Flask çerçeveleri gibi ek Python paketleri yüklemeniz istenebilir.

1. Projenize yeni bir rol ekledikten sonra yapılandırma yönergeleri görüntülenir. Yapılandırma değişiklikleri genellikle gereksizdir, ancak projelerinizin gelecekteki özelleştirmesi için yararlı olabilir. Aynı anda birden çok rol eklerken, yalnızca son rol için yönergelerin açık kaldığını unutmayın. Ancak, diğer rollerin yönergelerini ve sorun giderme ipuçlarını, rolün kökünde veya *depo* gözü klasöründe bulunan ilgili *readme.mht* dosyalarında bulabilirsiniz.

1. Projenin çöp *kutusu* klasörü, Python'u, projenizde herhangi bir [*gereksinim.txt*](#dependencies) dosyasını yüklemek ve gerekirse IIS'yi kurmak da dahil olmak üzere uzak sanal makineyi yapılandırmak için kullanılan bir veya iki PowerShell komut dosyası da içerir. Bu dosyaları dağıtımınızda istediğiniz gibi ayarlayabilirsiniz, ancak en yaygın seçenekler başka şekillerde yönetilebilir (aşağıdaki [rol dağıtımını yapılandırın).](#configure-role-deployment) Dosyalar kullanılamıyorsa, bunun yerine eski bir yapılandırma komut dosyası kullanıldığından, bu dosyaların kaldırılmasını önermiyoruz.

    ![İşçi Rolü Destek Dosyaları](media/template-azure-cloud-service-worker-role-support-files.png)

    Bu yapılandırma komut dosyalarını yeni bir projeye eklemek için projeye sağ tıklayın,**Yeni Öğe** **Ekle'yi** > seçin ve Web Rolü Destek Dosyaları veya İşçi Rolü **Destek** **Dosyaları'nı**seçin.

## <a name="configure-role-deployment"></a>Rol dağıtımını yapılandırma

Rol projesinin *çöp kutusu* klasöründeki PowerShell komut dosyaları bu rolün dağıtımını denetler ve yapılandırmayı özelleştirmek için düzenlenebilir:

- *ConfigureCloudService.ps1* web ve çalışan rolleri için kullanılır, genellikle bağımlılıkları yüklemek ve yapılandırmak ve Python sürümünü ayarlamak için.
- *LaunchWorker.ps1* yalnızca çalışan rolleri için kullanılır ve başlangıç davranışını değiştirmek, komut satırı bağımsız değişkenleri eklemek veya ortam değişkenleri eklemek için kullanılır.

Her iki dosya da özelleştirme yönergeleri içerir. Ayrıca, ana bulut hizmeti projesinin *ServiceDefinition.csdef* dosyasına başka bir görev ekleyerek, `PYTHON` değişkeni yüklü *python.exe* (veya eşdeğeri) yoluna ayarlayarak kendi Python sürümünüzü yükleyebilirsiniz. Ayarlandığında, `PYTHON` Python NuGet'den yüklenmez.

Ek yapılandırma aşağıdaki gibi gerçekleştirilebilir:

1. `pip` *Gereksinimleri.txt* dosyasını projenizin kök dizininde güncelleyerek paketleri yükleyin. *ConfigureCloudService.ps1* komut dosyası bu dosyayı dağıtıma yükler.
1. *web.config* dosyanızı (web rolleri) veya `Runtime` *ServiceDefinition.csdef* dosyanızın (işçi rolleri) bölümünü değiştirerek ortam değişkenlerini ayarlayın.
1. `Runtime/EntryPoint` *ServiceDefinitions.csdef* dosyanızın bölümündeki komut satırını değiştirerek, bir alt rol için kullanılacak komut dosyasını ve bağımsız değişkenlerini belirtin.
1. *Web.config* dosyası aracılığıyla bir web rolü için ana işleyici komut dosyasını ayarlayın.

## <a name="test-role-deployment"></a>Test rolü dağıtımı

Rollerinizi yazarken Bulut Hizmeti Emülatörü'ni kullanarak bulut projenizi yerel olarak test edebilirsiniz. Emülatör Azure SDK Araçlarına dahildir ve bulut hizmetiniz Azure'da yayımlandığında kullanılan ortamın sınırlı bir sürümüdür.

Emülatöre başlamak için öncelikle bulut projenizin, **başlangıç projesi olarak Set'e**sağ tıklayıp seçerek çözümünüzdeki başlangıç projesi olduğundan emin olun. Ardından **Hata** > **Ayıklama** **(F5)** **veya** > **Hata Ayıklama Başlatma** 'yı **(Ctrl**+**F5)** seçmeden başlat' ı seçin.

Emülatördeki sınırlamalar nedeniyle Python kodunuzu hata ayıklamanın mümkün olmadığını unutmayın. Bu nedenle, rolleri bağımsız olarak çalıştırarak hata ayıklamanızı öneririz ve yayımlamadan önce tümleştirme sınamak için emülatör kullanmanızı öneririz.

## <a name="deploy-a-role"></a>Bir rol dağıtma

**Yayımla** sihirbazını açmak için **Çözüm Gezgini'ndeki** rol projesini seçin ve ana menüden**Yayımla'yı** **Build** > seçin veya projeyi sağ tıklatın ve **Yayımla'yı**seçin.

Yayımlama işlemi iki aşamadan içerir. İlk olarak, Visual Studio bulut hizmetiniz için tüm rolleri içeren tek bir paket oluşturur. Bu paket, her rol için bir veya daha fazla sanal makinenin başlatılmasını sağlayan ve kaynağı dağıtan Azure'a dağıtılan pakettir.

Her sanal makine etkinleştirilirgibi, *ConfigureCloudService.ps1* komut dosyası yürütür ve herhangi bir bağımlılık yükler. Bu komut dosyası varsayılan olarak [NuGet'den](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) Python'un son sürümünü ve *requirements.txt* dosyasında belirtilen paketleri yükler.

Son olarak, alt roller Python komut dosyanızı çalıştırmaya başlayan *LaunchWorker.ps1'i*çalıştırın; web rolleri IIS'yi başlatın ve web isteklerini işlemeye başlar.

## <a name="dependencies"></a>Bağımlılıklar

Bulut Hizmetleri için *ConfigureCloudService.ps1* `pip` komut dosyası, bir dizi Python bağımlılığı yüklemek için kullanır. Bağımlılıklar *requirements.txt* adlı bir dosyada belirtilmelidir *(ConfigureCloudService.ps1*değiştirerek özelleştirilebilir). Dosya başlatma nın `pip install -r requirements.txt` bir parçası olarak yürütülür.

Bulut hizmeti örneklerinin C derleyicileri içermediğini, bu nedenle C uzantılı tüm kitaplıkların önceden derlenmiş ikili ler sağlaması gerektiğini unutmayın.

pip ve bağımlılıkları ve *requirements.txt'deki*paketler otomatik olarak indirilir ve ücretlendirilebilir bant genişliği kullanımı olarak sayılabilir. *Gereksinimleri yönetme.txt* dosyaları hakkında ayrıntılar için [gerekli paketleri yönet'e](managing-required-packages-with-requirements-txt.md) bakın.

## <a name="troubleshooting"></a>Sorun giderme

Web veya çalışan rolünüz dağıtımdan sonra doğru şekilde çalışmıyorsa, aşağıdakileri kontrol edin:

- Python projeniz *\\ * (en azından):

  - *CloudService.ps1 Yapıla*
  - *LaunchWorker.ps1* (işçi rolleri için)
  - *ps.cmd*

- Python projeniz tüm bağımlılıkları (veya dönüşümlü olarak tekerlek dosyaları koleksiyonunu) listeleyen bir *requirements.txt* dosyası içerir.
- Bulut hizmetinizde Uzak Masaüstü'nü etkinleştirin ve günlük dosyalarını araştırın.
- *ConfigureCloudService.ps1* ve *LaunchWorker.ps1* günlükleri *C:\Resources\Directory\%RoleId%olarak depolanır. Uzak bilgisayarda DiagnosticStore\LogFiles* klasörü.
- Web *rolleri, web.config'de*yapılandırılan bir yola ek günlükler `WSGI_LOG` yazabilir, yani appSetting'teki yol. En düzenli IIS veya FastCGI günlük de çalışır.
- Şu anda *LaunchWorker.ps1.log* dosyası, Python alt rolünüz tarafından görüntülenen çıktıveya hataları görüntülemenin tek yoludur.
