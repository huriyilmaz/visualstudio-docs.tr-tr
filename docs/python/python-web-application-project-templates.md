---
title: Python için Web uygulaması şablonları
description: Visual Studio, şişe, flask ve docgo çerçeveleri kullanarak Python web uygulamalarına yönelik şablonlar sağlar; destek, hata ayıklama konfigürasyonları ve Azure App Service yayımlamayı içerir.
ms.date: 01/28/2019
ms.topic: conceptual
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 56a9f0bc78d942d34ce0a2aadfd9f7a59becd7c8
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972914"
---
# <a name="python-web-application-project-templates"></a>Python web uygulaması proje şablonları

Visual Studio Python, proje şablonları ve çeşitli çerçeveleri işlemek üzere yapılandırılabilecek bir hata ayıklama başlatıcısı aracılığıyla şişe, flask ve docgo çerçeveleri aracılığıyla web projelerinin geliştirilmesini destekler. Bu şablonlar, gerekli bağımlılıkları bildirmek için bir *requirements.txt* dosyası içerir. bu şablonlardan birini bir proje oluştururken, Visual Studio bu paketleri yüklemenizi ister (bkz. bu makalenin sonraki kısımlarında [proje gereksinimlerini yükler](#install-project-requirements) ).

ayrıca, piramit gibi diğer çerçeveler için genel **Web Project** şablonunu da kullanabilirsiniz. Bu durumda, şablonla birlikte hiçbir çerçeve yüklenmez. Bunun yerine, gerekli paketleri proje için kullanmakta olduğunuz ortama (bkz. [Python ortamları penceresi-paket sekmesi](python-environments-window-tab-reference.md#packages-tab)) yükleyebilirsiniz.

Python web uygulamasını Azure 'a dağıtma hakkında bilgi için bkz. [Azure App Service yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md).

## <a name="use-a-project-template"></a>Proje şablonu kullanma

  >  **yeni**  >  **Project** dosya kullanarak bir şablondan proje oluşturursunuz. Web projelerine yönelik şablonları görmek için   >  iletişim kutusunun sol tarafındaki Python **Web** ' i seçin. Ardından seçtiğiniz bir şablonu seçin, proje ve çözüm için adlar sağlayıp bir çözüm dizini ve git deposu için seçenekleri ayarlayın ve **Tamam**' ı seçin.

![Web uygulamaları için yeni proje iletişim kutusu](media/projects-new-project-dialog-web.png)

::: moniker range="<=vs-2017"

daha önce bahsedilen genel **Web Project** şablonu, kod olmadan yalnızca boş bir Visual Studio projesi ve Python projesi dışında hiçbir varsayımsız bir proje sağlar.

::: moniker-end

::: moniker range=">=vs-2019"

daha önce bahsedilen genel **Web Project** şablonu, kod olmadan yalnızca boş bir Visual Studio projesi ve Python projesi dışında hiçbir varsayımsız bir proje sağlar.

::: moniker-end

Diğer tüm şablonlar şişe, Flask veya Docgo Web çerçevelerine dayalıdır ve aşağıdaki bölümlerde açıklandığı gibi üç genel gruba girer. Bu şablonlardan herhangi biri tarafından oluşturulan uygulamalar, uygulamayı yerel olarak çalıştırmak ve hata ayıklamak için yeterli kod içerir. Her biri aynı zamanda üretim Web sunucularıyla kullanmak üzere gerekli [wsgi uygulama nesnesini](https://www.python.org/dev/peps/pep-3333/) (Python.org) sağlar.

### <a name="blank-group"></a>Boş Grup

tüm **boş \<framework> Web Project** şablonları, daha fazla veya daha az ortak kod içeren bir proje oluşturur ve bir *requirements.txt* dosyasında belirtilen bağımlılıklardır.

| Şablon | Description |
| --- | --- |
| **Boş şişe Web Project** | , İçin bir giriş sayfası  `/` ve `/hello/<name>` `<name>` çok kısa bir satır içi sayfa şablonu kullanarak yankı sağlayan bir sayfa olan App.py içinde en az bir uygulama oluşturur. |
| **Boş Docgo Web Project** | Core Docgo site yapısıyla bir Docgo projesi oluşturur, ancak Docgo uygulaması yoktur. Daha fazla bilgi için bkz. [docgo şablonları](python-django-web-application-project-template.md) ve [docgo 1. adımı öğrenme](learn-django-in-visual-studio-step-01-project-and-solution.md). |
| **Boş Flask Web Project** | Tek bir "Merhaba Dünya!" ile en az bir uygulama üretir sayfası `/` . bu uygulama, [hızlı başlangıç: ilk Python web uygulamanızı oluşturmak için Visual Studio kullanma](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)sonucuna benzer. Ayrıca bkz. [Flask adımını öğrenin 1](learn-flask-visual-studio-step-01-project-solution.md).

### <a name="web-group"></a>Web grubu

tüm **\<Framework> Web Project** şablonları, seçilen çerçeveden bağımsız olarak aynı tasarıma sahip bir başlatıcı Web uygulaması oluşturur. Uygulamanın ana, hakkında ve Iletişim sayfaları, bir gezinti çubuğu ve önyükleme ile hızlı bir şekilde tasarım vardır. Her uygulama statik dosyaları (CSS, JavaScript ve yazı tipleri) sunacak şekilde yapılandırılır ve çerçeveye uygun bir sayfa şablonu mekanizması kullanır.

| Şablon | Description |
| --- | --- |
| **Şişe Web Project** | Statik dosyaları *statik* klasörde bulunan ve *app.py* içindeki kodla işlenen bir uygulama oluşturur. Ayrı sayfalar için yönlendirme *Routes.py* içinde bulunur ve *Görünümler* klasörü sayfa şablonlarını içerir.|
| **Docgo Web Project** | Üç sayfa, kimlik doğrulama desteği ve bir SQLite veritabanı (ancak veri modeli olmadan) ile bir Docgo projesi ve Docgo uygulaması oluşturur. Daha fazla bilgi için bkz. [docgo şablonları](python-django-web-application-project-template.md) ve [Docgo adım 4](learn-django-in-visual-studio-step-04-full-django-project-template.md). |
| **Flask Web Project** | *Statik klasörde bulunan* statik dosyaları içeren bir uygulama oluşturur. *Views.py* sürümündeki kod, *Şablonlar* klasöründe bulunan jınja altyapısını kullanan sayfa şablonlarıyla yönlendirme gerçekleştirir. *Runserver.py* dosyası başlangıç kodu sağlar. Bkz. 

::: moniker range="vs-2017"
### <a name="polls-group"></a>Grubu yoklamalar

**yoklamaları \<framework> web Project** şablonları, kullanıcıların farklı yoklama sorularını oylayabilir bir başlatıcı web uygulaması oluşturur. Her uygulama, yoklamaları ve kullanıcı yanıtlarını yönetmek üzere bir veritabanı kullanmak için **Web** projesi şablonlarının yapısını oluşturur. Uygulamalar, bir *Samples. JSON* dosyasından yoklamaları yükleyen uygun veri modellerini ve özel bir uygulama sayfasını (/Seed) içerir.

| Şablon | Description |
| --- | --- |
| **Şişe Web Project yoklar** | ortam değişkeni kullanılarak yapılandırılan, bellek içi veritabanı, mongodb veya Azure tablo Depolama karşı çalışabilen bir uygulama oluşturur `REPOSITORY_NAME` . Veri modelleri ve veri deposu kodu *modeller* klasöründe bulunur ve *Settings.py* dosyası, hangi veri deposunun kullanıldığını belirleyen kodu içerir. |
| **Docgo Web Project yoklar** | Üç sayfa ve bir SQLite veritabanı ile Docgo projesi ve Docgo uygulaması oluşturur. Kimliği doğrulanmış bir yöneticinin yoklamaları oluşturmasına ve yönetmesine izin vermek için Docgo yönetim arabirimine özelleştirmeler içerir. Daha fazla bilgi için bkz. [docgo şablonları](python-django-web-application-project-template.md) ve [docgo 6. adımı öğrenin](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md). |
| **Flask/Jade Web Project yoklar** | , **flask Web Project** şablonuyla aynı uygulamayı ve jınja şablon oluşturma altyapısı için jade uzantısını kullanarak oluşturur. |
::: moniker-end

## <a name="install-project-requirements"></a>Proje gereksinimlerini yükler

Çerçeveye özgü bir şablondan bir proje oluştururken, gerekli paketleri PIP kullanarak yüklemenize yardımcı olacak bir iletişim kutusu görünür. Ayrıca, Web sitenizi yayımladığınızda doğru bağımlılıkların dahil edilmesini sağlamak üzere Web projeleri için [sanal bir ortam](selecting-a-python-environment-for-a-project.md#use-virtual-environments) kullanmanızı öneririz:

![Bir proje şablonu için gerekli paketleri yükleyen iletişim kutusu](media/template-web-requirements-txt-wizard.png)

Kaynak denetimi kullanıyorsanız, genellikle bu ortam yalnızca *requirements.txt* kullanılarak yeniden oluşturulabilen sanal ortam klasörünü atlayabilirsiniz. Klasörü hariç tutmak için en iyi yol, yukarıda gösterilen istem içine **kendim yükleyeceğim** , sonra sanal ortam oluşturmadan önce otomatik yürütmeyi devre dışı bırakacağım. Ayrıntılar için bkz. [Docgo öğreticisini öğrenme-adım 1-2 ve 1-3](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) ve [Flask öğreticisini öğrenme-adımlar 1-2 ve 1-3](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository).

Microsoft Azure App Service ' ye dağıtım yaparken, bir Python sürümünü [site uzantısı](./managing-python-on-azure-app-service.md?view=vs-2019&preserve-view=true) olarak seçin ve paketleri el ile yükleyebilirsiniz. ayrıca Azure App Service, paketi Visual Studio dağıtıldığında *requirements.txt* bir **dosyadan otomatik olarak yüklemediğinden** , [aka.ms/PythonOnAppService](managing-python-on-azure-app-service.md)adresindeki yapılandırma ayrıntılarını izleyin.

## <a name="debugging"></a>Hata Ayıklama

bir web projesi hata ayıklama için başlatıldığında, Visual Studio rastgele bir bağlantı noktasında yerel bir web sunucusu başlatır ve varsayılan tarayıcınızı bu adrese ve bağlantı noktasına açar. Ek seçenekleri belirtmek için projeye sağ tıklayın, **Özellikler**' i seçin ve **Web başlatıcısı** sekmesini seçin:

![Genel Web şablonu için Web başlatıcısı özellikleri](media/template-web-launcher-properties.png)

**Hata ayıklama** grubunda:

- **Arama yolları**, **betik bağımsız değişkenleri**, **yorumlayıcı bağımsız değişkenleri** ve **yorumlayıcı yolu**: Bu seçenekler, [normal hata ayıklama](debugging-python-in-visual-studio.md)ile aynıdır.
- **Başlatma URL 'si**: tarayıcınızda açılan URL 'yi belirtir. Varsayılan olarak olur `localhost` .
- **bağlantı noktası numarası**: URL 'de hiçbiri belirtilmemişse kullanılacak bağlantı noktası (Visual Studio varsayılan olarak bir otomatik olarak seçilir). Bu ayar, `SERVER_PORT` yerel hata ayıklama sunucusunun dinlediği bağlantı noktasını yapılandırmak için şablonlar tarafından kullanılan ortam değişkeninin varsayılan değerini geçersiz kılmanıza olanak sağlar.

**Sunucu Çalıştır komutundaki** Özellikler ve **hata ayıklama sunucusu komut** grupları (ikinci olarak, görüntüde gösterilmekte olan), Web sunucusunun nasıl başlatılmadığını belirlemek için kullanılır. Birçok çerçeve geçerli proje dışında bir komut dosyası kullanımını gerektirdiğinden, betik burada yapılandırılabilir ve başlangıç modülünün adı bir parametre olarak geçirilebilir.

- **Komut**: bir Python betiği (*\* . köpek* dosyası), bir modül adı (içinde olduğu gibi) `python.exe -m module_name` veya tek satırlık kod (içinde olduğu gibi `python.exe -c "code"` ) olabilir. Açılan kutuda bulunan değer bu türlerden hangisinin hedeflendiğini gösterir.
- **Bağımsız değişkenler**: Bu bağımsız değişkenler komutundan sonra komut satırına geçirilir.
- **Ortam**: \<NAME> = \<VALUE> ortam değişkenlerini belirten bir çift satır ayrılmış listesi. Bu değişkenler, bağlantı noktası numarası ve arama yolları gibi ortamı değiştirebilen tüm özelliklerden sonra ayarlanır ve bu değerlerin üzerine yazabilir.

herhangi bir proje özelliği veya ortam değişkeni MSBuild sözdizimiyle belirtilebilir, örneğin: `$(StartupFile) --port $(SERVER_PORT)` .
`$(StartupFile)` , başlangıç dosyasının göreli yoludur ve `{StartupModule}` Başlangıç dosyasının Importable adıdır. `$(SERVER_HOST)` ve, `$(SERVER_PORT)` **başlatma URL 'Si** ve **bağlantı noktası numarası** özellikleri tarafından, otomatik olarak veya **ortam** özelliği tarafından ayarlanan normal ortam değişkenleridir.

> [!Note]
> **Run Server komutunda** bulunan değerler **hata ayıklama**  >  **başlatma sunucusu** komutu veya **CTRL** + **F5** ile birlikte kullanılır; **hata ayıklama sunucusu komut** grubundaki değerler **Hata Ayıkla**  >  **Start Debug Server** komutuyla veya **F5** ile kullanılır.

### <a name="sample-bottle-configuration"></a>Örnek şişe yapılandırması

**şişe Web Project** şablonu, gerekli yapılandırmayı yapan ortak kod içerir. İçeri aktarılan bir şişe uygulaması bu kodu içermeyebilir, ancak bu durumda aşağıdaki ayarlar uygulamayı yüklü modülünü kullanarak başlatır `bottle` :

- **Sunucu komut grubunu Çalıştır** :
  - **Komut**: `bottle` (modül)
  - **Bağımsız değişkenler**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- **Hata ayıklama sunucusu komut** grubu:
  - **Komut**: `bottle` (modül)
  - **Bağımsız değişkenler** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

`--reload`hata ayıklama için Visual Studio kullanılırken seçenek önerilmez.

### <a name="sample-pyramid-configuration"></a>Örnek piramit yapılandırması

Piramit uygulamalar şu anda en iyi `pcreate` komut satırı aracı kullanılarak oluşturulmuştur. Bir uygulama oluşturulduktan sonra, [**mevcut Python kod**](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) şablonundan kullanılarak içeri aktarılabilir. bunu yaptıktan sonra, seçenekleri yapılandırmak için **genel Web Project** özelleştirmesini seçin. Bu ayarlar, piramit 'in konumundaki bir sanal ortama yüklendiğini varsayar `..\env` .

- **Hata ayıklama** grubu:
  - **Sunucu bağlantı noktası**: 6543 (veya *.ini* dosyalarında yapılandırılmış herhangi bir şey)

- **Sunucu komut grubunu Çalıştır** :
  - Komut: `..\env\scripts\pserve-script.py` (betik)
  - Değişkenlerinden `Production.ini`

- **Hata ayıklama sunucusu komut** grubu:
  - Komut: `..\env\scripts\pserve-script.py` (betik)
  - Değişkenlerinden `Development.ini`

> [!Tip]
> Piramit, genellikle proje kökünün altındaki bir klasör olduğundan projenizin **çalışma dizini** özelliğini yapılandırmanız gerekir.

### <a name="other-configurations"></a>Diğer yapılandırma

Paylaşmak istediğiniz başka bir çerçeve için ayarlarınız varsa veya başka bir Framework için ayarları istemek istiyorsanız [GitHub bir sorun](https://github.com/Microsoft/PTVS/issues)açın.


## <a name="see-also"></a>Ayrıca bkz.

- [Python öğe şablonları başvurusu](python-item-templates.md)
- [Azure App Service’e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md)