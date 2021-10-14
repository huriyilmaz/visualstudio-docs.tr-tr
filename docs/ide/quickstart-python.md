---
title: 'Hızlı Başlangıç: Visual Studio ile Python web uygulaması oluşturma'
titleSuffix: ''
description: Bu hızlı başlangıçta, Python'Visual Studio basit bir web uygulaması oluşturmak için Visual Studio ve Flask çerçevesini kullanırız.
ms.date: 09/14/2021
ms.technology: vs-python
ms.topic: quickstart
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.custom:
- vs-acquisition
ms.workload:
- python
- data-science
ms.openlocfilehash: beb86c395735c2015eae64866aaf36aefbf9a507
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129971627"
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>Hızlı Başlangıç: Visual Studio kullanarak ilk Python web Visual Studio

Python IDE olarak Visual Studio 5-10 dakikalık bir tanıtımda Flask çerçevesini temel alan basit bir Python web uygulaması oluşturabilirsiniz. Projenin temel özellikleri hakkında bilgi edinerek projeyi Visual Studio adımlarla oluşturabilirsiniz.

::: moniker range="vs-2017"

Henüz yüklemedıysanız, Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) indirmeler sayfasına gidin. Yükleyicide Python geliştirme iş yükünün seçili **olduğundan emin** olun.

::: moniker-end

::: moniker range="vs-2019"

Henüz yüklemedıysanız, Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/downloads) indirmeler sayfasına gidin. Yükleyicide Python geliştirme iş yükünün seçili **olduğundan emin** olun.

::: moniker-end

::: moniker range=">=vs-2022"

Henüz yüklemedıysanız, Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/downloads) indirmeler sayfasına gidin. Uygulama Visual Studio Yükleyicisi Python geliştirme iş **yükünü** seçin ve yükleme ayrıntılarında Python **web desteği'ne tıklayın.**

![Python geliştirme iş Visual Studio Yükleyicisi Python web desteğinin seçili olduğu uygulamanın ekran görüntüsü.](media/vs-2022/python-web.png)

::: moniker-end

## <a name="create-the-project"></a>Proje oluşturma

Aşağıdaki adımlarda uygulama için kapsayıcı olarak görev alan boş bir proje oluşturulmektedir:

::: moniker range="vs-2017"
1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan Dosya'> **Yeni > Project.**

3. Yeni **Project** iletişim kutusunda, sağ üstteki arama alanına "Python Web Project" yazın, ortadaki **listede Web** projesi'ne tıklayın, projeye "HelloPython" gibi bir ad girin ve Tamam'ı **seçin.**

    ![Python Web Uygulaması'nın seçili olduğu Project iletişim kutusu](media/quickstart-python-00-web-project.png)

    Python proje şablonlarını görmüyorsanız, Visual Studio Yükleyicisi çalıştırın, Diğer Değiştir'i seçin, Python geliştirme iş  yükünü seçin ve ardından > Değiştir'i **seçin.**  

    ![Visual Studio yükleyicisinde Python geliştirme iş yükü](../python/media/installation-python-workload.png)

4. Yeni proje, **Çözüm Gezgini** bölmede açılır. Proje başka dosya içerdiği için bu noktada boştur.

    ![Yeni oluşturulan boş projeyi gösteren çözüm gezgini](media/quickstart-python-01-empty-project.png)
::: moniker-end

::: moniker range="vs-2019"
1. 2019 Visual Studio'i açın.
2. Başlangıç ekranında Yeni proje **oluştur'a tıklayın.**
3. Yeni proje **oluştur iletişim** kutusunda, üst sıradaki arama alanına "Python web" yazın, ortadaki **listede Web** Project'yi seçin ve ardından Sonraki:

    ![Python Web uygulaması seçiliyken yeni bir proje ekranı Project Python proje şablonlarını görmüyorsanız Visual Studio Yükleyicisi'yi çalıştırın, Diğer Değiştir'i seçin, Python geliştirme iş yükünü seçin ve ardından ](media/quickstart-python-00-web-project-2019a.png)   > Değiştir'i **seçin.** 

    ![Visual Studio yükleyicisinde Python geliştirme iş yükü](../python/media/installation-python-workload.png)

4. Aşağıdaki **Yeni projenizi yapılandır iletişim** kutusunda, ad olarak "HelloPython" **Project,** bir konum belirtin ve Oluştur'a **basın.** (Çözüm **adı,** otomatik olarak Project **ayarlanır.)**

    ![Yeni projenizi yapılandırma iletişim kutusu](media/quickstart-python-00-web-project-2019b.png)

5. Yeni proje, **Çözüm Gezgini** bölmede açılır. Proje başka dosya içerdiği için bu noktada boştur.

    ![Yeni oluşturulan boş projeyi Çözüm Gezgini.](media/quickstart-python-01-empty-project-2019.png)

::: moniker-end

::: moniker range=">=vs-2022"
1. 2022 Visual Studio açın.
1. Başlangıç ekranında Yeni proje **oluştur'a tıklayın.**
1. Yeni **proje oluştur iletişim** kutusunda, en üstte yer alan arama alanına "Python web" yazın. Listeden **Web Project'yi** ve ardından Sonraki'yi **seçin:**
   
   ![Python Web Uygulaması'nın seçili olduğu Yeni proje oluştur Project ekran görüntüsü.](media/vs-2022/python-web-project.png)
   
   Python web projesi şablonlarını görmüyorsanız araçları çalıştırmak için Araçlar Araçları ve Özellikleri  >   Al'ı Visual Studio Yükleyicisi. Yükleyici'de Python geliştirme iş **yükünü seçin** ve Yükleme **ayrıntıları'nın altında** Python web **desteği'ne tıklayın.** Ardından **Değiştir'i seçin.**

1. Yeni **projenizi yapılandır iletişim kutusunda,** ad olarak "HelloPython" **Project,** bir konum belirtin ve oluştur'a **tıklayın.** Çözüm **adı otomatik** olarak adı ile eş Project **uzer.**

   ![Yeni projenizi yapılandır iletişim kutusunu gösteren ekran görüntüsü.](media/vs-2022/configure-project.png)

Yeni proje, **Çözüm Gezgini** bölmede açılır. Proje başka dosya içerdiği için bu noktada boştur.

![Yeni oluşturulan boş Çözüm Gezgini ekran görüntüsü.](media/vs-2022/solution-explorer.png)
::: moniker-end

**Soru: Python uygulaması için Visual Studio oluşturmanın avantajı nedir?**

**Cevap:** Python uygulamaları genellikle yalnızca klasörler ve dosyalar kullanılarak tanımlanır, ancak uygulamalar büyüdükçe bu basit yapı zahmetli hale gelebilir. Uygulamalar otomatik olarak oluşturulan dosyaları, web uygulamaları için JavaScript'i ve diğer bileşenleri içerir. Bir Visual Studio projesi bu karmaşıklığı yönetmeye yardımcı olur.

*.pyproj dosyası olan* proje, projeniz ile ilişkili tüm kaynak ve içerik dosyalarını tanımlar. *.pyproj dosyası* her dosya için derleme bilgileri içerir, kaynak denetim sistemleriyle tümleştirileyecek bilgileri sürdürür ve uygulamanın mantıksal bileşenlerde düzenlenmesine yardımcı olur.

**Soru: Çözüm Gezgini'da gösterilen "çözüm" Çözüm Gezgini?**

**Cevap:** Visual Studio çözüm, bir veya daha fazla ilgili projeyi grup olarak yönetmenize yardımcı olan bir kapsayıcıdır. Çözüm, bir projeye özgü olmayan yapılandırma ayarlarını depolar. Bir çözümdeki projeler de diğerine başvurur. Örneğin, bir Python uygulama projesi çalıştırılırken, Python uygulamasının kullandığı C++ uzantısı gibi ikinci bir proje otomatik olarak derlenir.

## <a name="install-the-flask-library"></a>Flask kitaplığını yükleme

Python'daki web uygulamaları, web isteklerini yönlendirme ve yanıtları şekillendirme gibi alt düzey ayrıntıları işlemek için neredeyse her zaman kullanılabilir python kitaplıklarından birini kullanır. Visual Studio web uygulamaları için birçok şablon sağlar. Bu şablonlardan birini daha sonra bu Hızlı Başlangıç'ta kullanacağız.

Flask kitaplığını bu proje için kullanabileceğiniz varsayılan *genel Visual Studio* yüklemek için aşağıdaki adımları kullanın.

::: moniker range="vs-2017"
1. Projenin **varsayılan ortamını** görmek için projedeki Python Ortamları düğümünü genişletin.

    ![Varsayılan ortamı gösteren çözüm gezgini](media/quickstart-python-02-default-environment.png)

2. Ortama sağ tıklayın ve Python Paketini **Yükle'yi seçin.** Bu komut, **Paketler sekmesinde Python** Ortamları **penceresini** açar.

3. Arama alanına "flask" girin ve **PyPI'den pip install flask öğesini seçin.** Yönetici ayrıcalıkları istemlerini kabul et ve devam etmek **için** Visual Studio penceresini gözlemler. (Genel ortamın packages klasörü *C:\Program Files* gibi korumalı bir alanda yer alıyorsa yükseltme istemi gerçekleşir.)

    ![Pip install kullanarak Flask kitaplığını yükleme](media/quickstart-python-03-install-package.png)
::: moniker-end
::: moniker range="vs-2019"
1. Projenin **varsayılan ortamını** görmek için projedeki Python Ortamları düğümünü genişletin.

    ![Varsayılan ortamı gösteren çözüm gezgini](media/quickstart-python-02-default-environment-2019.png)

2. Ortama sağ tıklayın ve Python Paketlerini **Yönet... öğesini seçin.** Bu komut, **Paketler** **(PyPI) sekmesinde Python Ortamları penceresini** açar.

3. Arama alanına "flask" girin. Arama **kutusunun altında Flask** görünürse bu adımı atlayabilirsiniz. Aksi takdirde **Çalıştır komutu: pip install flask öğesini seçin.** Yönetici ayrıcalıkları istemlerini kabul et ve devam etmek **için** Visual Studio penceresini gözlemler. (Genel ortamın packages klasörü *C:\Program Files* gibi korumalı bir alanda yer alıyorsa yükseltme istemi gerçekleşir.)

    ![Pip install kullanarak Flask kitaplığını yükleme](media/quickstart-python-03-install-package-2019.png)
::: moniker-end

::: moniker range=">=vs-2022"
1. Projenin **varsayılan ortamını** görmek için projedeki Python Ortamları düğümünü genişletin.

    ![Çözüm Gezgini'da varsayılan ortamı gösteren ekran görüntüsü.](media/vs-2022/python-environment.png)

1. Ortama sağ tıklayın ve Python Paketlerini **Yönet'i seçin.** Bu komut, **Paketler** **(PyPI) sekmesinde Python Ortamları penceresini** açar.

1. Arama alanına "flask" girin. Arama **kutusunun altında Flask** görünürse bu adımı atlayabilirsiniz. Aksi takdirde Çalıştır **komutu: pip install flask öğesini seçin.**

    ![Pip install kullanarak Flask kitaplığını yüklemeyi gösteren ekran görüntüsü.](media/vs-2022/install-flask.png)

    Genel ortam paketleri klasörü *C:\Program Files* gibi korumalı bir alanda ise bir yükseltme istemi görüntülenir. Yönetici ayrıcalıkları istemlerini kabul etme. İlerleme durumu Visual Studio **çıkış** penceresini gözlemlemek.

::: moniker-end

Yüklendikten sonra kitaplık, python kodunda **kullanabileceğiniz Çözüm Gezgini** ortamında görüntülenir.

::: moniker range="vs-2017"
![Flask kitaplığı yüklü ve bu kitaplıkta Çözüm Gezgini](media/quickstart-python-04-package-installed.png)
::: moniker-end
::: moniker range="vs-2019"
![Flask kitaplığı yüklü ve bu kitaplıkta Çözüm Gezgini](media/quickstart-python-04-package-installed-2019.png)
::: moniker-end
::: moniker range=">=vs-2022"
![Flask kitaplığının yüklü olduğunu ve bu kitaplıkta görüntü Çözüm Gezgini.](media/vs-2022/flask-installed.png)
::: moniker-end

> [!Note]
> Geliştiriciler, kitaplıkları genel ortama yüklemek yerine, genellikle belirli bir proje için kitaplıkların yük devredilen bir "sanal ortam" oluşturması gerekir. Visual Studio şablonları genellikle Hızlı Başlangıç - Şablon kullanarak Python projesi oluşturma konularında da [ele alınarak bu seçeneği sağlar.](../python/quickstart-02-python-in-visual-studio-project-from-template.md)

**Soru: Diğer kullanılabilir Python paketleri hakkında nereden daha fazla bilgi öğrenebilirim?**

**Cevap:** Python Paket [Dizini'ne ziyaret edin.](https://pypi.org/)

## <a name="add-a-code-file"></a>Kod dosyası Ekle

Artık en az bir Web uygulaması uygulamak için bir Python kodu eklemek için hazırsınız.

::: moniker range="<=vs-2019"
1. **Çözüm Gezgini** projeye sağ tıklayın ve  > **Yeni öğe** Ekle ' yi seçin.

1. Görüntülenen iletişim kutusunda **boş Python dosyası**' nı seçin, *app.py* olarak adlandırın ve **Ekle**' yi seçin. Visual Studio, dosyayı otomatik olarak bir düzenleyici penceresinde açar.

1. Aşağıdaki kodu kopyalayın ve *app.py*'e yapıştırın:

    ```python
    from flask import Flask

    # Create an instance of the Flask class that is the WSGI application.
    # The first argument is the name of the application module or package,
    # typically __name__ when using a single module.
    app = Flask(__name__)

    # Flask route decorators map / and /hello to the hello function.
    # To add other resources, create functions that generate the page contents
    # and add decorators to define the appropriate resource locators for them.

    @app.route('/')
    @app.route('/hello')
    def hello():
        # Render the page
        return "Hello Python!"

    if __name__ == '__main__':
        # Run the app server on localhost:4449
        app.run('localhost', 4449)
    ```
::: moniker-end
::: moniker range=">= vs-2022"

1. **Çözüm Gezgini** projeye sağ tıklayın ve  > **Yeni öğe** Ekle ' yi seçin.

1. Görüntülenen iletişim kutusunda **boş**' ı seçin. **Ad** için *app.py* girin ve ardından **Ekle**' yi seçin. Visual Studio, dosyayı otomatik olarak bir düzenleyici penceresinde açar.

1. Aşağıdaki kodu kopyalayın ve *app.py*'e yapıştırın:

    ```python
    from flask import Flask

    # Create an instance of the Flask class that is the WSGI application.
    # The first argument is the name of the application module or package,
    # typically __name__ when using a single module.
    app = Flask(__name__)

    # Flask route decorators map / and /hello to the hello function.
    # To add other resources, create functions that generate the page contents
    # and add decorators to define the appropriate resource locators for them.

    @app.route('/')
    @app.route('/hello')
    def hello():
        # Render the page
        return "Hello Python!"

    if __name__ == '__main__':
        # Run the app server on localhost:4449
        app.run('localhost', 4449)
    ```
::: moniker-end

  >  **Yeni öğe** Ekle iletişim kutusunun Python sınıfı, Python paketi, Python birimi testi, *web.config* dosyaları ve daha fazlası dahil olmak üzere bir Python projesine ekleyebileceğiniz diğer birçok dosya türünü görüntülediğini fark etmiş olabilirsiniz. Genel olarak, bu *öğe şablonları* yararlı demirbaş kodla hızlı bir şekilde dosya oluşturmanın harika bir yoludur.

**Soru: Flask hakkında nereden daha fazla bilgi edinebilirim?**

**Cevap**: [Flask hızlı](https://flask.palletsprojects.com/quickstart/#quickstart)başlangıcı ile başlayan Flask belgelerine başvurun.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. **Çözüm Gezgini**' de, *app.py* ' a sağ tıklayın ve ardından açılan menüden **başlangıç dosyası olarak ayarla** ' yı seçin. Bu komut, uygulamayı çalıştırırken Python 'da başlatılacak kod dosyasını tanımlar.

    ::: moniker range="vs-2017"
    ![Çözüm Gezgini bir proje için başlangıç dosyası ayarlanıyor](media/quickstart-python-05-set-as-startup-file.png)
    ::: moniker-end
    ::: moniker range="vs-2019"
    ![Çözüm Gezgini bir proje için başlangıç dosyası ayarlanıyor](media/quickstart-python-05-set-as-startup-file-2019.png)
    ::: moniker-end
    ::: moniker range=">=vs-2022"
    ![Çözüm Gezgini içindeki bir projenin başlangıç dosyasını ayarlamayı gösteren ekran görüntüsü.](media/vs-2022/set-startup-file.png)
    ::: moniker-end

2. **Çözüm Gezgini** ' de projeye sağ tıklayın ve **Özellikler**' i seçin. **Özellikler** menüsünden **Hata Ayıkla** sekmesini seçin ve **bağlantı noktası numarası** özelliğini olarak ayarlayın `4449` . bu ayar `localhost:4449` , Visual Studio koddaki bağımsız değişkenlerle eşleşecek şekilde bir tarayıcı başlatır `app.run` .

3. Hata **ayıklama**  >  **olmadan Başlat** ' ı seçin veya + dosyalara yapılan değişiklikleri kaydeden ve uygulamayı çalıştıran CTRL **F5** tuşuna basın.

4. **Https: \/ /localhost: 4449 içinde çalışan** iletinin bulunduğu bir komut penceresi görüntülenir. Bir tarayıcı penceresi açılır `localhost:4449` ve **Hello, Python** iletisini görüntüler. `GET`İstek, komut penceresinde durumu ile de görüntülenir `200` .

    Bir tarayıcı otomatik olarak açılmazsa, seçtiğiniz tarayıcıyı başlatın ve adresine gidin `localhost:4449` .

    Yalnızca komut penceresinde Python etkileşimli kabuğunu görürseniz veya bu pencere ekranda yanıp sönmüyorsa, *app.py* 'in başlangıç dosyası olarak ayarlandığından emin olun.

5. `localhost:4449/hello`Kaynağın dekoratörü 'nin de çalışıp çalışmadığını sınamak için öğesine gidin `/hello` . Yine, `GET` istek, komut penceresinde durumu ile görünür `200` . Diğer URL 'Leri deneyin `404` , Ayrıca, komut penceresinde durum kodlarını gösterdiklerinden emin olmak için.

6. Uygulamayı durdurmak için komut penceresini kapatın ve ardından tarayıcı penceresini kapatın.

**Soru: hata ayıklama olmadan başlangıç ve hata ayıklama komutlarını başlatma arasındaki fark nedir?**

**cevap**: uygulamayı [Visual Studio hata ayıklayıcı](../python/debugging-python-in-visual-studio.md)bağlamında çalıştırmak için **hata ayıklamayı başlat** ' i kullanırsınız. Hata ayıklayıcı ile kesme noktaları ayarlayabilir, değişkenleri inceleyebilir ve satır satırına göre kod satırýnýz üzerinde ilerleyebileceğiniz adımları izleyebilirsiniz. Hata ayıklamayı mümkün kılan kancalar nedeniyle uygulamalar hata ayıklayıcıda daha yavaş çalışabilir.

**Hata ayıklama olmadan Başlat** , bunu komut satırından çalıştırdıysanız, hata ayıklama bağlamı olmadan doğrudan uygulamayı çalıştırır. **Hata ayıklama olmadan Başlat** Ayrıca otomatik olarak bir tarayıcı başlatır ve proje özellikleri **hata ayıklama** sekmesinde belirtilen URL 'ye gider.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio ilk Python uygulamanızı çalıştırırken tebrikler. Visual Studio Python ıde olarak kullanmanın biraz öğrendiniz!

> [!div class="nextstepaction"]
> [Uygulamayı Azure App Service dağıtma](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

Bu hızlı başlangıçta izlediğiniz adımlar oldukça geneldir, büyük olasılıkla otomatikleştirilmesi ve otomatik olması gerektiğini tahmin etmeniz gerekir. bu tür otomasyon Visual Studio proje şablonlarının rolüdür. Hızlı başlangıç-bu makaledeki, ancak daha az adımla bir Web uygulaması oluşturmak için [şablon kullanarak bir Python projesi oluşturun](../python/quickstart-02-python-in-visual-studio-project-from-template.md) .

etkileşimli pencere, hata ayıklama, veri görselleştirmesi ve Git ile çalışma gibi Visual Studio python 'da daha kapsamlı bir öğreticiye devam etmek için, [öğreticiyi izleyin: Visual Studio python 'u kullanmaya başlayın](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md).

Visual Studio sunabileceği daha fazla incelemek için aşağıdaki bağlantıları seçin.

- [Visual Studio 'de Python web uygulaması şablonları](../python/python-web-application-project-templates.md)hakkında bilgi edinin.
- [Python hata ayıklama](../python/debugging-python-in-visual-studio.md) hakkında bilgi edinin
- genel olarak [Visual Studio ıde](../get-started/visual-studio-ide.md) hakkında daha fazla bilgi edinin.
