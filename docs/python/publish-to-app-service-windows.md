---
title: Windows üzerinde Azure App Service bir Python uygulaması yayımlama
description: web.config dosyası için gerekli içerik dahil olmak üzere Visual Studio 'dan Windows üzerinde Azure App Service doğrudan bir Python web uygulaması yayımlama.
ms.date: 01/07/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: af3e7c2d74a9d7b3a95ae24bba37981822247728
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912554"
---
# <a name="publishing-to-azure-app-service-on-windows"></a>Windows üzerinde Azure App Service yayımlama

> [!Note]
> Bu içerik ve açıklanan özellikler kullanım dışıdır, ancak çalışmaya devam eder. Python geliştiricilerinin, mümkün olduğunda [Linux üzerinde App Service](publishing-python-web-applications-to-azure-from-visual-studio.md) 'a geçirilmesi önerilir.

Visual Studio, doğrudan Windows üzerinde Azure App Service bir Python web uygulaması yayımlama olanağı sağlar. Windows üzerinde Azure App Service yayımlama, gerekli dosyaları sunucuya kopyalama ve `web.config` Web sunucusuna uygulamanızı nasıl başlatacağı hakkında uygun bir dosya ayarlama anlamına gelir.

Yayımlama işlemi, Visual Studio 2017 ve üzeri ve Visual Studio 2015 arasında farklılık gösterir. Özellikle, Visual Studio 2015, oluşturma da dahil olmak üzere bazı adımları otomatikleştirir, `web.config` ancak bu Otomasyon uzun süreli esneklik ve denetimi sınırlandırır. Visual Studio 2017 ve üzeri, daha el ile adım gerektirir, ancak Python ortamınız üzerinde daha kesin bir denetim sağlar. Her iki seçenek de burada açıklanmıştır.

> [!Note]
> Visual Studio 2015 ile Visual Studio 2017 ve üzeri değişikliklerle ilgili değişiklikler hakkında daha fazla bilgi için bkz. [visual 2017 Studio 'Da Azure 'Da yayımlama](https://devblogs.microsoft.com/python/publish-to-azure-in-vs-2017/), blog gönderisi.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yol için, şişe, Flask veya Docgo çerçevelerini temel alan bir Web uygulaması projesine ihtiyacınız vardır. Henüz bir projeniz yoksa ve yayımlama işlemini denemek istiyorsanız, aşağıdaki gibi basit bir test projesi oluşturun:

1. Visual Studio 'da **dosya > yeni > proje**' yi seçin, "şişe" araması yapın, **şişe Web projesi**' ni seçin, proje için bir yol belirtin ve bir yol belirtin, **Tamam**' ı seçin. (Şişe şablonu Python geliştirme iş yüküne dahildir; [yükleme](installing-python-support-in-visual-studio.md)bölümüne bakın.)

1. Sanal ortam için **bir sanal ortama** ve tercih ettiğiniz taban yorumlayıcı ' yı seçerek dış paketleri yüklemek için istemleri izleyin. Bu seçeneği genellikle App Service üzerinde yüklü olan Python sürümü ile eşleştirin.

1. F5 tuşuna basarak veya hata **ayıklamayı başlatmak > hata ayıkla** öğesini seçerek projeyi yerel olarak test edin.

## <a name="create-an-azure-app-service"></a>Azure App Service oluşturma

Azure 'da yayımlamak için bir hedef App Service gerekir. Bu amaçla, bir Azure aboneliği kullanarak bir App Service oluşturabilir veya geçici bir site kullanabilirsiniz.

Henüz aboneliğiniz yoksa Azure hizmetleri için genel krediler içeren [ücretsiz bir tam Azure hesabıyla](https://azure.microsoft.com/free/)başlayın. Ayrıca, tam bir yıl boyunca her ay $25 kredi sağlayan [Visual Studio Dev Essentials](https://azure.microsoft.com/pricing/member-offers/vs-dev-essentials/)için kaydolmasını göz önünde bulundurun.

> [!Tip]
> Azure, hesabınızı doğrulamak için kredi kartı isteyip istemediği halde kart ücretlendirilmez. Ayrıca, ek ücret gerçekleşmeyecek olmasını sağlamak için ücretsiz kredinize eşit bir [harcama limiti](/azure/billing/billing-spending-limit) ayarlayabilirsiniz. Ayrıca, Azure, sonraki bölümde açıklandığı gibi basit test uygulamaları için ideal olan ücretsiz bir App Service plan katmanı sunar.

### <a name="using-a-subscription"></a>Abonelik kullanma

Etkin bir Azure aboneliği ile, şu şekilde boş bir Web uygulamasıyla App Service oluşturun:

1. [Portal.Azure.com](https://portal.azure.com)adresinde oturum açın.
1. **+ Yeni**' yi seçin ve ardından **Web uygulaması**' nı **Web ve mobil** seçin.
1. Web uygulaması için bir ad belirtin, **kaynak grubunu** "Yeni oluştur" olarak bırakın ve işletim sistemi olarak **Windows** 'u seçin.
1. **App Service planı/konumu**' nu seçin, **Yeni oluştur**' u seçin ve bir ad ve konum belirtin. Ardından **fiyatlandırma katmanı**' nı seçin, aşağı kaydırın ve **F1 ücretsiz** planı seçin, **Seç**' e ve ardından **Tamam** ' a ve ardından **Oluştur**' a basın.
1. Seçim App Service oluşturulduktan sonra, bu sayfaya gidin, **Yayımlama profilini al**' ı seçin ve dosyayı yerel olarak kaydedin.

### <a name="using-a-temporary-app-service"></a>Geçici bir App Service kullanma

Azure aboneliğine gerek duymadan geçici bir App Service aşağıdaki gibi oluşturun:

1. Tarayıcınızı açın [https://azure.microsoft.com/try/app-service/web/](https://azure.microsoft.com/try/app-service/web/) .
1. Uygulama türü için **Web uygulaması** ' nı seçin ve ardından **İleri**' yi seçin.
1. **Boş site**' yi ve ardından **Oluştur**' u seçin.
1. Seçtiğiniz sosyal oturum açma bilgileriyle oturum açın ve kısa bir süre sonra, görüntülenmiş URL 'de bir kez daha kullanılır.
1. **Yayımlama profilini indir** ' i seçin ve `.publishsettings` daha sonra kullandığınız dosyayı kaydedin.

## <a name="configure-python-on-azure-app-service"></a>Azure App Service üzerinde Python yapılandırma

Çalışan boş bir Web uygulaması (aboneliğinizde veya ücretsiz bir sitede) olan bir App Service sahip olduktan sonra, Python 'un seçili bir sürümünü [Azure App Service üzerinde Python 'U yönetme](managing-python-on-azure-app-service.md)bölümünde anlatıldığı şekilde yükleyebilirsiniz. Visual Studio 2017 ve sonrasında yayımlama için, bu makalede açıklandığı gibi, site uzantısıyla yüklenen Python Yorumlayıcısına tam yolu kaydedin.

İsterseniz, paketi `bottle` Bu yönergedeki diğer adımların bir parçası olarak yüklendiği için bu talimatlarda işlemi kullanarak da yükleyebilirsiniz.

## <a name="publish-to-app-service---visual-studio-2017-and-later"></a>App Service yayımlama-Visual Studio 2017 ve üzeri

Visual Studio 2017 ' den Azure App Service yayımlama ve sonrasında yalnızca projenizdeki dosyaları sunucusuna kopyalar. Bu nedenle, sunucu ortamını yapılandırmak için gerekli dosyaları oluşturmak gerekir.

1. Visual Studio **Çözüm Gezgini**, projeye sağ tıklayın ve **> yeni öğe Ekle...** seçeneğini belirleyin. Görüntülenen iletişim kutusunda, "Azure web.config (Fast CGI)" şablonunu seçip Tamam ' ı seçin. Bu, proje kök dizininizde bir `web.config` dosyası oluşturur.

1. Yolu, `PythonHandler` `web.config` sunucudaki Python yüklemesiyle eşleşecek şekilde değiştirin (tam Ayrıntılar için bkz. [IIS yapılandırma başvurusu](https://www.iis.net/configreference) (iis.net)). Örneğin, Python 3.6.1 x64 için giriş aşağıdaki gibi görünmelidir:

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. Girişi, `WSGI_HANDLER` `web.config` kullanmakta olduğunuz çerçeveye uygun şekilde ayarlayın:

    - **Şişe**: `app.wsgi_app` aşağıda gösterildiği gibi parantezler ekleyin. Bu nesne bir değişken yerine bir işlev (bkz.) olduğu için gereklidir `app.py` :

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask**: değeri, `WSGI_HANDLER` `<project_name>.app` `<project_name>` projenizin adıyla eşleşen olacak şekilde değiştirin. İçindeki ifadeye bakarak tam tanımlayıcı bulabilirsiniz `from <project_name> import app` `runserver.py` . Örneğin, proje "FlaskAzurePublishExample" olarak adlandırılmışsa, giriş şu şekilde görünür:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Docgo**: `web.config` docgo projeleri için iki değişiklik yapılması gerekir. İlk olarak, `WSGI_HANDLER` değeri olarak değiştirin `django.core.wsgi.get_wsgi_application()` (nesne `wsgi.py` dosyada bulunur):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        İkinci olarak, öğesinin altına aşağıdaki girişi ekleyin, bunu `WSGI_HANDLER` `DjangoAzurePublishExample` projenizin adıyla değiştirin:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoAzurePublishExample.settings" />
        ```

1. **Yalnızca docgo uygulamaları**: docgo proje `settings.py` dosyasında, site URL etki alanınızı `ALLOWED_HOSTS` aşağıda gösterildiği gibi ekleyin ve ' vspython-test-02.azurewebsites.net ' ÖĞESINI, Kurstaki URL 'niz ile değiştirin:

    ```python
    # Change the URL to your specific site
    ALLOWED_HOSTS = ['vspython-test-02.azurewebsites.net']
    ```

    URL 'nizi diziye ekleme hatası, "DisallowedHost HTTP_HOST üst bilgisinde yok: ' ' hatasıyla sonuçlanır \<site URL\> . ALLOWED_HOSTS için ' ' eklemeniz gerekebilir \<site URL\> . "

    Dizi boş olduğunda, Docgo 'nun otomatik olarak ' localhost 'a izin verdiğini, ancak üretim URL 'nizi eklemenin bu özellikleri kaldırdığına unutmayın. Bu nedenle, uygulamasının ayrı geliştirme ve üretim kopyalarını sürdürmek `settings.py` veya çalışma süresi değerlerini denetlemek için ortam değişkenlerini kullanmak isteyebilirsiniz.

1. **Çözüm Gezgini**, projenizle aynı adlı klasörü genişletin, klasöre sağ tıklayın `static` , **> yeni öğe Ekle...** öğesini seçin, "Azure statik dosyalar web.config" şablonunu seçin ve **Tamam**' ı seçin. Bu eylem `static` klasöründe, Python işlemesini bu klasör için devre dışı bırakan başka bir `web.config` oluşturur. Bu yapılandırma, statik dosyalar için, Python uygulamasını kullanmak yerine varsayılan web sunucusuna istekleri gönderir.

1. Projenizi kaydedin, ardından Visual Studio **Çözüm Gezgini**, projeye sağ tıklayın ve **Yayımla**' yı seçin.

    ![Projenin bağlam menüsünde Yayımla komutu](media/template-web-publish-command.png)

1. Görüntülenen **Yayımla** sekmesinde yayımlama hedefini seçin:

    a. Kendi Azure aboneliğiniz: **Microsoft Azure App Service**' i seçin ve ardından **Yayımla**' yı **seçin** . Uygun abonelik ve App Service 'i seçebileceğiniz bir iletişim kutusu görüntülenir. App Service görünmezse, geçici bir APp Service için aşağıda açıklandığı gibi indirilen yayımlama profilini kullanın.

    ![Azure 'Da yayımlama adım 1, Visual Studio 2017 ve üzeri, mevcut abonelikler](media/tutorials-common-publish-1a-2017.png)

    b. Try.azurewebsites.net üzerinde geçici bir App Service kullanıyorsanız veya bir yayımlama profili kullanmanız gerekiyorsa, **>** **içeri aktarma profilini** bulmak için denetimi seçin, bu seçeneği belirleyin ve ardından **Yayımla**' yı seçin. Bu, `.publishsettings` daha önce indirilen dosyanın konumunu ister.

    ![Azure 'Da yayımlama adım 1, Visual Studio 2017 ve üzeri, geçici App Service](media/tutorials-common-publish-1b-2017.png)

1. Visual Studio yayımlama durumunu bir "Web yayımlama etkinliği" penceresinde ve Yayımla penceresinde görüntüler. Yayımlama işlemi tamamlandıktan sonra, site URL 'sinde varsayılan tarayıcı açılır. URL, Yayımla penceresinde de gösterilir.

1. Tarayıcı açıldığında, "iç sunucu hatası oluştuğundan sayfa görüntülenemiyor" iletisini görebilirsiniz. Bu ileti, sunucudaki Python ortamınızın tam olarak yapılandırılmadığını gösterir, bu durumda aşağıdaki adımları uygulayın:

    a. Uygun bir Python site uzantısının yüklü olduğundan emin olmak için [Azure App Service Python 'U yönetmek](managing-python-on-azure-app-service.md)üzere tekrar başvurun.

    b. Dosyanızdaki Python yorumlayıcı yolunu iki kez kontrol edin `web.config` . Yol, seçtiğiniz site uzantısının yüklenmesi konumuyla tam olarak eşleşmelidir.

    c. Uygulamanızın dosyasında listelenen paketleri yükseltmek için kudu konsolunu kullanın: gibi ' `requirements.txt` de kullanılan Python klasörüne gidin `web.config` `/home/python361x64` ve [kudu konsolu](managing-python-on-azure-app-service.md#azure-app-service-kudu-console) bölümünde açıklandığı gibi aşağıdaki komutu çalıştırın:

    ```command
    python -m pip install --upgrade -r /home/site/wwwroot/requirements.txt
    ```

    Bu komutu çalıştırırken izin hataları görürseniz, bu komutu, App Service varsayılan Python yüklemelerinden birinin klasöründe *değil* , site uzantı klasörünüzde çalıştırıp çalıştırdığınızı iki kez kontrol edin. Bu varsayılan ortamları değiştiremeyeceğiniz için, paket yüklenmeye çalışılması kesinlikle başarısız olur.

    d. Ayrıntılı hata çıktısı için, `web.config` `<system.webServer>` daha ayrıntılı hata çıktısı sağlayan düğümü içine aşağıdaki satırı ekleyin:

    ```xml
    <httpErrors errorMode="Detailed"></httpErrors>
    ```

    e. Yeni paketleri yükledikten sonra App Service yeniden başlatmayı deneyin. Değişiklik yapıldığında yeniden başlatma gerekli değildir `web.config` , çünkü App Service her değiştiğinde otomatik olarak yeniden başlatılır `web.config` .

    > [!Tip]
    > Uygulamanızın `requirements.txt` dosyasında herhangi bir değişiklik yaparsanız, bu dosyada listelenen paketleri yüklemek için yeniden Kudu konsolunu kullanmayı unutmayın.

1. Sunucu ortamını tamamen yapılandırdıktan sonra, sayfayı tarayıcıda yenilediğinizde Web uygulamasının görünmesi gerekir.

    ![Bottle, Flask ve Django uygulamalarının App Service'te yayımlanmasının sonuçları](media/azure-publish-results.png)

## <a name="publishing-to-app-service---visual-studio-2015"></a>App Service yayımlama-Visual Studio 2015

> [!Note]
> Bu işlemin kısa bir videosunu [Visual Studio Python öğreticisi: Web sitesi oluşturma](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) (YouTube.com, 3m10s) üzerinde bulabilirsiniz.

1. **Çözüm Gezgini**'nde projeye sağ tıklayın ve **Yayımla**'yı seçin.

1. **Yayımla** iletişim kutusunda **Microsoft Azure App Service** seçin:

  ![Azure 'da yayımlama 1. adım](media/tutorials-common-publish-1.png)

1. Hedef seçin:

    - Azure aboneliğiniz varsa, yayımlama hedefi olarak **Microsoft Azure App Service** ' i seçin, ardından aşağıdaki iletişim kutusunda mevcut bir App Service seçin veya yeni bir tane oluşturmak için **Yeni** ' yi seçin.
    - Try.azurewebsites.net ' den geçici bir site kullanıyorsanız, yayımlama hedefi olarak **Içeri aktar** ' ı seçin, ardından `.publishsettings` siteden indirilen dosyaya gözatıp **Tamam**' ı seçin.

1. App Service ayrıntılar, aşağıdaki **Yayımla** Iletişim kutusunun **bağlantı** sekmesinde görüntülenir.

  ![Azure 'da Yayımla adım 2](media/tutorials-common-publish-2.png)

1. Ek ayarları gözden geçirmek için gerektiğinde **ileri >' yi** seçin.

1. **Yayımla**’yı seçin. Uygulamanız Azure 'a dağıtıldığında, varsayılan tarayıcınız bu sitede açılır.

Bu işlemin bir parçası olarak, Visual Studio aşağıdaki adımları da yapar:

- Sunucuda, `web.config` uygulamanın işlevine uygun işaretçileri içeren bir dosya oluşturun `wsgi_app` ve bunun varsayılan Python 3,4 yorumlayıcısı App Service.
- Projenin klasöründeki dosyalar için işlemeyi devre dışı bırakın `static` (Bu kuralların bulunduğu kurallar `web.config` ).
- Sanal ortamı sunucuda yayımlayın.
- `web.debug.config`Uzaktan hata ayıklamayı etkinleştirmek için bir dosya ve hata ayıklama araçları ekleyin. Visual Studio 2019 sürüm 16,4 ve önceki sürümlerde hata ayıklama araçları ptvsd ' dir. Visual Studio 2019 sürüm 16,5 ve üzeri için hata ayıklama araçları hata ayıklıyorsanız GPY.

Daha önce belirtildiği gibi, bu otomatik adımlar yayımlama işlemini basitleştirir, ancak Python ortamının denetimini daha kolay hale getirir. Örneğin, `web.config` dosya yalnızca sunucuda oluşturulur ancak projenize eklenmez. Yayımlama işlemi aynı zamanda sunucu yapılandırmasına güvenmek yerine, tüm sanal ortamı geliştirme bilgisayarınızdan kopyalarken daha uzun sürer.

Sonuç olarak, kendi `web.config` dosyanızı sürdürmek ve `requirements.txt` doğrudan sunucudaki paketleri sürdürmek için kullanmak isteyebilirsiniz. `requirements.txt`Özellikle, geliştirme ve sunucu ortamlarınızın her zaman eşleştiğini garanti eder.
