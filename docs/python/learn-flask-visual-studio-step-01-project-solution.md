---
title: 1. adımda Flask Visual Studio Flask hakkında temel bilgiler öğrenme
titleSuffix: ''
description: Önkoşullar, Git ve sanal ortamlar dahil olmak Visual Studio flask temel bilgilerine yönelik kılavuz.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 528471301c1de6d44d5de6464fa24c81f13b8b36
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054515"
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
  - **Kod araçları'Windows** GitHub **bileşenler sekmesinde Visual Studio** için Git ve uzantı **uzantısı.** 

Flask proje şablonları tüm önceki Visual Studio için Python Araçları dahil edilir ancak ayrıntılar bu öğreticide ele alınanlardan farklı olabilir.

Python geliştirmesi şu anda bu Mac için Visual Studio. Mac ve Linux'ta python [uzantısını kullanarak Visual Studio Code.](https://code.visualstudio.com/docs/python/python-tutorial)

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>1-1. Adım: Visual Studio proje ve çözüm oluşturma

1. Bu Visual Studio Yeni   >    >  **Dosya'Project** seçin, "Flask" araması yazın ve **Boş Flask Web** Project seçin. (Şablon Python altında da **bulunur**  >  **Sol** listede Web.)

    ![Boş Flask Web Visual Studio için yeni proje iletişim Project](media/flask/step01-new-blank-project.png)

1. İletişim kutusunun altındaki alanlara aşağıdaki bilgileri girin (önceki grafikte gösterildiği gibi) ve tamam'ı **seçin:**

    - **Ad:** Projeniz için Visual Studio **BasicProject olarak ayarlayın.** Bu ad Flask projesi için de kullanılır.
    - **Konum:** Uygulama çözümünün ve projesinin oluşturul Visual Studio bir konum belirtin.
    - **Çözüm adı:** **LearningFlask** olarak ayarlanır. Bu, bu öğreticide çözüm için birden çok proje için kapsayıcı olarak uygundur.
    - **Çözüm için dizin oluşturma:** Ayarlanmış (varsayılan) bırakın.
    - **Yeni Git deposu oluşturma:** Çözümü oluşturduğunda yerel bir Git deposu Visual Studio için bu seçeneği (varsayılan olarak açıktır) seçin. Bu seçeneği görmüyorsanız, Visual Studio yükleyicisini çalıştırın ve Kod araçları altındaki Bağımsız bileşenler sekmesinde Windows ve GitHub için  **Visual Studio** Uzantısı'Visual Studio **Git'i** **ekleyin.**

1. Bir süre sonra Visual Studio Bu proje dış paketler gerektiriyor (aşağıda gösterilmiştir) iletişim **kutusunu** size sorabilirsiniz. Şablonda en son Flask 1.x *paketine* başvuran birrequirements.txtdosyası olduğundan bu iletişim kutusu görüntülenir. (Tam **bağımlılıkları görmek için** Gerekli paketleri göster'i seçin.)

    ![Projenin dış paketler gerektirdiğini söyleyen istem](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. Bunları ben **yükleyeceğim seçeneğini belirleyin.** Sanal ortamı kısa süre içinde oluşturarak kaynak denetiminden dışlanmış olduğundan emin olun. (Ortam her zaman *requirements.txt.)*

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>1-2. Adım: Git denetimlerini inceleme ve uzak depoda yayımlama

New **Project** iletişim kutusunda **Yeni Git** deposu oluştur'Project proje, oluşturma işlemi tamamlandıktan hemen sonra yerel kaynak denetimine zaten kaydedilmiştir. Bu adımda, Visual Studio Git denetimlerini ve kaynak **denetimiyle Takım Gezgini** pencereyi tanımanız gerekir.

1. Ana pencerenin alt köşesindeki Git denetimlerini Visual Studio. Soldan sağa doğru bu denetimler, işlenmiş olmayan işlemeleri, işlanmamış değişiklikleri, deponun adını ve geçerli dalı gösterir:

    ![Visual Studio penceresinde Git denetimleri](media/flask/step01-git-controls.png)

    > [!Note]
    > Yeni Depo oluştur iletişim kutusunda **Yeni Git** deposu oluştur **Project** Git denetimleri yalnızca yerel  depo oluşturan bir Kaynak denetimine ekle komutunu gösterir.
    >
    > ![Depo oluşturmadıysanız kaynak Visual Studio Denetimine Ekle görüntülenir](media/tutorials-common/step01-git-add-to-source-control.png)

1. Değişiklikler düğmesini seçin ve Visual Studio açılan **Takım Gezgini** penceresinden **seçim** yapın. Yeni oluşturulan proje otomatik olarak kaynak denetimine zaten bağlı olduğundan, bekleyen hiçbir değişiklik görmüyoruz.

    ![Takım Gezgini sayfasındaki Takım Gezgini penceresi](media/flask/step01-team-explorer-changes.png)

1. İlke Visual Studio çubuğunda, atlanmamış işlemeler düğmesini **(2** ile yukarı ok)  seçerek eşitleme sayfasını **Takım Gezgini.** Yalnızca yerel bir depoya sahip olduğunuz için sayfa, depoyu farklı uzak depolarda yayımlamak için kolay seçenekler sağlar.

    ![Takım Gezgini denetimi için kullanılabilir Git deposu seçeneklerini gösteren bir pencere](media/flask/step01-team-explorer.png)

    Kendi projeleriniz için istediğiniz hizmeti seçebilirsiniz. Bu öğreticide, GitHub tamamlanan örnek [kodun Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask) deposunda tutularak bulunduğu GitHub kullanımı açıklanmıştır.

1. Yayımla denetimlerden birini **seçerek** **Takım Gezgini** daha fazla bilgi isteminde bulundurabilirsiniz. Örneğin, bu öğreticinin örneğini yayımlarken önce deponun kendisi oluşturulacak ve  bu durumda deponun URL'si ile Uzak Depoya Itme seçeneği kullanılmıştır.

    ![Takım Gezgini uzak depoya itmeye uygun bir pencere](media/flask/step01-push-to-github.png)

    Mevcut bir depoya sahip değilsanız, **GitHub'da yayımla ve** Azure DevOps'a Azure DevOps seçenekleri doğrudan deponun içinde bir depo Visual Studio. 

1. Bu öğreticide çalışmaya devam ettiyken, değişiklikleri işlemek ve itmek için Visual Studio denetimlerini düzenli aralıklarla kullanma alışkanlık haline geliyor. Bu öğretici size uygun noktaları anımsatır.

> [!Tip]
> içinde hızla **gezinmek Takım Gezgini,** kullanılabilir sayfaların açılır  menüsünü  görmek için üst bilgi (yukarıdaki görüntülerde Değişiklikler veya Anında İtme'yi okur) seçin.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Soru: Projenin başından itibaren kaynak denetimi kullanmanın bazı avantajları nelerdir?

Cevap: Öncelikle, baştaki kaynak denetimi kullanmak, özellikle de uzak depo kullanıyorsanız projenizin düzenli bir site dışı yedeğini sağlar. Bir projenin yalnızca yerel dosya sisteminde korunmasından farklı olarak, kaynak denetimi tam bir değişiklik geçmişi ve tek bir dosyayı veya projenin tamamını önceki bir durumuna geri döndürmeyi de sağlar. Bu değişiklik geçmişi regresyonların (test hataları) nedeninin belirlenmesine yardımcı olur. Ayrıca, bir proje üzerinde birden çok kişi çalışıyorsa, üzerine yazmayı yönetir ve çakışma çözümü sağladığından kaynak denetimi temel öneme sahip olur. Son olarak, temelde bir otomasyon biçimi olan kaynak denetimi, derlemeleri, testleri ve sürüm yönetimini otomatikleşmek için iyi ayarlar. Bu, bir proje için DevOps kullanmanın ilk adımıdır ve giriş engeli çok düşük olduğundan, başlangıçtan itibaren kaynak denetimi kullanmamanız için bir neden yoktur.

Otomasyon olarak kaynak denetimi hakkında daha fazla bilgi için, mobil uygulamalar için yazılmış olan MSDN Magazine makalesi olan The [Source of Truth: The Role of Repositories in DevOps](/archive/msdn-magazine/2016/september/mobile-devops-the-source-of-truth-the-role-of-repositories-in-devops)(Web uygulamaları için de geçerlidir) makalesine bakın.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Soru: Yeni Visual Studio otomatik olarak işlemesini önlenebilir miyim?

Yanıt: Evet. Otomatik işlemeyi devre dışı  bırakmak için Ayarlar sayfasında **Git Genel** ayarları'Takım Gezgini gidin, Değişiklikleri varsayılan olarak birleştirmeden sonra işle etiketli seçeneğin temizlemesini ve ardından  >  Güncelleştir'i **seçin.** 

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>1-3. Adım: Sanal ortamı oluşturma ve kaynak denetiminden dışlama

Artık projeniz için kaynak denetimi yapılandırdınıza göre, sanal ortamı projenin gerektirdiği gerekli Flask paketlerini oluşturabilirsiniz. Daha sonra **ortamın Takım Gezgini** denetiminden dışlamak için Takım Gezgini'i kullanabilirsiniz.

1. Bu **Çözüm Gezgini** Python Ortamları düğümüne sağ **tıklayın ve** Sanal Ortam **Ekle'yi seçin.**

    ![Sanal ortam ekle komutu Çözüm Gezgini](media/flask/step01-add-virtual-environment-command.png)

1. Sanal **Ortam Ekle iletişim** kutusu açılır ve bir iletiyle birlikte Bir sanal requirements.txt **bulunur.** Bu ileti, Visual Studio ortamı yapılandırmak için bu dosyayı kullandığını gösterir.

    ![Sanal ortam ekleme iletisiyle requirements.txt iletişim kutusu](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Varsayılan **değerleri kabul** etmek için Oluştur'a seçin. (Sanal ortamın adını istediğiniz gibi değiştirebilirsiniz. Bu, yalnızca alt klasör adını değiştirir ancak `env` standart bir kuraldır.)

1. İstendiğinde yönetici ayrıcalıklarına onay ve ardından birkaç dakika bekleyin Visual Studio paketleri indirir ve yüklür. Flask ve bağımlılıkları için bu, 100'den fazla alt klasöre yaklaşık bin dosyanın genişletilmesi anlamına gelir. İlerlemeyi Çıkış penceresinde Visual Studio **görebilirsiniz.** Beklerken, aşağıdaki Soru bölümlerine daha fazla bakın. Flask'in bağımlılıklarının açıklamasını [Flask](https://flask.palletsprojects.com/en/1.0.x/installation/#installation) yükleme sayfasında da görebilirsiniz (flask.pcocoo.org).

1. Git Visual Studio (durum çubuğunda), değişiklikler sayfasını Takım Gezgini'da açan değişiklik göstergesini **(99**&#42;)  **seçin.**

    Sanal ortamın oluşturulması yüzlerce değişiklikle getirildi ancak siz (veya projeyi başka herhangi biri) ortamı her zamanrequirements.txt'den yeniden ** oluşturasınız.

    Sanal ortamı dışlamak için **env** klasörüne sağ tıklayın ve Bu yerel öğeleri **yoksay'ı seçin.**

    ![Kaynak denetiminde sanal ortamı yoksayma değişiklikleri](media/flask/step01-ignore-local-items.png)

1. Sanal ortamı dışlamanın ardından, kalan tek değişiklik proje dosyasında ve *.gitignore dosyasındadır.* *.gitignore dosyası,* sanal ortam klasörü için ek bir girdi içerir. Bir fark görmek için dosyaya çift tıkabilirsiniz.

1. Bir işleme iletisi girin ve Hepsini İşle **düğmesini** seçin, ardından işlemeleri uzak depoya gönderin.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Soru: Neden sanal ortam oluşturmak istiyorum?

Cevap: Sanal ortam, uygulama bağımlılıklarınızı tam olarak yalıtmak için harika bir yol sağlar. Bu tür bir yalıtım, genel bir Python ortamındaki çakışmaları önler ve hem test hem de işbirliğine yardımcı olur. Zaman içinde, bir uygulama geliştirirken, sürekli olarak birçok yararlı Python paketi getirirsiniz. Paketleri projeye özgü bir sanal ortamda tutarak, projenin kaynak denetimine *dahil edilen ortamırequirements.txt* dosyasını kolayca güncelleştirebilirsiniz. Proje derleme sunucuları, dağıtım sunucuları ve diğer geliştirme bilgisayarları da dahil olmak üzere başka bir bilgisayarlara kopyalanırsa, yalnızca *requirements.txt* kullanarak ortamı kolayca yeniden oluşturabilirsiniz (bu nedenle ortamın kaynak denetiminde olması gerek değildir). Daha fazla bilgi için [bkz. Sanal ortamları kullanma.](selecting-a-python-environment-for-a-project.md#use-virtual-environments)

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Soru: Nasıl yaparım? denetimine zaten bağlı olan bir sanal ortamı kaldırmak mı gerekiyor?

Cevap: İlk *olarak, .gitignore* dosyanızı düzenleyemez ve klasörü dışlamak için en sonundaki bölümünü açıklamayla bulun ve gibi sanal ortam klasörü için yeni bir `# Python Tools for Visual Studio (PTVS)` satır `/BasicProject/env` ekleyin. (Visual Studio dosya dosyada **Çözüm Gezgini,** dosyayı doğrudan Dosya kullanarak **açın**  >  **Aç**  >  **Dosya** menüsü komutu. Dosyayı Takım Gezgini sayfasından da açabilirsiniz: **Ayarlar** sayfasında Depo **Ayarlar'ı** seçin, **&** Öznitelik Dosyalarını Yoksay bölümüne gidin ve **.gitignore öğesinin** yanındaki Düzenle bağlantısını seçin.  

İkinci olarak, bir komut penceresi açın, *basicProject* gibi env gibi sanal ortam klasörünü içeren *klasöre* gidin ve komutunu `git rm -r env` çalıştırın. Ardından, bu değişiklikleri komut satırı ( ) veya Takım Gezgini'nin `git commit -m 'Remove venv'` **Değişiklikler sayfasından işleyebilirsiniz.** 

## <a name="step-1-4-examine-the-boilerplate-code"></a>1-4. Adım: Ortak kodu inceleme

1. Proje oluşturma işlemi tamamlandıktan sonra çözüm ve **projeyi Çözüm Gezgini** içinde, projede yalnızca iki dosya (app.py *ve* *requirements.txt:*

    ![Dosyalarda boş Flask proje Çözüm Gezgini](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. Daha önce belirtildiği gibi, *requirements.txt* dosyası Flask paket bağımlılığını belirtir. Bu dosyanın varlığı, projeyi ilk kez oluştururken sizi sanal ortam oluşturmaya davet eder.

1. Tek bir *app.py* dosyası üç parça içerir. İlk olarak Flask için bir deyimdir; değişkenine atanan sınıfının bir örneğini oluşturmak ve ardından bir değişken `import` `Flask` `app` atamaktır (bu, bir web ana bilgisayarını dağıtırken yararlıdır, ancak şu anda `wsgi_app` kullanılmaz):

    ```python
    from flask import Flask
    app = Flask(__name__)

    # Make the WSGI interface available at the top level so wfastcgi can get it.
    wsgi_app = app.wsgi_app
    ```

1. Dosyanın sonundaki ikinci bölüm, Flask geliştirme sunucusunu ortam değişkenlerinden alınan belirli konak ve bağlantı noktası değerleriyle başlatan isteğe bağlı bir koddur (varsayılan olarak localhost:5555):

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

1. Üçüncüsü, url yolu için bir işlev ataan kısa bir kod bitidir, yani işlevin URL tarafından tanımlanan kaynağı sağladığı anlamına gelir. Yolları, bağımsız değişkeni site kökünden göreli URL olan Flask'in `@app.route` dekoratörünü kullanarak tanımlarsiniz. Kodda gördüğünüz gibi buradaki işlev yalnızca bir metin dizesi döndürür ve bu da tarayıcının işlemesi için yeterlidir. Aşağıdaki adımlarda HTML ile daha zengin sayfalar işlersiniz.

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-__name__-argument-to-the-flask-class"></a>Soru: Flask __sınıfına yönelik ad__ bağımsız değişkeninin amacı nedir?

Cevap: Bağımsız değişken, uygulamanın modülünün veya paketinin adıdır ve Flask'e uygulamaya ait şablonların, statik dosyaların ve diğer kaynakların nerede olduğunu söyler. Tek bir modülde yer alan uygulamalar için `__name__` her zaman uygun değer kullanılır. Hata ayıklama bilgisi gereken uzantılar için de önemlidir. Daha fazla bilgi ve ek bağımsız değişkenler için [Flask sınıf belgelerine (flask.pocoo.org).](https://flask.palletsprojects.com/en/1.0.x/api/#flask.Flask)

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>Soru: Bir işlevin birden fazla yol dekoratörü olabilir mi?

Cevap: Evet, aynı işlev birden çok yol kullanıyorsa istediğiniz sayıda dekoratör kullanabilirsiniz. Örneğin, `hello` "/" ve "/hello" için işlevini kullanmak için aşağıdaki kodu kullanın:

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>Soru: Flask, değişken URL yolları ve sorgu parametreleriyle nasıl çalışır?

Yanıt: Bir yolda, herhangi bir değişkeni ile işaretleyebilirsiniz ve Flask, URL yolundaki adlandırılmış bağımsız değişkeni kullanarak değişkeni `<variable_name>` işleve iletir. Örneğin, şeklinde bir yol, `/hello/<name>` işlevine çağrılır bir dize `name` bağımsız değişkeni üretir. Sorgu parametreleri özelliği `request.args` aracılığıyla, özellikle yöntemi aracılığıyla `request.args.get` kullanılabilir. Daha fazla bilgi için Flask [belgelerinde](https://flask.palletsprojects.com/en/1.1.x/quickstart/#the-request-object) request nesnesine bakın.

```python
# URL: /hello/<name>?message=Have%20a%20nice%20day
@app.route('/hello/<name>')
def hello(name):
    msg = request.args.get('message','')
    return "Hello " + name + "! "+ msg + "."
```

Türü değiştirmek için değişkene , , (klasör adlarının satırlarını çizen eğik çizgi kabul `int` `float` `path` eder) ön eklerini ve . `uuid` Ayrıntılar için Flask [belgelerinde](https://flask.palletsprojects.com/en/1.0.x/quickstart/#variable-rules) değişken kurallarına bakın.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Soru: Visual Studio paketleri yükledikten requirements.txt bir sanal ortamdan bir dosya oluşturamıyor musunuz?

Yanıt: Evet. Python Ortamları **düğümünü** genişletin, sanal ortamınıza sağ tıklayın ve Oluştur komutunu **requirements.txt** seçin. Ortamı değiştirirken bu komutu düzenli aralıklarla kullanmak ve değişiklikleri  kaynak denetiminerequirements.txtortamdaki diğer kod değişiklikleriyle birlikte işlemek iyi bir fikirdir. Derleme sunucusunda sürekli tümleştirmeyi ayar ediyorsanız, ortamı her değiştirerek dosyayı oluşturmalı ve değişiklikleri işlemelisiniz.

## <a name="step-1-5-run-the-project"></a>1-5. Adım: Projeyi çalıştırma

1. Bu Visual Studio **Hata** AyıklamaYı Başlat ( F5 ) öğesini seçin veya araç çubuğundaki Web Sunucusu düğmesini kullanın  >   (gördüğünüz tarayıcı farklılık gösterebilir): 

    ![Web sunucusu araç çubuğu düğmesini Visual Studio](media/tutorials-common/run-web-server-toolbar-button.png)

1. İki komut da PORT ortam değişkenine rastgele bir bağlantı noktası numarası atar ve `python app.py` çalıştırır. Kod, Flask'in geliştirme sunucusundaki bu bağlantı noktasını kullanarak uygulamayı başlatır. Hata Visual Studio **dosyası** yok iletisiyle hata ayıklayıcı başlatılamadı ifadesinin yer  alırsa, app.py'a sağ tıklayın Çözüm Gezgini Başlangıç Dosyası **Olarak** **Ayarla'yı seçin.**

1. Sunucu başlatıldığında, sunucu günlüğünü görüntüleyen bir konsol penceresi açılır. Visual Studio, işlevin işlenen `http://localhost:<port>` iletiyi göreceğiniz bir tarayıcıyı otomatik olarak `hello` açar:

    ![Flask projesi varsayılan görünümü](media/flask/step01-first-run-success.png)

1. Bitirerek konsol penceresini kapatarak veya hata ayıklamada hata ayıklamayı durdur komutunu kullanarak sunucuyu  >   Visual Studio.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Soru: Projenin Python alt menüsünde Hata Ayıklama menü komutlarını ve sunucu komutlarını kullanma arasındaki fark nedir?

Cevap: Hata ayıklama  menü komutları ve araç çubuğu düğmelerine ek olarak, projenin bağlam **menüsündeki Python** Çalıştırma sunucusu veya Python Çalıştırma hata ayıklama sunucusu komutlarını kullanarak da  >     >   sunucuyu başlatabilirsiniz. Her iki komut da çalışan sunucunun yerel URL'sini (localhost:port) gördüğünüz bir konsol penceresi açar. Ancak, bu URL'ye sahip bir tarayıcıyı el ile açmalısınız ve hata ayıklama sunucusunun çalıştırılırken hata ayıklayıcısı otomatik Visual Studio başlamaz. Hata Ayıkla İşleme Ekle komutunu kullanarak daha sonra, daha sonra, çalışan işleme **bir hata**  >  **ayıklayıcı** iliştirebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu noktada temel Flask projesi, başlangıç kodunu ve sayfa kodunu aynı dosyada içerir. En iyisi bu iki endişeyi ayırmak ve ayrıca şablonları kullanarak HTML ve verileri ayırmaktır.

> [!div class="nextstepaction"]
> [Görünümler ve sayfa şablonlarıyla bir Flask uygulaması oluşturma](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>Daha derine gitme

- [Flask Hızlı Başlangıç](https://flask.palletsprojects.com/en/1.0.x/quickstart/) (flask.pocoo.org)
- GitHub öğretici kaynak kodu: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)