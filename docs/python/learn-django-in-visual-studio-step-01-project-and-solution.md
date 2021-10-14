---
title: Visual Studio, 1. adım, docgo 'da docgo öğreticisini öğrenin
titleSuffix: ''
description: Visual Studio projeler bağlamında, destek Visual Studio docgo geliştirme için sağladığı desteği gösteren docgo hakkında bir yönergeler
ms.date: 11/19/2018
ms.topic: tutorial
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 2900e9bd4228d6cc45bdaec05db33d4dbbd0e4ab
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972277"
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

1. istenirse, yönetici ayrıcalıklarına onay vermeniz gerekirse birkaç Visual Studio dakika bekleyin. bu, docgo için birkaç bin dosyanın çok sayıda alt klasörde genişletilmesi anlamına gelir. ilerlemeyi Visual Studio **çıkış** penceresinde görebilirsiniz. Beklerken, aşağıdaki soru bölümlerini izleyin.

1. Git denetimlerinde Visual Studio (durum çubuğunda), **Takım Gezgini** **değişiklikler** sayfasını açan değişiklikler göstergesini ( **99&#42;**) seçin.

    Sanal ortam, binlerce değişikliğe göre oluşturulur, ancak siz (ya da projeyi Klonladığınız herkes) her zaman ortamı *requirements.txt* yeniden oluşturabileceğinden kaynak denetimine bunlardan herhangi birini eklemeniz gerekmez.

    Sanal ortamı dışlamak için **env** klasörüne sağ tıklayın ve **Bu yerel öğeleri yoksay**' ı seçin.

    ![Kaynak denetimi değişikliklerinde sanal ortam yok sayılıyor](media/django/step01-ignore-local-items.png)

1. Sanal ortamı dışladıktan sonra, kalan değişiklikler proje dosyası ve *. gitignore*' dir. *. Gitignore* dosyası, sanal ortam klasörü için eklenen bir giriş içerir. Bir farkı görmek için dosyaya çift tıklayabilirsiniz.

1. Bir işleme iletisi girin ve **Tümünü Kaydet** düğmesini seçin, ardından istediğiniz değişiklikleri uzak deponuza gönderin.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Soru: neden sanal ortam oluşturmak istiyorum?

Cevap: sanal bir ortam, uygulamanızın tam bağımlılıklarını yalıtmak için harika bir yoldur. Bu tür yalıtımlara genel bir Python ortamında çakışmalar önlenir ve hem test hem de işbirliği yardımcı olur. Zaman içinde, bir uygulama geliştirirken, çok sayıda faydalı Python paketini de bir araya getirebilirsiniz. Paketleri projeye özgü bir sanal ortamda tutarak, projenin kaynak denetimine dahil olan bu ortamı açıklayan *requirements.txt* dosyasını kolayca güncelleştirebilirsiniz. Proje, derleme sunucuları, dağıtım sunucuları ve diğer geliştirme bilgisayarları dahil olmak üzere başka bir bilgisayara kopyalandığında, ortamı yalnızca *requirements.txt* (ortamın kaynak denetiminde olması gerekmez) kullanarak yeniden oluşturmak kolaydır. Daha fazla bilgi için bkz. [sanal ortamları kullanma](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Soru: kaynak denetimine zaten kaydedilmiş bir sanal ortamı kaldırmak Nasıl yaparım? mı?

Cevap: Ilk olarak, klasörü hariç tutmak için *. gitignore* dosyanızı düzenleyin: ile birlikte, açıklama ile sonundaki bölümü bulun `# Python Tools for Visual Studio (PTVS)` ve sanal ortam klasörü için gibi yeni bir satır ekleyin `/BasicProject/env` . (Visual Studio dosyayı **Çözüm Gezgini** göstermediğinden, **dosyayı**  >  doğrudan kullanarak açın **Açık**  >  **Dosya** menü komutu. dosyayı **Takım Gezgini** içinden de açabilirsiniz: **Ayarlar** sayfasında **depo Ayarlar**' yı seçin, **& öznitelikleri dosyalarını yoksay** bölümüne gidin ve sonra **. gitignore**' in yanındaki **düzenle** bağlantısını seçin.

İkinci olarak, bir komut penceresi açın, *env* ve çalıştırmak gibi sanal ortam klasörünü Içeren *BasicProject* gibi bir klasöre gidin `git rm -r env` . Sonra bu değişiklikleri komut satırından ( `git commit -m 'Remove venv'` ) işleyin veya **Takım Gezgini** **değişiklikler** sayfasından işleyin.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Adım 1-4: ortak kodu Inceleme

Proje oluşturma işlemi tamamlandıktan sonra, ortak Docgo proje kodunu inceleyin (CLı komutu tarafından oluşturulan ile aynı `django-admin startproject <project_name>` ).

1. proje kökünde *manage.py*, Visual Studio otomatik olarak proje başlangıç dosyası olarak ayarlayan docgo komut satırı yönetim yardımcı programıdır. Yardımcı programını kullanarak komut satırından çalıştırırsınız `python manage.py <command> [options]` . ortak docgo görevleri için Visual Studio kullanışlı menü komutları sağlar. **Çözüm Gezgini** içinde projeye sağ tıklayın ve listeyi görmek için **Python** ' ı seçin. Bu öğreticinin kursunda bu komutlardan bazılarını karşılaşıyorsunuz.

    ![Python projesi bağlam menüsünde docgo komutları](media/django/step01-django-commands-menu.png)

2. Projenizde proje ile aynı adlı bir klasör. Temel Docgo proje dosyalarını içerir:

   - *__init. Kopyala*: Python 'a bu klasörün bir Python paketi olduğunu belirten boş bir dosya.
   - *wsgi.py*: wsgi uyumlu Web sunucularının projenize sunması için bir giriş noktası. Bu dosyayı genellikle üretim Web sunucuları için kancalar sağladığından olduğu gibi bırakın.
   - *Settings.py*: Docgo projesi için bir Web uygulaması geliştirme sürecinde değişiklik yaptığınız ayarları içerir.
   - *URLs.py*: Docgo projesi için bir içindekiler tablosu içerir ve bu, geliştirme sürecinde de değişiklik yapabilirsiniz.

     ![Çözüm Gezgini içindeki docgo proje dosyaları](media/django/step01-django-project-in-solution-explorer.png)

3. daha önce belirtildiği gibi, Visual Studio şablonu projenize docgo paket bağımlılığını belirten bir *requirements.txt* dosyası da ekler. Bu dosyanın varlığı, projeyi ilk oluştururken sanal ortam oluşturmak için sizi davet eder.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>soru: diğer paketleri yükledikten sonra sanal ortamdan bir requirements.txt dosyası Visual Studio verebilir misiniz?

Yanıt: Evet. **Python ortamları** düğümünü genişletin, sanal ortamınıza sağ tıklayıp **requirements.txtoluştur** komutunu seçin. Ortamı değiştirirken bu komutun düzenli aralıklarla kullanılması ve bu ortama bağlı diğer kod değişiklikleriyle birlikte kaynak denetimine *requirements.txt* değişiklikler yürütmesi yararlı olur. Bir yapı sunucusunda sürekli tümleştirme ayarlarsanız, ortamı her değiştirdiğinizde dosyayı oluşturmanız ve değişiklikleri uygulamanız gerekir.

## <a name="step-1-5-run-the-empty-django-project"></a>Adım 1-5: boş Docgo projesini çalıştırma

1. Visual Studio **, hata**  >  **ayıklamayı başlat** (**F5**) seçeneğini belirleyin veya araç çubuğunda **Web sunucusu** düğmesini kullanın (gördüğünüz tarayıcı farklılık gösterebilir):

    ![Visual Studio Web sunucusu araç çubuğu düğmesini Çalıştır](media/django/run-web-server-toolbar-button.png)

1. Sunucuyu çalıştırmak `manage.py runserver <port>` , Docgo 'nun yerleşik geliştirme sunucusunu Başlatan komutunu çalıştırmanın anlamına gelir. Visual Studio **hata ayıklayıcıyı** başlatma dosyası olmayan bir iletiyle başlatmazsa, **Çözüm Gezgini** **' a sağ tıklayıp** **başlangıç dosyası olarak ayarla**' yı seçin.

1. Sunucuyu başlattığınızda, sunucu günlüğünü de görüntüleyen bir konsol penceresi açık görürsünüz. Visual Studio otomatik olarak bir tarayıcı açar `http://localhost:<port>` . Docgo projesinde hiç uygulama olmadığından, en fazla ne kadar iyi çalıştığını bildirmek için Docgo yalnızca bir varsayılan sayfa gösterir:

    ![Docgo proje varsayılan görünümü](media/django/step01-first-run-success.png)

1. işiniz bittiğinde, konsol penceresini kapatarak veya Visual Studio **hata**  >  **ayıklamayı durdur** komutunu kullanarak sunucuyu durdurun.

### <a name="question-is-django-a-web-server-as-well-as-a-framework"></a>Soru: bir Web sunucusunun yanı sıra bir çerçeve mi?

Cevap: Evet ve hayır. Docgo 'ın geliştirme amacıyla kullanılan yerleşik bir Web sunucusu vardır. Bu Web sunucusu, Web uygulamasını yerel olarak çalıştırdığınızda (Visual Studio hata ayıklaması yaparken) kullanılır. Ancak, bir Web ana bilgisayarına dağıtırken, Docgo bunun yerine konağın Web sunucusunu kullanır. Docgo projesindeki *wsgi.py* modülü, üretim sunucularına çağrı gerçekleştirir.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Soru: Hata Ayıkla menü komutlarının ve proje Python alt menüsünde sunucu komutlarının kullanımı arasındaki fark nedir?

Cevap: **hata ayıklama** menü komutları ve araç çubuğu düğmelerine ek olarak,   >  projenin bağlam menüsündeki Python **çalıştırma sunucusu** veya **Python**  >  **çalıştırma hata ayıklama sunucusu** komutlarını kullanarak sunucuyu da başlatabilirsiniz. Her iki komut de çalışan sunucu için yerel URL 'YI (localhost: bağlantı noktası) görebileceğiniz bir konsol penceresi açar. ancak, bu URL ile bir tarayıcıyı el ile açmanız gerekir ve hata ayıklama sunucusunu çalıştırmak Visual Studio hata ayıklayıcıyı otomatik olarak başlatmamalıdır. Çalıştırmak istiyorsanız,   >  **işlemek için** hata ayıkla komutunu kullanarak, çalışan işleme daha sonra bir hata ayıklayıcı ekleyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu noktada, temel Docgo projesi herhangi bir uygulama içermez. Bir sonraki adımda bir uygulama oluşturursunuz. Genellikle docgo projesiyle daha fazla docgo uygulamalarıyla çalıştığınız için, mevcut olan ortak dosyalar hakkında daha fazla bilgi sahibi olmanız gerekmez.

> [!div class="nextstepaction"]
> [Görünümler ve sayfa şablonlarıyla bir Docgo uygulaması oluşturma](learn-django-in-visual-studio-step-02-create-an-app.md)

## <a name="go-deeper"></a>Daha derin git

- Docgo proje kodu: [Ilk Docgo uygulamanızı yazma, Bölüm 1](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) (docs.djangoproject.com)
- Yönetim yardımcı programı: [docgo-admin ve Manage.py](https://docs.djangoproject.com/en/2.0/ref/django-admin/) (docs.djangoproject.com)
- GitHub eğitim kaynak kodu: [Microsoft/python-sample-vs-learning-docgo](https://github.com/Microsoft/python-sample-vs-learning-django)