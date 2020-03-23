---
title: Visual Studio adım 1, Flask temelleri Flask öğretici öğrenin
titleSuffix: ''
description: Önkoşullar, Git ve sanal ortamlar da dahil olmak üzere Visual Studio projeleri bağlamında Flask temellerinin bir walkthrough.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7707d993ac5fb6f73060d0f862c828e67c833872
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79302849"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>Öğretici: Visual Studio Flask web çerçevesi ile başlayın

[Flask,](https://palletsprojects.com/p/flask/) URL yönlendirme ve sayfa oluşturma temellerini sağlayan web uygulamaları için hafif bir Python çerçevesidir.

Doğrudan form doğrulama, veritabanı soyutlama, kimlik doğrulama ve benzeri gibi özellikler sağlamadığından, flask "mikro" çerçeve olarak adlandırılır. Bu tür özellikler bunun yerine Flask *uzantıları*olarak adlandırılan özel Python paketleri tarafından sağlanmaktadır. Uzantılar Flask ile sorunsuz bir şekilde entegre olur, böylece Flask'ın bir parçası yatmaktadırlar. Örneğin, Flask kendisi bir sayfa şablonu altyapısı sağlamaz. Templating Jinja ve Jade gibi uzantıları tarafından sağlanmaktadır, bu öğretici gösterildiği gibi.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:

> [!div class="checklist"]
> - "Boş Flask Web Project" şablonu (adım 1) kullanarak Git deposunda temel bir Flask projesi oluşturun
> - Tek sayfalı bir Flask uygulaması oluşturun ve bu sayfayı şablon kullanarak işleme (adım 2)
> - Statik dosyalara hizmet, sayfa ekleme ve şablon kalıtımını kullanma (adım 3)
> - Birden fazla sayfaya ve duyarlı tasarıma sahip bir uygulama oluşturmak için Flask Web Project şablonuna bakın (adım 4)
> - Çeşitli depolama seçenekleri (Azure depolama, MongoDB veya bellek) kullanan bir yoklama uygulaması oluşturmak için Polls Flask Web Project şablonuna bakın.

Bu adımlar boyunca üç ayrı proje içeren tek bir Visual Studio çözümü oluşturursunuz. Visual Studio ile birlikte farklı Flask proje şablonları kullanarak proje oluşturun. Projeleri aynı çözümde tutarak, karşılaştırma için farklı dosyalar arasında kolayca geçiş yapabilirsiniz.

> [!Note]
> Bu öğretici, Flask hakkında daha fazla bilgi edinmeniz ve kendi projeleriniz için daha kapsamlı bir başlangıç noktası sağlayan farklı Flask proje şablonlarını nasıl kullanacağınız açısından [Flask Quickstart'tan](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) farklıdır. Örneğin, proje şablonları, paketi Quickstart'ta gösterildiği gibi el ile yüklemenize gerek yerine, proje oluştururken Flask paketini otomatik olarak yükler.

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio 2017 veya daha sonra Windows'da aşağıdaki seçeneklerle:
  - **Python geliştirme** iş yükü (Yükleyicideki**iş yükü** sekmesi). Talimatlar için Visual [Studio'da Python desteğini yükleyin'](installing-python-support-in-visual-studio.md)e bakın.
  - **Kod araçları**altında **Tek tek bileşenler** sekmesinde Visual Studio için Windows ve **GitHub Uzantısı** için **Git.**

Flask proje şablonları Visual Studio için Python Tools'un önceki tüm sürümleriyle birlikte verilir, ancak ayrıntılar bu öğreticide tartışılandan farklı olabilir.

Python geliştirme şu anda Visual Studio for Mac'te desteklenmez. Mac ve [Linux'ta Visual Studio Code'daki Python uzantısını](https://code.visualstudio.com/docs/python/python-tutorial)kullanın.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Adım 1-1: Visual Studio projesi ve çözümü oluşturun

1. Visual Studio'da **Dosya** > **Yeni** > **Projesi'ni**seçin, "Flask"ı arayın ve **Boş Flask Web Project** şablonunu seçin. (Şablon, sol listede **Python** > **Web** altında da bulunur.)

    ![Blank Flask Web Project için Visual Studio'da yeni proje iletişim kutusu](media/flask/step01-new-blank-project.png)

1. İletişim kutusunun altındaki alanlara aşağıdaki bilgileri girin (önceki grafikte gösterildiği gibi), **tamam'ı**seçin:

    - **Adı**: Visual Studio projesinin adını **BasicProject**olarak ayarlayın. Bu ad flask projesi için de kullanılır.
    - **Konum**: Visual Studio çözüm ve proje oluşturmak için bir konum belirtin.
    - **Çözüm adı**: Bu öğretici birden fazla proje için bir konteyner olarak çözüm için uygun olan **LearningFlask**ayarlayın.
    - **Çözüm için dizin oluşturma**: Set (varsayılan) bırak.
    - **Yeni Git deposu oluşturun**: Visual Studio'nun çözümü oluşturduğunda yerel bir Git deposu oluşturması için bu seçeneği (varsayılan olarak açık) seçin. Bu seçeneği görmüyorsanız, Visual Studio yükleyicisini çalıştırın ve **Kod araçları**altında **Tek tek bileşenler** sekmesine Windows için Git ve Visual Studio **için** **Git'i** ekleyin.

1. Bir süre sonra, Visual Studio **bu projenin dış paketler gerektirdiğini** belirten bir iletişim kutusu yla sizi ister (aşağıda gösterilmiştir). Şablon en son Flask 1.x paketine atıfta bulunan bir *requirements.txt* dosyası içerdiğinden bu iletişim kutusu görüntülenir. (Tam bağımlılıkları görmek için **gerekli paketleri göster'i** seçin.)

    ![Projenin dış paketler gerektirdiğini belirten komut istemi](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. **Ben onları kendim yükleyeceğim**seçeneğini seçin. Kaynak denetiminin dışında olduğundan emin olmak için kısa süre içinde sanal ortamı oluşturursunuz. (Ortam her zaman *requirements.txt*oluşturulabilir.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Adım 1-2: Git denetimlerini inceleyin ve uzak bir depoda yayımlayın

**Yeni Proje** iletişim kutusunda yeni Git **deposu oluştur'u** seçtiğiniziçin, oluşturma işlemi tamamlanır tamamlanmaz proje zaten yerel kaynak denetimine adanmıştır. Bu adımda, Visual Studio'nun Git denetimlerini ve kaynak denetimiyle çalıştığınız **Team Explorer** penceresini tanıtAbilirsiniz.

1. Visual Studio ana penceresinin alt köşesindeki Git denetimlerini inceleyin. Soldan sağa, bu denetimler itilmemiş taahhütleri, işlenmemiş değişiklikleri, deponun adını ve geçerli dalı gösterir:

    ![Visual Studio penceresinde git denetimleri](media/flask/step01-git-controls.png)

    > [!Note]
    > **Yeni Proje** iletişim kutusunda **yeni Git deposu oluştur'u** seçmezseniz, Git denetimleri yalnızca yerel bir depo oluşturan kaynak **denetimine ekle** komutunu gösterir.
    >
    > ![Kaynak Denetimine Ekle, bir depo oluşturmadıysanız Visual Studio'da görünür](media/tutorials-common/step01-git-add-to-source-control.png)

1. Değişiklikler düğmesini seçin ve Visual Studio **Değişiklikler** sayfasında **Team Explorer** penceresini açar. Yeni oluşturulan proje zaten kaynak denetimine otomatik olarak bağlı olduğundan, bekleyen değişiklikleri görmezsiniz.

    ![Değişiklikler sayfasında Kiteam Gezgini penceresi](media/flask/step01-team-explorer-changes.png)

1. Visual Studio durum çubuğunda, Takım Gezgini'nde **Eşitleme** sayfasını açmak için itilmemiş **Team Explorer**commits düğmesini **(2**ile yukarı ok) seçin. Yalnızca yerel bir deponuz olduğundan, sayfa depoyu farklı uzak depolara yayımlamak için kolay seçenekler sağlar.

    ![Kaynak denetimi için kullanılabilir Git deposu seçeneklerini gösteren Takım Gezgini penceresi](media/flask/step01-team-explorer.png)

    Kendi projeleriniz için istediğiniz hizmeti seçebilirsiniz. Bu öğretici, öğretici için tamamlanan örnek kodun [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask) deposunda muhafaza edildiği GitHub kullanımını gösterir.

1. **Yayımlama** denetimlerinden birini seçerken, **Takım Gezgini** daha fazla bilgi için sizden istenir. Örneğin, bu öğretici için örnek yayımlarken, önce deponun kendisinin oluşturulması gerekir, bu durumda deponun URL'si ile **Uzak Depoya Push** seçeneği kullanılmıştır.

    ![Varolan bir uzak depoya itmek için Takım Gezgini penceresi](media/flask/step01-push-to-github.png)

    Varolan bir deponuz yoksa, **GitHub'a Yayımla** ve **Azure DevOps'e Itme** seçenekleri doğrudan Visual Studio içinden bir depo oluşturmanıza izin vermez.

1. Bu öğretici ile çalışırken, değişiklikleri işlemek ve itmek için Visual Studio'daki denetimleri periyodik olarak kullanma alışkanlığı edinin. Bu öğretici size uygun noktalarda hatırlatıyor.

> [!Tip]
> **Ekip Gezgini**içinde hızla gezinmek için, kullanılabilir sayfaların açılır menüsünü görmek için üstbilgi (yukarıdaki resimlerde **Değişiklikleri** veya **İde'** i okuyan) üstbilgiyi seçin.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Soru: Bir projenin başlangıcından itibaren kaynak denetimi kullanmanın bazı avantajları nelerdir?

Cevap: Her şeyden önce, kaynak denetimini baştan kullanarak, özellikle uzaktan bir depo kullanıyorsanız, projenizin düzenli bir şirket dışı yedeklemesini sağlar. Yalnızca yerel bir dosya sisteminde bir projeyi sürdürmenin aksine, kaynak denetimi aynı zamanda tam bir değişiklik geçmişi ve tek bir dosyayı veya tüm projeyi önceki duruma geri çevirme kolay bir şekilde sağlar. Bu değişiklik geçmişi gerilemelerin (test hataları) nedenini belirlemeye yardımcı olur. Ayrıca, birden çok kişi bir proje üzerinde çalışıyorsa, kaynak denetimi, üzerine yazılar yönetir ve çakışma çözümü sağlar esastır. Son olarak, temelde bir otomasyon biçimi olan kaynak denetimi, yapı, test ve sürüm yönetimini otomatikleştirmek için sizi iyi ayarlar. Bu gerçekten bir proje için DevOps kullanarak ilk adım, ve giriş engelleri çok düşük olduğundan, gerçekten başından itibaren kaynak kontrolü kullanmamak için hiçbir neden yoktur.

Otomasyon olarak kaynak kontrolü hakkında daha fazla tartışma için, the [Source of Truth: The Role of Positories in DevOps](https://msdn.microsoft.com/magazine/mt763232)( MSDN Magazine dergisinde web uygulamaları için de geçerli olan mobil uygulamalar için yazılmış bir makale) başlıklı makaleye bakın.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Soru: Visual Studio'nun yeni bir projeyi otomatik olarak gerçekleştirmesini engelleyebilir miyim?

Cevap: Evet. Otomatik commit devre dışı kalmak için, **Team** **Explorer'da Ayarlar** sayfasına gidin , **Git** > **Global ayarlarını**seçin, **varsayılan olarak birleştirdikten sonra değişiklikleri gerçekleştir**seçeneğini temizleyin, ardından **Güncelleştir'i**seçin.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Adım 1-3: Sanal ortamı oluşturun ve kaynak denetiminden hariç tutun

Artık projeniz için kaynak denetimini yapılandırdığınıza göre, sanal ortamı projenin gerektirdiği gerekli Flask paketlerini oluşturabilirsiniz. Daha **sonra,** çevre klasörünü kaynak denetiminden dışlamak için Team Explorer'ı kullanabilirsiniz.

1. **Çözüm Gezgini'nde** **Python Ortamları** düğümüne sağ tıklayın ve Sanal Ortam **Ekle'yi**seçin.

    ![Solution Explorer'da Sanal ortam komutu ekleme](media/flask/step01-add-virtual-environment-command.png)

1. **Bir Virtual Environment Ekle** iletişim kutusu görüntülenir ve bir ileti ile **gereksinimlerin bir dosyaolduğunu söyleriz.txt dosyası.** Bu ileti, Visual Studio'nun sanal ortamı yapılandırmak için bu dosyayı kullandığını gösterir.

    ![requirements.txt iletisi ile sanal ortam iletişim kutusu ekleme](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Varsayılanları kabul etmek için **Oluştur'u** seçin. (İsterseniz sanal ortamın adını değiştirebilirsiniz, bu da alt klasörünün adını `env` değiştirir, ancak standart bir kuraldır.)

1. İstenirse yönetici ayrıcalıklarına izin verin, visual studio paketleri indirirken ve yüklerken birkaç dakika sabırlı olun, bu da Flask ve bağımlılıkları için 100'den fazla alt klasörde yaklaşık bin dosyanın genişletilmesi anlamına gelir. Visual Studio **Çıktı** penceresinde ilerlemeyi görebilirsiniz. Beklerken, takip eden Soru bölümlerini düşün. [Flask'ın Flask yükleme](https://flask.palletsprojects.com/en/1.0.x/installation/#installation) sayfasındaki (flask.pcocoo.org) bağımlılıklarının açıklamasını da görebilirsiniz.

1. Visual Studio Git denetimlerinde (durum çubuğunda), **Team Explorer'da** **Değişiklikler** sayfasını açan değişiklik göstergesini **(&#42;99'u **gösterir) seçin.

    Yüzlerce değişiklik getiren sanal ortamı oluşturmak, ancak siz (veya projeyi klonlayan herhangi bir kişi) her zaman *gereksinimleri.txt*çevreyi yeniden oluşturabilirsiniz, çünkü kaynak denetimine herhangi birini eklemeniz gerekmez.

    Sanal ortamı dışlamak için **env** klasörünü sağ tıklatın ve **bu yerel öğeleri yoksay'ı**seçin.

    ![Kaynak denetimi değişikliklerinde sanal ortamı yoksayma](media/flask/step01-ignore-local-items.png)

1. Sanal ortamı dışladıktan sonra, geriye kalan tek değişiklik proje dosyasında ve *.gitignore'dedir.* *.gitignore* dosyası, sanal ortam klasörü için ek bir giriş içerir. Diff görmek için dosyayı çift tıklatabilirsiniz.

1. İletiyi girin ve **Tümünü İşle** düğmesini seçin, ardından isterseniz iletileri uzaktan deponuza basın.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Soru: Neden sanal bir ortam oluşturmak istiyorum?

Yanıt: Sanal ortam, uygulamanızın tam bağımlılıklarını yalıtmak için harika bir yoldur. Bu tür yalıtım, küresel Python ortamındaki çakışmaları önler ve hem test hem de işbirliğine yardımcı olur. Zaman içinde, bir uygulama geliştirdikçe, her zaman birçok yararlı Python paketi getirirsiniz. Paketleri projeye özgü bir sanal ortamda tutarak, kaynak denetimine dahil edilen ortamı açıklayan projenin *gereksinimleri.txt* dosyasını kolayca güncelleştirebilirsiniz. Proje, yapı sunucuları, dağıtım sunucuları ve diğer geliştirme bilgisayarları da dahil olmak üzere diğer bilgisayarlara kopyalandığında, yalnızca *gereksinimleri.txt* kullanarak ortamı yeniden oluşturmak kolaydır (bu nedenle ortamın kaynak denetiminde olması gerekmez). Daha fazla bilgi için [bkz.](selecting-a-python-environment-for-a-project.md#use-virtual-environments)

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Soru: Kaynak denetimine adanmış bir sanal ortamı nasıl kaldıracağım?

Cevap: İlk olarak, klasörü hariç tutmak için *.gitignore* dosyanızı düzenleyin: açıklama `# Python Tools for Visual Studio (PTVS)` ile sonunda bölümü bulmak `/BasicProject/env`ve sanal ortam klasörü için yeni bir satır ekleyin, gibi . (Visual Studio **dosyayı Solution Explorer'da**göstermediği için **File** > **Dosyayı Aç** > **File** menüsü komutunu kullanarak doğrudan açın. Ayrıca **Takım Gezgini'nden**dosyayı açabilirsiniz: **Ayarlar** **sayfasında, Ayarlar Ayarlarını**seçin, Dosyaları **Yoksay &** bölümüne gidin, ardından **.gitignore'in**yanındaki **Edit** bağlantısını seçebilirsiniz .)

İkinci olarak, bir komut penceresi açın, *env*gibi sanal ortam klasörü içeren `git rm -r env` *BasicProject* gibi klasöre gidin ve çalıştırın . Ardından bu değişiklikleri komut satırından (`git commit -m 'Remove venv'`) veya **Team Explorer'ın** **Değişiklikler** sayfasından gerçekleştirin.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Adım 1-4: Ortak plaka kodunu inceleyin

1. Proje oluşturma tamamlandıktan sonra, çözüm ve proje **Çözüm Explorer,** proje sadece iki dosya, *app.py* ve *requirements.txt*içerir bakın:

    ![Solution Explorer'da Boş Flask proje dosyaları](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. Daha önce belirtildiği gibi, *requirements.txt* dosyası Flask paket bağımlılığını belirtir. Bu dosyanın varlığı, projeyi ilk oluştururken sizi sanal bir ortam oluşturmaya davet eden şeydir.

1. Tek *app.py* dosyası üç bölümden oluşur. İlk flask `import` için bir deyimdir, `Flask` değişkene `app`atanan sınıfın bir örneğini oluşturmak `wsgi_app` ve sonra bir değişken atamak (bir web ana bilgisayara dağıtılırken kullanışlıdır, ancak şu anda kullanılmaz):

    ```python
    from flask import Flask
    app = Flask(__name__)

    # Make the WSGI interface available at the top level so wfastcgi can get it.
    wsgi_app = app.wsgi_app
    ```

1. İkinci bölüm, dosyanın sonunda, ortam değişkenlerinden alınan belirli ana bilgisayar ve bağlantı noktası değerleri ile Flask geliştirme sunucusunu başlatan isteğe bağlı kod biraz (localhost:5555 varsayılan):

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. Üçüncü, işlevin URL tarafından tanımlanan kaynağı sağladığı anlamına gelen bir işlevi URL rotasına atayan kısa bir kod bitidir. Bağımsız değişkeni site kökünden göreli URL olan Flask'ın `@app.route` dekoratörü kullanarak yolları tanımlarsınız. Kodda gördüğünüz gibi, buradaki işlev yalnızca bir tarayıcının işlemesi için yeterli olan bir metin dizesini döndürür. Takip eden adımlarda HTML ile daha zengin sayfaları işleyebilirsiniz.

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-__name__-argument-to-the-flask-class"></a>Soru: Flask sınıfına __isim__ bağımsız değişkeninin amacı nedir?

Yanıt: Bağımsız değişken, uygulamanın modülünün veya paketinin adıdır ve Flask'a şablonları, statik dosyaları ve uygulamaya ait diğer kaynakları nerede arayacağını söyler. Tek bir modülde bulunan `__name__` uygulamalar için her zaman uygun değerdir. Hata ayıklama bilgisi ne ihtiyaç duyan uzantılar için de önemlidir. Daha fazla bilgi ve ek bağımsız değişkenler için [Flask sınıfı belgelerine](https://flask.palletsprojects.com/en/1.0.x/api/#flask.Flask) (flask.pocoo.org) bakın.

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>Soru: Bir işlevin birden fazla rota dekoratörü olabilir mi?

Cevap: Evet, aynı işlev birden çok rotaya hizmet veriyorsa istediğiniz kadar dekoratör kullanabilirsiniz. Örneğin, hem "/" hem de "/hello" `hello` işlevini kullanmak için aşağıdaki kodu kullanın:

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>Soru: Flask değişken URL rotaları ve sorgu parametreleri ile nasıl çalışır?

Cevap: Bir rotada, herhangi `<variable_name>`bir değişkeni işaretlersiniz ve Flask değişkeni adlandırılmış bir bağımsız değişken kullanarak işleve geçirir. Değişken URL yolunun bir parçası veya sorgu parametresi olabilir. Örneğin, işlev `'/hello/<name>` için çağrılan `name` bir dize bağımsız değişkeni oluşturur `?message=<msg>` ve rotada kullanmak "ileti=" sorgu parametresi için verilen değeri `msg`ayrıştırır ve işlevine şöyle aktarır:

```python
@app.route('/hello/<name>?message=<msg>')
def hello(name, msg):
    return "Hello " + name + "! Message is " + msg + "."
```

Türü değiştirmek için, değişkeni `int`, `float` `path` , , (klasör adlarını değiştirmek için kesikleri kabul eden) ile önek ve `uuid`. Ayrıntılar için Flask belgelerindeki [Değişken kurallarına](https://flask.palletsprojects.com/en/1.0.x/quickstart/#variable-rules) bakın.

Sorgu parametreleri, özellikle `request.args` `request.args.get` yöntem aracılığıyla özellik aracılığıyla da kullanılabilir. Daha fazla bilgi için Flask belgelerindeki İstek nesnesi'ne bakın. [The Request object](https://flask.palletsprojects.com/en/1.0.x/quickstart/#the-request-object)

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Soru: Visual Studio diğer paketleri yükledikten sonra sanal ortamdan bir requirements.txt dosyası oluşturabilir mi?

Cevap: Evet. Python **Ortamları** düğümünü genişletin, sanal ortamınıza sağ tıklayın ve **requirements.txt oluştur** komutunu seçin. Ortamı değiştirirken bu komutu düzenli aralıklarla kullanmak ve *gereksinimler.txt'de* bu ortama bağlı diğer kod değişiklikleriyle birlikte kaynak denetimine değişiklikler yapmak iyidir. Bir yapı sunucusunda sürekli tümleştirme ayarlarsanız, dosyayı oluşturmalı ve ortamı her değiştirdiğinizde değişiklikler gerçekleştirmeniz gerekir.

## <a name="step-1-5-run-the-project"></a>Adım 1-5: Projeyi çalıştırın

1. Visual Studio'da **Hata** > **Ayıklama Başlatma Hata Ayıklama** **(F5)** seçeneğini belirleyin veya araç çubuğundaki **Web Sunucusu** düğmesini kullanın (gördüğünüz tarayıcı değişebilir):

    ![Visual Studio'da web sunucusu araç çubuğu düğmesini çalıştırın](media/tutorials-common/run-web-server-toolbar-button.png)

1. Ya komut, PORT ortamı değişkenine rasgele bir `python app.py`bağlantı noktası numarası atar, sonra çalışır. Kod, flask'ın geliştirme sunucusundaki bağlantı noktasını kullanarak uygulamayı başlatır. Visual Studio, başlangıç dosyası olmamasıyla ilgili bir iletiyle **hata ayıklamaya başlayamadığını** söylüyorsa, **Solution Explorer'da** **app.py** sağ tıklayın ve Başlangıç Dosyası **olarak ayarla'yı**seçin.

1. Sunucu başlatıldığında, sunucu günlüğünü görüntüleyen bir konsol penceresinin açık olduğunu görürsünüz. Visual Studio daha sonra otomatik `http://localhost:<port>`olarak bir tarayıcıyı , `hello` işlev tarafından işlenen iletiyi görmeniz gereken yere açar:

    ![Flask proje varsayılan görünümü](media/flask/step01-first-run-success.png)

1. İşlem bittiğinde, konsol penceresini kapatarak veya Visual Studio'daki **Hata** > **Ayıklama Hata Ayıklama** Komutunu kullanarak sunucuyu durdurun.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Soru: Hata Ayıklama menüsü komutlarını kullanmakla projenin Python alt menüsündeki sunucu komutlarını kullanmak arasındaki fark nedir?

Cevap: **Hata Ayıklama** menü komutları ve araç çubuğu düğmelerine ek olarak, projenin bağlam menüsündeki **Python** > **Run sunucusu** veya **Python** > **Run hata ayıklama sunucu** komutlarını kullanarak sunucuyu başlatabilirsiniz. Her iki komut da çalışan sunucunun yerel URL'sini (localhost:port) gördüğünüz bir konsol penceresi açar. Ancak, bu URL'ye sahip bir tarayıcıyı el ile açmanız gerekir ve hata ayıklama sunucusunu çalıştırmak Visual Studio hata ayıklamasını otomatik olarak başlatmaz. **Hata** Ayıklama Komutunu kullanarak, isterseniz, daha sonra çalışan işleme **hata** > ayıklama ekleyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu noktada, temel Flask projesi aynı dosyada başlangıç kodu ve sayfa kodu içerir. Bu iki endişeyi ayırmak ve şablonları kullanarak HTML ve verileri ayırmak en iyisidir.

> [!div class="nextstepaction"]
> [Görünümler ve sayfa şablonları içeren bir Flask uygulaması oluşturma](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>Daha derine inin

- [Şişe Quickstart](https://flask.palletsprojects.com/en/1.0.x/quickstart/) (flask.pocoo.org)
- GitHub'da Öğretici kaynak kodu: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
