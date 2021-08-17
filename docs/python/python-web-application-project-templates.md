---
title: Python için web uygulaması şablonları
description: Visual Studio Bottle, Flask ve Django çerçevelerini kullanarak Python web uygulamaları için şablonlar sağlar; destek, hata ayıklama yapılandırmalarını ve Azure App Service.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 203a9481ed6a8d78784335420a3eceb641f29250c8f789c25e60cbb9d8d65c53
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121230072"
---
# <a name="python-web-application-project-templates"></a>Python web uygulaması proje şablonları

Visual Studio python, proje şablonları ve çeşitli çerçeveleri işlemek üzere yapılandırılan bir hata ayıklama başlatıcısı aracılığıyla Bottle, Flask ve Django çerçevelerinde web projeleri geliştirmeyi destekler. Bu şablonlar, gerekli *requirements.txt* için bir dosya içerir. Bu şablonlardan birini kullanarak proje oluştururken, Visual Studio paketleri yüklemeniz istenir (bu makalenin devamlarında proje [gereksinimlerini](#install-project-requirements) yükleme makalesine bakın).

Ayrıca, Pirami gibi diğer **çerçeveler Project** genel Web Uygulaması şablonunu da kullanabilirsiniz. Bu durumda, şablonla birlikte hiçbir çerçeve yüklenmez. Bunun yerine, proje için kullanmakta olduğunu ortama gerekli paketleri yükleyin [(bkz. Python ortamları penceresi - Paket sekmesi).](python-environments-window-tab-reference.md#packages-tab)

Python web uygulamasını Azure'a dağıtma hakkında daha fazla bilgi için [bkz.](publishing-python-web-applications-to-azure-from-visual-studio.md)Azure App Service.

## <a name="use-a-project-template"></a>Proje şablonu kullanma

Dosya Yeni Dosyası'Project   >  kullanarak  >  **şablondan proje Project.** Web projelerine yönelik şablonları görmek için iletişim kutusunun sol tarafındaki **Python**  >  **Web'i** seçin. Ardından proje ve çözüm için adlar sağlayarak istediğiniz şablonu seçin, çözüm dizini ve Git deposu için seçenekler belirleyin ve Tamam'ı **seçin.**

![Web uygulamaları için yeni proje iletişim kutusu](media/projects-new-project-dialog-web.png)

::: moniker range="<=vs-2017"

Daha önce Project genel **Web** Uygulaması şablonu, kod olmayan ve Python projesi Visual Studio varsayımları olmayan boş bir Visual Studio projesi sağlar.

::: moniker-end

::: moniker range=">=vs-2019"

Daha önce Project genel **Web** Uygulaması şablonu, kod olmayan ve Python projesi Visual Studio varsayımları olmayan boş bir Visual Studio projesi sağlar.

::: moniker-end

Diğer tüm şablonlar Bottle, Flask veya Django web çerçevelerini temel almaktadır ve aşağıdaki bölümlerde açıklandığı gibi üç genel gruba ayrılır. Bu şablonlardan herhangi biri tarafından oluşturulan uygulamalar, uygulamayı yerel olarak çalıştırmak ve hata ayıklamak için yeterli kod içerir. Her biri ayrıca üretim web [sunucularıyla kullanmak için gerekli WSGI](https://www.python.org/dev/peps/pep-3333/) python.org nesnesini (python.org) sağlar.

### <a name="blank-group"></a>Boş grup

Tüm **Boş \<framework> Web Project** şablonları, az veya çok az ortak kodla ve birrequirements.txtdosyasında bildirilen gerekli *bağımlılıklarla bir proje* oluşturur.

| Şablon | Açıklama |
| --- | --- |
| **Boş Bottle Web Project** | çok kısa bir satır *içi app.py* kullanarak bir giriş sayfası ve yankı oluşturan bir sayfa ile birlikte, çok küçük bir `/` uygulama `/hello/<name>` `<name>` oluşturur. |
| **Boş Django Web Project** | Temel Django site yapısına sahip ancak Django uygulamasına sahip bir Django projesi oluşturmaz. Daha fazla bilgi için [bkz. Django şablonları ve](python-django-web-application-project-template.md) [Learn Django 1. Adım.](learn-django-in-visual-studio-step-01-project-and-solution.md) |
| **Boş Flask Web Project** | Tek bir "Merhaba Dünya!" sayfası. `/` Bu uygulama, Hızlı Başlangıç: İlk Python web Visual Studio oluşturmak için Visual Studio [adımlarını izlemenin sonuçlarına benzer.](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) Ayrıca [bkz. Flask'i Öğrenme 1. Adım.](learn-flask-visual-studio-step-01-project-solution.md)

### <a name="web-group"></a>Web grubu

Tüm **\<Framework> Web Project** şablonları, seçilen çerçeveden bağımsız olarak aynı tasarıma sahip bir başlangıç web uygulaması oluşturur. Uygulamada Giriş, Hakkında ve Kişi sayfalarının yanı sıra Bootstrap kullanan bir gezinti çubuğu ve duyarlı tasarım vardır. Her uygulama statik dosyaları (CSS, JavaScript ve yazı tipleri) hizmet edecek şekilde uygun şekilde yapılandırılır ve çerçeve için uygun bir sayfa şablonu mekanizması kullanır.

| Şablon | Açıklama |
| --- | --- |
| **Bottle Web Project** | Statik dosyaları statik klasörde yer alan  ve dosya klasöründeki kod aracılığıyla *app.py.* Tek tek sayfaların yönlendirmesi routes.py *ve* *görünümler* klasörü sayfa şablonlarını içerir.|
| **Django Web Project** | Bir Django projesi ve üç sayfalık bir Django uygulaması, kimlik doğrulama desteği ve bir SQLite veritabanı (veri modeli yok) oluşturur. Daha fazla bilgi için [bkz. Django şablonları ve](python-django-web-application-project-template.md) [Learn Django Step 4](learn-django-in-visual-studio-step-04-full-django-project-template.md). |
| **Flask Web Project** | Statik dosyaları statik klasörde yer alan bir *uygulama* oluşturur. Şablon *views.py,* templates klasöründe bulunan Jinja altyapısını kullanan sayfa şablonlarıyla *yönlendirmeyi ele* almaktadır. Runserver.py  dosyası başlangıç kodu sağlar. Bkz. 

::: moniker range="vs-2017"
### <a name="polls-group"></a>Yoklamalar grubu

**\<framework> Yoklamalar Web Project** şablonları, kullanıcıların farklı yoklama sorularına oy verecekleri bir başlangıç web uygulaması oluşturur. Her uygulama, yoklamaları ve kullanıcı yanıtlarını yönetmek için bir veritabanı kullanmak üzere **Web** projesi şablonlarının yapısı üzerine kurulur. Uygulamalar, uygun veri modellerini ve dosya üzerinde bir veri kaynağından gelen yoklamaları yük *samples.jssayfasını (/seed)* içerir.

| Şablon | Açıklama |
| --- | --- |
| **Polls Bottle Web Project** | Ortam değişkeni kullanılarak yapılandırılan bir bellek içinde veritabanı, MongoDB veya Azure Tablo Depolama çalıştırabilecek bir `REPOSITORY_NAME` uygulama oluşturur. Veri modelleri ve veri deposu kodu *models* klasöründe bulunur ve *settings.py* dosyası hangi veri deposunın kullanlı olduğunu belirlemek için kod içerir. |
| **Django Web sitesini yoklar Project** | Bir Django projesi ve üç sayfalı bir Django uygulaması ve bir SQLite veritabanı oluşturur. Kimliği doğrulanmış bir yöneticinin yoklamaları oluşturmasına ve yönetmesine olanak sağlayan Django yönetim arabirimine özelleştirmeler içerir. Daha fazla bilgi için [bkz. Django şablonları ve](python-django-web-application-project-template.md) [Learn Django Step 6](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md). |
| **Flask/Jade Web Project** | **Polls Flask Web** Project şablonuyla aynı uygulamayı oluşturur, ancak Jinja şablon oluşturma altyapısı için Jade uzantısını kullanır. |
::: moniker-end

## <a name="install-project-requirements"></a>Proje gereksinimlerini yükleme

Çerçeveye özgü bir şablondan proje oluştururken, pip kullanarak gerekli paketleri yüklemenize yardımcı olacak bir iletişim kutusu görüntülenir. Ayrıca web sitenizi [yayımlarken](selecting-a-python-environment-for-a-project.md#use-virtual-environments) doğru bağımlılıkların dahil olması için web projeleri için sanal ortam kullanılması önerilir:

![Proje şablonu için gerekli paketleri yüken iletişim kutusu](media/template-web-requirements-txt-wizard.png)

Kaynak denetimi kullanıyorsanız, genellikle sanal ortam klasörünü atlarsınız çünkü bu ortam yalnızca *requirements.txt.* Klasörü dışlamanın en iyi yolu,  önce yukarıda gösterilen istemde ben yükleyeceğim öğesini seçmek ve ardından sanal ortamı oluşturmadan önce otomatik işlemeyi devre dışı bırakmaktır. Ayrıntılar için bkz. [Learn Django Tutorial - Steps 1-2 and 1-3](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) and [Learn Flask Tutorial - Steps 1-2 and 1-3](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository).

Microsoft Azure App Service dağıtım Microsoft Azure App Service python sürümünü site uzantısı olarak [seçin ve](./managing-python-on-azure-app-service.md?view=vs-2019&preserve-view=true) paketleri el ile yükleyin. Ayrıca, Azure App Service **bir** *requirements.txt* dosyasından paket yüklemez, çünkü Visual Studio'de yapılandırma [ayrıntılarını aka.ms/PythonOnAppService.](managing-python-on-azure-app-service.md)

## <a name="debugging"></a>Hata Ayıklama

Hata ayıklama için bir web projesi başlatıldığında, Visual Studio bir bağlantı noktası üzerinde yerel bir web sunucusu başlatır ve varsayılan tarayıcınızı bu adres ve bağlantı noktasına açar. Ek seçenekleri belirtmek için projeye sağ tıklayın, **Özellikler'i seçin** ve Web Başlatıcısı **sekmesini** seçin:

![Genel web şablonu için web başlatıcısı özellikleri](media/template-web-launcher-properties.png)

Hata **Ayıklama grubunda:**

- **Yolları,** Betik **Bağımsız Değişkenleri,** **Yorumlayıcı** Bağımsız Değişkenleri ve **Yorumlayıcı** Yolunu Ara: bu seçenekler normal hata ayıklama [ile aynıdır.](debugging-python-in-visual-studio.md)
- **Başlatma** URL'si: Tarayıcınızda açılan URL'yi belirtir. Varsayılan olarak olarak `localhost` kullanılır.
- **Bağlantı Noktası** Numarası: URL'de hiçbiri belirtilmezse, Visual Studio bağlantı noktası otomatik olarak seçer. Bu ayar, yerel hata ayıklama sunucusunun dinleyen bağlantı noktasını yapılandırmak için şablonlar tarafından kullanılan ortam değişkeninin varsayılan değerini `SERVER_PORT` geçersiz kılmaya olanak sağlar.

Sunucu Komutunu Çalıştır ve  **Sunucu Komut** Gruplarında Hata Ayıkla gruplarında (görüntüde gösterilenlerin altında ikinci özellikler yer almaktadır) web sunucusunun nasıl başlat olduğunu belirler. Birçok çerçeve, geçerli projenin dışında bir betik kullanımını gerektirmesi nedeniyle, betik burada ya da başlangıç modülünün adı bir parametre olarak geçiriliyor olabilir.

- **Komut:** Python betiği (*\* .py* dosyası), modül adı (içinde olduğu gibi) veya tek bir kod `python.exe -m module_name` satırı (örneğin, ) `python.exe -c "code"` olabilir. Açılan liste değeri, bu türlerden hangisinin amaçlı olduğunu gösterir.
- **Bağımsız değişkenler:** Bu bağımsız değişkenler komut satırına komutun ardından geçirildi.
- **Ortam:** Ortam değişkenlerini belirten çiftlerin \<NAME> = \<VALUE> yeni satırla ayrılmış listesi. Bu değişkenler, bağlantı noktası numarası ve arama yolları gibi ortamı değiştiren tüm özelliklerden sonra ayarlanır ve bu nedenle bu değerlerin üzerine yazabilirsiniz.

Herhangi bir proje özelliği veya ortam değişkeni, aşağıdaki MSBuild söz dizimleriyle belirtilebilir: `$(StartupFile) --port $(SERVER_PORT)` .
`$(StartupFile)` , başlangıç dosyasının göreli yoludur `{StartupModule}` ve başlangıç dosyasının içeri aktarılabilir adıdır. `$(SERVER_HOST)`ve , Başlatma URL'si ve Bağlantı Noktası Numarası özellikleri tarafından otomatik olarak veya Ortam özelliği tarafından `$(SERVER_PORT)` ayarlanmış normal ortam   **değişkenleridir.**

> [!Note]
> Sunucu **Komutunu Çalıştır'daki** değerler Hata Ayıklama Başlangıç Sunucusu komutu veya  >   **Ctrl** F5 ile + kullanılır;   Hata Ayıklama Sunucusu Komut grubunda yer alan değerler Hata Ayıklama Başlat Hata Ayıklama Sunucusu komutu veya **F5** ile  >   **kullanılır.**

### <a name="sample-bottle-configuration"></a>Örnek Bottle yapılandırması

**Bottle Web Project** şablonu, gerekli yapılandırmayı yapar ortak kodu içerir. Ancak, içe aktarılan bir bottle uygulaması bu kodu içermeyebilirsiniz, ancak bu durumda aşağıdaki ayarlar uygulamayı yüklü modülü kullanarak `bottle` başlatabilir:

- **Sunucu Komut grubunu** çalıştırın:
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