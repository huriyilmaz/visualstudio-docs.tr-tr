---
title: adım 1 ' de flask öğreticisi öğrenin Visual Studio, flask temelleri
titleSuffix: ''
description: önkoşullar, Git ve sanal ortamlar dahil Visual Studio projeler bağlamında flask temelleri hakkında bir anlatım.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625382"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>Öğretici: Visual Studio ' de Flask Web çerçevesi ile çalışmaya başlama

[Flask](https://palletsprojects.com/p/flask/) , URL yönlendirme ve sayfa işleme için temel bilgileri sağlayan Web uygulamalarına yönelik hafif bir Python çerçevesidir.

Doğrudan form doğrulaması, veritabanı soyutlama, kimlik doğrulama vb. gibi özellikler sağlamadığından Flask "mikro" çerçevesi olarak adlandırılır. Bu tür özellikler bunun yerine Flask *uzantıları* adlı özel Python paketleri tarafından sağlanır. Uzantılar Flask ile sorunsuz bir şekilde tümleşir, böylece Flask 'nin bir parçası gibi görünürler. Örneğin, Flask 'nın kendisi bir sayfa şablonu altyapısı sağlamıyor. Şablon oluşturma, bu öğreticide gösterildiği gibi Jınja ve Jade gibi uzantılar tarafından sağlanır.

::: moniker range="vs-2017"
Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
- "boş flask Web Project" şablonunu kullanarak Git deposunda temel bir flask projesi oluşturma (1. adım)
- Tek sayfalı bir Flask uygulaması oluşturun ve bu sayfayı şablon kullanarak oluşturun (2. adım)
- Statik dosyaları sunma, sayfa ekleme ve şablon devralmayı kullanma (3. adım)
- birden çok sayfa ve yanıt veren tasarıma sahip bir uygulama oluşturmak için flask Web Project şablonunu kullanın (4. adım)
- çeşitli depolama seçeneklerini (Azure storage, mongodb veya bellek) kullanan bir yoklama uygulaması oluşturmak için flask Web Project şablonunu yoklayarak kullanın.

bu adımları izleyerek, üç ayrı proje içeren tek bir Visual Studio çözümü oluşturursunuz. Projeyi, Visual Studio dahil edilen farklı Flask proje şablonlarını kullanarak oluşturursunuz. Projeleri aynı çözümde tutarak, karşılaştırma için farklı dosyalar arasında kolayca geri ve ileri geçiş yapabilirsiniz.
::: moniker-end

::: moniker range=">=vs-2019"

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
- "boş flask Web Project" şablonunu kullanarak Git deposunda temel bir flask projesi oluşturma (1. adım)
- Tek sayfalı bir Flask uygulaması oluşturun ve bu sayfayı şablon kullanarak oluşturun (2. adım)
- Statik dosyaları sunma, sayfa ekleme ve şablon devralmayı kullanma (3. adım)
- birden çok sayfa ve yanıt veren tasarıma sahip bir uygulama oluşturmak için flask Web Project şablonunu kullanın (4. adım)

bu adımları uygulayarak, iki ayrı proje içeren tek bir Visual Studio çözümü oluşturursunuz. Projeyi, Visual Studio dahil edilen farklı Flask proje şablonlarını kullanarak oluşturursunuz. Projeleri aynı çözümde tutarak, karşılaştırma için farklı dosyalar arasında kolayca geri ve ileri geçiş yapabilirsiniz.
::: moniker-end

> [!Note]
> Bu öğretici, Flask hakkında daha fazla bilgi edinmenize ve kendi projeleriniz için daha kapsamlı bir başlangıç noktası sağlayan farklı Flask proje şablonlarının nasıl kullanılacağına ilişkin [Flask hızlı](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) başlangıçından farklıdır. Örneğin, proje şablonları otomatik olarak bir proje oluştururken Flask paketini yükler ve hızlı başlangıçta gösterildiği gibi paketi el ile yüklemenizi gerektirir.

## <a name="prerequisites"></a>Önkoşullar

- aşağıdaki seçeneklerle Windows Visual Studio 2017 veya üzeri:
  - **Python geliştirme** iş yükü (yükleyicideki **iş yükü** sekmesi). Yönergeler için bkz. [Visual Studio Python desteğini Yüklemeyi](installing-python-support-in-visual-studio.md).
  - **kod araçları** altındaki **tek bileşenler** sekmesinde Visual Studio Windows ve **GitHub uzantısı** için **Git** .

flask proje şablonları, önceki Visual Studio için Python Araçları tüm sürümlerine dahildir, ancak ayrıntılar bu öğreticide açıklanabilecek verilerden farklı olabilir.

Python geliştirme Mac için Visual Studio şu anda desteklenmiyor. Mac ve Linux 'ta [Visual Studio Code ' de Python uzantısını](https://code.visualstudio.com/docs/python/python-tutorial)kullanın.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>adım 1-1: Visual Studio bir proje ve çözüm oluşturma

1. Visual Studio ' de **dosya**  >  **yeni**  >  **Project**' ni seçin, "flask" araması yapın ve **boş flask Web Project** şablonunu seçin. (Şablon **Python**  >  altında da bulunur **Web** , sol taraftaki listede.)

    ![boş flask Web Project için Visual Studio yeni proje iletişim kutusu](media/flask/step01-new-blank-project.png)

1. İletişim kutusunun altındaki alanlarda aşağıdaki bilgileri girin (önceki grafikte gösterildiği gibi) ve ardından **Tamam**' ı seçin:

    - **ad**: Visual Studio projesinin adını **basicproject** olarak ayarlayın. Bu ad ayrıca Flask projesi için de kullanılır.
    - **konum**: Visual Studio çözümünün ve projenin oluşturulacağı bir konum belirtin.
    - **Çözüm adı**: Bu öğreticide birden çok projenin kapsayıcısı olarak çözüm olarak uygun olan **Learningflask** olarak ayarlanır.
    - **Çözüm için dizin oluştur**: kümeyi bırak (varsayılan).
    - **yeni git deposu oluştur**: bu seçeneği, Visual Studio çözümü oluşturduğunda yerel bir Git deposu oluşturması için (varsayılan olarak temiz) seçin. bu seçeneği görmüyorsanız, Visual Studio yükleyiciyi çalıştırın ve **kod araçları** altındaki **tek bileşenler** sekmesinde Visual Studio için **Git Windows** ve **GitHub uzantısı** ekleyin.

1. bir süre sonra, Visual Studio **bu projenin dış paketler gerektirdiğini** belirten bir iletişim kutusu ister (aşağıda gösterilmiştir). Bu iletişim kutusu, şablon en son Flask 1. x paketine başvuran bir *requirements.txt* dosyası içerdiğinden görüntülenir. (Tam bağımlılıkları görmek için **gerekli paketleri göster** ' i seçin.)

    ![Projenin dış paketler gerektirdiğini söyleyen bir istem](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. **Kendim yükleyeceğim** seçeneğini belirleyin. Kaynak denetiminden dışlandığından emin olmak için sanal ortamı kısa süre içinde oluşturursunuz. (Ortam her zaman *requirements.txt* oluşturulabilir.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Adım 1-2: git denetimlerini Inceleme ve uzak depoda yayımlama

yeni **Project** iletişim kutusunda **yeni Git deposu oluştur** ' u seçtiğinizden, proje, oluşturma işlemi tamamlandıktan hemen sonra yerel kaynak denetimine zaten kaydedilmiş olur. bu adımda, Visual Studio Git denetimleri ve kaynak denetimi ile birlikte çalıştığınız **Takım Gezgini** pencere hakkında bilgi edinin.

1. Visual Studio ana penceresinin alt köşesindeki Git denetimlerini inceleyin. Soldan sağa, bu denetimler gönderilmeyen işlemeler, kaydedilmemiş değişiklikler, deponun adı ve geçerli dalı gösterir:

    ![Visual Studio penceresindeki Git denetimleri](media/flask/step01-git-controls.png)

    > [!Note]
    > yeni **Project** iletişim kutusunda **yeni git deposu oluştur** ' u seçmezseniz, git denetimleri yalnızca yerel bir depo oluşturan **kaynak denetimine ekle** komutunu gösterir.
    >
    > ![bir depo oluşturmadıysanız Visual Studio kaynak denetimine ekle görüntülenir](media/tutorials-common/step01-git-add-to-source-control.png)

1. değişiklikler düğmesini seçin ve Visual Studio **değişiklikler** sayfasında **Takım Gezgini** penceresini açar. Yeni oluşturulan proje kaynak denetimine otomatik olarak zaten yapıldığından, bekleyen bir değişiklik görmezsiniz.

    ![Değişiklikler sayfasında Takım Gezgini penceresi](media/flask/step01-team-explorer-changes.png)

1. Visual Studio durum çubuğunda, **Takım Gezgini**' de **eşitleme** sayfasını açmak için gönderişsiz işlemeler düğmesini ( **2** ile yukarı ok) seçin. Yalnızca yerel bir depo olduğundan, Bu sayfa depoyu farklı uzak depolara yayımlamak için kolay seçenekler sağlar.

    ![Kaynak denetimi için kullanılabilir git deposu seçeneklerini gösteren Takım Gezgini pencere](media/flask/step01-team-explorer.png)

    Kendi projeleriniz için istediğiniz hizmeti seçebilirsiniz. bu öğreticide, öğreticinin tamamlanan örnek kodunun [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask) deposunda gerçekleştiği GitHub kullanımı gösterilmektedir.

1. **Yayınlama** denetimlerinden herhangi birini seçerken **Takım Gezgini** daha fazla bilgi ister. Örneğin, bu öğretici için örnek yayımlarken, deponun kendisi oluşturulmalıdır, bu durumda depo URL 'SI ile **uzak depoya gönderim** seçeneği kullanılır.

    ![Var olan bir uzak depoya göndermek için Takım Gezgini pencere](media/flask/step01-push-to-github.png)

    mevcut bir deponuz yoksa **GitHub yayımla** ve **Azure DevOps seçeneklerine gönder** seçenekleri doğrudan Visual Studio içinden bir tane oluşturmanızı sağlar.

1. bu öğreticide çalışırken, değişiklikleri yürütmek ve göndermek için Visual Studio içindeki denetimleri kullanarak düzenli aralıklarla habite ulaşın. Bu öğretici size uygun noktalarda hatırlatır.

> [!Tip]
> **Takım Gezgini** içinde hızlıca gezinmek için, kullanılabilir sayfaların açılır menüsünü görmek üzere üstbilgiyi seçin (Yukarıdaki **Resimleri okur veya** yukarıdaki görüntüleri **Gönder** ) seçeneğini belirleyin.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Soru: bir projenin başından itibaren kaynak denetimi kullanmanın avantajları nelerdir?

Cevap: başlangıçtan itibaren kaynak denetimini kullanarak, özellikle de uzak bir depo kullanıyorsanız, projenizin düzenli olarak şirket dışı yedeklemesini sağlar. Yalnızca yerel bir dosya sistemindeki bir projeyi korumanın aksine, kaynak denetimi tam bir değişiklik geçmişi ve tek bir dosyayı ya da projenin tamamını önceki bir duruma geri döndürmenin kolay bir özelliğini sağlar. Bu değişiklik geçmişi, gerilemelerin nedenini (test arızaları) belirlemenize yardımcı olur. Ayrıca, bir proje üzerinde birden fazla kişi çalışıyorsa, kaynak denetimi, üzerine yazma işlemlerini yönetirken ve çakışma çözümü sağladığından gereklidir. Son olarak, otomasyon bir form olan kaynak denetimi, yapıları, testi ve yayın yönetimini otomatikleştirmek için size en iyi şekilde ayarlanır. bu aslında bir proje için DevOps kullanmanın ilk adımıdır ve giriş engelleri bu kadar düşük olduğundan, kaynak denetimini baştan kullanmanın gerçekten bir nedeni yoktur.

kaynak denetimi ile otomasyon olarak daha fazla tartışma için bkz. [gerçeği: DevOps içindeki depoların rolü](/archive/msdn-magazine/2016/september/mobile-devops-the-source-of-truth-the-role-of-repositories-in-devops), MSDN Magazine 'teki web apps için de geçerli olan mobil uygulamalar için yazılmış bir makale.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>soru: Visual Studio, yeni bir projeyi otomatik olarak yürütmeyi engelleyebilir miyim?

Yanıt: Evet. otomatik yürütmeyi devre dışı bırakmak için **Takım Gezgini** **Ayarlar** sayfasına gidin, **git**  >  **genel ayarları**' nı seçin, **varsayılan olarak birleştirmeden sonra değişiklikleri yürüt** etiketli seçeneği temizleyin ve ardından **güncelleştir**' i seçin.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Adım 1-3: sanal ortam oluşturma ve kaynak denetiminden dışlama

Projeniz için kaynak denetimini yapılandırdığınıza göre, sanal ortamı, projenin gerektirdiği gerekli Flask paketlerini oluşturabilirsiniz. Ardından, ortam klasörünü kaynak denetiminden dışlamak için **Takım Gezgini** kullanabilirsiniz.

1. **Çözüm Gezgini**, **Python ortamları** düğümüne sağ tıklayın ve **sanal ortam ekle**' yi seçin.

    ![Çözüm Gezgini sanal ortam komutu Ekle](media/flask/step01-add-virtual-environment-command.png)

1. Bir **requirements.txt dosyası bulduğumuz** belirten bir Ileti Ile **sanal ortam ekle** iletişim kutusu görüntülenir. bu ileti, Visual Studio sanal ortamı yapılandırmak için bu dosyayı kullanacağını gösterir.

    ![requirements.txt iletisiyle sanal ortam iletişim kutusu Ekle](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Varsayılanları kabul etmek için **Oluştur** ' u seçin. (İsterseniz sanal ortamın adını değiştirebilirsiniz, bu, yalnızca alt klasörünün adını değiştirir ancak `env` Standart bir kuraldır.)

1. istenirse, yönetici ayrıcalıklarına onay vermeniz gerekirse birkaç Visual Studio dakika bekleyin. flask ve bağımlılıkları, 100 ' den fazla alt klasörde binlerce dosya hakkında genişletme anlamına gelir. İlerlemeyi Çıkış penceresinde Visual Studio **görebilirsiniz.** Beklerken, aşağıdaki Soru bölümlerine daha fazla bakın. Flask'in bağımlılıklarının açıklamasını [Flask](https://flask.palletsprojects.com/en/1.0.x/installation/#installation) yükleme sayfasında da görebilirsiniz (flask.pcocoo.org).

1. Git Visual Studio (durum çubuğunda) değişiklik göstergesini **(99**&#42;gösterir) seçin. Bu durumda,  **Takım Gezgini.**

    Sanal ortamın oluşturulması yüzlerce değişiklikle getirildi ancak siz (veya projeyi başka herhangi biri) ortamı her zamanrequirements.txt'den yeniden ** oluşturasınız.

    Sanal ortamı dışlamak için **env** klasörüne sağ tıklayın ve Bu yerel öğeleri **yoksay'ı seçin.**

    ![Kaynak denetimi değişikliklerinde sanal ortamı yoksayma](media/flask/step01-ignore-local-items.png)

1. Sanal ortamı dışlamanın ardından, kalan tek değişiklik proje dosyasında ve *.gitignore dosyasındadır.* *.gitignore dosyası,* sanal ortam klasörü için ek bir girdi içerir. Bir fark görmek için dosyaya çift tıkabilirsiniz.

1. Bir işleme iletisi girin ve Hepsini İşle **düğmesini** seçin, ardından işlemeleri uzak depoya gönderin.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Soru: Neden sanal ortam oluşturmak istiyorum?

Cevap: Sanal ortam, uygulama bağımlılıklarınızı tam olarak yalıtmak için harika bir yol sağlar. Bu tür bir yalıtım, genel bir Python ortamındaki çakışmaları önler ve hem test hem de işbirliğine yardımcı olur. Zaman içinde, bir uygulama geliştirirken, sürekli olarak birçok yararlı Python paketi getirirsiniz. Paketleri projeye özgü bir sanal ortamda tutarak, projenin kaynak denetimine dahil edilen ortamı *requirements.txt* dosyasını kolayca güncelleştirebilirsiniz. Proje derleme sunucuları, dağıtım sunucuları ve diğer geliştirme bilgisayarları da dahil olmak üzere başka bir bilgisayarlara kopyalanırsa, yalnızca *requirements.txt* kullanarak ortamı kolayca yeniden oluşturabilirsiniz (bu nedenle ortamın kaynak denetiminde olması gerekmektedir). Daha fazla bilgi için [bkz. Sanal ortamları kullanma.](selecting-a-python-environment-for-a-project.md#use-virtual-environments)

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Soru: Nasıl yaparım? denetimine zaten bağlı olan bir sanal ortamı kaldırmak mı gerekiyor?

Cevap: İlk *olarak, .gitignore* dosyanızı düzenleyemez ve klasörü dışlamak için en sonundaki bölümünü açıklamayla bulun ve gibi sanal ortam klasörü için yeni `# Python Tools for Visual Studio (PTVS)` bir satır `/BasicProject/env` ekleyin. (Visual Studio dosya dosyada **Çözüm Gezgini,** dosyayı doğrudan Dosya kullanarak **açın**  >  **Aç**  >  **Dosya** menüsü komutu. Dosyayı  Takım Gezgini **sayfasından** da açabilirsiniz: Ayarlar sayfasında Depo **Ayarlar'ı** seçin, **&** Öznitelik Dosyalarını Yoksay bölümüne gidin ve **.gitignore öğesinin** yanındaki Düzenle bağlantısını seçin.) 

İkinci olarak, bir komut penceresi açın, env gibi sanal ortam klasörünü içeren *BasicProject* gibi *klasöre* gidin ve komutunu `git rm -r env` çalıştırın. Ardından bu değişiklikleri komut satırı ( `git commit -m 'Remove venv'` ) veya **Takım Gezgini'nin Değişiklikler** **sayfasından işleyebilirsiniz.**

## <a name="step-1-4-examine-the-boilerplate-code"></a>1-4. Adım: Ortak kodu inceleme

1. Proje oluşturma işlemi tamamlandıktan sonra çözüm ve **projeyi Çözüm Gezgini** içinde, projede yalnızca iki dosya (app.py *ve* *requirements.txt:*

    ![Dosyalarda boş Flask proje Çözüm Gezgini](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. Daha önce belirtildiği gibi, *requirements.txt* dosyası Flask paketi bağımlılığını belirtir. Bu dosyanın varlığı, projeyi ilk oluştururken sizi sanal ortam oluşturmaya davet eder.

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

Cevap: Bağımsız değişken, uygulamanın modülünün veya paketinin adıdır ve Flask'e uygulamaya ait şablonların, statik dosyaların ve diğer kaynakların nerede olduğunu söyler. Tek bir modülde yer alan uygulamalar için `__name__` her zaman uygun değer kullanılır. Hata ayıklama bilgisi gereken uzantılar için de önemlidir. Daha fazla bilgi ve ek bağımsız değişkenler için [Flask](https://flask.palletsprojects.com/en/1.0.x/api/#flask.Flask) sınıf belgelerine (flask.pocoo.org).

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

Yanıt: Evet. Python Ortamları **düğümünü** genişletin, sanal ortamınıza sağ tıklayın ve Oluştur komutunu **requirements.txt** seçin. Ortamı değiştirirken bu komutu düzenli aralıklarla kullanmak ve değişiklikleri  kaynak denetiminerequirements.txtve bu ortama bağlı diğer kod değişiklikleriyle birlikte işlemek iyi bir fikirdir. Derleme sunucusunda sürekli tümleştirmeyi ayar ediyorsanız, ortamı her değiştirerek dosyayı oluşturmalı ve değişiklikleri işlemelisiniz.

## <a name="step-1-5-run-the-project"></a>1-5. Adım: Projeyi çalıştırma

1. Bu Visual Studio Hata AyıklamaYı Başlat ( F5 ) öğesini seçin veya araç çubuğundaki Web Sunucusu düğmesini kullanın  >  (gördüğünüz tarayıcı farklılık gösterebilir):  

    ![Web sunucusu araç çubuğu düğmesini Visual Studio](media/tutorials-common/run-web-server-toolbar-button.png)

1. her iki komut da PORT ortam değişkenine rastgele bir bağlantı noktası numarası atar ve `python app.py` çalıştırır. Kod, Flask'in geliştirme sunucusundaki bu bağlantı noktasını kullanarak uygulamayı başlatır. Başlangıç Visual Studio **olmadığını** iletiyle hata ayıklayıcı başlatılamadı iletisiyle belirtiyorsa,  app.py'e sağ tıklayın ve Başlangıç Dosyası **Çözüm Gezgini** **Ayarla'yı seçin.**

1. Sunucu başlatıldığında, sunucu günlüğünü görüntüleyen bir konsol penceresi açılır. Visual Studio, işlevin işlenen `http://localhost:<port>` iletiyi göreceğiniz bir tarayıcıyı otomatik olarak `hello` açar:

    ![Flask projesi varsayılan görünümü](media/flask/step01-first-run-success.png)

1. Bitirerek konsol penceresini kapatarak veya hata ayıklamada hata ayıklamayı durdur komutunu kullanarak sunucuyu  >   Visual Studio.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Soru: Projenin Python alt menüsünde Hata Ayıklama menü komutlarını ve sunucu komutlarını kullanma arasındaki fark nedir?

Cevap: Hata ayıklama  menü komutları ve araç çubuğu düğmelerine ek olarak, projenin bağlam **menüsündeki Python** Çalıştırma sunucusu veya Python Çalıştırma hata ayıklama sunucusu komutlarını kullanarak da  >     >   sunucuyu başlatabilirsiniz. Her iki komut da çalışan sunucunun yerel URL'sini (localhost:port) gördüğünüz bir konsol penceresi açar. Ancak, bu URL'ye sahip bir tarayıcıyı el ile açmalısınız ve hata ayıklama sunucusunun çalıştır olması hata ayıklayıcıyı otomatik Visual Studio başlatmaz. Hata Ayıkla İşleme Ekle komutunu kullanarak daha sonra, daha sonra, çalışan işleme **bir hata**  >  **ayıklayıcı** iliştirebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu noktada temel Flask projesi, başlangıç kodunu ve sayfa kodunu aynı dosyada içerir. En iyisi bu iki endişeyi ayırmak ve ayrıca şablonları kullanarak HTML ve verileri ayırmaktır.

> [!div class="nextstepaction"]
> [Görünümler ve sayfa şablonlarıyla bir Flask uygulaması oluşturma](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>Daha derine gitme

- [Flask Hızlı Başlangıç](https://flask.palletsprojects.com/en/1.0.x/quickstart/) (flask.pocoo.org)
- GitHub öğreticisi: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)