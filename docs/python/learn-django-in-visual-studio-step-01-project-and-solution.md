---
title: Visual Studio 'da Docgo öğreticisini öğrenin, 1. adım, Docgo temelleri
titleSuffix: ''
description: Visual Studio projeleri bağlamında, Visual Studio 'nun Docgo geliştirmesi için sağladığı desteği gösteren bir Docgo hakkında yönergeler.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62962257"
---
# <a name="tutorial-get-started-with-the-django-web-framework-in-visual-studio"></a>Öğretici: Visual Studio 'da Docgo Web çerçevesini kullanmaya başlama

[Docgo](https://www.djangoproject.com/) , hızlı, güvenli ve ölçeklenebilir Web geliştirme için tasarlanan üst düzey bir Python çerçevesidir. Bu öğretici, docgo çerçevesini, Visual Studio 'nun Docgo tabanlı Web uygulamalarının oluşturulmasını kolaylaştırmak için sağladığı proje şablonları bağlamında ele almaktadır.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
> - Git deposunda "boş Docgo Web projesi" şablonunu kullanarak temel bir Docgo projesi oluşturma (1. adım)
> - Tek sayfalı bir Docgo uygulaması oluşturun ve bu sayfayı şablon kullanarak oluşturun (2. adım)
> - Statik dosyaları sunma, sayfa ekleme ve şablon devralmayı kullanma (3. adım)
> - Birden çok sayfa ve yanıt veren tasarıma sahip bir uygulama oluşturmak için Docgo Web projesi şablonunu kullanın (4. adım)
> - Kullanıcıların kimliğini doğrulama (5. adım)
> - Yönetim arabirimine modeller, veritabanı geçişleri ve özelleştirmeler kullanan bir uygulama oluşturmak için Docgo Web proje şablonunu yoklayan (6. adım) kullanın

## <a name="prerequisites"></a>Önkoşullar

- Aşağıdaki seçeneklerle Visual Studio 2017 veya üzeri Windows üzerinde:
  - **Python geliştirme** iş yükü (yükleyicideki**iş yükü** sekmesi). Yönergeler için bkz. [Visual Studio 'Da Python desteğini Yüklemeyi](installing-python-support-in-visual-studio.md).
  - **Visual Studio Için Windows ve GitHub Uzantısı** için **Git** , **kod araçları**altındaki **tek bileşenler** sekmesinde.

Docgo proje şablonları, önceki Visual Studio için Python Araçları tüm sürümlerine de dahildir, ancak Ayrıntılar Bu öğreticide açıklanana kadar farklılık gösterebilir (özellikle Docgo çerçevesinin önceki sürümleriyle farklıdır).

Python geliştirme Mac için Visual Studio şu anda desteklenmiyor. Mac ve Linux 'ta [Visual Studio Code ' de Python uzantısını](https://code.visualstudio.com/docs/python/python-tutorial)kullanın.

### <a name="visual-studio-projects-and-django-projects"></a>"Visual Studio projeleri" ve "Docgo projeleri"

Docgo terimlerinde, bir "Docgo Projesi", bir veya daha fazla site düzeyi yapılandırma dosyasından, bir Web ana bilgisayarına dağıttığınız bir veya daha fazla "uygulama" ile birlikte tam bir Web uygulaması oluşturmak üzere oluşur. Bir Docgo projesi birden çok uygulama içerebilir ve aynı uygulama birden çok Docgo projesinde olabilir.

Bir Visual Studio projesi, bölümü için birden çok uygulama ile birlikte Docgo projesi içerebilir. Kolaylık sağlaması için, bu öğretici yalnızca bir "proje" başvurduğu zaman Visual Studio projesine başvurur. Web uygulamasının "Docgo Projesi" bölümüne başvurduğunda, özel olarak "Docgo Projesi" kullanır.

Bu öğreticide, her biri tek bir Docgo uygulaması içeren üç ayrı Docgo projesi içeren tek bir Visual Studio çözümü oluşturacaksınız. Projeleri aynı çözümde tutarak, karşılaştırma için farklı dosyalar arasında kolayca geri ve ileri geçiş yapabilirsiniz.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Adım 1-1: Visual Studio projesi ve çözümü oluşturma

Komut satırından Docgo ile çalışırken, genellikle komutunu çalıştırarak bir proje başlatabilirsiniz `django-admin startproject <project_name>` . Visual Studio 'da, "boş Docgo Web projesi" şablonunu kullanarak bir Visual Studio projesi ve çözümü içinde aynı yapıyı sağlar.

1. Visual Studio 'da **Dosya**  >  **Yeni**  >  **Proje**' yi seçin, "docgo" araması yapın ve **boş docgo Web proje** şablonunu seçin. (Şablon **Python**  >  altında da bulunur **Web** , sol taraftaki listede.)

    ![Boş Docgo Web projesi için Visual Studio 'da yeni proje iletişim kutusu](media/django/step01-new-blank-project.png)

1. İletişim kutusunun altındaki alanlarda aşağıdaki bilgileri girin (önceki grafikte gösterildiği gibi) ve ardından **Tamam**' ı seçin:

    - **Ad**: Visual Studio projesinin adını **BasicProject**olarak ayarlayın. Bu ad, Docgo projesi için de kullanılır.
    - **Konum**: Visual Studio çözümünün ve projenin oluşturulacağı bir konum belirtin.
    - **Çözüm**: Bu denetimi varsayılan **yeni çözüm oluştur** seçeneğine ayarlı bırakın.
    - **Çözüm adı**: Bu öğreticide birden çok projenin kapsayıcısı olarak çözüm olarak uygun olan **Learningdocgo**olarak ayarlanır.
    - **Çözüm için dizin oluştur**: kümeyi bırak (varsayılan).
    - **Yeni git deposu oluştur**: Visual Studio 'nun çözümü oluşturduğunda yerel bir git deposu oluşturması için bu seçeneği (varsayılan olarak temiz) seçin. Bu seçeneği görmüyorsanız, Visual Studio yükleyicisi 'ni çalıştırın ve **kod araçları**' nın altındaki **tek bileşenler** sekmesinde Visual Studio için **Git ve Windows** için **GitHub uzantısını** ekleyin.

1. Bir süre sonra, Visual Studio **Bu projenin dış paketler gerektirdiğini** belirten bir iletişim kutusu ister (aşağıda gösterilmiştir). Bu iletişim kutusu, şablon en son Docgo 1. x paketine başvuran bir *requirements.txt* dosyası içerdiğinden görüntülenir. (Tam bağımlılıkları görmek için **gerekli paketleri göster** ' i seçin.)

    ![Projenin dış paketler gerektirdiğini söyleyen bir istem](media/django/step01-requirements-prompt-install-myself.png)

1. **Kendim yükleyeceğim**seçeneğini belirleyin. Kaynak denetiminden dışlandığından emin olmak için sanal ortamı kısa süre içinde oluşturursunuz. (Ortam her zaman *requirements.txt*oluşturulabilir.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Adım 1-2: git denetimlerini Inceleme ve uzak depoda yayımlama

Yeni **Proje** iletişim kutusunda **Yeni git deposu oluştur** ' u seçtiğinizden, proje, oluşturma işlemi tamamlandıktan hemen sonra yerel kaynak denetimine zaten kaydedilmiş olur. Bu adımda, Visual Studio 'nun git denetimleri ve kaynak denetimi ile birlikte çalıştığınız **Takım Gezgini** pencere hakkında bilgi edinin.

1. Visual Studio ana penceresinin alt köşesindeki git denetimlerini inceleyin. Soldan sağa, bu denetimler gönderilmeyen işlemeler, kaydedilmemiş değişiklikler, deponun adı ve geçerli dalı gösterir:

    ![Visual Studio penceresinde git denetimleri](media/django/step01-git-controls.png)

    > [!Note]
    > **Yeni proje** iletişim kutusunda **Yeni git deposu oluştur** ' u seçmezseniz, git denetimleri yalnızca yerel bir depo oluşturan **kaynak denetimine Ekle** komutunu gösterir.
    >
    > ![Bir depo oluşturmadıysanız Visual Studio 'da kaynak denetimine Ekle görüntülenir](media/django/step01-git-add-to-source-control.png)

1. Değişiklikler düğmesini seçin ve Visual Studio, **değişiklikler** sayfasında **Takım Gezgini** penceresini açar. Yeni oluşturulan proje kaynak denetimine otomatik olarak zaten yapıldığından, bekleyen bir değişiklik görmezsiniz.

    ![Değişiklikler sayfasında Takım Gezgini penceresi](media/django/step01-team-explorer-changes.png)

1. Visual Studio durum çubuğunda, **Takım Gezgini**' de **eşitleme** sayfasını açmak için teslim edilmemiş işlemeler düğmesini ( **2**ile yukarı ok) seçin. Yalnızca yerel bir depo olduğundan, Bu sayfa depoyu farklı uzak depolara yayımlamak için kolay seçenekler sağlar.

    ![Kaynak denetimi için kullanılabilir git deposu seçeneklerini gösteren Takım Gezgini pencere](media/django/step01-team-explorer.png)

    Kendi projeleriniz için istediğiniz hizmeti seçebilirsiniz. Bu öğreticide, öğreticinin tamamlanan örnek kodunun [Microsoft/Python-Sample-vs-Learning-docgo](https://github.com/Microsoft/python-sample-vs-learning-django) deposunda gerçekleştiği GitHub 'ın kullanımı gösterilmektedir.

1. **Yayınlama** denetimlerinden herhangi birini seçerken **Takım Gezgini** daha fazla bilgi ister. Örneğin, bu öğretici için örnek yayımlarken, deponun kendisi oluşturulmalıdır, bu durumda depo URL 'SI ile **uzak depoya gönderim** seçeneği kullanılır.

    ![Var olan bir uzak depoya göndermek için Takım Gezgini pencere](media/django/step01-push-to-github.png)

    Mevcut bir deponuz yoksa **GitHub 'Da Yayımla** ve **Azure DevOps 'a gönderim** seçenekleri, doğrudan Visual Studio içinden bir tane oluşturmanızı sağlar.

1. Bu öğreticide çalışırken, değişiklikleri yürütmek ve göndermek için Visual Studio 'daki denetimleri kullanarak düzenli aralıklarla habite ulaşın. Bu öğretici size uygun noktalarda hatırlatır.

> [!Tip]
> **Takım Gezgini**içinde hızlıca gezinmek için, kullanılabilir sayfaların açılır menüsünü görmek üzere üstbilgiyi seçin (Yukarıdaki **Resimleri okur veya** yukarıdaki görüntüleri **Gönder** ) seçeneğini belirleyin.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Soru: bir projenin başından itibaren kaynak denetimi kullanmanın avantajları nelerdir?

Cevap: başlangıçtan itibaren kaynak denetimini kullanarak, özellikle de uzak bir depo kullanıyorsanız, projenizin düzenli olarak şirket dışı yedeklemesini sağlar. Yalnızca yerel bir dosya sistemindeki bir projeyi korumanın aksine, kaynak denetimi tam bir değişiklik geçmişi ve tek bir dosyayı ya da projenin tamamını önceki bir duruma geri döndürmenin kolay bir özelliğini sağlar. Bu değişiklik geçmişi, gerilemelerin nedenini (test arızaları) belirlemenize yardımcı olur. Ayrıca, bir proje üzerinde birden fazla kişi çalışıyorsa, kaynak denetimi, üzerine yazma işlemlerini yönetirken ve çakışma çözümü sağladığından gereklidir. Son olarak, otomasyon bir form olan kaynak denetimi, yapıları, testi ve yayın yönetimini otomatikleştirmek için size en iyi şekilde ayarlanır. Bu aslında bir proje için DevOps kullanmanın ilk adımıdır ve giriş engelleri bu kadar düşük olduğundan, kaynak denetimini baştan kullanmanın gerçekten bir nedeni yoktur.

Otomasyon olarak kaynak denetimi hakkında daha fazla bilgi için bkz. [Truth 'Nın kaynağı: DevOps 'Daki depoların rolü](https://msdn.microsoft.com/magazine/mt763232), MSDN Magazine 'teki Web Apps için de geçerli olan mobil uygulamalar için yazılmış bir makaledir.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Soru: Visual Studio 'Nun yeni bir projeyi otomatik olarak çalıştırmasını engelleyebilir miyim?

Yanıt: Evet. Otomatik yürütmeyi devre dışı bırakmak için **Takım Gezgini** **Ayarlar** sayfasına gidin, **Git**  >  **genel ayarları**' nı seçin, **Varsayılan olarak Birleştirmeden sonra değişiklikleri Yürüt**etiketli seçeneği temizleyin ve ardından **Güncelleştir**' i seçin.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Adım 1-3: sanal ortam oluşturma ve kaynak denetiminden dışlama

Projeniz için kaynak denetimini yapılandırdığınıza göre, proje için gerekli Docgo paketlerini içeren sanal ortamı oluşturabilirsiniz. Ardından, ortam klasörünü kaynak denetiminden dışlamak için **Takım Gezgini** kullanabilirsiniz.

1. **Çözüm Gezgini**, **Python ortamları** düğümüne sağ tıklayın ve **sanal ortam ekle**' yi seçin.

    ![Çözüm Gezgini sanal ortam komutu Ekle](media/django/step01-add-virtual-environment-command.png)

1. Bir **requirements.txt dosyası bulduğumuz** belirten bir Ileti Ile **sanal ortam ekle** iletişim kutusu görüntülenir. Bu ileti, Visual Studio 'Nun sanal ortamı yapılandırmak için bu dosyayı kullandığını gösterir.

    ![requirements.txt iletisiyle sanal ortam iletişim kutusu Ekle](media/django/step01-add-virtual-environment-found-requirements.png)

1. Varsayılanları kabul etmek için **Oluştur** ' u seçin. (İsterseniz sanal ortamın adını değiştirebilirsiniz, bu, yalnızca alt klasörünün adını değiştirir ancak `env` Standart bir kuraldır.)

1. İstenirse, yönetici ayrıcalıklarına onay vermeniz gerekiyorsa, Visual Studio paketleri indirirken ve yüklerken birkaç dakika bekleyin. Bu, Docgo için birkaç bin dosyanın çok sayıda alt klasör üzerinde genişletilmesi anlamına gelir! İlerlemeyi, Visual Studio **çıktı** penceresinde görebilirsiniz. Beklerken, aşağıdaki soru bölümlerini izleyin.

1. Visual Studio git denetimlerinde (durum çubuğunda), **Takım Gezgini**içindeki **değişiklikler** sayfasını açan değişiklikler göstergesini ( **99&#42;**) seçin.

    Sanal ortam, binlerce değişikliğe göre oluşturulur, ancak siz (ya da projeyi Klonladığınız herkes) her zaman ortamı *requirements.txt*yeniden oluşturabileceğinden kaynak denetimine bunlardan herhangi birini eklemeniz gerekmez.

    Sanal ortamı dışlamak için **env** klasörüne sağ tıklayın ve **Bu yerel öğeleri yoksay**' ı seçin.

    ![Kaynak denetimi değişikliklerinde sanal ortam yok sayılıyor](media/django/step01-ignore-local-items.png)

1. Sanal ortamı dışladıktan sonra, kalan değişiklikler proje dosyası ve *. gitignore*' dir. *. Gitignore* dosyası, sanal ortam klasörü için eklenen bir giriş içerir. Bir farkı görmek için dosyaya çift tıklayabilirsiniz.

1. Bir işleme iletisi girin ve **Tümünü Kaydet** düğmesini seçin, ardından istediğiniz değişiklikleri uzak deponuza gönderin.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Soru: neden sanal ortam oluşturmak istiyorum?

Cevap: sanal bir ortam, uygulamanızın tam bağımlılıklarını yalıtmak için harika bir yoldur. Bu tür yalıtımlara genel bir Python ortamında çakışmalar önlenir ve hem test hem de işbirliği yardımcı olur. Zaman içinde, bir uygulama geliştirirken, çok sayıda faydalı Python paketini de bir araya getirebilirsiniz. Paketleri projeye özgü bir sanal ortamda tutarak, projenin kaynak denetimine dahil olan bu ortamı açıklayan *requirements.txt* dosyasını kolayca güncelleştirebilirsiniz. Proje, derleme sunucuları, dağıtım sunucuları ve diğer geliştirme bilgisayarları dahil olmak üzere başka bir bilgisayara kopyalandığında, ortamı yalnızca *requirements.txt* (ortamın kaynak denetiminde olması gerekmez) kullanarak yeniden oluşturmak kolaydır. Daha fazla bilgi için bkz. [sanal ortamları kullanma](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Soru: kaynak denetimine zaten kaydedilmiş bir sanal ortamı kaldırmak Nasıl yaparım? mı?

Cevap: Ilk olarak, klasörü hariç tutmak için *. gitignore* dosyanızı düzenleyin: ile birlikte, açıklama ile sonundaki bölümü bulun `# Python Tools for Visual Studio (PTVS)` ve sanal ortam klasörü için gibi yeni bir satır ekleyin `/BasicProject/env` . (Visual Studio **Çözüm Gezgini**dosyayı göstermediğinden, **dosyayı doğrudan dosya**  >  kullanarak açın **Açık**  >  **Dosya** menü komutu. Dosyayı **Takım Gezgini**içinden de açabilirsiniz: **Ayarlar** sayfasında **Depo ayarları**' nı seçin, **& öznitelik dosyalarını yoksay** bölümüne gidin ve sonra **. gitignore**' in yanındaki **Düzenle** bağlantısını seçin.

İkinci olarak, bir komut penceresi açın, *env*ve çalıştırmak gibi sanal ortam klasörünü Içeren *BasicProject* gibi bir klasöre gidin `git rm -r env` . Sonra bu değişiklikleri komut satırından ( `git commit -m 'Remove venv'` ) işleyin veya **Takım Gezgini** **değişiklikler** sayfasından işleyin.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Adım 1-4: ortak kodu Inceleme

Proje oluşturma işlemi tamamlandıktan sonra, ortak Docgo proje kodunu inceleyin (CLı komutu tarafından oluşturulan ile aynı `django-admin startproject <project_name>` ).

1. Proje kökünde *Manage.py*, Visual Studio 'nun otomatik olarak proje başlangıç dosyası olarak ayarladığı Docgo komut satırı yönetim yardımcı programıdır. Yardımcı programını kullanarak komut satırından çalıştırırsınız `python manage.py <command> [options]` . Ortak Docgo görevleri için, Visual Studio uygun menü komutları sağlar. **Çözüm Gezgini** içinde projeye sağ tıklayın ve listeyi görmek için **Python** ' ı seçin. Bu öğreticinin kursunda bu komutlardan bazılarını karşılaşıyorsunuz.

    ![Python projesi bağlam menüsünde docgo komutları](media/django/step01-django-commands-menu.png)

2. Projenizde proje ile aynı adlı bir klasör. Temel Docgo proje dosyalarını içerir:

   - *__init. Kopyala*: Python 'a bu klasörün bir Python paketi olduğunu belirten boş bir dosya.
   - *wsgi.py*: wsgi uyumlu Web sunucularının projenize sunması için bir giriş noktası. Bu dosyayı genellikle üretim Web sunucuları için kancalar sağladığından olduğu gibi bırakın.
   - *Settings.py*: Docgo projesi için bir Web uygulaması geliştirme sürecinde değişiklik yaptığınız ayarları içerir.
   - *URLs.py*: Docgo projesi için bir içindekiler tablosu içerir ve bu, geliştirme sürecinde de değişiklik yapabilirsiniz.

     ![Çözüm Gezgini içindeki docgo proje dosyaları](media/django/step01-django-project-in-solution-explorer.png)

3. Daha önce belirtildiği gibi, Visual Studio şablonu projenize Docgo paketi bağımlılığını belirten bir *requirements.txt* dosyası da ekler. Bu dosyanın varlığı, projeyi ilk oluştururken sanal ortam oluşturmak için sizi davet eder.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Soru: diğer paketleri yükledikten sonra Visual Studio sanal ortamdan bir requirements.txt dosyası oluşturabilir mi?

Yanıt: Evet. **Python ortamları** düğümünü genişletin, sanal ortamınıza sağ tıklayıp **requirements.txtoluştur** komutunu seçin. Ortamı değiştirirken bu komutun düzenli aralıklarla kullanılması ve bu ortama bağlı diğer kod değişiklikleriyle birlikte kaynak denetimine *requirements.txt* değişiklikler yürütmesi yararlı olur. Bir yapı sunucusunda sürekli tümleştirme ayarlarsanız, ortamı her değiştirdiğinizde dosyayı oluşturmanız ve değişiklikleri uygulamanız gerekir.

## <a name="step-1-5-run-the-empty-django-project"></a>Adım 1-5: boş Docgo projesini çalıştırma

1. Visual Studio **'da hata**  >  **ayıklamayı Başlat** (**F5**) ' i seçin veya araç çubuğunda **Web sunucusu** düğmesini kullanın (gördüğünüz tarayıcı değişebilir):

    ![Visual Studio 'da Web sunucusu araç çubuğu düğmesini Çalıştır](media/django/run-web-server-toolbar-button.png)

1. Sunucuyu çalıştırmak `manage.py runserver <port>` , Docgo 'nun yerleşik geliştirme sunucusunu Başlatan komutunu çalıştırmanın anlamına gelir. Visual Studio hata ayıklayıcıyı başlatma dosyası olmayan bir iletiyle **başlatmazsa** , **Çözüm Gezgini** içinde **Manage.py** öğesine sağ tıklayın ve **başlangıç dosyası olarak ayarla**' yı seçin.

1. Sunucuyu başlattığınızda, sunucu günlüğünü de görüntüleyen bir konsol penceresi açık görürsünüz. Visual Studio otomatik olarak bir tarayıcı açar `http://localhost:<port>` . Docgo projesinde hiç uygulama olmadığından, en fazla ne kadar iyi çalıştığını bildirmek için Docgo yalnızca bir varsayılan sayfa gösterir:

    ![Docgo proje varsayılan görünümü](media/django/step01-first-run-success.png)

1. İşiniz bittiğinde, konsol penceresini kapatarak veya **Debug**  >  Visual Studio 'da hata**ayıklamayı Durdur** komutunu kullanarak sunucuyu durdurun.

### <a name="question-is-django-a-web-server-as-well-as-a-framework"></a>Soru: bir Web sunucusunun yanı sıra bir çerçeve mi?

Cevap: Evet ve hayır. Docgo 'ın geliştirme amacıyla kullanılan yerleşik bir Web sunucusu vardır. Bu Web sunucusu, Web uygulamasını yerel olarak çalıştırdığınızda (örneğin, Visual Studio 'da hata ayıklarken) kullanılan şeydir. Ancak, bir Web ana bilgisayarına dağıtırken, Docgo bunun yerine konağın Web sunucusunu kullanır. Docgo projesindeki *wsgi.py* modülü, üretim sunucularına çağrı gerçekleştirir.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Soru: Hata Ayıkla menü komutlarının ve proje Python alt menüsünde sunucu komutlarının kullanımı arasındaki fark nedir?

Cevap: **hata ayıklama** menü komutları ve araç çubuğu düğmelerine ek olarak, **Python**  >  projenin bağlam menüsündeki Python**çalıştırma sunucusu** veya **Python**  >  **çalıştırma hata ayıklama sunucusu** komutlarını kullanarak sunucuyu da başlatabilirsiniz. Her iki komut de çalışan sunucu için yerel URL 'YI (localhost: bağlantı noktası) görebileceğiniz bir konsol penceresi açar. Ancak, bu URL ile bir tarayıcıyı el ile açmanız gerekir ve hata ayıklama sunucusunu çalıştırmak Visual Studio hata ayıklayıcıyı otomatik olarak başlatmamalıdır. Çalıştırmak istiyorsanız, **Debug**  >  **işlemek için** hata ayıkla komutunu kullanarak, çalışan işleme daha sonra bir hata ayıklayıcı ekleyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu noktada, temel Docgo projesi herhangi bir uygulama içermez. Bir sonraki adımda bir uygulama oluşturursunuz. Genellikle docgo projesiyle daha fazla docgo uygulamalarıyla çalıştığınız için, mevcut olan ortak dosyalar hakkında daha fazla bilgi sahibi olmanız gerekmez.

> [!div class="nextstepaction"]
> [Görünümler ve sayfa şablonlarıyla bir Docgo uygulaması oluşturma](learn-django-in-visual-studio-step-02-create-an-app.md)

## <a name="go-deeper"></a>Daha derin git

- Docgo proje kodu: [Ilk Docgo uygulamanızı yazma, Bölüm 1](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) (docs.djangoproject.com)
- Yönetim yardımcı programı: [docgo-admin ve Manage.py](https://docs.djangoproject.com/en/2.0/ref/django-admin/) (docs.djangoproject.com)
- GitHub 'daki öğretici kaynak kodu: [Microsoft/Python-Sample-vs-Learning-docgo](https://github.com/Microsoft/python-sample-vs-learning-django)
