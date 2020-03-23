---
title: Visual Studio adım 6, Anketler proje şablonu Django öğretici öğrenin
titleSuffix: ''
description: Visual Studio projeleri bağlamında Django temellerinin bir walkthrough, özellikle anketler Django Web Project şablonu gibi idari özelleştirme özellikleri.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c1fe3db702508267e96dc79f2f789a17a7edf98b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75755582"
---
# <a name="step-6-use-the-polls-django-web-project-template"></a>Adım 6: Anketler Django Web Projesi şablonu kullanın

**Önceki adım: [Django'daki kullanıcıları doğrulama](learn-django-in-visual-studio-step-05-django-authentication.md)**

Visual Studio'nun "Django Web Project" şablonundan anlayınca, artık aynı kod tabanını temel alan ve bir veritabanıyla çalışmayı gösteren üçüncü Django şablonu olan "Polls Django Web Project"e bakabilirsiniz.

Bu adımda nasıl öğrenirsiniz:

> [!div class="checklist"]
> - Şablondan bir proje oluşturun ve veritabanını başlatma (adım 6-1)
> - Veri modellerini anlama (adım 6-2)
> - Geçişleri uygulayın (adım 6-3)
> - Proje şablonu tarafından oluşturulan görünümleri ve sayfa şablonlarını anlama (adım 6-4)
> - Özel bir yönetim arabirimi oluşturma (adım 6-5)

Bu şablon kullanılarak oluşturulan bir proje, Django dokümanlarında [ilk Django uygulama öğreticinizi yazarak](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) elde ettiğinize benzer. Web uygulaması, insanların anketleri görüntülemesine ve oy kullanmalarına olanak tanıyan herkese açık bir sitenin yanı sıra anketleri yönetebileceğiniz özel bir yönetim arabiriminden oluşur. "Django Web Project" şablonuyla aynı kimlik doğrulama sistemini kullanır ve aşağıdaki bölümlerde araştırıldığı gibi Django modellerini uygulayarak veritabanından daha fazla yararlanır.

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>Adım 6-1: Projeyi oluşturun ve veritabanını başlatma

1. Visual Studio'da **Solution Explorer'a**gidin, bu eğitimde daha önce oluşturulan **LearningDjango** çözümüne sağ tıklayın ve**Yeni Proje** **Ekle'yi** > seçin. (Alternatif olarak, yeni bir çözüm kullanmak istiyorsanız, bunun yerine **Dosya** > **Yeni** > **Projesi'ni** seçin.)

1. Yeni proje iletişim kutusunda, **Anketler Django Web Project** şablonunu arayın ve seçin, projeyi "DjangoPolls" olarak adlandırın ve **Tamam'ı**seçin.

1. Visual Studio'daki diğer proje şablonları gibi, "Polls Django Web Project" şablonu bir *requirements.txt* dosyası içerir, Visual Studio bu bağımlılıkları nereye yükleyebileceğinizi sorar. Seçeneği seçin, **sanal ortama yükle**ve Sanal Ortam **Ekle** iletişim kutusunda varsayılanları kabul etmek için **Oluştur'u** seçin.

1. Python sanal ortamı ayarlamayı bitirdikten sonra, veritabanını başlatmave bir Django süper kullanıcısı (yani bir yönetici) oluşturmak için görüntülenen *readme.html'deki* yönergeleri izleyin. Adımlar ilk sağ **Çözüm Gezgini** **DjangoPolls** proje tıklayın, **Python** > **Django Geçir** komutunu seçin, sonra sağ proje yi yeniden tıklatın, **Python** > **Django Create Superuser** komutunu seçin ve istemleri izleyin. (Önce süper bir kullanıcı oluşturmaya çalışırsanız, veritabanı baş harfe başlatılmadığından bir hata görürsünüz.)

1. **DjangoPolls** **projesini, Solution Explorer'daki** projeyi sağ tıklatarak ve **Başlangıç Projesi olarak Set'i**seçerek Visual Studio çözümü için varsayılan olarak ayarlayın. Kalın olarak gösterilen başlangıç projesi, hata ayıklamayı başlattığınızda çalıştırılan şeydir.

1. **Hata Ayıklama** > **Hata Ayıklama** **(F5)** seçeneğini belirleyin veya sunucuyu çalıştırmak için araç çubuğundaki **Web Sunucusu** düğmesini kullanın:

    ![Visual Studio'da web sunucusu araç çubuğu düğmesini çalıştırın](media/django/run-web-server-toolbar-button.png)

1. Şablon tarafından oluşturulan uygulama, üst gezinme çubuğunu kullanarak arasında gezindiğiniz Ana Sayfa, Hakkında ve İletişim olmak üzere üç sayfadan oluşur. Uygulamanın farklı bölümlerini incelemek için bir veya iki dakika ayırın (Hakkında ve İletişim sayfaları "Django Web Projesi"ne çok benzer ve daha fazla tartışılmamamaktadır).

    ![Polls Django Web Project uygulamasının tam tarayıcı görünümü](media/django/step06-full-app-view.png)

1. Ayrıca, yönetim arabiriminin yalnızca kimlik doğrulaması yapılan yöneticilere yetki verdiğini göstermek için oturum açma ekranı görüntüleyen gezinme çubuğundaki **Yönetim** bağlantısını da seçin. Süper kullanıcı kimlik bilgilerini kullanın ve bu proje şablonu kullanılırken varsayılan olarak etkinleştirilen "/admin" sayfasına yönlendirilirsiniz.

    ![Anketler Django Web Projesi uygulamasının idari görünümü](media/django/step06-polls-administrative-interface.png)

1. Takip eden bölümler için uygulamayı çalışır durumda bırakabilirsiniz.

    Uygulamayı durdurmak ve kaynak [denetiminde değişiklikler yapmak](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)istiyorsanız, önce **Team Explorer'da** **Değişiklikler** sayfasını açın , sanal ortam için klasörü sağ tıklatın (muhtemelen **env),** ve **bu yerel öğeleri yoksay'ı**seçin.

### <a name="examine-the-project-contents"></a>Proje içeriğini inceleme

Daha önce de belirtildiği gibi. Visual Studio'daki diğer proje şablonlarını keşfettiyseniz, "Polls Django Web Project" şablonundan oluşturulan bir projede bulunanların çoğu tanıdık olmalıdır. Bu makaledeki ek adımlar, daha önemli değişiklikleri ve eklemeleri, yani veri modellerini ve ek görünümleri özetler.

### <a name="question-what-does-the-django-migrate-command-do"></a>Soru: Django Migrate komutu ne işe yarar?

Yanıt: **Django Geçir** komutu, `manage.py migrate` *uygulama/geçişler* klasöründe daha önce çalıştırılmamış tüm komutları çalıştıran komutu özel olarak çalıştırıyor. Bu durumda, komut veritabanında gerekli şemaları ayarlamak için bu klasörde *0001_initial.py* komut çalışır.

Geçiş komutunun kendisi, `manage.py makemigrations` uygulamanın *models.py* dosyasını tarayan, veritabanının geçerli durumuyla karşılaştıran ve ardından geçerli modellere uyacak şekilde veritabanı şemasını geçirmek için gerekli komut dosyalarını oluşturan komut tarafından oluşturulur. Zaman içinde modellerinizi güncelleyip değiştirince Django'nun bu özelliği çok güçlüdür. Geçişler oluşturarak ve çalıştırarak, modelleri ve veritabanını çok az zorlukla eşit tutarsınız.

Bu makalede daha sonra adım 6-3 bir geçiş ile çalışır.

## <a name="step-6-2-understand-data-models"></a>Adım 6-2: Veri modellerini anlama

Anket ve Seçim adlı uygulamanın modelleri *app/models.py'de*tanımlanır. Her `django.db.models.Model` biri, `models` veritabanı sütunlarını eşleyen modeldeki alanları `CharField` `IntegerField` tanımlamak ve beğenme ve sınıfın yöntemlerini kullanan bir Python sınıfıdır.

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

Gördüğünüz gibi, Bir Anket kendi `text` alanında bir açıklama ve `pub_date`yayın tarihi tutar. Bu alanlar, veritabanında Anket için var olan tek alanlardır; `total_votes` alan çalışma zamanında hesaplanır.

Bir `poll` Seçim, alan üzerinden bir Anket ile `text`ilgilidir, bir açıklama içerir , `votes`ve bu seçim için bir sayı korur . Alan `votes_percentage` çalışma zamanında hesaplanır ve veritabanında bulunmaz.

Alan türlerinin tam `CharField` listesi (sınırlı `TextField` metin) `EmailField`(sınırsız metin), `BooleanField` `ForeignKey`, `ManyToMany` `URLField`, `DateTimeField` `IntegerField` `DecimalField`, , , , ve . Her alan gibi `max_length`bazı öznitelikleri alır. Öznitelik, `blank=True` alanın isteğe bağlı olduğu anlamına gelir; `null=true` bir değerin isteğe bağlı olduğu anlamına gelir. Ayrıca, bir `choices` veri değeri/görüntü değeri tuples dizisindedeğerleri değerlerle sınırlayan bir öznitelik de vardır. (Django belgelerindeki [Model alan başvurusuna](https://docs.djangoproject.com/en/2.0/ref/models/fields/) bakın.)

[SQLite tarayıcısı](https://sqlitebrowser.org/)gibi bir aracı kullanarak projedeki *db.sqlite3* dosyasını inceleyerek veritabanında nelerin depoladığını tam olarak doğrulayabilirsiniz. Veritabanında, Choice modelindeki `poll` `poll_id`gibi yabancı bir anahtar alanının ; Django haritalamayı otomatik olarak işler.

Genel olarak, Django'da veritabanınızla çalışmak, Django'nun temel veritabanını sizin adınıza yönetebilmeleri için yalnızca modelleriniz aracılığıyla çalışmak anlamına gelir.

### <a name="seed-the-database-from-samplesjson"></a>Örnek.json veritabanı tohum

Başlangıçta, veritabanı hiçbir anket içerir. Anketleri el ile eklemek için "/admin" URL'sindeki yönetim arabirimini kullanabilir ve uygulamanın *samples.json* dosyasında tanımlanan anketlerle veritabanına tohum eklemek için çalışan sitedeki "/seed" sayfasını da ziyaret edebilirsiniz.

Django projesinin *urls.py* ek bir URL `url(r'^seed$', app.views.seed, name='seed'),`deseni vardır. `seed` *app/views.py'deki* görünüm *örnekleri.json* dosyasını yükler ve gerekli model nesnelerini oluşturur. Django daha sonra temel veritabanındaki eşleşen kayıtları otomatik olarak oluşturur.

Görünüm için yetkilendirme `@login_required` düzeyini belirtmek için dekoratörün kullanımına dikkat edin.

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

Efekti görmek için, henüz anket bulunmadığını görmek için uygulamayı ilk olarak çalıştırın. Ardından "/seed" URL'sini ziyaret edin ve uygulama ana sayfaya döndüğünde anketlerin kullanıma sunulduğunu görmeniz gerekir. Yine, [SQLite tarayıcı](https://sqlitebrowser.org/)gibi bir araç ile ham *db.sqlite3* dosyasını incelemek için çekinmeyin.

![Tohumlu veritabanı ile Anketler Django Web Projesi uygulaması](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>Soru: Django idari yardımcı programını kullanarak veritabanını başlatmamümkün mü?

Cevap: Evet, uygulamadaki tohumlama sayfasıyla aynı görevi yerine getirmek için [django-admin loaddata komutunu](https://docs.djangoproject.com/en/2.0/ref/django-admin/#loaddata) kullanabilirsiniz. Tam bir web uygulaması üzerinde çalışırken, iki yöntemin bir birleşimini kullanabilirsiniz: komut satırından bir veritabanını başlatma, ardından tohum sayfasını sabit kodlu bir dosyaya güvenmek yerine başka bir rasgele JSON gönderebileceğiniz bir API'ye dönüştürün.

## <a name="step-6-3-use-migrations"></a>Adım 6-3: Geçişleri kullanma

Projeyi `manage.py makemigrations` oluşturduktan sonra komutu (Visual Studio'daki bağlam menüsünü kullanarak) çalıştırdığınızda, Django dosya *uygulaması/migrations/0001_initial.py* dosyasını oluşturdu. Bu dosya, ilk veritabanı tabloları oluşturan bir komut dosyası içerir.

Zaman içinde modellerinizde kaçınılmaz değişiklikler yapacağınız için, Django bu modellerde temel veritabanı şemasını güncel tutmayı kolaylaştırır. Genel iş akışı aşağıdaki gibidir:

1. *models.py* dosyanızdaki modellerde değişiklik yapın.
1. Visual Studio'da **Solution Explorer'daki** projeye sağ tıklayın ve **Python** > **Django Make Migrations** komutunu seçin. Daha önce açıklandığı gibi, bu komut, veritabanını geçerli durumundan yeni duruma geçirmek için *uygulama/geçişlerde* komut dosyaları oluşturur.
1. Komut dosyalarını gerçek veritabanına uygulamak için projeyi yeniden tıklatın ve **Python** > **Django Geçir'i**seçin.

Django, geçiş komutunu çalıştırdığınızda hangi geçişler gerekiyorsa uygular gibi, herhangi bir veritabanına hangi geçişlerin uygulandığını izler. Örneğin, yeni, boş bir veritabanı oluşturursanız, geçiş komutunu çalıştırmak, her geçiş komutunu uygulayarak bu veritabanını geçerli modellerinizden güncel hale getirir. Benzer şekilde, birden çok model değişikliği yapar ve geliştirme bilgisayarında geçişler oluşturursanız, üretim sunucunuzda geçir komutunu çalıştırarak toplu geçişleri üretim veritabanınıza uygulayabilirsiniz. Django yine üretim veritabanının son geçişinden bu yana oluşturulan bu geçiş komut dosyaları geçerlidir.

Bir modeli değiştirmenin etkisini görmek için aşağıdaki adımları deneyin:

1. *Uygulama/models.py'deki* Yoklama modeline isteğe bağlı bir yazar `pub_date` alanı ekleyin `author` ve alandan sonra isteğe bağlı alan ekleyin:

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. Dosyayı kaydedin, ardından **Solution Explorer'daki** **DjangoPolls** projesini sağ tıklatın ve **Python** > **Django Geçişyap** komutunu seçin.
1. Adı **002_auto_** ile başlayan **geçişler** klasöründe yeni oluşturulan komut dosyasını görmek için **Tüm** > **Dosyaları Göster** komutunu seçin. Bu dosyaya sağ tıklayın ve **Projeye Ekle'yi**seçin. Daha sonra özgün görünümü geri yüklemek için **Project** > **Tüm Dosyaları Göster'i** yeniden seçebilirsiniz. (Bu adımla ilgili ayrıntılar için aşağıdaki ikinci soruya bakın.)
1. İstenirse, Django'nun önceki model durumundan yeni duruma geçişi nasıl komut dosyası olarak yazdığını incelemek için bu dosyayı açın.
1. Visual Studio projesini yeniden sağ tıklatın ve değişiklikleri veritabanına uygulamak için **Python** > **Django Migrate'i** seçin.
1. İstenirse, değişikliği onaylamak için veritabanını uygun bir görüntüleyicide açın.

Genel olarak, Django'nun geçiş özelliği, veritabanı şemanızı asla el ile yönetmeniz gerektiği anlamına gelir. Modellerinizde değişiklik yapın, geçiş komutdosyalarını oluşturun ve bunları geçiş komutuyla uygulayın.

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>Soru: Modellerde değişiklik yaptıktan sonra geçiş komutunu çalıştırmayı unutursam ne olur?

Cevap: Modeller veritabanındakilerle eşleşmiyorsa, Django çalışma zamanında uygun istisnalar dışında başarısız olur. Örneğin, önceki bölümde gösterilen model değişikliğini değiştirmeyi unutursanız, böyle bir sütunda bir hata **görürsünüz: app_poll.author:**

![Model değişikliği geçirildiğinde gösterilen hata](media/django/step06-exception-when-forgetting-to-migrate.png).

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>Soru: Solution Explorer, Django Make Migration'ı çalıştırdıktan sonra neden yeni oluşturulan komut dosyalarını göstermiyor?

Yanıt: Yeni oluşturulan komut dosyaları *uygulama/geçişler* klasöründe bulunmasına ve **Django Geçir** komutunu çalıştırırken uygulanmasına rağmen, Visual Studio projesine eklenmedikleri için **Solution Explorer'da** otomatik olarak görünmezler. Bunları görünür hale getirmek için önce **Project** > **Show All Files** menüsü komutunu veya aşağıdaki resimde özetlenen araç çubuğu düğmesini seçin. Bu komut, projenin kendisine eklenmemiş öğeler için noktalı bir anahat simgesi kullanarak **Çözüm Gezgini'nin** proje klasöründeki tüm dosyaları göstermesine neden olur. Eklemek istediğiniz dosyaları sağ tıklatın ve bir sonraki işleme ile kaynak denetiminde de içeren **Project'e Ekle'yi**seçin.

![Solution Explorer'da Project komutuna ekleme](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>Soru: Geçiş komutunu çalıştırmadan önce hangi geçişlerin uygulanacağını görebilir miyim?

Cevap: Evet, [django-admin showmigrations komutunu](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations)kullanın.

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>Adım 6-4: Proje şablonu tarafından oluşturulan görünümleri ve sayfa şablonlarını anlama

"Polls Django Web Project" şablonu tarafından oluşturulan görünümlerin çoğu (About and Contact sayfaları gibi), bu öğreticide daha önce birlikte çalıştığınız "Django Web Project" şablonu tarafından oluşturulan görünümlere oldukça benzer. Anketler uygulamasında farklı olan şey, ana sayfasının, oy kullanmak ve anket sonuçlarını görüntülemek için eklenen birkaç sayfa gibi modelleri kullanmasıdır.

İlk olarak, Django projesinin `urlpatterns` *urls.py* dosyasındaki dizisindeki ilk satır, uygulama görünümüne basit bir yönlendirmeden daha fazlasıdır. Bunun yerine, uygulamanın kendi *urls.py* dosyasını çeker:

```python
from django.conf.urls import url, include
import app.views

urlpatterns = [
    url(r'^', include('app.urls', namespace="app")),
    # ..
]
```

*App/urls.py* dosyası daha sonra biraz daha ilginç yönlendirme kodu içerir (açıklayıcı yorumlar eklendi):

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

Burada kullanılan daha karmaşık normal ifadelere aşina değilseniz, ifadeyi düz dilde bir açıklama için [regex101.com](https://regex101.com/) yapıştırabilirsiniz. (Önlerinden `/` `\` önce bir arka çizgi ekleyerek ileri eğik çizgilerden kaçmanız gerekir; python'da `r` "ham" anlamına gelen dize deki önek nedeniyle kaçmak gerekli değildir).

Django'da sözdizimi, `?P<name>pattern` göründükleri `name`sırada görünümlere bağımsız değişken olarak geçirilen , adlı bir grup oluşturur. Kodda daha önce `PollsDetailView` `PollsResultsView` gösterilen ve `pk` adlı `app.views.vote` bir argüman `poll_id`almak ve adlı bir argüman alır.

Ayrıca, görünümlerin çoğunun sadece *uygulama/görünümler.py'deki*bir görünüm işlevine doğrudan göndermeler olmadığını da görebilirsiniz. Bunun yerine, çoğu aynı dosyadaki bir sınıfa `django.views.generic.ListView` `django.views.generic.DetailView`başvurur veya . Temel sınıflar, `as_view` şablonu tanımlamak `template_name` için bir bağımsız değişken alan yöntemleri sağlar. `ListView` Ana sayfa için kullanılan taban sınıf, bu `queryset` durumda, `latest_poll_list`şablondaki verilere başvurmak istediğiniz değişken adı olan verileri ve özelliği içeren bir `context_object_name` özellik de bekler.

Şimdi `PollListView` *app/views.py'de*aşağıdaki gibi tanımlanan ana sayfaiçin inceleyebilirsiniz:

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

Burada yapılan tek şey, görünümün birlikte çalıştığı modeli (Anket) tanımlamak `get_context_data` ve `title` içeriğe eklemek ve `year` değerler eklemek için yöntemi geçersiz kılar.

Şablonun *(templates/app/index.html)* özü aşağıdaki gibidir:

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

Basitçe söylemek gerekirse, şablon Anket nesnelerinin `latest_poll_list`listesini alır ve daha sonra anketin `text` değerini kullanarak her ankete bağlantı içeren bir tablo satırı oluşturmak için bu liste yi yineler. Etikette, `{% url %}` "app:detail", "detay" adlı *app/urls.py'deki* url `poll.id` desenini ifade eder ve bağımsız değişken olarak kullanır. Bunun etkisi, Django'nun uygun deseni kullanarak bir URL oluşturması ve bunu bağlantı için kullanmasıdır. Bu gelecek geçirmezlik biti, bu URL deseni istediğiniz zaman değiştirebileceğiniz ve oluşturulan bağlantıların otomatik olarak eşleşecek şekilde güncelleştirilebildiği anlamına gelir.

`PollDetailView` `PollResultsView` *App/views.py'deki* ve sınıflar (burada gösterilmez) `PollListView` `DetailView` bunun yerine türedikleri dışında hemen hemen aynı görünür. Kendi şablonları, *app/templates/details.html* ve *app/templates/results.html* sonra çeşitli HTML denetimleri içinde modellerden uygun alanları yerleştirin. *details.html'deki* benzersiz bir parça, anket seçeneklerinin gönderildiğinde /vote URL'sine bir GÖNDERI yapan bir HTML formu içinde yer alan bir anket olmasıdır. Daha önce de görüldüğü gibi, `app.views.vote`bu URL deseni aşağıdaki gibi `poll_id` uygulanan ,'a yönlendirilir (bu görünüm için yönlendirmede kullanılan normal ifadede yine adlandırılmış bir grup olan bağımsız değişkene dikkat edin):

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

Burada, görünümün diğer sayfalar gibi karşılık gelen şablonu yoktur. Bunun yerine, anket yoksa (birinin "vote/1a2b3c" gibi bir URL'ye girmesi durumunda) 404'ü göstererek seçilen anketi doğrular. Daha sonra oy seçimi anket için geçerli olduğundan emin olun. Değilse, `except` blok sadece bir hata iletisi ile ayrıntıları sayfasını yeniden işler. Seçim geçerliyse, görünüm oylamayı tamamlar ve sonuçlar sayfasına yönlendirir.

## <a name="step-6-5-create-a-custom-administration-interface"></a>Adım 6-5: Özel bir yönetim arabirimi oluşturma

"Polls Django Web Project" şablonunun son parçaları, bu makalede daha önce 6-1 adım altında gösterildiği gibi varsayılan Django yönetim arabirimine özel uzantılarıdır. Varsayılan arabirim, kullanıcı ve grup yönetimi sağlar, ancak başka bir şey değil. Anketler proje şablonu, anketleri de yönetmenize olanak tanıyan özellikler ekler.

Her şeyden önce, Django projesinin *urls.py* URL `url(r'^admin/', include(admin.site.urls)),` desenleri varsayılan olarak dahil edilmiştir; "admin/doc" deseni de dahildir ancak yorumlanır.

Uygulama daha sonra *admin.py*dosyaiçerir , `django.contrib.admin` `INSTALLED_APPS` *settings.py*dizi dahil edilmesi sayesinde idari arayüzü ziyaret ettiğinizde Django otomatik olarak çalışır . Proje şablonu tarafından sağlanan bu dosyadaki kod aşağıdaki gibidir:

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

Gördüğünüz gibi, `PollAdmin` sınıf, yönettiği `django.contrib.admin.ModelAdmin` `Poll` modeldeki adları kullanarak bir dizi alanından türetilmiştir ve özelleştirmektedir. Bu alanlar Django belgelerinde [ModelAdmin seçenekleri](https://docs.djangoproject.com/en/2.0/ref/contrib/admin/#modeladmin-options) açıklanmıştır.

Çağrı `admin.site.register` daha sonra bu sınıfı modele`Poll`bağlar ( ) ve yönetici arabiriminde içerir. Genel sonuç aşağıda gösterilmiştir:

![Anketler Django Web Projesi uygulamasının idari görünümü](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>Sonraki adımlar

> [!Note]
> Bu öğretici boyunca kaynak kontrolü için Visual Studio çözüm taahhüt oldum, şimdi başka bir taahhüt yapmak için iyi bir zaman. Çözümünüz GitHub'daki öğretici kaynak koduyla eşleşmelidir: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

Visual Studio'da "Boş Django Web Projesi", "Django Web Projesi" ve "Polls Django Web Project" şablonlarının tamamını araştırdınız. Django'nun görünümleri ve şablonları kullanma gibi tüm temel lerini öğrendiniz ve yönlendirmeyi, kimlik doğrulamasını ve veritabanı modellerini kullanmayı keşfettiniz. Artık ihtiyacınız olan herhangi bir görünüm ve modelile kendi web uygulamanızı oluşturabilmeniz gerekir.

Geliştirme bilgisayarınızda bir web uygulaması çalıştırmak, uygulamayı müşterilerinizin kullanımına sunmayı sağlamanın yalnızca bir adımıdır. Sonraki adımlar aşağıdaki görevleri içerebilir:

- Web uygulamasını Azure Uygulama Hizmeti gibi bir üretim sunucusuna dağıtın. Bkz. [Azure Uygulama Hizmetinde Yayımla](publishing-python-web-applications-to-azure-from-visual-studio.md).

- *templates/404.html*adında bir şablon oluşturarak 404 sayfasını özelleştirin. Mevcut olduğunda, Django varsayılan şablonu yerine bu şablonu kullanır. Daha fazla bilgi için Django belgelerindeki [Hata görünümleri'ne](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) bakın.

- *tests.py*birim testleri yazma ; Visual Studio proje şablonları bunlar için başlangıç noktaları sağlar ve django belgelerinde [django'da](https://docs.djangoproject.com/en/2.0/topics/testing/) test ve test etme ilk [Django uygulamanızı yazma](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) hakkında daha fazla bilgi bulabilirsiniz.

- Uygulamayı SQLite'dan PostgreSQL, MySQL ve SQL Server gibi üretim düzeyinde bir veri deposuna değiştirin (bunların tümü Azure'da barındırılabilir). [SQLite](https://www.sqlite.org/whentouse.html) (sqlite.org) ne zaman kullanılacağı açıklandığı gibi, SQLite az 100K hits / gün ile düşük ve orta trafik siteleri için iyi çalışır, ancak daha yüksek hacimler için tavsiye edilmez. Ayrıca tek bir bilgisayarla sınırlıdır, bu nedenle yük dengeleme ve coğrafi çoğaltma gibi çok sunuculu senaryolarda kullanılamaz. Django'nun diğer veritabanları için desteği hakkında daha fazla bilgi için [Veritabanı kurulumuna](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup)bakın. [Python için Azure SDK'yı](/azure/python/) tablolar ve lekeler gibi Azure depolama hizmetleriyle çalışmak için de kullanabilirsiniz.

- Azure DevOps gibi bir hizmette sürekli tümleştirme/sürekli dağıtım ardışık bir şekilde ayarlayın. Kaynak denetimiyle (Azure Repos veya GitHub veya başka bir yerden) çalışmaya ek olarak, birim testlerinizi serbest bırakma için ön koşul olarak otomatik olarak çalıştıracak bir Azure DevOps Projesi'ni yapılandırabilir ve ayrıca ardışık hattı bir evreleme sunucusuna dağıtacak şekilde yapılandırabilirsiniz. üretime dağıtmadan önce ek testler. Ayrıca Azure DevOps, App Insights gibi izleme çözümleriyle bütünleşir ve çevik planlama araçlarıyla tüm döngüyü kapatır. Daha fazla bilgi için, Azure DevOps projesi ve ayrıca genel [Azure DevOps belgeleriyle](/azure/devops/?view=vsts) [Python için bir CI/CD ardışık alt bilgi](/azure/devops-project/azure-devops-project-python?view=vsts) hattı oluşturma'ya bakın.
