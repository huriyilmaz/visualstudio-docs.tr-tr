---
title: 6. adım olan Yoklamalar proje Visual Studio Django öğreticisini öğrenin
titleSuffix: ''
description: Visual Studio projeleri bağlamında Django temel bilgileri, özellikle de yönetim özelleştirmesi gibi Polls Django Web Project şablonunun özellikleriyle ilgili bir kılavuz.
ms.date: 11/19/2018
ms.topic: tutorial
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
monikerRange: vs-2017
ms.workload:
- python
- data-science
ms.openlocfilehash: b53fd936800c1890108c24fc9a4cbaefa8c16e5f
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129968598"
---
# <a name="step-6-use-the-polls-django-web-project-template"></a>6. Adım: Polls Django Web Project kullanma

**Önceki adım: [Django'da kullanıcıların kimliğini doğrulama](learn-django-in-visual-studio-step-05-django-authentication.md)**

Visual Studio'nin "Django Web Project" şablonunu anlamasıyla, artık aynı kod tabanını temel alan ve bir veritabanıyla çalışmayı gösteren üçüncü Django şablonu olan "Polls Django Web Project" şablonuna bakabilirsiniz.

Bu adımda şunların nasıl olduğunu öğreniriz:

> [!div class="checklist"]
> - Şablondan proje oluşturma ve veritabanını başlatma (6-1. adım)
> - Veri modellerini anlama (6-2. adım)
> - Geçişleri uygulama (6-3. adım)
> - Proje şablonu tarafından oluşturulan görünümleri ve sayfa şablonlarını anlama (6-4. adım)
> - Özel yönetim arabirimi oluşturma (6-5. adım)

Bu şablon kullanılarak oluşturulan bir proje, Django belgelerde ilk [Django](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) uygulamanızı yazma öğreticisini takip edinerek elde etmek istediğinize benzer. Web uygulaması, kullanıcıların yoklamaları görüntülemesini ve bunları oylamalarını sağlayan genel bir sitenin yanı sıra, yoklamaları yönetebilirsiniz özel bir yönetim arabirimi içerir. "Django Web Project" şablonuyla aynı kimlik doğrulama sistemini kullanır ve aşağıdaki bölümlerde incelenince Django modellerini kullanarak veritabanını daha fazla kullanır.

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>6-1. Adım: Projeyi oluşturma ve veritabanını başlatma

1. Bu Visual Studio' **Çözüm Gezgini** gidin, bu öğreticide daha önce oluşturulan **LearningDjango** çözümüne sağ tıklayın ve Yeni Ekle'yi  >  **Project.** (Alternatif olarak, yeni bir çözüm kullanmak için Dosya'yi **seçin**  >  **Yeni**  >  **Project.)**

1. Yeni proje iletişim kutusunda **Polls Django Web** Project şablonunu arayın ve seçin, projeyi "DjangoPolls" olarak arayın ve Tamam'ı **seçin.**

1. Visual Studio'daki diğer proje şablonları gibi "Polls Django Web Project" şablonu da *birrequirements.txt* dosyası içerir ve Visual Studio bu bağımlılıkların nereye yük olacağını sorar. Sanal ortama yükle **seçeneğini belirleyin ve Sanal Ortam** Ekle iletişim kutusunda **Oluştur'a** **seçerek** varsayılanları kabul edersiniz.

1. Python sanal ortamı ayarlamayı tamamlarsa, veritabanını  başlatmakreadme.htmlbir Django süper kullanıcısı (yani bir yönetici) oluşturmak için görüntülenenreadme.htmlyönergeleri izleyin. Adımlar önce **Çözüm Gezgini'daki** **DjangoPolls** projesine sağ tıklar, **Python** Django Geçişi komutunu seçin, sonra projeye yeniden sağ  >   tıklayın, **Python**  >  **Django Create Superuser** komutunu seçin ve istemleri izleyin. (İlk olarak süper kullanıcı oluşturma denemesi yapmak için veritabanı başlatılmamış olduğundan bir hatayla karşı karşıyasınız.)

1. **DjangoPolls** projesini, Visual Studio **Çözüm Gezgini'de** bu projeye sağ tıklar ve Başlangıç olarak ayarla'Project.  Kalın yazıyla gösterilen başlangıç projesi, hata ayıklayıcıyı başlatan projedir.

1. Hata **AyıklamaYı** Başlat Hata Ayıklama ( F5 ) öğesini seçin veya sunucuyu çalıştırmak  >   için araç **çubuğundaki Web** Sunucusu düğmesini kullanın:

    ![Web sunucusu araç çubuğunu Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Şablon tarafından oluşturulan uygulamada, üst gezinti çubuğunu kullanarak gezinen Giriş, Hakkında ve Kişi olmak için üç sayfa vardır. Uygulamanın farklı bölümlerini incelemek için bir veya iki dakika zaman (About ve Contact sayfaları "Django Web Project" sayfalarına çok benzer ve daha fazla tartışılamaz).

    ![Polls Django Web uygulamasına tam Project görünümü](media/django/step06-full-app-view.png)

1. Ayrıca gezinti **çubuğunda yönetim** arabiriminin yalnızca kimliği doğrulanmış yöneticiler için yetkilendirilen bir oturum açma ekranı görüntüleyen Yönetim bağlantısını seçin. Süper kullanıcı kimlik bilgilerini kullanın; bu proje şablonu kullanılırken varsayılan olarak etkin olan "/admin" sayfasına yönlendirilebilirsiniz.

    ![Polls Django Web uygulaması yönetim Project görünümü](media/django/step06-polls-administrative-interface.png)

1. Aşağıdaki bölümler için uygulamayı çalışıyor bırakın.

    Uygulamayı durdurmak ve değişiklikleri kaynak denetimine işlemek için,  [](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)önce **Takım Gezgini'de** Değişiklikler sayfasını açın, sanal ortamın klasörüne sağ tıklayın (büyük olasılıkla **env)** ve Bu yerel öğeleri yoksay'ı **seçin.**

### <a name="examine-the-project-contents"></a>Proje içeriğini inceleme

Daha önce de not edildi. "Polls Django Web Project" şablonundan oluşturulan bir projede yer alan birçok şey, Visual Studio'daki diğer proje şablonlarını incelemeyi Visual Studio. Bu makaledeki ek adımlar, veri modelleri ve ek görünümler gibi daha önemli değişiklikleri ve eklemeleri özetler.

### <a name="question-what-does-the-django-migrate-command-do"></a>Soru: Django Geçişi komutu ne yapar?

Cevap: **Django Geçişi** komutu özellikle komutunu çalıştırır ve bu komut daha önce çalıştırılan `manage.py migrate` *app/migrations* klasöründeki betikleri çalıştırır. Bu durumda, komutu veritabanında gerekli *şemayı ayarlamak için 0001_initial.py* betiği bu klasörde çalıştırır.

Geçiş betiği, uygulamanın models.py dosyasını taratan, veritabanının geçerli durumuyla karşılaştıran ve ardından geçerli modellerle eş değer veritabanı şemasını geçirmek için gerekli betikleri oluşturan komutu tarafından `manage.py makemigrations` oluşturulur.  Django'nun bu özelliği, modellerinizi zaman içinde güncelleştiren ve değiştirerek çok güçlü bir özelliktir. Geçişler oluşturarak ve çalıştırarak modelleri ve veritabanını eşit durumda tutmanız çok zor olur.

Bu makalenin sonraki 6-3. adımlarında bir geçişle çalışacaktır.

## <a name="step-6-2-understand-data-models"></a>6-2. Adım: Veri modellerini anlama

Uygulamanın Poll ve Choice adlı modelleri *app/models.py içinde tanımlanır.* Her biri, ve gibi sınıfının yöntemlerinden türetilen ve modelde veritabanı sütunlarıyla eşilen alanları tanımlamak için yöntemlerini kullanan bir Python `django.db.models.Model` `models` `CharField` `IntegerField` sınıfıdır.

```python
from django.db import models
from django.db.models import Sum

class Poll(models.Model):
    """A poll object for use in the application views and repository."""
    text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')

    def total_votes(self):
        """Calculates the total number of votes for this poll."""
        return self.choice_set.aggregate(Sum('votes'))['votes__sum']

    def __unicode__(self):
        """Returns a string representation of a poll."""
        return self.text

class Choice(models.Model):
    """A poll choice object for use in the application views and repository."""
    poll = models.ForeignKey(Poll)
    text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)

    def votes_percentage(self):
        """Calculates the percentage of votes for this choice."""
        total = self.poll.total_votes()
        return self.votes / float(total) * 100 if total > 0 else 0

    def __unicode__(self):
        """Returns a string representation of a choice."""
        return self.text
```

Gördüğünüz gibi bir Yoklama, alanında bir açıklama ve `text` içinde bir yayın tarihi bulundurarak devam `pub_date` eder. Veritabanındaki Yoklama için yalnızca bu alanlar vardır; `total_votes` alanı çalışma zamanında hesaplanır.

Seçim, alanı üzerinden yapılan bir Yoklama ile ilgilidir, içinde bir açıklama içerir ve içinde `poll` `text` bu seçimin sayısını `votes` sürdürür. `votes_percentage`Alan çalışma zamanında hesaplanır ve veritabanında bulunamıyor.

Alan türlerinin tam listesi `CharField` (sınırlı metin) `TextField` (sınırsız metin), `EmailField` , , , , , , , ve `URLField` `DateTimeField` `IntegerField` `DecimalField` `BooleanField` `ForeignKey` 'tir. `ManyToMany` Her alan gibi bazı öznitelikler `max_length` alır. özniteliği, `blank=True` alanın isteğe bağlı olduğu anlamına gelir; `null=true` bir değerin isteğe bağlı olduğu anlamına gelir. Ayrıca bir veri `choices` değeri/görüntüleme değeri veri dizileri dizisinde değerleri değerlerle sınırlayan bir öznitelik de vardır. (Django [belgelerinde](https://docs.djangoproject.com/en/2.0/ref/models/fields/) Model alanı başvurusuna bakın.)

SQLite tarayıcısı gibi bir araç kullanarak projede *db.sqlite3* dosyasını inceleerek veritabanında depolananları tam [olarak doğrulayabilirsiniz.](https://sqlitebrowser.org/) Veritabanında, Seçim modelinde olduğu gibi bir yabancı anahtar `poll` alanı olarak depolanmış olduğunu `poll_id` görüyorsunuz; Django eşlemeyi otomatik olarak ele alır.

Genel olarak, Django'daki veritabanınız ile çalışmak, Django'nun temel alınan veritabanını sizin adına yönetene kadar yalnızca modelleriniz aracılığıyla çalışmak anlamına gelir.

### <a name="seed-the-database-from-samplesjson"></a>samples.json'dan veritabanının çekirdeğini oluşturma

Başlangıçta veritabanı hiçbir yoklama içeriyor. El ile yoklama eklemek için "/admin" URL'sinde yönetim arabirimini kullanabilir ve ayrıca çalışan sitenin "/seed" sayfasını ziyaret edebilirsiniz. Ayrıca, *uygulamanın samples.json* dosyasında tanımlanan yoklamalarla veritabanının çekirdeğini ekleyebilirsiniz.

Django projesinin projesinin *urls.py* URL deseni ( ) `url(r'^seed$', app.views.seed, name='seed'),` vardır. `seed` *app/views.py dosyasındaki* görünüm *samples.json* dosyasını yükler ve gerekli model nesnelerini oluşturur. Ardından Django, temel alınan veritabanında eşleşen kayıtları otomatik olarak oluşturur.

Görünüm için yetkilendirme `@login_required` düzeyini belirtmek üzere dekoratörün kullanımına dikkatin.

```python
@login_required
def seed(request):
    """Seeds the database with sample polls."""
    samples_path = path.join(path.dirname(__file__), 'samples.json')
    with open(samples_path, 'r') as samples_file:
        samples_polls = json.load(samples_file)

    for sample_poll in samples_polls:
        poll = Poll()
        poll.text = sample_poll['text']
        poll.pub_date = timezone.now()
        poll.save()

        for sample_choice in sample_poll['choices']:
            choice = Choice()
            choice.poll = poll
            choice.text = sample_choice
            choice.votes = 0
            choice.save()

    return HttpResponseRedirect(reverse('app:home'))
```

Etkiyi görmek için önce uygulamayı çalıştırarak henüz yoklama olmadığını seçin. Ardından "/seed" URL'sini ziyaret edin. Uygulama giriş sayfasına geri döndüğünde yoklamaların kullanılabilir olduğunu görebilirsiniz. Burada da raw *db.sqlite3* dosyasını SQLite tarayıcısı gibi bir [araçla inceleyebilirsiniz.](https://sqlitebrowser.org/)

![Django Web Project uygulamasını çekirdek veritabanıyla yoklar](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>Soru: Django yönetim yardımcı programını kullanarak veritabanını başlatmak mümkün mü?

Cevap: Evet, [django-admin loaddata](https://docs.djangoproject.com/en/2.0/ref/django-admin/#loaddata) komutunu kullanarak uygulamanın çekirdek sayfasıyla aynı görevi gerçekleştirebilirsiniz. Tam bir web uygulaması üzerinde çalışırken iki yöntemin birleşimini kullanabilirsiniz: komut satırdan bir veritabanı başlatma, ardından çekirdek sayfasını burada sabit kodlu bir dosyaya güvenmek yerine başka rastgele JSON gönderebilmek için kullanabileceğiniz bir API'ye dönüştürebilirsiniz.

## <a name="step-6-3-use-migrations"></a>6-3. Adım: Geçişleri kullanma

Projeyi oluşturduktan sonra komutu (Visual Studio menüsündeki bağlam menüsünü `manage.py makemigrations` kullanarak) *0001_initial.py* dosyası Django tarafından oluşturuldu. Bu dosya, ilk veritabanı tablolarını oluşturan bir betik içerir.

Modellerinizi zaman içinde kaçınılmaz olarak değişiklikler yaptığınız için Django, temel alınan veritabanı şemasını bu modellerle güncel tutmanızı kolaylaştırır. Genel iş akışı aşağıdaki gibidir:

1. Dosyanız içinde modellerde *models.py* yapın.
1. Bu Visual Studio içinde projeye sağ **tıklayın Çözüm Gezgini** **Python**  >  **Django Make Migrations komutunu** seçin. Daha önce açıklandığı gibi bu komut, veritabanını geçerli durumdan yeni durumuna geçirmek için *uygulama/geçişlerde* betikler oluşturur.
1. Betikleri gerçek veritabanına uygulamak için projeye yeniden sağ tıklayın ve **Python**  >  **Django Geçişi'ne tıklayın.**

Django, herhangi bir veritabanına hangi geçişlerin uygulandığını izler; örneğin, geçiş komutunu çalıştırarak Django gereken geçişleri uygular. Örneğin, yeni ve boş bir veritabanı oluşturursanız, geçiş komutunun çalıştırarak her geçiş betiği uygulanarak geçerli modelleriniz güncel olur. Benzer şekilde, bir geliştirme bilgisayarda birden çok model değişikliği yaptı ve geçişler oluşturursanız, üretim sunucunuzda geçiş komutunu çalıştırarak toplu geçişleri üretim veritabanınıza uygulayabilirsiniz. Django yeniden yalnızca üretim veritabanının son geçiş işleminin sonundan sonra oluşturulan geçiş betiklerini uygular.

Modeli değiştirmenin etkisini görmek için aşağıdaki adımları deneyin:

1. isteğe bağlı bir alan eklemek için alanından sonra aşağıdaki satırı ekleyerek *app/models.py'de* `pub_date` Yoklama modeline isteğe bağlı bir yazar alanı `author` ekleyin:

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. Dosyayı kaydedin, ardından **DjangoPolls** projesine sağ **tıklayın Çözüm Gezgini** **Python**  >  **Django Make Migrations komutunu** seçin.
1. Yeni **Project** adını adıyla başlayan  >   **migrations** klasöründe görmek için Tüm Dosyaları Göster komutunu 002_auto_. Bu dosyaya sağ tıklayın ve dosyada **Ekle'yi Project.** Özgün görünümü geri yüklemek **Project**  >  **Tüm Dosyaları Göster'i** yeniden seçebilirsiniz. (Bu adımla ilgili ayrıntılar için aşağıdaki ikinci soruya bakın.)
1. İsterseniz, Django betiklerinin önceki model durumuyla yeni durumuna nasıl değiştiklerini incelemek için bu dosyayı açın.
1. Visual Studio projesine yeniden sağ tıklayın ve **Python**  >  **Django Geçişi'ne** seçerek değişiklikleri veritabanına uygulayabilirsiniz.
1. İsterseniz, değişikliği onaylamak için veritabanını uygun bir görüntüleyicide açın.

Genel olarak, Django'nun geçiş özelliği veritabanı şemanızı hiçbir zaman el ile yönetmenize gerek yok anlamına gelir. Modelleriniz üzerinde değişiklik yapın, geçiş betikleri oluşturmanız ve bunları migrate komutuyla uygulamanız gerekir.

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>Soru: Modellerde değişiklik yaptıktan sonra geçiş komutunu çalıştırmayı unuturum ne olur?

Cevap: modeller veritabanındaki verilerle eşleşmezse, uygun özel durumlarla birlikte, çalışma zamanında Docgo başarısız olur. Örneğin, önceki bölümde gösterilen model değişikliğini geçirmeyi unutursanız, bu sütun için bir hata görürsünüz **: app_poll. Author**:

![Model değişikliği geçirildiğinde gösterilen hata](media/django/step06-exception-when-forgetting-to-migrate.png).

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>Soru: Docgo geçişi gerçekleştirildikten sonra yeni oluşturulan betikleri gösterme Çözüm Gezgini neden yapılamıyor?

cevap: yeni oluşturulan betikler *uygulama/geçiş* klasöründe bulunmasına rağmen **docgo geçişi** komutu çalıştırılırken uygulandığından, Visual Studio projesine eklenmemiş olduklarından **Çözüm Gezgini** otomatik olarak görünmez. bunları görünür yapmak için, önce   >  **tüm dosyaları göster** menü komutunu veya aşağıdaki görüntüde özetlenen araç çubuğu düğmesini Project seçin. Bu komut, projenin kendine eklenmemiş öğeler için noktalı bir ana hat simgesi kullanarak proje klasöründeki tüm dosyaları göstermesini **Çözüm Gezgini** neden olur. eklemek istediğiniz dosyalara sağ tıklayın ve **Project dahil et**' i seçin. bu, bir sonraki yürütmeyle birlikte kaynak denetiminde de yer alır.

![Çözüm Gezgini Project komutuna dahil et](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>Soru: geçirme komutunu çalıştırmadan önce hangi geçişlerin uygulanacağını görebilir miyim?

Cevap: Evet, [docgo-admin showgeçişleri komutunu](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations)kullanın.

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>Adım 6-4: proje şablonu tarafından oluşturulan görünümleri ve sayfa şablonlarını anlayın

"docgo web Project" şablonu tarafından oluşturulan görünümlerin çoğu, yaklaşık olarak bu öğreticide daha önce çalıştığınız "docgo web Project" şablonu tarafından oluşturulan görünümlere oldukça benzerdir. Yoklamalar uygulamasındaki farklı özellikler, giriş sayfasının, oylama ve yoklama sonuçlarını görüntülemek için birkaç eklenen sayfa gibi modelleri kullanmasına olanak sağlar.

İle başlamak için, urls.py dosyasındaki Docgo projesi dizisinin ilk satırı `urlpatterns` yalnızca bir uygulama  görünümüne basit bir yönlendirmeden daha fazla. Bunun yerine, uygulamanın kendi *URLs.py* dosyasını çeker:

```python
from django.conf.urls import url, include
import app.views

urlpatterns = [
    url(r'^', include('app.urls', namespace="app")),
    # ..
]
```

*App/URLs. Kopyala* dosyası daha sonra bazı ilgi çekici yönlendirme kodu içerir (açıklama eklenen açıklama):

```python
urlpatterns = [
    # Home page routing
    url(r'^$',
        app.views.PollListView.as_view(
            queryset=Poll.objects.order_by('-pub_date')[:5],
            context_object_name='latest_poll_list',
            template_name='app/index.html',),
        name='home'),

    # Routing for a poll page, which use URLs in the form <poll_id>/,
    # where the id number is captured as a group named "pk".
    url(r'^(?P<pk>\d+)/$',
        app.views.PollDetailView.as_view(
            template_name='app/details.html'),
        name='detail'),

    # Routing for <poll_id>/results pages, again using a capture group
    # named pk.
    url(r'^(?P<pk>\d+)/results/$',
        app.views.PollResultsView.as_view(
            template_name='app/results.html'),
        name='results'),

    # Routing for <poll_id>/vote pages, with the capture group named
    # poll_id this time, which becomes an argument passed to the view.
    url(r'^(?P<poll_id>\d+)/vote/$', app.views.vote, name='vote'),
]
```

Burada daha karmaşık normal ifadelerle ilgili bilgi sahibi değilseniz, bir açıklama için ifadeyi düz bir dilde [regex101.com](https://regex101.com/) içine yapıştırabilirsiniz. ( `/` Bir ters eğik çizgi ekleyerek eğik çizgilerin önüne geçmeniz gerekir `\` ; `r` dizenin ön eki, yani "RAW") nedeniyle Python 'da kaçış gerekmez.

Docgo 'da sözdizimi `?P<name>pattern` adlı bir grup oluşturur `name` ve bu, görünümler için bağımsız değişken olarak, göründüğü sırada geçirilir. Daha önce gösterilen kodda adlı bir bağımsız değişken alır ve adlı bir bağımsız `PollsDetailView` `PollsResultsView` `pk` `app.views.vote` değişken alır `poll_id` .

Ayrıca, görünümlerin çoğunun yalnızca *App/views. Kopyala* içindeki bir görünüm işlevine yönelik başvuruları doğrudan yönlendirmediğinden de bakabilirsiniz. Bunun yerine, en çok, veya ' den türetilen aynı dosyadaki bir sınıfa `django.views.generic.ListView` başvurur `django.views.generic.DetailView` . Temel sınıflar `as_view` , `template_name` şablonu tanımlamak için bir bağımsız değişken veren yöntemler sağlar. Ana `ListView` sayfa için kullanılan temel sınıf, `queryset` Bu durumda, verileri içeren bir özelliği ve `context_object_name` şablondaki verilere başvurmak istediğiniz değişken adına sahip bir özelliği de bekler `latest_poll_list` .

Artık `PollListView` *uygulama/görünümlerde* aşağıdaki gibi tanımlanan giriş sayfası için ' i inceleyebilirsiniz:

```python
class PollListView(ListView):
    """Renders the home page, with a list of all polls."""
    model = Poll

    def get_context_data(self, **kwargs):
        context = super(PollListView, self).get_context_data(**kwargs)
        context['title'] = 'Polls'
        context['year'] = datetime.now().year
        return context
```

Burada yapılan tüm bunlar, görünümün (yoklama) birlikte çalışması için olan modeli tanımlamak ve `get_context_data` `title` `year` bağlama ve bağlam değerlerini geçersiz kılar.

Şablonun çekirdeği (*Şablonlar/uygulama/index.html*) aşağıdaki gibidir:

```html
{% if latest_poll_list %}
<table class="table table-hover">
    <tbody>
        {% for poll in latest_poll_list %}
        <tr>
            <td>
                <a href="{% url 'app:detail' poll.id %}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<!-- ... other content omitted ... -->
{% endif %}
```

Basitçe, şablon ' daki yoklama nesnelerinin listesini alır `latest_poll_list` ve sonra yoklamaya ilişkin değeri kullanarak her bir yoklamaya bağlantı içeren bir tablo satırı oluşturmak için bu listede yinelenir `text` . `{% url %}`"App: Detail" etiketinde "Detail" adlı bir bağımsız değişken olarak kullanılan *App/URLs* içindeki URL deseninin olması gerekir `poll.id` . Bunun etkisi, Docgo 'nun uygun kalıbı kullanarak bir URL oluşturması ve bu bağlantıyı kullanması için kullanılır. Daha sonra bu bit-yazım denetimi, bu URL deseninin istediğiniz zaman ve oluşturulan bağlantıların eşleşmek üzere otomatik olarak güncelleştirilmesini sağlayan anlamına gelir.

`PollDetailView` `PollResultsView` *App/views. Kopyala* içindeki ve sınıfları (burada gösterilmez), `PollListView` bunun yerine türettikleri hariç neredeyse özdeş olarak görünür `DetailView` . İlgili şablonlar, *uygulama/şablonlar/details.html* ve *uygulama/şablonlar/results.html* , daha sonra uygun ALANLARı modellerden çeşitli HTML denetimleri içinde yerleştirir. *details.html* benzersiz bir parça, bir yoklama seçeneklerinin, gönderildiğinde/oy URL 'sine gönderi GÖNDERDIĞI bir HTML biçiminde içermalarıdır. Daha önce görüldüğü gibi, bu URL deseninin öğesine yönlendirilmesi gerekir `app.views.vote` ve bu, aşağıdaki şekilde uygulanır ( `poll_id` Bu görünümün yönlendirmesinde kullanılan normal ifadede bir adlandırılmış grup olan bağımsız değişkeni unutmayın):

```python
def vote(request, poll_id):
    """Handles voting. Validates input and updates the repository."""
    poll = get_object_or_404(Poll, pk=poll_id)
    try:
        selected_choice = poll.choice_set.get(pk=request.POST['choice'])
    except (KeyError, Choice.DoesNotExist):
        return render(request, 'app/details.html', {
            'title': 'Poll',
            'year': datetime.now().year,
            'poll': poll,
            'error_message': "Please make a selection.",
    })
    else:
        selected_choice.votes += 1
        selected_choice.save()
        return HttpResponseRedirect(reverse('app:results', args=(poll.id,)))
```

Burada, görünümün kendisine karşılık gelen şablonu diğer sayfalar gibi değildir. Bunun yerine, yoklama yoksa, seçilen 404 yoklamayı doğrular (birisi "oy/1a2b3c" gibi bir URL 'ye girdiğinde). Daha sonra, oylanan seçeneğin yoklama için geçerli olduğundan emin olur. Aksi takdirde, `except` blok Ayrıntılar sayfasını bir hata iletisiyle yeniden işler. Seçim geçerliyse görünüm, oy alır ve sonuçlar sayfasına yeniden yönlendirir.

## <a name="step-6-5-create-a-custom-administration-interface"></a>Adım 6-5: özel bir yönetim arabirimi oluşturma

"docgo Web Project yokladığı son parçalar" şablonu, bu makalenin 6-1. adımında aşağıda gösterildiği gibi varsayılan docgo yönetim arabirimine yönelik özel uzantılardır. Varsayılan arabirim, Kullanıcı ve Grup yönetimi için sağlar, ancak hiçbir şey değildir. Yoklamalar proje şablonu, yoklamaları da yönetmenizi sağlayan özellikler ekler.

İlki, Docgo projesi *URLs.py* içindeki URL desenleri `url(r'^admin/', include(admin.site.urls)),` Varsayılan olarak eklenmiştir; "Yönetici/belge" deseni de dahil edilir ancak açıklama eklenir.

Daha sonra uygulama,  `django.contrib.admin` `INSTALLED_APPS` *Settings.py* dizisine dahil olmak üzere yönetim arabirimini ziyaret ettiğinizde docgo 'nun otomatik olarak çalıştığı admin.py dosyasını içerir. Proje şablonu tarafından sağlandığı gibi bu dosyadaki kod aşağıdaki gibidir:

```python
from django.contrib import admin
from app.models import Choice, Poll

class ChoiceInline(admin.TabularInline):
    """Choice objects can be edited inline in the Poll editor."""
    model = Choice
    extra = 3

class PollAdmin(admin.ModelAdmin):
    """Definition of the Poll editor."""
    fieldsets = [
        (None, {'fields': ['text']}),
        ('Date information', {'fields': ['pub_date']}),
    ]
    inlines = [ChoiceInline]
    list_display = ('text', 'pub_date')
    list_filter = ['pub_date']
    search_fields = ['text']
    date_hierarchy = 'pub_date'

admin.site.register(Poll, PollAdmin)
```

Görebileceğiniz gibi, `PollAdmin` sınıfı `django.contrib.admin.ModelAdmin` modelden türetilir ve tarafından yönetilen adları kullanarak bir dizi alanın adlarını `Poll` kullanır. Bu alanlar, Docgo belgelerindeki [Modeladmin seçeneklerinde](https://docs.djangoproject.com/en/2.0/ref/contrib/admin/#modeladmin-options) açıklanmıştır.

`admin.site.register`Sonra bu sınıfı modele ( `Poll` ) bağlar ve bunu yönetici arabirimine ekler. Genel sonuç aşağıda gösterilmektedir:

![docgo Web Project uygulamasını yoklayan yönetim görünümü](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>Sonraki adımlar

> [!Note]
> bu öğreticinin tamamında Visual Studio çözümünüzü kaynak denetimine uyguladıysanız, başka bir işleme yapmak iyi bir zaman vardır. çözümünüz GitHub: [Microsoft/python-sample-vs-learning-docgo](https://github.com/Microsoft/python-sample-vs-learning-django)üzerindeki öğretici kaynak kodu ile eşleşmelidir.

artık "boş docgo web Project", "docgo web Project" ve "docgo web Project" şablonlarını Visual Studio ' de incelediniz. Görünümler ve Şablonlar kullanma gibi Docgo 'un tüm temel bilgilerini öğrendiniz ve veritabanı modellerini kullanarak, bir yönlendirme, kimlik doğrulama ve değişiklik yapabilirsiniz. Artık ihtiyacınız olan herhangi bir görünüm ve modelle kendinizinkini bir Web uygulaması oluşturabilmeniz gerekir.

Geliştirme bilgisayarınızda bir Web uygulaması çalıştırmak, uygulamayı müşterileriniz için kullanılabilir hale getirmek için yalnızca bir adımdır. Sonraki adımlarda aşağıdaki görevler bulunabilir:

- Web uygulamasını Azure App Service gibi bir üretim sunucusuna dağıtın. Bkz. [Azure App Service yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md).

- *Şablonlar/404.html* adlı bir şablon oluşturarak 404 sayfasını özelleştirin. Mevcut olduğunda, Docgo, varsayılan değer yerine bu şablonu kullanır. Daha fazla bilgi için, bkz. Docgo belgelerindeki [hata görünümleri](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) .

- Birim testlerini *Tests.py*'de yazın; Visual Studio proje şablonları bunlar için başlangıç noktaları sağlar ve dmongo belgelerinde dmongo 'da [ilk dmongo uygulamanızı, 5. bölüm-test](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) ve [test](https://docs.djangoproject.com/en/2.0/topics/testing/) ' i yazarken daha fazla bilgi bulabilirsiniz.

- uygulamayı SQLite ' dan postgresql, MySQL ve SQL Server (tümü Azure üzerinde barındırılabilen) gibi bir üretim düzeyi veri deposu olarak değiştirin. SQLite (sqlite.org) [ne zaman kullanılacağı](https://www.sqlite.org/whentouse.html) konusunda açıklandığı gibi, SQLite, 100 ' den az KB/gün içinde düşük ve orta ölçekli trafik siteleri için uygundur, ancak daha yüksek birimler için önerilmez. Aynı zamanda tek bir bilgisayarla sınırlandırılmıştır, bu nedenle yük dengeleme ve coğrafi çoğaltma gibi çok sunuculu bir senaryoda kullanılamaz. Docgo 'nun diğer veritabanları için desteği hakkında bilgi için bkz. [veritabanı kurulumu](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup). Ayrıca, [Python Için Azure SDK 'sını](/azure/python/) tablolar ve Bloblar gibi Azure depolama hizmetleriyle birlikte çalışmak için de kullanabilirsiniz.

- Azure DevOps gibi bir hizmette sürekli tümleştirme/sürekli dağıtım işlem hattı ayarlayın. kaynak denetimi ile çalışmaya ek olarak (Azure Repos veya GitHub ya da başka bir yerde), birim testlerinizi bir ön koşul olarak otomatik olarak çalıştırmak için bir Azure DevOps Project yapılandırabilir ve ayrıca işlem hattını üretime dağıtmadan önce ek testler için bir hazırlama sunucusuna dağıtılacak şekilde yapılandırabilirsiniz. Azure DevOps, ayrıca, uygulama Analizler gibi izleme çözümleriyle tümleştirilir ve çevik planlama araçlarıyla tüm döngüyü kapatır. daha fazla bilgi için bkz. [Python için bir cı/CD işlem hattı oluşturma Azure DevOps projesi](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true) ve ayrıca genel [Azure DevOps belgeleri](/azure/devops/?view=vsts&preserve-view=true).
