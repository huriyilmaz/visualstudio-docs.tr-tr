---
title: Python uygulamasını Azure App Service'da yayımlama Windows
description: Python web uygulamasını, Visual Studio dosyası için gerekli içerik Azure App Service Windows doğrudan web.config yayımlama.
ms.date: 01/07/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 0865be9aadc7991dda8597b3bb418d058ced43b4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076249"
---
# <a name="publishing-to-azure-app-service-on-windows"></a>Azure App Service'da Windows

> [!Note]
> Bu içerik ve açıklanan özellikler kullanım dışıdır ancak çalışmaya devam eder. Python geliştiricilerinin mümkün olduğunca Linux üzerinde App Service [geçirmeleri](publishing-python-web-applications-to-azure-from-visual-studio.md) teşvik edilecektir.

Visual Studio, bir Python web uygulamasını doğrudan Azure App Service web Windows. Azure App Service Windows, gerekli dosyaların sunucuya kopyalayıp web sunucusuna uygulamanın nasıl başlatıı talimatı verir uygun bir dosya ayarlayıp ayarlama `web.config` anlamına gelir.

Yayımlama işlemi 2017 ve Visual Studio 2015 ile Visual Studio farklılık gösterir. Özellikle Visual Studio 2015, oluşturulması da dahil olmak üzere bazı adımları otomatik hale getirir, ancak bu otomasyon uzun vadeli `web.config` esnekliği ve denetimi sınırlar. Visual Studio 2017 ve sonrası için daha fazla el ile adım gerekir, ancak Python ortamınız üzerinde daha kesin denetim sağlar. Her iki seçenek de burada açıklanmıştır.

> [!Note]
> Visual Studio 2015 ile Visual Studio 2017 ve sonrası arasındaki değişiklikler hakkında arka plan bilgi için, Visual Studio [2017'de Azure'da](https://devblogs.microsoft.com/python/publish-to-azure-in-vs-2017/)yayımlama blog gönderisi.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuz için Bottle, Flask veya Django çerçevelerini temel alan bir web uygulaması projesine ihtiyacınız vardır. Henüz bir projeniz yoksa ve yayımlama işlemini denemek için aşağıdaki gibi basit bir test projesi oluşturun:

1. Bu Visual Studio Dosya **> Yeni > Project'yi** seçin, **"Bottle"** araması yazın, Bottle Web Project'ı seçin, proje için bir ad ve bir yol belirtin ve Tamam'ı **seçin.** (Bottle şablonu Python geliştirme iş yüküne dahildir; bkz. [Yükleme.)](installing-python-support-in-visual-studio.md)

1. Sanal ortama yükle'yi ve sanal ortam için **tercih** ettiğiniz temel yorumlayıcıyı seçerek dış paketleri yüklemek için istemleri izleyin. Bu seçimi genellikle python'un yüklü olduğu sürümle App Service.

1. F5 tuşuna basarak veya Hata Ayıklamayı Başlat'ı seçerek **projeyi > test etmek.**

## <a name="create-an-azure-app-service"></a>Azure App Service oluşturma

Azure'da yayımlamak için bir hedef App Service. Bu amaçla Azure aboneliği App Service bir abonelik oluşturabilir veya geçici bir site kullanabilirsiniz.

Henüz bir aboneliğiniz yoksa, Azure hizmetleri için kredi kredileri içeren ücretsiz bir tam [Azure](https://azure.microsoft.com/free/)hesabıyla başlayabilirsiniz. Ayrıca, tam bir [yıl boyunca Visual Studio Dev Essentials](https://azure.microsoft.com/pricing/member-offers/vs-dev-essentials/)aylık 25 ABD doları kredi veren Visual Studio Dev Essentials için kaydolmayı da göz önünde bulundurarak.

> [!Tip]
> Azure, hesabınızı doğrulamak için bir kredi kartı isterse de kart ücret ödemez. Ek ücret [oluşmayacak şekilde ücretsiz](/azure/billing/billing-spending-limit) kredilerinize eşit bir harcama limiti de slarından yararlanabilirsiniz. Ayrıca Azure, bir sonraki App Service açıklandığı gibi basit test uygulamaları için ideal olan ücretsiz bir App Service planı katmanı sağlar.

### <a name="using-a-subscription"></a>Abonelik kullanma

Etkin bir Azure aboneliğiyle, boş App Service web uygulamasıyla aşağıdaki gibi bir hesap oluşturun:

1. [portal.azure.com.](https://portal.azure.com)
1. **+Yeni'yi** ve ardından Web ve Mobil'yi **ve** ardından **Web Uygulaması'ı seçin.**
1. Web uygulaması için bir ad belirtin, Kaynak **Grubu'nda** "Yeni Oluştur" olarak bırakın ve **Windows** seçin.
1. **App Service planı/konumu'na,** Yeni **oluştur'a** ve bir ad ve konum belirtin. Ardından Fiyatlandırma **katmanı'yı** seçin, ekranı aşağı kaydırarak  **F1** Ücretsiz planını seçin, Seç'e ve ardından **Tamam'a** ve ardından Oluştur'a **basın.**
1. (İsteğe bağlı) Uygulama App Service sonra bu klasöre gidin, Yayımlama profili **al'ı seçin** ve dosyayı yerel olarak kaydedin.

### <a name="using-a-temporary-app-service"></a>Geçici bir çözüm App Service

Azure aboneliğine App Service gerek kalmadan geçici bir abonelik oluşturun:

1. tarayıcınızı 'de [https://azure.microsoft.com/try/app-service/web/](https://azure.microsoft.com/try/app-service/web/) açın.
1. Uygulama **türü olarak Web** Uygulaması'ı ve ardından Sonraki'yi **seçin.**
1. Boş **Site'yi** ve ardından **Oluştur'u seçin.**
1. Tercihen sosyal oturum açma bilgileriyle oturum açabilirsiniz ve kısa bir süre sonra siteniz görüntülenen URL'de kullanıma hazırdır.
1. Yayımlama **profilini indir'i** seçin ve `.publishsettings` daha sonra kullanmak üzere dosyayı kaydedin.

## <a name="configure-python-on-azure-app-service"></a>Python'i Azure App Service

Boş bir Web App Service (aboneliğinize veya ücretsiz bir siteye) sahip bir uygulamanız olduktan sonra, python'ın seçilen bir sürümünü [Azure App Service.](managing-python-on-azure-app-service.md) Visual Studio 2017 ve sonraki bir sürümü yayımlamak için, bu makalede açıklandığı gibi site uzantısıyla yüklenmiş Python yorumlayıcının tam yolunu kaydedin.

İsterseniz, paketi bu yönergelerde yer alan işlemi kullanarak da yükleyebilirsiniz çünkü bu paket bu kılavuzda yer alan diğer `bottle` adımların bir parçası olarak yüklenir.

## <a name="publish-to-app-service---visual-studio-2017-and-later"></a>App Service-Visual Studio 2017 ve sonraki bir

Azure App Service 2017 ve Visual Studio'den yayımlamak yalnızca projenizin dosyalarını sunucuya kopyalar. Bu nedenle, sunucu ortamını yapılandırmak için gerekli dosyaları oluşturmak gerekir.

1. Bu Visual Studio **Çözüm Gezgini,** projeye sağ tıklayın ve Yeni **Öğe... > Ekle'yi seçin.** Görüntülenen iletişim kutusunda "Azure web.config (Hızlı CGI)" şablonunu ve ardından Tamam'ı seçin. Bu, proje kök dizininizde bir `web.config` dosyası oluşturur.

1. içinde girdisini, yolun sunucuda Python yüklemesi ile eşleşmesi için (tam ayrıntılar için `PythonHandler` `web.config` [bkz. IIS](https://www.iis.net/configreference) Yapılandırma Başvurusu (iis.net) ). Örneğin Python 3.6.1 x64 için giriş aşağıdaki gibi görünebilirsiniz:

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. içinde `WSGI_HANDLER` `web.config` girdisini kullanmakta olan çerçeve için uygun şekilde ayarlayın:

    - **Bottle:** aşağıda gösterildiği gibi parantez `app.wsgi_app` ekleyin. Bu, nesne bir değişken yerine bir işlev (bkz. `app.py` ) olduğundan gereklidir:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask:** `WSGI_HANDLER` değerini, `<project_name>.app` `<project_name>` projenizin adıyla eşleşen değerle değiştirir. içinde deyimine bakarak tam kimlik `from <project_name> import app` doğrularını `runserver.py` bulabilirsiniz. Örneğin, proje "FlaskAzurePublishExample" olarak adlandırılmışsa girdi aşağıdaki gibi görünür:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Django:** `web.config` Django projeleri için için iki değişiklik gerekir. İlk olarak değeri `WSGI_HANDLER` olarak `django.core.wsgi.get_wsgi_application()` (nesne dosyasındadır) `wsgi.py` olarak değiştirebilirsiniz:

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        İkinci olarak, için aşağıdaki girdinin altına ekleyin `WSGI_HANDLER` ve `DjangoAzurePublishExample` yerine projenizin adını yazın:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoAzurePublishExample.settings" />
        ```

1. **Yalnızca Django** uygulamaları: Django projesinin `settings.py` dosyasında, `ALLOWED_HOSTS` 'vspython-test-02.azurewebsites.net' yerine URL'nizi yazın:

    ```python
    # Change the URL to your specific site
    ALLOWED_HOSTS = ['vspython-test-02.azurewebsites.net']
    ```

    URL'nizin diziye eklenemedik hatası "/ Geçersiz HTTP_HOST: ' ' hatasıyla \<site URL\> sonuçlanır. '' '' ifadesini \<site URL\> ALLOWED_HOSTS."

    Dizi boş olduğunda Django'nun 'localhost' özelliğine otomatik olarak izin verir ancak üretim URL'nizi eklemek bu özellikleri kaldırır. Bu nedenle, ayrı geliştirme ve üretim kopyalarını korumak veya çalışma zamanı değerlerini kontrol etmek `settings.py` için ortam değişkenlerini kullanmak istiyor olabilir.

1. Bu **Çözüm Gezgini** projeniz ile aynı adlı klasörü genişletin, klasöre sağ tıklayın, Ekle > Yeni Öğe... öğesini seçin, "Azure statik dosyaları web.config" şablonunu seçin ve `static` Tamam'ı **seçin.**  Bu eylem `static` klasöründe, Python işlemesini bu klasör için devre dışı bırakan başka bir `web.config` oluşturur. Bu yapılandırma, statik dosyalar için, Python uygulamasını kullanmak yerine varsayılan web sunucusuna istekleri gönderir.

1. Projenizi kaydedin, ardından Visual Studio **Çözüm Gezgini** tıklayın ve Yayımla'yı **seçin.**

    ![Projenin bağlam menüsünde yayımla komutu](media/template-web-publish-command.png)

1. Görüntülenen **Yayımla** sekmesinde yayımlama hedefini seçin:

    a. Kendi Azure aboneliğiniz: **Microsoft Azure App Service'ı ve** ardından Var **Olanı Seç'i** ve ardından **Yayımla'yı seçin.** Uygun aboneliği ve uygulama hizmetini seçerek bir iletişim kutusu açılır. Uygulama App Service yoksa, geçici bir APp Hizmeti için aşağıda açıklandığı gibi indirilen yayımlama profilini kullanın.

    ![Azure'da yayımla 1. Visual Studio 2017 ve sonraki, mevcut abonelikler](media/tutorials-common-publish-1a-2017.png)

    b. try.azurewebsites.net profilinde geçici bir App Service kullanıyorsanız veya başka bir şekilde yayımlama profili kullanıyorsanız, Profili içeri aktar'ı bulmak için denetimi seçin, bu seçeneği belirleyin ve ardından **>** Yayımla'yı **seçin.**  Bu, daha önce indirilen dosyanın `.publishsettings` konumunu belirtir.

    ![Azure'da yayımlama 1. Visual Studio 2017 ve sonraki, geçici uygulama hizmeti](media/tutorials-common-publish-1b-2017.png)

1. Visual Studio yayımlama durumunu bir "Web Yayımlama Etkinliği" penceresinde ve Yayımla penceresinde görüntüler. Yayımlama işlemi tamamlandıktan sonra varsayılan tarayıcı site URL'sini açar. URL, Yayımla penceresinde de gösterilir.

1. Tarayıcı açıldığında "İç sunucu hatası meydana geldiği için sayfa görüntülenemiyor." iletisini görebilirsiniz. Bu ileti, sunucu üzerinde Python ortamınız tam olarak yapılandırılmamış olduğunu gösterir; bu durumda aşağıdaki adımları uygulayın:

    a. Uygun bir [Python site uzantısını Azure App Service](managing-python-on-azure-app-service.md)emin olmak için python'da Python'i yönetme'ye yeniden bakın.

    b. Dosyanız içinde Python yorumlayıcı yolunu bir kez daha `web.config` kontrol edin. Yol, seçtiğiniz site uzantısının yükleme konumuyla tam olarak eşleşmeli.

    c. Kudu konsolunu kullanarak, uygulamanın dosyasında listelenen paketleri yükseltin: gibi içinde kullanılan aynı Python klasörüne gidin ve Kudu konsolu bölümünde açıklandığı gibi aşağıdaki `requirements.txt` `web.config` `/home/python361x64` [komutu](managing-python-on-azure-app-service.md#azure-app-service-kudu-console) çalıştırın:

    ```command
    python -m pip install --upgrade -r /home/site/wwwroot/requirements.txt
    ```

    Bu komutu çalıştırma sırasında izin hataları görüyorsanız, komutunu site uzantısı klasördür ancak  komutunun varsayılan Python yüklemelerinden birinin klasöründe App Service denetleyin. Bu varsayılan ortamları değiştiremezsiniz, paketleri yükleme denemesi kesinlikle başarısız olur.

    d. Ayrıntılı hata çıkışı için düğümün içinde aşağıdaki satırı ekleyin ve bu satır `web.config` daha ayrıntılı hata çıkışı `<system.webServer>` sağlar:

    ```xml
    <httpErrors errorMode="Detailed"></httpErrors>
    ```

    e. Yeni paketleri yükledikten sonra App Service yeniden başlatmayı deneyin. her değişiklikte otomatik olarak yeniden başlatma `web.config` App Service değiştirerek yeniden başlatma `web.config` gerekmez.

    > [!Tip]
    > Uygulamanızın `requirements.txt` dosyasında herhangi bir değişiklik yaparsanız, bu dosyada listelenen paketleri yüklemek için yeniden Kudu konsolunu kullanmayı unutmayın.

1. Sunucu ortamını tamamen yapılandırdıktan sonra, sayfayı tarayıcıda yenilediğinizde Web uygulamasının görünmesi gerekir.

    ![Bottle, Flask ve Django uygulamalarının App Service'te yayımlanmasının sonuçları](media/azure-publish-results.png)

## <a name="publishing-to-app-service---visual-studio-2015"></a>App Service -Visual Studio 2015

> [!Note]
> Python [Öğreticisi:](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) Web Sitesi Visual Studio (youtube.com, 3m10s) öğreticisinde bu işleme ait kısa bir video bulunabilir.

1. **Çözüm Gezgini**'nde projeye sağ tıklayın ve **Yayımla**'yı seçin.

1. Yayımla **iletişim** kutusunda **Microsoft Azure App Service:**

  ![Azure'da yayımlama 1. adım](media/tutorials-common-publish-1.png)

1. Bir hedef seçin:

    - Azure aboneliğiniz varsa yayımlama **hedefi olarak Microsoft Azure App Service'ı** seçin, ardından aşağıdaki iletişim kutusunda mevcut bir  App Service seçin veya Yeni'yi seçerek yeni bir tane oluşturun.
    - Try.azurewebsites.net'den geçici bir site kullanıyorsanız yayımlama hedefi  olarak İçeri aktar'ı seçin, ardından siteden indirilen dosyaya göz atarak `.publishsettings` Tamam'ı **seçin.**

1. App Service ayrıntıları aşağıdaki **Yayımla iletişim** kutusunun **Bağlantı sekmesinde** görünür.

  ![Azure'da yayımlama 2. adım](media/tutorials-common-publish-2.png)

1. Ek **ayarları >** için Gereken şekilde Sonraki Adım'ı seçin.

1. **Yayımla**’yı seçin. Uygulama Azure'a dağıtıldıktan sonra, varsayılan tarayıcınız bu sitede açılır.

Bu sürecin bir parçası Visual Studio aşağıdaki adımları da gerçekleştirebilirsiniz:

- Sunucuda uygulamanın işlevine uygun işaretçiler içeren ve uygulamanın varsayılan `web.config` `wsgi_app` Python 3.4 yorumlayıcı App Service bir dosya oluşturun.
- Projenin klasöründeki dosyalar için işlemeyi kapatın `static` (bunun kuralları `web.config` içindedir).
- Sanal ortamı sunucuya yayımlayın.
- Uzaktan hata `web.debug.config` ayıklamayı etkinleştirmek için bir dosya ve hata ayıklama araçları ekleyin. 2019 Visual Studio 16.4 ve önceki sürümler için hata ayıklama araçları ptvsd'tir. 2019 Visual Studio 16.5 ve sonraki sürümler için hata ayıklama araçları hata ayıklar.

Daha önce belirtildiği gibi, bu otomatik adımlar yayımlama işlemini basitleştirir ancak Python ortamını denetlemeyi zorlaştırmaktadır. Örneğin, `web.config` dosya yalnızca sunucuda oluşturulur ancak projenize eklenmez. Yayımlama işlemi, sunucu yapılandırmasına güvenmek yerine geliştirme bilgisayarınızdan tüm sanal ortamı kopyalayıp kopyalaması nedeniyle de daha uzun sürer.

Sonunda kendi dosyanızı korumak ve paketleri `web.config` doğrudan sunucuda korumak için kullanmak istiyor `requirements.txt` olabilirsiniz. özellikle `requirements.txt` kullanmak, geliştirme ve sunucu ortamlarının her zaman eşleşmesini garanti eder.
