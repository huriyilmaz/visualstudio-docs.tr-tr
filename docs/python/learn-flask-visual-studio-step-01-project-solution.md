---
title: Visual Studio 'da Flask öğreticisini öğrenin 1. adım, Flask temelleri
titleSuffix: ''
description: Önkoşullar, git ve sanal ortamlar dahil Visual Studio projeleri bağlamında Flask temelleri hakkında bir anlatım.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 89a84198256657ae7f94d0a923780163bee73e48
ms.sourcegitcommit: 5c0e20fc6005bc1f8ca38f4122378c4ac21ba89a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2021
ms.locfileid: "106110616"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>Öğretici: Visual Studio 'da Flask Web çerçevesi ile çalışmaya başlama

[Flask](https://palletsprojects.com/p/flask/) , URL yönlendirme ve sayfa işleme için temel bilgileri sağlayan Web uygulamalarına yönelik hafif bir Python çerçevesidir.

Doğrudan form doğrulaması, veritabanı soyutlama, kimlik doğrulama vb. gibi özellikler sağlamadığından Flask "mikro" çerçevesi olarak adlandırılır. Bu tür özellikler bunun yerine Flask *uzantıları* adlı özel Python paketleri tarafından sağlanır. Uzantılar Flask ile sorunsuz bir şekilde tümleşir, böylece Flask 'nin bir parçası gibi görünürler. Örneğin, Flask 'nın kendisi bir sayfa şablonu altyapısı sağlamıyor. Şablon oluşturma, bu öğreticide gösterildiği gibi Jınja ve Jade gibi uzantılar tarafından sağlanır.

::: moniker range="vs-2017"
Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
- "Boş Flask Web projesi" şablonunu kullanarak bir git deposunda temel bir Flask projesi oluşturma (1. adım)
- Tek sayfalı bir Flask uygulaması oluşturun ve bu sayfayı şablon kullanarak oluşturun (2. adım)
- Statik dosyaları sunma, sayfa ekleme ve şablon devralmayı kullanma (3. adım)
- Birden çok sayfa ve yanıt veren tasarıma sahip bir uygulama oluşturmak için Flask Web projesi şablonunu kullanın (4. adım)
- Çeşitli depolama seçeneklerini (Azure Storage, MongoDB veya bellek) kullanan bir yoklama uygulaması oluşturmak için Flask Web projesi şablonunu Yoklat ' i kullanın.

Bu adımları izleyerek, üç ayrı proje içeren tek bir Visual Studio çözümü oluşturursunuz. Projeyi, Visual Studio ile birlikte gelen farklı Flask proje şablonlarını kullanarak oluşturursunuz. Projeleri aynı çözümde tutarak, karşılaştırma için farklı dosyalar arasında kolayca geri ve ileri geçiş yapabilirsiniz.
::: moniker-end

::: moniker range=">=vs-2019"

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
- "Boş Flask Web projesi" şablonunu kullanarak bir git deposunda temel bir Flask projesi oluşturma (1. adım)
- Tek sayfalı bir Flask uygulaması oluşturun ve bu sayfayı şablon kullanarak oluşturun (2. adım)
- Statik dosyaları sunma, sayfa ekleme ve şablon devralmayı kullanma (3. adım)
- Birden çok sayfa ve yanıt veren tasarıma sahip bir uygulama oluşturmak için Flask Web projesi şablonunu kullanın (4. adım)

Bu adımları uygulayarak, iki ayrı proje içeren tek bir Visual Studio çözümü oluşturursunuz. Projeyi, Visual Studio ile birlikte gelen farklı Flask proje şablonlarını kullanarak oluşturursunuz. Projeleri aynı çözümde tutarak, karşılaştırma için farklı dosyalar arasında kolayca geri ve ileri geçiş yapabilirsiniz.
::: moniker-end

> [!Note]
> Bu öğretici, Flask hakkında daha fazla bilgi edinmenize ve kendi projeleriniz için daha kapsamlı bir başlangıç noktası sağlayan farklı Flask proje şablonlarının nasıl kullanılacağına ilişkin [Flask hızlı](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) başlangıçından farklıdır. Örneğin, proje şablonları otomatik olarak bir proje oluştururken Flask paketini yükler ve hızlı başlangıçta gösterildiği gibi paketi el ile yüklemenizi gerektirir.

## <a name="prerequisites"></a>Önkoşullar

- Aşağıdaki seçeneklerle Visual Studio 2017 veya üzeri Windows üzerinde:
  - **Python geliştirme** iş yükü (yükleyicideki **iş yükü** sekmesi). Yönergeler için bkz. [Visual Studio 'Da Python desteğini Yüklemeyi](installing-python-support-in-visual-studio.md).
  - **Visual Studio Için Windows ve GitHub Uzantısı** için **Git** , **kod araçları** altındaki **tek bileşenler** sekmesinde.

Flask proje şablonları, önceki Visual Studio için Python Araçları tüm sürümlerine dahildir, ancak Ayrıntılar Bu öğreticide açıklanabilecek verilerden farklı olabilir.

Python geliştirme Mac için Visual Studio şu anda desteklenmiyor. Mac ve Linux 'ta [Visual Studio Code ' de Python uzantısını](https://code.visualstudio.com/docs/python/python-tutorial)kullanın.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Adım 1-1: Visual Studio projesi ve çözümü oluşturma

1. Visual Studio 'da **Dosya**  >  **Yeni**  >  **Proje**' yi seçin, "Flask" araması yapın ve **boş Flask Web projesi** şablonunu seçin. (Şablon **Python**  >  altında da bulunur **Web** , sol taraftaki listede.)

    ![Boş Flask Web projesi için Visual Studio 'da yeni proje iletişim kutusu](media/flask/step01-new-blank-project.png)

1. İletişim kutusunun altındaki alanlarda aşağıdaki bilgileri girin (önceki grafikte gösterildiği gibi) ve ardından **Tamam**' ı seçin:

    - **Ad**: Visual Studio projesinin adını **BasicProject** olarak ayarlayın. Bu ad ayrıca Flask projesi için de kullanılır.
    - **Konum**: Visual Studio çözümünün ve projenin oluşturulacağı bir konum belirtin.
    - **Çözüm adı**: Bu öğreticide birden çok projenin kapsayıcısı olarak çözüm olarak uygun olan **Learningflask** olarak ayarlanır.
    - **Çözüm için dizin oluştur**: kümeyi bırak (varsayılan).
    - **Yeni git deposu oluştur**: Visual Studio 'nun çözümü oluşturduğunda yerel bir git deposu oluşturması için bu seçeneği (varsayılan olarak temiz) seçin. Bu seçeneği görmüyorsanız, Visual Studio yükleyicisi 'ni çalıştırın ve **kod araçları**' nın altındaki **tek bileşenler** sekmesinde Visual Studio için **Git ve Windows** için **GitHub uzantısını** ekleyin.

1. Bir süre sonra, Visual Studio **Bu projenin dış paketler gerektirdiğini** belirten bir iletişim kutusu ister (aşağıda gösterilmiştir). Bu iletişim kutusu, şablon en son Flask 1. x paketine başvuran bir *requirements.txt* dosyası içerdiğinden görüntülenir. (Tam bağımlılıkları görmek için **gerekli paketleri göster** ' i seçin.)

    ![Projenin dış paketler gerektirdiğini söyleyen bir istem](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. **Kendim yükleyeceğim** seçeneğini belirleyin. Kaynak denetiminden dışlandığından emin olmak için sanal ortamı kısa süre içinde oluşturursunuz. (Ortam her zaman *requirements.txt* oluşturulabilir.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Adım 1-2: git denetimlerini Inceleme ve uzak depoda yayımlama

Yeni **Proje** iletişim kutusunda **Yeni git deposu oluştur** ' u seçtiğinizden, proje, oluşturma işlemi tamamlandıktan hemen sonra yerel kaynak denetimine zaten kaydedilmiş olur. Bu adımda, Visual Studio 'nun git denetimleri ve kaynak denetimi ile birlikte çalıştığınız **Takım Gezgini** pencere hakkında bilgi edinin.

1. Visual Studio ana penceresinin alt köşesindeki git denetimlerini inceleyin. Soldan sağa, bu denetimler gönderilmeyen işlemeler, kaydedilmemiş değişiklikler, deponun adı ve geçerli dalı gösterir:

    ![Visual Studio penceresinde git denetimleri](media/flask/step01-git-controls.png)

    > [!Note]
    > **Yeni proje** iletişim kutusunda **Yeni git deposu oluştur** ' u seçmezseniz, git denetimleri yalnızca yerel bir depo oluşturan **kaynak denetimine Ekle** komutunu gösterir.
    >
    > ![Bir depo oluşturmadıysanız Visual Studio 'da kaynak denetimine Ekle görüntülenir](media/tutorials-common/step01-git-add-to-source-control.png)

1. Değişiklikler düğmesini seçin ve Visual Studio, **değişiklikler** sayfasında **Takım Gezgini** penceresini açar. Yeni oluşturulan proje kaynak denetimine otomatik olarak zaten yapıldığından, bekleyen bir değişiklik görmezsiniz.

    ![Değişiklikler sayfasında Takım Gezgini penceresi](media/flask/step01-team-explorer-changes.png)

1. Visual Studio durum çubuğunda, **Takım Gezgini**' de **eşitleme** sayfasını açmak için teslim edilmemiş işlemeler düğmesini ( **2** ile yukarı ok) seçin. Yalnızca yerel bir depo olduğundan, Bu sayfa depoyu farklı uzak depolara yayımlamak için kolay seçenekler sağlar.

    ![Kaynak denetimi için kullanılabilir git deposu seçeneklerini gösteren Takım Gezgini pencere](media/flask/step01-team-explorer.png)

    Kendi projeleriniz için istediğiniz hizmeti seçebilirsiniz. Bu öğreticide, öğreticinin tamamlanan örnek kodunun [Microsoft/Python-Sample-vs-Learning-Flask](https://github.com/Microsoft/python-sample-vs-learning-flask) deposunda gerçekleştiği GitHub 'ın kullanımı gösterilmektedir.

1. **Yayınlama** denetimlerinden herhangi birini seçerken **Takım Gezgini** daha fazla bilgi ister. Örneğin, bu öğretici için örnek yayımlarken, deponun kendisi oluşturulmalıdır, bu durumda depo URL 'SI ile **uzak depoya gönderim** seçeneği kullanılır.

    ![Var olan bir uzak depoya göndermek için Takım Gezgini pencere](media/flask/step01-push-to-github.png)

    Mevcut bir deponuz yoksa **GitHub 'Da Yayımla** ve **Azure DevOps 'a gönderim** seçenekleri, doğrudan Visual Studio içinden bir tane oluşturmanızı sağlar.

1. Bu öğreticide çalışırken, değişiklikleri yürütmek ve göndermek için Visual Studio 'daki denetimleri kullanarak düzenli aralıklarla habite ulaşın. Bu öğretici size uygun noktalarda hatırlatır.

> [!Tip]
> **Takım Gezgini** içinde hızlıca gezinmek için, kullanılabilir sayfaların açılır menüsünü görmek üzere üstbilgiyi seçin (Yukarıdaki **Resimleri okur veya** yukarıdaki görüntüleri **Gönder** ) seçeneğini belirleyin.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Soru: bir projenin başından itibaren kaynak denetimi kullanmanın avantajları nelerdir?

Cevap: başlangıçtan itibaren kaynak denetimini kullanarak, özellikle de uzak bir depo kullanıyorsanız, projenizin düzenli olarak şirket dışı yedeklemesini sağlar. Yalnızca yerel bir dosya sistemindeki bir projeyi korumanın aksine, kaynak denetimi tam bir değişiklik geçmişi ve tek bir dosyayı ya da projenin tamamını önceki bir duruma geri döndürmenin kolay bir özelliğini sağlar. Bu değişiklik geçmişi, gerilemelerin nedenini (test arızaları) belirlemenize yardımcı olur. Ayrıca, bir proje üzerinde birden fazla kişi çalışıyorsa, kaynak denetimi, üzerine yazma işlemlerini yönetirken ve çakışma çözümü sağladığından gereklidir. Son olarak, otomasyon bir form olan kaynak denetimi, yapıları, testi ve yayın yönetimini otomatikleştirmek için size en iyi şekilde ayarlanır. Bu aslında bir proje için DevOps kullanmanın ilk adımıdır ve giriş engelleri bu kadar düşük olduğundan, kaynak denetimini baştan kullanmanın gerçekten bir nedeni yoktur.

Otomasyon olarak kaynak denetimi hakkında daha fazla bilgi için bkz. [Truth 'Nın kaynağı: DevOps 'Daki depoların rolü](/archive/msdn-magazine/2016/september/mobile-devops-the-source-of-truth-the-role-of-repositories-in-devops), MSDN Magazine 'teki Web Apps için de geçerli olan mobil uygulamalar için yazılmış bir makaledir.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Soru: Visual Studio 'Nun yeni bir projeyi otomatik olarak çalıştırmasını engelleyebilir miyim?

Yanıt: Evet. Otomatik yürütmeyi devre dışı bırakmak için **Takım Gezgini** **Ayarlar** sayfasına gidin, **Git**  >  **genel ayarları**' nı seçin, **Varsayılan olarak Birleştirmeden sonra değişiklikleri Yürüt** etiketli seçeneği temizleyin ve ardından **Güncelleştir**' i seçin.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Adım 1-3: sanal ortam oluşturma ve kaynak denetiminden dışlama

Projeniz için kaynak denetimini yapılandırdığınıza göre, sanal ortamı, projenin gerektirdiği gerekli Flask paketlerini oluşturabilirsiniz. Ardından, ortam klasörünü kaynak denetiminden dışlamak için **Takım Gezgini** kullanabilirsiniz.

1. **Çözüm Gezgini**, **Python ortamları** düğümüne sağ tıklayın ve **sanal ortam ekle**' yi seçin.

    ![Çözüm Gezgini sanal ortam komutu Ekle](media/flask/step01-add-virtual-environment-command.png)

1. Bir **requirements.txt dosyası bulduğumuz** belirten bir Ileti Ile **sanal ortam ekle** iletişim kutusu görüntülenir. Bu ileti, Visual Studio 'Nun sanal ortamı yapılandırmak için bu dosyayı kullandığını gösterir.

    ![requirements.txt iletisiyle sanal ortam iletişim kutusu Ekle](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. Varsayılanları kabul etmek için **Oluştur** ' u seçin. (İsterseniz sanal ortamın adını değiştirebilirsiniz, bu, yalnızca alt klasörünün adını değiştirir ancak `env` Standart bir kuraldır.)

1. İstenirse, yönetici ayrıcalıklarına onay vermeniz gerekiyorsa, Visual Studio paketleri indirirken ve yüklerken birkaç dakika bekleyin. Bu durumda, Flask ve bağımlılıkları, 100 ' den fazla alt klasörde binlerce dosya hakkında genişlemekte. İlerlemeyi, Visual Studio **çıktı** penceresinde görebilirsiniz. Beklerken, aşağıdaki soru bölümlerini izleyin. Flask [yükleme](https://flask.palletsprojects.com/en/1.0.x/installation/#installation) sayfasında (Flask.pcocoo.org) Flask 'nın bağımlılıklarından oluşan bir açıklama da görebilirsiniz.

1. Visual Studio git denetimlerinde (durum çubuğunda), **Takım Gezgini** içindeki **değişiklikler** sayfasını açan değişiklikler göstergesini ( **99&#42;**) seçin.

    Sanal ortam yüzlerce değişikliğe göre oluşturulur, ancak siz (veya projeyi Klonladığınız herkes) her zaman ortamı *requirements.txt* yeniden oluşturabileceğinden kaynak denetimine bunlardan herhangi birini eklemeniz gerekmez.

    Sanal ortamı dışlamak için **env** klasörüne sağ tıklayın ve **Bu yerel öğeleri yoksay**' ı seçin.

    ![Kaynak denetimi değişikliklerinde sanal ortam yok sayılıyor](media/flask/step01-ignore-local-items.png)

1. Sanal ortamı dışladıktan sonra, kalan değişiklikler proje dosyası ve *. gitignore*' dir. *. Gitignore* dosyası, sanal ortam klasörü için eklenen bir giriş içerir. Bir farkı görmek için dosyaya çift tıklayabilirsiniz.

1. Bir işleme iletisi girin ve **Tümünü Kaydet** düğmesini seçin, ardından istediğiniz değişiklikleri uzak deponuza gönderin.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Soru: neden sanal ortam oluşturmak istiyorum?

Cevap: sanal bir ortam, uygulamanızın tam bağımlılıklarını yalıtmak için harika bir yoldur. Bu tür yalıtımlara genel bir Python ortamında çakışmalar önlenir ve hem test hem de işbirliği yardımcı olur. Zaman içinde, bir uygulama geliştirirken, çok sayıda faydalı Python paketini de bir araya getirebilirsiniz. Paketleri projeye özgü bir sanal ortamda tutarak, projenin kaynak denetimine dahil olan bu ortamı açıklayan *requirements.txt* dosyasını kolayca güncelleştirebilirsiniz. Proje, derleme sunucuları, dağıtım sunucuları ve diğer geliştirme bilgisayarları dahil olmak üzere başka bir bilgisayara kopyalandığında, ortamı yalnızca *requirements.txt* (ortamın kaynak denetiminde olması gerekmez) kullanarak yeniden oluşturmak kolaydır. Daha fazla bilgi için bkz. [sanal ortamları kullanma](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Soru: kaynak denetimine zaten kaydedilmiş bir sanal ortamı kaldırmak Nasıl yaparım? mı?

Cevap: Ilk olarak, klasörü hariç tutmak için *. gitignore* dosyanızı düzenleyin: ile birlikte, açıklama ile sonundaki bölümü bulun `# Python Tools for Visual Studio (PTVS)` ve sanal ortam klasörü için gibi yeni bir satır ekleyin `/BasicProject/env` . (Visual Studio **Çözüm Gezgini** dosyayı göstermediğinden, **dosyayı doğrudan dosya**  >  kullanarak açın **Açık**  >  **Dosya** menü komutu. Dosyayı **Takım Gezgini** içinden de açabilirsiniz: **Ayarlar** sayfasında **Depo ayarları**' nı seçin, **& öznitelik dosyalarını yoksay** bölümüne gidin ve sonra **. gitignore**' in yanındaki **Düzenle** bağlantısını seçin.

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

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Soru: diğer paketleri yükledikten sonra Visual Studio sanal ortamdan bir requirements.txt dosyası oluşturabilir mi?

Yanıt: Evet. **Python ortamları** düğümünü genişletin, sanal ortamınıza sağ tıklayıp **requirements.txtoluştur** komutunu seçin. Ortamı değiştirirken bu komutun düzenli aralıklarla kullanılması ve bu ortama bağlı diğer kod değişiklikleriyle birlikte kaynak denetimine *requirements.txt* değişiklikler yürütmesi yararlı olur. Bir yapı sunucusunda sürekli tümleştirme ayarlarsanız, ortamı her değiştirdiğinizde dosyayı oluşturmanız ve değişiklikleri uygulamanız gerekir.

## <a name="step-1-5-run-the-project"></a>Adım 1-5: projeyi çalıştırma

1. Visual Studio **'da hata**  >  **ayıklamayı Başlat** (**F5**) ' i seçin veya araç çubuğunda **Web sunucusu** düğmesini kullanın (gördüğünüz tarayıcı değişebilir):

    ![Visual Studio 'da Web sunucusu araç çubuğu düğmesini Çalıştır](media/tutorials-common/run-web-server-toolbar-button.png)

1. Her iki komut de bağlantı noktası ortam değişkenine rastgele bir bağlantı noktası numarası atar ve sonra çalışır `python app.py` . Kod, uygulamayı Flask geliştirme sunucusu içinde bu bağlantı noktasını kullanarak başlatır. Visual Studio hata ayıklayıcıyı başlatma dosyası olmayan bir iletiyle **başlatmazsa** , **Çözüm Gezgini** içinde **app.py** öğesine sağ tıklayın ve **başlangıç dosyası olarak ayarla**' yı seçin.

1. Sunucu başlatıldığında, sunucu günlüğünü görüntüleyen bir konsol penceresi açık görürsünüz. Sonra Visual Studio otomatik olarak bir tarayıcı açar `http://localhost:<port>` , burada işlev tarafından işlenmiş iletiyi görürsünüz `hello` :

    ![Flask proje varsayılan görünümü](media/flask/step01-first-run-success.png)

1. İşiniz bittiğinde, konsol penceresini kapatarak veya   >  Visual Studio 'da hata **ayıklamayı Durdur** komutunu kullanarak sunucuyu durdurun.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Soru: Hata Ayıkla menü komutlarının ve proje Python alt menüsünde sunucu komutlarının kullanımı arasındaki fark nedir?

Cevap: **hata ayıklama** menü komutları ve araç çubuğu düğmelerine ek olarak,   >  projenin bağlam menüsündeki Python **çalıştırma sunucusu** veya **Python**  >  **çalıştırma hata ayıklama sunucusu** komutlarını kullanarak sunucuyu da başlatabilirsiniz. Her iki komut de çalışan sunucu için yerel URL 'YI (localhost: bağlantı noktası) görebileceğiniz bir konsol penceresi açar. Ancak, bu URL ile bir tarayıcıyı el ile açmanız gerekir ve hata ayıklama sunucusunu çalıştırmak Visual Studio hata ayıklayıcıyı otomatik olarak başlatmamalıdır. Çalıştırmak istiyorsanız,   >  **işlemek için** hata ayıkla komutunu kullanarak, çalışan işleme daha sonra bir hata ayıklayıcı ekleyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu noktada, temel Flask projesi aynı dosyadaki başlangıç kodunu ve sayfa kodunu içerir. Bu iki kaygıyı ayırmak ve ayrıca şablonlar kullanarak HTML ve verileri ayırmak için idealdir.

> [!div class="nextstepaction"]
> [Görünümler ve sayfa şablonlarıyla Flask uygulaması oluşturma](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>Daha derin git

- [Flask hızlı başlangıç](https://flask.palletsprojects.com/en/1.0.x/quickstart/) (Flask.pocoo.org)
- GitHub 'daki öğretici kaynak kodu: [Microsoft/Python-Sample-vs-Learning-Flask](https://github.com/Microsoft/python-sample-vs-learning-flask)