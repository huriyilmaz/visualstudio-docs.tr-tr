---
title: Visual Studio, 1. adım, docgo 'da docgo öğreticisini öğrenin
titleSuffix: ''
description: Visual Studio projeler bağlamında, destek Visual Studio docgo geliştirme için sağladığı desteği gösteren docgo hakkında bir yönergeler
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bd3bb5bd5b9ac4864c9eb38f290d34d7cdd7fc1f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156623"
---
# <a name="tutorial-get-started-with-the-django-web-framework-in-visual-studio"></a>Öğretici: Visual Studio 'da Docgo Web çerçevesini kullanmaya başlama

[Docgo](https://www.djangoproject.com/) , hızlı, güvenli ve ölçeklenebilir Web geliştirme için tasarlanan üst düzey bir Python çerçevesidir. bu öğretici, dmı go tabanlı web uygulamalarının oluşturulmasını kolaylaştırmak için Visual Studio sağladığı proje şablonları bağlamında docgo çerçevesini araştırır.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

::: moniker range="vs-2017"
- "Blank docgo Web Project" şablonunu kullanarak Git deposunda temel bir docgo projesi oluşturma (1. adım)
- Tek sayfalı bir Docgo uygulaması oluşturun ve bu sayfayı şablon kullanarak oluşturun (2. adım)
- Statik dosyaları sunma, sayfa ekleme ve şablon devralmayı kullanma (3. adım)
- birden çok sayfa ve yanıt veren tasarıma sahip bir uygulama oluşturmak için docgo Web Project şablonunu kullanın (4. adım)
- Kullanıcıların kimliğini doğrulama (5. adım)
- yönetim arabirimine modeller, veritabanı geçişleri ve özelleştirmeler kullanan bir uygulama oluşturmak için docgo Web Project şablonunu yoklayan (6. adım) kullanın
::: moniker-end

::: moniker range=">=vs-2019"
- "Blank docgo Web Project" şablonunu kullanarak Git deposunda temel bir docgo projesi oluşturma (1. adım)
- Tek sayfalı bir Docgo uygulaması oluşturun ve bu sayfayı şablon kullanarak oluşturun (2. adım)
- Statik dosyaları sunma, sayfa ekleme ve şablon devralmayı kullanma (3. adım)
- birden çok sayfa ve yanıt veren tasarıma sahip bir uygulama oluşturmak için docgo Web Project şablonunu kullanın (4. adım)
- Kullanıcıların kimliğini doğrulama (5. adım)
::: moniker-end

## <a name="prerequisites"></a>Önkoşullar

- aşağıdaki seçeneklerle Windows Visual Studio 2017 veya üzeri:
  - **Python geliştirme** iş yükü (yükleyicideki **iş yükü** sekmesi). Yönergeler için bkz. [Visual Studio Python desteğini Yüklemeyi](installing-python-support-in-visual-studio.md).
  - **kod araçları** altındaki **tek bileşenler** sekmesinde Visual Studio Windows ve **GitHub uzantısı** için **Git** .

docgo proje şablonları, önceki Visual Studio için Python Araçları tüm sürümlerine de dahildir, ancak ayrıntılar bu öğreticide açıklanana kadar farklılık gösterebilir (özellikle docgo çerçevesinin önceki sürümleriyle farklıdır).

Python geliştirme Mac için Visual Studio şu anda desteklenmiyor. Mac ve Linux 'ta [Visual Studio Code ' de Python uzantısını](https://code.visualstudio.com/docs/python/python-tutorial)kullanın.

### <a name="visual-studio-projects-and-django-projects"></a>"Visual Studio projeleri" ve "docgo projeleri"

Docgo terimlerinde, bir "Docgo Projesi", bir veya daha fazla site düzeyi yapılandırma dosyasından, bir Web ana bilgisayarına dağıttığınız bir veya daha fazla "uygulama" ile birlikte tam bir Web uygulaması oluşturmak üzere oluşur. Bir Docgo projesi birden çok uygulama içerebilir ve aynı uygulama birden çok Docgo projesinde olabilir.

bölümü için bir Visual Studio projesi, birden çok uygulama ile birlikte docgo projesi içerebilir. kolaylık sağlaması için, bu öğretici yalnızca bir "proje" başvurduğu zaman, Visual Studio projesine başvurıyorlar. Web uygulamasının "Docgo Projesi" bölümüne başvurduğunda, özel olarak "Docgo Projesi" kullanır.

bu öğreticide, her biri tek bir docgo uygulaması içeren üç ayrı docgo projesi içeren tek bir Visual Studio çözümü oluşturacaksınız. Projeleri aynı çözümde tutarak, karşılaştırma için farklı dosyalar arasında kolayca geri ve ileri geçiş yapabilirsiniz.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>adım 1-1: Visual Studio bir proje ve çözüm oluşturma

Komut satırından Docgo ile çalışırken, genellikle komutunu çalıştırarak bir proje başlatabilirsiniz `django-admin startproject <project_name>` . Visual Studio, "boş docgo Web Project" şablonunu kullanmak, bir Visual Studio projesi ve çözümü içinde aynı yapıyı sağlar.

1. Visual Studio ' de **dosya**  >  **yeni**  >  **Project**' i seçin, "docgo" araması yapın ve **boş docgo Web Project** şablonunu seçin. (Şablon **Python**  >  altında da bulunur **Web** , sol taraftaki listede.)

    ![boş docgo Web için Visual Studio yeni proje iletişim kutusu Project](media/django/step01-new-blank-project.png)

1. İletişim kutusunun altındaki alanlarda aşağıdaki bilgileri girin (önceki grafikte gösterildiği gibi) ve ardından **Tamam**' ı seçin:

    - **ad**: Visual Studio projesinin adını **basicproject** olarak ayarlayın. Bu ad, Docgo projesi için de kullanılır.
    - **konum**: Visual Studio çözümünün ve projenin oluşturulacağı bir konum belirtin.
    - **Çözüm**: Bu denetimi varsayılan **yeni çözüm oluştur** seçeneğine ayarlı bırakın.
    - **Çözüm adı**: Bu öğreticide birden çok projenin kapsayıcısı olarak çözüm olarak uygun olan **Learningdocgo** olarak ayarlanır.
    - **Çözüm için dizin oluştur**: kümeyi bırak (varsayılan).
    - **yeni git deposu oluştur**: bu seçeneği, Visual Studio çözümü oluşturduğunda yerel bir Git deposu oluşturması için (varsayılan olarak temiz) seçin. bu seçeneği görmüyorsanız, Visual Studio yükleyiciyi çalıştırın ve **kod araçları** altındaki **tek bileşenler** sekmesinde Visual Studio için **Git Windows** ve **GitHub uzantısı** ekleyin.

1. bir süre sonra, Visual Studio **bu projenin dış paketler gerektirdiğini** belirten bir iletişim kutusu ister (aşağıda gösterilmiştir). Bu iletişim kutusu, şablon en son Docgo 1. x paketine başvuran bir *requirements.txt* dosyası içerdiğinden görüntülenir. (Tam bağımlılıkları görmek için **gerekli paketleri göster** ' i seçin.)

    ![Projenin dış paketler gerektirdiğini söyleyen bir istem](media/django/step01-requirements-prompt-install-myself.png)

1. **Kendim yükleyeceğim** seçeneğini belirleyin. Kaynak denetiminden dışlandığından emin olmak için sanal ortamı kısa süre içinde oluşturursunuz. (Ortam her zaman *requirements.txt* oluşturulabilir.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Adım 1-2: git denetimlerini Inceleme ve uzak depoda yayımlama

yeni **Project** iletişim kutusunda **yeni Git deposu oluştur** ' u seçtiğinizden, proje, oluşturma işlemi tamamlandıktan hemen sonra yerel kaynak denetimine zaten kaydedilmiş olur. bu adımda, Visual Studio Git denetimleri ve kaynak denetimi ile birlikte çalıştığınız **Takım Gezgini** pencere hakkında bilgi edinin.

1. Visual Studio ana penceresinin alt köşesindeki Git denetimlerini inceleyin. Soldan sağa, bu denetimler gönderilmeyen işlemeler, kaydedilmemiş değişiklikler, deponun adı ve geçerli dalı gösterir:

    ![Visual Studio penceresindeki Git denetimleri](media/django/step01-git-controls.png)

    > [!Note]
    > yeni **Project** iletişim kutusunda **yeni git deposu oluştur** ' u seçmezseniz, git denetimleri yalnızca yerel bir depo oluşturan **kaynak denetimine ekle** komutunu gösterir.
    >
    > ![bir depo oluşturmadıysanız Visual Studio kaynak denetimine ekle görüntülenir](media/django/step01-git-add-to-source-control.png)

1. değişiklikler düğmesini seçin ve Visual Studio **değişiklikler** sayfasında **Takım Gezgini** penceresini açar. Yeni oluşturulan proje kaynak denetimine otomatik olarak zaten yapıldığından, bekleyen bir değişiklik görmezsiniz.

    ![Değişiklikler sayfasında Takım Gezgini penceresi](media/django/step01-team-explorer-changes.png)

1. Visual Studio durum çubuğunda, **Takım Gezgini**' de **eşitleme** sayfasını açmak için gönderişsiz işlemeler düğmesini ( **2** ile yukarı ok) seçin. Yalnızca yerel bir depo olduğundan, Bu sayfa depoyu farklı uzak depolara yayımlamak için kolay seçenekler sağlar.

    ![Kaynak denetimi için kullanılabilir git deposu seçeneklerini gösteren Takım Gezgini pencere](media/django/step01-team-explorer.png)

    Kendi projeleriniz için istediğiniz hizmeti seçebilirsiniz. bu öğreticide, öğreticinin tamamlanan örnek kodunun [Microsoft/python-sample-vs-learning-docgo](https://github.com/Microsoft/python-sample-vs-learning-django) deposunda gerçekleştiği GitHub kullanımı gösterilmektedir.

1. **Yayınlama** denetimlerinden herhangi birini seçerken **Takım Gezgini** daha fazla bilgi ister. Örneğin, bu öğretici için örnek yayımlarken, deponun kendisi oluşturulmalıdır, bu durumda depo URL 'SI ile **uzak depoya gönderim** seçeneği kullanılır.

    ![Var olan bir uzak depoya göndermek için Takım Gezgini pencere](media/django/step01-push-to-github.png)

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

Projeniz için kaynak denetimini yapılandırdığınıza göre, proje için gerekli Docgo paketlerini içeren sanal ortamı oluşturabilirsiniz. Ardından, ortam klasörünü kaynak denetiminden dışlamak için **Takım Gezgini** kullanabilirsiniz.

1. **Çözüm Gezgini**, **Python ortamları** düğümüne sağ tıklayın ve **sanal ortam ekle**' yi seçin.

    ![Çözüm Gezgini sanal ortam komutu Ekle](media/django/step01-add-virtual-environment-command.png)

1. Bir **requirements.txt dosyası bulduğumuz** belirten bir Ileti Ile **sanal ortam ekle** iletişim kutusu görüntülenir. bu ileti, Visual Studio sanal ortamı yapılandırmak için bu dosyayı kullanacağını gösterir.

    ![requirements.txt iletisiyle sanal ortam iletişim kutusu Ekle](media/django/step01-add-virtual-environment-found-requirements.png)

1. Varsayılanları kabul etmek için **Oluştur** ' u seçin. (İsterseniz sanal ortamın adını değiştirebilirsiniz, bu, yalnızca alt klasörünün adını değiştirir ancak `env` Standart bir kuraldır.)

1. istenirse, yönetici ayrıcalıklarına onay vermeniz gerekirse birkaç Visual Studio dakika bekleyin. bu, docgo için birkaç bin dosyanın çok sayıda alt klasörde genişletilmesi anlamına gelir. İlerlemeyi Çıkış penceresinde Visual Studio **görebilirsiniz.** Beklerken, aşağıdaki Soru bölümlerine daha fazla bakın.

1. Git Visual Studio (durum çubuğunda), değişiklikler sayfasını Takım Gezgini'da açan değişiklik göstergesini **(99**&#42;)  **seçin.**

    Sanal ortamı oluşturmak binlerce değişiklik getirse de, siz (veya projeyi başka herhangi biri) ortamı her zamanrequirements.txt'den yeniden ** oluşturasınız.

    Sanal ortamı dışlamak için **env** klasörüne sağ tıklayın ve Bu yerel öğeleri **yoksay'ı seçin.**

    ![Kaynak denetiminde sanal ortamı yoksayma değişiklikleri](media/django/step01-ignore-local-items.png)

1. Sanal ortamı dışlamanın ardından, kalan tek değişiklik proje dosyasında ve *.gitignore dosyasındadır.* *.gitignore dosyası,* sanal ortam klasörü için ek bir girdi içerir. Bir fark görmek için dosyaya çift tıkabilirsiniz.

1. Bir işleme iletisi girin ve Hepsini İşle **düğmesini** seçin, ardından işlemeleri uzak depoya gönderin.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Soru: Neden sanal ortam oluşturmak istiyorum?

Cevap: Sanal ortam, uygulama bağımlılıklarınızı tam olarak yalıtmak için harika bir yol sağlar. Bu tür bir yalıtım, genel bir Python ortamındaki çakışmaları önler ve hem test hem de işbirliğine yardımcı olur. Zaman içinde, bir uygulama geliştirirken, sürekli olarak birçok yararlı Python paketi getirirsiniz. Paketleri projeye özgü bir sanal ortamda tutarak, projenin kaynak denetimine *dahil edilen ortamırequirements.txt* dosyasını kolayca güncelleştirebilirsiniz. Proje derleme sunucuları, dağıtım sunucuları ve diğer geliştirme bilgisayarları da dahil olmak üzere başka bir bilgisayarlara kopyalanırsa, yalnızca *requirements.txt* kullanarak ortamı kolayca yeniden oluşturabilirsiniz (bu nedenle ortamın kaynak denetiminde olması gerek değildir). Daha fazla bilgi için [bkz. Sanal ortamları kullanma.](selecting-a-python-environment-for-a-project.md#use-virtual-environments)

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Soru: Nasıl yaparım? denetimine zaten bağlı olan bir sanal ortamı kaldırmak mı gerekiyor?

Cevap: İlk *olarak, .gitignore* dosyanızı düzenleyemez ve klasörü dışlamak için en sonundaki bölümünü açıklamayla bulun ve gibi sanal ortam klasörü için yeni bir `# Python Tools for Visual Studio (PTVS)` satır `/BasicProject/env` ekleyin. (Visual Studio dosya dosyada **Çözüm Gezgini,** dosyayı doğrudan Dosya kullanarak **açın**  >  **Aç**  >  **Dosya** menüsü komutu. Dosyayı Takım Gezgini sayfasından da açabilirsiniz: **Ayarlar** sayfasında Depo **Ayarlar'ı** seçin, **&** Öznitelik Dosyalarını Yoksay bölümüne gidin ve **.gitignore öğesinin** yanındaki Düzenle bağlantısını seçin.  

İkinci olarak, bir komut penceresi açın, *basicProject* gibi env gibi sanal ortam klasörünü içeren *klasöre* gidin ve komutunu `git rm -r env` çalıştırın. Ardından, bu değişiklikleri komut satırı ( ) veya Takım Gezgini'nin `git commit -m 'Remove venv'` **Değişiklikler sayfasından işleyebilirsiniz.** 

## <a name="step-1-4-examine-the-boilerplate-code"></a>1-4. Adım: Ortak kodu inceleme

Proje oluşturma işlemi tamamlandıktan sonra, ortak Django proje kodunu (CLI komutu tarafından oluşturulanla aynı şekilde) `django-admin startproject <project_name>` incelersiniz.

1. Proje kök dosyanız *manage.py,* proje başlangıç dosyası olarak otomatik olarak Visual Studio Django komut satırı yönetim yardımcı programıdır. yardımcı programını kullanarak komut satırı üzerinde `python manage.py <command> [options]` çalıştırabilirsiniz. Yaygın Django görevleri için Visual Studio menü komutları sağlar. Aşağıdaki listede projeye sağ **Çözüm Gezgini** **Python'ı** seçerek listeyi göreceksiniz. Bu öğretici sırasında bu komutlardan bazılarla karşılaşırsınız.

    ![Python projesi bağlam menüsündeki Django komutları](media/django/step01-django-commands-menu.png)

2. Projeniz, projeyle aynı adlı bir klasördür. Temel Django proje dosyalarını içerir:

   - *__init.py:* Python'a bu klasörün bir Python paketi olduğunu söyleyen boş bir dosya.
   - *wsgi.py:* WSGI uyumlu web sunucularının projenize hizmet vermek için giriş noktası. Üretim web sunucularına kanca sağladığı için bu dosyayı genellikle olduğu gibi bırakırsanız.
   - *settings.py:* Bir web uygulaması geliştirme kursunda değiştirerek Django projesinin ayarlarını içerir.
   - *urls.py:* Django projesi için geliştirme aşamasında da değiştirerek bir içindekiler tablosu içerir.

     ![Çözüm Gezgini'daki Django proje Çözüm Gezgini](media/django/step01-django-project-in-solution-explorer.png)

3. Daha önce belirtildiği gibi, Visual Studio şablonu projenize Django *paket bağımlılığını* belirten birrequirements.txtdosyası da ekler. Bu dosyanın varlığı, projeyi ilk kez oluştururken sizi sanal ortam oluşturmaya davet eder.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Soru: Visual Studio paketleri yükledikten requirements.txt bir sanal ortamdan bir dosya oluşturamıyor musunuz?

Yanıt: Evet. Python Ortamları **düğümünü** genişletin, sanal ortamınıza sağ tıklayın ve Oluştur komutunu **requirements.txt** seçin. Ortamı değiştirirken bu komutu düzenli aralıklarla kullanmak ve değişiklikleri  kaynak denetiminerequirements.txtortamdaki diğer kod değişiklikleriyle birlikte işlemek iyi bir fikirdir. Derleme sunucusunda sürekli tümleştirmeyi ayar ediyorsanız, ortamı her değiştirerek dosyayı oluşturmalı ve değişiklikleri işlemelisiniz.

## <a name="step-1-5-run-the-empty-django-project"></a>1-5. Adım: Boş Django projesini çalıştırma

1. Bu Visual Studio **Hata** AyıklamaYı Başlat ( F5 ) öğesini seçin veya araç çubuğundaki Web Sunucusu düğmesini kullanın  >   (gördüğünüz tarayıcı farklılık gösterebilir): 

    ![Web sunucusu araç çubuğu düğmesini Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Sunucuyu çalıştırma, `manage.py runserver <port>` Django'nun yerleşik geliştirme sunucusunu başlatan komutunu çalıştırma anlamına gelir. Bir Visual Studio **dosyası** olmadığını iletiyle hata ayıklayıcı başlatılamadı iletisiyle belirtiyorsa, manage.py'ye sağ tıklayın Çözüm Gezgini Başlangıç Dosyası **Olarak** **Ayarla'yı seçin.** 

1. Sunucuyu başlatınca, sunucu günlüğünü de görüntüleyen bir konsol penceresi açılır. Visual Studio tarayıcıyı otomatik olarak `http://localhost:<port>` açar. Ancak Django projesinin hiç uygulaması yoktur, ancak Django şu ana kadarkilerin iyi çalıştığını kabul etmek için yalnızca varsayılan bir sayfa gösterir:

    ![Django projesi varsayılan görünümü](media/django/step01-first-run-success.png)

1. Bitirerek konsol penceresini kapatarak veya hata ayıklamada hata ayıklamayı durdur komutunu kullanarak sunucuyu  >   Visual Studio.

### <a name="question-is-django-a-web-server-as-well-as-a-framework"></a>Soru: Django hem web sunucusu hem de çerçeve mi?

Cevap: Evet ve hayır. Django'nun geliştirme amacıyla kullanılan yerleşik bir web sunucusu vardır. Bu web sunucusu, web uygulamasını yerel olarak çalıştırarak hata ayıklama gibi durumlarda Visual Studio. Ancak Django, bir web ana bilgisayar için dağıtım yapmak yerine ana bilgisayarının web sunucusunu kullanır. Django *wsgi.py* modülünün üretim sunucularına bağlanarak ilgilenmesi gerekir.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Soru: Projenin Python alt menüsünde Hata Ayıklama menü komutlarını ve sunucu komutlarını kullanma arasındaki fark nedir?

Cevap: Hata ayıklama  menü komutları ve araç çubuğu düğmelerine ek olarak, projenin bağlam **menüsündeki Python** Çalıştırma sunucusu veya Python Çalıştırma hata ayıklama sunucusu komutlarını kullanarak da  >     >   sunucuyu başlatabilirsiniz. Her iki komut da çalışan sunucunun yerel URL'sini (localhost:port) gördüğünüz bir konsol penceresi açar. Ancak, bu URL'ye sahip bir tarayıcıyı el ile açmalısınız ve hata ayıklama sunucusunun çalıştırılırken hata ayıklayıcısı otomatik Visual Studio başlamaz. Hata Ayıkla İşleme Ekle komutunu kullanarak daha sonra, daha sonra, çalışan işleme **bir hata**  >  **ayıklayıcı** iliştirebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu noktada, temel Django projesi hiçbir uygulama içermez. Bir sonraki adımda bir uygulama oluşturabilirsiniz. Django uygulamalarıyla genellikle Django projesinde olduğundan, şu anda ortak dosyalar hakkında çok daha fazla bilginiz olmayacaktır.

> [!div class="nextstepaction"]
> [Görünümler ve sayfa şablonlarıyla Django uygulaması oluşturma](learn-django-in-visual-studio-step-02-create-an-app.md)

## <a name="go-deeper"></a>Daha derine gitme

- Django proje kodu: [İlk Django uygulamanızı yazma, bölüm 1](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) (docs.djangoproject.com)
- Yönetim yardımcı programı: [django-admin ve manage.py](https://docs.djangoproject.com/en/2.0/ref/django-admin/) (docs.djangoproject.com)
- GitHub öğreticisi: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)