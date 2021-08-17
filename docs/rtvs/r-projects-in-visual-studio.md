---
title: R projeleri
description: Özellikler, proje komutları ve şablonlar Visual Studio bir yönetici R projesi oluşturma.
ms.date: 06/29/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 2e3a21d1ed1c64d80b8a8c91e5b7c1cab5573025513cf6f3bfbe6159c792be2e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121385606"
---
# <a name="create-r-projects-in-visual-studio"></a>Visual Studio'de R projeleri oluşturma

R projesi *(.rxproj* dosyası), projeniz ile ilişkili tüm kaynak ve içerik dosyalarını tanımlar. Ayrıca her dosya için derleme bilgileri içerir, kaynak denetim sistemleriyle tümleştirileyecek bilgileri sürdürür ve uygulamalarınızı mantıksal bileşenlerde düzenlemenize yardımcı olur. Ancak, yüklü paketlerin listesi gibi çalışma alanıyla ilgili bilgiler çalışma alanının kendisinde ayrı olarak korunur.

Projeler her zaman bir Visual Studio *çözümü* içinde yönetilir. Bu çözüm, herhangi bir sayıda proje içerebilir ve bu da diğerine başvurur. Bkz. [Birden çok proje türü Visual Studio.](#use-multiple-project-types-in-visual-studio)

## <a name="creating-a-new-r-project"></a>Yeni R projesi oluşturma

1. Visual Studio'yu açın.
1. Dosya **Adı'> Yeni > Project** (**Ctrl** + **Shift** + **N**) seçin
1. Şablonlar R altında "R Project" **öğesini** seçin, projeye bir ad ve konum girin ve  >  Tamam'ı **seçin:**

    ![Visual Studio'de R için yeni Project iletişim kutusu (VS2017'de RTVS)](media/getting-started-01-new-project.png)

Bu komut, boş bir betik ile bir proje *oluşturur. R* dosyası düzenleyicide açılır. Ayrıca, **Çözüm Gezgini** projesinde başka iki dosya daha olduğunu da düşünün:

![Şablondan oluşturulan bir R projesinin içeriği](media/projects-template-results.png)

. *Rhistory,* giriş penceresine hangi komutları [R Etkileşim.](interactive-repl-for-r-in-visual-studio.md) R Araçları ve Geçmiş komutuyla ayrılmış **bir**  >  **geçmiş Windows**  >  **açabilirsiniz.** Bu pencerede, geçmiş içeriğini temizlemek için bir araç çubuğu düğmesi ve bağlam menüsü öğeleri vardır.

*rproject.rproj* dosyası, diğer durumlarda aşağıdakiler tarafından yönetil olmayan R'ye özgü bazı proje Visual Studio:

| Özellik | Varsayılan | Açıklama |
| --- | --- | --- |
| Sürüm | 1.0 | Projeyi Visual Studio için R Araçları için kullanılan uygulamanın sürümü. |
| RestoreWorkspace | Varsayılan | Proje dizininde dosyasından önceki `.RData` Çalışma alanı değişkenlerini otomatik olarak yükle. |
| SaveWorkspace | Varsayılan | Bir projeyi kapatırken geçerli `.RData` çalışma alanı değişkenlerini proje dizininde dosyasına kaydedin. |
| AlwaysSaveHistory | Varsayılan | Bir projeyi kapatırken geçerli `.RHistory` Etkileşimli Pencere geçmişini proje dizininde dosyasına kaydedin. |
| EnableCodeIndexing | Yes | Kod aramalarını hızlandırmak için arka plan dizin oluşturma görevinin çalıştırıp çalıştırılamay olmadığını belirler. |
| UseSpacesForTab | Yes | Düzenleyicide Sekme tuşuna basıldığında boşluk (Evet) veya Sekme karakteri **(Hayır)** ek gerekip gerek olmadığını belirler. |
| NumSpacesForTab | 2 | UseSpacesForTab evet ise, eklenecek boşluk sayısı. |
| Encoding | UTF-8 | Dosyalar için varsayılan `.R` kodlama. |
| RnwWeave | Sweave | Bir Rnw dosyası weavingken kullanmak üzere paket. |
| Lateks | pdfLaTeX | RMarkdown PDF'ye dönüştürülürken kullanmak üzere kitaplık. |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>Dosya klasörünü R projesine dönüştürme

var olan bir klasörünüz *varsa.* Projede yönetmek istediğiniz R dosyaları için aşağıdaki adımları uygulayın:

1. Önceki bölümde olduğu gibi Visual Studio yeni bir proje oluşturun.
1. Dosyalarınızı proje klasörüne kopyalayın.
1. Yeni Visual Studio Çözüm Gezgini projeye sağ tıklayın, Var Olan Öğeyi Ekle'yi seçin ve eklemek  >  istediğiniz dosyalara göz atabilirsiniz. Bu dosyalar Tamam'ı seçdikten sonra proje ağacınıza **görünür.**
1. Kodu alt klasörlerde düzenlemek için projeye sağ tıklayın, önce Yeni Klasör Ekle'yi seçin, sonra dosyalarınızı bu klasöre kopyalayın ve 3. adımda bu mevcut  >   öğeleri ekleyin.

## <a name="project-properties"></a>Proje özellikleri

Proje özellik sayfalarını açmak için, Çözüm Gezgini  'de projeye sağ tıklayın ve Özellikler'i seçin veya **Project > (proje adı) özellikler menü** öğesini seçin. Açılan pencerede proje özellikleri görüntülenir:

| Tab | Özellik | Açıklama |
| --- | --- | --- |
| Çalıştır | Başlangıç dosyası | Kaynak başlangıç dosyası komutu,  **F5**, Hata Ayıklama Hata Ayıklamayı Başlat **veya** Hata ayıklama olmadan Başlat hatasını ayıkla  >     >  **komutuyla çalıştıran dosyanın adı.** Projede dosyaya sağ tıklar ve Başlangıç R betiği olarak **ayarla'ya tıklarsanız** başlangıç dosyası olarak da ayarlanır. |
| | Çalıştırma R Etkileşim sıfırlama | Projeyi çalıştırarak etkileşimli pencerenin çalışma alanında yer alan tüm değişkenleri temizler. Bunu yapmak, farklı çalıştırmalardan kalan çalışma alanı içeriğinin olmadığını garantiler. |
| | Uzak Project Yolu | Uzak çalışma alanının yolu. |
| | Çalıştırmada dosyaları aktarma | Aktaracak dosyalar'daki filtreye tabi proje dosyalarının **her** çalıştırma ile uzak bir çalışma alanına kopyalanır olup olmadığını gösterir. |
| | Aktarıla dosyalar | Çalıştırmada dosyaları aktar seçiliyse, uzak bir çalışma alanına kopyailecek belirli dosyaları gösteren dosya adlar **ve joker** karakterler. |
| Ayarlar | (Ayarlar. R dosyası) | R projesi ayarları, *Ayarlar. R* veya **.Ayarlar. Projenin* içinde bulunan R dosyaları. Ayar dosyası yoksa değişkenler ekleyebilir, sayfayı kaydedebilir ve varsayılan bir *Ayarlar. R* dosyası sizin için oluşturulur. Ayrıca Dosya Yeni Öğe Ekle menü komutu aracılığıyla **projeye**  >  **ayarlar dosyası ekleyebilirsiniz.** <br/> Ayarlar R kodu olarak depolanır ve dosya, diğer modüller çalıştırılamadan önce kaynak olarak kullanılabilir, bu nedenle ortamı önceden tanımlanmış ayarlarla önceden doldurmak için kullanılır. |

## <a name="r-specific-project-commands"></a>R'ye özgü proje komutları

Visual Studio projeleri hem sağ tıklama menüsü hem de sağ tıklama menüsü aracılığıyla bir dizi **genel Project** destekler. Bu genel özellikler hakkında ayrıntılı bilgi için [bkz.](../ide/solutions-and-projects-in-visual-studio.md)Visual Studio. Ancak, bu Visual Studio için R Araçları (RTVS), R projesi için sağ tıklama menüsüne ve ayrıca proje içindeki dosya ve klasörlere kendi komutlarını ekler.

| Komut | Açıklama |
| --- | --- |
| Çalışma Dizinini Burada Ayarla | R Etkileşim penceresinin çalışma dizinini proje klasörüne ayarlar. Bu klasör, proje içindeki herhangi bir alt klasörde de kullanılabilir. |
| İçeren Klasörü Aç | Seçilen Windows konumdaki Gezgin'i açar. |
| R Betiği Ekleme | Yeni bir oluşturur ve *açar. Varsayılan* adı olan R dosyası. Oluşturmak için Yeni Öğe **Ekle**  >  **komutunu** da *kullanabilirsiniz. R* dosyalarının yanı sıra bir dizi diğer dosya türü. Bkz. [R'ye özgü öğe şablonları.](#r-specific-item-templates) |
| Yeni R Markdown | Yeni *. RMD* belgesi oluşturur ve varsayılan adla açar. Ayrıca,   >  **Yeni öğe** Ekle komutunu da *. RMD* dosyalarının yanı sıra diğer birçok dosya türünü oluşturmak için de kullanabilirsiniz. Bkz. [R-özel öğe şablonları](#r-specific-item-templates).  |
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
