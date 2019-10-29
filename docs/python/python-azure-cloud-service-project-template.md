---
title: Python için Azure bulut hizmeti proje şablonu
description: Visual Studio, rol dağıtımı, bağımlılıklar ve sorun giderme dahil olmak üzere Python 'da yazılmış Azure bulut hizmetleri için şablonlar sağlar.
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
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983657"
---
# <a name="azure-cloud-service-projects-for-python"></a>Python için Azure bulut hizmeti projeleri

Visual Studio, Python kullanarak Azure Cloud Services oluşturmaya başlamanıza yardımcı olacak şablonlar sağlar.

[Bulut hizmeti](/azure/cloud-services/) herhangi bir sayıda *çalışan rolünden* ve *web rolünden*oluşur ve her biri kavramsal olarak ayrı bir görev gerçekleştirir, ancak ölçeklendirme için gerektiğinde sanal makinelerde ayrı olarak çoğaltılabilirler. Web rolleri, ön uç Web uygulamaları için barındırma sağlar. Python 'un ilgilendiğinde, WSGI 'yi destekleyen herhangi bir Web çerçevesi bu tür bir uygulamayı yazmak için kullanılabilir ( [Web projesi şablonu](python-web-application-project-templates.md)tarafından desteklenir). Çalışan rolleri, kullanıcılarla doğrudan etkileşimde bulunmayan uzun süre çalışan işlemlere yöneliktir. Genellikle, [`pip install azure`](https://pypi.org/project/azure)ile yüklenen "Azure" paketindeki paketleri kullanırlar.

Bu makalede, Visual Studio 2017 ve üzeri sürümlerde proje şablonu ve diğer destek ile ilgili ayrıntılar yer almaktadır (önceki sürümler benzerdir ancak bazı farklardır). Python 'dan Azure ile çalışma hakkında daha fazla bilgi için [Azure Python Geliştirici Merkezi](/azure/python/)' ni ziyaret edin.

## <a name="create-a-project"></a>Proje oluşturma

1. Bulut hizmeti şablonunu kullanmak için gerekli olan [Visual Studio Için Azure .NET SDK 'sını](https://visualstudio.microsoft.com/vs/azure-tools/)yükler.
1. Visual Studio 'da **dosya** > **Yeni** > **Proje**' yi seçin, ardından "Azure Python" araması yapın ve listeden **Azure Cloud Service** ' i seçin:

    ![Python için Azure bulut proje şablonu](media/template-azure-cloud-project.png)

1. Dahil edilecek bir veya daha fazla rol seçin. Bulut projeleri farklı dillerde yazılmış rolleri birleştirebilir, böylece uygulamanızın her bölümünü en uygun dilde kolayca yazabilirsiniz. Bu iletişim kutusunu tamamladıktan sonra projeye yeni roller eklemek için **Çözüm Gezgini** **Roller** ' e sağ tıklayın ve **Ekle**' nin altındaki öğelerden birini seçin.

    ![Azure bulut proje şablonunda rol ekleme](media/template-azure-cloud-service-project-wizard.png)

1. Tek tek rol projeleri oluşturulduğunda, bunlardan birini kullanan bir rol seçtiyseniz Docgo, şişe veya Flask çerçeveleri gibi ek Python paketleri kurmanız istenebilir.

1. Projenize yeni bir rol eklendikten sonra, yapılandırma yönergeleri görünür. Yapılandırma değişiklikleri genellikle gereksizdir, ancak projelerinizi daha sonra özelleştirmek için faydalı olabilir. Aynı anda birden çok rol eklenirken, yalnızca son rolün yönergelerinin açık kalacağını unutmayın. Bununla birlikte, ilgili *Benioku. mht* dosyalarındaki diğer roller için, rol kökünde veya *bin* klasöründe bulunan yönergeler ve sorun giderme ipuçları bulabilirsiniz.

1. Bir projenin *bin* klasörü, Python yükleme, projenizdeki tüm [*gereksinimler. txt*](#dependencies) dosyası ve gerekirse IIS 'yi ayarlama dahil olmak üzere uzak sanal makineyi yapılandırmak için kullanılan bir veya iki PowerShell komut dosyasını da içerir. En yaygın seçeneklerin diğer yollarla yönetilebilmesi için, bu dosyaları dağıtımınıza istediğiniz şekilde düzenleyebilirsiniz (bkz. aşağıdaki [rol dağıtımını yapılandırma](#configure-role-deployment) ). Dosyalar kullanılabilir değilse, eski bir yapılandırma betiği kullanıldığından, bu dosyaları kaldırmayı önermiyor.

    ![Çalışan rolü destek dosyaları](media/template-azure-cloud-service-worker-role-support-files.png)

    Bu yapılandırma betiklerini yeni bir projeye eklemek için projeye sağ tıklayın, > **Yeni öğe** **Ekle** ' yi seçin ve **Web rolü destek dosyaları** ya da **çalışan rolü destek dosyaları**' nı seçin.

## <a name="configure-role-deployment"></a>Rol dağıtımını yapılandırma

Bir rol projesinin *bin* klasöründeki PowerShell betikleri, bu rolün dağıtımını denetler ve yapılandırmayı özelleştirmek için düzenlenebilir.

- *Configurechoparlör Service. ps1* , genellikle bağımlılıkları yükleyip yapılandırmak ve Python sürümünü ayarlamak için Web ve çalışan rolleri için kullanılır.
- *Launchworker. ps1* yalnızca çalışan rolleri için kullanılır ve başlangıç davranışını değiştirmek, komut satırı bağımsız değişkenleri eklemek veya ortam değişkenleri eklemek için kullanılır.

Her iki dosya de özelleştirmeye yönelik yönergeler içerir. Ayrıca, ana bulut hizmeti projesinin *ServiceDefinition. csdef* dosyasına başka bir görev ekleyerek, Python 'un kendi sürümünüzü yükleyebilirsiniz. `PYTHON` değişkenini yüklü *Python. exe* (veya eşdeğer) yoluna ayarlayabilirsiniz. `PYTHON` ayarlandığında, Python, NuGet 'ten yüklenmez.

Ek yapılandırma aşağıdaki şekilde gerçekleştirilebilir:

1. Projenizin kök dizinindeki *requirements. txt* dosyasını güncelleştirerek `pip` kullanarak paket yükler. *Configurechoparlör Service. ps1* betiği bu dosyayı dağıtıma yüklenir.
1. *Web. config* dosyanızı (Web rolleri) veya *ServiceDefinition. csdef* dosyanızın (çalışan rolleri) `Runtime` bölümünü değiştirerek ortam değişkenlerini ayarlayın.
1. *Servicedefinitions. csdef* dosyanızın `Runtime/EntryPoint` bölümündeki komut satırını değiştirerek bir çalışan rolü için kullanılacak betiği ve bağımsız değişkenleri belirtin.
1. Web *. config* dosyası aracılığıyla bir Web rolü için ana işleyici betiği ayarlayın.

## <a name="test-role-deployment"></a>Test rolü dağıtımı

Rollerinizi yazarken, bulut hizmeti öykünücüsünü kullanarak bulut projenizi yerel olarak test edebilirsiniz. Öykünücü Azure SDK Tools dahildir ve bulut hizmetiniz Azure 'da yayımlandığında kullanılan ortamın sınırlı bir sürümüdür.

Öykünücüyü başlatmak için önce bulut projenizin çözümünüzdeki başlangıç projesi olduğundan emin olun ve **Başlangıç projesi olarak ayarla**' yı seçin. Ardından hata ayıklamayı **Başlat** (**F5** **) veya hata ayıklama > ** hata **ayıklama olmadan başlat** ' ı ** > seçin (** **CTRL**+**F5**).

Öykünücüdeki sınırlamalar nedeniyle Python kodunuzda hata ayıklama mümkün olmadığı unutulmamalıdır. Bu nedenle, rolleri bağımsız olarak çalıştırarak hata ayıklamanızı ve yayımlamadan önce tümleştirme testi için öykünücüyü kullanmanızı öneririz.

## <a name="deploy-a-role"></a>Rol dağıtma

**Yayımla** Sihirbazı 'nı açmak için **Çözüm Gezgini** ' de rol projesi seçin ve ana menüden **derleme** > **Yayımla** ' yı seçin veya projeye sağ tıklayıp **Yayımla**' yı seçin.

Yayımlama işlemi iki aşamadan oluşur. İlk olarak, Visual Studio bulut hizmetiniz için tüm rolleri içeren tek bir paket oluşturur. Bu paket, her rol için bir veya daha fazla sanal makine başlatan ve kaynağı dağıtan Azure 'a dağıtılır.

Her sanal makine etkinleştiğinde *Configurechoparlör Service. ps1* betiğini yürütür ve tüm bağımlılıkları kurar. Bu komut dosyası varsayılan olarak, [NuGet](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) 'den en son Python sürümünü ve *requirements. txt* dosyasında belirtilen paketleri kurar.

Son olarak, çalışan rolleri, Python betiğinizi çalıştırmaya başlayan *Launchworker. ps1*öğesini yürütür; Web rolleri IIS 'yi başlatır ve Web isteklerini işlemeye başlar.

## <a name="dependencies"></a>Bağımlılıklar

Cloud Services için *Configurechoparlör Service. ps1* betiği bir Python bağımlılıkları kümesini yüklemek için `pip` kullanır. Bağımlılıklar, *requirements. txt* adlı bir dosyada belirtilmelidir ( *Configurechoparlör Service. ps1*' i değiştirerek özelleştirilebilir). Dosya, başlatmanın bir parçası olarak `pip install -r requirements.txt` ile yürütülür.

Bulut hizmeti örneklerinin C derleyicileri içermiyorsa, bu nedenle C uzantılarına sahip tüm kitaplıkların önceden derlenmiş ikili dosyalar sağlaması gerekir.

PIP ve bağımlılıkları ve *gereksinimleri. txt*içindeki paketler otomatik olarak indirilir ve Borçlandırılabilir bant genişliği kullanımı olarak sayılabilir. *Requirements. txt* dosyalarını yönetme hakkında ayrıntılı bilgi için bkz. [gerekli paketleri yönetme](managing-required-packages-with-requirements-txt.md) .

## <a name="troubleshooting"></a>Sorun giderme

Web veya çalışan rolünüzün dağıtımdan sonra düzgün davranması durumunda, aşağıdakileri denetleyin:

- Python projeniz, (en az) içeren bir *bin\\* klasörü içerir:

  - *Configurecses hizmeti. ps1*
  - *Launchworker. ps1* (çalışan rolleri için)
  - *PS. cmd*

- Python projeniz, tüm bağımlılıkları (veya alternatif olarak bir tekerlek dosyaları koleksiyonunu) listelemek için bir *requirements. txt* dosyası içerir.
- Bulut hizmetinizde uzak masaüstü 'Nü etkinleştirin ve günlük dosyalarını araştırın.
- *Configurechoparlör Service. ps1* ve *launchworker. ps1* günlükleri *C:\resources\directory\%RoleID% yolunda depolanır. Uzak bilgisayardaki DiagnosticStore\LogFiles* klasörü.
- Web rolleri, *Web. config*' de yapılandırılmış bir yola ek Günlükler yazabilir, yani `WSGI_LOG` AppSetting yolunda yer alabilir. Çoğu normal IIS veya FastCGI günlüğü de geçerlidir.
- Şu anda, Python Worker rolünüzde görüntülenen çıktıyı veya hataları görüntülemenin tek yolu, *launchworker. ps1. log* dosyasıdır.
