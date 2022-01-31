---
title: Visual Studio 6. adım, proje şablonunu yokladığı için docgo öğreticisini öğrenin
titleSuffix: ''
description: Visual Studio projeler bağlamında, özellikle de yönetim özelleştirmesi gibi docgo Web Project şablonunu yoklayan özellikler olan docgo hakkında bir adım adım yönergeler.
ms.date: 01/25/2022
ms.topic: tutorial
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
monikerRange: vs-2017
ms.workload:
- python
- data-science
ms.openlocfilehash: 072e6040dfca3f2ec78defc3f6a2c41969f2fe1c
ms.sourcegitcommit: 20f9529648e69707063dccb2b15089bf4e9bf639
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "137887144"
---
# <a name="step-6-use-the-polls-django-web-project-template"></a>6. adım: docgo Web Project şablonunu yoklayıp kullanın

**Önceki adım: [Docgo 'da kullanıcıların kimliğini doğrulama](learn-django-in-visual-studio-step-05-django-authentication.md)**

Visual Studio "docgo web Project" şablonunu anlamış olursunuz, artık aynı kod tabanında bulunan ve bir veritabanıyla çalışmayı gösteren "docgo web Project ' i yoklar" adlı üçüncü docgo şablonuna bakabilirsiniz.

Bu adımda şunları yapmayı öğreneceksiniz:

> [!div class="checklist"]
> - Şablondan bir proje oluşturun ve veritabanını başlatın (adım 6-1)
> - Veri modellerini anlama (adım 6-2)
> - Geçişleri Uygula (adım 6-3)
> - Proje şablonu tarafından oluşturulan görünümleri ve sayfa şablonlarını anlayın (adım 6-4)
> - Özel bir yönetim arabirimi oluşturma (adım 6-5)

Bu şablon kullanılarak oluşturulan bir proje, Docgo belgelerinden [Ilk Docgo uygulamanızı yazma](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) öğreticisini izleyerek aldığınız duruma benzer. Web uygulaması, kullanıcıların yoklamaları ve oylar görüntülemesini sağlayan bir genel siteden oluşur ve bu sayede yoklamaları yönetebileceğiniz özel bir yönetim arabirimidir. "docgo Web Project" şablonuyla aynı kimlik doğrulama sistemini kullanır ve aşağıdaki bölümlerde araştırılan docgo modellerini uygulayarak veritabanını daha fazla kullanımını sağlar.

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>Adım 6-1: projeyi oluşturma ve veritabanını başlatma

1. Visual Studio, **Çözüm Gezgini**' e gidin, bu öğreticide daha önce oluşturulan **learningdocgo** çözümüne sağ tıklayın ve **yeni Project** **ekle**  >  ' yi seçin. (Alternatif olarak, yeni bir çözüm kullanmak isterseniz **Dosya**  >  ' yı seçin. **Yeni**  >  bunun yerine **Project** .)

1. yeni proje iletişim kutusunda, **docgo Web Project şablonunu yoklayıp** seçin, "DjangoPolls" projesini çağırın ve **tamam**' ı seçin.

1. Visual Studio diğer proje şablonları gibi, "docgo Web Project yokladığı şablon bir *requirements.txt* dosyası içeriyorsa Visual Studio istemler bu bağımlılıkların nereye yükleneceğini sorar. **Bir sanal ortama yükleyip**, sanal **ortam ekle** iletişim kutusunda Varsayılanları kabul etmek için **Oluştur** seçeneğini belirleyin.

1. Python sanal ortamı ayarlamayı tamamladıktan sonra, veritabanını başlatmak ve bir Docgo süper kullanıcısı (yani bir yönetici) oluşturmak için görüntülenen *readme.html* yönergeleri izleyin. Adımlar ilk olarak **Çözüm Gezgini**' de **DjangoPolls** projesine sağ tıklayıp **Python**  >  **docgo geçişi** komutunu seçin, ardından projeye tekrar sağ tıklayın, **Python**  >  **docgo süper kullanıcı oluştur** komutunu seçin ve istemleri izleyin. (Önce bir süper kullanıcı oluşturmaya çalışırsanız, veritabanı başlatılmadığından bir hata görürsünüz.)

1. **DjangoPolls** projesini, **Çözüm Gezgini** ' de projeye sağ tıklayıp **başlangıç Project olarak ayarla**' yı seçerek Visual Studio çözüm için varsayılan olacak şekilde ayarlayın. Kalın olarak gösterilen başlangıç projesi, hata ayıklayıcıyı başlattığınızda çalıştırılan şeydir.

1.  > Sunucuyu çalıştırmak için hata ayıklama **başlatma hata ayıklamayı Başlat** (**F5**) veya araç çubuğundaki **Web sunucusu** **düğmesini seçin:**

    ![Visual Studio Web sunucusu araç çubuğu düğmesini Çalıştır](media/django/run-web-server-toolbar-button.png)

1. Şablon tarafından oluşturulan uygulamanın, en üst gezinti çubuğunu kullanarak gittiğiniz üç sayfası, ev, bilgi ve Ilgili kişi vardır. uygulamanın farklı parçalarını incelemek için bir dakika veya iki dakikanızı alın (hakkında ve ilgili sayfalar "docgo Web Project" ile çok benzer ve daha fazla açıklanmıyor).

    ![docgo Web Project uygulamasındaki yoklamaları için tam tarayıcı görünümü](media/django/step06-full-app-view.png)

1. Ayrıca, yönetim arabiriminin yalnızca kimliği doğrulanmış Yöneticiler için yetkilendirilmiş olduğunu göstermek için bir oturum açma ekranı görüntüleyen gezinti çubuğunda **Yönetim** bağlantısını seçin. Süper Kullanıcı kimlik bilgilerini kullanın ve bu proje şablonu kullanılırken varsayılan olarak etkinleştirilen "/admin" sayfasına yönlendirilmiştiniz.

    ![docgo Web Project uygulamasını yoklayan yönetim görünümü](media/django/step06-polls-administrative-interface.png)

1. Uygulamanın, izleyen bölümler için çalışır durumda kalmasını sağlayabilirsiniz.

    Uygulamayı durdurmak ve [kaynak denetimine değişiklikleri uygulamak](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)istiyorsanız, önce **Takım Gezgini** içindeki **değişiklikler** sayfasını açın, sanal ortam (Belki de **env**) klasörüne sağ tıklayın ve **Bu yerel öğeleri yoksay**' ı seçin.

### <a name="examine-the-project-contents"></a>Proje içeriğini inceleyin

Daha önce belirtildiği gibi. "docgo Web Project tarafından oluşturulan bir projede ne kadar çok), Visual Studio diğer proje şablonlarını araştırdıysanız, şablon tanıdık gelmelidir. Bu makaledeki ek adımlar, veri modelleri ve ek görünümler gibi daha önemli değişiklikler ve eklemeler özetler.

### <a name="question-what-does-the-django-migrate-command-do"></a>Soru: Docgo geçişi komutu ne yapar?

Cevap: **Docgo geçiş** komutu özellikle, daha önce çalıştırmayan *uygulama/geçiş* klasöründe betikleri çalıştıran komutu çalıştırır `manage.py migrate` . Bu durumda, komut veritabanında gerekli şemayı ayarlamak için bu klasördeki *0001_initial. Kopyala* komut dosyasını çalıştırır.

Geçiş betiği, uygulamanın *models.py* dosyasını tarayan, onu veritabanının geçerli durumuyla karşılaştıran ve ardından veritabanı şemasını geçerli modellerle eşleşecek şekilde geçirmek için gerekli betikleri üreten komut tarafından `manage.py makemigrations` oluşturulur. Bu Docgo özelliği, modellerinizi zaman içinde güncelleştirdiğinizde ve değiştirirken oldukça güçlüdür. Geçişler oluşturup çalıştırdığınızda, modelleri ve veritabanını çok az zorluk ile eşitlenmiş halde tutabilirsiniz.

Bu makalenin ilerleyen bölümlerinde 6-3 adımında bir geçişle çalışırsınız.

## <a name="step-6-2-understand-data-models"></a>Adım 6-2: veri modellerini anlama

Yoklama ve seçim adlı uygulama modelleri *App/modeller. Kopyala* bölümünde tanımlanmıştır. , ' Dan `django.db.models.Model` türetilen ve ' ın sınıf, veritabanı sütunları ile eşlenen modeldeki alanları tanımlamak için ve `IntegerField` gibi `CharField` yöntemleri `models` kullanan bir Python sınıfıdır.

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

Görebileceğiniz gibi, bir yoklama, alanında bir açıklama `text` ve içinde `pub_date` bir yayımlama tarihi tutar. Bu alanlar, veritabanında yoklama için mevcut olan tek alanlardır; `total_votes` alan çalışma zamanında hesaplanır.

Seçim, alan aracılığıyla `poll` bir yoklama ile ilgilidir, içinde `text` bir açıklama içerir ve içinde `votes` Bu seçenek için bir sayı tutar. `votes_percentage`Alan çalışma zamanında hesaplanır ve veritabanında bulunamadı.

Alan türlerinin `CharField` tam listesi (sınırlı metin) `TextField` (sınırsız metin), `EmailField` , `DateTimeField` `URLField` `IntegerField` ,,, `DecimalField` , `BooleanField` , `ForeignKey` , ve. `ManyToMany` Her alan gibi `max_length` bazı öznitelikleri alır. `blank=True`Özniteliği alanın isteğe bağlı olduğu anlamına gelir; `null=true` bir değer isteğe bağlıdır. Ayrıca değerleri veri değeri/görüntü değer tanımlama grupları dizisindeki değerlere sınırlayan bir `choices` özniteliği vardır. (Docgo belgelerindeki [model alan başvurusuna](https://docs.djangoproject.com/en/2.0/ref/models/fields/) bakın.)

[SQLite tarayıcısı](https://sqlitebrowser.org/)gibi bir araç kullanarak, projedeki *DB. SQLite3* dosyasını inceleyerek veritabanında nelerin depolandığını tam olarak doğrulayabilirsiniz. Veritabanında, seçim modelinde olduğu gibi `poll` bir yabancı anahtar alanının olarak `poll_id` depolandığını görürsünüz; Docgo eşlemeyi otomatik olarak işler.

Genel olarak, DMİ go 'da veritabanımız ile çalışmak, Docgo 'nun sizin adınıza temel alınan veritabanını yönetebilmesi için modelleriniz aracılığıyla özel olarak çalışıyor demektir.

### <a name="seed-the-database-from-samplesjson"></a>Veritabanını Samples. JSON öğesinden çekirdek yapın

Başlangıçta, veritabanı hiçbir yoklama içermez. "/Admin" URL 'sindeki yönetim arabirimini kullanarak el ile yoklamalar ekleyebilirsiniz ve ayrıca veritabanını uygulamanın *Samples. JSON* dosyasında tanımlanan yoklamalarda eklemek için çalışan sitede "/Seed" sayfasını da ziyaret edebilirsiniz.

Docgo projesinin *URLs.py* EKLENMIŞ bir URL kalıbı `url(r'^seed$', app.views.seed, name='seed'),` vardır. `seed` *App/views. Kopyala* 'daki görünüm, *Samples. JSON* dosyasını yükler ve gerekli model nesnelerini oluşturur. Docgo daha sonra otomatik olarak ilgili veritabanında eşleşen kayıtları oluşturur.

Görünümün yetkilendirme düzeyini göstermek için dekoratörün kullanımını `@login_required` göz önünde edin.

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

![çekirdek oluşturulmuş bir veritabanıyla docgo Web Project uygulamasını yoklar](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>Soru: Docgo yönetim yardımcı programını kullanarak veritabanını başlatmak mümkün mü?

Cevap: Evet, [docgo-admin LoadData komutunu](https://docs.djangoproject.com/en/2.0/ref/django-admin/#loaddata) kullanarak uygulamadaki dengeli dağıtım sayfasıyla aynı görevi gerçekleştirebilirsiniz. Tam bir Web uygulaması üzerinde çalışırken, iki yöntemin bir bileşimini kullanabilirsiniz: komut satırından bir veritabanı başlatabilir ve ardından çekirdek sayfasını buraya, sabit kodlanmış bir dosyaya güvenmek yerine, herhangi bir rastgele JSON gönderebileceğiniz bir API 'ye dönüştürebilirsiniz.

## <a name="step-6-3-use-migrations"></a>Adım 6-3: geçişleri kullanma

projeyi oluşturduktan sonra komutu çalıştırdığınızda `manage.py makemigrations` (Visual Studio bağlam menüsünü kullanarak), dosya *uygulaması/geçişleri/0001_initial. kopyala* dosyasını oluşturdunuz. Bu dosya, ilk veritabanı tablolarını oluşturan bir komut dosyası içerir.

Modellerinizde zaman içinde değişiklikler yapmanız gerektiği için, bu modellerle temel alınan veritabanı şemasını güncel tutmayı kolaylaştırır. Genel iş akışı aşağıdaki gibidir:

1. *Models.py* dosyanızdaki modellerdeki değişiklikleri yapın.
1. Visual Studio, **Çözüm Gezgini** projeye sağ tıklayın ve **Python**  >  **docgo geçişleri yap** komutunu seçin. Daha önce açıklandığı gibi, bu komut, veritabanını geçerli durumundan yeni duruma geçirmek için *uygulama/geçişlerde* betikler oluşturur.
1. Betikleri gerçek veritabanına uygulamak için, projeye tekrar sağ tıklayın ve **Python**  >  **docgo geçişi**' ni seçin.

Docgo, belirli bir veritabanına uygulanan geçişleri izler, örneğin, Migrate komutunu çalıştırdığınızda Docgo, hangi geçişlerin gerekli olduğunu uygular. Yeni, boş bir veritabanı oluşturursanız, geçiş komutunun çalıştırılması, her geçiş betiği uygulanarak geçerli modellerinizde güncel hale getirir. Benzer şekilde, birden çok model değişikliği yaparsanız ve bir geliştirme bilgisayarında geçişler oluşturursanız, üretim sunucunuzdaki Migrate komutunu çalıştırarak toplu geçişleri üretim veritabanınıza uygulayabilirsiniz. Docgo, yalnızca üretim veritabanının son geçişinden bu yana oluşturulmuş olan geçiş betiklerini uygular.

Bir modeli değiştirmenin etkisini görmek için aşağıdaki adımları deneyin:

1. İsteğe `author` bağlı bir alan eklemek için alandan sonra `pub_date` aşağıdaki satırı ekleyerek *App/modeller. Kopyala* içindeki yoklama modeline isteğe bağlı bir yazar alanı ekleyin:

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. Dosyayı kaydedin, sonra **Çözüm Gezgini** ' de **DjangoPolls** projesine sağ tıklayın ve **Python**  >  **docgo geçişleri yap** komutunu seçin.
1. "**tüm dosyaları göster** " komutunu **Project**  >  seçerek, adı **002_auto_** ile başlayan **geçişler** klasöründe yeni oluşturulan betiği görüntüleyin. Bu dosyaya sağ tıklayın ve **Project dahil et**' i seçin. sonra özgün görünümü geri yüklemek için **Project**  >  **tüm dosyaları yeniden göster** ' i seçebilirsiniz. (Bu adımla ilgili ayrıntılar için aşağıdaki ikinci soruya bakın.)
1. İsterseniz, Docgo 'nun önceki model durumundan yeni duruma nasıl değişiklik olduğunu incelemek için bu dosyayı açın.
1. Visual Studio projesine tekrar sağ tıklayın ve değişiklikleri veritabanına uygulamak için **Python**  >  **docgo geçişi** ' ni seçin.
1. İsterseniz, değişikliği onaylamak için veritabanını uygun bir görüntüleyicide açın.

Genel, Dibgo 'nun geçiş özelliği, veritabanı şemanızı hiçbir şekilde el ile yönetmeyeceğiniz anlamına gelir. Modellerinizde değişiklikler yapmanız, geçiş betikleri oluşturmanız ve geçirme komutuyla uygulamanız yeterlidir.

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>Soru: modellere değişiklikler yaptıktan sonra Migrate komutunu çalıştırmayı unutursam ne olur?

Cevap: Modeller veritabanındakilerle eşlemezse Django uygun özel durumlar dışında çalışma zamanında başarısız olur. Örneğin, önceki bölümde gösterilen model değişikliğini geçirmeyi unutursanız böyle bir sütun yok hatasını **alırsınız: app_poll.author**:

![Model değişikliği geçirilmezken gösterilen hata](media/django/step06-exception-when-forgetting-to-migrate.png).

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>Soru: Django Make Migrations Çözüm Gezgini yeni oluşturulan betikleri neden gösteresiniz?

Cevap: Yeni oluşturulan betikler *app/migrations* klasöründe mevcut olsa da ve **Django Geçişi** komutu çalıştırılırken uygulansa da, Çözüm Gezgini'de otomatik olarak görünmezler çünkü Visual Studio projesine eklenmezler. Bunları görünür hale Project **Tüm** **Dosyaları** >  Göster menü komutunu veya aşağıdaki resimde özetlenen araç çubuğu düğmesini seçin. Bu komut **Çözüm Gezgini** proje klasörüne eklenmeden öğeler için noktalı ana hat simgesi kullanarak proje klasöründeki tüm dosyaları göstermenizi sağlar. Eklemek istediğiniz dosyalara sağ tıklayın ve bir sonraki **işlemeyle birlikte Project** denetimine de dahil olan Dahil Etme'yi seçin.

![komutuna Project komutuna Çözüm Gezgini](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>Soru: Geçiş komutunu çalıştırmadan önce hangi geçişlerin uygulan olacağını görebilir miyim?

Cevap: Evet, [django-admin showmigrations komutunu kullanın](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations).

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>6.-4. Adım: Proje şablonu tarafından oluşturulan görünümleri ve sayfa şablonlarını anlama

Hakkında ve kişi sayfalarının görünümleri gibi "Polls Django Web Project" şablonu tarafından oluşturulan görünümlerin çoğu, bu öğreticinin önceki adımlarında üzerinde çalıştığınız "Django Web Project" şablonu tarafından oluşturulan görünümlere oldukça benzer. Yoklamalar uygulamasındaki fark, giriş sayfasının modelleri kullanması ve yoklama sonuçlarını oylamak ve görüntülemek için eklenen birkaç sayfayı kullanmasıdır.

İlk olarak, Django `urlpatterns` projesinin urls.py dizisinde yer alan ilk satır, uygulama  görünümüne basit bir yönlendirmeden fazlasıdır. Bunun yerine, uygulamanın kendi *urls.py çeker:*

```python
from django.conf.urls import url, include
import app.views

urlpatterns = [
    url(r'^', include('app.urls', namespace="app")),
    # ..
]
```

Ardından *app/urls.py* dosyası biraz daha ilginç yönlendirme kodu (açıklamalı açıklamalar eklendi) içerir:

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

Burada kullanılan daha karmaşık normal ifadeler hakkında bilginiz yoksa, düz dilde bir açıklama için [ifadeyi regex101.com](https://regex101.com/) içine yapıştırarak ifadeyi yapıştırsınız. (Eğik çizgilerden `/` `\` önce bir eğik çizgi ekleyerek eğik çizgiden kaçabilirsiniz; dizenin ön eki nedeniyle "ham" anlamına gelen kaçış Python'da `r` gerekli değildir.

Django'da söz dizimi `?P<name>pattern` , görünümlere `name`görünme sırasına göre bağımsız değişken olarak geçirilen adlı bir grup oluşturur. Daha önce gösterilen kodda adlı `PollsDetailView` bir `PollsResultsView` bağımsız değişken alır ve `pk` adlı `app.views.vote` bir bağımsız değişken alır `poll_id`.

Ayrıca görünümlerin çoğunun *app/views.py'de bir görünüm işlevine doğrudan başvurular olmadığını da görüyorsunuz*. Bunun yerine, çoğu aynı dosyada veya türetilen bir sınıfa `django.views.generic.ListView` başvurur `django.views.generic.DetailView`. Temel sınıflar, şablonu `as_view` tanımlamak için bağımsız değişken alan `template_name` yöntemleri sağlar. Giriş `ListView` sayfası için kullanılan temel sınıf, `queryset` `context_object_name` verileri içeren bir özellik ve şablonda verilere başvurmak istediğiniz değişken adına (bu durumda) sahip bir özellik de bekler `latest_poll_list`.

Artık app `PollListView` /views.py içinde aşağıdaki gibi tanımlanan giriş sayfası *için sayfasını inceleyebilirsiniz*:

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

Burada yapılan tek şey görünümün (Yoklama) `get_context_data` `title` `year` ile birlikte çalıştığını tanımlamak ve bağlama ve değerleri eklemek için yöntemini geçersiz kılmaktır.

Şablonun (*templates/app/index.html*) çekirdeği aşağıdaki gibidir:

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

Basitçe ifade etmek gerekirse `latest_poll_list`, şablon içinde Yoklama nesnelerinin listesini alır ve ardından bu listede yineler ve yoklamanın değerini kullanarak her bir yoklamanın bağlantısını içeren bir tablo satırı `text` oluşturur. Etikette `{% url %}` , "app:detail", bağımsız değişken olarak kullanılarak *app/urls.py'de* "detail" adlı URL desenini `poll.id` ifade eder. Bunun etkisi Django'nun uygun deseni kullanarak bir URL oluşturduğu ve bağlantı için bunu kullandığıdır. Bu bit gelecek proofing, URL desenini istediğiniz zaman değiştirerek oluşturulan bağlantıların otomatik olarak eşleşmesi için güncelleştirilecek şekilde değişebilirsiniz.

`PollDetailView` *app/views.py'de* (burada gösterilmez) `PollListView` ve `PollResultsView` sınıfları, bunun yerine türetmeleri dışında neredeyse aynıdır`DetailView`. İlgili şablonlar, *app/templates/details.html* *ve app/templates/results.html* çeşitli HTML denetimlerinde modellerden uygun alanları yer alıyor. Örneğin,details.htmlbir ** html formu içinde yer alan ve /vote URL'sinde post (POST) özelliğine sahip olan benzersiz bir parçadır. Daha önce de olduğu gibi, bu URL `app.views.vote`deseni aşağıdaki gibi uygulanan adresine yönlendirildi ( `poll_id` bu görünüm için yönlendirmede kullanılan normal ifadede yine adlandırılmış bir grup olan bağımsız değişkenini not edin):

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

Burada, görünümün diğer sayfalar gibi kendi karşılık gelen şablonu yok. Bunun yerine, seçilen yoklama doğrulanır ve yoklama yoksa 404 gösterir (yalnızca birisi "vote/1a2b3c" gibi bir URL girerse). Ardından, oy veren seçimin yoklama için geçerli olduğundan emin olur. Yoksa, blok `except` yalnızca ayrıntılar sayfasını bir hata iletisiyle yeniden işler. Seçim geçerli ise görünümde oy uzun olur ve sonuçlar sayfasına yeniden yönlendirilmesi gerekir.

## <a name="step-6-5-create-a-custom-administration-interface"></a>6-5. Adım: Özel yönetim arabirimi oluşturma

"Polls Django Web Project" şablonunun son parçaları, bu makalenin 6-1. adımlarında gösterildiği gibi varsayılan Django yönetim arabirimine özel uzantılardır. Varsayılan arabirim kullanıcı ve grup yönetimi sağlar ancak başka bir şey yoktur. Yoklamalar proje şablonu, yoklamaları yönetmenize olanak sağlayan özellikler de ekler.

İlk olarak, Django  `url(r'^admin/', include(admin.site.urls)),` projesinin çalışma urls.py URL desenleri varsayılan olarak dahil edilir; "admin/doc" deseni de dahil edilir ancak açıklamaya açıklama eklidir.

Uygulama daha sonra admin.py dosyasını *içerir. Bu* dosya, Django'nun `django.contrib.admin` `INSTALLED_APPS` yönetim arabirimini ziyaret etme sırasında otomatik olarak çalıştırılacağı dosya *settings.py.* Proje şablonu tarafından sağlanan bu dosyada yer alan kod aşağıdaki gibidir:

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

Sizin de gördüğünüz gibi sınıf `PollAdmin` , `django.contrib.admin.ModelAdmin` `Poll` modelden yönetecekleri adları kullanarak bir dizi alandan türettir ve özelleştirmektedir. Bu alanlar Django [belgelerinde ModelAdmin](https://docs.djangoproject.com/en/2.0/ref/contrib/admin/#modeladmin-options) seçeneklerinde açıklanmıştır.

çağrısı daha `admin.site.register` sonra bu sınıfı modele (`Poll`) bağlar ve yönetici arabirimine ekler. Genel sonuç aşağıda gösterilmiştir:

![Polls Django Web uygulaması yönetim Project görünümü](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>Sonraki adımlar

> [!Note]
> Bu öğretici boyunca Visual Studio çözümlerinizi kaynak denetimine sunuyorsanız, şimdi başka bir işleme yapmak için iyi bir zamandır. Çözümünüz, microsoft[/python-sample-vs-learning-django GitHub öğretici kaynak koduyla eşleşmeli](https://github.com/Microsoft/python-sample-vs-learning-django).

Artık Visual Studio'daki "Blank Django Web Project", "Django Web Project" ve "Polls Django Web Project" şablonlarının tamamını Visual Studio. Görünümleri ve şablonları kullanma gibi Django ile ilgili tüm temel bilgileri öğrendin, ayrıca yönlendirme, kimlik doğrulaması ve veritabanı modellerini kullanma hakkında bilginiz var. Artık ihtiyacınız olan görünümlere ve modellere sahip bir web uygulaması oluşturabileceksiniz.

Geliştirme bilgisayarınızda web uygulaması çalıştırma, uygulamayı müşterileriniz için kullanılabilir hale uygulamanın yalnızca bir adımıdır. Sonraki adımlar aşağıdaki görevleri içerebilir:

- Web uygulamasını üretim sunucusuna dağıtın, örneğin Azure App Service. Bkz [. Azure App Service'da yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md).

- templates/404.htmladlı bir şablon oluşturarak 404 *sayfasını özelleştirin*. Django mevcut olduğunda varsayılan şablonu yerine bu şablonu kullanır. Daha fazla bilgi için Django [belgelerinde](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) Hata görünümleri'ne bakın.

- Birim testlerini *tests.py;* Visual Studio proje şablonları bunlar için başlangıç noktaları sağlar ve Django belgelerinde İlk [Django](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) uygulamanızı yazma, 5. bölüm - [Django'da](https://docs.djangoproject.com/en/2.0/topics/testing/) test etme ve Test etme bölümünde daha fazla bilgi bulabilirsiniz.

- Uygulamayı SQLite'dan PostgreSQL, MySQL ve SQL Server (bunların hepsi Azure'da barındırabilirsiniz) gibi üretim düzeyinde bir veri deposuna değiştirme. SQLite (sqlite.org) ne zaman kullanılır? konusunda açıklandığı gibi, [SQLite](https://www.sqlite.org/whentouse.html) günde 100.000'den az isabete sahip düşük ve orta ölçekli trafik siteleri için iyi çalışır, ancak daha yüksek birimler için önerilmez. Ayrıca tek bir bilgisayarla da sınırlıdır, bu nedenle yük dengeleme ve coğrafi çoğaltma gibi çok sunuculu senaryolarda kullanılamaz. Django'nun diğer veritabanları için desteği hakkında bilgi için bkz. [Veritabanı kurulumu](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup). Tablolar ve bloblar [gibi Azure depolama hizmetleriyle](/azure/python/) çalışmak üzere Python için Azure SDK'yı da kullanabilirsiniz.

- Azure DevOps gibi bir hizmette sürekli tümleştirme/sürekli dağıtım işlem hattı Azure DevOps. Kaynak denetimiyle (Azure Repos veya GitHub veya başka bir yerde) çalışmaya ek olarak, birim testlerinizi yayın için önkul olarak otomatik olarak çalıştırmak üzere bir Azure DevOps Project yapılandırabilirsiniz ve ayrıca işlem hattını üretime dağıtmadan önce ek testler için bir hazırlama sunucusuna dağıtacak şekilde yapılandırabilirsiniz. Azure DevOps, App Analizler gibi izleme çözümleriyle tümleştirildi ve çevik planlama araçlarıyla döngünin tamamını kapatıyor. Daha fazla bilgi için Azure DevOps projesiyle [Python için CI/CD](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true) işlem hattı oluşturma ve genel Azure DevOps [bakın](/azure/devops/?view=vsts&preserve-view=true).
