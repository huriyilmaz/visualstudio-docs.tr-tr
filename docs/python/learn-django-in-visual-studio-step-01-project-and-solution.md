---
title: Visual Studio, adım 1, Django temelleri Django öğretici öğrenin
titleSuffix: ''
description: Visual Studio projeleri bağlamında Django temellerinin bir walkthrough, Destek Visual Studio Gösteren Django gelişimi için sağlar.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: b41ed3901cd4ad18a1b52ddbdc7ee6fd82cb5380
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62962257"
---
# <a name="tutorial-get-started-with-the-django-web-framework-in-visual-studio"></a>Öğretici: Visual Studio'daki Django web çerçevesi ile başlayın

[Django,](https://www.djangoproject.com/) hızlı, güvenli ve ölçeklenebilir web geliştirme için tasarlanmış üst düzey bir Python çerçevesidir. Bu öğretici, Visual Studio'nun Django tabanlı web uygulamalarının oluşturulmasını kolaylaştırmak için sağladığı proje şablonları bağlamında Django çerçevesini inceler.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:

> [!div class="checklist"]
> - "Boş Django Web Projesi" şablonu (adım 1) kullanarak Git deposunda temel bir Django projesi oluşturun
> - Tek sayfalı bir Django uygulaması oluşturun ve bu sayfayı şablon kullanarak oluşturun (adım 2)
> - Statik dosyalara hizmet, sayfa ekleme ve şablon kalıtımını kullanma (adım 3)
> - Birden fazla sayfaya ve duyarlı tasarıma sahip bir uygulama oluşturmak için Django Web Project şablonuna bakın (adım 4)
> - Kullanıcıları kimlik doğrulaması (adım 5)
> - Modelleri, veritabanı geçişlerini ve yönetim arabirimine özelleştirmeler kullanan bir uygulama oluşturmak için Polls Django Web Project şablonuna kullanın (adım 6)

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio 2017 veya daha sonra Windows'da aşağıdaki seçeneklerle:
  - **Python geliştirme** iş yükü (Yükleyicideki**iş yükü** sekmesi). Talimatlar için Visual [Studio'da Python desteğini yükleyin'](installing-python-support-in-visual-studio.md)e bakın.
  - **Kod araçları**altında **Tek tek bileşenler** sekmesinde Visual Studio için Windows ve **GitHub Uzantısı** için **Git.**

Django proje şablonları visual studio için Python Tools'un önceki tüm sürümleriyle birlikte verilir, ancak ayrıntılar bu öğreticide tartışılandan farklı olabilir (özellikle Django çerçevesinin önceki sürümlerinde farklıdır).

Python geliştirme şu anda Visual Studio for Mac'te desteklenmez. Mac ve [Linux'ta Visual Studio Code'daki Python uzantısını](https://code.visualstudio.com/docs/python/python-tutorial)kullanın.

### <a name="visual-studio-projects-and-django-projects"></a>"Visual Studio projeleri" ve "Django projeleri"

Django terminolojisinde, bir "Django projesi" tam bir web uygulaması oluşturmak için bir web barındırma ağına dağıttığınız bir veya daha fazla "uygulama" ile birlikte birkaç site düzeyinde yapılandırma dosyasından oluşur. Bir Django projesi birden fazla uygulama içerebilir ve aynı uygulama birden fazla Django projesinde olabilir.

Bir Visual Studio projesi, kendi payına, birden fazla uygulama ile birlikte Django proje içerebilir. Basitlik uğruna, ne zaman bu öğretici sadece bir "proje" anlamına gelir, visual studio proje atıfta bulunuyor. Web uygulamasının "Django projesi" bölümüne atıfta bulunduğunda, özellikle "Django projesi"ni kullanır.

Bu eğitim boyunca, her biri tek bir Django uygulaması içeren üç ayrı Django projesi içeren tek bir Visual Studio çözümü oluşturacaksınız. Projeleri aynı çözümde tutarak, karşılaştırma için farklı dosyalar arasında kolayca geçiş yapabilirsiniz.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Adım 1-1: Visual Studio projesi ve çözümü oluşturun

Komut satırından Django ile çalışırken, genellikle komutu `django-admin startproject <project_name>` çalıştırarak bir proje başlarsınız. Visual Studio'da "Blank Django Web Project" şablonu kullanılarak visual studio projesi ve çözümü içinde aynı yapı yı sağlar.

1. Visual Studio'da **Dosya** > **Yeni** > **Projesi'ni**seçin, "Django"yu arayın ve Boş **Django Web Projesi** şablonunu seçin. (Şablon, sol listede **Python** > **Web** altında da bulunur.)

    ![Blank Django Web Projesi için Visual Studio'da yeni proje iletişim kutusu](media/django/step01-new-blank-project.png)

1. İletişim kutusunun altındaki alanlara aşağıdaki bilgileri girin (önceki grafikte gösterildiği gibi), **tamam'ı**seçin:

    - **Adı**: Visual Studio projesinin adını **BasicProject**olarak ayarlayın. Bu ad, Django projesi için de kullanılır.
    - **Konum**: Visual Studio çözüm ve proje oluşturmak için bir konum belirtin.
    - **Çözüm**: Bu denetim kümesini varsayılan olarak bırakın Yeni çözüm seçeneği **oluştur.**
    - **Çözüm adı**: Bu öğretici birden fazla proje için bir konteyner olarak çözüm için uygun olan **LearningDjango,** ayarlayın.
    - **Çözüm için dizin oluşturma**: Set (varsayılan) bırak.
    - **Yeni Git deposu oluşturun**: Visual Studio'nun çözümü oluşturduğunda yerel bir Git deposu oluşturması için bu seçeneği (varsayılan olarak açık) seçin. Bu seçeneği görmüyorsanız, Visual Studio yükleyicisini çalıştırın ve **Kod araçları**altında **Tek tek bileşenler** sekmesine Windows için Git ve Visual Studio **için** **Git'i** ekleyin.

1. Bir süre sonra, Visual Studio **bu projenin dış paketler gerektirdiğini** belirten bir iletişim kutusu yla sizi ister (aşağıda gösterilmiştir). Şablon en son Django 1.x paketine başvuran bir *requirements.txt* dosyası içerdiğinden bu iletişim kutusu görüntülenir. (Tam bağımlılıkları görmek için **gerekli paketleri göster'i** seçin.)

    ![Projenin dış paketler gerektirdiğini belirten komut istemi](media/django/step01-requirements-prompt-install-myself.png)

1. **Ben onları kendim yükleyeceğim**seçeneğini seçin. Kaynak denetiminin dışında olduğundan emin olmak için kısa süre içinde sanal ortamı oluşturursunuz. (Ortam her zaman *requirements.txt*oluşturulabilir.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Adım 1-2: Git denetimlerini inceleyin ve uzak bir depoda yayımlayın

**Yeni Proje** iletişim kutusunda yeni Git **deposu oluştur'u** seçtiğiniziçin, oluşturma işlemi tamamlanır tamamlanmaz proje zaten yerel kaynak denetimine adanmıştır. Bu adımda, Visual Studio'nun Git denetimlerini ve kaynak denetimiyle çalıştığınız **Team Explorer** penceresini tanıtAbilirsiniz.

1. Visual Studio ana penceresinin alt köşesindeki Git denetimlerini inceleyin. Soldan sağa, bu denetimler itilmemiş taahhütleri, işlenmemiş değişiklikleri, deponun adını ve geçerli dalı gösterir:

    ![Visual Studio penceresinde git denetimleri](media/django/step01-git-controls.png)

    > [!Note]
    > **Yeni Proje** iletişim kutusunda **yeni Git deposu oluştur'u** seçmezseniz, Git denetimleri yalnızca yerel bir depo oluşturan kaynak **denetimine ekle** komutunu gösterir.
    >
    > ![Kaynak Denetimine Ekle, bir depo oluşturmadıysanız Visual Studio'da görünür](media/django/step01-git-add-to-source-control.png)

1. Değişiklikler düğmesini seçin ve Visual Studio **Değişiklikler** sayfasında **Team Explorer** penceresini açar. Yeni oluşturulan proje zaten kaynak denetimine otomatik olarak bağlı olduğundan, bekleyen değişiklikleri görmezsiniz.

    ![Değişiklikler sayfasında Kiteam Gezgini penceresi](media/django/step01-team-explorer-changes.png)

1. Visual Studio durum çubuğunda, Takım Gezgini'nde **Eşitleme** sayfasını açmak için itilmemiş **Team Explorer**commits düğmesini **(2**ile yukarı ok) seçin. Yalnızca yerel bir deponuz olduğundan, sayfa depoyu farklı uzak depolara yayımlamak için kolay seçenekler sağlar.

    ![Kaynak denetimi için kullanılabilir Git deposu seçeneklerini gösteren Takım Gezgini penceresi](media/django/step01-team-explorer.png)

    Kendi projeleriniz için istediğiniz hizmeti seçebilirsiniz. Bu öğretici, öğretici için tamamlanan örnek kodun [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django) deposunda muhafaza edildiği GitHub kullanımını gösterir.

1. **Yayımlama** denetimlerinden birini seçerken, **Takım Gezgini** daha fazla bilgi için sizden istenir. Örneğin, bu öğretici için örnek yayımlarken, önce deponun kendisinin oluşturulması gerekir, bu durumda deponun URL'si ile **Uzak Depoya Push** seçeneği kullanılmıştır.

    ![Varolan bir uzak depoya itmek için Takım Gezgini penceresi](media/django/step01-push-to-github.png)

    Varolan bir deponuz yoksa, **GitHub'a Yayımla** ve **Azure DevOps'e Itme** seçenekleri doğrudan Visual Studio içinden bir depo oluşturmanıza izin vermez.

1. Bu öğretici ile çalışırken, değişiklikleri işlemek ve itmek için Visual Studio'daki denetimleri periyodik olarak kullanma alışkanlığı edinin. Bu öğretici size uygun noktalarda hatırlatıyor.

> [!Tip]
> **Ekip Gezgini**içinde hızla gezinmek için, kullanılabilir sayfaların açılır menüsünü görmek için üstbilgi (yukarıdaki resimlerde **Değişiklikleri** veya **İde'** i okuyan) üstbilgiyi seçin.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Soru: Bir projenin başlangıcından itibaren kaynak denetimi kullanmanın bazı avantajları nelerdir?

Cevap: Her şeyden önce, kaynak denetimini baştan kullanarak, özellikle uzaktan bir depo kullanıyorsanız, projenizin düzenli bir şirket dışı yedeklemesini sağlar. Yalnızca yerel bir dosya sisteminde bir projeyi sürdürmenin aksine, kaynak denetimi aynı zamanda tam bir değişiklik geçmişi ve tek bir dosyayı veya tüm projeyi önceki duruma geri çevirme kolay bir şekilde sağlar. Bu değişiklik geçmişi gerilemelerin (test hataları) nedenini belirlemeye yardımcı olur. Ayrıca, birden çok kişi bir proje üzerinde çalışıyorsa, kaynak denetimi, üzerine yazılar yönetir ve çakışma çözümü sağlar esastır. Son olarak, temelde bir otomasyon biçimi olan kaynak denetimi, yapı, test ve sürüm yönetimini otomatikleştirmek için sizi iyi ayarlar. Bu gerçekten bir proje için DevOps kullanarak ilk adım, ve giriş engelleri çok düşük olduğundan, gerçekten başından itibaren kaynak kontrolü kullanmamak için hiçbir neden yoktur.

Otomasyon olarak kaynak kontrolü hakkında daha fazla tartışma için, the [Source of Truth: The Role of Positories in DevOps](https://msdn.microsoft.com/magazine/mt763232)( MSDN Magazine dergisinde web uygulamaları için de geçerli olan mobil uygulamalar için yazılmış bir makale) başlıklı makaleye bakın.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Soru: Visual Studio'nun yeni bir projeyi otomatik olarak gerçekleştirmesini engelleyebilir miyim?

Cevap: Evet. Otomatik commit devre dışı kalmak için, **Team** **Explorer'da Ayarlar** sayfasına gidin , **Git** > **Global ayarlarını**seçin, **varsayılan olarak birleştirdikten sonra değişiklikleri gerçekleştir**seçeneğini temizleyin, ardından **Güncelleştir'i**seçin.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Adım 1-3: Sanal ortamı oluşturun ve kaynak denetiminden hariç tutun

Artık projeniz için kaynak denetimini yapılandırdığınıza göre, proje için gerekli Django paketlerini içeren sanal ortamı oluşturabilirsiniz. Daha **sonra,** çevre klasörünü kaynak denetiminden dışlamak için Team Explorer'ı kullanabilirsiniz.

1. **Çözüm Gezgini'nde** **Python Ortamları** düğümüne sağ tıklayın ve Sanal Ortam **Ekle'yi**seçin.

    ![Solution Explorer'da Sanal ortam komutu ekleme](media/django/step01-add-virtual-environment-command.png)

1. **Bir Virtual Environment Ekle** iletişim kutusu görüntülenir ve bir ileti ile **gereksinimlerin bir dosyaolduğunu söyleriz.txt dosyası.** Bu ileti, Visual Studio'nun sanal ortamı yapılandırmak için bu dosyayı kullandığını gösterir.

    ![requirements.txt iletisi ile sanal ortam iletişim kutusu ekleme](media/django/step01-add-virtual-environment-found-requirements.png)

1. Varsayılanları kabul etmek için **Oluştur'u** seçin. (İsterseniz sanal ortamın adını değiştirebilirsiniz, bu da alt klasörünün adını `env` değiştirir, ancak standart bir kuraldır.)

1. İstenirse yönetici ayrıcalıklarına izin verin, visual studio paketleri indirirken ve yüklerken birkaç dakika sabırlı olun, bu da Django için binlerce dosyayı yaklaşık birkaç alt klasörde genişletmek anlamına gelir! Visual Studio **Çıktı** penceresinde ilerlemeyi görebilirsiniz. Beklerken, takip eden Soru bölümlerini düşün.

1. Visual Studio Git denetimlerinde (durum çubuğunda), **Team Explorer'da** **Değişiklikler** sayfasını açan değişiklik göstergesini **(&#42;99'u **gösterir) seçin.

    Binlerce değişiklik getiren sanal ortamı oluşturmak, ancak siz (veya projeyi klonlayan herhangi bir kişi) her zaman *gereksinimleri.txt*çevreyi yeniden oluşturabilirsiniz, çünkü kaynak denetimine herhangi birini eklemeniz gerekmez.

    Sanal ortamı dışlamak için **env** klasörünü sağ tıklatın ve **bu yerel öğeleri yoksay'ı**seçin.

    ![Kaynak denetimi değişikliklerinde sanal ortamı yoksayma](media/django/step01-ignore-local-items.png)

1. Sanal ortamı dışladıktan sonra, geriye kalan tek değişiklik proje dosyasında ve *.gitignore'dedir.* *.gitignore* dosyası, sanal ortam klasörü için ek bir giriş içerir. Diff görmek için dosyayı çift tıklatabilirsiniz.

1. İletiyi girin ve **Tümünü İşle** düğmesini seçin, ardından isterseniz iletileri uzaktan deponuza basın.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Soru: Neden sanal bir ortam oluşturmak istiyorum?

Yanıt: Sanal ortam, uygulamanızın tam bağımlılıklarını yalıtmak için harika bir yoldur. Bu tür yalıtım, küresel Python ortamındaki çakışmaları önler ve hem test hem de işbirliğine yardımcı olur. Zaman içinde, bir uygulama geliştirdikçe, her zaman birçok yararlı Python paketi getirirsiniz. Paketleri projeye özgü bir sanal ortamda tutarak, kaynak denetimine dahil edilen ortamı açıklayan projenin *gereksinimleri.txt* dosyasını kolayca güncelleştirebilirsiniz. Proje, yapı sunucuları, dağıtım sunucuları ve diğer geliştirme bilgisayarları da dahil olmak üzere diğer bilgisayarlara kopyalandığında, yalnızca *gereksinimleri.txt* kullanarak ortamı yeniden oluşturmak kolaydır (bu nedenle ortamın kaynak denetiminde olması gerekmez). Daha fazla bilgi için [bkz.](selecting-a-python-environment-for-a-project.md#use-virtual-environments)

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Soru: Kaynak denetimine adanmış bir sanal ortamı nasıl kaldıracağım?

Cevap: İlk olarak, klasörü hariç tutmak için *.gitignore* dosyanızı düzenleyin: açıklama `# Python Tools for Visual Studio (PTVS)` ile sonunda bölümü bulmak `/BasicProject/env`ve sanal ortam klasörü için yeni bir satır ekleyin, gibi . (Visual Studio **dosyayı Solution Explorer'da**göstermediği için **File** > **Dosyayı Aç** > **File** menüsü komutunu kullanarak doğrudan açın. Ayrıca **Takım Gezgini'nden**dosyayı açabilirsiniz: **Ayarlar** **sayfasında, Ayarlar Ayarlarını**seçin, Dosyaları **Yoksay &** bölümüne gidin, ardından **.gitignore'in**yanındaki **Edit** bağlantısını seçebilirsiniz .)

İkinci olarak, bir komut penceresi açın, *env*gibi sanal ortam klasörü içeren `git rm -r env` *BasicProject* gibi klasöre gidin ve çalıştırın . Ardından bu değişiklikleri komut satırından (`git commit -m 'Remove venv'`) veya **Team Explorer'ın** **Değişiklikler** sayfasından gerçekleştirin.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Adım 1-4: Ortak plaka kodunu inceleyin

Proje oluşturma tamamlandıktan sonra, ortak Django proje kodunu inceleyin (yine CLI `django-admin startproject <project_name>`komutu tarafından oluşturulan aynıdır).

1. Proje kökünüzde *manage.py*, Visual Studio'nun proje başlangıç dosyası olarak otomatik olarak ayarladığının Django komut satırı yönetim yardımcı programıdır. Komut satırındaki yardımcı programı `python manage.py <command> [options]`. Sık kullanılan Django görevleri için Visual Studio kullanışlı menü komutları sağlar. **Solution Explorer'da** projeyi sağ tıklatın ve listeyi görmek için **Python'u** seçin. Bu öğretici süresince bu komutlardan bazılarıyla karşılaşırsınız.

    ![Python proje bağlam menüsünde Django komutları](media/django/step01-django-commands-menu.png)

2. Projenizde projeyle aynı adlı bir klasör bulunur. Bu temel Django proje dosyaları içerir:

   - *__init.py*: Python'a bu klasörün bir Python paketi olduğunu söyleyen boş bir dosya.
   - *wsgi.py*: WSGI uyumlu web sunucuları için projenize hizmet vermek için bir giriş noktası. Üretim web sunucuları için kancasağlar genellikle olarak bu dosyayı bırakın.
   - *settings.py*: bir web uygulaması geliştirme süresince değiştirdiğiniz Django projesi için ayarlar içerir.
   - *urls.py*: Django projesi için de geliştirme aşamasında değiştirdiğiniz bir içerik tablosu içerir.

     ![Solution Explorer'daki Django proje dosyaları](media/django/step01-django-project-in-solution-explorer.png)

3. Daha önce de belirtildiği gibi, Visual Studio şablonu da Django paket bağımlılığı nı belirten projenize bir *requirements.txt* dosyası ekler. Bu dosyanın varlığı, projeyi ilk oluştururken sizi sanal bir ortam oluşturmaya davet eden şeydir.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Soru: Visual Studio diğer paketleri yükledikten sonra sanal ortamdan bir requirements.txt dosyası oluşturabilir mi?

Cevap: Evet. Python **Ortamları** düğümünü genişletin, sanal ortamınıza sağ tıklayın ve **requirements.txt oluştur** komutunu seçin. Ortamı değiştirirken bu komutu düzenli aralıklarla kullanmak ve *gereksinimler.txt'de* bu ortama bağlı diğer kod değişiklikleriyle birlikte kaynak denetimine değişiklikler yapmak iyidir. Bir yapı sunucusunda sürekli tümleştirme ayarlarsanız, dosyayı oluşturmalı ve ortamı her değiştirdiğinizde değişiklikler gerçekleştirmeniz gerekir.

## <a name="step-1-5-run-the-empty-django-project"></a>Adım 1-5: Boş Django projesini çalıştırın

1. Visual Studio'da **Hata** > **Ayıklama Başlatma Hata Ayıklama** **(F5)** seçeneğini belirleyin veya araç çubuğundaki **Web Sunucusu** düğmesini kullanın (gördüğünüz tarayıcı değişebilir):

    ![Visual Studio'da web sunucusu araç çubuğu düğmesini çalıştırın](media/django/run-web-server-toolbar-button.png)

1. Sunucuyu çalıştırmak, Django'nun yerleşik geliştirme sunucusunu başlatan komutu `manage.py runserver <port>`çalıştırmak anlamına gelir. Visual Studio, başlangıç dosyası olmamasıyla ilgili bir iletiyle **hata ayıklamaya başlayamadığını söylüyorsa,** **Solution Explorer'da** **manage.py** sağ tıklatın ve Başlangıç Dosyası **olarak ayarla'yı**seçin.

1. Sunucuyu başlattığınızda, sunucu günlüğünü de görüntüleyen bir konsol penceresinin açık olduğunu görürsünüz. Visual Studio otomatik olarak `http://localhost:<port>`bir tarayıcı yı açar. Ancak Django projesinde uygulama bulunmadığından, Django şimdiye kadar sahip olduğunuz şeyin iyi çalıştığını kabul etmek için yalnızca varsayılan bir sayfa gösterir:

    ![Django proje varsayılan görünümü](media/django/step01-first-run-success.png)

1. İşlem bittiğinde, konsol penceresini kapatarak veya Visual Studio'daki **Hata** > **Ayıklama Hata Ayıklama** Komutunu kullanarak sunucuyu durdurun.

### <a name="question-is-django-a-web-server-as-well-as-a-framework"></a>Soru: Django bir web sunucusu yanı sıra bir çerçeve mi?

Cevap: Evet ve hayır. Django geliştirme amaçlı kullanılan yerleşik bir web sunucusu var. Bu web sunucusu, Visual Studio'da hata ayıklama gibi web uygulamasını yerel olarak çalıştırdığınızda kullanılan sunucudur. Ancak, bir web barındırma sitesine dağıtığınızda, Django bunun yerine ana bilgisayarWeb sunucusunu kullanır. Django projesindeki *wsgi.py* modülü, üretim sunucularına bağlanmayı hallediyor.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Soru: Hata Ayıklama menüsü komutlarını kullanmakla projenin Python alt menüsündeki sunucu komutlarını kullanmak arasındaki fark nedir?

Cevap: **Hata Ayıklama** menü komutları ve araç çubuğu düğmelerine ek olarak, projenin bağlam menüsündeki **Python** > **Run sunucusu** veya **Python** > **Run hata ayıklama sunucu** komutlarını kullanarak sunucuyu başlatabilirsiniz. Her iki komut da çalışan sunucunun yerel URL'sini (localhost:port) gördüğünüz bir konsol penceresi açar. Ancak, bu URL'ye sahip bir tarayıcıyı el ile açmanız gerekir ve hata ayıklama sunucusunu çalıştırmak Visual Studio hata ayıklamasını otomatik olarak başlatmaz. **Hata** Ayıklama Komutunu kullanarak, isterseniz, daha sonra çalışan işleme **hata** > ayıklama ekleyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu noktada, temel Django projesi herhangi bir uygulama içermez. Bir sonraki adımda bir uygulama oluşturursunuz. Genellikle Django uygulamalarıyla Django projesinden daha fazla çalıştığınız için, şu anda ortak dosyalar hakkında daha fazla bilgi sahibi olmanız gerekmez.

> [!div class="nextstepaction"]
> [Görünümler ve sayfa şablonları içeren bir Django uygulaması oluşturma](learn-django-in-visual-studio-step-02-create-an-app.md)

## <a name="go-deeper"></a>Daha derine inin

- Django proje kodu: [İlk Django uygulaması, bölüm 1](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) (docs.djangoproject.com) yazma
- İdari yardımcı program: [django-admin ve manage.py](https://docs.djangoproject.com/en/2.0/ref/django-admin/) (docs.djangoproject.com)
- GitHub'da Öğretici kaynak kodu: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
