---
title: Python uygulama projelerini yönetme
description: Visual Studio'daki projeler, dosyalar arasındaki bağımlılıkları ve bir uygulamadaki ilişkilerin karmaşıklığını yönetir.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d50cbfbd517073544ebd172627d24bd7c3878fa5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302814"
---
# <a name="python-projects-in-visual-studio"></a>Visual Studio'da Python projeleri

Python uygulamaları genellikle yalnızca klasörler ve dosyalar kullanılarak tanımlanır, ancak uygulamalar büyüdükçe ve belki de otomatik olarak oluşturulan dosyaları, web uygulamaları için JavaScript'i ve benzeri öğeleri içerdince bu yapı karmaşık hale gelebilir. Visual Studio projesi bu karmaşıklığı yönetmenize yardımcı olur. Proje *(.pyproj* dosyası) projenizle ilişkili tüm kaynak ve içerik dosyalarını tanımlar, her dosya için yapı bilgileri içerir, kaynak denetim sistemleriyle tümleştirmek için bilgileri korur ve uygulamanızı mantıksal bileşenler halinde düzenlemenize yardımcı olur.

![Solution Explorer'da Python projesi](media/projects-solution-explorer.png)

Buna ek olarak, projeler her zaman bir visual studio *çözümü*içinde yönetilir , hangi birbirlerine referans olabilir projeler herhangi bir sayı içerebilir. Örneğin, bir Python projesi, bir uzantı modülü uygulayan bir C++ projesine başvuruyapabilir. Bu ilişkiyle Visual Studio, Python projesini hata ayıklamaya başladığınızda C++ projesini (gerekirse) otomatik olarak oluşturur. (Genel bir tartışma için [Visual Studio'daki Çözümler ve projelere](../ide/solutions-and-projects-in-visual-studio.md)bakın.)

Visual Studio, varolan bir klasör ağacından proje oluşturmak için bir şablon ve temiz, boş bir proje oluşturmak için şablon da dahil olmak üzere bir dizi uygulama yapısını hızlı bir şekilde ayarlamak için çeşitli Python proje şablonları sağlar. Dizin için [Proje şablonlarına](#project-templates) bakın.

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Visual Studio 2019, Python kodu içeren bir klasör açmayı ve Visual Studio proje ve çözüm dosyaları oluşturmadan bu kodu çalıştırmayı destekler. Daha fazla bilgi için [Bkz. Quickstart: Python kodunu bir klasörde açın ve çalıştırın.](quickstart-05-python-visual-studio-open-folder.md) Ancak, bu bölümde açıklandığı gibi, bir proje dosyası kullanmanın yararları vardır.
::: moniker-end

> [!Tip]
> Bir proje olmadan, Visual Studio'nun tüm sürümleri Python koduyla iyi çalışır. Örneğin, python dosyasını tek başına açabilir ve otomatik tamamlama, IntelliSense ve hata ayıklamanın keyfini çıkarabilir (editöre sağ tıklayıp **Hata Ayıklama ile Başlat'ı**seçerek). Ancak, bu tür kod her zaman varsayılan genel ortamı kullandığından, kod farklı bir ortam için yapılmışsa yanlış tamamlamalar veya hatalar görebilirsiniz. Ayrıca, Visual Studio tek dosyanın açıldığı klasördeki tüm dosyaları ve paketleri analiz eder ve bu da önemli bir CPU süresi tüketebilir.
>
> [Varolan dosyalardan proje oluştur'da](#create-project-from-existing-files)açıklandığı gibi, varolan koddan bir Visual Studio projesi oluşturmak basit bir konudur.

|   |   |
|---|---|
| ![video için film kamera simgesi](../install/media/video-icon.png "Nasıl yapılacağını görmek için") | [Derin Dalış: Python projeleri (youtube.com,](https://youtu.be/Aq8eqApnugM) 8m 55s) ile kaynak denetimini kullanın. |

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Dosya ekleme, başlangıç dosyası atama ve ortamları ayarlama

Uygulamanızı geliştirirken, genellikle projeye farklı türde yeni dosyalar eklemeniz gerekir. Bu tür dosyaların eklenmesi, projeyi sağ tıklayarak ve eklemek için bir dosya için göz attığınız > **Varolan** Öğeekle'yi **seçerek**veya çeşitli öğe şablonlarıyla bir iletişim kurarak**Yeni Öğe** **Ekle'yi** > seçerek yapılır. [Öğe şablonları](python-item-templates.md) başvurusu açıklandığı gibi, seçenekler boş Python dosyaları, python sınıfı, bir birim testi ve web uygulamaları ile ilgili çeşitli dosyaları içerir. Visual Studio sürümünizde nelerin mevcut olduğunu öğrenmek için bir test projesi yle bu seçenekleri keşfedebilirsiniz.

Her Python projesinde **Solution Explorer'da**boldface olarak gösterilen atanmış bir başlatma dosyası vardır. Başlangıç dosyası, hata ayıklamaya **(F5** veya **Hata** > Ayıklama**Başlatma Hata Ayıklama)** veya Projenizi **Etkileşimli** pencerede çalıştırdığınızda **(Python Interactive'de****Shift**+**Alt**+**F5** veya Hata **Ayıklama** > Projesi) çalıştırdığınızda çalışan dosyadır. Değiştirmek için yeni dosyayı sağ tıklatın ve **Başlangıç Öğesi olarak Ayarla'yı** (veya Visual Studio'nun eski sürümlerinde **Başlangıç Dosyası Olarak Ayarla'yı)** seçin.

> [!Tip]
> Seçili başlangıç dosyasını bir projeden kaldırır ve yeni sini seçmezseniz, Visual Studio projeyi çalıştırmayı denediğinizde hangi Python dosyasıyla başlayacağını bilmez. Bu durumda Visual Studio 2017 sürüm 15.6 ve daha sonra bir hata gösterir; Önceki sürümler, Python yorumlayıcısı çalışırken bir çıkış penceresi açar veya çıkış penceresinin göründüğünü ancak hemen kaybolduğunu görürsünüz. Bu davranışlardan herhangi biri ile karşılaşırsanız, atanmış bir başlangıç dosyanız olup olmadığını denetleyin.
>
> Çıktı penceresini herhangi bir nedenle açık tutmak istiyorsanız, projenizi sağ tıklatın, **Özellikler'i** `-i` seçin, Hata **Ayıklama** sekmesini seçin ve ardından **Yorumlayıcı Bağımsız Değişkenler** alanına ekleyin. Bu bağımsız değişken, bir program tamamlandıktan sonra yorumlayıcının etkileşimli moda geçmesine neden olur ve böylece çıkmak için **Ctrl**+**Z** > **Girin'i** girene kadar pencereyi açık tutar.

::: moniker range="vs-2017"
Yeni bir proje her zaman varsayılan genel Python ortamı ile ilişkilidir. Projeyi farklı bir ortamla (sanal ortamlar dahil) ilişkilendirmek için projedeki **Python Ortamları** düğümüne sağ tıklayın, **Python Ortamları Ekle/Kaldır'ı**seçin ve istediğiniz leri seçin.
::: moniker-end
::: moniker range=">=vs-2019"
Yeni bir proje her zaman varsayılan genel Python ortamı ile ilişkilidir. Projeyi farklı bir ortamla (sanal ortamlar dahil) ilişkilendirmek için, projedeki **Python Ortamları** düğümüne sağ tıklayın, **Çevre Ekle'yi**seçin ve istediğiniz leri seçin. Ayrıca, araç çubuğundaki ortam açılır denetimi, projeyi seçmek ve ortama eklemek veya projeye başka bir tane eklemek için de kullanabilirsiniz.

![Python araç çubuğuna Çevre komutu ekleme](media/environments/environments-toolbar-2019.png)
::: moniker-end

Etkin ortamı değiştirmek için **Çözüm Gezgini'nde** istenen ortamı sağ tıklatın ve aşağıda gösterildiği gibi **Ortamı Etkinleştir'i** seçin. Daha fazla bilgi için [bkz.](selecting-a-python-environment-for-a-project.md)

![Python projesi için ortamı etkinleştirme](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Proje şablonları

Visual Studio, sıfırdan veya varolan koddan bir Python projesi ayarlamanın çeşitli yollarını sunar. Şablon kullanmak için**Yeni** > **Proje** **Dosyası** > dosyası komutunu seçin veya **Çözüm Gezgini'ndeki** çözüme sağ tıklayın ve her ikisi de aşağıdaki **Yeni Proje** iletişim kutusunu oluşturan Yeni**Proje** **Ekle'yi** > seçin. Python'a özgü şablonları görmek için "Python"da arama yapın veya **Yüklü** > **Python** düğümünü seçin:

![Python şablonları ile yeni proje iletişim kutusu](media/projects-new-project-dialog.png)

Aşağıdaki tablo, Visual Studio 2017 ve sonraki sürümlerde bulunan şablonları özetler (tüm şablonlar önceki tüm sürümlerde bulunmaz):

| Şablon | Açıklama |
| --- | --- |
| [**Varolan Python kodundan**](#create-project-from-existing-files) | Klasör yapısındaki varolan Python kodundan visual studio projesi oluşturur.  |
| **Python Uygulaması** | Tek, boş kaynak dosyası olan yeni bir Python uygulaması için temel proje yapısı. Varsayılan olarak, proje [farklı bir ortam atayarak](selecting-a-python-environment-for-a-project.md)değiştirebileceğiniz varsayılan genel ortamın konsol yorumlayıcısında çalışır. |
| [**Azure bulut hizmeti**](python-azure-cloud-service-project-template.md) | Python'da yazılmış bir Azure bulut hizmeti projesi. |
| [**Web projeleri**](python-web-application-project-templates.md) | Şişe, Django ve Flask gibi çeşitli çerçevelere dayalı web uygulamaları için projeler. |
| **IronPython Uygulaması** | Python Application şablonuna benzer, ancak ironPython varsayılan olarak .NET interop ve karma mod hata ayıklama .NET dilleri ile etkinleştirme kullanır. |
| **IronPython WPF Uygulaması** | Uygulamanın kullanıcı arabirimi için Windows Presentation Foundation XAML dosyaları ile IronPython kullanan bir proje yapısı. Visual Studio bir XAML Kullanıcı Bira sıcağı tasarımcısı sağlar, kod arkası Python'da yazılabilir ve uygulama konsol görüntülemeden çalışır. |
| **IronPython Silverlight Web Sayfası** | Silverlight kullanarak bir tarayıcıda çalışan bir IronPython projesi. Uygulamanın Python kodu web sayfasında komut dosyası olarak yer aldı. Bir ortak komut dosyası etiketi, Silverlight'ın içinde çalışan IronPython'u ortaya çıkaran ve Python kodunun DOM ile etkileşimkurabileceği bazı JavaScript kodunu aşağı çeker. |
| **IronPython Windows Formlar Uygulaması** | Windows Formlar ile kod kullanılarak oluşturulan UI ile IronPython kullanarak bir proje yapısı. Uygulama bir konsol görüntülemeden çalışır. |
| **Arka Plan Uygulaması (IoT)** | Python projelerinin aygıtlarda arka plan hizmeti olarak çalıştırılmasını destekler. Daha fazla bilgi için [Windows IoT Geliştirme Merkezi'ni](https://dev.windows.com/en-us/iot) ziyaret edin. |
| **Python Uzantı Modülü** | Bu şablon, Visual Studio 2017 veya sonraki yıllarda Python iş yüküyle **Python yerel geliştirme araçlarını** yüklediyseniz Visual C++ altında görünür (bkz. [Yükleme).](installing-python-support-in-visual-studio.md) Python için [C++ uzantısı oluştur'da](working-with-c-cpp-python-in-visual-studio.md)açıklanana benzer bir C++ uzantısı DLL için çekirdek yapısını sağlar. |

> [!Note]
> Python yorumlanmış bir dil olduğundan, Visual Studio'daki Python projeleri diğer derlenmiş dil projeleri gibi tek başına yürütülebilir bir dil üretmez (örneğin C#. Daha fazla bilgi [için, sorular ve yanıtlar](overview-of-python-tools-for-visual-studio.md#questions-and-answers)bakın.

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Varolan dosyalardan proje oluşturma

> [!Important]
> Burada açıklanan işlem özgün kaynak dosyalarını hareket ettirmez veya kopyalamaz. Bir kopyayla çalışmak istiyorsanız, önce klasörü çoğaltın.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Bağlantılı dosyalar

Bağlantılı dosyalar, bir projeye getirilen ancak genellikle uygulamanın proje klasörlerinin dışında ikamet eden dosyalardır. **Bunlar, solution** explorer'da, üzerine konmuş kısayol simgesi olan normal dosyalar olarak görünür: ![Bağlantılı dosya simgesi](media/projects-linked-file-icon.png)

Bağlantılı dosyalar `<Compile Include="...">` öğe kullanılarak *.pyproj* dosyasında belirtilir. Bağlı dosyalar dizin yapısının dışında göreli bir yol kullanıyorsa örtülüdür veya **Çözüm Gezgini**içindeki yolları kullanıyorsa açıktır:

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Bağlantılı dosyalar aşağıdaki koşullardan herhangi biri altında yoksayılır:

- Bağlantılı dosya, Bağlantı meta verilerini ve Proje dizinindeki Ekle özniteliği yaşamlarında belirtilen yolu içerir
- Bağlı dosya, proje hiyerarşisi içinde bulunan bir dosyayı yineler
- Bağlantılı dosya Bağlantı meta verileri içerir ve Bağlantı yolu proje hiyerarşisi dışında göreceli bir yoldur
- Bağlantı yolu köklü

### <a name="work-with-linked-files"></a>Bağlantılı dosyalarla çalışma

Varolan bir öğeyi bağlantı olarak eklemek için, dosyayı eklemek istediğiniz projedeki klasöre sağ tıklayın ve ardından**Varolan Öğe** **Ekle'yi** > seçin. Görünen iletişim kutusunda, bir dosya seçin ve **Ekle** düğmesinin açılır tarafından **Bağlantı Olarak Ekle'yi** seçin. Çakışan dosya olmaması koşuluyla, bu komut seçili klasörde bir bağlantı oluşturur. Ancak, aynı ada sahip bir dosya veya projede zaten bu dosyaya bağlantı varsa bağlantı eklenmez.

Proje klasörlerinde zaten var olan bir dosyaya bağlanmayı denerseniz, bu dosya bağlantı olarak değil, normal bir dosya olarak eklenir. Bir dosyayı bir bağlantıya dönüştürmek için, dosyayı proje hiyerarşisi dışındaki bir konuma kaydetmek için **Dosya** > **Kaydet'i** seçin; Visual Studio otomatik olarak bir bağlantıya dönüştürür. Benzer şekilde, dosyayı proje hiyerarşisi içinde bir yere kaydetmek için **Dosya** > **Kaydet'i** kullanılarak bir bağlantı geri dönüştürülebilir.

**Çözüm Gezgini'nde**bağlantılı bir dosyayı taşırsanız, bağlantı taşınır, ancak gerçek dosya etkilenmez. Benzer şekilde, bir bağlantıyı siler dosyayı etkilemeden bağlantıyı kaldırır.

Bağlantılı dosyalar yeniden adlandırılamaz.

## <a name="references"></a>Başvurular

Visual Studio projeleri, **Solution Explorer'daki** **Başvuru** düğümü altında görünen projelere ve uzantılara referans eklemeyi destekler:

![Python projelerinde uzantı başvuruları](media/projects-extension-references.png)

Uzantı başvuruları genellikle projeler arasındaki bağımlılıkları gösterir ve IntelliSense'i tasarım zamanında veya derleme zamanında bağlamak için kullanılır. Python projeleri benzer bir şekilde referansları kullanır, ancak Python'un dinamik doğası nedeniyle öncelikle tasarım zamanında geliştirilmiş IntelliSense sağlamak için kullanılır. Ayrıca, ek bağımlılıkları yüklemek için Microsoft Azure'a dağıtım için de kullanılabilirler.

### <a name="extension-modules"></a>Uzatma modülleri

*.pyd* dosyasına yapılan bir başvuru, oluşturulan modül için IntelliSense'e olanak sağlar. Visual Studio *.pyd* dosyasını Python tercümanına yükler ve türlerini ve işlevlerini içe dönük olarak görür. Ayrıca, imza yardımı sağlamak için işlevler için doküman dizelerini ayrıştamayı da dener.

Uzatma modülü herhangi bir zamanda diskte güncelleştirilirse, Visual Studio arka plandaki modülü yeniden analiz eder. Bu eylemin çalışma zamanı davranışı üzerinde hiçbir etkisi yoktur, ancak çözümleme tamamlanana kadar bazı tamamlamalar kullanılamaz.

Ayrıca modülü içeren klasöre bir [arama yolu](search-paths.md) eklemeniz gerekebilir.

### <a name="net-projects"></a>.NET projeleri

IronPython ile çalışırken, IntelliSense'i etkinleştirmek için .NET derlemelerine göndermeler ekleyebilirsiniz. Çözümünüzdeki .NET projeleri için Python projenizdeki **Başvuru** düğümüne sağ tıklayın, **Referans Ekle'yi**seçin, **Projeler** sekmesini seçin ve istediğiniz projeye göz atın. Ayrı olarak indirdiğiniz DL'ler için **Gözat** sekmesini seçin ve istediğiniz DLL'ye göz atın.

IronPython'daki başvurular çağrı yapılana `clr.AddReference('<AssemblyName>')` kadar kullanılamadığından, genellikle kodunuzun başında derlemeye uygun `clr.AddReference` bir çağrı eklemeniz gerekir. Örneğin, Visual Studio'daki **IronPython Windows Forms Application** proje şablonu tarafından oluşturulan kod, dosyanın üst kısmında iki çağrı içerir:

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>WebPI projeleri

WebPI akışı aracılığıyla ek bileşenler yükleyebileceğiniz Microsoft Azure Bulut Hizmetleri'ne dağıtım için WebPI ürün girişlerine başvurular ekleyebilirsiniz. Varsayılan olarak, görüntülenen besleme Python'a özgüdür ve Django, CPython ve diğer temel bileşenleri içerir. Ayrıca aşağıda gösterildiği gibi kendi akışı nızı da seçebilirsiniz. Microsoft Azure'da yayımlama yaparken, bir kurulum görevi başvurulan tüm ürünleri yükler.

> [!IMPORTANT]
> WebPI projeleri Visual Studio 2017 veya Visual Studio 2019'da kullanılamaz.

![WebPI Referansları](media/projects-webPI-components.png)
