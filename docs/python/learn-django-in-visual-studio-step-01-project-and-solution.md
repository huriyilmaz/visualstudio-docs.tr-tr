---
title: Visual Studio, 1. adım, Django temel bilgileri'ne göz atarak Django öğreticisi hakkında bilgi edinin
titleSuffix: ''
description: Django geliştirmesi için sağladığı destek Visual Studio Django temel bilgileri Visual Studio kılavuz.
ms.custom: devdivchpfy22
ms.date: 12/20/2021
ms.topic: tutorial
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 829250064d43af913e102bd8e298760b732b0f69
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135803355"
---
# <a name="tutorial-get-started-with-the-django-web-framework-in-visual-studio"></a>Öğretici: Kullanmaya başlayın Django web çerçevesiyle Visual Studio

[Django](https://www.djangoproject.com/) hızlı, güvenli ve ölçeklenebilir web geliştirme için tasarlanmış üst düzey bir Python çerçevesidir. Bu öğreticide, Django tabanlı web uygulamalarının oluşturulmasını Visual Studio sağlayan proje şablonları bağlamında Django çerçevesi keşfedildi.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

::: moniker range="vs-2017"
- "Blank Django Web Project" şablonunu kullanarak Git deposunda temel bir Django projesi oluşturma (1. adım)
- Tek sayfalı bir Django uygulaması oluşturma ve bu sayfayı şablon kullanarak işleme (2. adım)
- Statik dosyaları hizmet etme, sayfa ekleme ve şablon devralma kullanma (3. adım)
- Django Web Project şablonunu kullanarak birden çok sayfa ve duyarlı tasarıma sahip bir uygulama oluşturma (4. adım)
- Kullanıcıların kimliğini doğrulama (5. adım)
- Yönetim arabirimine modelleri, veritabanı geçişlerini ve özelleştirmelerini kullanan bir uygulama oluşturmak için Polls Django Web Project şablonunu kullanın (6. adım)
::: moniker-end

::: moniker range=">=vs-2019"
- "Blank Django Web Project" şablonunu kullanarak Git deposunda temel bir Django projesi oluşturma (1. adım)
- Tek sayfalı bir Django uygulaması oluşturma ve bu sayfayı şablon kullanarak işleme (2. adım)
- Statik dosyaları hizmet etme, sayfa ekleme ve şablon devralma kullanma (3. adım)
- Django Web Project şablonunu kullanarak birden çok sayfa ve duyarlı tasarıma sahip bir uygulama oluşturma (4. adım)
- Kullanıcıların kimliğini doğrulama (5. adım)
::: moniker-end

## <a name="prerequisites"></a>Önkoşullar

::: moniker range="<=vs-2019"
- Visual Studio 2017 veya sonraki Windows seçenekleriyle birlikte kullanın:
  - **Python geliştirme iş** yükü (**Yükleyicide** İş yükü sekmesi). Yönergeler için [bkz. Python desteğini Visual Studio.](installing-python-support-in-visual-studio.md)
  - **Git for Windows** and **GitHub Extension for Visual Studio** tab **on the Individual components (Kod** araçları altındaki Bağımsız bileşenler sekmesinde). 
::: moniker-end

::: moniker range="vs-2022"
- Visual Studio 2022'Windows seçenekleriyle birlikte kullanın:
  - **Python geliştirme iş** yükü (**Yükleyicide** İş yükü sekmesi). Yönergeler için [bkz. Python desteğini Visual Studio.](installing-python-support-in-visual-studio.md)
  - **Kod araçları Windows** Bileşenler **sekmesindeki** Git for **Windows.**
::: moniker-end

Django proje şablonları, Visual Studio için Python Araçları'nin önceki tüm sürümlerine de dahil edilir, ancak ayrıntılar bu öğreticide ele alınanlardan farklı olabilir (özellikle Django çerçevesinin önceki sürümlerinden farklıdır).

Python geliştirmesi şu anda bu Mac için Visual Studio. Mac ve Linux'ta python [uzantısını kullanarak Visual Studio Code.](https://code.visualstudio.com/docs/python/python-tutorial)

### <a name="visual-studio-projects-and-django-projects"></a>"Visual Studio projeleri" ve "Django projeleri"

Django terminolojisinde bir "Django projesi", tam bir web uygulaması oluşturmak için bir web ana bilgisayar üzerinde dağıtmış olduğunuz bir veya daha fazla "uygulama" ile birlikte çeşitli site düzeyinde yapılandırma dosyalarından oluşur. Bir Django projesi birden çok uygulama içerebilir ve aynı uygulama birden çok Django projesinde olabilir.

Bir Visual Studio projesi, Django projesini ve birden çok uygulama içerebilir. Kolaylık olması açısından, bu öğretici yalnızca bir "proje" anlamına her başvurulduğu zaman, Visual Studio ifade eder. Web uygulamasının "Django projesi" bölümüne başvurulduğu zaman, özel olarak "Django projesi" kullanır.

Bu öğretici boyunca, her biri tek bir Django uygulaması içeren üç ayrı Django projesi içeren tek bir Visual Studio çözüm oluşturacağız. Projeleri aynı çözümde tutarak, karşılaştırma için farklı dosyalar arasında kolayca geçiş yapabilirsiniz.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>1-1. Adım: Visual Studio proje ve çözüm oluşturma

Komut satırdan Django ile çalışırken genellikle komutunu çalıştırarak bir projeyi `django-admin startproject <project_name>` başlatabilirsiniz. Bu Visual Studio" "Boş Django Web Project" şablonu kullanılarak bir proje ve çözüm içinde Visual Studio yapıyı sağlar.

::: moniker range="<=vs-2019"
1. Bu Visual Studio Yeni   >    >  **Dosya'Project** seçin, "Django" araması yazın ve **Boş Django Web Project** seçin. (Şablonu Python'ın altında da **bulabilirsiniz**  >  **Sol** listede Web.)

    ![Boş Django Web Visual Studio için yeni proje iletişim Project](media/django/step01-new-blank-project.png)

1. İletişim kutusunun en altındaki alanlara aşağıdaki bilgileri girin (önceki grafikte gösterildiği gibi) ve tamam'ı **seçin:**

    - **Ad:** Projeniz için Visual Studio **BasicProject olarak ayarlayın.** Bu ad Django projesi için de kullanılır.
    - **Konum:** Uygulama çözümünün ve projenin oluşturul Visual Studio bir konum belirtin.
    - **Çözüm:** Bu denetimi varsayılan Yeni çözüm oluştur **seçeneği olarak** bırakın.
    - **Çözüm adı:** **LearningDjango** olarak ayarlayın. Bu, bu öğreticide çözüm için birden çok proje için kapsayıcı olarak uygundur.
    - **Çözüm için dizin oluşturma:** Ayarlanmış (varsayılan) bırakın.
    - **Yeni Git deposu oluşturma:** Çözümü oluşturduğunda yerel bir Git deposu Visual Studio için bu seçeneği (varsayılan olarak açıktır) seçin. Bu seçeneği görmüyorsanız, Visual Studio yükleyicisini çalıştırın ve Kod araçları altındaki Bağımsız bileşenler sekmesinde Windows ve GitHub için  **GitHub** Uzantısı'Visual Studio'ı **ekleyin.** 

1. Bir süre sonra Visual Studio Bu proje dış paketler gerektiriyor (aşağıda gösterilmiştir) iletişim **kutusunu** girmenizi sağlar. Şablonda en son Django 1.x *paketine* başvuran birrequirements.txtdosyası olduğundan bu iletişim kutusu görüntülenir. (Tam **bağımlılıkları görmek için** Gerekli paketleri göster'i seçin.)

    ![Projenin dış paketler gerektirdiğini söyleyen istem](media/django/step01-requirements-prompt-install-myself.png)

1. Bunları ben **yükleyeceğim seçeneğini belirleyin.** Sanal ortamı kısa süre içinde oluşturarak kaynak denetiminden dışlanmış olduğundan emin olun. (Ortamı her zaman *requirements.txt.)*
::: moniker-end

::: moniker range="vs-2022"
1. Bu Visual Studio Yeni  >  > **Dosya'Project** seçin, "Django" araması yazın ve **Boş Django Web Project** şablonunu seçin ve ardından Sonraki'yi **seçin.**

    ![Boş Django Web Visual Studio için yeni proje iletişim Project](media/django/step-01-create-new-project-screen-1-vs-2022.png)
  
1. Aşağıdaki bilgileri girin ve Oluştur'a **basın:**

    - **Project:** proje adı olarak Visual Studio **BasicProject olarak ayarlayın.** Bu ad Django projesi için de kullanılır.
    - **Konum:** Uygulama çözümünün ve projenin oluşturul Visual Studio bir konum belirtin.
    - **Çözüm:** Bu denetimi varsayılan Yeni çözüm oluştur **seçeneği olarak** bırakın.
    - **Çözüm adı:** **LearningDjango** olarak ayarlayın. Bu, bu öğreticide çözüm için birden çok proje için kapsayıcı olarak uygundur.

::: moniker-end

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>1-2. Adım: Git denetimlerini inceleme ve uzak depoda yayımlama

::: moniker range="<=vs-2019"
New **Project** iletişim kutusunda **Yeni Git** deposu oluştur'Project, oluşturma işlemi tamamlandıktan sonra proje zaten yerel kaynak denetimine kaydedilmiştir. Bu adımda, Visual Studio Git denetimleri ve kaynak **denetimiyle Takım Gezgini** pencere hakkında bilgi edinebilirsiniz.

1. Ana pencerenin alt köşesindeki Git Visual Studio inceleme. Soldan sağa doğru bu denetimler, işlenmiş olmayan işlemeleri, işlanmamış değişiklikleri, deponun adını ve geçerli dalı gösterir:

    ![Visual Studio penceresinde git denetimleri](media/django/step01-git-controls.png)

    > [!Note]
    > Yeni Depo oluştur iletişim kutusunda **Yeni Git** **deposu** oluştur Project Git denetimleri yalnızca yerel  depo oluşturan bir Kaynak denetimine ekle komutunu gösterir.
    >
    > ![Depo oluşturmadıysanız Visual Studio Denetimine Ekle görüntülenir](media/django/step01-git-add-to-source-control.png)

1. Değişiklikler düğmesini seçin ve Visual Studio sayfasında **Takım Gezgini** penceresini **açın.** Yeni oluşturulan proje otomatik olarak kaynak denetimine zaten bağlı olduğundan, bekleyen hiçbir değişiklik görmüyoruz.

    ![Takım Gezgini sayfasındaki Takım Gezgini penceresi](media/django/step01-team-explorer-changes.png)

1. İlke Visual Studio çubuğunda, atlanmamış işlemeler düğmesini **(2** ile yukarı ok) seçerek eşitleme sayfasını  **Takım Gezgini.** Yalnızca yerel bir depoya sahip olduğunuz için sayfa, depoyu farklı uzak depolarda yayımlamak için kolay seçenekler sağlar.

    ![Takım Gezgini denetimi için kullanılabilir Git deposu seçeneklerini gösteren bir pencere](media/django/step01-team-explorer.png)

    Kendi projeleriniz için istediğiniz hizmeti seçebilirsiniz. Bu öğreticide, GitHub için tamamlanmış örnek [kodun Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django) deposunda tutularak bulunduğu GitHub'nin kullanımı açıklanmıştır.

1. Yayımla denetimlerden birini **seçerek** **Takım Gezgini** daha fazla bilgi isteminde bulundurabilirsiniz. Örneğin, bu öğreticinin örneğini yayımlarken önce deponun kendisi oluşturulacak ve  bu durumda deponun URL'si ile Uzak Depoya Itme seçeneği kullanılmıştır.

    ![Takım Gezgini uzak depoya itmeye uygun bir pencere](media/django/step01-push-to-github.png)

    Mevcut bir depoya sahip değilsanız, **GitHub'da yayımla ve** Azure DevOps'a Visual Studio. 

1. Bu öğreticide çalışmaya devam ettiyken, değişiklikleri işlemek ve itmek için Visual Studio denetimlerini düzenli aralıklarla kullanma alışkanlık haline geliyor. Bu öğretici size uygun noktaları anımsatır.

> [!Tip]
> içinde hızla **gezinmek Takım Gezgini,** kullanılabilir sayfaların açılır  menüsünü  görmek için üst bilgi (yukarıdaki görüntülerde Değişiklikler veya Anında İtme)'yi seçin.

::: moniker-end

::: moniker range="vs-2022"
Bu adımda, Visual Studio Git denetimleri ve kaynak **denetimiyle Takım Gezgini** pencere hakkında bilgi edinebilirsiniz.

1. Projeyi yerel kaynak denetiminize işlemek  için ana pencerenin alt köşesindeki Kaynak Denetimine Ekle komutuna Visual Studio Git seçeneğini belirleyin. Bu eylem sizi, yeni bir depo oluştur ve iterek Git deposu oluştur penceresine alır.

    ![Git deposu oluşturma](media/django/step01-git-add-to-source-control.png)

1. Depoyu oluşturduktan sonra, altta bir dizi yeni Git denetimi görünür. Soldan sağa doğru bu denetimler, işlenmiş olmayan işlemeleri, işlanmamış değişiklikleri, geçerli dalı ve deponun adını gösterir:

    ![Visual Studio penceresinde git denetimleri](media/django/step01-git-controls.png)


1. Git değişiklikleri düğmesini seçin ve Visual Studio git **değişiklikleri Takım Gezgini** açılan **pencereyi** açın. Yeni oluşturulan proje otomatik olarak kaynak denetimine zaten bağlı olduğundan, bekleyen hiçbir değişiklik görmüyoruz.

    ![Takım Gezgini Git Değişiklikleri sayfasındaki bir pencere](media/django/step-01-team-explorer-git-changes-vs-2022.png)
    

1. Visual Studio durum çubuğunda, **Takım Gezgini**' de **eşitleme** sayfasını açmak için gönderişsiz işlemeler düğmesini ( **2** ile yukarı ok) seçin. Yalnızca yerel bir depo olduğundan, Bu sayfa depoyu farklı uzak depolara yayımlamak için kolay seçenekler sağlar.

    ![Kaynak denetimi için kullanılabilir git deposu seçeneklerini gösteren Takım Gezgini pencere](media/django/step01-team-explorer.png)

    Kendi projeleriniz için istediğiniz hizmeti seçebilirsiniz. bu öğreticide, öğreticinin tamamlanan örnek kodunun [Microsoft/python-sample-vs-learning-docgo](https://github.com/Microsoft/python-sample-vs-learning-django) deposunda gerçekleştiği GitHub kullanımı gösterilmektedir.

1. **Yayınlama** denetimlerinden herhangi birini seçerken **Takım Gezgini** daha fazla bilgi ister. Örneğin, bu öğretici için örnek yayımlarken, deponun kendisi oluşturulmalıdır, bu durumda deponun URL 'SI ile **uzak depoya gönder** seçeneği kullanılmıştır.

    ![Var olan bir uzak depoya göndermek için Takım Gezgini pencere](media/django/step01-push-to-github.png)

    mevcut bir deponuz yoksa **GitHub yayımla** ve **Azure DevOps seçeneklerine gönder** seçenekleri doğrudan Visual Studio içinden bir tane oluşturmanızı sağlar.

1. bu öğreticide çalışırken, değişiklikleri yürütmek ve göndermek için Visual Studio içindeki denetimleri kullanarak düzenli aralıklarla habite ulaşın. Bu öğretici size uygun noktalarda hatırlatır.

> [!Tip]
> **Takım Gezgini** içinde hızlıca gezinmek için, kullanılabilir sayfaların açılır menüsünü görmek üzere üstbilgiyi seçin (Yukarıdaki **Resimleri okur veya** yukarıdaki görüntüleri **Gönder** ) seçeneğini belirleyin.

::: moniker-end

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Soru: bir projenin başından itibaren kaynak denetimi kullanmanın avantajları nelerdir?

Yanıt: başlangıçtan itibaren kaynak denetimi, özellikle de uzak bir depo kullanıyorsanız, projenizin düzenli olarak şirket dışı yedeklemesini sağlar. Yalnızca yerel bir dosya sistemindeki bir projeyi korumanın aksine, kaynak denetimi tam bir değişiklik geçmişi ve tek bir dosyayı ya da projenin tamamını önceki bir duruma geri döndürmenin kolay bir özelliğini sağlar. Bu değişiklik geçmişi, gerilemelerin nedenini (test arızaları) belirlemenize yardımcı olur. Bir projede birden fazla kişi çalışıyorsa, kaynak denetimi, üzerine yazma işlemlerini yönettiğinden ve çakışma çözümü sağladığından gereklidir.

Son olarak, otomasyon bir form olan kaynak denetimi, yapıları, testi ve yayın yönetimini otomatikleştirmek için size en iyi şekilde ayarlanır. bu, bir proje için DevOps kullanmanın ilk adımıdır. Giriş engelleri bu kadar düşük olduğundan, kaynak denetimini baştan kullanmanın bir nedeni yoktur.

kaynak denetimi ile otomasyon olarak daha fazla tartışma için bkz. [gerçeği: DevOps içindeki depoların rolü](/archive/msdn-magazine/2016/september/mobile-devops-the-source-of-truth-the-role-of-repositories-in-devops), MSDN Magazine 'teki web apps için de geçerli olan mobil uygulamalar için yazılmış bir makale.

### <a name="question-can-i-prevent-visual-studio-from-autocommitting-a-new-project"></a>soru: Visual Studio yeni bir projeyi tekrar işlemesini engelleyebilir miyim?

Yanıt: Evet. yeniden yürütmeyi devre dışı bırakmak için **Takım Gezgini** **Ayarlar** sayfasına gidin, **git**  >  **genel ayarları**' nı seçin, **varsayılan olarak birleştirmeden sonra değişiklikleri yürüt** etiketli seçeneği temizleyin ve ardından **güncelleştir**' i seçin.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Adım 1-3: sanal ortam oluşturma ve kaynak denetiminden dışlama

Projeniz için kaynak denetimini yapılandırdığınıza göre, proje için gerekli Docgo paketlerini içeren sanal ortamı oluşturabilirsiniz. Ardından, ortam klasörünü kaynak denetiminden dışlamak için **Takım Gezgini** kullanabilirsiniz.

::: moniker range="<=vs-2019"

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

1. Bir işleme iletisi girin ve **Tümünü Kaydet** düğmesini seçin ve ardından işlemeleri uzak deponuza gönderin.

::: moniker-end

::: moniker range="vs-2022"

1. **Çözüm Gezgini**, **Python ortamları** düğümüne sağ tıklayın ve **ortam ekle**' yi seçin.

    ![Çözüm Gezgini sanal ortam komutu Ekle](media/django/step-01-add-virtual-environment-command-vs-2022.png)


1. Sanal ortam Ekle iletişim kutusunda Varsayılanları kabul etmek için **Oluştur** ' u seçin. (İsterseniz sanal ortamın adını değiştirebilirsiniz, bu, yalnızca alt klasörünün adını değiştirir ancak `env` Standart bir kuraldır.)

    ![requirements.txt iletisiyle sanal ortam iletişim kutusu Ekle](media/django/step-01-add-virtual-environment-dialog-vs-2022.png)

1. istenirse, yönetici ayrıcalıklarına izin vermek için Visual Studio birkaç dakika bekleyin ve paketleri indirip yükler. Bu süre boyunca, birkaç alt klasör olarak çok sayıda dosya aktarılmıştır! ilerlemeyi Visual Studio **çıkış** penceresinde görebilirsiniz. Beklerken, aşağıdaki soru bölümlerini izleyin.

1. Git denetimlerinde Visual Studio (durum çubuğunda), **Takım Gezgini** **değişiklikler** sayfasını açan değişiklikler göstergesini ( **99&#42;**) seçin.

    Sanal ortam, binlerce değişikliğe göre oluşturulur, ancak siz (ya da projeyi Klonladığınız herkes) her zaman ortamı *requirements.txt* yeniden oluşturabileceğinden kaynak denetimine bunlardan herhangi birini eklemeniz gerekmez.

    Sanal ortamı dışlamak için **env** klasörüne sağ tıklayın ve **Bu yerel öğeleri yoksay**' ı seçin.

    ![Kaynak denetimi değişikliklerinde sanal ortam yok sayılıyor](media/django/step-01-ignore-local-items-vs-2022.png)

1. Sanal ortamı dışladıktan sonra, kalan değişiklikler proje dosyası ve *. gitignore*' dir. *. Gitignore* dosyası, sanal ortam klasörü için eklenen bir giriş içerir. Bir farkı görmek için dosyaya çift tıklayabilirsiniz.

1. Bir işleme iletisi girin ve **Tümünü Kaydet** düğmesini seçin ve ardından işlemeleri uzak deponuza gönderin.

::: moniker-end

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Soru: neden sanal ortam oluşturmak istiyorum?

Cevap: sanal bir ortam, uygulamanızın tam bağımlılıklarını yalıtmak için harika bir yoldur. Bu tür yalıtımlara genel bir Python ortamında çakışmalar önlenir ve hem test hem de işbirliği yardımcı olur. Zaman içinde, bir uygulama geliştirirken, çok sayıda faydalı Python paketini de bir araya getirebilirsiniz. Paketleri projeye özgü bir sanal ortamda tutarak, projenin kaynak denetimine dahil olan bu ortamı açıklayan *requirements.txt* dosyasını kolayca güncelleştirebilirsiniz. Proje, derleme sunucuları, dağıtım sunucuları ve diğer geliştirme bilgisayarları dahil olmak üzere başka bir bilgisayara kopyalandığında, ortamı yalnızca *requirements.txt* (ortamın kaynak denetiminde olması gerekmez) kullanarak yeniden oluşturmak kolaydır. Daha fazla bilgi için bkz. [sanal ortamları kullanma](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Soru: kaynak denetimine zaten kaydedilmiş bir sanal ortamı kaldırmak Nasıl yaparım? mı?

Cevap: Ilk olarak, klasörü hariç tutmak için *. gitignore* dosyanızı düzenleyin: ile birlikte, açıklama ile sonundaki bölümü bulun `# Python Tools for Visual Studio (PTVS)` ve sanal ortam klasörü için gibi yeni bir satır ekleyin `/BasicProject/env` . (Visual Studio dosyayı **Çözüm Gezgini** göstermediği **için dosya dosya**  >  **aç**  >   menü komutunu kullanarak doğrudan açın. dosyayı **Takım Gezgini** içinden de açabilirsiniz: **Ayarlar** sayfasında **depo Ayarlar**' yı seçin, **& öznitelikleri dosyalarını yoksay** bölümüne gidin ve sonra **. gitignore**' in yanındaki **düzenle** bağlantısını seçin.

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

### <a name="question-is-django-a-web-server-and-a-framework"></a>Soru: bir Web sunucusu ve çerçeve mi?

Cevap: Evet ve hayır. Docgo, geliştirme amaçlarıyla kullanılan yerleşik bir Web sunucusuna sahiptir. Bu Web sunucusu, Web uygulamasını yerel olarak çalıştırdığınızda (Visual Studio hata ayıklaması yaparken) kullanılır. Ancak, bir Web ana bilgisayarına dağıtırken, Docgo bunun yerine konağın Web sunucusunu kullanır. Docgo projesindeki *wsgi.py* modülü, üretim sunucularına çağrı gerçekleştirir.

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