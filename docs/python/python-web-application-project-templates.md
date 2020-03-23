---
title: Python için Web uygulama şablonları
description: Visual Studio, Şişe, Flask ve Django çerçevelerini kullanarak Python web uygulamaları için şablonlar sağlar; destek, hata ayıklama yapılandırmalarını ve Azure Uygulama Hizmeti'nde yayımlamayı içerir.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 73420f5fa6a90638f4a3dbbdf484178c5e177ce9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302758"
---
# <a name="python-web-application-project-templates"></a>Python web uygulaması proje şablonları

Visual Studio'daki Python, proje şablonları ve çeşitli çerçeveleri işledecek şekilde yapılandırılabilen hata ayıklama başlatıcısı aracılığıyla Bottle, Flask ve Django çerçevelerinde web projeleri geliştirmeyi destekler. Bu şablonlar gerekli bağımlılıkları bildirmek için bir *requirements.txt* dosyası içerir. Bu şablonlardan birinden proje oluştururken, Visual Studio bu paketleri yüklemenizi ister (bu makalenin ilerleyen saatlerinde [proje gereksinimlerini yükleyin' e](#install-project-requirements) bakın).

Piramit gibi diğer çerçeveler için genel **Web Project** şablonu da kullanabilirsiniz. Bu durumda, şablonla birlikte hiçbir çerçeve yüklenir. Bunun yerine, proje için kullandığınız ortama gerekli paketleri yükleyin [(bkz. Python ortamları penceresi - Paket sekmesi).](python-environments-window-tab-reference.md#packages-tab)

Bir Python web uygulamasını Azure'a dağıtma hakkında bilgi [için](publishing-python-web-applications-to-azure-from-visual-studio.md)bkz.

## <a name="use-a-project-template"></a>Proje şablonu kullanma

 > **New**Yeni >  **Dosya****Projesi'ni**kullanarak şablondan bir proje oluşturursunuz. Web projeleri için şablonları görmek için iletişim kutusunun sol tarafındaki **Python** > **Web'i** seçin. Ardından, proje ve çözüm için adlar sağlayarak, çözüm dizini ve Git deposu için seçenekler belirleyin ve **Tamam'ı**seçin.

![Web uygulamaları için yeni proje iletişim kutusu](media/projects-new-project-dialog-web.png)

Daha önce bahsedilen genel **Web Projesi** şablonu, yalnızca bir Python projesi olmaktan başka bir kodu ve varsayımı olmayan boş bir Visual Studio projesi sağlar. Azure Bulut **Hizmeti** şablonu yla ilgili ayrıntılar için [Python için Azure bulut hizmeti projelerine](python-azure-cloud-service-project-template.md)bakın.

Diğer tüm şablonlar Şişe, Flask veya Django web çerçevelerini temel alınarak aşağıdaki bölümlerde açıklandığı gibi üç genel gruba ayrılır. Bu şablonlardan herhangi biri tarafından oluşturulan uygulamalar, uygulamayı yerel olarak çalıştırmak ve hata ayıklamak için yeterli kod içerir. Her biri aynı zamanda üretim web sunucuları ile kullanılmak üzere gerekli [WSGI uygulama nesnesi](https://www.python.org/dev/peps/pep-3333/) (python.org) sağlar.

### <a name="blank-group"></a>Boş grup

**Tüm \<Boş çerçeve> Web Project** şablonları, daha fazla veya daha az en az ortak koda ve *gereksinimler.txt* dosyasında bildirilen gerekli bağımlılıklara sahip bir proje oluşturur.

| Şablon | Açıklama |
| --- | --- |
| **Boş Şişe Web Projesi** | Çok kısa bir satır içi sayfa `/` şablonu `/hello/<name>` kullanarak yankılanan `<name>` bir sayfa ile *app.py* içinde en az uygulama oluşturur. |
| **Boş Django Web Projesi** | Çekirdek Django site yapısı ile bir Django proje oluşturur ama hiçbir Django uygulamaları. Daha fazla bilgi için [Django şablonlarına](python-django-web-application-project-template.md) bakın ve [Django Adım 1'i öğrenin.](learn-django-in-visual-studio-step-01-project-and-solution.md) |
| **Boş Flask Web Projesi** | Tek bir "Hello World!" ile minimal bir uygulama oluşturur. için `/`sayfa . Bu uygulama Quickstart ayrıntılı adımları aşağıdaki sonucu [benzer: İlk Python web uygulaması oluşturmak için Visual Studio kullanın.](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) Ayrıca [bkz.](learn-flask-visual-studio-step-01-project-solution.md)

### <a name="web-group"></a>Web grubu

Tüm ** \<Framework> Web Project** şablonları, seçilen çerçeveden bağımsız olarak aynı tasarıma sahip bir başlangıç web uygulaması oluşturur. Uygulamanın Ana Sayfa, Hakkında ve İletişim sayfalarının yanı sıra bir navigasyon çubuğu ve Bootstrap'ı kullanarak duyarlı tasarım vardır. Her uygulama statik dosyalara (CSS, JavaScript ve yazı tipleri) hizmet etmek üzere uygun şekilde yapılandırılır ve çerçeveye uygun bir sayfa şablonu mekanizması kullanır.

| Şablon | Açıklama |
| --- | --- |
| **Şişe Web Projesi** | Statik dosyaları *statik* klasörde bulunan ve *app.py*kod aracılığıyla işlenen bir uygulama oluşturur. Tek tek sayfalar için yönlendirme *routes.py*bulunur ve *görünümler* klasöründe sayfa şablonları bulunur.|
| **Django Web Projesi** | Bir Django projesi ve üç sayfa, kimlik doğrulama desteği ve Bir SQLite veritabanı (ancak veri modelleri) ile bir Django uygulaması oluşturur. Daha fazla bilgi için [Django şablonlarına](python-django-web-application-project-template.md) bakın ve [Django Adım 4'e öğrenin.](learn-django-in-visual-studio-step-04-full-django-project-template.md) |
| **Flask Web Projesi** | Statik dosyaları *statik* klasörde bulunan bir uygulama oluşturur. *views.py'daki* kod, *şablonlar* klasöründe bulunan Jinja altyapısını kullanarak sayfa şablonları ile yönlendirmeyi işler. *runserver.py* dosyası başlangıç kodu sağlar. Bkz. [Flask Adım 4 öğrenin](learn-flask-visual-studio-step-04-full-flask-project-template.md). |
| **Flask/Yeşim Web Projesi** | **Flask Web Project** şablonu ile aynı uygulamayı oluşturur ancak Jinja cazip motoru için Yeşim uzantısını kullanır. |

### <a name="polls-group"></a>Anketler grubu

Web Project şablonları **> \<Anketler çerçevesi,** kullanıcıların farklı anket sorularında oy kullanabileceği bir başlangıç web uygulaması oluşturur. Her uygulama, anketleri ve kullanıcı yanıtlarını yönetmek için bir veritabanı kullanmak üzere **Web** proje şablonlarının yapısına göre inşa edilmiştir. Uygulamalar, uygun veri modellerini ve *bir samples.json* dosyasından anketleri yükleyen özel bir uygulama sayfası (/tohum) içerir.

| Şablon | Açıklama |
| --- | --- |
| **Anketler Şişe Web Projesi** | `REPOSITORY_NAME` Ortam değişkeni kullanılarak yapılandırılan bellek içi veritabanı, MongoDB veya Azure Tablo Depolamasına karşı çalışan bir uygulama oluşturur. Veri modelleri ve veri deposu kodu *modeller* klasöründe bulunur ve *settings.py* dosyası hangi veri deposunun kullanıldığını belirlemek için kod içerir. |
| **Anketler Django Web Projesi** | Bir Django projesi ve üç sayfa ve bir SQLite veritabanı ile bir Django uygulaması oluşturur. Kimlik doğrulaması yapılan bir yöneticinin anketler oluşturmasına ve yönetmesine izin vermek için Django yönetim arabirimine özelleştirmeler içerir. Daha fazla bilgi için [Django şablonlarına](python-django-web-application-project-template.md) bakın ve [Django Adım 6'yı öğrenin.](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md) |
| **Anketler Flask Web Projesi** | `REPOSITORY_NAME` Ortam değişkeni kullanılarak yapılandırılan bellek içi veritabanı, MongoDB veya Azure Tablo Depolamasına karşı çalışan bir uygulama oluşturur. Veri modelleri ve veri deposu kodu *modeller* klasöründe bulunur ve *settings.py* dosyası hangi veri deposunun kullanıldığını belirlemek için kod içerir. Uygulama sayfa şablonları için Jinja motorkullanır. Bkz. [Flask Adım 5 öğrenin](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md). |
| **Anketler Flask / Yeşim Web Projesi** | **Polls Flask Web Project** şablonu yla aynı uygulamayı oluşturur ancak Jinja cazip motoru için Yeşim uzantısını kullanır. |

## <a name="install-project-requirements"></a>Proje gereksinimlerini yükleme

Çerçeveye özgü bir şablondan proje oluştururken, gerekli paketleri pip kullanarak yüklemenize yardımcı olacak bir iletişim kutusu görüntülenir. Ayrıca, web sitenizi yayımladığınızda doğru bağımlılıkların dahil edilmesi için web projeleri için sanal bir [ortam](selecting-a-python-environment-for-a-project.md#use-virtual-environments) kullanmanızı öneririz:

![Proje şablonu için gerekli paketleri yükleyen iletişim kutusu](media/template-web-requirements-txt-wizard.png)

Kaynak denetimi kullanıyorsanız, genellikle sanal ortam klasörünü atlarsınız, çünkü bu ortam yalnızca *requirements.txt*kullanılarak yeniden oluşturulabilir. Klasörü dışlamanın en iyi yolu, önce yukarıda gösterilen komut istemine **kendim yükleyeceğimi** seçmek, ardından sanal ortamı oluşturmadan önce otomatik işlemeyi devre dışı bırakmaktır. Ayrıntılar için, [Bkz. Django Tutorial öğrenin - Adımlar 1-2 ve 1-3](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) ve [Flask Tutorial öğrenin - Adımlar 1-2 ve 1-3](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository).

Microsoft Azure Uygulama Hizmeti'ne dağıtılırken, [site uzantısı](/visualstudio/python/managing-python-on-azure-app-service?view=vs-2019) olarak Python'un bir sürümünü seçin ve paketleri el ile yükleyin. Ayrıca, Azure Uygulama Hizmeti Visual Studio'dan dağıtıldığında *gereksinimleri.txt* dosyasından paketleri otomatik olarak **yüklemediği** için, [aka.ms/PythonOnAppService'daki](managing-python-on-azure-app-service.md)yapılandırma ayrıntılarını izleyin.

Microsoft Azure Bulut *Hizmetleri* *gereksinimleri.txt* dosyasını destekler. Ayrıntılar için [Azure bulut hizmeti projelerine](python-azure-cloud-service-project-template.md) bakın.

## <a name="debugging"></a>Hata ayıklama

Hata ayıklama için bir web projesi başlatıldığında, Visual Studio rasgele bir bağlantı noktasında yerel bir web sunucusu başlatır ve varsayılan tarayıcınızı bu adrese ve bağlantı noktasına açar. Ek seçenekler belirtmek için projeyi sağ tıklatın, **Özellikler'i**seçin ve **Web Başlatıcısı** sekmesini seçin:

![Genel web şablonu için web başlatıcısı özellikleri](media/template-web-launcher-properties.png)

Hata **Ayıklama** grubunda:

- **Arama Yolları**, **Komut Dosyası Bağımsız Değişkenleri**, **Yorumlayıcı Bağımsız Değişkenler**ve **Yorumlayıcı Yolu**: bu seçenekler normal hata [ayıklama](debugging-python-in-visual-studio.md)ile aynıdır.
- **Başlat URL:** tarayıcınızda açılan URL'yi belirtir. Varsayılan olarak `localhost`.
- **Bağlantı Noktası Numarası**: URL'de hiçbiri belirtilmemişse kullanılacak bağlantı noktası (Visual Studio varsayılan olarak otomatik olarak birini seçer). Bu ayar, yerel hata ayıklama `SERVER_PORT` sunucusunun dinlediği bağlantı noktasını yapılandırmak için şablonlar tarafından kullanılan ortam değişkeninin varsayılan değerini geçersiz kılmanızı sağlar.

Run Server **Komutu** ve **Hata Ayıklama Sunucusu Komutu** gruplarından (ikincisi resimde gösterilenin altındadır) özellikleri, web sunucusunun nasıl başlatıldığını belirler. Birçok çerçeve geçerli projenin dışında bir komut dosyası kullanımını gerektirdiğinden, komut dosyası burada yapılandırılabilir ve başlangıç modülünün adı parametre olarak geçirilebilir.

- **Komut**: Python komut dosyası (*\*.py* dosyası), bir `python.exe -m module_name`modül adı (olduğu gibi, `python.exe -c "code"`) veya tek bir kod satırı (olduğu gibi, ) olabilir. Açılan değer, bu türlerden hangisinin amaçlandığını gösterir.
- **Bağımsız değişkenler**: bu bağımsız değişkenler komutu izleyen komut satırına aktarılır.
- **Çevre**: NAME>= \<\<ÇEVRE değişkenlerini belirten> çiftleri yeni bir satır ayrılmış listesi. Bu değişkenler, bağlantı noktası numarası ve arama yolları gibi ortamı değiştirebilecek tüm özelliklerden sonra ayarlanır ve bu nedenle bu değerlerin üzerine yazılabilir.

Herhangi bir proje özelliği veya ortam değişkeni MSBuild `$(StartupFile) --port $(SERVER_PORT)`sözdizimi ile belirtilebilir, örneğin: .
`$(StartupFile)`başlangıç dosyasına göreli yoldur ve `{StartupModule}` başlangıç dosyasının içe aktarılabilir adıdır. `$(SERVER_HOST)`ve `$(SERVER_PORT)` **Başlat URL'si** ve **Bağlantı Noktası Numarası** özellikleri tarafından otomatik olarak veya **Çevre** özelliği tarafından ayarlanan normal ortam değişkenleridir.

> [!Note]
> Run **Server** Komutu'ndaki değerler **Hata Ayıklama** > **Başlangıç Sunucusu** komutu veya **Ctrl**+**F5**ile kullanılır; **Hata Ayıklama Sunucusu Komutu** grubundaki değerler **Hata** > **Ayıklama Başlat Hata Ayıklama Sunucusu** komutu veya **F5**ile kullanılır.

### <a name="sample-bottle-configuration"></a>Örnek Şişe yapılandırması

**Şişe Web Projesi** şablonu, gerekli yapılandırmayı yapan ortak kod içerir. İçe aktarılan şişe uygulaması bu kodu içermeyebilir, ancak bu durumda aşağıdaki `bottle` ayarlar uygulamayı yüklü modülü kullanarak başlatabilir:

- **Sunucu Komutgrubunu çalıştır:**
  - **Komut** `bottle` : (modül)
  - **Bağımsız değişkenler**:`--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- **Hata Ayıklama Sunucu Komutu** grubu:
  - **Komut** `bottle` : (modül)
  - **Bağımsız değişkenler**`--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

Hata `--reload` ayıklama için Visual Studio'yu kullanırken bu seçenek önerilmez.

### <a name="sample-pyramid-configuration"></a>Örnek Piramit yapılandırması

Piramit uygulamaları şu anda `pcreate` en iyi komut satırı aracı kullanılarak oluşturulur. Bir uygulama oluşturulduktan sonra, [**Varolan Python kodu şablonundan**](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) alınarak içe aktarılabilir. Bunu yaptıktan sonra, seçenekleri yapılandırmak için **Genel Web Projesi** özelleştirmesini seçin. Bu ayarlar, Piramit'in `..\env`sanal bir ortama yüklenmiş olduğunu varsayıyor.

- **Hata ayıklama** grubu:
  - **Sunucu Bağlantı Noktası**: 6543 (veya *.ini* dosyalarında yapılandırılan her neyse)

- **Sunucu Komutgrubunu çalıştır:**
  - Komut: `..\env\scripts\pserve-script.py` (komut dosyası)
  - Bağımsız değişken:`Production.ini`

- **Hata Ayıklama Sunucu Komutu** grubu:
  - Komut: `..\env\scripts\pserve-script.py` (komut dosyası)
  - Bağımsız değişken:`Development.ini`

> [!Tip]
> Piramit uygulamaları genellikle proje kökünün altında bir klasör olduğundan, büyük olasılıkla projenizin **Çalışma Dizini** özelliğini yapılandırmanız gerekir.

### <a name="other-configurations"></a>Diğer yapılandırmalar

Paylaşmak istediğiniz başka bir çerçeve için ayarlarınız varsa veya başka bir çerçeve için ayarlar istemek istiyorsanız, [GitHub'da](https://github.com/Microsoft/PTVS/issues)bir sorun açın.

## <a name="convert-a-project-to-azure-cloud-service"></a>Projeyi Azure Bulut Hizmetine dönüştürme

**Microsoft Azure Bulut Hizmeti Projesi'ne Dönüştür** komutu (aşağıdaki resim) çözümünüze bir bulut hizmeti projesi ekler. Bu proje, kullanılacak sanal makineler ve hizmetler için dağıtım ayarlarını ve yapılandırmayı içerir. Bulut Hizmetlerine dağıtmak için bulut projesinde **Yayımla** komutunu kullanın; Python projesindeki **Yayımla** komutu hala Web Sitelerine dağıtılır. Daha fazla bilgi için Azure [bulut hizmeti projelerine](python-azure-cloud-service-project-template.md)bakın.

![Microsoft Azure bulut hizmeti proje komutuna dönüştürme](media/template-web-convert-menu.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Python öğe şablonları başvuru](python-item-templates.md)
- [Azure App Service’e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md)
