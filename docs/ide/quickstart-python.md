---
title: "Quickstart: Python web uygulaması oluşturmak için Visual Studio'u kullanın"
description: Bu hızlı başlangıçta, Python'da basit bir web uygulaması oluşturmak için Visual Studio ve Flask çerçevesini kullanıyorsunuz.
ms.date: 03/07/2019
ms.technology: vs-python
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 649f933c3d0fc2962ed0f7efc2ab09449bdd72ba
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444953"
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>Quickstart: Visual Studio'u kullanarak ilk Python web uygulamanızı oluşturun

Python IDE olarak Visual Studio'ya 5-10 dakikalık girişte, Flask çerçevesine dayalı basit bir Python web uygulaması oluşturursunuz. Visual Studio'nun temel özellikleri hakkında bilgi edinmenize yardımcı olacak ayrı adımlarla projeyi oluşturursunuz.

::: moniker range="vs-2017"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin. Yükleyicide, **Python geliştirme** iş yükünü seçtiğinizden emin olun.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin. Yükleyicide, **Python geliştirme** iş yükünü seçtiğinizden emin olun.

::: moniker-end

## <a name="create-the-project"></a>Proje oluşturma

Aşağıdaki adımlar, uygulama için bir kapsayıcı olarak hizmet veren boş bir proje oluşturur:

::: moniker range="vs-2017"
1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan **Dosya > Yeni > Projesi'ni**seçin.

3. Yeni **Proje** iletişim kutusunda, sağ üstteki arama alanına "Python Web Project" girin, orta listede **Web projesini** seçin, projeye "HelloPython" gibi bir ad verin, ardından **Tamam'ı**seçin.

    ![Python Web Project seçili yeni proje iletişim kutusu](media/quickstart-python-00-web-project.png)

    Python proje şablonlarını görmüyorsanız, **Visual Studio Installer'ı**çalıştırın, **Daha Fazla** > **Değiştir'i**seçin, **Python geliştirme** iş yükünü seçin ve ardından **Değiştir'i**seçin.

    ![Visual Studio yükleyicisinde Python geliştirme iş yükü](../python/media/installation-python-workload.png)

4. Yeni **proje, çözüm gezgininde** sağ bölmede açılır. Başka dosya içermedığından proje bu noktada boştur.

    ![Yeni oluşturulan boş projeyi gösteren çözüm gezgini](media/quickstart-python-01-empty-project.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Görsel Stüdyo 2019'u açın.
2. Başlangıç ekranında **yeni bir proje oluştur'u**seçin.
3. Yeni **bir proje** oluştur iletişim kutusunda, en üstteki arama alanına "Python web" girin, orta listede **Web Project'i** seçin ve **ardından İleri'yi**seçin:

    ![Python Web Project seçili yeni bir proje ekranı oluşturma](media/quickstart-python-00-web-project-2019a.png)

    Python proje şablonlarını görmüyorsanız, **Visual Studio Installer'ı**çalıştırın, **Daha Fazla** > **Değiştir'i**seçin, **Python geliştirme** iş yükünü seçin ve ardından **Değiştir'i**seçin.

    ![Visual Studio yükleyicisinde Python geliştirme iş yükü](../python/media/installation-python-workload.png)

4. Aşağıdaki yeni proje iletişim **günlüğüne Yapıla,** **Proje adı**için "HelloPython" girin, konum belirtin ve **Oluştur'u**seçin. (Çözüm **adı** otomatik olarak Proje **adı**ile eşleşecek şekilde ayarlanır.)

    ![Yeni proje iletişim günlüğüne yapıla](media/quickstart-python-00-web-project-2019b.png)

5. Yeni **proje, çözüm gezgininde** sağ bölmede açılır. Başka dosya içermedığından proje bu noktada boştur.

    ![Yeni oluşturulan boş projeyi gösteren çözüm gezgini](media/quickstart-python-01-empty-project-2019.png)
::: moniker-end

**Soru: Python uygulaması için Visual Studio'da proje oluşturmanın avantajı nedir?**

**Cevap**: Python uygulamaları genellikle yalnızca klasörler ve dosyalar kullanılarak tanımlanır, ancak uygulamalar büyüdükçe ve belki de otomatik olarak oluşturulan dosyaları, web uygulamaları için JavaScript'i ve benzerlerini içerdiğiiçin bu basit yapı külfetli hale gelebilir. Visual Studio projesi bu karmaşıklığı yönetmenize yardımcı olur. Proje *(.pyproj* dosyası) projenizle ilişkili tüm kaynak ve içerik dosyalarını tanımlar, her dosya için yapı bilgileri içerir, kaynak denetim sistemleriyle tümleştirmek için bilgileri korur ve uygulamanızı mantıksal bileşenler halinde düzenlemenize yardımcı olur.

**Soru: Çözüm Gezgini'nde gösterilen "çözüm" nedir?**

**Yanıt**: Visual Studio çözümü, grup olarak bir veya daha fazla ilgili projeyi yönetmenize yardımcı olan ve projeye özgü olmayan yapılandırma ayarlarını depolar. Çözümdeki projeler, bir projeyi (Python uygulaması) otomatik olarak ikinci bir proje (Python uygulamasında kullanılan C++ uzantısı gibi) oluşturması gibi bir çözümde de birbirlerine başvurulabilir.

## <a name="install-the-flask-library"></a>Flask kitaplığını yükleme

Python'daki Web uygulamaları, web isteklerini yönlendirme ve yanıtları şekillendirme gibi düşük düzeyli ayrıntıları işlemek için hemen hemen her zaman kullanılabilir birçok Python kitaplığından birini kullanır. Bu amaçla Visual Studio, bu Quickstart'ta daha sonra kullandığınız web uygulamaları için çeşitli şablonlar sağlar.

Burada, Flask kitaplığını Visual Studio'nun bu proje için kullandığı varsayılan "genel ortama" yüklemek için aşağıdaki adımları kullanırsınız.

::: moniker range="vs-2017"
1. Proje için varsayılan ortamı görmek için projedeki **Python Ortamları** düğümunu genişletin.

    ![Varsayılan ortamı gösteren çözüm gezgini](media/quickstart-python-02-default-environment.png)

2. Ortama sağ tıklayın ve **Python Paketini Yükle'yi**seçin. Bu **komut, Paketler** sekmesinde **Python Ortamları** penceresini açar.

3. Arama alanına "şişe" girin ve **PyPI'den pip yükleme şişesini**seçin. Yönetici ayrıcalıkları için herhangi bir istem kabul edin ve ilerleme için Visual Studio'daki **Çıktı** penceresini gözlemleyin. (Genel ortam için paketler klasörü *C:\Program Files*gibi korunan bir alanda bulunduğunda yükseklik istemi olur.)

    ![Pip yüklemeyi kullanarak Flask kitaplığını yükleme](media/quickstart-python-03-install-package.png)
::: moniker-end
::: moniker range=">=vs-2019"
1. Proje için varsayılan ortamı görmek için projedeki **Python Ortamları** düğümunu genişletin.

    ![Varsayılan ortamı gösteren çözüm gezgini](media/quickstart-python-02-default-environment-2019.png)

2. Ortama sağ tıklayın ve **Python Paketlerini Yönet'i seçin... seçeneğini belirleyin.** Bu **komut, Paketler (PyPI)** sekmesinde **Python Ortamları** penceresini açar.

3. Arama alanına "şişe" girin. **Flask** arama kutusunun altında görünüyorsa, bu adımı atlayabilirsiniz. Aksi takdirde **Çalıştır komutunu seçin: pip yükleme şişesi**. Yönetici ayrıcalıkları için herhangi bir istem kabul edin ve ilerleme için Visual Studio'daki **Çıktı** penceresini gözlemleyin. (Genel ortam için paketler klasörü *C:\Program Files*gibi korunan bir alanda bulunduğunda yükseklik istemi olur.)

    ![Pip yüklemeyi kullanarak Flask kitaplığını yükleme](media/quickstart-python-03-install-package-2019.png)
::: moniker-end

4. Yüklendikten sonra kitaplık **Solution Explorer'da**ortamda görünür, bu da python kodunda kullanabileceğiniz anlamına gelir.

    ::: moniker range="vs-2017"
    ![Şişe kitaplığı Yüklendi ve Solution Explorer'da gösteriliyor](media/quickstart-python-04-package-installed.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Şişe kitaplığı Yüklendi ve Solution Explorer'da gösteriliyor](media/quickstart-python-04-package-installed-2019.png)
    ::: moniker-end

> [!Note]
> Geliştiriciler, kitaplıkları genel ortama yüklemek yerine genellikle belirli bir proje için kitaplıklar yükleyecek bir "sanal ortam" oluşturur. Visual Studio şablonları genellikle Quickstart'ta açıkgörüldüğü gibi bu seçeneği sunar [- Şablon kullanarak Python projesi oluşturun.](../python/quickstart-02-python-in-visual-studio-project-from-template.md)

**Soru: Diğer kullanılabilir Python paketleri hakkında daha fazla bilgi nereden edinebilirim?**

**Cevap**: [Python Paket Dizini'ni ziyaret edin.](https://pypi.org/)

## <a name="add-a-code-file"></a>Kod dosyası ekleme

Artık en az web uygulamasını uygulamak için biraz Python kodu eklemeye hazırsınız.

1. **Solution Explorer'da** projeyi sağ tıklatın ve Yeni Öğe **> Ekle'yi**seçin.

1. Görünen iletişim kutusunda **Boş Python Dosyası'nı**seçin, *app.py*adlandırın ve **Ekle'yi**seçin. Visual Studio dosyayı bir düzenleyici penceresinde otomatik olarak açar.

1. Aşağıdaki kodu kopyalayın ve *app.py*yapıştırın:

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

1. > Yeni Öğe **Ekle** iletişim kutusunun Python sınıfı, Python paketi, Python birim testi, *web.config* dosyaları ve daha fazlası dahil olmak üzere python projesine ekleyebileceğiniz diğer birçok dosya türünü görüntülediğini fark etmiş sinizdir. Genel olarak, bu öğe şablonları, çağrıldıkları gibi, yararlı ortak kodlu dosyaları hızla oluşturmak için harika bir yoldur.

**Soru: Flask hakkında daha fazla bilgi nereden edinebilirim?**

**Cevap**: [Flask Quickstart](https://flask.palletsprojects.com/en/1.1.x/quickstart/#quickstart)ile başlayan Flask belgelerine bakın.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. **Solution Explorer'da** *app.py* sağ tıklatın ve başlangıç dosyası **olarak ayarla'yı**seçin. Bu komut, uygulamayı çalıştırırken Python'da başlatılabilmek için kod dosyasını tanımlar.

    ::: moniker range="vs-2017"
    ![Solution Explorer'da bir proje için başlangıç dosyasını ayarlama](media/quickstart-python-05-set-as-startup-file.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Solution Explorer'da bir proje için başlangıç dosyasını ayarlama](media/quickstart-python-05-set-as-startup-file-2019.png)
    ::: moniker-end

2. **Solution Explorer'da** projeyi sağ tıklatın ve **Özellikler'i**seçin. Ardından **Hata Ayıklama** sekmesini seçin ve `4449`Bağlantı Noktası **Numarası** özelliğini ' olarak ayarlayın. Bu adım, Visual Studio'nun koddaki `localhost:4449` `app.run` bağımsız değişkenlerle eşleşecek bir tarayıcı başlatmasını sağlar.

3. Hata **Ayıklama > Hata Ayıklama olmadan Başlat** 'ı **(Ctrl**+**F5)** seçin, bu da dosyalardaki değişiklikleri kaydeder ve uygulamayı çalıştırın.

4. **\/Https: /localhost:4449'da çalışan**iletiyle bir komut penceresi görüntülenir ve `localhost:4449` "Merhaba, Python!" iletisini gördüğünüz yere bir tarayıcı penceresi açılmalıdır. GET isteği de 200 durumu ile komut penceresinde görünür.

    Bir tarayıcı otomatik olarak açılmıyorsa, seçtiğiniz tarayıcıyı `localhost:4449`başlatın ve 'ye gidin.

    Komut penceresinde yalnızca Python etkileşimli kabuğunu görürseniz veya bu pencere ekranda kısa bir süre yanıp sönerse, yukarıdaki adım 1'de *app.py* başlangıç dosyası olarak ayarladığınızdan emin olun.

5. Kaynağın `localhost:4449/hello` dekoratöründe de çalıştığını test etmek için gidin. `/hello` Yine, GET isteği komut penceresinde 200 durumu ile görünür. Komut penceresinde 404 durum kodlarını gösterdiklerini görmek için başka bir URL'yi de denemeden çekinmeyin.

6. Uygulamayı durdurmak için komut penceresini kapatın ve ardından tarayıcı penceresini kapatın.

**Soru: Hata Ayıklama komutu olmadan Başlat ve Hata Ayıklama Başlat arasındaki fark nedir?**

**Cevap**: Uygulamayı Visual Studio hata ayıklayıcısı bağlamında çalıştırmak için **Başlat Hata Ayıklama'yı** kullanarak kesme noktaları ayarlamanızı, değişkenleri incelemenizi ve kod satırı satır adım atmanızı sağlarsınız. [Visual Studio debugger](../python/debugging-python-in-visual-studio.md) Hata ayıklamayı mümkün kılan çeşitli kancalar nedeniyle uygulamalar hata ayıklamada daha yavaş çalışabilir. **Hata Ayıklama olmadan başlatın**, aksine, uygulamayı komut satırından, hata ayıklama bağlamı olmadan çalıştırıyormuş gibi doğrudan çalıştırıyor ve ayrıca otomatik olarak bir tarayıcı başlatıyor ve proje özelliklerinin **Hata Ayıklama** sekmesinde belirtilen URL'ye yönlendiriyor.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio'da Python IDE olarak visual studio'u kullanmayı biraz öğrendiğiniz ilk Python uygulamanızı çalıştırdığınız için tebrikler!

> [!div class="nextstepaction"]
> [Uygulamayı Azure Uygulama Hizmetine dağıtma](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

Bu Quickstart'ta izlediğiniz adımlar oldukça genel olduğundan, bunların otomatikleştirilen ve olması gerektiğini tahmin etmişsinizdir. Bu tür otomasyon Visual Studio proje şablonlarının rolüdür. Quickstart üzerinden git - Bu makalede oluşturduğunuza benzer bir web uygulaması oluşturan bir gösteri için [şablon kullanarak bir Python projesi oluşturun,](../python/quickstart-02-python-in-visual-studio-project-from-template.md) ancak daha az adımla.

Etkileşimli pencereyi kullanma, hata ayıklama, veri görselleştirme ve Git ile çalışma dahil olmak üzere Visual Studio'da Python hakkında daha kapsamlı bir öğreticiyle devam etmek için [Tutorial: The Python in Visual Studio'da başlayın.](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

Visual Studio'nun sunduğu daha fazlasını keşfetmek için aşağıdaki bağlantıları seçin.

- Visual [Studio'da Python web uygulaması şablonları](../python/python-web-application-project-templates.md)hakkında bilgi edinin.
- Python [hata ayıklama](../python/debugging-python-in-visual-studio.md) hakkında bilgi edinin
- Genel olarak [Visual Studio IDE](../get-started/visual-studio-ide.md) hakkında daha fazla bilgi edinin.
