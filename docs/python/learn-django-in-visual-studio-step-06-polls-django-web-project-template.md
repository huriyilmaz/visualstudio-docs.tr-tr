---
title: Visual Studio adım 6 ' da Docgo öğreticisini öğrenin, proje şablonunu yoklar
titleSuffix: ''
description: Visual Studio projeleri bağlamında, özellikle de yönetim özelleştirmesi gibi Docgo Web projesi şablonunu Yoklakla ilgili temel bilgileri bildiren bir adım adım yönergeler.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 1f81c665bc742daf7e2b0e34a849aad566362a28
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099342"
---
# <a name="step-6-use-the-polls-django-web-project-template"></a>6. Adım: Docgo Web proje şablonunu yoklayan şekilde kullanın

**Önceki adım: [Docgo 'da kullanıcıların kimliğini doğrulama](learn-django-in-visual-studio-step-05-django-authentication.md)**

Visual Studio 'nun "Docgo Web projesi" şablonunu anlamış olursunuz, ancak aynı kod tabanında bulunan ve bir veritabanıyla çalışmayı gösteren "docgo Web projesini Yoklat" adlı üçüncü Docgo şablonuna bakabilirsiniz.

Bu adımda şunları yapmayı öğreneceksiniz:

> [!div class="checklist"]
> - Şablondan bir proje oluşturun ve veritabanını başlatın (adım 6-1)
> - Veri modellerini anlama (adım 6-2)
> - Geçişleri Uygula (adım 6-3)
> - Proje şablonu tarafından oluşturulan görünümleri ve sayfa şablonlarını anlayın (adım 6-4)
> - Özel bir yönetim arabirimi oluşturma (adım 6-5)

Bu şablon kullanılarak oluşturulan bir proje, Docgo belgelerinden [Ilk Docgo uygulamanızı yazma](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) öğreticisini izleyerek aldığınız duruma benzer. Web uygulaması, kullanıcıların yoklamaları ve oylar görüntülemesini sağlayan bir genel siteden oluşur ve bu sayede yoklamaları yönetebileceğiniz özel bir yönetim arabirimidir. "Docgo Web projesi" şablonuyla aynı kimlik doğrulama sistemini kullanır ve aşağıdaki bölümlerde araştırılan Docgo modellerini uygulayarak veritabanını daha fazla kullanımını sağlar.

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>Adım 6-1: projeyi oluşturma ve veritabanını başlatma

1. Visual Studio 'da **Çözüm Gezgini**gidin, bu öğreticide daha önce oluşturulan **learningdocgo** çözümüne sağ tıklayın ve **Add**  >  **Yeni proje**Ekle ' yi seçin. (Alternatif olarak, yeni bir çözüm kullanmak isterseniz **Dosya**  >  ' yı seçin. **Yeni**  >  Bunun yerine **Proje** .)

1. Yeni proje iletişim kutusunda, **Docgo Web projesi şablonunu yoklayıp** seçin, "DjangoPolls" projesini çağırın ve **Tamam**' ı seçin.

1. Visual Studio 'daki diğer proje şablonları gibi, "Docgo Web projesini yoklamalar" şablonu bir *requirements.txt* dosyası Içeriyorsa, Visual Studio komut istemleri bu bağımlılıkların nereye yükleneceğini sorar. **Bir sanal ortama yükleyip**, sanal **ortam ekle** iletişim kutusunda Varsayılanları kabul etmek için **Oluştur** seçeneğini belirleyin.

1. Python sanal ortamı ayarlamayı tamamladıktan sonra, veritabanını başlatmak ve bir Docgo süper kullanıcısı (yani bir yönetici) oluşturmak için görüntülenen *readme.html* içindeki yönergeleri izleyin. Adımlar ilk olarak **Çözüm Gezgini**' de **DjangoPolls** projesine sağ tıklayıp **Python**  >  **docgo geçişi** komutunu seçin, ardından projeye tekrar sağ tıklayın, **Python**  >  **docgo süper kullanıcı oluştur** komutunu seçin ve istemleri izleyin. (Önce bir süper kullanıcı oluşturmaya çalışırsanız, veritabanı başlatılmadığından bir hata görürsünüz.)

1. **Çözüm Gezgini** ' de projeye sağ tıklayıp **Başlangıç projesi olarak ayarla**' yı seçerek **DjangoPolls** projesini Visual Studio çözümü için varsayılan olacak şekilde ayarlayın. Kalın olarak gösterilen başlangıç projesi, hata ayıklayıcıyı başlattığınızda çalıştırılan şeydir.

1. Sunucuyu çalıştırmak için **hata ayıklama**  >  **başlatma hata ayıklamayı Başlat** (**F5**) veya araç çubuğundaki **Web sunucusu** düğmesini seçin:

    ![Visual Studio 'da Web sunucusu araç çubuğu düğmesini Çalıştır](media/django/run-web-server-toolbar-button.png)

1. Şablon tarafından oluşturulan uygulamanın, en üst gezinti çubuğunu kullanarak gittiğiniz üç sayfası, ev, bilgi ve Ilgili kişi vardır. Uygulamanın farklı kısımlarını incelemek için bir dakika veya iki dakikanızı alın (hakkında ve Ilgili sayfalar "Docgo web projesine çok benzer" ve daha fazla açıklanmazlar).

    ![Docgo Web projesi uygulamasının yokladığı tam tarayıcı görünümü](media/django/step06-full-app-view.png)

1. Ayrıca, yönetim arabiriminin yalnızca kimliği doğrulanmış Yöneticiler için yetkilendirilmiş olduğunu göstermek için bir oturum açma ekranı görüntüleyen gezinti çubuğunda **Yönetim** bağlantısını seçin. Süper Kullanıcı kimlik bilgilerini kullanın ve bu proje şablonu kullanılırken varsayılan olarak etkinleştirilen "/admin" sayfasına yönlendirilmiştiniz.

    ![Docgo Web projesi uygulamasındaki yoklamalar yönetim görünümü](media/django/step06-polls-administrative-interface.png)

1. Uygulamanın, izleyen bölümler için çalışır durumda kalmasını sağlayabilirsiniz.

    Uygulamayı durdurmak ve [kaynak denetimine değişiklikleri uygulamak](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)istiyorsanız, önce **Takım Gezgini**içindeki **değişiklikler** sayfasını açın, sanal ortam (Belki de **env**) klasörüne sağ tıklayın ve **Bu yerel öğeleri yoksay**' ı seçin.

### <a name="examine-the-project-contents"></a>Proje içeriğini inceleyin

Daha önce belirtildiği gibi. Visual Studio 'daki diğer proje şablonlarını araştırdıysanız, "Docgo Web projesini Yokladır" şablonundan oluşturulan bir projede nelerin büyük bölümü tanıdık gelmelidir. Bu makaledeki ek adımlar, veri modelleri ve ek görünümler gibi daha önemli değişiklikler ve eklemeler özetler.

### <a name="question-what-does-the-django-migrate-command-do"></a>Soru: Docgo geçişi komutu ne yapar?

Cevap: **Docgo geçiş** komutu özellikle `manage.py migrate` , daha önce çalıştırmayan *uygulama/geçiş* klasöründe betikleri çalıştıran komutu çalıştırır. Bu durumda, komut veritabanında gerekli şemayı ayarlamak için bu klasördeki *0001_initial. Kopyala* komut dosyasını çalıştırır.

Geçiş betiği, `manage.py makemigrations` uygulamanın *models.py* dosyasını tarayan, onu veritabanının geçerli durumuyla karşılaştıran ve ardından veritabanı şemasını geçerli modellerle eşleşecek şekilde geçirmek için gerekli betikleri üreten komut tarafından oluşturulur. Bu Docgo özelliği, modellerinizi zaman içinde güncelleştirdiğinizde ve değiştirirken oldukça güçlüdür. Geçişler oluşturup çalıştırdığınızda, modelleri ve veritabanını çok az zorluk ile eşitlenmiş halde tutabilirsiniz.

Bu makalenin ilerleyen bölümlerinde 6-3 adımında bir geçişle çalışırsınız.

## <a name="step-6-2-understand-data-models"></a>Adım 6-2: veri modellerini anlama

Yoklama ve seçim adlı uygulama modelleri *App/modeller. Kopyala*bölümünde tanımlanmıştır. , ' Dan türetilen ve ' ın `django.db.models.Model` `models` sınıf, `CharField` `IntegerField` veritabanı sütunları ile eşlenen modeldeki alanları tanımlamak için ve gibi yöntemleri kullanan bir Python sınıfıdır.

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

Görebileceğiniz gibi, bir yoklama, alanında bir açıklama `text` ve içinde bir yayımlama tarihi tutar `pub_date` . Bu alanlar, veritabanında yoklama için mevcut olan tek alanlardır; `total_votes` alan çalışma zamanında hesaplanır.

Seçim, alan aracılığıyla bir yoklama ile ilgilidir `poll` , içinde bir açıklama içerir `text` ve içinde bu seçenek için bir sayı tutar `votes` . `votes_percentage`Alan çalışma zamanında hesaplanır ve veritabanında bulunamadı.

Alan türlerinin tam listesi `CharField` (sınırlı metin) `TextField` (sınırsız metin),,,, `EmailField` `URLField` `DateTimeField` `IntegerField` , `DecimalField` , `BooleanField` , `ForeignKey` , ve `ManyToMany` . Her alan gibi bazı öznitelikleri alır `max_length` . `blank=True`Özniteliği alanın isteğe bağlı olduğu anlamına gelir; `null=true` bir değer isteğe bağlıdır. Ayrıca `choices` değerleri veri değeri/görüntü değer tanımlama grupları dizisindeki değerlere sınırlayan bir özniteliği vardır. (Docgo belgelerindeki [model alan başvurusuna](https://docs.djangoproject.com/en/2.0/ref/models/fields/) bakın.)

[SQLite tarayıcısı](https://sqlitebrowser.org/)gibi bir araç kullanarak, projedeki *DB. SQLite3* dosyasını inceleyerek veritabanında nelerin depolandığını tam olarak doğrulayabilirsiniz. Veritabanında, seçim modelinde olduğu gibi bir yabancı anahtar alanının `poll` olarak depolandığını görürsünüz `poll_id` ; Docgo eşlemeyi otomatik olarak işler.

Genel olarak, DMİ go 'da veritabanımız ile çalışmak, Docgo 'nun sizin adınıza temel alınan veritabanını yönetebilmesi için modelleriniz aracılığıyla özel olarak çalışıyor demektir.

### <a name="seed-the-database-from-samplesjson"></a>Veritabanını samples.jstemel alarak

Başlangıçta, veritabanı hiçbir yoklama içermez. "/Admin" URL 'sindeki yönetim arabirimini kullanarak el ile yoklamalar ekleyebilirsiniz ve ayrıca veritabanını uygulamanın *samples.jsdosya üzerinde* tanımlanan yoklamalarda eklemek için çalışan sitede "/Seed" sayfasını da ziyaret edebilirsiniz.

Docgo projesinin *URLs.py* EKLENMIŞ bir URL kalıbı vardır `url(r'^seed$', app.views.seed, name='seed'),` . `seed` *App/views. Kopyala* 'daki görünüm, *samples.js* dosyasına yükler ve gerekli model nesnelerini oluşturur. Docgo daha sonra otomatik olarak ilgili veritabanında eşleşen kayıtları oluşturur.

`@login_required`Görünümün yetkilendirme düzeyini göstermek için dekoratörün kullanımını göz önünde edin.

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

Etkiyi görmek için, hiçbir yokladığı henüz mevcut olmadığını görmek üzere uygulamayı çalıştırın. Ardından "/Seed" URL 'sini ziyaret edin ve uygulama ana sayfaya döndüğünde, yoklamaları kullanılabilir hale geldiğini görmeniz gerekir. Burada, ham *DB. SQLite3* dosyasını [SQLite tarayıcısı](https://sqlitebrowser.org/)gibi bir araçla inceleyebilirsiniz.

![Çekirdek oluşturulmuş bir veritabanıyla Docgo Web projesi uygulamasını yoklar](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>Soru: Docgo yönetim yardımcı programını kullanarak veritabanını başlatmak mümkün mü?

Cevap: Evet, [docgo-admin LoadData komutunu](https://docs.djangoproject.com/en/2.0/ref/django-admin/#loaddata) kullanarak uygulamadaki dengeli dağıtım sayfasıyla aynı görevi gerçekleştirebilirsiniz. Tam bir Web uygulaması üzerinde çalışırken, iki yöntemin bir bileşimini kullanabilirsiniz: komut satırından bir veritabanı başlatabilir ve ardından çekirdek sayfasını buraya, sabit kodlanmış bir dosyaya güvenmek yerine, herhangi bir rastgele JSON gönderebileceğiniz bir API 'ye dönüştürebilirsiniz.

## <a name="step-6-3-use-migrations"></a>Adım 6-3: geçişleri kullanma

`manage.py makemigrations`Projeyi oluşturduktan sonra komutunu çalıştırdığınızda (Visual Studio 'daki bağlam menüsünü kullanarak), dosya *uygulaması/geçişleri/0001_initial. Kopyala* dosyasını oluşturdunuz. Bu dosya, ilk veritabanı tablolarını oluşturan bir komut dosyası içerir.

Modellerinizde zaman içinde değişiklikler yapmanız gerektiği için, bu modellerle temel alınan veritabanı şemasını güncel tutmayı kolaylaştırır. Genel iş akışı aşağıdaki gibidir:

1. *Models.py* dosyanızdaki modellerdeki değişiklikleri yapın.
1. Visual Studio 'da **Çözüm Gezgini** projeye sağ tıklayın ve **Python**  >  **docgo geçişleri yap** komutunu seçin. Daha önce açıklandığı gibi, bu komut, veritabanını geçerli durumundan yeni duruma geçirmek için *uygulama/geçişlerde* betikler oluşturur.
1. Betikleri gerçek veritabanına uygulamak için, projeye tekrar sağ tıklayın ve **Python**  >  **docgo geçişi**' ni seçin.

Docgo, belirli bir veritabanına uygulanan geçişleri izler, örneğin, Migrate komutunu çalıştırdığınızda Docgo, hangi geçişlerin gerekli olduğunu uygular. Yeni, boş bir veritabanı oluşturursanız, geçiş komutunun çalıştırılması, her geçiş betiği uygulanarak geçerli modellerinizde güncel hale getirir. Benzer şekilde, birden çok model değişikliği yaparsanız ve bir geliştirme bilgisayarında geçişler oluşturursanız, üretim sunucunuzdaki Migrate komutunu çalıştırarak toplu geçişleri üretim veritabanınıza uygulayabilirsiniz. Docgo, yalnızca üretim veritabanının son geçişinden bu yana oluşturulmuş olan geçiş betiklerini uygular.

Bir modeli değiştirmenin etkisini görmek için aşağıdaki adımları deneyin:

1. İsteğe bağlı bir alan eklemek için alandan sonra aşağıdaki satırı ekleyerek *App/modeller. Kopyala* içindeki yoklama modeline isteğe bağlı bir yazar alanı ekleyin `pub_date` `author` :

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. Dosyayı kaydedin, sonra **Çözüm Gezgini** ' de **DjangoPolls** projesine sağ tıklayın ve **Python**  >  **docgo geçişleri yap** komutunu seçin.
1. **Project**  >  Yeni oluşturulan betiği, **geçiş** klasörü **002_auto_** ile başlayan geçişler klasöründe görmek için proje**tüm dosyaları göster** komutunu seçin. Bu dosyaya sağ tıklayın ve **projeye dahil et**' i seçin. Sonra **Project**  >  orijinal görünümü geri yüklemek için proje**tüm dosyaları yeniden göster** ' i seçebilirsiniz. (Bu adımla ilgili ayrıntılar için aşağıdaki ikinci soruya bakın.)
1. İsterseniz, Docgo 'nun önceki model durumundan yeni duruma nasıl değişiklik olduğunu incelemek için bu dosyayı açın.
1. Visual Studio projesine tekrar sağ tıklayın ve **Python**  >  değişiklikleri veritabanına uygulamak için Python**docgo geçişi** ' ni seçin.
1. İsterseniz, değişikliği onaylamak için veritabanını uygun bir görüntüleyicide açın.

Genel, Dibgo 'nun geçiş özelliği, veritabanı şemanızı hiçbir şekilde el ile yönetmeyeceğiniz anlamına gelir. Modellerinizde değişiklikler yapmanız, geçiş betikleri oluşturmanız ve geçirme komutuyla uygulamanız yeterlidir.

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>Soru: modellere değişiklikler yaptıktan sonra Migrate komutunu çalıştırmayı unutursam ne olur?

Cevap: modeller veritabanındaki verilerle eşleşmezse, uygun özel durumlarla birlikte, çalışma zamanında Docgo başarısız olur. Örneğin, önceki bölümde gösterilen model değişikliğini geçirmeyi unutursanız, bu sütun için bir hata görürsünüz **: app_poll. Author**:

![Model değişikliği geçirildiğinde gösterilen hata](media/django/step06-exception-when-forgetting-to-migrate.png).

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>Soru: Docgo geçişi gerçekleştirildikten sonra yeni oluşturulan betikleri gösterme Çözüm Gezgini neden yapılamıyor?

Cevap: yeni oluşturulan betikler *uygulama/geçiş* klasöründe bulunmasına rağmen **Docgo geçişi** komutu çalıştırılırken uygulandığından, Visual Studio projesine eklenmemiş olduklarından **Çözüm Gezgini** otomatik olarak görünmez. Bunları görünür yapmak için önce **Proje**  >  **tüm dosyaları göster** menü komutunu ya da aşağıdaki görüntüde özetlenen araç çubuğu düğmesini seçin. Bu komut, projenin kendine eklenmemiş öğeler için noktalı bir ana hat simgesi kullanarak proje klasöründeki tüm dosyaları göstermesini **Çözüm Gezgini** neden olur. Eklemek istediğiniz dosyalara sağ tıklayın ve **projeye dahil et**' i seçin. Bu, bir sonraki Yürütmeyle birlikte kaynak denetiminde de yer alır.

![Çözüm Gezgini içinde proje komutuna dahil et](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>Soru: geçirme komutunu çalıştırmadan önce hangi geçişlerin uygulanacağını görebilir miyim?

Cevap: Evet, [docgo-admin showgeçişleri komutunu](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations)kullanın.

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>Adım 6-4: proje şablonu tarafından oluşturulan görünümleri ve sayfa şablonlarını anlayın

Bu öğreticide daha önce sizinle çalıştığınız "Docgo Web projesi" şablonu tarafından oluşturulan görünümlerin büyük bir çoğunluğu, yaklaşık olarak bu öğreticide daha önce çalıştık. Yoklamalar uygulamasındaki farklı özellikler, giriş sayfasının, oylama ve yoklama sonuçlarını görüntülemek için birkaç eklenen sayfa gibi modelleri kullanmasına olanak sağlar.

İle başlamak için, urls.py dosyasındaki Docgo projesi dizisinin ilk satırı `urlpatterns` yalnızca bir uygulama *urls.py* görünümüne basit bir yönlendirmeden daha fazla. Bunun yerine, uygulamanın kendi *URLs.py* dosyasını çeker:

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

Ayrıca, görünümlerin çoğunun yalnızca *App/views. Kopyala*içindeki bir görünüm işlevine yönelik başvuruları doğrudan yönlendirmediğinden de bakabilirsiniz. Bunun yerine, en çok, veya ' den türetilen aynı dosyadaki bir sınıfa `django.views.generic.ListView` başvurur `django.views.generic.DetailView` . Temel sınıflar `as_view` , `template_name` şablonu tanımlamak için bir bağımsız değişken veren yöntemler sağlar. Ana `ListView` sayfa için kullanılan temel sınıf, `queryset` Bu durumda, verileri içeren bir özelliği ve `context_object_name` şablondaki verilere başvurmak istediğiniz değişken adına sahip bir özelliği de bekler `latest_poll_list` .

Artık `PollListView` *uygulama/görünümlerde*aşağıdaki gibi tanımlanan giriş sayfası için ' i inceleyebilirsiniz:

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

Şablonun çekirdeği (*Templates/App/index.html*) aşağıdaki gibidir:

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

`PollDetailView` `PollResultsView` *App/views. Kopyala* içindeki ve sınıfları (burada gösterilmez), `PollListView` bunun yerine türettikleri hariç neredeyse özdeş olarak görünür `DetailView` . İlgili şablonlar, *App/Templates/details.html* ve *App/Templates/results.html* , daha sonra çeşitli HTML denetimlerinde modellerden uygun alanları yerleştirir. *details.html* 'deki benzersiz bir parça, bir yoklama seçeneklerinin, gönderildiğinde/oy URL 'sine gönderi GÖNDERDIĞI bir HTML biçiminde içermalarıdır. Daha önce görüldüğü gibi, bu URL deseninin öğesine yönlendirilmesi gerekir `app.views.vote` ve bu, aşağıdaki şekilde uygulanır ( `poll_id` Bu görünümün yönlendirmesinde kullanılan normal ifadede bir adlandırılmış grup olan bağımsız değişkeni unutmayın):

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

"Docgo Web projesini Yoklat" şablonunun son parçaları, bu 6-1 makalenin önceki bölümlerinde gösterildiği gibi varsayılan Docgo yönetim arabirimine yönelik özel uzantılardır. Varsayılan arabirim, Kullanıcı ve Grup yönetimi için sağlar, ancak hiçbir şey değildir. Yoklamalar proje şablonu, yoklamaları da yönetmenizi sağlayan özellikler ekler.

İlki, Docgo projesi *URLs.py* içindeki URL desenleri `url(r'^admin/', include(admin.site.urls)),` Varsayılan olarak eklenmiştir; "Yönetici/belge" deseni de dahil edilir ancak açıklama eklenir.

Daha sonra uygulama, *admin.py* `django.contrib.admin` `INSTALLED_APPS` *Settings.py*dizisine dahil olmak üzere yönetim arabirimini ziyaret ettiğinizde docgo 'nun otomatik olarak çalıştığı admin.py dosyasını içerir. Proje şablonu tarafından sağlandığı gibi bu dosyadaki kod aşağıdaki gibidir:

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

![Docgo Web projesi uygulamasındaki yoklamalar yönetim görünümü](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>Sonraki adımlar

> [!Note]
> Visual Studio çözümünüzü Bu öğreticinin tamamında kaynak denetimine uyguladıysanız, başka bir işleme yapmak iyi bir zaman olabilir. Çözümünüz GitHub 'daki öğretici kaynak kodu ile eşleşmelidir: [Microsoft/Python-Sample-vs-Learning-docgo](https://github.com/Microsoft/python-sample-vs-learning-django).

Artık, Visual Studio 'daki "boş Docgo Web projesinden", "Docgo Web Project" ve "Docgo Web projesini Yoklat" şablonlarını tamamen araştırdık. Görünümler ve Şablonlar kullanma gibi Docgo 'un tüm temel bilgilerini öğrendiniz ve veritabanı modellerini kullanarak, bir yönlendirme, kimlik doğrulama ve değişiklik yapabilirsiniz. Artık ihtiyacınız olan herhangi bir görünüm ve modelle kendinizinkini bir Web uygulaması oluşturabilmeniz gerekir.

Geliştirme bilgisayarınızda bir Web uygulaması çalıştırmak, uygulamayı müşterileriniz için kullanılabilir hale getirmek için yalnızca bir adımdır. Sonraki adımlarda aşağıdaki görevler bulunabilir:

- Web uygulamasını Azure App Service gibi bir üretim sunucusuna dağıtın. Bkz. [Azure App Service yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md).

- *Şablonlar/404.html*adlı bir şablon oluşturarak 404 sayfasını özelleştirin. Mevcut olduğunda, Docgo, varsayılan değer yerine bu şablonu kullanır. Daha fazla bilgi için, bkz. Docgo belgelerindeki [hata görünümleri](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) .

- Birim testlerini *Tests.py*'de yazın; Visual Studio proje şablonları bunlar için başlangıç noktaları sağlar ve dmongo belgelerinde dmongo 'da [Ilk Dmongo uygulamanızı yazma, 5. bölüm-test](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) ve [test etme](https://docs.djangoproject.com/en/2.0/topics/testing/) konusunda daha fazla bilgi bulabilirsiniz.

- Uygulamayı SQLite ' dan PostgreSQL, MySQL ve SQL Server (tümü Azure üzerinde barındırılabilen) gibi bir üretim düzeyi veri deposu olarak değiştirin. SQLite (sqlite.org) [ne zaman kullanılacağı](https://www.sqlite.org/whentouse.html) konusunda açıklandığı gibi, SQLite, 100 ' den az KB/gün içinde düşük ve orta ölçekli trafik siteleri için uygundur, ancak daha yüksek birimler için önerilmez. Aynı zamanda tek bir bilgisayarla sınırlandırılmıştır, bu nedenle yük dengeleme ve coğrafi çoğaltma gibi çok sunuculu bir senaryoda kullanılamaz. Docgo 'nun diğer veritabanları için desteği hakkında bilgi için bkz. [veritabanı kurulumu](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup). Ayrıca, [Python Için Azure SDK 'sını](/azure/python/) tablolar ve Bloblar gibi Azure depolama hizmetleriyle birlikte çalışmak için de kullanabilirsiniz.

- Azure DevOps gibi bir hizmette sürekli tümleştirme/sürekli dağıtım işlem hattı ayarlayın. Kaynak denetimiyle (Azure Repos veya GitHub ya da başka bir yerde) çalışmaya ek olarak, bir Azure DevOps projesini, birim testlerinizi bir ön koşul olarak otomatik olarak çalıştıracak şekilde yapılandırabilir ve ayrıca işlem hattını üretime dağıtmadan önce ek testler için bir hazırlama sunucusuna dağıtılacak şekilde yapılandırabilirsiniz. Azure DevOps, Ayrıca, App Insights gibi izleme çözümleriyle tümleştirilir ve çevik planlama araçlarıyla tüm döngüyü kapatır. Daha fazla bilgi için bkz. [Azure DevOps projesiyle Python için BIR CI/CD işlem hattı oluşturma](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true) ve ayrıca genel [Azure DevOps belgeleri](/azure/devops/?view=vsts&preserve-view=true).
