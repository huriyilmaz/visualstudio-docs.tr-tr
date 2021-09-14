---
title: Python uygulama projelerini yönetme
description: Uygulama Visual Studio dosyalar arasındaki bağımlılıkları ve bir uygulamanın ilişkilerinin karmaşıklığını yönetmeye yöneliktir.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 97caa4f5677ec9357db1a0756f96cd37476ef66c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625335"
---
# <a name="python-projects-in-visual-studio"></a>Visual Studio'da Python projeleri

Python uygulamaları genellikle yalnızca klasörler ve dosyalar kullanılarak tanımlanır, ancak uygulamalar daha büyük hale geldi ve belki de otomatik olarak oluşturulan dosyalar, web uygulamaları için JavaScript gibi daha da karmaşık hale gelir. Bir Visual Studio projesi bu karmaşıklığı yönetmeye yardımcı olur. Proje *(.pyproj* dosyası) projeniz ile ilişkili tüm kaynak ve içerik dosyalarını tanımlar, her dosya için derleme bilgileri içerir, kaynak denetim sistemleriyle tümleştirilen bilgileri sürdürür ve uygulamanızı mantıksal bileşenlerde düzenlemenize yardımcı olur.

![Çözüm Gezgini'de Python projesi](media/projects-solution-explorer.png)

Ayrıca, projeler her zaman bir Visual Studio çözümü içinde yönetilir. Bu çözüm, bir diğerine başvuracak herhangi bir sayıda proje içerebilir. Örneğin, bir Python projesi uzantı modülü uygulayan bir C++ projesine başvurur. Bu ilişkiyle, Visual Studio Python projesinde hata ayıklamaya başlarken C++ projesini (gerekirse) otomatik olarak derler. (Genel bir tartışma için [bkz. Visual Studio.)](../ide/solutions-and-projects-in-visual-studio.md)

Visual Studio, mevcut bir klasör ağacından proje oluşturmak için bir şablon ve temiz, boş bir proje oluşturmak için şablon da dahil olmak üzere bir dizi uygulama yapısını hızlı bir şekilde ayarlamak için çeşitli Python proje şablonları sağlar. Bkz. [Project için](#project-templates) şablon oluşturma.

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Visual Studio 2019, Python kodu içeren bir klasör açılmasını ve proje ve çözüm dosyaları oluşturmadan Visual Studio çalıştırmayı destekler. Daha fazla bilgi için [bkz. Hızlı Başlangıç: Python kodunu bir klasörde açma ve çalıştırma.](quickstart-05-python-visual-studio-open-folder.md) Ancak bu bölümde açıklanan şekilde bir proje dosyası kullanmanın avantajları vardır.
::: moniker-end

> [!Tip]
> Proje olmadan, tüm python Visual Studio Python koduyla iyi çalışır. Örneğin, bir Python dosyasını tek başına açabilir ve otomatik tamamlama, IntelliSense ve hata ayıklamanın keyfini çıkarabilirsiniz (düzenleyicide sağ tıklar ve Hata Ayıklamayı **Başlat'ı seçerek).** Ancak, bu tür kod her zaman varsayılan genel ortamı kullandığından, kod farklı bir ortama yönelikse hatalı tamamlamalar veya hatalar ile karşı karşınız olabilir. Ayrıca Visual Studio, tek dosyanın aç olduğu klasördeki tüm dosyaları ve paketleri analiz eder ve bu da cpu süresine neden olabilir.
>
> Mevcut dosyalardan proje oluşturma konusunda açıklandığı Visual Studio bir proje oluşturmak basit [bir işlemdir.](#create-project-from-existing-files)

![video için film kamerası simgesi](../install/media/video-icon.png "Nasıl yapılacağını görmek için") Derin [Inceleme: Python projeleriyle](https://youtu.be/Aq8eqApnugM) kaynak denetimi kullanın (youtube.com, 8m 55s).

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Dosya ekleme, başlangıç dosyası atama ve ortamları ayarlama

Uygulamayı geliştirirken normalde projeye farklı türlerde yeni dosyalar eklemeniz gerekir. Bu tür dosyaları eklemek için projeye sağ tıklar ve eklemek istediğiniz bir dosyaya göz atmak için Var Olan Öğeyi Ekle'yi veya Yeni Öğe Ekle'yi seçerek yapılır. Bu, çeşitli öğe şablonlarıyla bir iletişim  >     >  kutusu oluşturur. Öğe şablonları [başvurusunda açıklandığı gibi,](python-item-templates.md) seçenekler boş Python dosyalarını, Python sınıfını, birim testini ve web uygulamalarıyla ilgili çeşitli dosyaları içerir. Bu seçenekleri bir test projesiyle keşfedebilirsiniz. Bu seçeneklerle ilgili bilgi edinmek için Visual Studio.

Her Python projesinin atanmış bir başlangıç dosyası vardır ve bu dosya, **Çözüm Gezgini.** Başlangıç dosyası, hata ayıklamaya başlarken (**F5** veya Hata AyıklamaYı Başlat Hata Ayıklama ) veya projenizi Etkileşimli pencerede (  >  **Shift**  Alt F5 veya Python Interactive'de Yürütmede Hata Ayıkla ) Project +  +    >  **dosyasıdır.** Değiştirmek için yeni dosyaya sağ tıklayın ve Başlangıç Öğesi  Olarak Ayarla **(veya** Önceki sürümlerde Başlangıç Dosyası Olarak Ayarla) seçeneğini Visual Studio.

> [!Tip]
> Seçilen başlangıç dosyasını bir projeden kaldırır ve yenisini seçmezsiniz, Visual Studio çalıştırmaya çalışsanız hangi Python dosyasıyla başlayacağınız hakkında bir şey bilmiyorsanız. Bu durumda, Visual Studio 2017 sürüm 15.6 ve sonraki sürümlerde bir hata gösterir; önceki sürümler Python yorumlayıcısını çalıştıran bir çıkış penceresi açar veya çıkış penceresinin görüntü olduğunu ancak hemen kaybolur olduğunu görebilirsiniz. Bu davranışlardan herhangi biri ile karşılaşırsanız, atanmış bir başlangıç dosyanız olup değildir.
>
> Herhangi bir nedenle çıkış penceresini açık tutmak için projenize sağ tıklayın,  Özellikler'i **seçin,** Hata Ayıkla sekmesini seçin ve yorumlayıcı Bağımsız Değişkenleri `-i` **alanına** ekleyin. Bu bağımsız değişken, program tamamlandıktan sonra yorumlayıcının etkileşimli moda geçişe neden olur ve çıkış için **Ctrl** Z Enter tuşlarına basarak +   >  **pencereyi** açık tutun.

::: moniker range="vs-2017"
Yeni bir proje her zaman varsayılan genel Python ortamıyla ilişkilendirilr. Projeyi farklı bir ortamla (sanal ortamlar dahil) ilişkilendirmek için projedeki **Python** Ortamları düğümüne sağ tıklayın, Python Ortamları **Ekle/Kaldır'ı** seçin ve istediğiniz ortamı seçin.
::: moniker-end
::: moniker range=">=vs-2019"
Yeni bir proje her zaman varsayılan genel Python ortamıyla ilişkilendirilr. Projeyi farklı bir ortamla (sanal ortamlar dahil) ilişkilendirmek için projedeki **Python** Ortamları düğümüne sağ tıklayın, Ortam **Ekle..** öğesini seçin ve istediğiniz ortamı seçin. Ayrıca araç çubuğundaki ortamlar açılan denetimiyle projeyi seçerek veya projeye bir tane daha ekleyebilirsiniz.

![Python araç çubuğunda Ortam Ekle komutu](media/environments/environments-toolbar-2019.png)
::: moniker-end

Etkin ortamı değiştirmek için, çalışma alanı içinde istediğiniz ortama sağ Çözüm Gezgini aşağıda **gösterildiği** gibi **Ortamı Etkinleştir'i** seçin. Daha fazla bilgi için [bkz. Proje için ortam seçme.](selecting-a-python-environment-for-a-project.md)

![Python projesi için ortam etkinleştirme](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Project şablonları

Visual Studio, sıfırdan veya mevcut koddan Python projesi ayarlamanın çeşitli yollarını sağlar. Şablon kullanmak için Dosya Yeni Project menü komutunu seçin veya Çözüm Gezgini'de çözüme sağ tıklayın ve her ikisi de aşağıdaki Yeni Project iletişim  >    >   kutusunu    >   **Project** seçin. Python'a özgü şablonları görmek için "Python" araması yazın veya Yüklü  >  **Python düğümünü** seçin:

![Python şablonlarıyla yeni proje iletişim kutusu](media/projects-new-project-dialog.png)

::: moniker range="<=vs-2017"

Aşağıdaki tabloda 2017'de Visual Studio (tüm şablonlar önceki sürümlerde mevcut değildir) özetlenmiştir:

| Şablon | Description |
| --- | --- |
| [**Mevcut Python kodundan**](#create-project-from-existing-files) | Klasör yapısında Visual Studio Python kodundan bir proje oluşturur.  |
| **Python Uygulaması** | Tek, boş bir kaynak dosyası olan yeni bir Python uygulaması için temel bir proje yapısı. Varsayılan olarak, proje varsayılan genel ortamın konsol yorumlayıcıda çalışır ve bunu farklı bir ortam [ataarak değiştirebilirsiniz.](selecting-a-python-environment-for-a-project.md) |
| [**Web projeleri**](python-web-application-project-templates.md) | Bottle, Django ve Flask gibi çeşitli çerçeveleri temel alan web uygulamalarına yönelik projeler. |
| **IronPython Uygulaması** | Python Uygulama şablonuna benzer, ancak .NET birlikte çalışabilirliği ve .NET dilleriyle karma mod hata ayıklamasını etkinleştiren IronPython kullanır. |
| **IronPython WPF Uygulaması** | Uygulamanın kullanıcı arabirimi için XAML dosyalarını Windows Presentation Foundation IronPython kullanan bir proje yapısı. Visual Studio XAML kullanıcı arabirimi tasarımcısı sağlar, python'da arkadan kod yazabilir ve uygulama konsolu görüntülemeden çalışır. |
| **IronPython Silverlight Web Sayfası** | Silverlight kullanarak tarayıcıda çalışan bir IronPython projesi. Uygulamanın Python kodu web sayfasına betik olarak dahil edilir. Ortak betik etiketi, Silverlight'ın içinde çalışan IronPython'ı başlatan ve Python kodunuzun DOM ile etkileşim kuramadığı bazı JavaScript kodunu çeker. |
| **IronPython Windows Forms Uygulaması** | Windows Forms ile kod kullanılarak oluşturulan kullanıcı arabirimi ile IronPython kullanan Windows. Uygulama bir konsol görüntülemeden çalışır. |
| **Arka Plan Uygulaması (IoT)** | Cihazlarda arka plan hizmetleri olarak çalıştırmak için Python projelerini dağıtmayı destekler. Daha fazla [bilgi Windows IoT Geliştirme Merkezi IoT](https://dev.windows.com/en-us/iot) hizmetleri sitesini ziyaret edin. |
| **Python Uzantısı Modülü** | Bu şablon Visual C++ 2017 veya sonraki  bir sürümüne Python iş yüküyle Python yerel geliştirme araçlarını yüklemiş Visual Studio görünür (bkz. [Yükleme).](installing-python-support-in-visual-studio.md) Python için C++ uzantısı oluşturma konusunda açıklananlara benzer şekilde C++ uzantısı DLL'si [için temel yapıyı sağlar.](working-with-c-cpp-python-in-visual-studio.md) |
::: moniker-end

::: moniker range=">=vs-2019"

Aşağıdaki tabloda 2019'da Visual Studio (tüm şablonlar önceki sürümlerde mevcut değildir) özetlenmiştir:

| Şablon | Description |
| --- | --- |
| [**Mevcut Python kodundan**](#create-project-from-existing-files) | Klasör yapısında Visual Studio Python kodundan bir proje oluşturur.  |
| **Python Uygulaması** | Tek, boş bir kaynak dosyası olan yeni bir Python uygulaması için temel bir proje yapısı. Varsayılan olarak, proje varsayılan genel ortamın konsol yorumlayıcıda çalışır ve bunu farklı bir ortam [ataarak değiştirebilirsiniz.](selecting-a-python-environment-for-a-project.md) |
| [**Web projeleri**](python-web-application-project-templates.md) | Bottle, Django ve Flask gibi çeşitli çerçeveleri temel alan web uygulamalarına yönelik projeler. |
| **IronPython Uygulaması** | Python Uygulama şablonuna benzer, ancak .NET birlikte çalışabilirliği ve .NET dilleriyle karma mod hata ayıklamasını etkinleştiren IronPython kullanır. |
| **IronPython WPF Uygulaması** | Uygulamanın kullanıcı arabirimi için XAML dosyalarını Windows Presentation Foundation IronPython kullanan bir proje yapısı. Visual Studio XAML kullanıcı arabirimi tasarımcısı sağlar, python'da arkadan kod yazabilir ve uygulama konsolu görüntülemeden çalışır. |
| **IronPython Silverlight Web Sayfası** | Silverlight kullanarak tarayıcıda çalışan bir IronPython projesi. Uygulamanın Python kodu web sayfasına betik olarak dahil edilir. Ortak betik etiketi, Silverlight'ın içinde çalışan IronPython'ı başlatan ve Python kodunuzun DOM ile etkileşim kuramadığı bazı JavaScript kodunu çeker. |
| **IronPython Windows Forms Uygulaması** | Windows Forms ile kod kullanılarak oluşturulan kullanıcı arabirimi ile IronPython kullanan Windows. Uygulama bir konsol görüntülemeden çalışır. |
| **Arka Plan Uygulaması (IoT)** | , Cihazlarda arka plan hizmetleri olarak çalışacak Python projelerinin dağıtılmasını destekler. daha fazla bilgi için [Windows ıot Geliştirme Merkezi](https://dev.windows.com/en-us/iot) ziyaret edin. |
| **Python uzantı modülü** | python **yerel geliştirme araçlarını** Visual Studio 2017 veya sonraki bir sürümde (bkz. [yükleme](installing-python-support-in-visual-studio.md)) python iş yüküne yüklediyseniz, bu şablon Visual C++ altında görüntülenir. Bu, [Python Için c++ uzantısı oluşturma](working-with-c-cpp-python-in-visual-studio.md)konusunda açıklananlara benzer bir C++ uzantısı DLL için çekirdek yapı sağlar. |
::: moniker-end

> [!Note]
> python, yorumlanan bir dil olduğundan, Visual Studio ' deki Python projeleri, diğer derlenmiş dil projeleri gibi tek başına yürütülebilir dosya oluşturmaz (örneğin, C#). Daha fazla bilgi için bkz. [sorular ve yanıtlar](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Mevcut dosyalardan bir proje oluşturma

> [!Important]
> Burada açıklanan işlem özgün kaynak dosyalarını taşımaz veya kopyalamaz. Bir kopyalama ile çalışmak istiyorsanız önce klasörü çoğaltın.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Bağlı dosyalar

Bağlantılı dosyalar bir projeye getirilen ancak genellikle uygulamanın proje klasörlerinin dışında bulunan dosyalardır. Bunlar, bir kaplama kısayolu simgesi olan normal dosyalar olarak **Çözüm Gezgini** görünürler: ![ bağlı dosya simgesi](media/projects-linked-file-icon.png)

Bağlantılı dosyalar *. pyproj* dosyasında öğesi kullanılarak belirtilir `<Compile Include="...">` . Bağlı dosyalar, dizin yapısının dışında göreli bir yol kullanıyorsa veya **Çözüm Gezgini** içinde yollar kullandıklarında açık bir şekilde yapılır:

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

Var olan bir öğeyi bağlantı olarak eklemek için, projede dosyayı eklemek istediğiniz klasörü sağ tıklatın ve ardından   >  **Varolan öğe** Ekle ' yi seçin. Görüntülenen iletişim kutusunda bir dosya seçin ve **Ekle** düğmesine açılan listeden **bağlantı olarak ekle** ' yi seçin. Çakışan dosya olmadığından, bu komut seçili klasörde bir bağlantı oluşturur. Ancak, aynı ada sahip bir dosya zaten varsa veya projede zaten bu dosya için bir bağlantı varsa bağlantı eklenmez.

Proje klasörlerinde zaten bulunan bir dosyaya bağlantı kurmayı denerseniz, bir bağlantı olarak değil, normal bir dosya olarak eklenir. Dosyayı bir bağlantıya dönüştürmek **için dosya**  >  **farklı kaydet** ' i seçerek dosyayı proje hiyerarşisi dışında bir konuma kaydedin; Visual Studio otomatik olarak bağlantıya dönüştürülür. Benzer şekilde, dosyayı   >  Proje hiyerarşisinde bir yere kaydetmek için dosya **farklı kaydet** kullanılarak bir bağlantı geri dönüştürülebilir.

Bağlı bir dosyayı **Çözüm Gezgini** taşırsanız bağlantı taşınır ancak gerçek dosya etkilenmez. Benzer şekilde, bir bağlantıyı silme, dosyayı etkilemeden bağlantıyı kaldırır.

Bağlantılı dosyalar yeniden adlandırılamaz.

## <a name="references"></a>Başvurular

Visual Studio projeler, **Çözüm Gezgini** içindeki **başvurular** düğümü altında görünen projelere ve uzantılara başvuru eklemeyi destekler:

![Python projelerindeki uzantı başvuruları](media/projects-extension-references.png)

Uzantı başvuruları genellikle projeler arasındaki bağımlılıkları gösterir ve tasarım zamanında IntelliSense sağlamak veya derleme zamanında bağlamak için kullanılır. Python projeleri, başvuruları benzer bir biçimde kullanır, ancak Python 'un dinamik doğası gereği, gelişmiş IntelliSense sağlamak için öncelikle tasarım zamanında kullanılır. ayrıca, ek bağımlılıklar yüklemek üzere Microsoft Azure dağıtım için de kullanılabilir.

### <a name="extension-modules"></a>Uzantı modülleri

*. PYD* dosyası başvurusu, oluşturulan modül için IntelliSense 'i sağlar. Visual Studio, *. pyd* dosyasını Python yorumlayıcı 'ya yükler ve bunların türlerini ve işlevlerini gözlemleyip. Ayrıca, imza yardımı sağlamak için işlevler için belge dizelerini ayrıştırmaya çalışır.

herhangi bir zamanda uzantı modülü diskte güncelleştirilirse, Visual Studio arka planda modülü yeniden analiz eder. Bu eylemin çalışma zamanı davranışı üzerinde hiçbir etkisi yoktur, ancak bazı tamamlamalar analiz tamamlanana kadar kullanılamaz.

Modülün bulunduğu klasöre bir [arama yolu](search-paths.md) da eklemeniz gerekebilir.

### <a name="net-projects"></a>.NET projeleri

IronPython ile çalışırken, IntelliSense 'i etkinleştirmek için .NET derlemelerine başvurular ekleyebilirsiniz. Çözümünüzdeki .NET projeleri için, Python projenizde **Başvurular** düğümüne sağ tıklayın, **Başvuru Ekle**' yi seçin, **Projeler** sekmesini seçin ve istediğiniz projeye gidin. Ayrı olarak indirdiğiniz dll 'Ler için, bunun yerine, **Gözden** geçirme sekmesini seçin ve istenen dll 'ye gidin.

Bir çağrısı yapılıncaya kadar IronPython içindeki başvurular kullanılamadığından `clr.AddReference('<AssemblyName>')` , `clr.AddReference` genellikle kodunuzun başlangıcında derlemeye uygun bir çağrı eklemeniz gerekir. örneğin, Visual Studio içindeki **ıronpython Windows Forms uygulama** projesi şablonu tarafından oluşturulan kod, dosyanın en üstünde iki çağrı içerir:

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>WebPI projeleri

webpı akışı aracılığıyla ek bileşenler yükleyebileceğiniz Microsoft Azure Cloud Services dağıtım için webpı ürün girişlerine başvurular ekleyebilirsiniz. Varsayılan olarak, belirtilen akış Python 'a özgüdür ve Docgo, Cpyıthon ve diğer çekirdek bileşenleri içerir. Ayrıca, aşağıda gösterildiği gibi kendi akışınızı de seçebilirsiniz. Microsoft Azure yayımlandığında, bir kurulum görevi başvurulan ürünlerin tümünü kurar.

> [!IMPORTANT]
> webpı projeleri Visual Studio 2017 veya Visual Studio 2019 ' de kullanılamaz.

![WebPI başvuruları](media/projects-webPI-components.png)
