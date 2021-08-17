---
title: R projeleri
description: özellikler, proje komutları ve şablonlar dahil Visual Studio bir manager R projesi oluşturma.
ms.date: 06/29/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 4fd62b1641a9da10484d31e5f2eb212a09cbce12
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060654"
---
# <a name="create-r-projects-in-visual-studio"></a>Visual Studio R projeleri oluşturma

R Projesi ( *. RXPROJ* dosyası), projenizle ilişkili tüm kaynak ve içerik dosyalarını tanımlar. Ayrıca her dosya için derleme bilgilerini içerir, kaynak denetimi sistemleriyle tümleştirilecek bilgileri saklar ve uygulamanızı mantıksal bileşenlerde düzenlemenize yardımcı olur. Ancak, yüklü paketlerin listesi gibi çalışma alanıyla ilgili bilgiler, çalışma alanının kendisinde ayrı olarak tutulur.

projeler her zaman bir Visual Studio *çözümü* içinde yönetilir ve bu, bir diğerine başvuruda bulunan herhangi bir sayıda proje içerebilir. Bkz. [Visual Studio birden çok proje türü kullanma](#use-multiple-project-types-in-visual-studio).

## <a name="creating-a-new-r-project"></a>Yeni bir R projesi oluşturma

1. Visual Studio'yu açın.
1. **dosya > yeni > seçin Project** (**Ctrl** + **+ Shift** + **N**)
1. **şablonlar** R altında "R Project" seçeneğini belirleyin  >  , projeye bir ad ve konum verin ve **tamam**' ı seçin:

    ![Visual Studio R (VS2017 ' de rtvs) için yeni Project iletişim kutusu](media/getting-started-01-new-project.png)

Bu komut, boş bir betiği olan bir proje oluşturur *. R* dosyası düzenleyicide açık. Ayrıca, projede iki farklı dosya **Çözüm Gezgini** de görebilirsiniz:

![Şablondan oluşturulan bir R projesinin içeriği](media/projects-template-results.png)

*. Rhistory* [R etkileşim](interactive-repl-for-r-in-visual-studio.md) penceresine girdiğiniz komutları kaydeder. **R araçları**  >  **Windows**  >  **history** komutuyla adanmış bir geçmiş penceresi açabilirsiniz. Bu pencerede, geçmiş içeriğini temizlemek için bir araç çubuğu düğmesi ve bağlam menüsü öğeleri bulunur.

*Rproject. rproj* dosyası, başka bir şekilde yönetilmeyen Visual Studio tarafından yönetilmeyen belirli R 'a özgü proje ayarlarını korur:

| Özellik | Varsayılan | Açıklama |
| --- | --- | --- |
| Sürüm | 1.0 | projeyi oluşturmak için kullanılan Visual Studio için R Araçları sürümü. |
| RestoreWorkspace | Varsayılan | Önceki çalışma alanı değişkenlerini `.RData` Proje dizinindeki dosyadan otomatik olarak yükle. |
| SaveWorkspace | Varsayılan | Proje kapatılırken geçerli çalışma alanı değişkenlerini `.RData` Proje dizinindeki dosyaya kaydedin. |
| AlwaysSaveHistory | Varsayılan | Projeyi kapatırken, geçerli etkileşimli pencere geçmişini `.RHistory` Proje dizinindeki dosyaya kaydet. |
| Enablecodeındexing | Yes | Kod aramalarını hızlandırmak için bir arka plan dizin oluşturma görevinin çalıştırılıp çalıştırılmayacağını belirler. |
| UseSpacesForTab | Yes | Düzenleyicide **sekme** tuşuna basıldığında boşluk (Evet) veya sekme karakteri (Hayır) eklemek isteyip istemediğinizi belirler. |
| NumSpacesForTab | 2 | UseSpacesForTab Evet ise eklenecek boşluk sayısı. |
| Encoding | UTF-8 | Dosyalar için varsayılan kodlama `.R` . |
| RnwWeave | Sweave | RNW dosyası dalgalı olarak kullanılacak paket. |
| LaTeX | pdfLaTeX | Rmarki 'YI PDF 'ye dönüştürürken kullanılacak kitaplık. |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>Bir dosya klasörünü R projesine dönüştürme

Var olan bir klasörünüz varsa *.* Bir projede yönetmek istediğiniz R dosyaları, aşağıdaki adımları uygulayın:

1. önceki bölümde olduğu gibi Visual Studio yeni bir proje oluşturun.
1. Dosyalarınızı proje klasörüne kopyalayın.
1. Visual Studio Çözüm Gezgini projeye sağ tıklayın,   >  **varolan öğe** ekle ' yi seçin ve eklemek istediğiniz dosyalara gidin. Bu dosyalar, **Tamam ' ı** seçtikten sonra proje ağacınızdaki görünür.
1. Kodu alt klasörlere düzenlemek için projeye sağ tıklayın, önce yeni klasör **Ekle**' yi seçin  >   , sonra dosyalarınızı bu klasöre kopyalayın ve adım 3 ' te mevcut öğeleri ekleyin.

## <a name="project-properties"></a>Proje özellikleri

proje özelliği sayfalarını açmak için **Çözüm Gezgini** ' de projeye sağ tıklayın ve **özellikler**' i seçin ya da **Project > (proje adı) özellikler** menü öğesini seçin. Açılan pencere, proje özelliklerini görüntüler:

| Tab | Özellik | Açıklama |
| --- | --- | --- |
| Çalıştır | Başlangıç dosyası | **Kaynak başlangıç dosyası** komutuyla çalışan dosyanın adı, **F5**, hata ayıklama başlatması veya hata ayıklama **başlatma**  >     >  **hatası olmadan Başlat**. Projedeki dosyaya sağ tıklayıp **Başlangıç R betiği olarak ayarla** ' yı seçtiğinizde, başlangıç dosyası olarak da ayarlanır. |
| | Çalıştırmada R Etkileşim Sıfırla | Projeyi çalıştırırken etkileşimli pencerenin çalışma alanındaki tüm değişkenleri temizler. Bunun yapılması, bazı çalışma alanı içeriklerinin daha fazla çalışılmasından emin olmasını garanti eder. |
| | uzak Project yolu | Uzak bir çalışma alanının yolu. |
| | Çalıştırma sırasında dosyaları aktar | **Dosya aktarımına** bağlı proje dosyalarının her çalıştırma ile uzak çalışma alanına kopyalanıp kopyalanmayacağını belirtir. |
| | Aktarılacak dosyalar | Bir uzak çalışma alanına kopyalanacak belirli dosyaları belirten dosya adları ve joker karakterler, **çalışma sırasında dosya aktar** seçildiyse seçilir. |
| Ayarlar | (Ayarlar. R dosyası) | R proje ayarları Ayarlar gelir *. R* veya **. Ayarlar.* Projenin içinde bulunan R dosyaları. hiçbir ayar dosyası yoksa, değişken ekleyebilir, sayfayı kaydedebilir ve bir varsayılan *Ayarlar. R* dosyası sizin için oluşturulur. Ayrıca, **Dosya**  >  **Yeni öğe Ekle** menü komutu aracılığıyla projeye ayarlar dosyası ekleyebilirsiniz. <br/> Ayarlar, R kodu olarak depolanır ve dosya başka modüller çalıştırılmadan önce kaynağı oluşturulabilir, böylece ortam önceden tanımlanmış ayarlarla önceden dolduruluyor. |

## <a name="r-specific-project-commands"></a>R 'e özgü proje komutları

Visual Studio projeler, sağ tıklama menüsü ve **Project** menüsü aracılığıyla bir dizi genel komutu destekler. Bu genel yetenekler hakkında daha fazla bilgi için, bkz. [Visual Studio çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md). ancak, Visual Studio için R Araçları (rtvs), bir R projesi için sağ tıklama menüsüne ve ayrıca proje içindeki dosya ve klasörler için kendi komutlarının bir sayısını eklediğini unutmayın.

| Komut | Açıklama |
| --- | --- |
| Çalışma dizinini burada ayarla | R Etkileşim pencerenin çalışma dizinini proje klasörüne ayarlar ve bu da bir proje içindeki herhangi bir alt klasörde kullanılabilir. |
| Içeren klasörü aç | seçili dosyanın konumunda Windows gezginini açar. |
| R betiği Ekle | Yeni bir oluşturur ve açar *. R* dosyası varsayılan bir ada sahiptir.   >  Oluşturmak için **Yeni öğe** Ekle komutunu da kullanabilirsiniz *. R* dosyalarının yanı sıra diğer birçok dosya türünü de vardır. Bkz. [R-özel öğe şablonları](#r-specific-item-templates). |
| R Markdown Ekle | Yeni *. RMD* belgesi oluşturur ve varsayılan adla açar. Ayrıca,   >  **Yeni öğe** Ekle komutunu da *. RMD* dosyalarının yanı sıra diğer birçok dosya türünü oluşturmak için de kullanabilirsiniz. Bkz. [R-özel öğe şablonları](#r-specific-item-templates).  |
| Saklı yordamları Yayımla | R betiklerinizde bulunan saklı yordamları yayımlamak için bir işlem başlatır. bkz. [SQL Server saklı yordamlarla çalışma](integrating-sql-server-with-r.md#work-with-sql-server-stored-procedures). |

## <a name="r-specific-item-templates"></a>R 'e özgü öğe şablonları

RTVS, belirli dosya türleri için bir dizi şablon içerir. bir R projesine sağ tıklayıp   >  **yeni öğe** ekle ' yi seçerek, yeni   >  **öğe ekle**' yi Project seçerek veya **dosya**  >  **yeni**  >  **dosya** ' yı kullanarak ve **R** sekmesini seçerek şablonlara erişebilirsiniz. Bir şablonu keşfetmenin en iyi yolu, yeni bir proje oluşturmak ve her türde dosya eklemek.

> [!Note]
>   >  **Yeni öğe** Ekle komutu ayrıca tabloda listelenmeyen genel dosya türlerini görüntüler; **Dosya**  >  **Yeni**  >  **Dosya** , bu türler **genel** sekmesinde yer alır.

| Dosya türü | Açıklama |
| --- | --- |
| R Betiği | R komut satırına girilebilecek aynı komutları içeren bir metin dosyası. |
| R Markdown | [R Markdown](rmarkdown-with-r-in-visual-studio.md) bir belge içeren dosya. |
| R Ayarlar | R uygulama ayarlarını tutan bir dosya. |
| R belgeleri | Yalnızca ad, diğer ad ve başlık alanlarını içeren bir genel R belge dosyası. |
| R belgeleri (Işlev) | Bir işlevi açıklama içeren çok sayıda alanı içeren R belge dosyası. |
| R belgeleri (veri kümesi) | Bir veri kümesini tanımlamak için açıklamaları olan çok sayıda alan içeren R belge dosyası. |
| SQL Sorgulayamadı | Boş bir *. SQL* dosyası. bkz. [SQL Server ve R ile çalışma](integrating-sql-server-with-r.md). |
| R ile saklı yordam | alt SQL sorgu ve alt saklı yordam şablon dosyası içeren bir R dosyası. bkz. [SQL Server ve R ile çalışma](integrating-sql-server-with-r.md). |

## <a name="use-multiple-project-types-in-visual-studio"></a>Visual Studio birden çok proje türü kullanma

Visual Studio Çözümler, ilgili projeleri tek bir mantıksal yerde toplayıp yönetmek için uygun bir yer sağlar. Çözümler, kodunuzu organize etmenize ve takımlar içinde işbirliğini kolaylaştırır.

aşağıdaki örnekte çözüm, r ve Azure Machine Learning kullanılarak oluşturulmuş bir model ve bir python/scikit-öğren projesi, yoğun hesaplama çalışması için modüller içeren bir C++ projesi, veri yönetimi için bir SQL projesi ve sonucu yayımlayan web sitesi için bir Python/şişe projesi içerir:

![Visual Studio Bir çözümde birden çok ilgili projeyi gösteren Çözüm Gezgini](media/projects-polyglot.png)

Kalın ile vurgulanan proje, çözüm için "başlangıç" projem dir; değiştirmek için, farklı bir projeye sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

> [!Note]
> Mevcut olduğunda, (Python için [C++ uzantısı oluşturma](../python/working-with-c-cpp-python-in-visual-studio.md)) bir açık R-C#/c + + dil tümleştirmesi yoktur.  Ancak, R için C# ve C++ köprülerini sağlayan kitaplıklar mevcuttur.

Projeleri ve çözümleri genel olarak yönetme hakkında daha fazla bilgi için, bkz. [Visual Studio çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md).
