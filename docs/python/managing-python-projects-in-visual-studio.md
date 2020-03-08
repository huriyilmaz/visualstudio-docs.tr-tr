---
title: Python uygulaması projeleri yönetme
description: Visual Studio projeleri, dosyaları ve uygulama ilişkilerde karmaşıklığını arasındaki bağımlılıkları yönetin.
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409045"
---
# <a name="python-projects-in-visual-studio"></a>Visual Studio'da Python projeleri

Python uygulamaları, genellikle yalnızca klasörleri ve dosyaları kullanılarak tanımlanır, ancak uygulamalar daha büyük hale gelir ve belki de JavaScript web uygulamaları için otomatik olarak oluşturulan dosyaları içeren vb. gibi bu yapı karmaşık hale gelebilir. Visual Studio projesi Bu karmaşıklığı yönetmenize yardımcı olur. Proje ( *. pyproj* dosyası), projenizle ilişkili tüm kaynak ve içerik dosyalarını tanımlar, her bir dosya için derleme bilgilerini içerir, kaynak denetimi sistemleriyle tümleştirilecek bilgileri saklar ve uygulamanızı mantıksal bileşenlerde düzenlemenize yardımcı olur.

![Çözüm Gezgini'nde proje Python](media/projects-solution-explorer.png)

Ayrıca, projeler her zaman bir Visual Studio *çözümü*içinde yönetilir ve bu, bir diğerine başvurgerekebilecek birçok proje içerebilir. Örneğin, bir Python projesi bir uzantı modülü uygulayan bir C++ projesi başvurabilir. Python projesi hata ayıklamaya başladığınızda bu ilişki ile Visual Studio C++ projesi (gerekirse) otomatik olarak oluşturur. (Genel bir tartışma için bkz. [Visual Studio 'Da çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md).)

Visual Studio, çeşitli uygulama yapılarının bir projeden varolan bir klasör ağacı oluşturmak için bir şablon ve temiz, boş bir proje oluşturmak için bir şablon dahil olmak üzere, bir numarası hızlı bir şekilde ayarlamak için Python proje şablonları sağlar. Bkz. bir dizin için [Proje şablonları](#project-templates) .

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Visual Studio 2019, Python kodu içeren bir klasörün açılmasını destekler ve Visual Studio proje ve çözüm dosyaları oluşturmadan kodu çalıştırır. Daha fazla bilgi için bkz. [hızlı başlangıç: Python kodunu bir klasörde açma ve çalıştırma](quickstart-05-python-visual-studio-open-folder.md). Ancak, bu bölümde açıklandığı gibi bir proje dosyası kullanmanın avantajları vardır.
::: moniker-end

> [!Tip]
> Proje olmadan, Visual Studio 'nun tüm sürümleri Python kodu ile iyi çalışır. Örneğin, bir Python dosyasını kendisiyle açabilir ve otomatik olarak tamamlanan, IntelliSense ve hata ayıklamadan (düzenleyicide sağ tıklayıp **hata ayıklamaya başla**' yı seçerek) yararlanabilirsiniz. Bu tür kod her zaman varsayılan genel ortam kullandığından, kodu farklı bir ortam için tasarlanmıştır ancak yanlış tamamlama veya hataları görebilirsiniz. Ayrıca, Visual Studio, tüm dosyaları ve paketleri içinden tek dosya açıldığında, klasörde önemli miktarda CPU süresi kullanabilecek analiz eder.
>
> Mevcut [dosyalardan bir proje oluşturma](#create-project-from-existing-files)bölümünde açıklandığı gibi, mevcut koddan bir Visual Studio projesi oluşturmanın basit bir önemi vardır.

|   |   |
|---|---|
| ![video için film kamerası simgesi](../install/media/video-icon.png "Video izleyin") | [Derin bakış: Python projeleriyle kaynak denetimi kullanın](https://youtu.be/Aq8eqApnugM) (YouTube.com, 8gb 55s). |

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>Dosya ekleme, bir başlangıç dosyası atayın ve ortamlarını ayarlama

Uygulamanızı geliştirirken, genellikle farklı türdeki yeni dosyalar projeye eklemeniz gerekir. Bu tür dosyaları eklemek, projeye sağ tıklayıp > **Ekle** ' yi seçerek bir dosya **eklemek veya eklemek** üzere bir dosyaya gözatmanıza veya > **Yeni öğe**eklemeye kadar çok sayıda öğe şablonu Içeren bir iletişim kutusu getiren **var olan** öğe Ekle ' yi seçmektir. [Öğe şablonları](python-item-templates.md) başvurusunda açıklandığı gibi, Seçenekler boş Python dosyalarını, bir Python sınıfını, birim testini ve Web uygulamalarıyla ilgili çeşitli dosyaları içerir. Hangi Visual Studio sürümünde kullanılabilir olduğunu öğrenmek için bu seçenekler bir test projesi ile keşfedebilirsiniz.

Her Python projesinde, **Çözüm Gezgini**kalın harflerle gösterilen bir atanmış başlangıç dosyası vardır. Başlangıç dosyası, hata ayıklamayı başlattığınızda (**F5** veya **Hata Ayıkla** > **başlangıç hata ayıklaması**) veya projenizi **etkileşimli** pencerede çalıştırdığınızda (**SHIFT**+**alt**+**F5** veya **hata ayıklama** > **Python etkileşimli 'de projeyi yürütmek**için) çalıştırılan dosyadır. Bunu değiştirmek için, yeni dosyaya sağ tıklayın ve **Başlangıç öğesi olarak ayarla** ' yı (veya Visual Studio 'nun eski sürümlerinde **başlangıç dosyası olarak ayarla** ) seçin.

> [!Tip]
> Seçili başlangıç dosyasını bir projeden kaldırır ve yeni bir tane seçmezseniz, projeyi çalıştırmaya çalıştığınızda Visual Studio hangi Python dosyasının başlatılacağını bilmez. Bu durumda, Visual Studio 2017 sürüm 15.6 ve daha sonra bir hata gösterir. önceki sürümlerinde çalışan Python yorumlayıcısı ile ya da bir çıktı penceresini açın veya çıkış penceresine bakın görünür ancak hemen kaybolur. Bu davranışların karşılaşırsanız, bir atanan başlangıç dosyası olduğunu denetleyin.
>
> Herhangi bir nedenle çıkış penceresini açık tutmak istiyorsanız projenize sağ tıklayın, **Özellikler**' i seçin, **Hata Ayıkla** sekmesini seçin ve sonra **yorumlayıcı bağımsız değişkenleri** alanına `-i` ekleyin. Bu bağımsız değişken, bir program tamamlandıktan sonra yorumlayıcının etkileşimli moda geçmesine neden olur ve ardından CTRL+**Z** tuşuna girene kadar pencereyi açık tutun > çıkmak Için **ENTER** **tuşuna** olun.

::: moniker range="vs-2017"
Yeni bir proje her zaman varsayılan global Python ortamı ile ilişkilidir. Projeyi farklı bir ortamla (sanal ortamlar dahil) ilişkilendirmek için, projede **Python ortamları** düğümüne sağ tıklayın, **Python ortamlarını Ekle/Kaldır**' ı seçin ve istediklerinizi seçin.
::: moniker-end
::: moniker range=">=vs-2019"
Yeni bir proje her zaman varsayılan global Python ortamı ile ilişkilidir. Projeyi farklı bir ortamla (sanal ortamlar dahil) ilişkilendirmek için, projede **Python ortamları** düğümüne sağ tıklayın, **ortam ekle..** öğesini seçin ve istediklerinizi seçin. Ayrıca, araç çubuğundaki ortamlar açılan denetimini kullanarak projeye bir tane seçebilir ve ortam ekleyebilir veya ekleyebilirsiniz.

![Python araç çubuğuna ortam ekleme komutu](media/environments/environments-toolbar-2019.png)
::: moniker-end

Etkin ortamı değiştirmek için **Çözüm Gezgini** ' de istediğiniz ortama sağ tıklayın ve ortamı aşağıda gösterildiği gibi **Etkinleştir** ' i seçin. Daha fazla bilgi için bkz. [proje için ortam seçme](selecting-a-python-environment-for-a-project.md).

![Python projesi için bir ortam etkinleştirme](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Proje şablonları

Visual Studio, bir Python projesi sıfırdan veya mevcut koddan ayarlamak için çeşitli yollarla sağlar. Bir şablon kullanmak için **dosya** > **Yeni** > **projesi** menü komutunu seçin veya **Çözüm Gezgini** çözüme sağ tıklayın ve her ikisi de aşağıdaki **Yeni proje** iletişim kutusunu açılan > **Yeni proje** **Ekle** ' yi seçin. Python 'a özgü şablonları görmek için, "Python" üzerinde arama yapın veya **yüklü** > **Python** düğümünü seçin:

![Python şablonlarla yeni proje iletişim kutusu](media/projects-new-project-dialog.png)

Aşağıdaki tabloda, Visual Studio 2017 ve üzeri sürümlerde kullanılabilen şablonlar özetlenmektedir (tüm şablonlar önceki sürümlerde kullanılamaz):

| Şablon | Açıklama |
| --- | --- |
| [**Mevcut Python kodundan**](#create-project-from-existing-files) | Visual Studio projesi klasörü yapısı içinde mevcut Python kodu oluşturur.  |
| **Python uygulaması** | Tek ve boş bir dosya ile yeni bir Python uygulaması için bir temel Proje yapısı. Varsayılan olarak, proje varsayılan genel ortamın konsol yorumlayıcısında çalışır ve bu, [farklı bir ortam atayarak](selecting-a-python-environment-for-a-project.md)değiştirebilirsiniz. |
| [**Azure bulut hizmeti**](python-azure-cloud-service-project-template.md) | Python'da yazılmış bir Azure bulut hizmeti için bir proje. |
| [**Web projeleri**](python-web-application-project-templates.md) | Bottle, Django ve Flask gibi çeşitli çerçevelerini temel alan web apps için proje. |
| **IronPython uygulaması** | Benzer şekilde kullanır ancak Python uygulaması şablonu tarafından IronPython varsayılan etkinleştirme .NET birlikte çalışabilirlik ve karma mod .NET dilleri ile hata ayıklama. |
| **IronPython WPF uygulaması** | IronPython, Windows Presentation Foundation XAML dosyaları için uygulamanın kullanıcı arabirimini kullanarak bir proje yapısı. Visual Studio XAML Tasarımcısı sağlar, arka plan kod Python'da yazılabilir ve uygulama konsol görüntülemeden çalışır. |
| **IronPython Silverlight Web sayfası** | Silverlight'ı kullanarak bir tarayıcıda çalışan IronPython projesi. Uygulamanın Python kodu web sayfasına komut dosyası olarak dahil edilir. Ortak komut dosyası etiketi Python kodunuzu DOM ile etkileşim kurabilir Silverlight içinde çalışan IronPython başlatır miktar JavaScript kodu aşağı çeker |
| **IronPython Windows Forms uygulaması** | IronPython ile kullanıcı arabirimini kullanarak bir proje yapısı, kod ile Windows Forms kullanılarak oluşturulur. Uygulama, bir konsolu görüntülemeden çalışır. |
| **Arka plan uygulaması (IoT)** | Arka plan Hizmetleri cihazlarda çalıştırmak için Python projeleri dağıtılmasını destekler. Daha fazla bilgi için [Windows IoT geliştirme merkezi](https://dev.windows.com/en-us/iot) ' ni ziyaret edin. |
| **Python uzantı modülü** | Python **yerel geliştirme araçları** 'Nı C++ Visual Studio 2017 veya sonraki sürümlerde Python iş yüküne yüklediyseniz, bu şablon görsel altında görüntülenir (bkz. [yükleme](installing-python-support-in-visual-studio.md)). [Python için C++ uzantı oluşturma](working-with-c-cpp-python-in-visual-studio.md)konusunda açıklananlara C++ benzer bir uzantı dll 'si için çekirdek yapı sağlar. |

> [!Note]
> Python yorumlanan bir dil olduğundan, Visual Studio'da Python projeleri bir tek başına yürütülebilir dosya gibi diğer derlenmiş dili projeler (C#, örneğin) üretmediği. Daha fazla bilgi için bkz. [sorular ve yanıtlar](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>Var olan bir proje oluşturun

> [!Important]
> Burada açıklanan işlemi taşıma veya kopyalama orijinal kaynak dosyalarına desteklemez. Bir kopya ile çalışmak istiyorsanız, klasörü ilk çoğaltma.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Bağlantılı dosyaları

Bağlı dosyalar projeye kapsama alınır, ancak genellikle uygulamanın proje klasörleri dışında bulunan dosyalardır. **Çözüm Gezgini** , bir kaplama kısayolu simgesiyle normal dosyalar olarak görünürler: ![bağlantılı dosya simgesi](media/projects-linked-file-icon.png)

Bağlantılı dosyalar *. pyproj* dosyasında `<Compile Include="...">` öğesi kullanılarak belirtilir. Bağlı dosyalar, dizin yapısının dışında göreli bir yol kullanıyorsa veya **Çözüm Gezgini**içinde yollar kullandıklarında açık bir şekilde yapılır:

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Bağlantılı dosyaları aşağıdaki koşullardan herhangi biri altında göz ardı edilir:

- Bağlı dosya bağlantı meta verileri ve proje dizininden INCLUDE özniteliği olduğu belirtilen yolu içerir.
- Bağlı dosya proje hiyerarşisi içinde var olan bir dosya yineleme
- Bağlı dosya bağlantı meta verileri içeriyorsa ve bağlantı yolu göreli bir yol proje hiyerarşisi dışında
- Bağlantı yolunun kökü

### <a name="work-with-linked-files"></a>Bağlantılı dosyaları ile çalışma

Var olan bir öğeyi bağlantı olarak eklemek için, projede dosyayı eklemek istediğiniz klasöre sağ tıklayın ve ardından > **var olan öğe** **Ekle** ' yi seçin. Görüntülenen iletişim kutusunda bir dosya seçin ve **Ekle** düğmesine açılan listeden **bağlantı olarak ekle** ' yi seçin. Koşuluyla çakışan dosya yok, bu komut, seçili klasörde bulunan bir bağlantı oluşturur. Ancak, bu dosyanın bir bağlantısını projesinde zaten var veya aynı ada sahip bir dosya zaten var. bağlantı eklenmez.

Proje klasörleri zaten var olan bir bağlantı çalışırsanız, bir bağlantı değil de, normal bir dosya olarak eklenir. Dosyayı bir bağlantıya dönüştürmek **için dosyayı proje** hiyerarşisi dışında bir konuma kaydetmek üzere dosya > **farklı kaydet** ' i seçin; Visual Studio otomatik olarak bir bağlantıya dönüştürür. Benzer şekilde, bir bağlantı dosyayı proje hiyerarşisinde bir yere kaydetmek için **farklı kaydet** > **Dosya** kullanılarak geri dönüştürülebilir.

Bağlı bir dosyayı **Çözüm Gezgini**taşırsanız bağlantı taşınır ancak gerçek dosya etkilenmez. Benzer şekilde, bir bağlantının silinmesi bağlantı dosyasını etkilemeden kaldırır.

Bağlantılı dosyaları yeniden adlandırılamaz.

## <a name="references"></a>Başvurular

Visual Studio projeleri, **Çözüm Gezgini**' deki **Başvurular** düğümü altında görünen projelere ve uzantılara başvuru eklemeyi destekler:

![Python projeleri uzantısı başvuruları](media/projects-extension-references.png)

Uzantı başvuruları genellikle projeleri arasındaki bağımlılıkları göstermek ve tasarım zamanı veya derleme zamanında bağlama IntelliSense sağlamak için kullanılır. Python projeleri benzer şekilde başvuruları kullanın, ancak Python dinamik doğası nedeniyle öncelikle tasarım zamanında geliştirilmiş IntelliSense sağlamak için kullanılırlar. Bunlar ayrıca Microsoft Azure'a dağıtılacak Ek Bağımlılıklar'ı yüklemek için kullanılabilir.

### <a name="extension-modules"></a>Uzantı modüllerini

*. PYD* dosyası başvurusu, oluşturulan modül için IntelliSense 'i sağlar. Visual Studio, *. PYD* dosyasını Python yorumlayıcı 'ya yükler ve bunların tür ve işlevlerini gözlemleyip. İmza Yardımı sağlamak işlevleri için belge dizelerini ayrıştırmak de çalışır.

Herhangi bir zamanda uzantı modülü diskte güncelleştirdiyseniz, Visual Studio arka planda modülü çözümlemeden. Bu eylemin çalışma zamanı davranışı üzerinde hiçbir etkisi yoktur, ancak bazı tamamlamalar analiz tamamlanana kadar kullanılamaz.

Modülün bulunduğu klasöre bir [arama yolu](search-paths.md) da eklemeniz gerekebilir.

### <a name="net-projects"></a>.NET projeleri

IronPython ile çalışırken, IntelliSense etkinleştirmek için .NET derlemelerine başvurular ekleyebilirsiniz. Çözümünüzdeki .NET projeleri için, Python projenizde **Başvurular** düğümüne sağ tıklayın, **Başvuru Ekle**' yi seçin, **Projeler** sekmesini seçin ve istediğiniz projeye gidin. Ayrı olarak indirdiğiniz dll 'Ler için, bunun yerine, **Gözden** geçirme sekmesini seçin ve istenen dll 'ye gidin.

`clr.AddReference('<AssemblyName>')` çağrısı yapılıncaya kadar IronPython içindeki başvurular kullanılamadığından, genellikle kodunuzun başlangıcında derlemeye uygun bir `clr.AddReference` çağrısı da eklemeniz gerekir. Örneğin, Visual Studio 'da **IronPython Windows Forms uygulama** projesi şablonu tarafından oluşturulan kod, dosyanın en üstünde iki çağrı içerir:

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>Webpı projeleri

Microsoft Azure bulut hizmetlerine Webpı aracılığıyla ek bileşenler yükleyebileceği dağıtım için Webpı ürün girişleri başvuruları ekleyebilirsiniz. Varsayılan olarak görüntülenen akış Python özgü olan ve Django CPython ve diğer temel bileşenleri içerir. Kendi akışınızı, aşağıda gösterildiği gibi de seçebilirsiniz. Microsoft Azure'a yayımlarken, Kurulum görev tüm başvurulan ürünleri yükler.

> [!IMPORTANT]
> WebPI projeleri Visual Studio 2017 veya Visual Studio 2019 ' de kullanılamaz.

![Webpı başvuruları](media/projects-webPI-components.png)
