---
title: SDK Microsoft Yardım Görüntüleyicisi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: 34
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cafdfacec24e906569d0f2b0d1a334511a75e30a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300713"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Yardım Görüntüleyicisi SDK’sı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu makale, Visual Studio Yardım Görüntüleyicisi tümleştiricileri için aşağıdaki görevleri içerir:

- Konu oluşturma (F1 desteği)

- Yardım Görüntüleyici içeriği oluşturma-marka paketi

- Makale kümesi dağıtma

- Visual Studio Kabuğu 'na yardım ekleme (tümleşik veya yalıtılmış)

- Ek Kaynaklar

### <a name="creating-a-topic-f1-support"></a>Konu oluşturma (F1 desteği)
 Bu bölümde, sunulan konunun bileşenlerine genel bir bakış sunulmaktadır. konu gereksinimleri, bir konunun nasıl oluşturulacağı hakkında kısa bir açıklama (F1 destek gereksinimleri dahil) ve son olarak, işlenen sonucuyla ilgili örnek bir konu.

 **Yardım Görüntüleyicisi konusuna genel bakış**

 İşleme için bir konu çağrıldığında, Yardım Görüntüleyicisi, Install veya Last Update sırasında konuyla ilişkili olan marka paketi öğelerini XHTML konusuyla birlikte alır ve iki öğeyi de gösterilen içerik görünümüne (marka verileri +) sonucunu birleştirir. Konu verileri).  Marka paketi logo, içerik davranışları desteği ve marka metni (telif hakkı vb.) içerir.  Marka paketi öğeleri hakkında daha fazla bilgi için aşağıdaki "marka paketi oluşturma" konusuna bakın.  Konuyla ilişkili bir marka paketi olmadığı durumda, Yardım Görüntüleyicisi Yardım Görüntüleyici uygulama kökünde (Branding_en-US. mshc) bulunan geri dönüş markalama paketini kullanır.

 **Yardım Görüntüleyicisi konu gereksinimleri**

 Yardım Görüntüleyicisi içinde doğru bir şekilde işlenebilmek için ham konu içeriğinin W3C temel 1,1 XHTML olması gerekir.

 Bir konu genellikle iki bölüm içerir:

- Meta veriler (bkz. Içerik meta verileri başvurusu): konuyla ilgili veriler, örneğin, konu benzersiz KIMLIĞI, anahtar sözcük değeri, TOC KIMLIĞI, üst düğüm KIMLIĞI, vb.

- Gövde içeriği: desteklenen içerik davranışları (daraltılabilir alan, kod parçacığı vb. dahil olmak üzere W3C temel 1,1 XHTML ile uyumludur. Tam liste aşağıda gösterilmiştir).

  Visual Studio marka paketi desteklenen denetimler:

- Bağlantılar

- CodeSnippet

- CollapsibleArea

- Devralınan üye

- LanguageSpecificText

  Desteklenen dil dizeleri (büyük/küçük harfe duyarlı değil):

- JavaScript

- CSharp veya c #

- CPlusPlus veya VisualC + + ya da c++

- j

- VisualBasic veya vb

- f # veya FSharp veya FS

- diğer – bir dil adını temsil eden bir dize

  **Yardım Görüntüleyici konusu oluşturma**

  ContosoTopic4. htm adlı yeni bir XHTML belgesi oluşturun ve başlık etiketini (aşağıda) ekleyin.

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

 Daha sonra, konunun nasıl sunulacağınızı (kendi kendine markalı veya değil) tanımlamak için veri ekleyin, bu konunun TOC içinde olduğu, KIMLIĞI (diğer konuların bağlantı başvurusu için) vb. bu konunun bulunduğu F1 için nasıl başvurulacağını tanımlayın.  Desteklenen meta verilerin tüm listesi için aşağıdaki "Içerik meta verileri" tablosuna bakın.

- Bu durumda, Visual Studio Yardım Görüntüleyicisi markalama paketinin bir türevi olan kendi marka paketimizi kullanacağız.

- IDE Özellik paketinde verilen F1 değeri ile eşleşecek F1 meta adı ve değerini ("Microsoft. help. F1" content = "ContosoTopic4") ekleyin.  (Daha fazla bilgi için F1 support bölümüne bakın.)   Bu, IDE 'de F1 seçildiğinde bu konuyu göstermek için IDE içindeki F1 çağrısıyla eşleşen değerdir.

- Konu KIMLIĞINI ekleyin. Bu konuya bağlantı sağlamak için diğer konular tarafından kullanılan dizedir.  Bu konu, Yardım Görüntüleyicisi KIMLIĞIDIR.

- TOC için, bu konunun üst düğümünü ekleyerek TOC düğümünün bu konu başlığının nerede görüneceğini belirleyin.

- TOC için, bu konunun düğüm sırasını ekleyin. Üst düğümde n sayıda alt düğüm olduğunda, bu konunun konumunun alt düğümlerinin sıralaması olarak tanımlayın. Örneğin, bu konu 4 ' ün 4 alt konu konusunun sayısıdır.)

  Örnek meta veri bölümü:

```html
<html>
<head>
<title>Contoso Topic 4</title>

<meta name="SelfBranded" content="false" />
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />

</head>

<body>

</body>
</html>

```

 **Konu gövdesi**

 Konunun başlık ve alt bilgisini dahil değil), sayfa bağlantıları, bir not bölümü, daraltılabilir alan, kod parçacığı ve dile özgü metnin bir bölümünü içerir.  Sunulma konusunun bu alanlarla ilgili bilgiler için bkz. marka bölümü.

1. Konu başlığı etiketi ekleyin: `<div class="title">Contoso Topic 4</div>`

2. Bir Note bölümü ekleyin: `<div class="alert"> add your table tag and text </div>`

3. Daraltılabilir alan ekle: `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Kod parçacığı ekleme: `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Kod diline özgü metin ekleme: `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` devLangnu = diğer dilleri girmenize izin verir. Örneğin, devLangnu = "FORTRAN" kod parçacığı DisplayLanguage = FORTRAN olduğunda FORTRAN öğesini görüntüler.

6. Sayfa bağlantıları ekle: `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Note: desteklenmeyen yeni "görüntü dili" (örnek, F#, COBOL, FORTRAN) için kod parçacığındaki kod renklendirme tek renkli olacaktır.

 **Örnek Yardım Görüntüleyicisi konusu** Kod, meta verilerin, kod parçacığının, daraltılabilir alanın ve dile özgü metnin nasıl tanımlanacağını gösterir.

```
<?xml version="1.0" encoding="utf-8"?>
<html>
<head>
<title>Contoso Topic 4</title>

    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />
<meta name="SelfBranded" content="false" />
</head>

<body>
<div class="title">Contoso Topic 4</div>

  <div id="header">
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">
        <tr id="headerTableRow2"><td align="left">
            <span id="nsrTitle">Contoso Topic 1</span>
          </td>
<td align="right">
</td></tr>
<tr id="headerTableRow1"><td align="left">
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>
          </td></tr>
      </table>
</div>

<h2>Table of Contents</h2>

<ul class="toc">
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>
<li class="tocline1"><a href="#seealso" target="_self">2.1 See Also</a></li>
</ul>

<div class="topic">

<div id="mainSection">
<div id="mainBody">

<a name="introduction"></a>
<h2>1.0 Introduction</h2>
<p>[This documentation is for sample purposes only.]</p>

<p>Contoso Topic 1 contains examples of:
<ul>
<li>Collapsible Area</li>
<li>Bookmark ("See also")</li>
<li>Code Snippets from Branding Package</li>
</ul>
 </p>
<div class="alert"><table><tr><th>
<strong>Note </strong></th></tr>
<tr><td>
<p>This is an example of a <span class="label">Note </span>section.
Call out important items for your reader in this <span class="label">Note </span>box.
</p></td></tr>
</table>
</div>
</div>

<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">

            <a id="sectionToggle0"><!----></a>

<div>
Example of Collapsible Area
<br/>
Lorem ipsum dolor sit amet...
</div>
</CollapsibleArea>

<div id="snippetGroup" >
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip
Dim messageBoxVB as New System.Text.StringBuilder()
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)
    messageBoxVB.AppendLine()
 ...
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")
End Sub
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)
{
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );
messageBoxCS.AppendLine();
...
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );
}
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >
some F# code
</CodeSnippet>
</div>

<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />

<a name="seealso"></a>
<h1 class="heading">See Also</h1>

    <div id="seeAlsoSection" class="section">
    <div class="seeAlsoStyle">
        <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>

```

 **F1 desteği**

 Visual Studio 'da, F1 ' i seçtiğinizde, imlecin IDE içinde yerleştirilmesiyle sağlanan değerler oluşturulur ve bir "özellik paketi" ' ni sağlanan değerlerle doldurur (imleç konumuna göre). İmleç özellik x 'in üzerindeyken, özellik x etkin/odağa sahiptir ve özellik paketini değerlerle doldurur.  F1 seçildiğinde, özellik paketi doldurulur ve Visual Studio F1 kodu, müşteriler varsayılan yardım kaynağının yerel mi yoksa çevrimiçi mi olduğunu (çevrimiçi), daha sonra kullanıcılar ayarına göre (çevrimiçi olarak varsayılan) (çevrimiçi) ve Kabuk yürütme ' ye göre uygun dizeyi oluşturur. (örneğin, exe başlatma parametreleri için yardım Yönetici Kılavuzu) yerel yardım varsayılan ise özellik çantasından yerel Yardım Görüntüleyicisi + anahtar kelimeleridir ve parametre listesinde anahtar sözcüğe sahip MSDN URL 'SI ile birlikte

 Birden çok değerli dize olarak adlandırılan F1 için üç dize döndürülürse, ilk terimi alın, bir isabet arayın ve bulunursa, bu işlemi yaptık; Aksi takdirde, sonraki dizeye geçin.  Sıralama önemli. Çok değerli anahtar sözcüklerin sunumu, en kısa dize için en uzun dize olmalıdır.  Bunu, birden çok değerli anahtar kelimelerinde doğrulamak için, seçilen anahtar sözcüğü içerecek şekilde çevrimiçi F1 URL dizesine bakın.

 Visual Studio 2012 ' de, özellikle çevrimiçi ve çevrimdışı arasında daha güçlü bir bölme yaptık. böylece, kullanıcının ayarı çevrimiçi ise, Yardım Kitaplığı Aracısı aracılığıyla yönlendirme yerine yalnızca MSDN 'deki çevrimiçi sorgu hizmetinize doğrudan F1 isteği geçirdik. Visual Studio 2010. Daha sonra, bu bağlamda farklı bir şey yapılıp yapılmayacağını öğrenmek için "satıcı içeriği yüklendi = true" durumuna güveniyoruz. Bu değer true ise, müşterileriniz için desteklemek istediğiniz seçeneğe bağlı olarak bu ayrıştırma ve yönlendirme mantığını gerçekleştirirsiniz. Yanlış ise MSDN 'ye gitmeniz yeterlidir. Kullanıcının ayarı yerel ise, tüm çağrılar yerel yardım altyapısına gider.

 F1 akış diyagramı:

 ![F1 akışı](../../extensibility/internals/media/f1flow.png "F1flow")

 Yardım Görüntüleyicisi varsayılan yardım içerik kaynağı çevrimiçi olarak ayarlandığında (tarayıcıda Başlat):

- Visual Studio Iş ortağı (VSP) özellikleri, F1 özellik paketine (özellik paketi öneki. anahtar sözcüğü ve kayıt defterinde bulunan ön ek için çevrimiçi URL) bir değer yayar: F1 tarayıcıya bir VSP URL + parametreleri gönderir.

- Visual Studio özellikleri (dil Düzenleyicisi, Visual Studio 'ya özgü menü öğeleri vb.): F1 tarayıcıya bir Visual Studio URL 'SI gönderir.

  Yardım Görüntüleyicisi varsayılan yardım içerik kaynağı yerel yardım (yardım görüntüleyicisinde Başlat) olarak ayarlandığında:

- F1 özellik paketi ile yerel depo dizini (diğer bir deyişle, özellik paketi öneki. anahtar sözcük = yerel depo dizininde bulunan değer) arasında anahtar sözcük eşleşme olan VSP özellikleri: F1, yardım görüntüleyicisindeki konuyu işler.

- Visual Studio özellikleri (VSP 'nin Visual Studio özelliklerinden yayılan özellik paketini geçersiz kılmasına yönelik bir seçenek): F1, yardım görüntüleyicisinde bir Visual Studio konusu oluşturur.

  Satıcı yardım içeriği için F1 geri dönüşü etkinleştirmek üzere aşağıdaki kayıt defteri değerlerini ayarlayın. F1 geri dönüş, Yardım Görüntüleyicisi 'nin çevrimiçi F1 Yardım içeriğine bakmak üzere ayarlandığı ve satıcının içeriğinin yerel olarak kullanıcının sabit sürücüsüne yüklendiği anlamına gelir. Yardım Görüntüleyicisi, içerik için yerel yardım 'a bakmalıdır, ancak varsayılan ayar çevrimiçi yardım için olsa bile.

1. Yardım 2,1 kayıt defteri anahtarı altındaki **Vendorcontent** değerini ayarlayın:

   - 32 bit işletim sistemleri için:

        HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Help\v2.1\Catalogs\VisualStudio12

        "VendorContent" = DWORD: 00000001

   - 64 bit işletim sistemleri için:

        HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

        "VendorContent" = DWORD: 00000001

2. İş ortağı ad alanını yardım 2,1 kayıt defteri anahtarı altına kaydedin:

   - 32 bit işletim sistemleri için:

      HKEY_LOCAL_MACHINE \Software\microsoft\help\v2,\partner<em>\\< ad alanı\></em>

      "konum" = "çevrimdışı"

   - 64 bit işletim sistemleri için:

      HKEY_LOCAL_MACHINE \Software\wow6432node\microsoft\help\v2,\partner<em>\\< ad alanı\></em>

      "konum" = "çevrimdışı"

   **Temel yerel ad alanı ayrıştırma**

   Temel yerel ad alanı ayrıştırmayı açmak için, kayıt defterinde şu ada sahip yeni bir DWORD ekleyin: BaseNativeNamespaces ve değerini 1 olarak ayarlayın (desteklemek istedikleri Katalog anahtarı altında).  Örneğin, Visual Studio kataloğunu kullanmak istiyorsanız, anahtarı yola ekleyebilirsiniz:

   HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

   ÜST BILGIDE/YÖNTEMDE bir F1 anahtar kelimesiyle karşılaşıldığında, '/' karakteri ayrıştırılır ve bu da aşağıdaki yapının oluşmasına neden olur:

- ÜST BILGI: kayıt defterine kaydolmak için kullanılabilecek ad alanı olacaktır

- Yöntem: Bu, üzerinden geçirilen anahtar sözcük olur.

  Örneğin, CustomLibrary adlı özel bir kitaplık ve MyTestMethod adlı bir yöntem verildiğinde, bir F1 isteği geldiğinde `CustomLibrary/MyTestMethod`olarak biçimlendirilir.

  Kullanıcı daha sonra CustomLibrary 'yi Iş ortakları Hive altında ad alanı olarak kaydedebilir ve istediği konum anahtarını sağlayabilir ve sorguya geçirilen anahtar sözcük MyTestMethod olur.

  **IDE 'de yardım hata ayıklama aracında etkinleştirme**

  Aşağıdaki kayıt defteri anahtarını ve değerini ekleyin:

  HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\12.0\Dynamic yardım anahtarı: hata ayıklama çıkışını perakende değerde görüntüle: Evet

  IDE 'de, yardım menüsü öğesi altında "hata ayıklama yardım bağlamı" nı seçin.

  **İçerik meta verileri**

  Aşağıdaki tabloda, köşeli ayraçlar arasında görünen tüm dizeler, tanınan bir değerle değiştirilmelidir. Örneğin, \<meta Name = "Microsoft. help. locale" content = "[Language Code]"/>, "[Language Code]", "en-US" gibi bir değer ile değiştirilmelidir.

|Özellik (HTML temsili)|Açıklama|
|--------------------------------------|-----------------|
|\< meta Name = "Microsoft. help. locale" content = "[Language-Code]"/>|Bu konu için bir yerel ayar ayarlar. Bu etiket bir konu başlığında kullanılıyorsa, yalnızca bir kez kullanılması gerekir ve diğer Microsoft Yardım etiketlerinin üzerine eklenmelidir. Bu etiket kullanılmazsa, konunun gövde metni, belirtilen ürün yerel ayarıyla ilişkili sözcük kesici kullanılarak dizinlenir; Aksi halde, en-US sözcük kesici kullanılır. Bu etiket, ıSOC RFC 4646 ' e uygundur. Microsoft Yardım 'ın doğru şekilde çalıştığından emin olmak için, genel dil özniteliği yerine bu özelliği kullanın.|
|\< meta Name = "Microsoft. help. Topılocale" content = "[Language-Code]"/>|Diğer yerel ayarlar da kullanıldığında, bu konu için bir yerel ayar ayarlar. Bu etiket bir konu başlığında kullanılıyorsa, yalnızca bir kez kullanılmalıdır. Katalog birden fazla dilde içerik içerdiğinde bu etiketi kullanın. Bir katalogdaki birden çok konu aynı KIMLIĞE sahip olabilir, ancak her birinin benzersiz bir Topılocale belirtmesi gerekir. Kataloğun yerel ayarıyla eşleşen bir Topılocale belirten konu, içindekiler tablosunda görüntülenen konudur. Ancak, konunun tüm dil sürümleri arama sonuçlarında görüntülenir.|
|\< başlığı > [title]\</title >|Bu konunun başlığını belirtir. Bu etiket gereklidir ve konunun yalnızca bir kez kullanılması gerekir. Konunun gövdesinde \<div > bölümü yoksa, bu başlık konu başlığında ve içindekiler tablosunda görüntülenir.|
|\< meta Name = "Microsoft. help. Keywords" content = "[aKeywordPhrase]"/>|Yardım görüntüleyicisinin Dizin bölmesinde görüntülenen bir bağlantının metnini belirtir. Bağlantıya tıklandığında konu görüntülenir. Bir konu için birden çok dizin anahtar sözcüğü belirtebilir veya bu konunun bağlantılarının dizinde görünmesini istemiyorsanız bu etiketi atlayabilirsiniz. Önceki yardım sürümlerindeki "K" anahtar sözcükleri bu özelliğe dönüştürülebilir.|
|\< meta Name = "Microsoft. help. ID" content = "[TopicId]"/>|Bu konu için tanımlayıcıyı ayarlar. Bu etiket gereklidir ve konunun yalnızca bir kez kullanılması gerekir. KIMLIğIN aynı yerel ayara sahip olan katalogdaki konular arasında benzersiz olması gerekir. Başka bir konu başlığında, bu KIMLIĞI kullanarak bu konuya bir bağlantı oluşturabilirsiniz.|
|\< meta Name = "Microsoft. help. F1" content = "[System. Windows. Controls. Ilkel. ırecyıclingıtemcontainergenerator]"/>|Bu konu için F1 anahtar sözcüğünü belirtir. Bir konu için birden çok F1 anahtar sözcüğü belirtebilir veya bu konunun, bir uygulama kullanıcısı F1 tuşuna bastığında görüntülenmesini istemiyorsanız bu etiketi atlayabilirsiniz. Genellikle, bir konu için yalnızca bir F1 anahtar sözcüğü belirtilir. Önceki yardım sürümlerindeki "F" anahtar sözcükleri bu özelliğe dönüştürülebilir.|
|\< meta Name = "Description" content = "[konu açıklaması]"/>|Bu konudaki içeriğin kısa bir özetini sağlar. Bu etiket bir konu başlığında kullanılıyorsa, yalnızca bir kez kullanılmalıdır. Bu özelliğe doğrudan sorgu kitaplığı tarafından erişilir; Dizin dosyasında depolanmaz.|
 meta Name = "Microsoft. help. TocParent" içerik = "[parent_Id]"/>|İçindekiler tablosunda bu konunun üst konusunu belirtir. Bu etiket gereklidir ve konunun yalnızca bir kez kullanılması gerekir. Değer, üst öğenin Microsoft.Help.Id. Bir konu, içindekiler tablosunda tek bir konuma sahip olabilir. "-1", TOC kökünün konu KIMLIĞI olarak değerlendirilir. [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)], Bu sayfa Yardım Görüntüleyicisi giriş sayfasıdır. Bu, en üst düzeyde gösterildiklerinden emin olmak için bazı konulara özel olarak TocParent =-1 eklediğimiz nedenidir. Yardım Görüntüleyicisi giriş sayfası bir sistem sayfasıdır ve bu nedenle yok edilir. VSP, KIMLIĞI-1 olan bir sayfa eklemeye çalışırsa, bu, içerik kümesine eklenebilir, ancak Yardım Görüntüleyicisi her zaman sistem sayfasını kullanır – Yardım Görüntüleyicisi giriş|
|\< meta Name = "Microsoft. help. TocOrder" content = "[pozitif tamsayı]"/>|Bu konunun içerik tablosunda, eşi konularına göre göründüğünü belirtir. Bu etiket gereklidir ve konunun yalnızca bir kez kullanılması gerekir. Değer bir tamsayıdır. Daha yüksek değerli bir tamsayıyı belirten konunun üzerinde bir alt değer tamsayı belirten bir konu görüntülenir.|
|\< meta Name = "Microsoft. help. Product" content = "[ürün kodu]"/>|Bu konunun açıkladığı ürünü belirtir. Bu etiket bir konu başlığında kullanılıyorsa, yalnızca bir kez kullanılmalıdır. Bu bilgiler, Yardım dizin oluşturucuya geçirilen bir parametre olarak da sağlanabilir.|
|\< meta Name = "Microsoft. help. ProductVersion" content = "[sürüm numarası]"/>|Bu konunun açıkladığı ürünün sürümünü belirtir. Bu etiket bir konu başlığında kullanılıyorsa, yalnızca bir kez kullanılmalıdır. Bu bilgiler, Yardım dizin oluşturucuya geçirilen bir parametre olarak da sağlanabilir.|
|\< meta Name = "Microsoft. help. Category" content = "[dize]"/>|İçeriğin alt bölümleri tanımlamak için ürünler tarafından kullanılır. Bir konu için birden çok alt bölüm tanımlayabilir veya bağlantıların herhangi bir alt bölümleri belirlemesine izin istemiyorsanız bu etiketi atlayabilirsiniz. Bu etiket, bir konu yardım 'ın önceki bir sürümünden dönüştürüldüğünde TargetOS ve Targetframeworkbilinen özniteliklerini depolamak için kullanılır. İçeriğin biçimi AttributeName: AttributeValue.|
|\< meta Name = "Microsoft. help. TopicVersion Content =" [konu sürüm numarası] "/>|Bir katalogda birden fazla sürüm mevcut olduğunda konusunun bu sürümünü belirtir. Microsoft.Help.Id 'in benzersiz olması garanti edilmediği için, bir katalogda bir konunun birden fazla sürümü varsa, örneğin bir katalog .NET Framework 3,5 için bir konu ve .NET Framework 4 ' ü ve her ikisi de aynı mikro yumuşatılmış. Help.Id.|
|\< meta Name = "Selfmarkalı" content = "[TRUE veya FALSE]"/>|Bu konunun Yardım Kitaplığı Yöneticisi başlangıç marka paketini veya konuya özgü bir marka paketini kullanıp kullanmadığını belirtir. Bu etiket doğru ya da yanlış olmalıdır. DOĞRU ise, ilişkili konunun marka paketi, Yardım Kitaplığı Yöneticisi başladığında ayarlanan marka paketini geçersiz kılar, böylece konu diğer içeriğin işlenmesinin dışında olsa bile, konunun istendiği şekilde işlenir. YANLıŞ ise, Yardım Kitaplığı Yöneticisi başladığında ayarlanan marka paketine göre geçerli konu oluşturulur. Varsayılan olarak, Yardım Kitaplığı Yöneticisi kendini markalamayı doğru olarak bildirmediği sürece yanlış olarak kabul eder; Bu nedenle, \<meta Name = "Selfmarkalı" content = "FALSE"/> bildirmeniz gerekmez.|

### <a name="creating-a-branding-package"></a>Marka paketi oluşturma
 Visual Studio sürümü, Visual Studio Iş ortakları için yalıtılmış ve tümleşik kabuklar da dahil olmak üzere birçok farklı Visual Studio ürününü kapsar.  Bu ürünlerin her biri, ürüne özel olarak bazı konu tabanlı yardım içeriği marka desteği gerektirir.  Örneğin, Visual Studio konularının tutarlı bir marka sunumu olması gerekir, ancak ISO kabuğunu sarmalayan SQL Studio, her konu için kendi benzersiz yardım içeriği markalamasını gerektirir.  Tümleşik bir kabuk Iş ortağı, kendi konu markalarını koruyarak Yardım konularının üst Visual Studio ürün Yardım içerikleri dahilinde olmasını isteyebilir.

 Marka paketleri, Yardım Görüntüleyicisi 'Ni içeren ürün tarafından yüklenir.  Visual Studio ürünleri için:

- Yardım Görüntüleyicisi 2,1 uygulama kökünde (örnek: C:\Program Files (x86) \Microsoft yardım Viewer\v2,1), bir geri dönüş marka paketi (Branding_\<locale >. mshc) yüklenir.  Bu, ürün markası paketinin yüklü olmadığı (içerik yüklenmemiş) veya yüklü marka paketinin bozuk olduğu durumlarda kullanılır.  Uygulama kök geri dönüş markalama paketi kullanıldığında Visual Studio öğeleri (logo ve geri bildirim) yok sayılır.

- İçerik paketi hizmetinden Visual Studio içeriği yüklendiğinde, bir marka paketi de yüklenir (ilk kez içerik yükleme senaryosu için).  Marka paketine yönelik bir güncelleştirme varsa, güncelleştirme sonraki içerik güncelleştirmesi veya ek paket yükleme eylemi gerçekleştiğinde yüklenir.

  Microsoft Yardım Görüntüleyicisi konu meta verilerine dayalı olarak konuların markalamasını destekler.

- Konu meta verileri kendi kendine markalı = doğru tanımlar, konuyu olduğu gibi işler, hiçbir şey yapmaz (marka olarak en fazla).

- Konu meta verileri kendi kendine markalı = false tanımlıyor, TopicVendor meta veri değeriyle ilişkili marka paketini kullanın.

- Burada konu meta verileri name = "Microsoft. help. TopicVendor" Content =\< marka paketi adı ' nı satıcının MSHA > tanımlar, içerik değerinde tanımlanan marka paketini kullanın.

- Visual Studio kataloğu 'nda, marka paketlerinin öncelikli bir uygulaması vardır.  İlk Visual Studio varsayılan markası uygulanır ve ardından konu meta verilerinde tanımlandıysa ve ilişkili marka paketiyle (yükleme msha bölümünde tanımlandığı gibi) destekleniyorsa, satıcı tanımlı marka bir geçersiz kılma olarak uygulanır.

  Marka öğeleri genellikle üç ana kategoriye ayrılır:

- Üstbilgi öğeleri (örnek geri bildirim bağlantısı, koşullu vazgeçme metni, logo)

- İçerik davranışları (örnek, genişletme/daraltma denetim metni öğeleri ve kod parçacığı öğeleri)

- Footer öğeleri (örnek telif hakkı)

  Markalı öğeler olarak kabul edilen öğeler (bu belirtimde ayrıntılı) şunları içerir:

- Katalog/ürün logosu (örnek, Visual Studio)

- Geri bildirim bağlantısı ve e-posta öğeleri

- Vazgeçme Metni

- Telif hakkı metni

  Visual Studio Yardım Görüntüleyicisi markalama paketindeki destek dosyaları şunlardır:

- Grafikler (logolar, simgeler vb.)

- Marka. js – içerik davranışlarını destekleyen betik dosyaları

- Marka. xml – katalog içeriklerine sürekli olarak kullanılan dizeler.  Note: marka. xml içindeki Visual Studio yerelleştirme metin öğeleri için _locID = "benzersiz değer >\<ekleyin"

- Sunum tutarlılığı için marka. css – stil tanımları

- Tutarlı yazdırılmış sunum için. CSS stili tanımları yazdırılıyor

  Yukarıda belirtildiği gibi, marka paketleri konusuyla ilişkilendirilir:

- Meta verilerde Selfmarkalı = false tanımlandığında konu, Katalog markalama paketini devralır

- Ya da Selfmarkalı = false olduğunda ve MSHA 'da tanımlanmış benzersiz bir marka paketi varsa ve içerik yüklendiğinde kullanılabilir

  Özel marka paketleri uygulayan VSPs 'ler için (VSP içeriği, Selfmarkalı = true), devam etmenin bir yolu, geri dönüş markalama paketiyle (yardım görüntüleyiciyle yüklenir) başlamamaya ve dosyanın adını uygun şekilde değiştirecek.  Branding_\<locale >. mshc dosyası,. mshc olarak değiştirilmiş dosya uzantısına sahip bir zip dosyasıdır, bu nedenle uzantıyı. mshc 'den. zip 'e değiştirmeniz ve içeriği ayıklamanız yeterlidir.  Marka paketi öğeleri için aşağıya bakın ve uygun şekilde değiştirin (örneğin, logoyu VSP logosu olarak ve marka. xml dosyasındaki logo başvurusunu değiştirin, her VSP için bkz. xml, VSP özellikleri, vb.).

  Tüm değişiklikler tamamlandığında, istenen marka öğelerini içeren bir ZIP dosyası oluşturun ve uzantıyı. mshc olarak değiştirin.

  Özel marka paketini ilişkilendirmek için, markalama mshc dosyasına yönelik başvuruyu içeren MSHA 'yı oluşturun (konuları içeren).  Temel bir MSHA oluşturmak için aşağıdaki "MSHA" başlığına bakın.

  Marka. xml dosyası, konu başlığı \<meta ad = "Microsoft. help. Selfmarkalı" content = "false"/> içerdiğinde bir konudaki belirli öğeleri tutarlı bir şekilde oluşturmak için kullanılan liste öğelerini içerir.  Marka. xml dosyasındaki öğelerin Visual Studio listesi aşağıda listelenmiştir.  Bu liste, kendi ürün marka ihtiyaçlarını karşılamak üzere bu öğeleri (örneğin logo, geri bildirim ve telif hakkı) değiştiren ISO kabuğu benimseme şablonu olarak kullanılmak üzere tasarlanmıştır.

  Not: "{n}" tarafından belirtilen değişkenlerin kod bağımlılıkları vardır – bu değerleri kaldırmak veya değiştirmek hatalara ve büyük olasılıkla uygulama kilitlenmesine neden olur. Yerelleştirme tanımlayıcıları (örnek _locID = "codeparçacığını. n") Visual Studio marka paketine dahil edilmiştir.

  **Marka. xml**

|||
|-|-|
|Özellik:|**CollapsibleArea**|
|Kullanırsınız|Genişlet içerik denetimi metnini Genişlet|
|**Öğe**|**Değer**|
|ExpandText|Genişlet|
|CollapseText|Daralt|
|Özellik:|**CodeSnippet**|
|Kullanırsınız|Kod parçacığı denetim metni.  Note: "bölünmez" boşluk ile kod parçacığı içeriği, boşluk olarak değiştirilecek.|
|**Öğe**|**Değer**|
|CopyToClipboard|Panoya Kopyala|
|ViewColorizedText|Renklendirilmiş görüntüleme|
|CombinedVBTabDisplayLanguage|Visual Basic (örnek)|
|VBDeclaration|Bildirim|
|VBUsage|Kullanım|
|Özellik:|**Geri bildirim, altbilgi ve logo**|
|Kullanırsınız|Müşterinin, e-posta ile geçerli konu hakkında geri bildirim sağlaması için bir geri bildirim denetimi sağlayın.  İçerik için telif hakkı metni.  Logo tanımı.|
|**Öğe**|**Değer (Bu dizeler, içerik benimseme gereksinimini karşılayacak şekilde değiştirilebilir.)**|
|Yaptırımlar|© 2013 Microsoft Corporation. Tüm hakları saklıdır.|
|SendFeedback|bir href = "{0}" {1}> geri bildirim gönder\</a > Bu konuda Microsoft 'a \<.|
|FeedbackLink||
|Logo başlığı|[!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]|
|LogoFileName|vs_logo_bk.gif|
|LogoFileNameHC|vs_logo_wh. gif|
|Özellik:|**Sorumluluk reddi**|
|Kullanırsınız|Makine çevirisi içeriği için büyük/küçük harfe özgü bildirimler kümesi.|
|**Öğe**|**Değer**|
|MT_Editable|Bu makale makine çevirisi yapıldı. Bir Internet bağlantınız varsa, bu sayfayı orijinal Ingilizce içeriğiyle aynı anda düzenlenebilir modda görüntülemek için "Bu konuyu çevrimiçi görüntüle" seçeneğini belirleyin.|
|MT_NonEditable|Bu makale makine çevirisi yapıldı. Bir Internet bağlantınız varsa, bu sayfayı orijinal Ingilizce içeriğiyle aynı anda düzenlenebilir modda görüntülemek için "Bu konuyu çevrimiçi görüntüle" seçeneğini belirleyin.|
|MT_QualityEditable|Bu makale el ile çevrilmiştir. Bir Internet bağlantınız varsa, bu sayfayı orijinal Ingilizce içeriğiyle aynı anda düzenlenebilir modda görüntülemek için "Bu konuyu çevrimiçi görüntüle" seçeneğini belirleyin.|
|MT_QualityNonEditable|Bu makale el ile çevrilmiştir. Bir Internet bağlantınız varsa, bu sayfayı orijinal Ingilizce içeriğiyle aynı anda düzenlenebilir modda görüntülemek için "Bu konuyu çevrimiçi görüntüle" seçeneğini belirleyin.|
|MT_BetaContents|Bu makale, bir ön sürüm için makine çevirisi yapıldı. Bir Internet bağlantınız varsa, bu sayfayı orijinal Ingilizce içeriğiyle aynı anda düzenlenebilir modda görüntülemek için "Bu konuyu çevrimiçi görüntüle" seçeneğini belirleyin.|
|MT_BetaRecycledContents|Bu makale, ön sürüm için el ile çevrilmiştir. Bir Internet bağlantınız varsa, bu sayfayı orijinal Ingilizce içeriğiyle aynı anda düzenlenebilir modda görüntülemek için "Bu konuyu çevrimiçi görüntüle" seçeneğini belirleyin.|
|Özellik:|**LinkTable**|
|Kullanırsınız|Çevrimiçi konu bağlantıları desteği|
|**Öğe**|**Değer**|
|LinkTableTitle|Tablo bağla|
|Topicenulınktext|Bilgisayarınızda mevcut olan bu konunun Ingilizce sürümünü\</a > görüntüleyin.|
|Topiconlinelink metni|Bu konuyu bir href = "{0}" {1}> çevrimiçi\</a \<görüntüleyin >|
|OnlineText|Online|
|Özellik:|**Video ses denetimi**|
|Kullanırsınız|Video içeriği için öğeleri ve metni görüntüleme|
|**Öğe**|**Değer**|
|MultiMediaNotSupported|{0} içeriğini desteklemek için Internet Explorer 9 veya üzeri yüklü olmalıdır.|
|VideoText|videoyu görüntüleme|
|AudioText|ses akışı|
|Onlinevideolınktext|\<p > Bu konuyla ilgili videoyu görüntülemek Için, {0}\<bir href = "{1}" >{2}\</a > ' a tıklayın.\</p >|
|Onlinesesolınktext|\<p > Bu konuyla ilişkili sesi dinlemek Için {0}' a href = "{1}" >{2}\</a > \<tıklayın.\</p >|
|Özellik:|**İçerik yüklü değil denetimi**|
|Kullanırsınız|Contentnotyüklüyken. htm işleme için kullanılan metin öğeleri (dizeler)|
|**Öğe**|**Değer**|
|Contentnotınstalınstalınstalde başlığı|Bilgisayarınızda içerik bulunamadı.|
|Contentnotınstalınstaldownloadcontenttext|\<p > bilgisayarınıza içerik indirmek Için bir href = "{0}" {1}\<Yönet sekmesine >/a\<tıklayın.\</p >|
|Contentnotınstalınstalınstalde metni|\<p > bilgisayarınızda hiç içerik yüklü değil. Yerel Yardım içeriği yüklemesi için yöneticinize başvurun.\</p >|
|Özellik:|**Konu bulunamadı denetimi**|
|Kullanırsınız|Topicnotfound. htm işleme için kullanılan metin öğeleri (dizeler)|
|**Öğe**|**Değer**|
|Topınotfoundtitle|İstenen konu bilgisayarınızda bulunamıyor.|
|Topınotfoundviewonlinetext|\<p > istediğiniz konu bilgisayarınızda bulunamadı, ancak bir href = "{0}" {1}\<çevrimiçi >/a\<konusunu görüntüleyebilirsiniz >.\</p >|
|TopicNotFoundDownloadContentText|\<p > benzer konuların bağlantılarını görmek için gezinti bölmesine bakın veya bir href = "{0}" {1}\<, içeriği bilgisayarınıza indirmek için Yönet sekmesine >/a\<tıklayın.\</p >|
|Topınotfoundmetni|\<p > istediğiniz konu bilgisayarınızda bulunamadı.\</p >|
|Özellik:|**Konu başlığı bozuk denetimi**|
|Kullanırsınız|Topıbozulan. htm işleme için kullanılan metin öğeleri (dizeler)|
|**Öğe**|**Değer**|
|Topıbozuk Tedtitle|İstenen konu gösterilemiyor.|
|Topıboztedviewonlinetext|\<p > Yardım Görüntüleyicisi istenen konuyu görüntüleyemiyor. Konunun içeriğinde veya temeldeki sistem bağımlılığında bir hata olabilir.\</p >|
|Özellik:|**Giriş sayfası denetimi**|
|Kullanırsınız|Yardım Görüntüleyicisi üst düzey düğüm içeriğinin görüntülenmesini destekleyen metin.|
|**Öğe**|**Değer**|
|HomePageTitle|Yardım Görüntüleyicisi giriş sayfası|
|Homepagetanıtımı|\<p > Microsoft araçları, ürünleri, teknolojileri ve hizmetleri kullanan herkese yönelik önemli bir bilgi kaynağı olan Microsoft Yardım Görüntüleyicisi hoş geldiniz. Yardım Görüntüleyicisi, nasıl yapılır ve başvuru bilgilerine, örnek koda, teknik makalelere ve daha fazlasına erişmenizi sağlar. İhtiyacınız olan içeriği bulmak için içindekiler tablosuna göz atarak tam metin aramasını kullanın veya anahtar sözcük dizinini kullanarak içerik üzerinde gezinin.\</p >|
|Homepagecontentınstalltext|\<p >\<br/> \<bir href = "{0}" {1}> Içeriği Yönet\</a > sekmesini kullanarak şunları yapın:\<ul >\<li > bilgisayarınıza içerik ekleyin.\</li >\<li > yerel içeriklerinizin güncelleştirmelerini denetleyin.\</li >\<li > içeriği bilgisayarınızdan kaldırın.\</li >\</ul >\</p >|
|Homepageınstalınstalbook defterleri|Yüklü kitaplar|
|Homepagenobooksyüklü|Bilgisayarınızda içerik bulunamadı.|
|HomePageHelpSettings|Yardım Içeriği ayarları|
|HomePageHelpSettingsText|\<p > geçerli ayarınız yerel yardımdır. Yardım Görüntüleyicisi bilgisayarınıza yüklediğiniz içeriği görüntüler.\<br/> yardım içeriklerinizi değiştirmek Için, Visual Studio menü çubuğunda \<span Style = "{0}" > Yardım ' ı seçin, yardım tercihi\</span > belirleyin.\<br/>\</p >|
|Karşılık|MB|

 **marka. js**

 Marka. js dosyası, Visual Studio Yardım Görüntüleyicisi markalama öğeleri tarafından kullanılan JavaScript 'ı içerir.  Aşağıda, marka öğelerinin ve destekleyici JavaScript işlevinin bir listesi verilmiştir.  Bu dosya için Yerelleştirilecek tüm dizeler, bu dosyanın en üstündeki "yerelleştirilebilir dizeler" bölümünde tanımlanmıştır.  ITıL dosyası, marka. js dosyası içindeki Loc dizeleri için oluşturulmuştur.

||||
|-|-|-|
|**Marka özelliği**|**JavaScript Işlevi**|**Açıklama**|
|Var...||Değişkenleri tanımlama|
|Kullanıcı kodu dilini al|setUserPreferenceLang|bir dizini # ile kod diline eşler|
|Tanımlama bilgisi değerlerini ayarlama ve edinme|getCookie, setCookie||
|Devralınan üye|changeMembersLabel|Devralınan üyeyi Genişlet/Daralt|
|Selfmarkalı = false olduğunda|onLoad|Bir yazdırma isteği olup olmadığını denetlemek için sorgu dizesini okuyun.  Tüm kod parçacıklarını Kullanıcı tarafından tercih edilen sekmesine odaklamak için ayarlayın.  Bu bir yazdırma isteği ise, isPrinterFriendly değerini true olarak ayarlayın. Yüksek karşıtlık modunu denetleyin.|
|Kod parçacığı|addSpecificTextLanguageTagSet||
||Getındexfromdevlang||
||Değişiklik sekmesi||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|Tüm daraltılabilir denetim nesnelerini listeye yaz.|
||CA_Click|Daraltılabilir alanın durumuna bağlı olarak, hangi görüntü ve metnin mevcut olduğunu tanımlar|
|Logo için Karşıtlık desteği|ıblackıce arka planı ()|Arka planın siyah olup olmadığını anlamak için çağırılır.  Yalnızca yüksek karşıtlık modunda doğru olduğunda geçerlidir.|
||Ishighkontrast ()|yüksek karşıtlık modunu algılamak için renkli bir Aralık kullanın|
||Onhighkarşıtlıklı (siyah)|Yüksek karşıtlık algılandığında çağırılır|
|LST işlevselliği|||
||Addtolanspectextıdset (kimlik)||
||updateLST (currentLang)||
||Getdevlangfromcodeparçacığını (Lang)||
|Multimedya işlevselliği|Başlık (başlangıç, bitiş, metin, stil)||
||findAllMediaControls (normalizedId)||
||getActivePlayer (normalizedId)||
||captionsOnOff (kimlik)||
||toSeconds (t)||
||getAllComments (düğüm)||
||styleRectify (styleName, Stildeğeri)||
||showCC (kimlik)||
||alt başlık (kimlik)||

 **HTM DOSYALARı**

 Marka paketi içerik kullanıcılarına yardımcı olmak için anahtar bilgilerini iletişim için senaryoları destekleyen bir dizi HTM dosyası içerir. Örneğin, hangi içerik kümelerinin yükleneceğini ve konu başlıkları ne zaman Yerel konu kümesinde bulunur. Bu HTM dosyaları her ürün için değiştirilebilir.  ISO kabuğu satıcıları, varsayılan marka paketini alabilir ve bu sayfaların davranışını ve içeriğini, ihtiyacını pakete göre değiştirebilir.  Bu dosyalar, marka etiketlerin marka. xml dosyasından ilgili içeriği alması için kendi marka paketine başvurur.

||||
|-|-|-|
|**Dosyasýný**|**Kullanırsınız**|**Görünen Içerik kaynağı**|
|giriş sayfası. htm|Bu, şu anda yüklü olan içeriği görüntüleyen ve kullanıcıya içerik hakkında sunmanız gereken diğer tüm iletileri gösteren bir sayfasıdır.  Bu dosya, "Microsoft.Help.Id" content = "-1" ek meta veri özniteliğine sahiptir ve bu içeriği TOC yerel içeriğinin üst kısmına koyar.||
||< META_HOME_PAGE_TITLE_ADD/>|Marka. xml, etiket \<HomePageTitle >|
||< HOME_PAGE_INTRODUCTION_SECTION_ADD/>|Marka. xml, etiket \<Homepagetanıtımı >|
||< HOME_PAGE_CONTENT_INSTALL_SECTION_ADD/>|Marka. xml, etiket \<Homepagecontentınstalltext >|
||< HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD/>|Başlık bölümü markalaması. xml etiketi\<Homepageınstaltabook >, uygulamadan oluşturulan veriler, \<Homepagenobooksyüklü > hiçbir kitap yüklü olmadığında.|
||< HOME_PAGE_SETTINGS_SECTION_ADD/>|Başlık bölümü markalaması. xml etiketi \<HomePageHelpSettings >, Bölüm metni \<HomePageHelpSettingsText >.|
|topıbozulan. htm|Yerel küme içinde bir konu mevcut olduğunda, ancak bazı nedenlerle görüntülenemiyor (bozuk içerik).||
||< META_TOPIC_CORRUPTED_TITLE_ADD/>|Marka. xml, etiket \<Topıboztedtitle >|
||< TOPIC_CORRUPTED_SECTION_ADD/>|Marka. xml, etiket \<Topicboztedviewonlinetext >|
|topicnotfound. htm|Bir konu, yerel içerik kümesinde bulunamadığında veya çevrimiçi olarak kullanılabilir||
||< META_TOPIC_NOT_FOUND_TITLE_ADD/>|Marka. xml, etiket \<Topınotfoundtitle >|
||< META_TOPIC_NOT_FOUND_ID_ADD/>|Marka. xml, etiket \<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|
||< TOPIC_NOT_FOUND_SECTION_ADD/>|Marka. xml, etiket \<TopicNotFoundText >|
|contentnotyüklüyken. htm|Ürün için yerel içerik yüklü olmadığında.||
||< META_CONTENT_NOT_INSTALLED_TITLE_ADD/>|Marka. xml, etiket \<Contentnotınstalınstalınstaltada title >|
||< META_CONTENT_NOT_INSTALLED_ID_ADD/>|Marka. xml, Tag \<Contentnotınstalınstaldownloadcontenttext >|
||< CONTENT_NOT_INSTALLED_SECTION_ADD/>|Marka. xml, etiket \<Contentnotınstalınstalınstaltaınstalınstal>|

 **CSS dosyaları**

 Visual Studio Yardım Görüntüleyicisi markalama paketi, tutarlı Visual Studio yardım içeriği sunumunu desteklemeye yönelik iki CSS dosyası içerir:

- Marka. css – kendini Selfmarkalı = false olarak işlemek için CSS öğeleri içerir

- Printer. css – kendini Selfmarkalı = false olarak işlemek için CSS öğeleri içerir

  Marka. css dosyaları Visual Studio konu sunumu için tanımlar içerir (desteklenmediği uyarısıyla, paket hizmetinden >. mshc) Branding_\<yerel ayarda bulunan marka. css 'nin değişebilir.

  **Grafik dosyaları**

  Visual Studio içeriği, Visual Studio logosunun yanı sıra diğer grafikleri de görüntüler.  Visual Studio Yardım Görüntüleyicisi markalama paketindeki grafik dosyalarının tüm listesi aşağıda gösterilmiştir.

||||
|-|-|-|
|**Dosyasýný**|**Kullanırsınız**|**Örnekler**|
|Clear. gif|Daraltılabilir alanı işlemek için kullanılır||
|footer_slice. gif|Alt bilgi sunumu||
|info_icon. gif|Bilgiler görüntülenirken kullanılır|Sorumluluk reddi|
|online_icon. gif|Bu simge çevrimiçi bağlantılarla ilişkilendirilmelidir||
|tabLeftBD. gif|Kod parçacığı kapsayıcısını işlemek için kullanılır||
|tabRightBD. gif|Kod parçacığı kapsayıcısını işlemek için kullanılır||
|vs_logo_bk.gif|\<LogoFileName > marka. XML etiketinde tanımlandığı şekilde normal karşıtlık logo başvuruları için kullanılır.  Visual Studio ürünleri için logo adı vs_logo_bk. gif şeklindedir.||
|vs_logo_wh. gif|\<LogoFileNameHC > marka. XML etiketinde tanımlandığı şekilde normal yüksek logo başvuruları için kullanılır.  Visual Studio ürünleri için logo adı vs_logo_wh. gif şeklindedir.||
|ccOff. png|Resim yazısı grafiği||
|ccOn. png|Resim yazısı grafiği||
|Imaprite. png|Daraltılabilir alanı işlemek için kullanılır|genişletme veya daraltma grafiği|

### <a name="deploying-a-set-of-topics"></a>Konu kümesi dağıtma
 Bu, bir MSHA dosyasından ve konuları içeren Cabs veya MSHCs kümesinden oluşan bir Yardım Görüntüleyici içerik dağıtımı kümesi oluşturmaya yönelik basit ve hızlı bir öğreticidir. MSHA, bir cab veya MSHC dosyaları kümesini tanımlayan bir XML dosyasıdır. Yardım Görüntüleyicisi, içeriğin bir listesini almak için MSHA 'yı okuyabilir (. CAB veya. MSHC dosyaları) yerel yükleme için kullanılabilir.

 Bu yalnızca Yardım Görüntüleyicisi MSHA için en temel XML şemasını açıklayan bir öncü.  Bu kısa genel bakış ve örnek HelpContentSetup. msha altında örnek bir uygulama vardır.

 Bu öncü için MSHA adı, HelpContentSetup. msha ' dır (dosyanın adı uzantı ile herhangi bir şey olabilir). MSHA). HelpContentSetup. msha (aşağıdaki örnekte), var olan Cabs veya MSHCs 'nin bir listesini içermelidir.  Dosya türü MSHA içinde tutarlı olmalıdır (MSHA ve CAB dosya türlerinin bir birleşimini desteklemez). Her CAB veya MSHC için bir \<div Class = "Package" >...\</div > olmalıdır (aşağıdaki örneğe bakın).

 Note: aşağıdaki uygulama örneğinde marka paketini sunuyoruz. Gerekli Visual Studio içerik işleme öğelerini ve içerik davranışlarını almak için bu önemlidir.

 Örnek HelpContentSetup. msha dosyası: ("içerik kümesi adı 1" ve "içerik kümesi adı 2" vb. dosya adlarınızla değiştirin.)

```
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>.

```

1. "C:\SampleContent" gibi bir yerel klasör oluşturun

2. Bu örnek için, MSHC dosyalarını, konuları içerecek şekilde kullanacağız.  Bir MSHC, dosya uzantısının. zip ' den ' e değiştiği bir zip dosyasıdır. MSHC.

3. Aşağıdaki HelpContentSetup. msha dosyasını bir metin dosyası olarak oluşturun (dosyayı oluşturmak için Notepad kullanılmıştır) ve yukarıdaki belirtilen klasöre kaydedin (bkz. 1. adım).

   "Marka" sınıfı vardır ve benzersizdir. Bu temel markada, yüklenen içeriğin markalaması olacak ve MSHCs 'de bulunan içerik davranışları, marka paketinde bulunan uygun destek öğelerine sahip olacak şekilde bu şekilde eklenmiştir. Bu olmadan, sistem kopyalanan (yüklenmiş) içeriğin bir parçası olmayan destek öğelerini ararken hatalar oluşur.

   Visual Studio marka paketini edinmek için, Branding_en-US. mshc dosyasını C:\Program Files (x86) \Microsoft Help Viewer\v2,\ konumunda çalışma klasörünüze kopyalayın.

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>
<div class="package">
<span class="packageType">branding</span>
<span class="name">Branding_en-US</span>
<span class="deployed">True</span>
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>
</div>
</div>
</body>
</html>

```

 **Özet**

 Yukarıdaki adımların kullanılması ve genişletilmesi, VSPs 'nin içerik kümelerini Visual Studio yardım görüntüleyicisine dağıtmasına olanak sağlar.

### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Visual Studio Kabuğu 'na yardım ekleme (tümleşik ve yalıtılmış)
 **Giriş**

 Bu izlenecek yol, yardım içeriğinin bir Visual Studio Kabuğu uygulamasına nasıl ekleneceğini ve sonra nasıl dağıtılacağını göstermektedir.

 **Requirements**

1. [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]

2. [Yalıtılmış Kabuk yeniden dağıtım Visual Studio 2013](https://aka.ms/VS2013/IsoShell-LP/all)

   **Genel bakış**

   [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] kabuğu, bir uygulamayı temel alan [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] IDE 'nin bir sürümüdür. Bu tür uygulamalar, oluşturduğunuz uzantılarla birlikte yalıtılmış Kabuğu içerir. Uzantıları derlemek için [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] SDK 'sına dahil olan yalıtılmış Kabuk proje şablonlarını kullanın.

   Yalıtılmış kabuk tabanlı bir uygulama ve onun yardımını oluşturmaya yönelik temel adımlar:

3. [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] ISO kabuğu yeniden dağıtılabilir (bir Microsoft Download) alın.

4. Visual Studio 'da yalıtılmış Kabuğu temel alan bir yardım uzantısı oluşturun, örneğin, bu kılavuzda daha sonra açıklanan contoso yardım uzantısı.

5. Uzantıyı ve ISO kabuğunu yeniden dağıtılabilir bir dağıtım MSI (uygulama kurulumu) içine sarın. Bu Izlenecek yol, kurulum adımını içermez.

   Bir Visual Studio içerik deposu oluşturun. Tümleşik Kabuk senaryosunda, Visual Studio12 öğesini ürün kataloğu adı ile aşağıdaki gibi değiştirin:

- C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12. klasörü oluştur

- CatalogType. xml adlı bir dosya oluşturun ve klasöre ekleyin. Dosya aşağıdaki kod satırlarını içermelidir:

  ```
  <?xml version="1.0" encoding="UTF-8"?>
  <catalogType>UserManaged</catalogType>
  ```

  Kayıt defterinde içerik deposunu tanımlayın. Tümleşik Kabuk için VisualStudio12 öğesini ürün kataloğu adıyla değiştirin:

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

   Anahtar: LocationPath dize değeri: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12\en-US

   Anahtar: katalogadı dize değeri: [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] belgeleri

  **Projeyi Oluşturma**

  Yalıtılmış Kabuk uzantısı oluşturmak için:

1. Visual Studio 'da, **Dosya**altında **Yeni proje**' yi seçin, **diğer proje türleri** altında **genişletilebilirlik**' i seçin ve ardından **Visual Studio Kabuğu yalıtılmış**' i seçin. Visual Studio yalıtılmış Kabuk şablonunu temel alan bir genişletilebilirlik projesi oluşturmak için projeyi `ContosoHelpShell`olarak adlandırın.

2. Çözüm Gezgini, ContosoHelpShellUI projesinde, kaynak dosyaları klasöründe ApplicationCommands. vsct öğesini açın. Bu satırın açıklama olarak belirlendiğinden emin olun ("No_Help" araması yapın): `<!-- <define name=“No_HelpMenuCommands”/> -->`

3. **Hata ayıklamayı**derlemek ve çalıştırmak için F5 tuşunu seçin. Yalıtılmış Kabuk IDE 'nin deneysel örneğinde **Yardım** menüsünü seçin. **Görünüm yardım**, **Yardım Içeriği ekleme ve kaldırma**ve **Yardım tercihi** komutlarının göründüğünden emin olun.

4. Çözüm Gezgini ' de, ContosHelpShell projesinde, kabuk özelleştirme klasöründe ContosoHelpShell. pkgdef ' yi açın. Contoso Yardım kataloğunu tanımlamak için aşağıdaki satırları ekleyin:

   ```
    [$RootKey$\Help]
   "Product"="Contoso"
   "Catalog"="Contoso"
   “Version"="100"
   "BrandingPackage"="ContosoBrandingPackage.mshc"
   ```

5. Çözüm Gezgini ' de, ContosHelpShell projesinde, kabuk özelleştirme klasöründe, ContosoHelpShell. Application. pkgdef ' yi açın. F1 yardımını etkinleştirmek için aşağıdaki satırları ekleyin:

   ```
   // F1 Help Provider

   [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
   "Name"="13407"
   "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"
   @="Help3 Provider"
   [$RootKey$\HelpProviders]
   @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"
   [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
   "Name"="Help3 Provider"
   @="{4A791146-19E4-11D3-B86B-00C04F79F802}"
   ```

6. Çözüm Gezgini, ContosoHelpShell çözümünün bağlam menüsünde **Özellikler** menü öğesini seçin. **Yapılandırma özellikleri**altında **Configuration Manager**' yi seçin. **Yapılandırma** sütununda, her "Debug" değerini "Release" olarak değiştirin.

7. Çözümü oluşturun. Bu, bir sonraki bölümde kullanılacak olan bir yayın klasöründe bir dosya kümesi oluşturur.

   Bunu dağıtıldıktan sonra test etmek için:

8. Contoso 'yu dağıttığınız makinede, indirilen (yukarıdaki) ISO kabuğunu yükleyebilirsiniz.

9. \\\Program Files (x86)\\bir klasör oluşturun ve `Contoso`olarak adlandırın.

10. ContosoHelpShell sürüm klasöründeki içerikleri \\\Program Files (x86) \Contoso\ klasörüne kopyalayın.

11. **Başlat** menüsünde **Çalıştır** ' a ve `Regedit`girerek kayıt defteri düzenleyicisini başlatın. Kayıt Defteri Düzenleyicisi 'nde **Dosya**' yı ve ardından **içeri aktar**' ı seçin. ContosoHelpShell proje klasörüne gidin. ContosoHelpShell alt klasöründe ContosoHelpShell. reg ' yi seçin.

12. Bir içerik deposu oluşturun:

     ISO kabuğu için-Contoso içerik deposu oluşturma C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

     [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] Tümleşik Kabuk için C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12 klasörünü oluşturun

13. CatalogType. xml oluşturun ve şunu içeren içerik deposuna (önceki adım) ekleyin:

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

14. Aşağıdaki kayıt defteri anahtarlarını ekleyin:

     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12Key: LocationPath dize değeri:

     ISO kabuğu için:

     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12

     [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] Tümleşik Kabuk:

     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12en-US

     Anahtar: katalogadı dize değeri: [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] belgeleri. ISO kabuğu için bu, kataloğunuzun adıdır.

15. İçeriğinizi (Cabs veya MSHC ve MSHA) yerel bir klasöre kopyalayın.

16. İçerik deposunu test etmek için örnek tümleşik kabuk komut satırı. ISO kabuğu için, Katalog ve launchingApp değerlerini ürünle eşleşmesi için uygun şekilde değiştirin.

      "C:\Program Files (x86) \Microsoft Help Viewer\v2,\hlpviewer.exe"/katalogadı VisualStudio12/helpQuery method = "sayfa & ID = ContosoTopic0"/launchingApp Microsoft, VisualStudio, 12.0

17. Contoso uygulamasını başlatın (contoso uygulama kökünden). ISO kabuğu 'nda **Yardım** menü öğesini seçin ve **yerel yardım 'ı kullanmak**için **Yardım tercihini ayarla** ' yı değiştirin.

18. Kabuk içinde **Yardım** menü öğesini seçin ve ardından **Yardım 'ı görüntüleyin**. Yerel Yardım Görüntüleyicisi başlatması gerekir. **Içeriği Yönet** sekmesini seçin. **Yükleme kaynağı**altında **disk** seçenek düğmesini seçin. **...** Düğmesini seçin ve contoso içeriğini içeren yerel klasöre (Yukarıdaki adımda yerel klasöre kopyalanmış) gidin. HelpContentSetup. msha ' ı seçin. Contoso artık kitap seçimlerinde kitap olarak görünür olmalıdır. **Ekle**' yi seçin ve ardından **Güncelleştir** düğmesini (sağ alt köşedeki) seçin.

19. Contoso IDE içinde F1 işlevini test etmek için F1 tuşunu seçin.

### <a name="additional-resources"></a>Ek Kaynaklar

Çalışma zamanı API 'SI için bkz. [Windows Yardım API 'si](https://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx).

Yardım API 'sinin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Yardım Görüntüleyicisi kod örnekleri](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples).

Sorunları ortadan kaldırma ile ilgili güncelleştirmeler için bkz. [Yardım Görüntüleyicisi Benioku](https://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409).