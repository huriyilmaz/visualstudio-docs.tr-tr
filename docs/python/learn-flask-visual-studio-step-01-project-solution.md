---
title: 1. adımda Flask Visual Studio Flask hakkında temel bilgiler öğrenme
titleSuffix: ''
description: Önkoşullar, Git ve sanal ortamlar dahil olmak Visual Studio flask temel bilgilerine yönelik kılavuz.
ms.date: 01/07/2019
ms.topic: tutorial
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 8c4a7839805ffa0d3421cac692ef92f067cce3e0
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129968468"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>Öğretici: Kullanmaya başlayın Flask web çerçevesiyle Visual Studio

[Flask,](https://palletsprojects.com/p/flask/) WEB uygulamaları için URL yönlendirme ve sayfa işleme ile ilgili temel bilgileri sağlayan basit bir Python çerçevesidir.

Flask, form doğrulama, veritabanı soyutlama, kimlik doğrulaması gibi özellikleri doğrudan sağlamayarak "mikro" çerçeve olarak adlandırılan bir çerçevedir. Bu tür özellikler bunun yerine Flask uzantıları olarak adlandırılan özel Python *paketleriyle sağlanır.* Uzantılar Flask'in kendi parçası gibi görünmesi için Flask ile sorunsuz bir şekilde tümleştirildi. Örneğin Flask'in kendisi bir sayfa şablonu altyapısı sağlamaz. Templating, bu öğreticide de olduğu gibi Jinja ve Jade gibi uzantılar tarafından sağlanır.

::: moniker range="vs-2017"
Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
- "Blank Flask Web Project" şablonunu kullanarak Git deposunda temel bir Flask projesi oluşturma (1. adım)
- Tek sayfalı bir Flask uygulaması oluşturma ve bu sayfayı şablon kullanarak işleme (2. adım)
- Statik dosyaları hizmet etme, sayfa ekleme ve şablon devralma kullanma (3. adım)
- Flask Web Project şablonunu kullanarak birden çok sayfa ve duyarlı tasarıma sahip bir uygulama oluşturma (4. adım)
- Çeşitli depolama seçenekleri (Azure depolama, MongoDB veya bellek) kullanan bir yoklama uygulaması oluşturmak için Polls Flask Web Project şablonunu kullanın.

Bu adımlar boyunca üç ayrı proje içeren tek bir Visual Studio çözüm oluşturabilirsiniz. Projeyi, proje şablonlarına dahil edilen farklı Flask proje şablonlarını Visual Studio. Projeleri aynı çözümde tutarak, karşılaştırma için farklı dosyalar arasında kolayca geçiş yapabilirsiniz.
::: moniker-end

::: moniker range=">=vs-2019"

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
- "Blank Flask Web Project" şablonunu kullanarak Git deposunda temel bir Flask projesi oluşturma (1. adım)
- Tek sayfalı bir Flask uygulaması oluşturma ve bu sayfayı şablon kullanarak işleme (2. adım)
- Statik dosyaları hizmet etme, sayfa ekleme ve şablon devralma kullanma (3. adım)
- Flask Web Project şablonunu kullanarak birden çok sayfa ve duyarlı tasarıma sahip bir uygulama oluşturma (4. adım)

Bu adımlar boyunca iki ayrı proje içeren tek bir Visual Studio çözüm oluşturabilirsiniz. Projeyi, proje şablonlarına dahil edilen farklı Flask proje şablonlarını Visual Studio. Projeleri aynı çözümde tutarak, karşılaştırma için farklı dosyalar arasında kolayca geçiş yapabilirsiniz.
::: moniker-end

> [!Note]
> Bu [öğretici, Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) hakkında daha fazla bilgi edinmek ve kendi projeleriniz için daha kapsamlı bir başlangıç noktası sağlayan farklı Flask proje şablonlarını nasıl kullanabileceğinizi öğrenmek için Flask Hızlı Başlangıç'tan farklıdır. Örneğin, proje şablonları, Hızlı Başlangıç'ta gösterildiği gibi paketi el ile yüklemeniz gerekerek değil, proje oluşturulurken Flask paketini otomatik olarak yüklenir.

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio 2017 veya sonraki Windows seçenekleriyle birlikte kullanın:
  - **Python geliştirme iş** yükü (**Yükleyicide** İş yükü sekmesi). Yönergeler için [bkz. Python desteğini Visual Studio.](installing-python-support-in-visual-studio.md)
  - **Kod araçları'Windows** GitHub **bileşenler sekmesinde Visual Studio** için Git ve **Uzantı** **uzantısını kullanın.**

Flask proje şablonları tüm önceki Visual Studio için Python Araçları dahil edilir, ancak ayrıntılar bu öğreticide ele alınanlardan farklı olabilir.

Python geliştirmesi şu anda bu Mac için Visual Studio. Mac ve Linux'ta python [uzantısını kullanarak Visual Studio Code.](https://code.visualstudio.com/docs/python/python-tutorial)

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>1-1. Adım: Visual Studio proje ve çözüm oluşturma

1. Bu Visual Studio Yeni   >    >  **Dosya'Project** seçin, "Flask" araması yazın ve **Boş Flask Web** Uygulaması şablonunu Project seçin. (Şablon Python altında da **bulunur**  >  **Sol** listede Web.)

    ![Boş Flask Web Visual Studio için yeni proje iletişim Project](media/flask/step01-new-blank-project.png)

1. İletişim kutusunun en altındaki alanlara aşağıdaki bilgileri girin (önceki grafikte gösterildiği gibi) ve tamam'ı **seçin:**

    - **Ad:** Projeniz için Visual Studio **BasicProject olarak ayarlayın.** Bu ad Flask projesi için de kullanılır.
    - **Konum:** Uygulama çözümünün ve projenin oluşturul Visual Studio bir konum belirtin.
    - **Çözüm adı:** **LearningFlask** olarak ayarlanır. Bu, bu öğreticide çözüm için birden çok proje için kapsayıcı olarak uygundur.
    - **Çözüm için dizin oluşturma:** Ayarlanmış (varsayılan) bırakın.
    - **Yeni Git deposu oluşturma:** Çözümü oluşturduğunda yerel bir Git deposu Visual Studio için bu seçeneği (varsayılan olarak açıktır) seçin. Bu seçeneği görmüyorsanız, Visual Studio yükleyicisini çalıştırın ve Kod araçları altındaki Bağımsız bileşenler sekmesinde Windows ve GitHub için  **GitHub** **Uzantısı'Visual Studio'ı ekleyin.** 

1. Bir süre sonra Visual Studio Bu proje dış paketler gerektiriyor (aşağıda gösterilmiştir) iletişim **kutusunu** size sorabilirsiniz. Şablon en son Flask 1.x *paketine* başvuran birrequirements.txtdosyası içerir. (Tam **bağımlılıkları görmek için** Gerekli paketleri göster'i seçin.)

    ![Projenin dış paketler gerektirdiğini söyleyen istem](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. Bunları ben **yükleyeceğim seçeneğini belirleyin.** Sanal ortamı kısa süre içinde oluşturarak kaynak denetiminden dışlamanız gerekir. (Ortam her zaman *requirements.txt.)*

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>1-2. Adım: Git denetimlerini inceleme ve uzak depoda yayımlama

New **Project** iletişim kutusunda **Yeni Git** deposu oluştur'Project proje, oluşturma işlemi tamamlandıktan hemen sonra yerel kaynak denetimine zaten kaydedilmiştir. Bu adımda, Visual Studio Git denetimleri ve kaynak **denetimiyle Takım Gezgini** pencere hakkında bilgi edinebilirsiniz.

1. Ana pencerenin alt köşesindeki Git denetimlerini Visual Studio. Soldan sağa doğru bu denetimler, işlenmiş olmayan işlemeleri, işlanmamış değişiklikleri, deponun adını ve geçerli dalı gösterir:

    ![Visual Studio penceresinde Git denetimleri](media/flask/step01-git-controls.png)

    > [!Note]
    > Yeni Depo oluştur iletişim kutusunda **Yeni Git**  deposu Project Git denetimleri yalnızca yerel  depo oluşturan bir Kaynak denetimine ekle komutunu gösterir.
    >
    > ![Depo oluşturmadıysanız Visual Studio Denetimine Ekle görüntülenir](media/tutorials-common/step01-git-add-to-source-control.png)

1. Değişiklikler düğmesini seçin ve Visual Studio, **Takım Gezgini** sayfasında kendi Takım Gezgini **penceresini** açar. Yeni oluşturulan proje otomatik olarak kaynak denetimine zaten bağlı olduğundan, bekleyen hiçbir değişiklik görmüyoruz.

    ![Takım Gezgini sayfasındaki Takım Gezgini penceresi](media/flask/step01-team-explorer-changes.png)

1. İlke Visual Studio çubuğunda, atlanmamış işlemeler düğmesini **(2** ile yukarı ok) seçerek eşitleme sayfasını  **Takım Gezgini.** Yalnızca yerel bir depoya sahip olduğunuz için sayfa, depoyu farklı uzak depolarda yayımlamak için kolay seçenekler sağlar.

    ![Takım Gezgini denetimi için kullanılabilir Git deposu seçeneklerini gösteren bir pencere](media/flask/step01-team-explorer.png)

    Kendi projeleriniz için istediğiniz hizmeti seçebilirsiniz. Bu öğreticide, GitHub tamamlanan örnek [kodun Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask) deposunda tutularak bulunduğu GitHub kullanımı açıklanmıştır.

1. Yayımla denetimlerden birini **seçerek** **Takım Gezgini** daha fazla bilgi isteminde bulundurabilirsiniz. Örneğin, bu öğreticinin örneğini yayımlarken önce deponun kendisi oluşturulacak ve  bu durumda deponun URL'si ile Uzak Depoya Itme seçeneği kullanılmıştır.

    ![Takım Gezgini uzak depoya itme penceresi](media/flask/step01-push-to-github.png)

    Mevcut bir depoya sahip değilsanız, GitHub'da **yayımla ve** Azure DevOps'a Azure DevOps seçenekleri doğrudan deponun içinde bir depo Visual Studio. 

1. Bu öğreticide çalışmaya devam ettiyken, değişiklikleri işlemek ve itmek için Visual Studio denetimlerini düzenli aralıklarla kullanma alışkanlık haline geliyor. Bu öğretici size uygun noktaları anımsatır.

> [!Tip]
> içinde hızla **gezinmek Takım Gezgini,** kullanılabilir sayfaların açılır  menüsünü  görmek için üst bilgi (yukarıdaki görüntülerde Değişiklikler veya Anında İtme)'yi seçin.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Soru: Bir projenin başından itibaren kaynak denetimi kullanmanın bazı avantajları nelerdir?

Cevap: Öncelikle, baştaki kaynak denetimi kullanmak, özellikle de uzak depo kullanıyorsanız projenizin düzenli bir site dışı yedeğini sağlar. Bir projenin yalnızca yerel bir dosya sisteminde korunmasından farklı olarak, kaynak denetimi tam bir değişiklik geçmişi ve tek bir dosyayı veya projenin tamamını önceki bir durumuna geri döndürmeyi de sağlar. Bu değişiklik geçmişi regresyonların (test hataları) nedeninin belirlenmesine yardımcı olur. Ayrıca, üzerine yazmaları yönetir ve çakışma çözümü sağladığından, bir proje üzerinde birden çok kişi çalışıyorsa kaynak denetimi önemlidir. Son olarak, temelde bir otomasyon biçimi olan kaynak denetimi, derlemeleri, testleri ve sürüm yönetimini otomatikleşmek için iyi ayarlar. Bu, bir proje için DevOps kullanmanın ilk adımıdır ve giriş engeli çok düşük olduğundan, başlangıçtan itibaren kaynak denetimi kullanmamanız için bir neden yoktur.

Otomasyon olarak kaynak denetimi hakkında daha fazla bilgi için, mobil uygulamalar için yazılmış olan MSDN Magazine'de web uygulamaları için yazılmış olan [The Source of Truth: The Role of Repositories in DevOps](/archive/msdn-magazine/2016/september/mobile-devops-the-source-of-truth-the-role-of-repositories-in-devops)makalesine bakın.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Soru: Yeni Visual Studio otomatik olarak işlemesini önlenebilir miyim?

Yanıt: Evet. Otomatik işlemeyi devre dışı  bırakmak için Ayarlar sayfasında **Git Genel** Takım Gezgini'ı seçin, Değişiklikleri birleştirmeden sonra varsayılan olarak işle etiketli seçeneği temizleyebilirsiniz ve   >  ardından Güncelleştir'i **seçin.** 

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>1-3. Adım: Sanal ortamı oluşturma ve kaynak denetiminden dışlama

Artık projeniz için kaynak denetimi yapılandırdınıza göre, sanal ortamı projenin gerektirdiği gerekli Flask paketlerini oluşturabilirsiniz. Ardından ortamın **Takım Gezgini** denetiminden dışlamak için Takım Gezgini'ı kullanabilirsiniz.

1. Uygulama **Çözüm Gezgini** Python Ortamları düğümüne sağ **tıklayın ve** Sanal Ortam **Ekle'yi seçin.**

    ![Sanal ortam ekle komutu Çözüm Gezgini](media/flask/step01-add-virtual-environment-command.png)

1. Sanal **Ortam Ekle iletişim** kutusu açılır ve bir iletiyle birlikte Bir sanal requirements.txt **bulunur.** Bu ileti, Visual Studio ortamı yapılandırmak için bu dosyayı kullandığını gösterir.

    ![Sanal ortam ekle iletişim kutusu ve requirements.txt ekleme](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Varsayılanları **kabul** etmek için Oluştur'a seçin. (Sanal ortamın adını istediğiniz gibi değiştirebilirsiniz. Bu, yalnızca alt klasör adını değiştirir ancak `env` standart bir kuraldır.)

1. İstendiğinde yönetici ayrıcalıklarına onay ve ardından birkaç dakika bekleyin. Visual Studio paketleri indirir ve yüklür. Flask ve bağımlılıkları için bu, 100'den fazla alt klasöre yaklaşık bin dosyanın genişletilmesi anlamına gelir. ilerlemeyi Visual Studio **çıkış** penceresinde görebilirsiniz. Beklerken, aşağıdaki soru bölümlerini izleyin. Flask [yükleme](https://flask.palletsprojects.com/en/1.0.x/installation/#installation) sayfasında (Flask.pcocoo.org) Flask 'nın bağımlılıklarından oluşan bir açıklama da görebilirsiniz.

1. Git denetimlerinde Visual Studio (durum çubuğunda), **Takım Gezgini** **değişiklikler** sayfasını açan değişiklikler göstergesini ( **99&#42;**) seçin.

    Sanal ortam yüzlerce değişikliğe göre oluşturulur, ancak siz (veya projeyi Klonladığınız herkes) her zaman ortamı *requirements.txt* yeniden oluşturabileceğinden kaynak denetimine bunlardan herhangi birini eklemeniz gerekmez.

    Sanal ortamı dışlamak için **env** klasörüne sağ tıklayın ve **Bu yerel öğeleri yoksay**' ı seçin.

    ![Kaynak denetimi değişikliklerinde sanal ortam yok sayılıyor](media/flask/step01-ignore-local-items.png)

1. Sanal ortamı dışladıktan sonra, kalan değişiklikler proje dosyası ve *. gitignore*' dir. *. Gitignore* dosyası, sanal ortam klasörü için eklenen bir giriş içerir. Bir farkı görmek için dosyaya çift tıklayabilirsiniz.

1. Bir işleme iletisi girin ve **Tümünü Kaydet** düğmesini seçin, ardından istediğiniz değişiklikleri uzak deponuza gönderin.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Soru: neden sanal ortam oluşturmak istiyorum?

Cevap: sanal bir ortam, uygulamanızın tam bağımlılıklarını yalıtmak için harika bir yoldur. Bu tür yalıtımlara genel bir Python ortamında çakışmalar önlenir ve hem test hem de işbirliği yardımcı olur. Zaman içinde, bir uygulama geliştirirken, çok sayıda faydalı Python paketini de bir araya getirebilirsiniz. Paketleri projeye özgü bir sanal ortamda tutarak, projenin kaynak denetimine dahil olan bu ortamı açıklayan *requirements.txt* dosyasını kolayca güncelleştirebilirsiniz. Proje, derleme sunucuları, dağıtım sunucuları ve diğer geliştirme bilgisayarları dahil olmak üzere başka bir bilgisayara kopyalandığında, ortamı yalnızca *requirements.txt* (ortamın kaynak denetiminde olması gerekmez) kullanarak yeniden oluşturmak kolaydır. Daha fazla bilgi için bkz. [sanal ortamları kullanma](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Soru: kaynak denetimine zaten kaydedilmiş bir sanal ortamı kaldırmak Nasıl yaparım? mı?

Cevap: Ilk olarak, klasörü hariç tutmak için *. gitignore* dosyanızı düzenleyin: ile birlikte, açıklama ile sonundaki bölümü bulun `# Python Tools for Visual Studio (PTVS)` ve sanal ortam klasörü için gibi yeni bir satır ekleyin `/BasicProject/env` . (Visual Studio dosyayı **Çözüm Gezgini** göstermediğinden, **dosyayı**  >  doğrudan kullanarak açın **Açık**  >  **Dosya** menü komutu. dosyayı **Takım Gezgini** içinden de açabilirsiniz: **Ayarlar** sayfasında **depo Ayarlar**' yı seçin, **& öznitelikleri dosyalarını yoksay** bölümüne gidin ve sonra **. gitignore**' in yanındaki **düzenle** bağlantısını seçin.

İkinci olarak, bir komut penceresi açın, *env* ve çalıştırmak gibi sanal ortam klasörünü Içeren *BasicProject* gibi bir klasöre gidin `git rm -r env` . Sonra bu değişiklikleri komut satırından ( `git commit -m 'Remove venv'` ) işleyin veya **Takım Gezgini** **değişiklikler** sayfasından işleyin.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Adım 1-4: ortak kodu Inceleme

1. Proje oluşturma işlemi tamamlandıktan sonra, projenin yalnızca iki dosya içerdiği, *app.py* ve *requirements.txt* **Çözüm Gezgini** çözüm ve projeyi görürsünüz:

    ![Çözüm Gezgini 'de boş Flask proje dosyaları](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. Daha önce belirtildiği gibi, *requirements.txt* dosyası Flask paket bağımlılığını belirtir. Bu dosyanın varlığı, projeyi ilk oluştururken sanal ortam oluşturmak için sizi davet eder.

1. Tek *app.py* dosyası üç bölümden oluşur. İlk olarak, bir `import` Flask için bir ifade, `Flask` değişkene atanan sınıfının bir örneğini oluşturma `app` ve sonra bir `wsgi_app` değişken atama (bir Web ana bilgisayarına dağıtım yaparken faydalıdır, ancak şu anda kullanılmadığında yararlı olur):

    ```python
    from flask import Flask
    app = Flask(__name__)

    # Make the WSGI interface available at the top level so wfastcgi can get it.
    wsgi_app = app.wsgi_app
    ```

1. İkinci bölüm, dosyanın sonundaki bir Flask geliştirme sunucusunu, ortam değişkenlerinden alınan belirli ana bilgisayar ve bağlantı noktası değerleriyle Başlatan bir isteğe bağlı koddur (varsayılan olarak localhost: 5555):

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

1. Üçüncü, bir URL yoluna bir işlev atayan, işlevin URL tarafından tanımlanan kaynağı sağladığı bir kod olan kısa bir bittir. `@app.route`Bağımsız değişkeni, site kökünden gelen GÖRELI URL olan Flask dekoratörü kullanarak yollar tanımlarsınız. Kodda görebileceğiniz gibi, bu işlev yalnızca bir tarayıcının işlemesi için yeterli olan bir metin dizesi döndürür. İzleyen adımlarda, HTML ile daha zengin sayfalar işleyebilirsiniz.

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-__name__-argument-to-the-flask-class"></a>Soru: Flask sınıfına __ad__ bağımsız değişkeninin amacı nedir?

Yanıt: bağımsız değişkeni, uygulamanın modülünün veya paketinin adıdır ve uygulamaya ait şablonlar, statik dosyalar ve diğer kaynakların nerede bakacağını belirtir. Tek bir modülde bulunan uygulamalar için `__name__` her zaman uygun değerdir. Hata ayıklama bilgileri gerektiren uzantılar için de önemlidir. Daha fazla bilgi ve ek bağımsız değişkenler için bkz. [Flask sınıfı belgeleri](https://flask.palletsprojects.com/en/1.0.x/api/#flask.Flask) (Flask.pocoo.org).

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>Soru: bir işlevde birden fazla yol dekoratör olabilir mi?

Cevap: Evet, aynı işlev birden çok yol için hizmet veriyorsa, istediğiniz sayıda dekoratı kullanabilirsiniz. Örneğin, `hello` "/" ve "/Hello" için işlevi kullanmak için aşağıdaki kodu kullanın:

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>Soru: nasıl Flask, değişken URL yönlendirmeleri ve sorgu parametreleriyle nasıl çalışır?

Cevap: bir rotada, ile herhangi bir değişkeni işaretlersiniz `<variable_name>` ve sonra, URL yolundaki adlandırılmış bir bağımsız değişkeni kullanarak değişkeni işlevi işleve geçirir. Örneğin, biçiminde bir yol, `/hello/<name>` işlevine çağrılan bir dize bağımsız değişkeni oluşturur `name` . Sorgu parametreleri, `request.args` özellikle yöntemi aracılığıyla özelliği aracılığıyla kullanılabilir `request.args.get` . Daha fazla bilgi için Flask belgelerindeki [istek nesnesine](https://flask.palletsprojects.com/en/1.1.x/quickstart/#the-request-object) bakın.

```python
# URL: /hello/<name>?message=Have%20a%20nice%20day
@app.route('/hello/<name>')
def hello(name):
    msg = request.args.get('message','')
    return "Hello " + name + "! "+ msg + "."
```

Türü değiştirmek için, değişkeni, `int` `float` , `path` (klasör adlarını belirtmek için eğik çizgileri kabul eder), ve ile önekini yapın `uuid` . Ayrıntılar için Flask belgelerindeki [değişken kuralları](https://flask.palletsprojects.com/en/1.0.x/quickstart/#variable-rules) bölümüne bakın.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>soru: diğer paketleri yükledikten sonra sanal ortamdan bir requirements.txt dosyası Visual Studio verebilir misiniz?

Yanıt: Evet. **Python ortamları** düğümünü genişletin, sanal ortamınıza sağ tıklayıp **requirements.txtoluştur** komutunu seçin. Ortamı değiştirirken bu komutun düzenli aralıklarla kullanılması ve bu ortama bağlı diğer kod değişiklikleriyle birlikte kaynak denetimine *requirements.txt* değişiklikler yürütmesi yararlı olur. Bir yapı sunucusunda sürekli tümleştirme ayarlarsanız, ortamı her değiştirdiğinizde dosyayı oluşturmanız ve değişiklikleri uygulamanız gerekir.

## <a name="step-1-5-run-the-project"></a>Adım 1-5: projeyi çalıştırma

1. Visual Studio **, hata**  >  **ayıklamayı başlat** (**F5**) seçeneğini belirleyin veya araç çubuğunda **Web sunucusu** düğmesini kullanın (gördüğünüz tarayıcı farklılık gösterebilir):

    ![Visual Studio Web sunucusu araç çubuğu düğmesini Çalıştır](media/tutorials-common/run-web-server-toolbar-button.png)

1. Her iki komut de bağlantı noktası ortam değişkenine rastgele bir bağlantı noktası numarası atar ve sonra çalışır `python app.py` . Kod, uygulamayı Flask geliştirme sunucusu içinde bu bağlantı noktasını kullanarak başlatır. Visual Studio **hata ayıklayıcıyı** başlatma dosyası olmayan bir iletiyle başlatmazsa, **Çözüm Gezgini** **' a sağ tıklayıp** **başlangıç dosyası olarak ayarla**' yı seçin.

1. Sunucu başlatıldığında, sunucu günlüğünü görüntüleyen bir konsol penceresi açık görürsünüz. Visual Studio, ' e otomatik olarak bir tarayıcı açar `http://localhost:<port>` , burada işlev tarafından işlenmiş iletiyi görürsünüz `hello` :

    ![Flask proje varsayılan görünümü](media/flask/step01-first-run-success.png)

1. işiniz bittiğinde, konsol penceresini kapatarak veya Visual Studio **hata**  >  **ayıklamayı durdur** komutunu kullanarak sunucuyu durdurun.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Soru: Hata Ayıkla menü komutlarının ve proje Python alt menüsünde sunucu komutlarının kullanımı arasındaki fark nedir?

Cevap: **hata ayıklama** menü komutları ve araç çubuğu düğmelerine ek olarak,   >  projenin bağlam menüsündeki Python **çalıştırma sunucusu** veya **Python**  >  **çalıştırma hata ayıklama sunucusu** komutlarını kullanarak sunucuyu da başlatabilirsiniz. Her iki komut de çalışan sunucu için yerel URL 'YI (localhost: bağlantı noktası) görebileceğiniz bir konsol penceresi açar. ancak, bu URL ile bir tarayıcıyı el ile açmanız gerekir ve hata ayıklama sunucusunu çalıştırmak Visual Studio hata ayıklayıcıyı otomatik olarak başlatmamalıdır. Çalıştırmak istiyorsanız,   >  **işlemek için** hata ayıkla komutunu kullanarak, çalışan işleme daha sonra bir hata ayıklayıcı ekleyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu noktada, temel Flask projesi aynı dosyadaki başlangıç kodunu ve sayfa kodunu içerir. Bu iki kaygıyı ayırmak ve ayrıca şablonlar kullanarak HTML ve verileri ayırmak için idealdir.

> [!div class="nextstepaction"]
> [Görünümler ve sayfa şablonlarıyla Flask uygulaması oluşturma](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>Daha derin git

- [Flask hızlı başlangıç](https://flask.palletsprojects.com/en/1.0.x/quickstart/) (Flask.pocoo.org)
- GitHub eğitim kaynak kodu: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)