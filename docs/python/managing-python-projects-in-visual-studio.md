---
title: Python uygulama projelerini yönetme
description: Visual Studio projeler, dosyalar arasındaki bağımlılıkları ve bir uygulamadaki ilişkilerin karmaşıklığını yönetir.
ms.date: 03/18/2019
ms.topic: conceptual
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 77b67853fd673b8c97a18ab1906aa31a089ea6be
ms.sourcegitcommit: f303d052e451bcfd4722b99a9adbcb3f575d1678
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "137816823"
---
# <a name="python-projects-in-visual-studio"></a>Visual Studio 'de Python projeleri

Python uygulamaları genellikle yalnızca klasörler ve dosyalar kullanılarak tanımlanır, ancak bu yapı, uygulamalar daha büyük hale geldiği ve belki de otomatik olarak oluşturulan dosyalar, Web uygulamaları için JavaScript vb. gibi karmaşık hale gelebilir. bir Visual Studio projesi bu karmaşıklığın yönetilmesine yardımcı olur. Proje ( *. pyproj* dosyası), projenizle ilişkili tüm kaynak ve içerik dosyalarını tanımlar, her bir dosya için derleme bilgilerini içerir, kaynak denetimi sistemleriyle tümleştirilecek bilgileri saklar ve uygulamanızı mantıksal bileşenlerde düzenlemenize yardımcı olur.

![Çözüm Gezgini Python projesi](media/projects-solution-explorer.png)

ayrıca, projeler her zaman bir Visual Studio *çözümü* içinde yönetilir ve bu, bir diğerine başvurgerekebilecek birçok proje içerebilir. Örneğin, bir Python projesi uzantı modülünü uygulayan bir C++ projesine başvurabilir. bu ilişkiyle, Python projesinde hata ayıklamaya başladığınızda Visual Studio otomatik olarak C++ projesini (gerekliyse) oluşturur. (Genel bir tartışma için [Visual Studio çözüm ve projeler](../ide/solutions-and-projects-in-visual-studio.md)bölümüne bakın.)

Visual Studio, var olan bir klasör ağacından bir proje oluşturmak için bir şablon ve temiz ve boş bir proje oluşturmak için bir şablon dahil olmak üzere çeşitli Python proje şablonları sağlar. bkz. bir dizin için [Project şablonları](#project-templates) .

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Visual Studio 2019, Python kodu içeren bir klasörü açmayı ve bu kodu Visual Studio proje ve çözüm dosyaları oluşturmadan çalıştırmayı destekler. Daha fazla bilgi için bkz. [hızlı başlangıç: Python kodunu bir klasörde açma ve çalıştırma](quickstart-05-python-visual-studio-open-folder.md). Ancak, bu bölümde açıklandığı gibi bir proje dosyası kullanmanın avantajları vardır.
::: moniker-end

> [!Tip]
> proje olmadan, tüm Visual Studio sürümleri Python kodu ile iyi çalışır. Örneğin, bir Python dosyasını kendisiyle açabilir ve otomatik olarak tamamlanan, IntelliSense ve hata ayıklamadan (düzenleyicide sağ tıklayıp **hata ayıklamaya başla**' yı seçerek) yararlanabilirsiniz. Bu kod, her zaman varsayılan genel ortamı kullandığından, kodun farklı bir ortam için amaçlanmış olması durumunda yanlış tamamlanmış veya hatalı hatalarla karşılaşabilirsiniz. ayrıca, Visual Studio, tek dosyanın açıldığı klasördeki tüm dosya ve paketleri analiz eder ve bu da önemli ölçüde CPU süresi tüketebilir.
>
> mevcut [dosyalardan proje oluşturma](#create-project-from-existing-files)bölümünde açıklandığı gibi, mevcut koddan bir Visual Studio projesi oluşturmak basit bir işlemdir.

![video derinlemesine bakış için film kamerası simgesi](../install/media/video-icon.png "Nasıl yapılacağını görmek için") [: Python projeleriyle kaynak denetimi kullanın](https://youtu.be/Aq8eqApnugM) (YouTube.com, 8gb 55s).

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Dosya ekleme, başlangıç dosyası atama ve ortamları ayarlama

Uygulamanızı geliştirirken, genellikle projeye farklı türlerde yeni dosyalar eklemeniz gerekir. Bu tür dosyaları eklemek, projeye sağ tıklayıp,   >  eklenecek bir dosyaya gözatabileceğiniz **Varolan öğe** Ekle ' yi seçerek ve   >  çeşitli öğe şablonlarıyla bir iletişim kutusu getiren **Yeni öğe** Ekle ' yi seçerek yapılır. [Öğe şablonları](python-item-templates.md) başvurusunda açıklandığı gibi, Seçenekler boş Python dosyalarını, bir Python sınıfını, birim testini ve Web uygulamalarıyla ilgili çeşitli dosyaları içerir. Visual Studio sürümünüzde nelerin kullanılabildiğini öğrenmek için bu seçenekleri bir test projesiyle keşfedebilirsiniz.

Her Python projesinde, **Çözüm Gezgini** kalın harflerle gösterilen bir atanmış başlangıç dosyası vardır. başlangıç dosyası, hata ayıklamayı başlattığınızda (**F5** veya **hata** ayıklama  >  **başlatma hata ayıklaması**) veya projenizi **etkileşimli** pencerede çalıştırdığınızda (**shıft** + **Alt** + **F5** veya **hata ayıklama** işlemi  >  **Project Python etkileşimli**), çalıştırılan dosyadır. Bunu değiştirmek için, yeni dosyaya sağ tıklayın ve **Başlangıç öğesi olarak ayarla** ' yı seçin (veya Visual Studio eski sürümlerinde **başlangıç dosyası olarak ayarlayın** ).

> [!Tip]
> seçili başlangıç dosyasını bir projeden kaldırır ve yeni bir tane seçmezseniz, projeyi çalıştırmaya çalıştığınızda Visual Studio hangi Python dosyasının başlatılacağını bilmez. bu durumda, Visual Studio 2017 sürüm 15,6 ve sonrasında bir hata gösterilir; önceki sürümler, Python yorumlayıcı çalıştıran bir çıkış penceresi açın veya çıkış penceresinin görüntülendiğini, ancak neredeyse hemen kaybolduğunu görürsünüz. Bu davranışlardan herhangi biriyle karşılaşırsanız, atanmış bir başlangıç dosyasına sahip olup olmadığınızı kontrol edin.
>
> Herhangi bir nedenle çıkış penceresini açık tutmak istiyorsanız projenize sağ tıklayın, **Özellikler**' i seçin, **Hata Ayıkla** sekmesini seçin ve ardından `-i` **yorumlayıcı bağımsız değişkenleri** alanına ekleyin. Bu bağımsız değişken, bir program tamamlandıktan sonra yorumlayıcı 'nın etkileşimli moda geçmesine neden olur, böylece  + çıkmak için CTRL **Z**  >  **ENTER** tuşuna girene kadar pencereyi açık tutun.

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

## <a name="project-templates"></a>Project şablonları

Visual Studio, bir Python projesini sıfırdan ya da mevcut koddan ayarlamanıza olanak sağlayan çeşitli yollar sunar. bir şablon kullanmak için **dosya**  >  **yeni**  >  **Project** menü komutunu seçin veya **Çözüm Gezgini** çözüme sağ tıklayın ve   >  her ikisi de aşağıdaki **yeni Project** iletişim kutusunu seçerek **yeni Project** ekle ' yi seçin. Python 'a özgü şablonları görmek için, "Python" üzerinde arama yapın veya **yüklü**  >  **Python** düğümünü seçin:

![Python şablonlarıyla yeni proje iletişim kutusu](media/projects-new-project-dialog.png)

::: moniker range="<=vs-2017"

aşağıdaki tabloda Visual Studio 2017 ' de kullanılabilen şablonlar özetlenmektedir (tüm şablonlar önceki sürümlerde kullanılamaz):

| Şablon | Description |
| --- | --- |
| [**Mevcut Python kodundan**](#create-project-from-existing-files) | bir klasör yapısındaki mevcut Python kodundan bir Visual Studio projesi oluşturur.  |
| **Python uygulaması** | Tek, boş kaynak dosyası olan yeni bir Python uygulaması için temel bir proje yapısı. Varsayılan olarak, proje varsayılan genel ortamın konsol yorumlayıcısında çalışır ve bu, [farklı bir ortam atayarak](selecting-a-python-environment-for-a-project.md)değiştirebilirsiniz. |
| [**Web projeleri**](python-web-application-project-templates.md) | Şişe, Docgo ve Flask gibi çeşitli çerçeveleri temel alan Web uygulamalarına yönelik projeler. |
| **IronPython uygulaması** | Python uygulama şablonuna benzer ancak varsayılan olarak IronPython 'u kullanarak .net birlikte çalışma ve karışık modda hata ayıklamayı .NET dilleri ile etkinleştirir. |
| **IronPython Silverlight Web sayfası** | Silverlight kullanan bir tarayıcıda çalışan bir IronPython projesi. Uygulamanın Python kodu Web sayfasına betik olarak dahildir. Ortak betik etiketi, bir Silverlight içinde çalışan IronPython 'u Başlatan, Python kodunuzun DOM ile etkileşimde bulunduğu bazı JavaScript kodlarını çeker. |
| **ıronpython Windows Forms uygulaması** | Windows Forms ile kod kullanılarak kullanıcı arabirimi ile ıronpython kullanan bir proje yapısı. Uygulama, konsolu görüntülemeden çalışır. |
| **Arka plan uygulaması (IoT)** | , Cihazlarda arka plan hizmetleri olarak çalışacak Python projelerinin dağıtılmasını destekler. daha fazla bilgi için [Windows ıot Geliştirme Merkezi](https://dev.windows.com/en-us/iot) ziyaret edin. |
| **Python uzantı modülü** | python **yerel geliştirme araçlarını** Visual Studio 2017 veya sonraki bir sürümde (bkz. [yükleme](installing-python-support-in-visual-studio.md)) python iş yüküne yüklediyseniz, bu şablon Visual C++ altında görüntülenir. Bu, [Python Için c++ uzantısı oluşturma](working-with-c-cpp-python-in-visual-studio.md)konusunda açıklananlara benzer bir C++ uzantısı DLL için çekirdek yapı sağlar. |
::: moniker-end

::: moniker range=">=vs-2019"

aşağıdaki tabloda Visual Studio 2019 ' de kullanılabilen şablonlar özetlenmektedir (tüm şablonlar önceki sürümlerde kullanılamaz):

| Şablon | Description |
| --- | --- |
| [**Mevcut Python kodundan**](#create-project-from-existing-files) | bir klasör yapısındaki mevcut Python kodundan bir Visual Studio projesi oluşturur.  |
| **Python uygulaması** | Tek, boş kaynak dosyası olan yeni bir Python uygulaması için temel bir proje yapısı. Varsayılan olarak, proje varsayılan genel ortamın konsol yorumlayıcısında çalışır ve bu, [farklı bir ortam atayarak](selecting-a-python-environment-for-a-project.md)değiştirebilirsiniz. |
| [**Web projeleri**](python-web-application-project-templates.md) | Şişe, Docgo ve Flask gibi çeşitli çerçeveleri temel alan Web uygulamalarına yönelik projeler. |
| **IronPython uygulaması** | Python uygulama şablonuna benzer ancak varsayılan olarak IronPython 'u kullanarak .net birlikte çalışma ve karışık modda hata ayıklamayı .NET dilleri ile etkinleştirir. |
| **IronPython WPF uygulaması** | uygulamanın kullanıcı arabirimi için Windows Presentation Foundation XAML dosyaları ile ıronpython kullanan bir proje yapısı. Visual Studio XAML kullanıcı arabirimi tasarımcısı sağlar, arka plan kod Python 'da yazılabilir ve uygulama bir konsolu görüntülemeden çalışır. |
| **IronPython Silverlight Web sayfası** | Silverlight kullanan bir tarayıcıda çalışan bir IronPython projesi. Uygulamanın Python kodu Web sayfasına betik olarak dahildir. Ortak betik etiketi, bir Silverlight içinde çalışan IronPython 'u Başlatan, Python kodunuzun DOM ile etkileşimde bulunduğu bazı JavaScript kodlarını çeker. |
| **ıronpython Windows Forms uygulaması** | Windows Forms ile kod kullanılarak kullanıcı arabirimi ile ıronpython kullanan bir proje yapısı. Uygulama, konsolu görüntülemeden çalışır. |
| **Arka plan uygulaması (IoT)** | , Cihazlarda arka plan hizmetleri olarak çalışacak Python projelerinin dağıtılmasını destekler. daha fazla bilgi için [Windows ıot Geliştirme Merkezi](https://dev.windows.com/en-us/iot) ziyaret edin. |
| **Python uzantı modülü** | Bu şablon, Visual C++ 2017 veya  sonraki bir sürümüne Python iş yüküyle Python yerel geliştirme araçlarını Visual Studio altında görünür (bkz. [Yükleme).](installing-python-support-in-visual-studio.md) Python için C++ uzantısı oluşturma konusunda açıklananlara benzer şekilde C++ uzantısı DLL'si [için temel yapıyı sağlar.](working-with-c-cpp-python-in-visual-studio.md) |
::: moniker-end

> [!Note]
> Python yorumlanır bir dil olduğundan, Visual Studio'daki Python projeleri, derlenmiş diğer dil projeleri (örneğin C#) gibi tek başına yürütülebilir bir yürütülebilir dosya üretmez. Daha fazla bilgi için bkz. [sorular ve yanıtlar.](overview-of-python-tools-for-visual-studio.md#questions-and-answers)

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Mevcut dosyalardan proje oluşturma

> [!Important]
> Burada açıklanan işlem özgün kaynak dosyaları taşımaz veya kopyalamaz. Bir kopyayla çalışmak için önce klasörü çoğaltabilirsiniz.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Bağlantılı dosyalar

Bağlantılı dosyalar bir projeye getirilen ancak genellikle uygulamanın proje klasörlerinin dışında bulunan dosyalardır. Bunlar, **Çözüm Gezgini** kısayol simgesiyle normal dosyalar olarak görünür: ![ Bağlantılı dosya simgesi](media/projects-linked-file-icon.png)

Bağlantılı dosyalar öğesi kullanılarak *.pyproj* dosyasında `<Compile Include="...">` belirtilir. Bağlı dosyalar dizin yapısının dışında göreli bir yol kullanıyorsa örtülü veya dizin içindeki yolları kullanıyorsa **açık Çözüm Gezgini:**

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Bağlantılı dosyalar aşağıdaki koşullardan herhangi biri altında yoksayılır:

- Bağlantılı dosya, Bağlantı meta verilerini ve Include özniteliğinde belirtilen yolu proje dizininde içerir
- Bağlantılı dosya, proje hiyerarşisinde mevcut olan bir dosyayı yineler
- Bağlantılı dosya Bağlantı meta verilerini içerir ve Bağlantı yolu proje hiyerarşisinin dışında göreli bir yoldur
- Bağlantı yolunun kökü vardır

### <a name="work-with-linked-files"></a>Bağlantılı dosyalarla çalışma

Var olan bir öğeyi bağlantı olarak eklemek için projesinde dosyayı eklemek istediğiniz klasöre sağ tıklayın ve Var Olan Öğeyi **Ekle'yi**  >  **seçin.** Açılan iletişim kutusunda bir dosya seçin ve Ekle **düğmesinin** açılan menüsünden Bağlantı Olarak **Ekle'yi** seçin. Çakışan dosya olmadığının şartıyla, bu komut seçili klasörde bir bağlantı oluşturur. Ancak projede zaten aynı adı veya bu dosyanın bağlantısı olan bir dosya varsa bağlantı eklenmez.

Proje klasörlerini zaten var olan bir dosyaya bağlamayı denemeniz, bağlantı olarak değil normal bir dosya olarak eklenir. Bir dosyayı bir bağlantıya dönüştürmek için Dosya **Farklı**  >  **Kaydet'i** seçerek dosyayı proje hiyerarşisinin dışındaki bir konuma kaydedin; Visual Studio otomatik olarak bir bağlantıya dönüştürür. Benzer şekilde, bir bağlantı, dosyayı proje hiyerarşisinin içinde **bir** yere kaydetmek için  >   Dosya Farklı Kaydet kullanılarak geri dönüştürmek için kullanılabilir.

içinde bağlantılı bir dosyayı **Çözüm Gezgini,** bağlantı taşınır ancak gerçek dosya etkilenmez. Benzer şekilde, bağlantıyı silmek de dosyayı etkilemeden bağlantıyı kaldırır.

Bağlantılı dosyalar yeniden adlandırılamaz.

## <a name="references"></a>Başvurular

Visual Studio projeleri, projelerde ve uzantılarda, uygulamanın Başvurular düğümü **altında** görünen başvurular eklemeyi **Çözüm Gezgini:**

![Python projelerinde uzantı başvuruları](media/projects-extension-references.png)

Uzantı başvuruları genellikle projeler arasındaki bağımlılıkları ifade ediyor ve tasarım zamanında IntelliSense sağlamak veya derleme zamanında bağlantı sağlamak için kullanılır. Python projeleri başvuruları benzer bir şekilde kullanır, ancak Python'ın dinamik yapısı nedeniyle bunlar öncelikli olarak tasarım zamanında gelişmiş IntelliSense sağlamak için kullanılır. Bunlar, ek bağımlılıkları yüklemek Microsoft Azure dağıtım için de kullanılabilir.

### <a name="extension-modules"></a>Uzantı modülleri

*.pyd* dosyasına başvuru, oluşturulan modül için IntelliSense'i sağlar. *Visual Studio.pyd dosyasını* Python yorumlayıcıya yükler ve türlerini ve işlevlerini inceler. Ayrıca, imza yardımı sağlamak için işlevler için belge dizelerini ayrıştırmaya çalışır.

Uzantı modülü diskte herhangi bir zamanda güncelleştirildiğinde, Visual Studio modülünü arka planda yeniden kullanır. Bu eylemin çalışma zamanı davranışı üzerinde hiçbir etkisi yoktur, ancak analiz tamamlandıktan sonra bazı tamamlamalar kullanılamaz.

Modülü içeren klasöre [bir arama](search-paths.md) yolu da eklemeniz gerekir.

### <a name="net-projects"></a>.NET projeleri

IronPython ile çalışırken, IntelliSense'i etkinleştirmek için .NET derlemelerine başvurular ebilirsiniz. Çözümünüzdeki .NET projeleri için Python  projenizin Başvurular düğümüne sağ tıklayın, Başvuru Ekle'yi **seçin,** Projeler **sekmesini** seçin ve istenen projeye göz atın. Ayrı olarak indirdiğiniz DLL'ler için Gözat sekmesini **seçin** ve istediğiniz DLL'ye göz atabilirsiniz.

IronPython'daki başvurular çağrısı yapılana kadar kullanılamaz olduğundan, derlemeye, genellikle kodunuzun başına uygun bir çağrı `clr.AddReference('<AssemblyName>')` `clr.AddReference` eklemeniz gerekir. Örneğin, **Windows'de IronPython Windows Forms** Uygulaması proje şablonu Visual Studio dosyanın en üstünde iki çağrı içerir:

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>WebPI projeleri

WebPI akışı aracılığıyla ek bileşenler yükleyecek şekilde web Microsoft Azure Cloud Services webpi ürün girişlerine başvurular ebilirsiniz. Varsayılan olarak, görüntülenen akış Python'a özgü olup Django, CPython ve diğer temel bileşenleri içerir. Ayrıca, aşağıda gösterildiği gibi kendi akışınızı da seçin. Microsoft Azure'da yayımlarken, bir kurulum görevi başvurulan tüm ürünleri yüklür.

> [!IMPORTANT]
> WebPI projeleri 2017 veya Visual Studio 2019 Visual Studio kullanılamaz.

![WebPI Başvuruları](media/projects-webPI-components.png)
