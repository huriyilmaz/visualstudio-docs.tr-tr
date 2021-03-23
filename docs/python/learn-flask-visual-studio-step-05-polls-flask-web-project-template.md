---
title: Visual Studio 'da Flask öğreticisini öğrenin 5. adım, proje şablonunu yoklamalar
titleSuffix: ''
description: Visual Studio projeleri bağlamında Flask temel bilgileri, özellikle Flask Web projesini yoklayıp ve Flask/Jade Web projesi şablonlarının yokladığı bir adım adım.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
monikerRange: vs-2017
ms.workload:
- python
- data-science
ms.openlocfilehash: fd67e527ccf62de17dc15a5415f573c9622a51e9
ms.sourcegitcommit: f1dff6c4532c43b0444aa12ea57e90bb7dba6fba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805984"
---
# <a name="step-5-use-the-polls-flask-web-project-template"></a>5. Adım: Flask Web projesi şablonunu yoklayıp kullanın

**Önceki adım: [tam Flask Web projesi şablonunu kullanın](learn-flask-visual-studio-step-04-full-flask-project-template.md)**

Visual Studio 'nun "Flask Web projesi" şablonunu anlamış olursunuz, ancak aynı kod tabanında derleme yapmak için "Flask Web projesini yoklar" şeklinde üçüncü Flask şablonuna bakabilirsiniz.

Bu adımda şunları yapmayı öğreneceksiniz:

> [!div class="checklist"]
> - Şablondan bir proje oluşturun ve veritabanını başlatın (adım 5-1)
> - Veri modellerini anlama (adım 5-2)
> - Veri depolarını yedeklemeyi anlama (adım 5-3)
> - Yoklama ayrıntılarını ve sonuçlar görünümlerini anlayın (adım 5-4)

Visual Studio aynı zamanda aynı uygulamayı üreten "Flask/Jade Web projesini Yokladır" şablonunu da sağlar, ancak Jınja şablon oluşturma altyapısı için Jade uzantısını kullanır. Ayrıntılar için bkz. [4. adım-Flask/Jade Web projesi şablonu](learn-flask-visual-studio-step-04-full-flask-project-template.md#the-flaskjade-web-project-template).

## <a name="step-5-1-create-the-project"></a>Adım 5-1: projeyi oluşturma

1. Visual Studio 'da **Çözüm Gezgini** gidin, bu öğreticide daha önce oluşturulan **learningflask** çözümüne sağ tıklayın ve   >  **Yeni proje** Ekle ' yi seçin. (Alternatif olarak, yeni bir çözüm kullanmak isterseniz **Dosya**  >  ' yı seçin. **Yeni**  >  Bunun yerine **Proje** .)

1. Yeni proje iletişim kutusunda, **Flask Web projesi şablonunu yoklayıp** seçin, "Flaskyoklamaları" projesini çağırın ve **Tamam**' ı seçin.

1. Visual Studio 'daki diğer proje şablonları gibi, "Flask Web projesi yoklamaları" şablonu bir *requirements.txt* dosyası Içeriyorsa, Visual Studio bu bağımlılıkların nereye yükleneceğini sorar. **Bir sanal ortama yükleyip**, sanal **ortam ekle** iletişim kutusunda Varsayılanları kabul etmek için **Oluştur** seçeneğini belirleyin. (Bu şablon, Azure-Storage ve pymongo paketlerinin yanı sıra Flask gerektirir; "Flask/Jade Web projesini yoklamalar" da pyjade gerektirir.)

1. **Çözüm Gezgini** ' de projeye sağ tıklayıp **Başlangıç projesi olarak ayarla**' yı seçerek, **Flaskyoklamaları** projesini Visual Studio çözümü için varsayılan olacak şekilde ayarlayın. Kalın olarak gösterilen başlangıç projesi, hata ayıklayıcıyı başlattığınızda çalıştırılan şeydir.

1. Sunucuyu çalıştırmak için **hata ayıklama**  >  **başlatma hata ayıklamayı Başlat** (**F5**) veya araç çubuğundaki **Web sunucusu** düğmesini seçin:

    ![Visual Studio 'da Web sunucusu araç çubuğu düğmesini Çalıştır](media/django/run-web-server-toolbar-button.png)

1. Şablon tarafından oluşturulan uygulamanın, en üst gezinti çubuğunu kullanarak gittiğiniz üç sayfası, ev, bilgi ve Ilgili kişi vardır. Uygulamanın farklı parçalarını incelemek için bir dakika veya iki dakikanızı alın (hakkında ve Ilgili sayfalar "Flask web projesine" benzer ve daha fazla açıklanmıyor).

    ![Bir Flask Web projesi uygulamasının yokladığı tam görünüm](media/flask/step06-full-app-view.png)

1. Giriş sayfasında, **örnek yoklamalar oluştur** düğmesi, uygulamanın veri deposunu, sayfada *modeller/samples.js* bölümünde açıklanan üç farklı yoklamalar ile başlatır. Varsayılan olarak, uygulama, uygulama her yeniden başlatıldığında sıfırlanarak bir bellek içi veritabanı (hakkında sayfasında gösterildiği gibi) kullanır. Uygulama, bu makalenin ilerleyen kısımlarında açıklandığı gibi Azure Storage ve Mongo DB ile çalışmak için de kod içerir.

1. Veri deposunu başlatıldıktan sonra, giriş sayfasında gösterildiği gibi farklı yoklamalarda oy verebilirsiniz (gezinme çubuğu ve altbilgisi breçekimi için atlanır):

    ![Veri deposu başlatıldıktan sonra yoklamalar uygulamasının görünümü](media/flask/step06-polls-initialized.png)

1. Bir yoklamayı seçtiğinizde belirli seçimler görüntülenir:

    ![Yoklama için oylama arabirimi](media/flask/step06-polls-voting-interface.png)

1. Oyladıktan sonra, uygulama bir sonuç sayfası gösterir ve yeniden oylamaya olanak tanır:

    ![Oylama sonrasında Sonuçlar görünümü](media/flask/step06-polls-results.png)

1. Uygulamanın, izleyen bölümler için çalışır durumda kalmasını sağlayabilirsiniz.

    Uygulamayı durdurmak ve [kaynak denetimine değişiklikleri uygulamak](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)istiyorsanız, önce **Takım Gezgini** içindeki **değişiklikler** sayfasını açın, sanal ortam (Belki de **env**) klasörüne sağ tıklayın ve **Bu yerel öğeleri yoksay**' ı seçin.

### <a name="examine-the-project-contents"></a>Proje içeriğini inceleyin

Daha önce belirtildiği gibi. Visual Studio 'daki diğer proje şablonlarını araştırdıysanız, "Flask Web projesi" şablonundan oluşturulan bir projede (ve "Flask/Jade Web projesini yoklamalar" şablonunun) büyük bir bölümü tanıdık gelmelidir. Bu makaledeki ek adımlar, veri modelleri ve ek görünümler gibi daha önemli değişiklikler ve eklemeler özetler.

## <a name="step-5-2-understand-the-data-models"></a>Adım 5-2: veri modellerini anlama

Uygulamanın veri modelleri,, *modeller/ \_ \_ init \_ \_ . Kopyala*' da tanımlanan yoklama ve seçim adlı Python sınıflarıdır. Bir yoklama, bir seçim örnekleri koleksiyonu kullanılabilir yanıtları temsil eden bir soruyu temsil eder. Bir yoklama Ayrıca toplam oy sayısını (herhangi bir seçim için) ve görünümleri oluşturmak için kullanılan istatistikleri hesaplamak için bir yöntemi tutar:

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

Bu veri modelleri, uygulamanın görünümlerinin bir sonraki adımda açıklanan farklı türlerde veri depolarına karşı çalışmasına izin veren genel soyutlamalar olur.

## <a name="step-5-3-understand-the-backing-data-stores"></a>Adım 5-3: veri depolarını yedeklemeyi anlama

"Flask Web projesi yoklamaları" şablonu tarafından oluşturulan uygulama, bellekte, Azure Tablo depolamada veya bir Mongo DB veritabanında bulunan bir veri deposuna karşı çalışabilir.

Veri depolama mekanizması aşağıdaki gibi çalışmaktadır:

1. Depo türü, `REPOSITORY_NAME` "Memory", "azuretablestore" veya "MongoDB" olarak ayarlanabilir ortam değişkeni aracılığıyla belirtilir. *Settings.py* ' deki bir kod, varsayılan olarak "bellek" kullanarak adı alır. Yedekleme deposunu değiştirmek istiyorsanız, ortam değişkenini ayarlamanız ve uygulamayı yeniden başlatmanız gerekir.

    ```python
    from os import environ
    REPOSITORY_NAME = environ.get('REPOSITORY_NAME', 'memory')
    ```

1. *Settings.py* kodu daha sonra bir `REPOSITORY_SETTINGS` nesnesi başlatır. Azure Tablo mağazasını veya Mondo DB 'yi kullanmak istiyorsanız, önce bu veri depolarını başka bir yerde başlatmalısınız, sonra uygulamaya nasıl bağlanacağınızı belirten gerekli ortam değişkenlerini ayarlamanız gerekir:

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

1. *Views.py*' de, uygulama, `Repository` veri deposunun adını ve ayarlarını kullanarak bir nesneyi başlatmak için bir fabrika yöntemi çağırır:

    ```python
    from FlaskPolls.models import PollNotFound
    from FlaskPolls.models.factory import create_repository
    from FlaskPolls.settings import REPOSITORY_NAME, REPOSITORY_SETTINGS

    repository = create_repository(REPOSITORY_NAME, REPOSITORY_SETTINGS)
    ```

1. `factory.create_repository`Yöntemi, yalnızca uygun depo modülünü içeri aktaran *models\factory.exe* içinde bulunur, ardından bir `Repository` örnek oluşturur:

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

1. `Repository`Her bir veri deposuna özgü sınıfının uygulamaları *models\azuretablestorage.py*, *models\mongodb.exe* ve *models\memory.exe* içinde bulunabilir. Azure depolama uygulama, Azure depolama paketini kullanır; Mongo DB uygulama, pymongo paketini kullanır. Adım 5-1 ' de belirtildiği gibi, her iki paket de proje şablonunun *requirements.txt* dosyasına dahil edilir. Ayrıntıları keşfetmek, okuyucu için bir alıştırma olarak kalır.

Kısaca, `Repository` sınıfı veri deposunun özelliklerini soyutlar ve uygulama, çalışma zamanında ortam değişkenlerini kullanarak kullanılacak üç uygulamayı seçer ve yapılandırır.

Aşağıdaki adımlar, Eğer istenirse, proje şablonu tarafından sağlandığımız üç farklı veri deposu için destek ekler:

1. Sınıfın temel arabirimine sahip olmak için *Memory.py* öğesini yeni bir dosyaya kopyalayın `Repository` .
1. Sınıfın uygulamasını, kullanmakta olduğunuz veri deposuna uygun olarak değiştirin.
1. *Factory.py* `elif` ' i değiştirerek, eklenen veri deponuzda adını tanıyan başka bir durum ekleyin ve uygun modülü içeri aktarır.
1. *Settings.py* öğesini ortam değişkeninde başka bir adı tanıyacak şekilde değiştirin `REPOSITORY_NAME` ve `REPOSITORY_SETTINGS` uygun şekilde başlatın.

### <a name="seed-the-data-store-from-samplesjson"></a>samples.jsüzerindeki veri deposunu temel alarak

Başlangıçta, seçilen tüm veri depolarıyla hiçbir yoklama yoktur, bu nedenle uygulamanın giriş sayfasında **örnek yoklamalar oluştur** düğmesi Ile birlikte **hiçbir yoklama yok** iletisi görüntülenir. Ancak düğmeyi seçtiğinizde, Görünüm kullanılabilir yoklamaları görüntülenecek şekilde değişir. Bu anahtar *templates\index.html* içindeki Koşullu Etiketler aracılığıyla gerçekleşir (breçekimi için bazı boş satırlar hariç):

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

`polls`Şablondaki değişken, `repository.get_polls` veri deposu başlatılana kadar hiçbir şey döndüren bir çağrısından gelir.

**Örnek yoklamalar oluştur** düğmesinin seçilmesi/Seed URL 'sine gider. Bu yolun işleyicisi  *views.py* içinde tanımlanmıştır:

```python
@app.route('/seed', methods=['POST'])
def seed():
    """Seeds the database with sample polls."""
    repository.add_sample_polls()
    return redirect('/')
```

' A yapılan çağrı, `repository.add_sample_polls()` `Repository` seçtiğiniz veri deponuzdaki belirli uygulamalardan birini sonlandırır. Her uygulama, `_load_samples_json` dosyadaki *models\samples.js* belleğe yüklemek *için \_ \_ Init \_ \_ . Kopyala* içinde bulunan yöntemi çağırır, ardından `Poll` veri deposunda gerekli ve nesneleri oluşturmak için bu verileri yineler `Choice` .

İşlem tamamlandıktan sonra, `redirect('/')` `seed` yöntemindeki ifade giriş sayfasına geri gider. `repository.get_polls`Artık bir veri nesnesi döndürdüğünden, *templates\index.html* içindeki Koşullu Etiketler artık yoklamaları içeren bir tablo oluşturur.

### <a name="question-how-does-one-add-new-polls-to-the-app"></a>Soru: bir uygulama uygulamaya nasıl yeni yoklamalar ekler?

Cevap: proje şablonu aracılığıyla belirtilen uygulama, yoklamaları ekleme veya düzenlemeyle ilgili bir tesis içermez. Yeni başlatma verileri oluşturmak için *models\samples.jsüzerinde* değişiklik yapabilirsiniz, ancak bunu yapmak veri deposunun sıfırlanması anlamına gelir. Özellikleri Düzenle özelliğini uygulamak için, `Repository` gerekli ve örnekleri oluşturmak üzere sınıf arabirimini yöntemlerle genişletmeli `Choice` ve `Poll` ardından bu yöntemleri kullanan ek sayfalarda bir kullanıcı arabirimi uygulamalısınız.

## <a name="step-5-4-understand-the-poll-detail-and-results-views"></a>Adım 5-4: yoklama ayrıntılarını ve sonuçlar görünümlerini anlayın

"Flask Web projesini Yoklat" ve "Flask/Jade Web projesi" şablonlarını oluşturan görünümlerin çoğu, bu öğreticide daha önce ile çalıştığınız "Flask Web projesi" (veya "Flask/Jade Web projesi") şablonu tarafından oluşturulan görünümlere oldukça benzerdir. Önceki bölümde, giriş sayfasının başlatma düğmesini veya yoklamalar listesini göstermek için nasıl uygulandığını de öğrenirsiniz.

Burada kalan özellikler, tek bir yoklamada oylama (Ayrıntılar) ve sonuç görünümünü incelemektir.

Giriş sayfasından bir yoklama seçtiğinizde, uygulama/Poll/} URL 'sine gider ve bu, \<key\> bir yoklama için  benzersiz bir tanımlayıcı olarak kullanılır. *Views.py* ' de, `details` işlevin hem Get hem de ISTEKLER için bu URL yönlendirmeyi işlemek üzere atandığını görebilirsiniz. Ayrıca `<key>` , URL rotasında kullanarak bu formun tüm rotasını aynı işleve eşler ve aynı ada sahip işleve bir bağımsız değişken üretir:

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

Bir yoklamayı (GET istekleri) göstermek için, bu işlev yalnızca yoklama dizisinin üzerinde dolaşır `choices` , her biri için bir radyo düğmesi oluşturaraktemplates\details.html üzerine çağrı yaparsınız.

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

**Oy** düğmesi olduğundan `type="submit"` , bir `details` kez daha sonra işlevine yönlendirilen aynı URL 'ye bir post isteği gönderir. Ancak, bu kez, form verilerinden seçimi ayıklar ve/Results/adresine yeniden yönlendirir \<choice\> .

/Results/ \<key\> URL daha sonra `results` *views.py* içindeki işleve yönlendirilir. Bu, daha sonra yoklamada `calculate_stats` yöntemi çağırır ve işleme için *templates\results.html* kullanır:

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

Bölümü için *results.html* şablonu, yoklamaya ilişkin seçimler boyunca yinelenir ve her biri için bir ilerleme çubuğu oluşturur:

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
> Visual Studio çözümünüzü Bu öğreticinin tamamında kaynak denetimine uyguladıysanız, başka bir işleme yapmak iyi bir zaman olabilir. Çözümünüz GitHub 'daki öğretici kaynak kodu ile eşleşmelidir: [Microsoft/Python-Sample-vs-Learning-Flask](https://github.com/Microsoft/python-sample-vs-learning-flask).

Artık "boş Flask Web projesinin", "Flask [/Jade] Web projesinin" tamamını incelediniz ve Visual Studio 'daki "Flask [/Jade] Web projesi" şablonlarını araştırdık. Flask 'nin görünümlerini, şablonlarını ve yönlendirmeyi kullanma gibi tüm temel bilgilerini öğrendiniz ve veri depolarının nasıl kullanılacağını gördünüz. Artık ihtiyacınız olan herhangi bir görünüm ve modelle kendi Web uygulamasını kullanmaya başlamanızı öneririz.

Geliştirme bilgisayarınızda bir Web uygulaması çalıştırmak, uygulamayı müşterileriniz için kullanılabilir hale getirmek için yalnızca bir adımdır. Sonraki adımlarda aşağıdaki görevler bulunabilir:

- Web uygulamasını Azure App Service gibi bir üretim sunucusuna dağıtın. Bkz. [Azure App Service yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md).

- PostgreSQL, MySQL ve SQL Server (tümü Azure üzerinde barındırılabilen) gibi başka bir üretim düzeyi veri deposu kullanan bir depo uygulamasını ekleyin. Ayrıca, [Python Için Azure SDK 'sını](/azure/python/) tablolar ve Bloblar gibi Azure depolama hizmetleriyle ve Cosmos DB de kullanabilirsiniz.

- Azure DevOps gibi bir hizmette sürekli tümleştirme/sürekli dağıtım işlem hattı ayarlayın. Kaynak denetimiyle (Azure Repos veya GitHub ya da başka bir yerde) çalışmaya ek olarak, bir Azure DevOps projesini, birim testlerinizi bir ön koşul olarak otomatik olarak çalıştıracak şekilde yapılandırabilir ve ayrıca işlem hattını üretime dağıtmadan önce ek testler için bir hazırlama sunucusuna dağıtılacak şekilde yapılandırabilirsiniz. Azure DevOps, Ayrıca, App Insights gibi izleme çözümleriyle tümleştirilir ve çevik planlama araçlarıyla tüm döngüyü kapatır. Daha fazla bilgi için bkz. [Python için BIR CI/CD işlem hattı oluşturma Azure DevOps Projeleri](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true) ve ayrıca genel [Azure DevOps belgeleri](/azure/devops/?view=vsts&preserve-view=true).
