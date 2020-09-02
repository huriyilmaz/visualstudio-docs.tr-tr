---
title: Python uygulama projelerini yönetme
description: Visual Studio 'daki projeler, dosyalar arasındaki bağımlılıkları ve bir uygulamadaki ilişkilerin karmaşıklığını yönetir.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9031b0107babf3d31b6e3b70bb7952cd83467d7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238796"
---
# <a name="python-projects-in-visual-studio"></a>Visual Studio 'da Python projeleri

Python uygulamaları genellikle yalnızca klasörler ve dosyalar kullanılarak tanımlanır, ancak bu yapı, uygulamalar daha büyük hale geldiği ve belki de otomatik olarak oluşturulan dosyalar, Web uygulamaları için JavaScript vb. gibi karmaşık hale gelebilir. Visual Studio projesi bu karmaşıklığın yönetilmesine yardımcı olur. Proje ( *. pyproj* dosyası), projenizle ilişkili tüm kaynak ve içerik dosyalarını tanımlar, her bir dosya için derleme bilgilerini içerir, kaynak denetimi sistemleriyle tümleştirilecek bilgileri saklar ve uygulamanızı mantıksal bileşenlerde düzenlemenize yardımcı olur.

![Çözüm Gezgini Python projesi](media/projects-solution-explorer.png)

Ayrıca, projeler her zaman bir Visual Studio *çözümü*içinde yönetilir ve bu, bir diğerine başvurgerekebilecek birçok proje içerebilir. Örneğin, bir Python projesi uzantı modülünü uygulayan bir C++ projesine başvurabilir. Bu ilişkiyle birlikte, Python projesinde hata ayıklamaya başladığınızda Visual Studio otomatik olarak C++ projesini (gerekliyse) oluşturur. (Genel bir tartışma için bkz. [Visual Studio 'Da çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md).)

Visual Studio, var olan bir klasör ağacından proje oluşturmak için bir şablon ve temiz ve boş bir proje oluşturmak için bir şablon dahil olmak üzere çeşitli Python proje şablonları sağlar. Bkz. bir dizin için [Proje şablonları](#project-templates) .

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Visual Studio 2019, Python kodu içeren bir klasörün açılmasını destekler ve Visual Studio proje ve çözüm dosyaları oluşturmadan kodu çalıştırır. Daha fazla bilgi için bkz. [hızlı başlangıç: Python kodunu bir klasörde açma ve çalıştırma](quickstart-05-python-visual-studio-open-folder.md). Ancak, bu bölümde açıklandığı gibi bir proje dosyası kullanmanın avantajları vardır.
::: moniker-end

> [!Tip]
> Proje olmadan, Visual Studio 'nun tüm sürümleri Python kodu ile iyi çalışır. Örneğin, bir Python dosyasını kendisiyle açabilir ve otomatik olarak tamamlanan, IntelliSense ve hata ayıklamadan (düzenleyicide sağ tıklayıp **hata ayıklamaya başla**' yı seçerek) yararlanabilirsiniz. Bu kod, her zaman varsayılan genel ortamı kullandığından, kodun farklı bir ortam için amaçlanmış olması durumunda yanlış tamamlanmış veya hatalı hatalarla karşılaşabilirsiniz. Ayrıca, Visual Studio, tek dosyanın açıldığı klasördeki tüm dosya ve paketleri analiz ederek önemli ölçüde CPU süresi tüketebilir.
>
> Mevcut [dosyalardan bir proje oluşturma](#create-project-from-existing-files)bölümünde açıklandığı gibi, mevcut koddan bir Visual Studio projesi oluşturmanın basit bir önemi vardır.

![video derinlemesine bakış için film kamerası simgesi](../install/media/video-icon.png "Nasıl yapılacağını görmek için") [: Python projeleriyle kaynak denetimi kullanın](https://youtu.be/Aq8eqApnugM) (YouTube.com, 8gb 55s).

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Dosya ekleme, başlangıç dosyası atama ve ortamları ayarlama

Uygulamanızı geliştirirken, genellikle projeye farklı türlerde yeni dosyalar eklemeniz gerekir. Bu tür dosyaları eklemek, projeye sağ tıklayıp, **Add**  >  eklenecek bir dosyaya gözatabileceğiniz**Varolan öğe** Ekle ' yi seçerek ve **Add**  >  çeşitli öğe şablonlarıyla bir iletişim kutusu getiren**Yeni öğe**Ekle ' yi seçerek yapılır. [Öğe şablonları](python-item-templates.md) başvurusunda açıklandığı gibi, Seçenekler boş Python dosyalarını, bir Python sınıfını, birim testini ve Web uygulamalarıyla ilgili çeşitli dosyaları içerir. Visual Studio sürümünüzde nelerin kullanılabildiğini öğrenmek için bu seçenekleri bir test projesiyle keşfedebilirsiniz.

Her Python projesinde, **Çözüm Gezgini**kalın harflerle gösterilen bir atanmış başlangıç dosyası vardır. Başlangıç dosyası, hata ayıklamayı başlattığınızda (**F5** veya **Hata Ayıkla**,  >  **hata ayıklamayı Başlat**) veya projenizi **etkileşimli** pencerede çalıştırdığınızda (**SHIFT** + **alt** + **F5** veya bir **Debug**  >  **projeyi Python etkileşimli olarak**Hata Ayıkla) çalışan dosyadır. Bunu değiştirmek için, yeni dosyaya sağ tıklayın ve **Başlangıç öğesi olarak ayarla** ' yı (veya Visual Studio 'nun eski sürümlerinde **başlangıç dosyası olarak ayarla** ) seçin.

> [!Tip]
> Seçili başlangıç dosyasını bir projeden kaldırır ve yeni bir tane seçmezseniz, projeyi çalıştırmaya çalıştığınızda Visual Studio hangi Python dosyasının başlatılacağını bilmez. Bu durumda, Visual Studio 2017 sürüm 15,6 ve sonraki bir hata gösterir. önceki sürümler, Python yorumlayıcı çalıştıran bir çıkış penceresi açın veya çıkış penceresinin görüntülendiğini, ancak neredeyse hemen kaybolduğunu görürsünüz. Bu davranışlardan herhangi biriyle karşılaşırsanız, atanmış bir başlangıç dosyasına sahip olup olmadığınızı kontrol edin.
>
> Herhangi bir nedenle çıkış penceresini açık tutmak istiyorsanız projenize sağ tıklayın, **Özellikler**' i seçin, **Hata Ayıkla** sekmesini seçin ve ardından `-i` **yorumlayıcı bağımsız değişkenleri** alanına ekleyin. Bu bağımsız değişken, bir program tamamlandıktan sonra yorumlayıcı 'nın etkileşimli moda geçmesine neden olur, böylece **Ctrl** + çıkmak için CTRL**Z**  >  **ENTER** tuşuna girene kadar pencereyi açık tutun.

::: moniker range="vs-2017"
Her zaman varsayılan genel Python ortamıyla ilişkili yeni bir proje. Projeyi farklı bir ortamla (sanal ortamlar dahil) ilişkilendirmek için, projede **Python ortamları** düğümüne sağ tıklayın, **Python ortamlarını Ekle/Kaldır**' ı seçin ve istediklerinizi seçin.
::: moniker-end
::: moniker range=">=vs-2019"
Her zaman varsayılan genel Python ortamıyla ilişkili yeni bir proje. Projeyi farklı bir ortamla (sanal ortamlar dahil) ilişkilendirmek için, projede **Python ortamları** düğümüne sağ tıklayın, **ortam ekle..** öğesini seçin ve istediklerinizi seçin. Ayrıca, araç çubuğundaki ortamlar açılan denetimini kullanarak projeye bir tane seçebilir ve ortam ekleyebilir veya ekleyebilirsiniz.

![Python araç çubuğuna ortam ekleme komutu](media/environments/environments-toolbar-2019.png)
::: moniker-end

Etkin ortamı değiştirmek için **Çözüm Gezgini** ' de istediğiniz ortama sağ tıklayın ve ortamı aşağıda gösterildiği gibi **Etkinleştir** ' i seçin. Daha fazla bilgi için bkz. [proje için ortam seçme](selecting-a-python-environment-for-a-project.md).

![Python projesi için bir ortamı etkinleştirme](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Proje şablonları

Visual Studio, sıfırdan veya mevcut koddan bir Python projesi ayarlamanıza yönelik çeşitli yollar sunar. Bir şablon kullanmak için **Dosya**  >  **Yeni**  >  **Proje** menü komutunu seçin veya **Çözüm Gezgini** ' de çözüme sağ tıklayıp yeni proje **Ekle**' yi seçin ve  >  **New Project**her ikisi de aşağıdaki **Yeni proje** iletişim kutusunu açın. Python 'a özgü şablonları görmek için, "Python" üzerinde arama yapın veya **yüklü**  >  **Python** düğümünü seçin:

![Python şablonlarıyla yeni proje iletişim kutusu](media/projects-new-project-dialog.png)

Aşağıdaki tabloda, Visual Studio 2017 ve üzeri sürümlerde kullanılabilen şablonlar özetlenmektedir (tüm şablonlar önceki sürümlerde kullanılamaz):

| Şablon | Description |
| --- | --- |
| [**Mevcut Python kodundan**](#create-project-from-existing-files) | Bir klasör yapısındaki mevcut Python kodundan bir Visual Studio projesi oluşturur.  |
| **Python uygulaması** | Tek, boş kaynak dosyası olan yeni bir Python uygulaması için temel bir proje yapısı. Varsayılan olarak, proje varsayılan genel ortamın konsol yorumlayıcısında çalışır ve bu, [farklı bir ortam atayarak](selecting-a-python-environment-for-a-project.md)değiştirebilirsiniz. |
| [**Azure bulut hizmeti**](python-azure-cloud-service-project-template.md) | Python 'da yazılmış bir Azure bulut hizmeti projesi. |
| [**Web projeleri**](python-web-application-project-templates.md) | Şişe, Docgo ve Flask gibi çeşitli çerçeveleri temel alan Web uygulamalarına yönelik projeler. |
| **IronPython uygulaması** | Python uygulama şablonuna benzer ancak varsayılan olarak IronPython 'u kullanarak .net birlikte çalışma ve karışık modda hata ayıklamayı .NET dilleri ile etkinleştirir. |
| **IronPython WPF uygulaması** | Uygulamanın kullanıcı arabirimi için Windows Presentation Foundation XAML dosyaları ile IronPython kullanan bir proje yapısı. Visual Studio bir XAML kullanıcı arabirimi Tasarımcısı sağlar, arka plan kod Python 'da yazılabilir ve uygulama bir konsolu görüntülemeden çalışır. |
| **IronPython Silverlight Web sayfası** | Silverlight kullanan bir tarayıcıda çalışan bir IronPython projesi. Uygulamanın Python kodu Web sayfasına betik olarak dahildir. Ortak betik etiketi, bir Silverlight içinde çalışan IronPython 'u Başlatan, Python kodunuzun DOM ile etkileşimde bulunduğu bazı JavaScript kodlarını çeker. |
| **IronPython Windows Forms uygulaması** | Windows Forms ile kod kullanılarak kullanıcı arabirimi ile IronPython kullanan bir proje yapısı. Uygulama, konsolu görüntülemeden çalışır. |
| **Arka plan uygulaması (IoT)** | , Cihazlarda arka plan hizmetleri olarak çalışacak Python projelerinin dağıtılmasını destekler. Daha fazla bilgi için [Windows IoT geliştirme merkezi](https://dev.windows.com/en-us/iot) ' ni ziyaret edin. |
| **Python uzantı modülü** | Bu şablon, Python **yerel geliştirme araçlarını** Visual Studio 2017 veya sonraki sürümlerde Python iş yüküne yüklediyseniz Visual C++ altında görüntülenir (bkz. [yükleme](installing-python-support-in-visual-studio.md)). Bu, [Python Için c++ uzantısı oluşturma](working-with-c-cpp-python-in-visual-studio.md)konusunda açıklananlara benzer bir C++ uzantısı DLL için çekirdek yapı sağlar. |

> [!Note]
> Python, yorumlanan bir dil olduğundan, Visual Studio 'daki Python projeleri diğer derlenmiş dil projeleri gibi tek başına bir yürütülebilir dosya üretmez (örneğin, C#). Daha fazla bilgi için bkz. [sorular ve yanıtlar](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Mevcut dosyalardan bir proje oluşturma

> [!Important]
> Burada açıklanan işlem özgün kaynak dosyalarını taşımaz veya kopyalamaz. Bir kopyalama ile çalışmak istiyorsanız önce klasörü çoğaltın.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Bağlı dosyalar

Bağlantılı dosyalar bir projeye getirilen ancak genellikle uygulamanın proje klasörlerinin dışında bulunan dosyalardır. Bunlar, bir kaplama kısayolu simgesi olan normal dosyalar olarak **Çözüm Gezgini** görünürler: ![ bağlı dosya simgesi](media/projects-linked-file-icon.png)

Bağlantılı dosyalar *. pyproj* dosyasında öğesi kullanılarak belirtilir `<Compile Include="...">` . Bağlı dosyalar, dizin yapısının dışında göreli bir yol kullanıyorsa veya **Çözüm Gezgini**içinde yollar kullandıklarında açık bir şekilde yapılır:

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Bağlı dosyalar aşağıdaki koşullardan herhangi biri altında yok sayılır:

- Bağlantılı dosya, bağlantı meta verilerini ve Include özniteliğinde belirtilen yolu proje dizini içinde yaşar
- Bağlantılı dosya proje hiyerarşisi içinde bulunan bir dosyayı yineliyor
- Bağlantılı dosya, bağlantı meta verilerini içerir ve bağlantı yolu proje hiyerarşisinin dışında göreli bir yoldur
- Bağlantı yolunun kökü

### <a name="work-with-linked-files"></a>Bağlantılı dosyalarla çalışma

Var olan bir öğeyi bağlantı olarak eklemek için, projede dosyayı eklemek istediğiniz klasörü sağ tıklatın ve ardından **Add**  >  **Varolan öğe**Ekle ' yi seçin. Görüntülenen iletişim kutusunda bir dosya seçin ve **Ekle** düğmesine açılan listeden **bağlantı olarak ekle** ' yi seçin. Çakışan dosya olmadığından, bu komut seçili klasörde bir bağlantı oluşturur. Ancak, aynı ada sahip bir dosya zaten varsa veya projede zaten bu dosya için bir bağlantı varsa bağlantı eklenmez.

Proje klasörlerinde zaten bulunan bir dosyaya bağlantı kurmayı denerseniz, bir bağlantı olarak değil, normal bir dosya olarak eklenir. Dosyayı bir bağlantıya dönüştürmek **için dosya**  >  **farklı kaydet** ' i seçerek dosyayı proje hiyerarşisi dışında bir konuma kaydedin; Visual Studio otomatik olarak bir bağlantıya dönüştürür. Benzer şekilde, dosyayı **File**  >  Proje hiyerarşisinde bir yere kaydetmek için dosya**farklı kaydet** kullanılarak bir bağlantı geri dönüştürülebilir.

Bağlı bir dosyayı **Çözüm Gezgini**taşırsanız bağlantı taşınır ancak gerçek dosya etkilenmez. Benzer şekilde, bir bağlantıyı silme, dosyayı etkilemeden bağlantıyı kaldırır.

Bağlantılı dosyalar yeniden adlandırılamaz.

## <a name="references"></a>Başvurular

Visual Studio projeleri, **Çözüm Gezgini**' deki **Başvurular** düğümü altında görünen projelere ve uzantılara başvuru eklemeyi destekler:

![Python projelerindeki uzantı başvuruları](media/projects-extension-references.png)

Uzantı başvuruları genellikle projeler arasındaki bağımlılıkları gösterir ve tasarım zamanında IntelliSense sağlamak veya derleme zamanında bağlamak için kullanılır. Python projeleri, başvuruları benzer bir biçimde kullanır, ancak Python 'un dinamik doğası gereği, gelişmiş IntelliSense sağlamak için öncelikle tasarım zamanında kullanılır. Ayrıca, ek bağımlılıklar yüklemek üzere Microsoft Azure dağıtım için de kullanılabilir.

### <a name="extension-modules"></a>Uzantı modülleri

*. PYD* dosyası başvurusu, oluşturulan modül için IntelliSense 'i sağlar. Visual Studio, *. PYD* dosyasını Python yorumlayıcı 'ya yükler ve bunların tür ve işlevlerini gözlemleyip. Ayrıca, imza yardımı sağlamak için işlevler için belge dizelerini ayrıştırmaya çalışır.

Herhangi bir zamanda uzantı modülü diskte güncelleştirilirse, Visual Studio modülü arka planda yeniden analiz eder. Bu eylemin çalışma zamanı davranışı üzerinde hiçbir etkisi yoktur, ancak bazı tamamlamalar analiz tamamlanana kadar kullanılamaz.

Modülün bulunduğu klasöre bir [arama yolu](search-paths.md) da eklemeniz gerekebilir.

### <a name="net-projects"></a>.NET projeleri

IronPython ile çalışırken, IntelliSense 'i etkinleştirmek için .NET derlemelerine başvurular ekleyebilirsiniz. Çözümünüzdeki .NET projeleri için, Python projenizde **Başvurular** düğümüne sağ tıklayın, **Başvuru Ekle**' yi seçin, **Projeler** sekmesini seçin ve istediğiniz projeye gidin. Ayrı olarak indirdiğiniz dll 'Ler için, bunun yerine, **Gözden** geçirme sekmesini seçin ve istenen dll 'ye gidin.

Bir çağrısı yapılıncaya kadar IronPython içindeki başvurular kullanılamadığından `clr.AddReference('<AssemblyName>')` , `clr.AddReference` genellikle kodunuzun başlangıcında derlemeye uygun bir çağrı eklemeniz gerekir. Örneğin, Visual Studio 'da **IronPython Windows Forms uygulama** projesi şablonu tarafından oluşturulan kod, dosyanın en üstünde iki çağrı içerir:

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>WebPI projeleri

WebPI akışı aracılığıyla ek bileşenler yükleyebileceğiniz Microsoft Azure Cloud Services dağıtım için WebPI ürün girişlerine başvurular ekleyebilirsiniz. Varsayılan olarak, belirtilen akış Python 'a özgüdür ve Docgo, Cpyıthon ve diğer çekirdek bileşenleri içerir. Ayrıca, aşağıda gösterildiği gibi kendi akışınızı de seçebilirsiniz. Microsoft Azure yayımlandığında, bir kurulum görevi başvurulan ürünlerin tümünü kurar.

> [!IMPORTANT]
> WebPI projeleri Visual Studio 2017 veya Visual Studio 2019 ' de kullanılamaz.

![WebPI başvuruları](media/projects-webPI-components.png)
