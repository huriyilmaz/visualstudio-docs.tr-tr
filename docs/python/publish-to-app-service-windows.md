---
title: Windows'da Azure Uygulama Hizmeti'nde Python uygulaması yayınlama
description: Python web uygulamasını visual studio'dan Windows'da doğrudan Azure App Service'e yayınlama, web.config dosyası için gerekli içerik dahil.
ms.date: 01/07/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: cf9125476a4fdc369cc22034e081f2151020f064
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62784681"
---
# <a name="publishing-to-azure-app-service-on-windows"></a>Windows'da Azure Uygulama Hizmetine Yayımlama

> [!Note]
> Bu içerik ve açıklanan özellikler amortismana alınır, ancak çalışmaya devam edilir. Python geliştiricileri mümkün seçeneğ [inde Linux' taki App Service'](publishing-python-web-applications-to-azure-from-visual-studio.md) e geçmeye çağırılır.

Visual Studio, Python web uygulamasını doğrudan Windows'daki Azure Uygulama Hizmeti'nde yayımlama olanağı sağlar. Windows'da Azure Uygulama Hizmeti'nde yayımlama, gerekli dosyaları sunucuya kopyalamak ve web sunucusuna uygulamanızı nasıl başlatılabildiğini söyleyen uygun `web.config` bir dosya oluşturmak anlamına gelir.

Yayın süreci Visual Studio 2017 ve sonrası ile Visual Studio 2015 arasında farklılık göstermektedir. Özellikle Visual Studio 2015, uzun vadeli esneklik ve `web.config`denetimi sınırlar, ancak bu otomasyonun oluşturulması da dahil olmak üzere bazı adımları otomatikleştirir. Visual Studio 2017 ve daha sonra daha fazla manuel adım gerektirir, ancak Python ortamınız üzerinde daha kesin denetim sağlar. Her iki seçenek de burada açıklanmıştır.

> [!Note]
> Visual Studio 2015 ve Visual Studio 2017 ve sonrası arasındaki değişiklikler hakkında arka plan için, visual [studio 2017'de Azure'a Yayımla](https://devblogs.microsoft.com/python/publish-to-azure-in-vs-2017/)başlıklı blog gönderisine bakın.

## <a name="prerequisites"></a>Önkoşullar

Bu izbin için Şişe, Flask veya Django çerçevelerini temel alan bir web uygulaması projesine ihtiyacınız vardır. Henüz bir projeniz yoksa ve yayımlama işlemini denemek istiyorsanız, aşağıdaki gibi basit bir test projesi oluşturun:

1. Visual Studio'da, **Dosya > Yeni > Projesi'ni**seçin, "Şişe" aramasını, Şişe Web **Projesi'ni**seçin, proje için bir yol belirtive adlandırın, **Tamam'ı**tıklatın. (Şişe şablonu Python geliştirme iş yüküne dahildir; bkz. [Yükleme](installing-python-support-in-visual-studio.md).)

1. **Sanal ortama Yükle'yi** ve sanal ortam için tercih ettiğiniz temel yorumlayıcıyı seçerek harici paketleri yüklemek için istemleri izleyin. Bu seçimi genellikle App Service'de yüklü Python sürümüyle eşleşirsiniz.

1. F5 tuşuna basarak veya **Hata Ayıklama'yı başlat'>** hata ayıklama yı seçerek projeyi yerel olarak test edin.

## <a name="create-an-azure-app-service"></a>Azure App Service oluşturma

Azure'da yayımlama için hedef bir Uygulama Hizmeti gerektirir. Bu amaçla, Azure aboneliğini kullanarak bir Uygulama Hizmeti oluşturabilir veya geçici bir site kullanabilirsiniz.

Zaten bir aboneliğiniz yoksa, Azure hizmetleri için cömert krediler içeren [ücretsiz tam Azure hesabıyla](https://azure.microsoft.com/free/)başlayın. Ayrıca [Visual Studio Dev Essentials](https://azure.microsoft.com/pricing/member-offers/vs-dev-essentials/)için kaydolma düşünün , hangi tam bir yıl için her ay 25 $ kredi verir.

> [!Tip]
> Azure hesabınızı doğrulamak için bir kredi kartı istese de, kartücretlendirilmez. Ayrıca, ekstra ücret ödememenizi garanti etmek için ücretsiz kredilerinize eşit bir [harcama sınırı](/azure/billing/billing-spending-limit) da belirleyebilirsiniz. Buna ek olarak, Azure, bir sonraki bölümde açıklandığı gibi basit test uygulamaları için ideal olan ücretsiz bir Uygulama Hizmeti planı katmanı sağlar.

### <a name="using-a-subscription"></a>Abonelik kullanma

Etkin bir Azure aboneliği yle, boş bir Web Uygulamasıyla aşağıdaki gibi bir Uygulama Hizmeti oluşturun:

1. [portal.azure.com'da](https://portal.azure.com)oturum açın.
1. **+Yeni'yi**seçin, ardından **Web + Mobile'ı** seçin ve ardından **Web Uygulaması'nı**seçin.
1. Web uygulaması için bir ad belirtin, **Kaynak Grubu'nu** "Yeni Oluştur" olarak bırakın ve işletim sistemi olarak **Windows'u** seçin.
1. **App hizmet planı/konumu**seçin, **yeni oluştur'u**seçin ve bir ad ve konum belirtin. Sonra **Fiyatlandırma katmanıseçin,** aşağı kaydırın ve **F1 Free** planını seçin, **Seç**tuşuna basın, ardından **Tamam'a** basın ve ardından **Oluştur'** un.
1. (İsteğe bağlı) Uygulama Hizmeti oluşturulduktan sonra, uygulama için gidin, **yayımlama profilini alın'ı**seçin ve dosyayı yerel olarak kaydedin.

### <a name="using-a-temporary-app-service"></a>Geçici Bir Uygulama Hizmeti Kullanma

Aşağıdaki gibi bir Azure aboneliğine ihtiyaç duymadan geçici bir Uygulama Hizmeti oluşturun:

1. [tarayıcınızı try.azurewebsites.net için](https://try.azurewebsites.net)açın.
1. Uygulama türü için **Web Uygulaması'nı** seçin ve **ardından İleri'yi**seçin.
1. **Boş Site'yi**seçin, ardından **Oluştur'** u seçin.
1. Seçtiğiniz sosyal girişle oturum açın ve kısa bir süre sonra siteniz görüntülenen URL'de hazır olur.
1. **Yayımlama profilini İndir'i** seçin ve daha sonra kullandığınız dosyayı `.publishsettings` kaydedin.

## <a name="configure-python-on-azure-app-service"></a>Azure Uygulama Hizmetinde Python'u Yapılandırma

Boş bir Web Uygulaması çalışan bir Uygulama Hizmetine sahip olduktan sonra (aboneliğinizde veya ücretsiz bir sitede), Python'un seçilen bir sürümünü [Azure App Service'de Python'u Yönetme](managing-python-on-azure-app-service.md)olarak tanımlayın. Visual Studio 2017 ve sonrası yayın için, bu makalede açıklandığı şekilde site uzantısı ile yüklü Python yorumlayıcısı için tam yolu kaydedin.

İstenirse, bu `bottle` paket bu izlenme deki diğer adımların bir parçası olarak yüklendiğinden, bu yönergedeki işlemi kullanarak paketi de yükleyebilirsiniz.

## <a name="publish-to-app-service---visual-studio-2017-and-later"></a>Uygulama Hizmetine Yayınla - Visual Studio 2017 ve sonrası

Visual Studio 2017'den Azure Uygulama Hizmetine yayımlama ve daha sonra yalnızca projenizdeki dosyaları sunucuya kopyalar. Bu nedenle, sunucu ortamını yapılandırmak için gerekli dosyaları oluşturmak gerekir.

1. Visual Studio **Solution Explorer'da**projeyi sağ tıklatın ve **Yeni Öğe ekle> seçin...** seçeneğini belirleyin. Görünen iletişim kutusunda ,"Azure web.config (Hızlı CGI)" şablonu seçeneğini belirleyin ve Tamam'ı seçin. Bu, proje kök dizininizde bir `web.config` dosyası oluşturur.

1. Girişi, `PythonHandler` `web.config` yolun sunucudaki Python yüklemesi ile eşleşerek değiştirin (tam ayrıntılar için [IIS Configuration Reference](https://www.iis.net/configreference) (iis.net) adresine bakın). Örneğin, Python 3.6.1 x64 için giriş aşağıdaki gibi görünmelidir:

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. `WSGI_HANDLER` Girişi kullanmakta `web.config` olduğunuz çerçeveye uygun olarak ayarlayın:

    - **Şişe**: aşağıda gösterildiği `app.wsgi_app` gibi sonra parantez ekleyin. Bu nesne bir değişken yerine bir `app.py`işlev (bkz) olduğundan gereklidir:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Şişe**: Projenizin `<project_name>.app` `<project_name>` adı ile `WSGI_HANDLER` eşleşen değeri değiştirin. Tam identiferi ifadeye `from <project_name> import app` bakarak `runserver.py`bulabilirsiniz. Örneğin, proje "FlaskAzurePublishExample" olarak adlandırılırsa, giriş aşağıdaki gibi görünür:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Django**: Django `web.config` projeleri için iki değişiklik gereklidir. İlk olarak, `WSGI_HANDLER` değeri `django.core.wsgi.get_wsgi_application()` değiştirin (nesne `wsgi.py` dosyada:

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        İkinci olarak, projenizin `WSGI_HANDLER`adı ile `DjangoAzurePublishExample` değiştirerek aşağıdaki girişi ekleyin:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoAzurePublishExample.settings" />
        ```

1. **Yalnızca Django uygulamaları**: Django `settings.py` projesinin dosyasında, sitenizin URL etki alanını aşağıda gösterildiği `ALLOWED_HOSTS` gibi ekleyin ve URL'nizle 'vspython-test-02.azurewebsites.net' yerine ekleyin:

    ```python
    # Change the URL to your specific site
    ALLOWED_HOSTS = ['vspython-test-02.azurewebsites.net']
    ```

    Url'nizi diziye ekleyememesi , "DisallowedHost at / Geçersiz HTTP_HOST\<üstbilgi: ' site URL'si\>' hatasıyla sonuçlanır. ALLOWED_HOSTS ' site\<URL'sini\>' eklemeniz gerekebilir."

    Dizi boşolduğunda, Django'nun otomatik olarak 'localhost'a izin verdiğini, ancak üretim URL'nizi eklemenin bu yetenekleri kaldırdığını unutmayın. Bu `settings.py`nedenle, çalışma süresi değerlerini denetlemek için ayrı geliştirme ve üretim kopyalarını korumak veya ortam değişkenlerini kullanmak isteyebilirsiniz.

1. **Çözüm Gezgini'nde,** projenizle aynı adlı klasörü `static` genişletin, klasöre sağ tıklayın, **Yeni Öğe > Ekle'yi seçin...**, "Azure statik dosyaları web.config" şablonunu seçin ve **Tamam'ı**seçin. Bu eylem `static` klasöründe, Python işlemesini bu klasör için devre dışı bırakan başka bir `web.config` oluşturur. Bu yapılandırma, statik dosyalar için, Python uygulamasını kullanmak yerine varsayılan web sunucusuna istekleri gönderir.

1. Projenizi kaydedin, ardından Visual Studio **Solution Explorer'da,** projeyi sağ tıklatın ve **Yayımla'yı**seçin.

    ![Projenin bağlam menüsünde komut yayımlama](media/template-web-publish-command.png)

1. Görünen **Yayımla** sekmesinde yayımlama hedefini seçin:

    a. Kendi Azure aboneliğiniz: **Microsoft Azure Uygulama Hizmeti'ni**seçin, ardından **Varolan'ı seçin** ve ardından **Yayımla'yı**seçin. Uygun abonelik ve uygulama hizmetini seçebileceğiniz bir iletişim kutusu görüntülenir. Uygulama Hizmeti görünmüyorsa, geçici bir APp Hizmeti için aşağıda açıklandığı gibi indirilen yayımlama profilini kullanın.

    ![Azure adım 1, Visual Studio 2017 ve sonrası, mevcut abonelikleri yayımla](media/tutorials-common-publish-1a-2017.png)

    b. try.azurewebsites.net'da geçici bir Uygulama Hizmeti kullanıyorsanız veya bir yayımlama profili **>** kullanmanız gerekiyorsa, **İçe Aktar profilini**bulmak için denetimi seçin, bu seçeneği seçin ve **ardından Yayımla'yı**seçin. Bu, daha önce indirilen `.publishsettings` dosyanın konumu için istemleri.

    ![Azure adım 1, Visual Studio 2017 ve sonrası geçici uygulama hizmetinde yayımlayın](media/tutorials-common-publish-1b-2017.png)

1. Visual Studio yayımlama durumunu "Web Yayımlama Etkinliği" penceresinde ve Yayımla penceresinde görüntüler. Yayımlama tamamlandıktan sonra, varsayılan tarayıcı site URL'sinde açılır. URL, Yayımla penceresinde de gösterilir.

1. Tarayıcı açıldığında, "Dahili sunucu hatası oluştuğu için sayfa görüntülenemiyor" iletisini görebilirsiniz. Bu ileti, sunucudaki Python ortamınızın tam olarak yapılandırılmadığını gösterir ve bu durumda aşağıdaki adımları yapar:

    a. [Azure Uygulama Hizmetinde Python'u Yönetme'ye](managing-python-on-azure-app-service.md)yeniden bakın ve uygun bir Python site uzantınız olduğundan emin olun.

    b. Dosyanızdaki Python yorumlayıcısına giden `web.config` yolu iki kez kontrol edin. Yol, seçtiğiniz site uzantısının yükleme konumuyla tam olarak eşleşmelidir.

    c. Uygulamanızın `requirements.txt` dosyasında listelenen paketleri yükseltmek için Kudu konsolunu kullanın: Kullanılan python klasörüne `web.config` `/home/python361x64`gidin ve [Kudu konsolbölümünde](managing-python-on-azure-app-service.md#azure-app-service-kudu-console) açıklandığı gibi aşağıdaki komutu çalıştırın:

    ```command
    python -m pip install --upgrade -r /home/site/wwwroot/requirements.txt
    ```

    Bu komutu çalıştırırken izin hataları görürseniz, Uygulamayı Servis'in varsayılan Python yüklemelerinden birinin klasöründe *değil,* site uzantısı klasörünüzde komutu çalıştırdığınızı iki kez kontrol edin. Bu varsayılan ortamları değiştiremediğiniz için, paketleri yüklemeye çalışmak kesinlikle başarısız olur.

    d. Ayrıntılı hata çıktısı için, `web.config` daha `<system.webServer>` ayrıntılı hata çıktısı sağlayan düğüm içine aşağıdaki satırı ekleyin:

    ```xml
    <httpErrors errorMode="Detailed"></httpErrors>
    ```

    e. Yeni paketler yükledikten sonra Uygulama Hizmetini yeniden başlatmayı deneyin. Uygulama Hizmeti `web.config` `web.config` her değiştiğinde otomatik olarak yeniden başlatma yaptığı ndan, değiştirme yaparken yeniden başlatma gerekmez.

    > [!Tip]
    > Uygulamanızın `requirements.txt` dosyasında herhangi bir değişiklik yaparsanız, bu dosyada listelenen paketleri yüklemek için yeniden Kudu konsolunu kullanmayı unutmayın.

1. Sunucu ortamını tamamen yapılandırdıktan sonra, sayfayı tarayıcıda yenilediğinizde Web uygulamasının görünmesi gerekir.

    ![Bottle, Flask ve Django uygulamalarının App Service'te yayımlanmasının sonuçları](media/azure-publish-results.png)

## <a name="publishing-to-app-service---visual-studio-2015"></a>Uygulama Hizmetine Yayın - Visual Studio 2015

> [!Note]
> Bu sürecin kısa bir video [Visual Studio Python Tutorial bulunabilir: Bir Web Sitesi Oluşturma](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (youtube.com, 3m10s).

1. **Çözüm Gezgini'nde**, projeyi seç seçeneğini sağ **tıklatın.**

1. **Yayımla** iletişim kutusunda Microsoft **Azure Uygulama Hizmeti'ni**seçin:

  ![Azure adım 1'de yayımla](media/tutorials-common-publish-1.png)

1. Bir hedef seçin:

    - Azure aboneliğiniz varsa, yayımlama hedefi olarak **Microsoft Azure Uygulama Hizmeti'ni** seçin, ardından aşağıdaki iletişim kutusunda varolan bir Uygulama Hizmeti seçin veya yeni bir abonelik oluşturmak için **Yeni'yi** seçin.
    - try.azurewebsites.net'dan geçici bir site kullanıyorsanız, yayımlama hedefi olarak Içe `.publishsettings` **Aktar'ı** seçin, ardından siteden indirilen dosyaya göz atın ve **Tamam'ı**seçin.

1. Uygulama Hizmeti ayrıntıları, aşağıdaki **Yayımla** iletişim kutusunun **Bağlantı** sekmesinde görünür.

  ![Azure adım 2'ye yayımla](media/tutorials-common-publish-2.png)

1. Ek ayarları gözden geçirmek için gerektiğinde **Sonraki >'ı** seçin.

1. **Yayımla**’yı seçin. Uygulamanız Azure'a dağıtıldıktan sonra varsayılan tarayıcınız bu sitede açılır.

Bu işlemin bir parçası olarak Visual Studio da aşağıdaki adımları yapar:

- Sunucuda, uygulamanın işlevine ve App Service'in `web.config` `wsgi_app` varsayılan Python 3.4 yorumlayıcısına uygun işaretçiler içeren bir dosya oluşturun.
- Proje `static` klasöründeki dosyalar için işlemeyi kapatın (bunun `web.config`için kurallar var).
- Sanal ortamı sunucuda yayımlayın.
- Uzaktan `web.debug.config` hata ayıklamayı etkinleştirmek için bir dosya ve ptvsd hata ayıklama araçları ekleyin.

Daha önce de belirtildiği gibi, bu otomatik adımlar yayımlama işlemini basitleştirir, ancak Python ortamını denetlemeyi zorlaştırır. Örneğin, `web.config` dosya yalnızca sunucuda oluşturulur, ancak projenize eklenmez. Sunucu yapılandırması yerine tüm sanal ortamı geliştirme bilgisayarınızdan kopyaladığı için yayımlama işlemi de daha uzun sürer.

Sonunda kendi `web.config` dosyanızı korumak ve doğrudan `requirements.txt` sunucuda paketleri korumak için kullanmak isteyebilirsiniz. Özellikle `requirements.txt`kullanmak, geliştirme ve sunucu ortamlarınızın her zaman eşleşip eşleşmediğini garanti eder.
