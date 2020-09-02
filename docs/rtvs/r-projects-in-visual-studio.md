---
title: R projeleri
description: Visual Studio 'da özellikler, proje komutları ve şablonlar dahil olmak üzere bir Manager R projesi oluşturma.
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: bcdef95935c0522c8b93a972d7f44fbd7632c53b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89312697"
---
# <a name="create-r-projects-in-visual-studio"></a>Visual Studio 'da R projeleri oluşturma

R Projesi ( *. RXPROJ* dosyası), projenizle ilişkili tüm kaynak ve içerik dosyalarını tanımlar. Ayrıca her dosya için derleme bilgilerini içerir, kaynak denetimi sistemleriyle tümleştirilecek bilgileri saklar ve uygulamanızı mantıksal bileşenlerde düzenlemenize yardımcı olur. Ancak, yüklü paketlerin listesi gibi çalışma alanıyla ilgili bilgiler, çalışma alanının kendisinde ayrı olarak tutulur.

Projeler her zaman bir Visual Studio *çözümü*içinde yönetilir ve bu, bir diğerine başvuruda bulunan herhangi bir sayıda proje içerebilir. Bkz. [Visual Studio 'da birden çok proje türü kullanma](#use-multiple-project-types-in-visual-studio).

## <a name="creating-a-new-r-project"></a>Yeni bir R projesi oluşturma

1. Visual Studio'yu açın.
1. **Dosya > yeni > projesi** seçin (**CTRL** + **+ Shift** + **N**)
1. **Şablonlar**R altında "R proje" seçeneğini belirleyin  >  **R**, projeye bir ad ve konum verin ve **Tamam**' ı seçin:

    ![Visual Studio 'da R için yeni proje iletişim kutusu (VS2017 ' de RTVS)](media/getting-started-01-new-project.png)

Bu komut, boş bir betiği olan bir proje oluşturur *. R* dosyası düzenleyicide açık. Ayrıca, projede iki farklı dosya **Çözüm Gezgini** de görebilirsiniz:

![Şablondan oluşturulan bir R projesinin içeriği](media/projects-template-results.png)

*. Rhistory* [R etkileşim](interactive-repl-for-r-in-visual-studio.md) penceresine girdiğiniz komutları kaydeder. **R araçları**  >  **Windows**  >  **geçmişi** komutuyla adanmış bir geçmiş penceresi açabilirsiniz. Bu pencerede, geçmiş içeriğini temizlemek için bir araç çubuğu düğmesi ve bağlam menüsü öğeleri bulunur.

*Rproject. rproj* dosyası, başka bir şekilde Visual Studio tarafından yönetilmeyen belirli R-özel proje ayarlarını tutar:

| Özellik | Varsayılan | Açıklama |
| --- | --- | --- |
| Sürüm | 1.0 | Projeyi oluşturmak için kullanılan Visual Studio için R Araçları sürümü. |
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

Var olan bir klasörünüz varsa *. * Bir projede yönetmek istediğiniz R dosyaları, aşağıdaki adımları uygulayın:

1. Önceki bölümde olduğu gibi Visual Studio 'da yeni bir proje oluşturun.
1. Dosyalarınızı proje klasörüne kopyalayın.
1. Visual Studio Çözüm Gezgini, projeye sağ tıklayın, **Add**  >  **Varolan öğe**Ekle ' yi seçin ve eklemek istediğiniz dosyalara gidin. Bu dosyalar, **Tamam ' ı**seçtikten sonra proje ağacınızdaki görünür.
1. Kodu alt klasörlere düzenlemek için projeye sağ tıklayın, önce yeni klasör **Ekle**' yi seçin  >  **New Folder** , sonra dosyalarınızı bu klasöre kopyalayın ve adım 3 ' te mevcut öğeleri ekleyin.

## <a name="project-properties"></a>Proje özellikleri

Proje özelliği sayfalarını açmak için **Çözüm Gezgini** içinde projeye sağ tıklayın ve **Özellikler**' i seçin veya **Proje > (proje adı) Özellikler** menü öğesini seçin. Açılan pencere, proje özelliklerini görüntüler:

| Tab | Özellik | Açıklama |
| --- | --- | --- |
| Çalıştır | Başlangıç dosyası | **Kaynak başlangıç dosyası** komutuyla çalışan dosyanın adı, **F5**, hata ayıklama başlatması veya hata ayıklama **başlatma**  >  **Start debugging** **Debug**  >  **hatası olmadan Başlat**. Projedeki dosyaya sağ tıklayıp **Başlangıç R betiği olarak ayarla** ' yı seçtiğinizde, başlangıç dosyası olarak da ayarlanır. |
| | Çalıştırmada R Etkileşim Sıfırla | Projeyi çalıştırırken etkileşimli pencerenin çalışma alanındaki tüm değişkenleri temizler. Bunun yapılması, bazı çalışma alanı içeriklerinin daha fazla çalışılmasından emin olmasını garanti eder. |
| | Uzak proje yolu | Uzak bir çalışma alanının yolu. |
| | Çalıştırma sırasında dosyaları aktar | **Dosya aktarımına**bağlı proje dosyalarının her çalıştırma ile uzak çalışma alanına kopyalanıp kopyalanmayacağını belirtir. |
| | Aktarılacak dosyalar | Bir uzak çalışma alanına kopyalanacak belirli dosyaları belirten dosya adları ve joker karakterler, **çalışma sırasında dosya aktar** seçildiyse seçilir. |
| Ayarlar | (Settings. R dosyası) | R Project ayarları ayarlarından geliyor *. r* veya **. Projenin içinde bulunan Settings. R* dosyaları. Hiçbir ayar dosyası yoksa, değişken ekleyebilir, sayfayı kaydedebilir ve varsayılan *ayarlar. R* dosyası sizin için oluşturulur. Ayrıca, **Dosya**  >  **Yeni öğe Ekle** menü komutu aracılığıyla projeye ayarlar dosyası ekleyebilirsiniz. <br/> Ayarlar R kodu olarak depolanır ve dosyanın başka modüller çalıştırılmadan önce kaynağı oluşturulabilir ve bu sayede ortam önceden tanımlanmış ayarlarla önceden dolduruluyor. |

## <a name="r-specific-project-commands"></a>R 'e özgü proje komutları

Visual Studio projeleri, sağ tıklama menüsü ve **Proje** menüsü aracılığıyla bir dizi genel komutu destekler. Bu genel yetenekler hakkında daha fazla bilgi için bkz. [Visual Studio 'Da çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md). Ancak, Visual Studio için R Araçları (RTVS), bir R Projesi için sağ tıklama menüsüne ve ayrıca proje içindeki dosya ve klasörler için kendi komutlarının bir sayısını eklediğini unutmayın.

| Komut | Açıklama |
| --- | --- |
| Çalışma dizinini burada ayarla | R Etkileşim pencerenin çalışma dizinini proje klasörüne ayarlar ve bu da bir proje içindeki herhangi bir alt klasörde kullanılabilir. |
| Içeren klasörü aç | Seçili dosyanın konumundaki Windows Gezgini 'ni açar. |
| R betiği Ekle | Yeni bir oluşturur ve açar *. R* dosyası varsayılan bir ada sahiptir. **Add**  >  Oluşturmak için**Yeni öğe** Ekle komutunu da kullanabilirsiniz *. R* dosyalarının yanı sıra diğer birçok dosya türünü de vardır. Bkz. [R-özel öğe şablonları](#r-specific-item-templates). |
| R Markdown Ekle | Yeni *. RMD* belgesi oluşturur ve varsayılan adla açar. Ayrıca, **Add**  >  **Yeni öğe** Ekle komutunu da *. RMD* dosyalarının yanı sıra diğer birçok dosya türünü oluşturmak için de kullanabilirsiniz. Bkz. [R-özel öğe şablonları](#r-specific-item-templates).  |
| Saklı yordamları Yayımla | R betiklerinizde bulunan saklı yordamları yayımlamak için bir işlem başlatır. Bkz. [SQL Server saklı yordamlarla çalışma](integrating-sql-server-with-r.md#work-with-sql-server-stored-procedures). |

## <a name="r-specific-item-templates"></a>R 'e özgü öğe şablonları

RTVS, belirli dosya türleri için bir dizi şablon içerir. Bir R projesine sağ tıklayıp **Add**  >  **Yeni öğe**Ekle ' yi seçerek, **Proje**  >  **Ekle yeni öğe**' yi seçerek veya **Dosya**  >  **Yeni**  >  **Dosya** ' yı seçip **R** sekmesini seçerek şablonlara erişirsiniz. Bir şablonu keşfetmenin en iyi yolu, yeni bir proje oluşturmak ve her türde dosya eklemek.

> [!Note]
> **Add**  >  **Yeni öğe** Ekle komutu ayrıca tabloda listelenmeyen genel dosya türlerini görüntüler; **Dosya**  >  **Yeni**  >  **Dosya** , bu türler **genel** sekmesinde yer alır.

| Dosya türü | Açıklama |
| --- | --- |
| R Betiği | R komut satırına girilebilecek aynı komutları içeren bir metin dosyası. |
| R Markdown | [R Markdown](rmarkdown-with-r-in-visual-studio.md) bir belge içeren dosya. |
| R ayarları | R uygulama ayarlarını tutan bir dosya. |
| R belgeleri | Yalnızca ad, diğer ad ve başlık alanlarını içeren bir genel R belge dosyası. |
| R belgeleri (Işlev) | Bir işlevi açıklama içeren çok sayıda alanı içeren R belge dosyası. |
| R belgeleri (veri kümesi) | Bir veri kümesini tanımlamak için açıklamaları olan çok sayıda alan içeren R belge dosyası. |
| SQL sorgusu | Boş bir *. SQL* dosyası. Bkz. [SQL Server ve R Ile çalışma](integrating-sql-server-with-r.md). |
| R ile saklı yordam | Alt SQL sorgusu ve alt saklı yordam şablon dosyası içeren bir R dosyası. Bkz. [SQL Server ve R Ile çalışma](integrating-sql-server-with-r.md). |

## <a name="use-multiple-project-types-in-visual-studio"></a>Visual Studio 'da birden çok proje türü kullanma

Visual Studio çözümleri, ilgili projeleri tek bir mantıksal yerde toplamak ve yönetmek için kullanışlı bir yer sağlar. Çözümler, kodunuzu organize etmenize ve takımlar içinde işbirliğini kolaylaştırır.

Aşağıdaki örnekte çözüm, R ve Azure Machine Learning kullanılarak oluşturulmuş bir model ve bir Python/scikit-öğren projesi, yoğun hesaplama çalışması için modüller içeren bir C++ projesi, veri yönetimi için bir SQL projesi ve sonucu yayımlayan Web sitesi için bir Python/şişe projesi içerir:

![Bir çözümde birden çok ilgili projeyi gösteren Visual Studio Çözüm Gezgini](media/projects-polyglot.png)

Kalın ile vurgulanan proje, çözüm için "başlangıç" projem dir; değiştirmek için, farklı bir projeye sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

> [!Note]
> Mevcut olduğunda, (Python için [C++ uzantısı oluşturma](../python/working-with-c-cpp-python-in-visual-studio.md)) bir açık R-C#/c + + dil tümleştirmesi yoktur.  Ancak, R için C# ve C++ köprülerini sağlayan kitaplıklar mevcuttur.

Projeleri ve çözümleri genel olarak yönetme hakkında daha fazla bilgi için bkz. [Visual Studio 'Da çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md).
