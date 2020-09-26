---
title: Python için Web uygulaması şablonları
description: Visual Studio, şişe, Flask ve Docgo çerçeveleri kullanarak Python web uygulamalarına yönelik şablonlar sağlar; destek, hata ayıklama konfigürasyonları ve Azure App Service yayımlamayı içerir.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 572e02d614f0c6b5f782d683ff7e42e954b54441
ms.sourcegitcommit: 13cf7569f62c746708a6ced1187d8173eda7397c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352342"
---
# <a name="python-web-application-project-templates"></a>Python web uygulaması proje şablonları

Visual Studio 'da Python, proje şablonları ve çeşitli çerçeveleri işleyecek şekilde yapılandırılabilecek bir hata ayıklama başlatıcısı aracılığıyla şişe, Flask ve Docgo çerçeveleri aracılığıyla web projelerinin geliştirilmesini destekler. Bu şablonlar, gerekli bağımlılıkları bildirmek için bir *requirements.txt* dosyası içerir. Bu şablonlardan birini bir proje oluştururken, Visual Studio bu paketleri yüklemenizi ister (bkz. Bu makalenin ilerleyen kısımlarında [proje gereksinimlerini yükler](#install-project-requirements) ).

Ayrıca, piramit gibi diğer çerçeveler için genel **Web projesi** şablonunu da kullanabilirsiniz. Bu durumda, şablonla birlikte hiçbir çerçeve yüklenmez. Bunun yerine, gerekli paketleri proje için kullanmakta olduğunuz ortama (bkz. [Python ortamları penceresi-paket sekmesi](python-environments-window-tab-reference.md#packages-tab)) yükleyebilirsiniz.

Python web uygulamasını Azure 'a dağıtma hakkında bilgi için bkz. [Azure App Service yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md).

## <a name="use-a-project-template"></a>Proje şablonu kullanma

**Dosya**  >  **Yeni**proje ' ye kullanarak bir şablondan proje oluşturursunuz  >  **Project**. Web projelerine yönelik şablonları görmek için **Python**  >  iletişim kutusunun sol tarafındaki Python**Web** ' i seçin. Ardından seçtiğiniz bir şablonu seçin, proje ve çözüm için adlar sağlayıp bir çözüm dizini ve git deposu için seçenekleri ayarlayın ve **Tamam**' ı seçin.

![Web uygulamaları için yeni proje iletişim kutusu](media/projects-new-project-dialog-web.png)

Daha önce bahsedilen genel **Web projesi** şablonu, kod olmadan yalnızca boş bir Visual Studio projesi ve Python projesi dışında bir varsayımsız bir proje sağlar. **Azure bulut hizmeti** şablonu hakkında daha fazla bilgi için bkz. [Python için Azure bulut hizmeti projeleri](python-azure-cloud-service-project-template.md).

Diğer tüm şablonlar şişe, Flask veya Docgo Web çerçevelerine dayalıdır ve aşağıdaki bölümlerde açıklandığı gibi üç genel gruba girer. Bu şablonlardan herhangi biri tarafından oluşturulan uygulamalar, uygulamayı yerel olarak çalıştırmak ve hata ayıklamak için yeterli kod içerir. Her biri aynı zamanda üretim Web sunucularıyla kullanmak üzere gerekli [wsgi uygulama nesnesini](https://www.python.org/dev/peps/pep-3333/) (Python.org) sağlar.

### <a name="blank-group"></a>Boş Grup

Tüm **boş \<framework> Web projesi** şablonları, daha fazla veya daha az ortak kod içeren bir proje oluşturur ve bir *requirements.txt* dosyasında belirtilen bağımlılıklardır.

| Şablon | Description |
| --- | --- |
| **Boş şişe Web projesi** | , İçin bir giriş sayfası *app.py* `/` ve `/hello/<name>` `<name>` çok kısa bir satır içi sayfa şablonu kullanarak yankı sağlayan bir sayfa olan App.py içinde en az bir uygulama oluşturur. |
| **Boş Docgo Web projesi** | Core Docgo site yapısıyla bir Docgo projesi oluşturur, ancak Docgo uygulaması yoktur. Daha fazla bilgi için bkz. [docgo şablonları](python-django-web-application-project-template.md) ve [docgo 1. adımı öğrenme](learn-django-in-visual-studio-step-01-project-and-solution.md). |
| **Boş Flask Web projesi** | Tek bir "Merhaba Dünya!" ile en az bir uygulama üretir sayfası `/` . Bu uygulama, [hızlı başlangıç: Ilk Python web uygulamanızı oluşturmak Için Visual Studio 'Yu kullanma](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)sonucuna benzer. Ayrıca bkz. [Flask adımını öğrenin 1](learn-flask-visual-studio-step-01-project-solution.md).

### <a name="web-group"></a>Web grubu

Tüm ** \<Framework> Web projesi** şablonları, seçilen çerçeveye bakılmaksızın özdeş tasarıma sahip bir başlatıcı Web uygulaması oluşturur. Uygulamanın ana, hakkında ve Iletişim sayfaları, bir gezinti çubuğu ve önyükleme ile hızlı bir şekilde tasarım vardır. Her uygulama statik dosyaları (CSS, JavaScript ve yazı tipleri) sunacak şekilde yapılandırılır ve çerçeveye uygun bir sayfa şablonu mekanizması kullanır.

| Şablon | Description |
| --- | --- |
| **Şişe Web projesi** | Statik dosyaları *statik* klasörde bulunan ve *app.py*içindeki kodla işlenen bir uygulama oluşturur. Ayrı sayfalar için yönlendirme *Routes.py*içinde bulunur ve *Görünümler* klasörü sayfa şablonlarını içerir.|
| **Docgo Web projesi** | Üç sayfa, kimlik doğrulama desteği ve bir SQLite veritabanı (ancak veri modeli olmadan) ile bir Docgo projesi ve Docgo uygulaması oluşturur. Daha fazla bilgi için bkz. [docgo şablonları](python-django-web-application-project-template.md) ve [Docgo adım 4](learn-django-in-visual-studio-step-04-full-django-project-template.md). |
| **Flask Web projesi** | *Statik klasörde bulunan* statik dosyaları içeren bir uygulama oluşturur. *Views.py* sürümündeki kod, *Şablonlar* klasöründe bulunan jınja altyapısını kullanan sayfa şablonlarıyla yönlendirme gerçekleştirir. *Runserver.py* dosyası başlangıç kodu sağlar. Bkz. [Flask adımını öğrenme 4](learn-flask-visual-studio-step-04-full-flask-project-template.md). |
| **Flask/Jade Web projesi** | **Flask Web projesi** şablonuyla aynı uygulamayı, ancak Jınja şablon oluşturma altyapısı Için Jade uzantısını kullanarak oluşturur. |

### <a name="polls-group"></a>Grubu yoklamalar

** \<framework> Web projesi şablonlarının yokladığı** , kullanıcıların farklı yoklama sorularını oylayabilir bir başlatıcı Web uygulaması oluşturur. Her uygulama, yoklamaları ve kullanıcı yanıtlarını yönetmek üzere bir veritabanı kullanmak için **Web** projesi şablonlarının yapısını oluşturur. Uygulamalar, uygun veri modellerini ve dosyadaki *samples.js* yoklamaları yükleyen özel bir uygulama sayfasını (/Seed) içerir.

| Şablon | Description |
| --- | --- |
| **Şişe Web projesini yoklar** | Ortam değişkeni kullanılarak yapılandırılan bir bellek içi veritabanı, MongoDB veya Azure Tablo depolama için çalışabilen bir uygulama oluşturur `REPOSITORY_NAME` . Veri modelleri ve veri deposu kodu *modeller* klasöründe bulunur ve *Settings.py* dosyası, hangi veri deposunun kullanıldığını belirleyen kodu içerir. |
| **Docgo Web projesini yoklar** | Üç sayfa ve bir SQLite veritabanı ile Docgo projesi ve Docgo uygulaması oluşturur. Kimliği doğrulanmış bir yöneticinin yoklamaları oluşturmasına ve yönetmesine izin vermek için Docgo yönetim arabirimine özelleştirmeler içerir. Daha fazla bilgi için bkz. [docgo şablonları](python-django-web-application-project-template.md) ve [docgo 6. adımı öğrenin](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md). |
| **Flask Web projesini yoklar** | Ortam değişkeni kullanılarak yapılandırılan bir bellek içi veritabanı, MongoDB veya Azure Tablo depolama için çalışabilen bir uygulama oluşturur `REPOSITORY_NAME` . Veri modelleri ve veri deposu kodu *modeller* klasöründe bulunur ve *Settings.py* dosyası, hangi veri deposunun kullanıldığını belirleyen kodu içerir. Uygulama, sayfa şablonları için Jınja altyapısını kullanır. Bkz. [Flask adım 5](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)' i öğrenin. |
| **Flask/Jade Web projesini yoklar** | , **Flask Web projesi şablonu yoklayıp** aynı uygulamayı oluşturur, ancak Jınja şablon oluşturma altyapısı Için Jade uzantısını kullanarak. |

## <a name="install-project-requirements"></a>Proje gereksinimlerini yükler

Çerçeveye özgü bir şablondan bir proje oluştururken, gerekli paketleri PIP kullanarak yüklemenize yardımcı olacak bir iletişim kutusu görünür. Ayrıca, Web sitenizi yayımladığınızda doğru bağımlılıkların dahil edilmesini sağlamak üzere Web projeleri için [sanal bir ortam](selecting-a-python-environment-for-a-project.md#use-virtual-environments) kullanmanızı öneririz:

![Bir proje şablonu için gerekli paketleri yükleyen iletişim kutusu](media/template-web-requirements-txt-wizard.png)

Kaynak denetimi kullanıyorsanız, genellikle bu ortam yalnızca *requirements.txt*kullanılarak yeniden oluşturulabilen sanal ortam klasörünü atlayabilirsiniz. Klasörü hariç tutmak için en iyi yol, yukarıda gösterilen istem içine **kendim yükleyeceğim** , sonra sanal ortam oluşturmadan önce otomatik yürütmeyi devre dışı bırakacağım. Ayrıntılar için bkz. [Docgo öğreticisini öğrenme-adım 1-2 ve 1-3](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) ve [Flask öğreticisini öğrenme-adımlar 1-2 ve 1-3](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository).

Microsoft Azure App Service ' ye dağıtım yaparken, bir Python sürümünü [site uzantısı](./managing-python-on-azure-app-service.md?view=vs-2019&preserve-view=true) olarak seçin ve paketleri el ile yükleyebilirsiniz. Ayrıca, Azure App Service Visual Studio 'dan dağıtıldığında *requirements.txt* bir dosyadan **paketleri otomatik olarak yüklemediğinden** , [aka.MS/PythonOnAppService](managing-python-on-azure-app-service.md)adresindeki yapılandırma ayrıntılarını izleyin.

Microsoft Azure Cloud Services *does* *requirements.txt* dosyasını destekler. Ayrıntılar için bkz. [Azure Cloud Service Projects](python-azure-cloud-service-project-template.md) .

## <a name="debugging"></a>Hata Ayıklama

Bir Web projesi hata ayıklama için başlatıldığında, Visual Studio rastgele bir bağlantı noktasında yerel bir Web sunucusu başlatır ve varsayılan tarayıcınızı bu adrese ve bağlantı noktasına açar. Ek seçenekleri belirtmek için projeye sağ tıklayın, **Özellikler**' i seçin ve **Web başlatıcısı** sekmesini seçin:

![Genel Web şablonu için Web başlatıcısı özellikleri](media/template-web-launcher-properties.png)

**Hata ayıklama** grubunda:

- **Arama yolları**, **betik bağımsız değişkenleri**, **yorumlayıcı bağımsız değişkenleri**ve **yorumlayıcı yolu**: Bu seçenekler, [normal hata ayıklama](debugging-python-in-visual-studio.md)ile aynıdır.
- **Başlatma URL 'si**: tarayıcınızda açılan URL 'yi belirtir. Varsayılan olarak olur `localhost` .
- **Bağlantı noktası numarası**: URL 'de hiçbiri belirtilmemişse kullanılacak bağlantı noktası (Visual Studio varsayılan olarak bir otomatik olarak seçilir). Bu ayar, `SERVER_PORT` yerel hata ayıklama sunucusunun dinlediği bağlantı noktasını yapılandırmak için şablonlar tarafından kullanılan ortam değişkeninin varsayılan değerini geçersiz kılmanıza olanak sağlar.

**Sunucu Çalıştır komutundaki** Özellikler ve **hata ayıklama sunucusu komut** grupları (ikinci olarak, görüntüde gösterilmekte olan), Web sunucusunun nasıl başlatılmadığını belirlemek için kullanılır. Birçok çerçeve geçerli proje dışında bir komut dosyası kullanımını gerektirdiğinden, betik burada yapılandırılabilir ve başlangıç modülünün adı bir parametre olarak geçirilebilir.

- **Komut**: bir Python betiği (* \* . köpek* dosyası), bir modül adı (içinde olduğu gibi) `python.exe -m module_name` veya tek satırlık kod (içinde olduğu gibi `python.exe -c "code"` ) olabilir. Açılan kutuda bulunan değer bu türlerden hangisinin hedeflendiğini gösterir.
- **Bağımsız değişkenler**: Bu bağımsız değişkenler komutundan sonra komut satırına geçirilir.
- **Ortam**: \<NAME> = \<VALUE> ortam değişkenlerini belirten bir çift satır ayrılmış listesi. Bu değişkenler, bağlantı noktası numarası ve arama yolları gibi ortamı değiştirebilen tüm özelliklerden sonra ayarlanır ve bu değerlerin üzerine yazabilir.

Herhangi bir proje özelliği veya ortam değişkeni MSBuild sözdizimi ile belirtilebilir, örneğin: `$(StartupFile) --port $(SERVER_PORT)` .
`$(StartupFile)` , başlangıç dosyasının göreli yoludur ve `{StartupModule}` Başlangıç dosyasının Importable adıdır. `$(SERVER_HOST)` ve, `$(SERVER_PORT)` **başlatma URL 'Si** ve **bağlantı noktası numarası** özellikleri tarafından, otomatik olarak veya **ortam** özelliği tarafından ayarlanan normal ortam değişkenleridir.

> [!Note]
> **Run Server komutunda** bulunan değerler **hata ayıklama**  >  **başlatma sunucusu** komutu veya **CTRL** + **F5**ile birlikte kullanılır; **hata ayıklama sunucusu komut** grubundaki değerler **Hata Ayıkla**  >  **Start Debug Server** komutuyla veya **F5**ile kullanılır.

### <a name="sample-bottle-configuration"></a>Örnek şişe yapılandırması

**Şişe Web projesi** şablonu, gerekli yapılandırmayı yapan ortak kod içerir. İçeri aktarılan bir şişe uygulaması bu kodu içermeyebilir, ancak bu durumda aşağıdaki ayarlar uygulamayı yüklü modülünü kullanarak başlatır `bottle` :

- **Sunucu komut grubunu Çalıştır** :
  - **Komut**: `bottle` (modül)
  - **Bağımsız değişkenler**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- **Hata ayıklama sunucusu komut** grubu:
  - **Komut**: `bottle` (modül)
  - **Arguments** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

`--reload`Hata ayıklama Için Visual Studio kullanılırken bu seçenek önerilmez.

### <a name="sample-pyramid-configuration"></a>Örnek piramit yapılandırması

Piramit uygulamalar şu anda en iyi `pcreate` komut satırı aracı kullanılarak oluşturulmuştur. Bir uygulama oluşturulduktan sonra, [**mevcut Python kod**](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) şablonundan kullanılarak içeri aktarılabilir. Bunu yaptıktan sonra, seçenekleri yapılandırmak için **Genel Web projesi** özelleştirmesini seçin. Bu ayarlar, piramit 'in konumundaki bir sanal ortama yüklendiğini varsayar `..\env` .

- **Hata ayıklama** grubu:
  - **Sunucu bağlantı noktası**: 6543 (veya *. ini* dosyalarında yapılandırılmış herhangi bir şey)

- **Sunucu komut grubunu Çalıştır** :
  - Komut: `..\env\scripts\pserve-script.py` (betik)
  - Değişkenlerinden `Production.ini`

- **Hata ayıklama sunucusu komut** grubu:
  - Komut: `..\env\scripts\pserve-script.py` (betik)
  - Değişkenlerinden `Development.ini`

> [!Tip]
> Piramit, genellikle proje kökünün altındaki bir klasör olduğundan projenizin **çalışma dizini** özelliğini yapılandırmanız gerekir.

### <a name="other-configurations"></a>Diğer yapılandırma

Paylaşmak istediğiniz başka bir çerçeve için ayarlarınız varsa veya başka bir Framework için ayarları istemek istiyorsanız [GitHub 'da bir sorun](https://github.com/Microsoft/PTVS/issues)açın.

## <a name="convert-a-project-to-azure-cloud-service"></a>Projeyi Azure bulut hizmeti 'ne Dönüştür

**Microsoft Azure Cloud Service projesi komutuna Dönüştür** komutu (aşağıdaki görüntü) çözümünüze bir bulut hizmeti projesi ekler. Bu proje, kullanılacak sanal makinelerin ve hizmetlerin dağıtım ayarlarını ve yapılandırmasını içerir. Cloud Services dağıtmak için bulut projesindeki **Yayımla** komutunu kullanın; Python projesindeki **Yayımla** komutu hala Web sitelerine dağıtılır. Daha fazla bilgi için bkz. [Azure bulut hizmeti projeleri](python-azure-cloud-service-project-template.md).

![Microsoft Azure bulut hizmeti projesi komutuna Dönüştür](media/template-web-convert-menu.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Python öğe şablonları başvurusu](python-item-templates.md)
- [Azure App Service’e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md)