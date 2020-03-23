---
title: R projeleri
description: Visual Studio'da özellikleri, proje komutlarını ve şablonları içeren bir yönetici R projeleri oluşturma.
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: bcdef95935c0522c8b93a972d7f44fbd7632c53b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302695"
---
# <a name="create-r-projects-in-visual-studio"></a>Visual Studio'da R projeleri oluşturun

Bir R projesi *(.rxproj* dosyası) projenizle ilişkili tüm kaynak ve içerik dosyalarını tanımlar. Ayrıca, her dosya için yapı bilgileri içerir, kaynak denetim sistemleri ile tümleştirmek için bilgileri korur ve mantıksal bileşenler halinde uygulamanızı düzenlemenize yardımcı olur. Ancak, yüklenen paketlerin listesi gibi çalışma alanıyla ilgili bilgiler çalışma alanının kendisinde ayrı olarak tutulur.

Projeler her zaman bir birbiriyle referans olabilecek herhangi bir sayıda proje içerebilen bir Visual Studio *çözümü*içinde yönetilir. Bkz. [Visual Studio'da birden çok proje türü kullanın.](#use-multiple-project-types-in-visual-studio)

## <a name="creating-a-new-r-project"></a>Yeni bir R projesi oluşturma

1. Visual Studio'yu açın.
1. **Yeni > Projesi> Dosya** seçin (**Ctrl**+**Shift**+**N**)
1. **Şablonlar** > **R**altından "R Project"i seçin, projeye bir ad ve konum verin ve **Tamam'ı**seçin:

    ![Visual Studio'da R için Yeni Proje iletişim kutusu (VS2017'de RTVS)](media/getting-started-01-new-project.png)

Bu komut boş bir komut dosyası olan bir proje *oluşturur. *Editörde R dosyası açılır. **Çözüm Gezgini'nde** de dikkat edin, projede iki dosya daha vardır:

![Şablondan oluşturulan bir R projesinin içeriği](media/projects-template-results.png)

*Şey. Rhistory,* [R Interactive](interactive-repl-for-r-in-visual-studio.md) penceresine girdiğiniz komutları kaydeder. **R Tools** > **Windows** > **History** komutuyla özel bir geçmiş penceresi açabilirsiniz. Bu pencerede geçmiş içeriğini temizlemek için bir araç çubuğu düğmesi ve bağlam menüsü öğeleri vardır.

*rproject.rproj* dosyası, Visual Studio tarafından yönetilmeyen belirli R'ye özgü proje ayarlarını korur:

| Özellik | Varsayılan | Açıklama |
| --- | --- | --- |
| Sürüm | 1.0 | Projeyi oluşturmak için Görsel Stüdyo için R Tools sürümü kullanılmıştır. |
| Geri YüklemeÇalışma Alanı | Varsayılan | Önceki Çalışma Alanı değişkenlerini proje `.RData` dizinindeki dosyadan otomatik olarak yükleyin. |
| SaveWorkspace | Varsayılan | Projeyi kapatırken geçerli `.RData` çalışma alanı değişkenlerini proje dizinindeki dosyaya kaydedin. |
| Her Zaman Tarihi Kaydet | Varsayılan | Bir projeyi kapatırken `.RHistory` geçerli Etkileşimli Pencere geçmişini proje dizinindeki dosyaya kaydedin. |
| EtkinleştirkodDizilimi | Evet | Kod aramalarını hızlandırmak için arka plan dizinleme görevinin çalıştırılıp çalıştırılmayacağını belirler. |
| SpacesFortab'ı kullanma | Evet | Sekme **tuşuna** düzenleyicide basıldığında boşluk (Evet) veya Sekme karakteri (Hayır) ekleyip eklemeyin ilerler. |
| NumSpacesForTab | 2 | UseSpacesForTab Evet ise eklenecek alan sayısı. |
| Encoding | UTF-8 | Dosyalar için `.R` varsayılan kodlama. |
| RnwWeave | Sweave | Rnw dosyasını derken kullanılacak paket. |
| Lateks | pdfLaTeX | RMarkdown'ı PDF'ye dönüştürürken kullanılacak kitaplık. |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>Dosya klasörünü R projesine dönüştürme

Varolan bir klasörünüz *varsa. *Projede yönetmek istediğiniz R dosyaları aşağıdaki adımları yapın:

1. Önceki bölümde olduğu gibi Visual Studio'da yeni bir proje oluşturun.
1. Dosyalarınızı proje klasörüne kopyalayın.
1. Visual Studio Solution Explorer'da projeyi sağ tıklatın,**Varolan Öğe** **ekle'yi** > seçin ve eklemek istediğiniz dosyalara göz atın. Bu dosyalar **Tamam'ı**seçtikten sonra proje ağacınızda görünür.
1. Kodu alt klasörlere düzenlemek için projeyi sağ tıklatın, önce**Yeni Klasör** **Ekle'yi** > seçin, ardından dosyalarınızı bu klasöre kopyalayın ve 3.

## <a name="project-properties"></a>Proje özellikleri

Proje özelliği sayfalarını açmak için Solution **Explorer'da** projeyi sağ tıklatın ve **Özellikler'i**seçin veya **Project > (proje adı) özellikleri** menü öğesini seçin. Açılan pencere proje özelliklerini görüntüler:

| Tab | Özellik | Açıklama |
| --- | --- | --- |
| Çalıştırın | Başlangıç dosyası | Kaynak başlangıç dosyası komutu, **F5,** **Hata Ayıklama** > Başlat **hata** > **ayıklama**veya**hata ayıklama başlatma**ile çalıştırılabilen **dosyanın** adı hata ayıklama olmadan başlat. Projedeki dosyaya sağ tıklayarak ve **Başlangıç R komut dosyası olarak Ayarla'yı** seçmek de dosyayı başlangıç dosyası olarak ayarlar. |
| | R Interactive'i Çalıştırmada Sıfırla | Projeyi çalıştırırken etkileşimli pencerenin çalışma alanından tüm değişkenleri temizler. Bunu yapmak, çalıştırmalardan arta kalan çalışma alanı içeriğinin olmadığını garanti eder. |
| | Uzak Proje Yolu | Uzak bir çalışma alanına giden yol. |
| | Dosyaları çalıştırmada aktarma | **Aktarım**için Dosyalar'daki filtreye tabi olan proje dosyalarının her çalıştırmada uzak bir çalışma alanına kopyalanıp kopyalanmayacağını gösterir. |
| | Aktarım için dosyalar | **Çalışan Aktarım dosyaları** seçilirse, uzak bir çalışma alanına kopyalanması gereken belirli dosyaları gösteren dosya adları ve joker karakterler. |
| Ayarlar | (Settings.R dosyası) | R proje ayarları *Settings.R* veya * adresinden*gelir. *Project içinde bulunan Ayarlar.R dosyaları. Ayarlar dosyası yoksa, değişkenler ekleyebilir, sayfayı kaydedebilir ve varsayılan *Settings.R* dosyası sizin için oluşturulur. **Ayrıca Dosya** > **Ekle Yeni Öğe** menüsü komutu ile projeye ayarlar dosyası ekleyebilirsiniz. <br/> Ayarlar R kodu olarak depolanır ve dosya diğer modülleri çalıştırmadan önce kaynak lanabilir, böylece önceden tanımlanmış ayarlarla ortamı önceden doldurma. |

## <a name="r-specific-project-commands"></a>R'ye özgü proje komutları

Visual Studio projeleri, hem sağ tıklatma menüsü hem de **Proje** menüsü aracılığıyla bir dizi genel komutu destekler. Bu genel yetenekler hakkında ayrıntılı bilgi için [Visual Studio'daki Çözümler ve projelere](../ide/solutions-and-projects-in-visual-studio.md)bakın. Ancak, R Tools for Visual Studio (RTVS) bir R projesi için sağ tıklama menüsüne kendi komutlarını ve proje içindeki dosya ve klasörleri eklediğine dikkat edin.

| Komut | Açıklama |
| --- | --- |
| Set Çalışma Rehberi Burada | R Interactive penceresinin çalışma dizinini proje klasörüne ayarlar ve proje içindeki herhangi bir alt klasörde de kullanılabilir. |
| İçeren Klasörü Aç | Windows Gezgini'ni seçili dosyanın konumunda açar. |
| R Komut Dosyası Ekle | Oluşturur ve yeni bir *. *Varsayılan adı olan R dosyası. **Yeni Öğe** **Ekle** > komutunu oluşturmak için de kullanabilirsiniz. * R* dosyaları nın yanı sıra diğer dosya türlerinin bir dizi. [Bkz. R'ye özgü öğe şablonları.](#r-specific-item-templates) |
| R İşareti Ekle | Varsayılan bir adla yeni *.rmd* belgesi oluşturur ve açar. *.rmd* dosyalarının yanı sıra bir dizi diğer dosya türü oluşturmak için**Yeni Öğe** **Ekle** > komutunu da kullanabilirsiniz. [Bkz. R'ye özgü öğe şablonları.](#r-specific-item-templates)  |
| Depolanan Yordamları Yayımla | R komut dosyalarında bulunan depolanmış yordamları yayımlamak için bir işlem başlatır. Bkz. [SQL Server depolanan yordamlarla Çalışma.](integrating-sql-server-with-r.md#work-with-sql-server-stored-procedures) |

## <a name="r-specific-item-templates"></a>R'ye özgü öğe şablonları

RTVS belirli dosya türleri için şablonlar bir dizi içerir. Bir R projesine sağ tıklayarak ve**Yeni Öğe** **Ekle'yi** > seçerek, **Project** > **Add New Item'i**seçerek veya **Dosya** > **Yeni** > **Dosya'yı** kullanarak **R** sekmesini seçerek şablonlara erişebilirsiniz. Şablonu keşfetmenin en iyi yolu yeni bir proje oluşturmak ve her türden dosya eklemektir.

> [!Note]
> **Yeni Öğe** **Ekle** > komutları, tabloda listelenmemiş genel dosya türlerini de görüntüler; **Dosya** > **Yeni** > **Dosya** ile bu türler **Genel** sekmesinde bulunur.

| Dosya Türü | Açıklama |
| --- | --- |
| R Betiği | R komut satırına girilebilen aynı komutları içeren bir metin dosyası. |
| R Markdown | [R Markdown](rmarkdown-with-r-in-visual-studio.md) belgesi içeren bir dosya. |
| R Ayarları | R uygulama ayarlarını tutan bir dosya. |
| R Dokümantasyon | Yalnızca ad, takma ad ve başlık alanlarını içeren genel bir R belgeleme dosyası. |
| R Dokümantasyon (Fonksiyon) | Bir işlevi açıklamak için açıklamalar içeren birçok alan içeren bir R dokümantasyon dosyası. |
| R Dokümantasyon (Dataset) | Bir veri kümesini açıklamak için açıklamalar içeren birçok alan içeren bir R dokümantasyon dosyası. |
| SQL Sorgusu | Boş bir *.sql* dosyası. Bkz. [SQL Server ve R ile Çalışma](integrating-sql-server-with-r.md). |
| R ile Depolanan Yordam | Alt SQL Sorgusu ve alt depolanmış yordam şablon dosyası içeren bir R dosyası. Bkz. [SQL Server ve R ile Çalışma](integrating-sql-server-with-r.md). |

## <a name="use-multiple-project-types-in-visual-studio"></a>Visual Studio'da birden çok proje türü kullanma

Visual Studio Solutions, ilgili projeleri tek bir mantıksal yerde toplamak ve yönetmek için uygun bir yer sağlar. Çözümler kodunuzu düzenli tutmaya yardımcı olur ve ekipler içinde işbirliğini kolaylaştırır.

Aşağıdaki örnekte, çözüm, R ve Azure Machine Learning kullanılarak oluşturulmuş bir modele sahip bir R projesi, python/scikit-learn projesi, yoğun hesaplama çalışmaları için modüller içeren bir C++ projesi, veri yönetimi için bir SQL projesi ve sonucu yayınlayan web sitesi için bir Python/Bottle projesi içerir:

![Visual Studio Solution Explorer bir çözümde birden çok ilgili projeyi gösteriyor](media/projects-polyglot.png)

Boldface ile vurgulanan proje çözüm için "başlangıç" projesidir; değiştirmek için, farklı bir projeyi sağ tıklatın ve **başlangıç projesi olarak Ayarla'yı**seçin.

> [!Note]
> Şu anda, c#/C++ dil tümleştirmesinde açık bir R yok (Python'da olduğu gibi, [bkz. Python için C++ uzantısı oluştur).](../python/working-with-c-cpp-python-in-visual-studio.md)  Ancak R için C# ve C++ köprüleri sağlayan kitaplıklar vardır.

Genel olarak proje ve çözümleri yönetme hakkında daha fazla bilgi için [Visual Studio'daki Çözümler ve projelere](../ide/solutions-and-projects-in-visual-studio.md)bakın.
