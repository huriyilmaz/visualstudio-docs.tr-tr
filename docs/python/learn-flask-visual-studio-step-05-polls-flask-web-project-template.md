---
title: Visual Studio adım 5, Anketler proje şablonu Flask öğretici öğrenin
titleSuffix: ''
description: Visual Studio projeleri bağlamında Flask temelleri bir walkthrough, özellikle Anketler Flask Web Projesi ve Anketler Flask / Yeşim Web Projesi şablonları özellikleri.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c540dfef9d2d46bb621432b3e37438e0b6b07298
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "70154891"
---
# <a name="step-5-use-the-polls-flask-web-project-template"></a>Adım 5: Anketler Flask Web Projesi şablonu kullanın

**Önceki adım: [Flask Web Project şablonuna tam olarak kullanın](learn-flask-visual-studio-step-04-full-flask-project-template.md)**

Visual Studio'nun "Flask Web Project" şablonundan anlayınca, artık aynı kod tabanını temel alan üçüncü Flask şablonu olan "Polls Flask Web Project"e bakabilirsiniz.

Bu adımda nasıl öğrenirsiniz:

> [!div class="checklist"]
> - Şablondan bir proje oluşturun ve veritabanını başlatma (adım 5-1)
> - Veri modellerini anlama (adım 5-2)
> - Destek veri depolarını anlama (adım 5-3)
> - Anket ayrıntılarını ve sonuç görünümlerini anlama (adım 5-4)

Visual Studio aynı uygulamayı üreten "Polls Flask/Jade Web Project" şablonu da sağlar, ancak Jinja cazip motoru için Yeşim uzantısını kullanır. Ayrıntılar için Bkz. [Adım 4 - Flask/Jade Web Project şablonu.](learn-flask-visual-studio-step-04-full-flask-project-template.md#the-flaskjade-web-project-template)

## <a name="step-5-1-create-the-project"></a>Adım 5-1: Projeyi oluşturma

1. Visual Studio'da **Solution Explorer'a**gidin, bu eğitimde daha önce oluşturulan **LearningFlask** çözümüne sağ tıklayın ve**Yeni Proje** **Ekle'yi** > seçin. (Alternatif olarak, yeni bir çözüm kullanmak istiyorsanız, bunun yerine **Dosya** > **Yeni** > **Projesi'ni** seçin.)

1. Yeni proje iletişim kutusunda, **Polls Flask Web Project** şablonunu arayın ve seçin, projeyi "FlaskPolls" olarak adlandırın ve **Tamam'ı**seçin.

1. Visual Studio'daki diğer proje şablonları gibi, "Polls Flask Web Project" şablonu bir *requirements.txt* dosyası içerir, Visual Studio bu bağımlılıkları nereye yükleyebileceğinizi sorar. Seçeneği seçin, **sanal ortama yükle**ve Sanal Ortam **Ekle** iletişim kutusunda varsayılanları kabul etmek için **Oluştur'u** seçin. (Bu şablon flask yanı sıra azure depolama ve pymongo paketleri gerektirir; "Anketler Flask / Yeşim Web Projesi" de pyjade gerektirir.)

1. **Solution Explorer'daki** projeyi sağ tıklatarak ve **Başlangıç Projesi olarak Set'i**seçerek **FlaskPolls** projesini Visual Studio çözümü için varsayılan olarak ayarlayın. Kalın olarak gösterilen başlangıç projesi, hata ayıklamayı başlattığınızda çalıştırılan şeydir.

1. **Hata Ayıklama** > **Hata Ayıklama** **(F5)** seçeneğini belirleyin veya sunucuyu çalıştırmak için araç çubuğundaki **Web Sunucusu** düğmesini kullanın:

    ![Visual Studio'da web sunucusu araç çubuğu düğmesini çalıştırın](media/django/run-web-server-toolbar-button.png)

1. Şablon tarafından oluşturulan uygulama, üst gezinme çubuğunu kullanarak arasında gezindiğiniz Ana Sayfa, Hakkında ve İletişim olmak üzere üç sayfadan oluşur. Uygulamanın farklı bölümlerini incelemek için bir veya iki dakika ayırın (Hakkında ve İletişim sayfaları "Flask Web Project"e çok benzer ve daha fazla tartışılmaz).

    ![Polls Flask Web Project uygulamasının tam görünümü](media/flask/step06-full-app-view.png)

1. Ana sayfada, **Örnek Anketler Oluştur** düğmesi, *models/samples.json* sayfasında açıklanan üç farklı anketle uygulamanın veri deposunu başlangıç olarak sunar. Varsayılan olarak, uygulama her başlatıldığında sıfırlanan bir bellek veritabanı (About sayfasında gösterildiği gibi) kullanır. Uygulama, bu makalede daha sonra açıklandığı gibi Azure Depolama ve Mongo DB ile çalışmak için kod da içerir.

1. Veri deposunun başlatılmasını yaptıktan sonra, ana sayfada gösterildiği gibi farklı anketlerde oy verebilirsiniz (gezinme çubuğu ve altbilgi kısalık için atlanır):

    ![Veri deposu nun başlatılmasından sonra Anketler uygulamasının görünümü](media/flask/step06-polls-initialized.png)

1. Bir anket seçmek, belirli seçeneklerini görüntüler:

    ![Anket için oylama arabirimi](media/flask/step06-polls-voting-interface.png)

1. Oy kullandıktan sonra, uygulama bir sonuç sayfası gösterir ve yeniden oy kullanmanızı sağlar:

    ![Oylamadan sonra sonuç görünümü](media/flask/step06-polls-results.png)

1. Takip eden bölümler için uygulamayı çalışır durumda bırakabilirsiniz.

    Uygulamayı durdurmak ve kaynak [denetiminde değişiklikler yapmak](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)istiyorsanız, önce **Team Explorer'da** **Değişiklikler** sayfasını açın , sanal ortam için klasörü sağ tıklatın (muhtemelen **env),** ve **bu yerel öğeleri yoksay'ı**seçin.

### <a name="examine-the-project-contents"></a>Proje içeriğini inceleme

Daha önce de belirtildiği gibi. Visual Studio'daki diğer proje şablonlarını araştırdıysanız, "Polls Flask Web Project" şablonundan (ve "Polls Flask/Jade Web Project" şablonundan) oluşturulan bir projede ne varsa, tanıdık olmalıdır. Bu makaledeki ek adımlar, daha önemli değişiklikleri ve eklemeleri, yani veri modellerini ve ek görünümleri özetler.

## <a name="step-5-2-understand-the-data-models"></a>Adım 5-2: Veri modellerini anlama

Uygulamanın veri modelleri, Poll and Choice adlı Python sınıflarıdır ve *modellerde/\_\_init\_\_.py'de*tanımlanır. Anket, Seçim örnekleri koleksiyonunun kullanılabilir yanıtları temsil ettiği bir soruyu temsil eder. Anket ayrıca toplam oy sayısını (herhangi bir seçim için) ve görünüm oluşturmak için kullanılan istatistikleri hesaplama yöntemini de korur:

```python
class Poll(object):
    """A poll object for use in the application views and repository."""
    def __init__(self, key=u'', text=u''):
        """Initializes the poll."""
        self.key = key
        self.text = text
        self.choices = []
        self.total_votes = None

    def calculate_stats(self):
        """Calculates some statistics for use in the application views."""
        total = 0
        for choice in self.choices:
            total += choice.votes
        for choice in self.choices:
            choice.votes_percentage = choice.votes / float(total) * 100 \
                if total > 0 else 0
        self.total_votes = total

class Choice(object):
    """A poll choice object for use in the application views and repository."""
    def __init__(self, key=u'', text=u'', votes=0):
        """Initializes the poll choice."""
        self.key = key
        self.text = text
        self.votes = votes
        self.votes_percentage = None
```

Bu veri modelleri, uygulamanın görünümlerinin bir sonraki adımda açıklanan farklı destek veri depolarına karşı çalışmasını sağlayan genel soyutlamalardır.

## <a name="step-5-3-understand-the-backing-data-stores"></a>Adım 5-3: Destek veri depolarını anlama

"Polls Flask Web Project" şablonu tarafından oluşturulan uygulama bellekte, Azure tablo depolamasında veya Mongo DB veritabanında bir veri deposuna karşı çalıştırılabilir.

Veri depolama mekanizması aşağıdaki gibi çalışır:

1. Depo türü, "bellek", `REPOSITORY_NAME` "azuretablestore" veya "mongodb" olarak ayarlanabilen ortam değişkeni aracılığıyla belirtilir. *settings.py'daki* bir kod, varsayılan olarak "bellek" kullanarak adı alır. Destek mağazasını değiştirmek istiyorsanız, ortam değişkenini ayarlamanız ve uygulamayı yeniden başlatmanız gerekir.

    ```python
    from os import environ
    REPOSITORY_NAME = environ.get('REPOSITORY_NAME', 'memory')
    ```

1. *settings.py* kodu daha sonra `REPOSITORY_SETTINGS` bir nesneyi başharfe ait hale Azure tablo deposunu veya Mondo DB'yi kullanmak istiyorsanız, önce bu veri depolarını başka bir yerde başlatmanız, ardından uygulamaya mağazaya nasıl bağlanış yapılacağını söyleyen gerekli ortam değişkenlerini ayarlamanız gerekir:

    ```python
    if REPOSITORY_NAME == 'azuretablestorage':
        REPOSITORY_SETTINGS = {
            'STORAGE_NAME': environ.get('STORAGE_NAME', ''),
            'STORAGE_KEY': environ.get('STORAGE_KEY', ''),
            'STORAGE_TABLE_POLL': environ.get('STORAGE_TABLE_POLL', 'polls'),
            'STORAGE_TABLE_CHOICE': environ.get('STORAGE_TABLE_CHOICE', 'choices'),
        }
    elif REPOSITORY_NAME == 'mongodb':
        REPOSITORY_SETTINGS = {
            'MONGODB_HOST': environ.get('MONGODB_HOST', None),
            'MONGODB_DATABASE': environ.get('MONGODB_DATABASE', 'polls'),
            'MONGODB_COLLECTION': environ.get('MONGODB_COLLECTION', 'polls'),
        }
    elif REPOSITORY_NAME == 'memory':
        REPOSITORY_SETTINGS = {}
    else:
        raise ValueError('Unknown repository.')
    ```

1. *views.py'* de uygulama, veri deposunun `Repository` adını ve ayarlarını kullanarak bir nesneyi başlatmayı fabrika yöntemi olarak çağırır:

    ```python
    from FlaskPolls.models import PollNotFound
    from FlaskPolls.models.factory import create_repository
    from FlaskPolls.settings import REPOSITORY_NAME, REPOSITORY_SETTINGS

    repository = create_repository(REPOSITORY_NAME, REPOSITORY_SETTINGS)
    ```

1. Yöntem `factory.create_repository` *modelleri bulunur\factory.py*, sadece uygun depo modülü ithal, sonra bir `Repository` örnek oluşturur:

    ```python
    def create_repository(name, settings):
        """Creates a repository from its name and settings. The settings
        is a dictionary where the keys are different for every type of repository.
        See each repository for details on the required settings."""
        if name == 'azuretablestorage':
            from .azuretablestorage import Repository
        elif name == 'mongodb':
            from .mongodb import Repository
        elif name == 'memory':
            from .memory import Repository
        else:
            raise ValueError('Unknown repository.')

        return Repository(settings)
    ```

1. Her veri deposuna özgü `Repository` sınıfın uygulamaları *modeller\azuretablestorage.py,* *models\mongodb.py*ve *models\memory.py*bulunabilir. Azure depolama uygulaması azure depolama paketini kullanır; Mongo DB uygulaması pymongo paketini kullanır. Adım 5-1'de belirtildiği gibi, her iki paket de proje şablonunun *gereksinimleri.txt* dosyasına dahildir. Ayrıntıları keşfetmek okuyucu için bir egzersiz olarak bırakılır.

Kısacası, `Repository` sınıf veri deposunun özelliklerini soyutlar ve uygulama, üç uygulamadan hangisini kullanacağını seçmek ve yapılandırmak için çalışma zamanında ortam değişkenlerini kullanır.

Aşağıdaki adımlar, istenirse, proje şablonu tarafından sağlanan üç veri deposundan farklı bir veri deposu için destek ekler:

1. Sınıfın *memory.py* temel arabirimine sahip olmak için memory.py `Repository` yeni bir dosyaya kopyalayın.
1. Sınıfın uygulamasını, kullanmakta olduğunuz veri deposuna uygun olarak değiştirin.
1. Eklenen *factory.py* veri deponuzun adını tanıyan ve uygun modülü içe aktaran başka bir `elif` servis talebi eklemek için factory.py değiştirin.
1. Ortam değişkenindeki `REPOSITORY_NAME` başka bir adı tanımak `REPOSITORY_SETTINGS` ve buna göre baş harfe getirmek için *settings.py* değiştirin.

### <a name="seed-the-data-store-from-samplesjson"></a>Data deposunu samples.json'dan tohumla

Başlangıçta, seçilen herhangi bir veri deposunda anket bulunmadığından, uygulamanın ana sayfası **Örnek Anketler Oluştur** düğmesiyle birlikte yok etme **iletisini** gösterir. Ancak düğmeyi seçtikten sonra, görünüm kullanılabilir anketleri görüntülemek için değişir. Bu anahtar *şablonlar\index.html* (kısalık için atlanan bazı boş satırlar) koşullu etiketler ilerler:

```html
{% extends "layout.html" %}
{% block content %}
<h2>{{title}}.</h2>

{% if polls %}
<table class="table table-hover">
    <tbody>
        {% for poll in polls %}
        <tr>
            <td>
                <a href="/poll/{{poll.key}}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<p>No polls available.</p>
<br />
<form action="/seed" method="post">
    <button class="btn btn-primary" type="submit">Create Sample Polls</button>
</form>
{% endif %}
{% endblock %}
```

Şablondaki `polls` `repository.get_polls`değişken, veri deposu başaçılana kadar hiçbir şey döndürmeyen bir çağrıdan gelir.

**Örnek Anketler Oluştur** düğmesini seçmek /seed URL'sine yönlendirilir. Bu rotanın işleyicisi *views.py*tanımlanır:

```python
@app.route('/seed', methods=['POST'])
def seed():
    """Seeds the database with sample polls."""
    repository.add_sample_polls()
    return redirect('/')
```

Arama, `repository.add_sample_polls()` seçtiğiniz veri deposu için `Repository` belirli uygulamalardan birinde sona erer. Her uygulama `_load_samples_json` *\_\_modelleri\_\_init .py* bulunan yöntemi *çağırır modelleri\samples.json* dosyasını belleğe yüklemek için, `Poll` sonra `Choice` gerekli ve nesneleri veri deposunda oluşturmak için bu verileri üzerinden yineler.

Bu işlem tamamlandıktan `redirect('/')` sonra, `seed` yöntemdeki deyim ana sayfaya geri döner. Artık `repository.get_polls` bir veri nesnesi döndürdeğinden, *şablonlar\index.html'deki* koşullu etiketler artık anketleri içeren bir tablo işler.

### <a name="question-how-does-one-add-new-polls-to-the-app"></a>Soru: Uygulamaya nasıl yeni anketler eklenir?

Yanıt: Proje şablonu aracılığıyla sağlanan uygulama, anket ekleme veya düzenleme olanağı içermez. Yeni başlatma verileri oluşturmak için *models\samples.json'u* değiştirebilirsiniz, ancak bunu yapmak veri deposunu sıfırlamak anlamına gelir. Düzenleme özelliklerini uygulamak için, gerekli `Repository` `Choice` ve `Poll` örnekleri oluşturmak için sınıf arabirimini yöntemlerle genişletmeniz ve ardından bu yöntemleri kullanan ek sayfalarda bir web-i ii uygulamanız gerekir.

## <a name="step-5-4-understand-the-poll-detail-and-results-views"></a>Adım 5-4: Anket ayrıntılarını ve sonuç görünümlerini anlama

"Polls Flask Web Project" ve "Polls Flask/Jade Web Project" şablonları tarafından oluşturulan görünümlerin çoğu, Bu eğitimde daha önce birlikte çalıştığınız "Flask Web Project" (veya "Flask/Jade Web Project") şablonu tarafından oluşturulan görünümlere oldukça benzerdir. Önceki bölümde, başlangıç düğmesini veya anket listesini göstermek için ana sayfanın nasıl uygulandığını da öğrendiniz.

Burada kalan tek bir anketin oy verme (ayrıntıları) ve sonuç görünümünü incelemektir.

Ana sayfadan bir anket seçtiğinizde, uygulama URL/poll/\<\> *anahtarına* doğru identifer olarak yönlendirilir. *views.py,* işlevin `details` hem GET hem de istekler için bu URL yönlendirmesini işlemek üzere atandığını görebilirsiniz. Ayrıca, URL rotasında kullanmanın, `<key>` bu formun herhangi bir rotasını aynı işleve eşlediğini ve aynı adıtaşıyan işleviçin bir bağımsız değişken oluşturduğunu da görebilirsiniz:

```python
@app.route('/poll/<key>', methods=['GET', 'POST'])
def details(key):
    """Renders the poll details page."""
    error_message = ''
    if request.method == 'POST':
        try:
            choice_key = request.form['choice']
            repository.increment_vote(key, choice_key)
            return redirect('/results/{0}'.format(key))
        except KeyError:
            error_message = 'Please make a selection.'

    return render_template(
        'details.html',
        title='Poll',
        year=datetime.now().year,
        poll=repository.get_poll(key),
        error_message=error_message,
    )
```

Bir anket (GET isteklerini) göstermek için, bu işlev yalnızca anketin `choices` dizisini yineleyen *template\details.html'i*çağırır ve her biri için bir radyo düğmesi oluşturur.

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% if error_message %}
<p class="text-danger">{{error_message}}</p>
{% endif %}

<form action="/poll/{{poll.key}}" method="post">
    {% for choice in poll.choices %}
    <div class="radio">
        <label>
            <input type="radio" name="choice" id="choice{{choice.key}}" value="{{choice.key}}" />
            {{ choice.text }}
        </label>
    </div>
    {% endfor %}
    <br />
    <button class="btn btn-primary" type="submit">Vote</button>
</form>

{% endblock %}
```

Oy **düğmesi** `type="submit"`, seçerek bir POST isteği işlevine bir kez daha yönlendirilen `details` aynı URL'ye geri oluşturur. Ancak bu kez, form verilerinden seçimi ayıklar ve /results/choice'a\<\>yönlendirir.

/results/\<key\> URL daha sonra `results` *views.py*işlevine yönlendirilir , daha `calculate_stats` sonra anketin yöntemini çağırır ve oluşturma için *template\results.html* kullanır:

```python
@app.route('/results/<key>')
def results(key):
    """Renders the results page."""
    poll = repository.get_poll(key)
    poll.calculate_stats()
    return render_template(
        'results.html',
        title='Results',
        year=datetime.now().year,
        poll=poll,
    )
```

*Results.html* şablonu, kendi payına, sadece anketin seçimleri ile yinelenir ve her biri için bir ilerleme çubuğu oluşturur:

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% for choice in poll.choices %}
<div class="row">
    <div class="col-sm-5">{{choice.text}}</div>
    <div class="col-sm-5">
        <div class="progress">
            <div class="progress-bar" role="progressbar" aria-valuenow="{{choice.votes}}" aria-valuemin="0" aria-valuemax="{{poll.total_votes}}" style="width: {{choice.votes_percentage}}%;">
                {{choice.votes}}
            </div>
        </div>
    </div>
</div>
{% endfor %}

<br />
<a class="btn btn-primary" href="/poll/{{poll.key}}">Vote again?</a>

{% endblock %}
```

## <a name="next-steps"></a>Sonraki adımlar

> [!Note]
> Bu öğretici boyunca kaynak kontrolü için Visual Studio çözüm taahhüt oldum, şimdi başka bir taahhüt yapmak için iyi bir zaman. Çözümünüz GitHub'daki öğretici kaynak koduyla eşleşmelidir: [Microsoft/python-sample-vs-learning-flask.](https://github.com/Microsoft/python-sample-vs-learning-flask)

Visual Studio'da "Blank Flask Web Project", "Flask[/Jade] Web Project" ve "Polls Flask[/Jade] Web Project" şablonlarının tamamını araştırdınız. Görünümleri, şablonları ve yönlendirmeyi kullanma gibi Flask'ın tüm temel lerini öğrendiniz ve destek veri depolarını nasıl kullanacağınızı gördünüz. Artık ihtiyacınız olan herhangi bir görünüm ve modelile kendi web uygulamaüzerinde başlamak gerekir.

Geliştirme bilgisayarınızda bir web uygulaması çalıştırmak, uygulamayı müşterilerinizin kullanımına sunmayı sağlamanın yalnızca bir adımıdır. Sonraki adımlar aşağıdaki görevleri içerebilir:

- Web uygulamasını Azure Uygulama Hizmeti gibi bir üretim sunucusuna dağıtın. Bkz. [Azure Uygulama Hizmetinde Yayımla](publishing-python-web-applications-to-azure-from-visual-studio.md).

- PostgreSQL, MySQL ve SQL Server gibi başka bir üretim düzeyinde veri deposu kullanan (tümü Azure'da barındırılan) bir depo uygulaması ekleyin. [Python için Azure SDK'yı,](/azure/python/) tablolar ve lekeler gibi Azure depolama hizmetlerinin yanı sıra Cosmos DB ile çalışmak için de kullanabilirsiniz.

- Azure DevOps gibi bir hizmette sürekli tümleştirme/sürekli dağıtım ardışık bir şekilde ayarlayın. Kaynak denetimiyle (Azure Repos veya GitHub veya başka bir yerden) çalışmaya ek olarak, birim testlerinizi serbest bırakma için ön koşul olarak otomatik olarak çalıştıracak bir Azure DevOps Projesi'ni yapılandırabilir ve ayrıca ardışık hattı bir evreleme sunucusuna dağıtacak şekilde yapılandırabilirsiniz. üretime dağıtmadan önce ek testler. Ayrıca Azure DevOps, App Insights gibi izleme çözümleriyle bütünleşir ve çevik planlama araçlarıyla tüm döngüyü kapatır. Daha fazla bilgi için, [Azure DevOps Projeleri ile Python için bir CI/CD ardışık alanı oluşturma](/azure/devops-project/azure-devops-project-python?view=vsts) ve ayrıca genel Azure [DevOps belgeleri](/azure/devops/?view=vsts)ne bakın.
