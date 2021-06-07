---
title: SDK Microsoft Yardım Görüntüleyicisi | Microsoft Docs
description: Bir makale oluşturma, Yardım Görüntüleyicisi içeriği oluşturma ve bir makale kümesi dağıtma gibi Visual Studio Yardım Görüntüleyicisi görevleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8bc2ed473e25dc75d0155bc864aa02c157e3482f
ms.sourcegitcommit: f430d014f912aa7874e1db65026dc72688b973e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111448330"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Yardım Görüntüleyicisi SDK’sı

Bu makale, Visual Studio Yardım Görüntüleyicisi tümleştiricileri için aşağıdaki görevleri içerir:

- Konu oluşturma (F1 desteği)

- Yardım Görüntüleyici içeriği oluşturma-marka paketi

- Makale kümesi dağıtma

- Visual Studio Kabuğu 'na yardım ekleme (tümleşik veya yalıtılmış)

- Ek Kaynaklar

## <a name="create-a-topic-f1-support"></a>Konu oluşturma (F1 desteği)

Bu bölümde, sunulan konunun bileşenlerine genel bir bakış sunulmaktadır. konu gereksinimleri, bir konunun nasıl oluşturulacağı hakkında kısa bir açıklama (F1 destek gereksinimleri dahil) ve son olarak, işlenen sonucuyla ilgili örnek bir konu.

**Yardım Görüntüleyicisi konusuna genel bakış**

İşleme için bir konu çağrıldığında, Yardım Görüntüleyicisi, Install veya Last Update sırasında konuyla ilişkili olan marka paketi öğelerini XHTML konusuyla birlikte alır ve bunları, sunulan içerik görünümü (marka verileri + konu verileri) sonucu olarak birleştirir.  Marka paketi logo, içerik davranışları desteği ve marka metni (telif hakkı vb.) içerir.  Marka paketi öğeleri hakkında daha fazla bilgi için aşağıdaki "marka paketi oluşturma" konusuna bakın.  Konuyla ilişkili bir marka paketi olmadığı durumda, Yardım Görüntüleyicisi Yardım Görüntüleyici uygulama kökünde (Branding_en-US. mshc) bulunan geri dönüş markalama paketini kullanır.

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

- javascript

- CSharp veya c #

- CPlusPlus veya VisualC + + ya da c++

- j

- VisualBasic veya vb

- f # veya FSharp veya FS

- diğer-bir dil adını temsil eden bir dize

**Yardım Görüntüleyici konusu oluşturma**

ContosoTopic4.htm adlı yeni bir XHTML belgesi oluşturun ve başlık etiketini (aşağıda) ekleyin.

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

Daha sonra, konunun nasıl sunulacağınızı (kendi kendine markalı veya değil) tanımlamak için veri ekleyin, bu konunun TOC içinde olduğu, KIMLIĞI (diğer konuların bağlantı başvurusu için) vb. bu konunun bulunduğu F1 için nasıl başvurulacağını tanımlayın. Desteklenen meta verilerin tüm listesi için aşağıdaki "Içerik meta verileri" tablosuna bakın.

- Bu durumda, Visual Studio Yardım Görüntüleyicisi markalama paketinin bir türevi olan kendi marka paketimizi kullanacağız.

- IDE Özellik paketinde verilen F1 değeri ile eşleşecek F1 meta adı ve değerini ("Microsoft. help. F1" content = "ContosoTopic4") ekleyin. (Daha fazla bilgi için F1 support bölümüne bakın.) Bu, IDE 'de F1 seçildiğinde bu konuyu göstermek için IDE içindeki F1 çağrısıyla eşleşen değerdir.

- Konu KIMLIĞINI ekleyin. Bu konuya bağlantı sağlamak için diğer konular tarafından kullanılan dizedir. Bu konu, Yardım Görüntüleyicisi KIMLIĞIDIR.

- TOC için, bu konunun üst düğümünü ekleyerek TOC düğümünün bu konu başlığının nerede görüneceğini belirleyin.

- TOC için, bu konunun düğüm sırasını ekleyin. Üst düğümün `n` alt düğüm sayısı olduğunda, bu konunun konumunun alt düğümlerinin sırasını belirleyin. Örneğin, bu konu 4 ' ün 4 alt konu konusunun sayısıdır.

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

1. Konu başlığı etiketi ekleyin:  `<div class="title">Contoso Topic 4</div>`

2. Bir dekont bölümü ekleyin: `<div class="alert"> add your table tag and text </div>`

3. Daraltılabilir bir alan ekleyin:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Kod parçacığı ekleyin:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Kod diline özgü metin ekleme:  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` `devLangnu=` diğer dilleri girmenizi sağlayan unutmayın. Örneğin, `devLangnu="Fortran"` kod parçacığı DisplayLanguage = FORTRAN olduğunda FORTRAN öğesini görüntüler.

6. Sayfa bağlantıları ekle: `<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Note: desteklenmeyen yeni "görüntüleme dili" (örnek, F #, COBOL, FORTRAN) için kod parçacığında tek renkli olacak kod renklendirme.

**Örnek Yardım Görüntüleyicisi konusu** Kod, meta verilerin, kod parçacığının, daraltılabilir alanın ve dile özgü metinlerin nasıl tanımlanacağını gösterir.

```html
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
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>
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
        <a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>
```

**F1 desteği**

Visual Studio 'da, F1 ' i seçtiğinizde, imlecin IDE içinde yerleştirilmesiyle sağlanan değerler oluşturulur ve bir "özellik paketi" ' ni sağlanan değerlerle doldurur (imleç konumuna göre). İmleç özellik x 'in üzerindeyken, özellik x etkin/odağa sahiptir ve özellik paketini değerlerle doldurur.  F1 seçildiğinde, özellik paketi doldurulur ve Visual Studio F1 kodu, müşterilerin varsayılan yardım kaynağının yerel mi yoksa çevrimiçi mi olduğunu (çevrimiçi olarak varsayılan) görür. ardından, kullanıcılar ayarına göre uygun dizeyi oluşturur (varsayılan olarak çevrimiçi)-Shell yürütme (varsayılan olarak, exe başlatma parametreleri için yardım Yönetici Kılavuzu), yerel yardım varsayılan ise özellik çantasından yerel Yardım Görüntüleyicisi + anahtar kelimeleridir. ya da parametre listesindeki anahtar kelimesiyle MSDN URL 'SI.

Birden çok değerli dize olarak adlandırılan F1 için üç dize döndürülürse, ilk terimi alın, bir isabet arayın ve bulunursa, bu işlemi yaptık; Aksi takdirde, sonraki dizeye geçin.  Sıralama önemli. Çok değerli anahtar sözcüklerin sunumu, en kısa dize için en uzun dize olmalıdır.  Bunu, birden çok değerli anahtar kelimelerinde doğrulamak için, seçilen anahtar sözcüğü içerecek şekilde çevrimiçi F1 URL dizesine bakın.

Visual Studio 2012 ' de, özellikle çevrimiçi ve çevrimdışı arasında daha güçlü bir bölme yaptık, böylece Kullanıcı ayarı çevrimiçi hale getirilseydi, bu durumda, Visual Studio 2010 ' de bulunan Yardım Kitaplığı Aracısı aracılığıyla yönlendirmek yerine doğrudan MSDN 'deki çevrimiçi sorgu hizmetimize F1 isteğini geçirdik. Daha sonra, bu bağlamda farklı bir şey yapılıp yapılmayacağını öğrenmek için "satıcı içeriği yüklendi = true" durumuna güveniyoruz. Bu değer true ise, müşterileriniz için desteklemek istediğiniz seçeneğe bağlı olarak bu ayrıştırma ve yönlendirme mantığını gerçekleştirirsiniz. Yanlış ise MSDN 'ye gitmeniz yeterlidir. Kullanıcının ayarı yerel ise, tüm çağrılar yerel yardım altyapısına gider.

F1 akış diyagramı:

![F1 akışı](../../extensibility/internals/media/f1flow.png "F1flow")

Yardım Görüntüleyicisi varsayılan yardım içerik kaynağı çevrimiçi olarak ayarlandığında (tarayıcıda Başlat):

- Visual Studio Iş ortağı (VSP) özellikleri, F1 özellik paketine (özellik paketi öneki. anahtar sözcüğü ve kayıt defterinde bulunan ön ek için çevrimiçi URL) bir değer yayar: F1 tarayıcıya bir VSP URL + parametreleri gönderir.

- Visual Studio özellikleri (dil Düzenleyicisi, Visual Studio 'ya özgü menü öğeleri vb.): F1 tarayıcıya bir Visual Studio URL 'SI gönderir.

Yardım Görüntüleyicisi varsayılan yardım içerik kaynağı yerel yardım (yardım görüntüleyicisinde Başlat) olarak ayarlandığında:

- F1 özellik paketi ile yerel depo dizini (diğer bir deyişle, özellik paketi öneki. anahtar sözcük = yerel depo dizininde bulunan değer) arasında anahtar sözcük eşleşme olan VSP özellikleri: F1, yardım görüntüleyicisindeki konuyu işler.

- Visual Studio özellikleri (VSP 'nin Visual Studio özelliklerinden yayılan özellik paketini geçersiz kılmasına yönelik bir seçenek): F1, yardım görüntüleyicisinde bir Visual Studio konusu oluşturur.

Satıcı yardım içeriği için F1 geri dönüşü etkinleştirmek üzere aşağıdaki kayıt defteri değerlerini ayarlayın. F1 geri dönüş, Yardım Görüntüleyicisi 'nin çevrimiçi F1 Yardım içeriğine bakmak üzere ayarlandığı ve satıcının içeriğinin yerel olarak kullanıcının sabit sürücüsüne yüklendiği anlamına gelir. Yardım Görüntüleyicisi, içerik için yerel yardım 'a bakmalıdır, ancak varsayılan ayar çevrimiçi yardım için olsa bile.

1. Yardım 2,3 kayıt defteri anahtarı altındaki **Vendorcontent** değerini ayarlayın:

   - 32 bit işletim sistemleri için:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent" = DWORD: 00000001

   - 64 bit işletim sistemleri için:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent" = DWORD: 00000001

2. İş ortağı ad alanını yardım 2,3 kayıt defteri anahtarı altına kaydedin:

   - 32 bit işletim sistemleri için:

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner<em> \\<ad \> alanı</em>

      "konum" = "çevrimdışı"

   - 64 bit işletim sistemleri için:

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner<em> \\<ad \> alanı</em>

      "konum" = "çevrimdışı"

**Temel yerel ad alanı ayrıştırma**

Temel yerel ad alanı ayrıştırmayı açmak için, kayıt defterinde şu ada sahip yeni bir DWORD ekleyin: BaseNativeNamespaces ve değerini 1 olarak ayarlayın (desteklemek istedikleri Katalog anahtarı altında).  Örneğin, Visual Studio kataloğunu kullanmak istiyorsanız, anahtarı yola ekleyebilirsiniz:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

ÜST BILGIDE/YÖNTEMDE bir F1 anahtar kelimesiyle karşılaşıldığında, '/' karakteri ayrıştırılır ve bu da aşağıdaki yapının oluşmasına neden olur:

- ÜST BILGI: kayıt defterine kaydolmak için kullanılabilecek ad alanı olacaktır

- Yöntem: Bu, üzerinden geçirilen anahtar sözcük olur.

Örneğin, CustomLibrary adlı özel bir kitaplık ve MyTestMethod adlı bir yöntem verildiğinde bir F1 isteği geldiğinde olarak biçimlendirilir `CustomLibrary/MyTestMethod` .

Kullanıcı daha sonra CustomLibrary 'yi Iş ortakları Hive altında ad alanı olarak kaydedebilir ve istediği konum anahtarını sağlayabilir ve sorguya geçirilen anahtar sözcük MyTestMethod olur.

**IDE 'de yardım hata ayıklama aracında etkinleştirme**

Aşağıdaki kayıt defteri anahtarını ve değerini ekleyin:

::: moniker range="vs-2017"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic Help**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Dynamic Help**

::: moniker-end

Değer: perakende verilerinde hata ayıklama çıkışını görüntüle: Evet

IDE 'de, yardım menüsü öğesi altında **Hata Ayıkla yardım bağlamı**' nı seçin.

**İçerik meta verileri**

Aşağıdaki tabloda, köşeli ayraçlar arasında görünen tüm dizeler, tanınan bir değerle değiştirilmelidir. Örneğin, \<meta name="Microsoft.Help.Locale" content="[language code]" /> "[Language Code]", "en-US" gibi bir değer ile değiştirilmelidir.

| Özellik (HTML temsili) | Açıklama |
| - | - |
| \< meta name="Microsoft.Help.Locale" content="[language-code]" /> | Bu konu için bir yerel ayar ayarlar. Bu etiket bir konu başlığında kullanılıyorsa, yalnızca bir kez kullanılması gerekir ve diğer Microsoft Yardım etiketlerinin üzerine eklenmelidir. Bu etiket kullanılmazsa, konunun gövde metni, belirtilen ürün yerel ayarıyla ilişkili sözcük kesici kullanılarak dizinlenir; Aksi halde, en-US sözcük kesici kullanılır. Bu etiket, ıSOC RFC 4646 ' e uygundur. Microsoft Yardım 'ın doğru şekilde çalıştığından emin olmak için, genel dil özniteliği yerine bu özelliği kullanın. |
| \< meta name="Microsoft.Help.TopicLocale" content="[language-code]" /> | Diğer yerel ayarlar da kullanıldığında, bu konu için bir yerel ayar ayarlar. Bu etiket bir konu başlığında kullanılıyorsa, yalnızca bir kez kullanılmalıdır. Katalog birden fazla dilde içerik içerdiğinde bu etiketi kullanın. Bir katalogdaki birden çok konu aynı KIMLIĞE sahip olabilir, ancak her birinin benzersiz bir Topılocale belirtmesi gerekir. Kataloğun yerel ayarıyla eşleşen bir Topılocale belirten konu, içindekiler tablosunda görüntülenen konudur. Ancak, konunun tüm dil sürümleri arama sonuçlarında görüntülenir. |
| \< title>Başlığın\</title> | Bu konunun başlığını belirtir. Bu etiket gereklidir ve konunun yalnızca bir kez kullanılması gerekir. Konunun gövdesi bir başlık \<div> bölümü içermiyorsa, bu başlık konu başlığında ve içindekiler tablosunda görüntülenir. |
| \< meta name=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/> | Yardım görüntüleyicisinin Dizin bölmesinde görüntülenen bir bağlantının metnini belirtir. Bağlantıya tıklandığında konu görüntülenir. Bir konu için birden çok dizin anahtar sözcüğü belirtebilir veya bu konunun bağlantılarının dizinde görünmesini istemiyorsanız bu etiketi atlayabilirsiniz. Önceki yardım sürümlerindeki "K" anahtar sözcükleri bu özelliğe dönüştürülebilir. |
| \< meta name="Microsoft.Help.Id" content="[TopicID]"/> | Bu konu için tanımlayıcıyı ayarlar. Bu etiket gereklidir ve konunun yalnızca bir kez kullanılması gerekir. KIMLIğIN aynı yerel ayara sahip olan katalogdaki konular arasında benzersiz olması gerekir. Başka bir konu başlığında, bu KIMLIĞI kullanarak bu konuya bir bağlantı oluşturabilirsiniz. |
| \< meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | Bu konu için F1 anahtar sözcüğünü belirtir. Bir konu için birden çok F1 anahtar sözcüğü belirtebilir veya bu konunun, bir uygulama kullanıcısı F1 tuşuna bastığında görüntülenmesini istemiyorsanız bu etiketi atlayabilirsiniz. Genellikle, bir konu için yalnızca bir F1 anahtar sözcüğü belirtilir. Önceki yardım sürümlerindeki "F" anahtar sözcükleri bu özelliğe dönüştürülebilir. |
| \< meta name="Description" content="[topic description]" /> | Bu konudaki içeriğin kısa bir özetini sağlar. Bu etiket bir konu başlığında kullanılıyorsa, yalnızca bir kez kullanılmalıdır. Bu özelliğe doğrudan sorgu kitaplığı tarafından erişilir; Dizin dosyasında depolanmaz. |
| meta Name = "Microsoft. help. TocParent" içerik = "[parent_Id]"/> | İçindekiler tablosunda bu konunun üst konusunu belirtir. Bu etiket gereklidir ve konunun yalnızca bir kez kullanılması gerekir. Değer, üst öğenin Microsoft.Help.Id. Bir konu, içindekiler tablosunda tek bir konuma sahip olabilir. "-1", TOC kökünün konu KIMLIĞI olarak değerlendirilir. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]' De, Bu sayfa Yardım Görüntüleyicisi giriş sayfasıdır. Bu, en üst düzeyde gösterildiklerinden emin olmak için bazı konulara özel olarak TocParent =-1 eklediğimiz nedenidir. Yardım Görüntüleyicisi giriş sayfası bir sistem sayfasıdır ve bu nedenle yok edilir. VSP, KIMLIĞI-1 olan bir sayfa eklemeye çalışırsa, bu, içerik kümesine eklenebilir, ancak Yardım Görüntüleyicisi her zaman sistem sayfasını kullanır. Yardım Görüntüleyicisi giriş |
| \< meta name="Microsoft.Help.TocOrder" content="[positive integer]"/> | Bu konunun içerik tablosunda, eşi konularına göre göründüğünü belirtir. Bu etiket gereklidir ve konunun yalnızca bir kez kullanılması gerekir. Değer bir tamsayıdır. Daha yüksek değerli bir tamsayıyı belirten konunun üzerinde bir alt değer tamsayı belirten bir konu görüntülenir. |
| \< meta name="Microsoft.Help.Product" content="[product code]"/> | Bu konunun açıkladığı ürünü belirtir. Bu etiket bir konu başlığında kullanılıyorsa, yalnızca bir kez kullanılmalıdır. Bu bilgiler, Yardım dizin oluşturucuya geçirilen bir parametre olarak da sağlanabilir. |
| \< meta name="Microsoft.Help.ProductVersion" content="[version number]"/> | Bu konunun açıkladığı ürünün sürümünü belirtir. Bu etiket bir konu başlığında kullanılıyorsa, yalnızca bir kez kullanılmalıdır. Bu bilgiler, Yardım dizin oluşturucuya geçirilen bir parametre olarak da sağlanabilir. |
| \< meta name="Microsoft.Help.Category" content="[string]"/> | İçeriğin alt bölümleri tanımlamak için ürünler tarafından kullanılır. Bir konu için birden çok alt bölüm tanımlayabilir veya bağlantıların herhangi bir alt bölümleri belirlemesine izin istemiyorsanız bu etiketi atlayabilirsiniz. Bu etiket, bir konu yardım 'ın önceki bir sürümünden dönüştürüldüğünde TargetOS ve Targetframeworkbilinen özniteliklerini depolamak için kullanılır. İçeriğin biçimi AttributeName: AttributeValue. |
| \< meta name="Microsoft.Help.TopicVersion content="[topic version number]"/> | Bir katalogda birden fazla sürüm mevcut olduğunda konusunun bu sürümünü belirtir. Microsoft.Help.Id 'in benzersiz olması garanti edilmediği için, bir katalogda bir konunun birden fazla sürümü varsa, örneğin bir katalog .NET Framework 3,5 için bir konu ve .NET Framework 4 ' ü ve her ikisi de aynı Microsoft.Help.Id öğesine sahip olduğunda bu etiket gereklidir. |
| \< meta name="SelfBranded" content="[TRUE or FALSE]"/> | Bu konunun Yardım Kitaplığı Yöneticisi başlangıç marka paketini veya konuya özgü bir marka paketini kullanıp kullanmadığını belirtir. Bu etiket doğru ya da yanlış olmalıdır. DOĞRU ise, ilişkili konunun marka paketi, Yardım Kitaplığı Yöneticisi başladığında ayarlanan marka paketini geçersiz kılar, böylece konu diğer içeriğin işlenmesinin dışında olsa bile, konunun istendiği şekilde işlenir. YANLıŞ ise, Yardım Kitaplığı Yöneticisi başladığında ayarlanan marka paketine göre geçerli konu oluşturulur. Varsayılan olarak, Yardım Kitaplığı Yöneticisi kendini markalamayı doğru olarak bildirmediği sürece yanlış olarak kabul eder; Bu nedenle, bildirmeniz gerekmez \<meta name="SelfBranded" content="FALSE"/> . |

## <a name="create-a-branding-package"></a>Marka paketi oluşturma

Visual Studio sürümü, Visual Studio Iş ortakları için yalıtılmış ve tümleşik kabuklar da dahil olmak üzere birçok farklı Visual Studio ürününü kapsar.  Bu ürünlerin her biri, ürüne özel olarak bazı konu tabanlı yardım içeriği marka desteği gerektirir.  Örneğin, Visual Studio konularının tutarlı bir marka sunumu olması gerekir, ancak ISO kabuğunu sarmalayan SQL Studio, her konu için kendi benzersiz yardım içeriği markalamasını gerektirir.  Tümleşik bir kabuk Iş ortağı, kendi konu markalarını koruyarak Yardım konularının üst Visual Studio ürün Yardım içerikleri dahilinde olmasını isteyebilir.

Marka paketleri, Yardım Görüntüleyicisi 'Ni içeren ürün tarafından yüklenir.  Visual Studio ürünleri için:

- Yardım Görüntüleyicisi \<locale> 2,3 uygulama kökünde (örnek: C:\Program Files (x86) \Microsoft yardım Viewer\v2.3) Yardım Görüntüleyici dil paketi 'ne bir geri dönüş marka paketi (Branding_. mshc) yüklenir.  Bu, ürün markası paketinin yüklü olmadığı (içerik yüklenmemiş) veya yüklü marka paketinin bozuk olduğu durumlarda kullanılır.  Uygulama kök geri dönüş markalama paketi kullanıldığında Visual Studio öğeleri (logo ve geri bildirim) yok sayılır.

- İçerik paketi hizmetinden Visual Studio içeriği yüklendiğinde, bir marka paketi de yüklenir (ilk kez içerik yükleme senaryosu için).  Marka paketine yönelik bir güncelleştirme varsa, güncelleştirme sonraki içerik güncelleştirmesi veya ek paket yükleme eylemi gerçekleştiğinde yüklenir.

Microsoft Yardım Görüntüleyicisi konu meta verilerine dayalı olarak konuların markalamasını destekler.

- Konu meta verileri kendi kendine markalı = doğru tanımlar, konuyu olduğu gibi işler, hiçbir şey yapmaz (marka olarak en fazla).

- Konu meta verileri kendi kendine markalı = false tanımlıyor, TopicVendor meta veri değeriyle ilişkili marka paketini kullanın.

- Konu meta verileri name = "Microsoft. help. TopicVendor" Content = tanımlar \< branding package name in vendor MSHA> , içerik değerinde tanımlanan marka paketini kullanın.

- Visual Studio kataloğu 'nda, marka paketlerinin öncelikli bir uygulaması vardır.  İlk Visual Studio varsayılan markası uygulanır ve ardından konu meta verilerinde tanımlandıysa ve ilişkili marka paketiyle (yükleme msha bölümünde tanımlandığı gibi) destekleniyorsa, satıcı tanımlı marka bir geçersiz kılma olarak uygulanır.

Marka öğeleri genellikle üç ana kategoriye ayrılır:

- Üstbilgi öğeleri (örnek geri bildirim bağlantısı, koşullu vazgeçme metni, logo)

- İçerik davranışları (denetim metni öğelerini ve kod parçacığı öğelerini genişletme/daraltma örnekleri)

- Alt bilgi öğeleri (örneğin Telif Hakkı)

Markalı öğeler olarak kabul edilen öğeler şunlardır (bu özellikte ayrıntılı olarak açıklandı):

- Katalog/ürün logosu (örnek, Visual Studio)

- Geri bildirim bağlantısı ve e-posta öğeleri

- Sorumluluk reddi metni

- Telif hakkı metni

Yardım Görüntüleyicisi markalama paketinde Visual Studio dosyaları şunlardır:

- Grafikler (logolar, simgeler vb.)

- Branding.js - içerik davranışlarını destekleyen betik dosyaları

- Branding.xml - katalog içeriği arasında tutarlı olarak kullanılan dizeler.  Not: Visual Studio metin öğelerini yerelleştirmeye eklemek branding.xml" _locID=" \<unique value> "

- Branding.css - sunum tutarlılığı için stil tanımları

- Print.css - tutarlı yazdırılmış sunu için stil tanımları

Yukarıda belirtildiği gibi MarkaLama Paketleri şu konu başlığıyla ilişkilendirilmektedir:

- Meta verilerde SelfBranded = false tanımlandığı zaman, konu katalog markalama paketini devralıyor

- Veya SelfBranded = false olduğunda ve MSHA'da tanımlanan ve içerik yüklenirken kullanılabilen benzersiz bir Marka Paketi olduğunda

ÖZEL marka paketleri (VSP içeriği, SelfBranded=True) uygulayan VSP'ler için devam etme yollarından biri geri dönüş marka paketiyle (Yardım Görüntüleyicisi ile birlikte yüklenir) başlamak ve dosyanın adını uygun şekilde değiştirmektir.  .mshc Branding_ dosyası, dosya uzantısı .mshc olarak değiştirilmiş bir zip dosyasıdır, bu nedenle uzantıyı \<locale> .mshc yerine .mshc olarak .zip ve içeriği ayıklamanız gerekir.  Paket öğelerini markalama ve uygun şekilde değiştirme (örneğin, logoyu VSP logosuyla ve Branding.xml dosyasındaki logo başvurusuyla değiştirme, VSP özelliklerine göre Branding.xml güncelleştirme gibi) için aşağıya bakın.

Tüm değişiklikler tamamlansa, istenen marka öğelerini içeren bir zip dosyası oluşturun ve uzantıyı .mshc olarak ayarlayın.

Özel markalama paketini ilişkilendirmek için, markalama mshc dosyasının başvurularını ve mshc içeriğini içeren (konuları içeren) MSHA'yı oluşturun.  Temel bir MSHA oluşturma hakkında bilgi için aşağıdaki "MSHA"ya bakın.

Dosya Branding.xml, konu başlığında yer alan belirli öğeleri tutarlı bir şekilde işlemek için kullanılan öğelerin listesini \<meta name="Microsoft.Help.SelfBranded" content="false"/> içerir.  Visual Studio dosyasındaki öğelerin Branding.xml listesi aşağıda listelenmiştir.  Bu liste, ISO Shell'i benimseyenler için şablon olarak kullanılmak üzere tasarlanmıştır ve bu öğelerde (logo, geri bildirim ve Telif Hakkı gibi) kendi ürün markalama ihtiyaçlarını karşılayacak şekilde değişikliklerini sağlar.

Not: "{n}" tarafından not alan değişkenlerin kod bağımlılıkları vardır. Bu değerlerin kaldırılması veya değiştirilmesi hatalara ve büyük olasılıkla uygulama kilitlenmeye neden olur. Yerelleştirme tanımlayıcıları (_locID="codesnippet.n") Visual Studio Paketi'ne dahil edilir.

**Branding.xml**

| Öğe | Açıklama |
| - | - |
| Özelliği: | **Daraltılabilir Alan** |
| Kullanın: | Genişlet, içerik denetimi metnini daraltıyor |
| **Öğe** | **Değer** |
| ExpandText | Genişlet |
| DaraltMetin | Daralt |
| Özelliği: | **CodeSnippet** |
| Kullanın: | Kod parçacığı denetim metni.  Not: "HataYa Neden Olmayan" alana sahip kod parçacığı içeriği boşluk olarak değiştirilir. |
| **Öğe** | **Değer** |
| CopyToClipboard | Panoya kopyala |
| ViewColorizedText | Renklendirmeyi Görüntüle |
| CombinedVBTabDisplayLanguage | Visual Basic (Örnek) |
| VBDeclaration | Bildirim |
| VBUsage | Kullanım |
| Özelliği: | **Geri Bildirim, Alt Bilgi ve Logo** |
| Kullanın: | Müşterinin e-posta yoluyla geçerli konu hakkında geri bildirim sağlaması için bir Geri Bildirim denetimi sağlama.  İçerik için telif hakkı metni.  Logo tanımı. |
| **Öğe** | **Değer (Bu dizeler içeriği benimseyenin ihtiyaçlarını karşılayacak şekilde değiştirilebilir.)** |
| Telif hakkı | © 2013 Microsoft Corporation. All rights reserved. |
| SendFeedback | \<a href="{0}" {1}>Bu konu hakkında \</a> Microsoft'a Geri Bildirim gönderin. |
| FeedbackLink | |
| LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| Özelliği: | **Bildirim** |
| Kullanın: | Makine tarafından çevrilmiş içerik için büyük/küçük harfe özgü bir sorumluluk reddi kümesi. |
| **Öğe** | **Değer** |
| MT_Editable | Bu makale makine çevirisidir. İnternet bağlantınız varsa, bu sayfayı aynı anda özgün İngilizce içerikle düzenlenebilir modda görüntülemek için "Bu konuyu çevrimiçi görüntüle"yi seçin. |
| MT_NonEditable | Bu makale makine çevirisidir. İnternet bağlantınız varsa, bu sayfayı aynı anda özgün İngilizce içerikle düzenlenebilir modda görüntülemek için "Bu konuyu çevrimiçi görüntüle"yi seçin. |
| MT_QualityEditable | Bu makale el ile çevrildi. İnternet bağlantınız varsa, bu sayfayı aynı anda özgün İngilizce içerikle düzenlenebilir modda görüntülemek için "Bu konuyu çevrimiçi görüntüle"yi seçin. |
| MT_QualityNonEditable | Bu makale el ile çevrildi. İnternet bağlantınız varsa, bu sayfayı aynı anda özgün İngilizce içerikle düzenlenebilir modda görüntülemek için "Bu konuyu çevrimiçi görüntüle"yi seçin. |
| MT_BetaContents | Bu makale, bir ön sürüm için makine çevirisidir. İnternet bağlantınız varsa, bu sayfayı aynı anda özgün İngilizce içerikle düzenlenebilir modda görüntülemek için "Bu konuyu çevrimiçi görüntüle"yi seçin. |
| MT_BetaRecycledContents | Bu makale bir ön sürüm için el ile çevrilmiştir. Bir Internet bağlantınız varsa, bu sayfayı orijinal Ingilizce içeriğiyle aynı anda düzenlenebilir modda görüntülemek için "Bu konuyu çevrimiçi görüntüle" seçeneğini belirleyin. |
| Özellik | **LinkTable** |
| Kullanırsınız | Çevrimiçi konu bağlantıları desteği |
| **Öğe** | **Değer** |
| LinkTableTitle | Tablo bağla |
| Topicenulınktext | \</a>Bilgisayarınızda mevcut olan bu konunun İngilizce sürümünü görüntüleyin. |
| Topiconlinelink metni | Bu konuyu \<a href="{0}" {1}> çevrimiçi görüntüleyin\</a> |
| OnlineText | Çevrimiçi |
| Özellik | **Video ses denetimi** |
| Kullanırsınız | Video içeriği için öğeleri ve metni görüntüleme |
| **Öğe** | **Değer** |
| MultiMediaNotSupported | İçeriği desteklemek için Internet Explorer 9 veya üzeri yüklü olmalıdır {0} . |
| VideoText | videoyu görüntüleme |
| AudioText | ses akışı |
| Onlinevideolınktext | \<p>Bu konuyla ilişkili videoyu görüntülemek için {0} \<a href="{1}"> {2} buraya tıklayın \</a> .\</p> |
| Onlinesesolınktext | \<p>Bu konuyla ilişkili sesi dinlemek için {0} \<a href="{1}"> {2} buraya tıklayın \</a> .\</p> |
| Özellik | **İçerik yüklü değil denetimi** |
| Kullanırsınız | contentnotinstalled.htm işleme için kullanılan metin öğeleri (dizeler) |
| **Öğe** | **Değer** |
| Contentnotınstalınstalınstalde başlığı | Bilgisayarınızda içerik bulunamadı. |
| Contentnotınstalınstaldownloadcontenttext | \<p>İçeriği bilgisayarınıza indirmek için \<a href="{0}" {1}> Yönet sekmesine tıklayın \</a> .\</p> |
| Contentnotınstalınstalınstalde metni | \<p>Bilgisayarınızda yüklü içerik yok. Yerel Yardım içeriği yüklemesi için yöneticinize başvurun.\</p> |
| Özellik | **Konu bulunamadı denetimi** |
| Kullanırsınız | topicnotfound.htm işleme için kullanılan metin öğeleri (dizeler) |
| **Öğe** | **Değer** |
| Topınotfoundtitle | İstenen konu bilgisayarınızda bulunamıyor. |
| Topınotfoundviewonlinetext | \<p>İstediğiniz konu bilgisayarınızda bulunamadı, ancak \<a href="{0}" {1}> konuyu çevrimiçi olarak görebilirsiniz \</a> .\</p> |
| TopicNotFoundDownloadContentText | \<p>Benzer konuların bağlantıları için gezinti bölmesine bakın veya \<a href="{0}" {1}> \</a> içeriği bilgisayarınıza Indirmek için Yönet sekmesine tıklayın.\</p> |
| Topınotfoundmetni | \<p>İstediğiniz konu bilgisayarınızda bulunamadı.\</p> |
| Özellik | **Konu başlığı bozuk denetimi** |
| Kullanırsınız | topiccorrupted.htm işleme için kullanılan metin öğeleri (dizeler) |
| **Öğe** | **Değer** |
| Topıbozuk Tedtitle | İstenen konu gösterilemiyor. |
| Topıboztedviewonlinetext | \<p>Yardım Görüntüleyicisi istenen konuyu görüntüleyemiyor. Konunun içeriğinde veya temeldeki sistem bağımlılığında bir hata olabilir.\</p> |
| Özellik | **Giriş sayfası denetimi** |
| Kullanırsınız | Yardım Görüntüleyicisi üst düzey düğüm içeriğinin görüntülenmesini destekleyen metin. |
| **Öğe** | **Değer** |
| HomePageTitle | Yardım Görüntüleyicisi giriş sayfası |
| Homepagetanıtımı | \<p>Microsoft araçları, ürünleri, teknolojileri ve hizmetleri kullanan herkese yönelik önemli bir bilgi kaynağı olan Microsoft Yardım Görüntüleyicisi hoş geldiniz. Yardım Görüntüleyicisi, nasıl yapılır ve başvuru bilgilerine, örnek koda, teknik makalelere ve daha fazlasına erişmenizi sağlar. İhtiyacınız olan içeriği bulmak için içindekiler tablosuna göz atarak tam metin aramasını kullanın veya anahtar sözcük dizinini kullanarak içerik üzerinde gezinin.\</p> |
| Homepagecontentınstalltext | \<p>\<br />\<a href="{0}" {1}>İçeriği Yönet sekmesini kullanarak \</a> şunları yapın: \<ul> \<li> bilgisayarınıza içerik ekleyin. \</li> \<li> Yerel içeriklerinizin güncelleştirmelerini denetleyin. \</li> \<li> İçeriği bilgisayarınızdan kaldırın.\</li>\</ul>\</p> |
| Homepageınstalınstalbook defterleri | Yüklü kitaplar |
| Homepagenobooksyüklü | Bilgisayarınızda içerik bulunamadı. |
| HomePageHelpSettings | Yardım Içeriği ayarları |
| HomePageHelpSettingsText | \<p>Geçerli ayarınız yerel yardımdır. Yardım Görüntüleyicisi bilgisayarınıza yüklediğiniz içeriği görüntüler. \<br /> Yardım içeriği kaynağınızı değiştirmek için, Visual Studio menü çubuğunda \<span style="{0}"> Yardım, yardım tercihi ayarla ' yı seçin \</span> .\<br />\</p> |
| Karşılık | MB |

**branding.js**

branding.js dosyası, Visual Studio Yardım Görüntüleyicisi markalama öğeleri tarafından kullanılan JavaScript 'ı içerir.  Aşağıda, marka öğelerinin ve destekleyici JavaScript işlevinin bir listesi verilmiştir.  Bu dosya için Yerelleştirilecek tüm dizeler, bu dosyanın en üstündeki "yerelleştirilebilir dizeler" bölümünde tanımlanmıştır.  ITıL dosyası branding.js dosyası içindeki Loc dizeleri için oluşturulmuştur.

|**Marka özelliği**|**JavaScript Işlevi**|**Açıklama**|
|-|-|-|
|Var...||Değişkenleri tanımlama|
|Kullanıcı kodu dilini al|setUserPreferenceLang|bir dizini # ile kod diline eşler|
|Tanımlama bilgisi değerlerini ayarlama ve edinme|getCookie, setCookie||
|Devralınan üye|changeMembersLabel|Devralınan üyeyi Genişlet/Daralt|
|Selfmarkalı = false olduğunda|onLoad|Bir yazdırma isteği olup olmadığını denetlemek için sorgu dizesini okuyun.  Tüm kod parçacıklarını Kullanıcı tarafından tercih edilen sekmesine odaklamak için ayarlayın.  Bu bir yazdırma isteği ise, isPrinterFriendly değerini true olarak ayarlayın. Yüksek karşıtlık modunu denetleyin.|
|Kod Parçacığı|addSpecificTextLanguageTagSet||
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

Marka paketi, içerik kullanıcılarına yardımcı olmak üzere anahtar bilgilerini iletişim için senaryoları destekleyen bir dizi HTM dosyası içerir. Örneğin, hangi içerik kümelerinin yükleneceğini açıklayan bir bölüm ve yerel konu başlıklarında konular bulunamadığında kullanıcıya söyleyen sayfalar. Bu HTM dosyaları her ürün için değiştirilebilir.  ISO kabuğu satıcıları, varsayılan marka paketini alabilir ve bu sayfaların davranışını ve içeriğini, ihtiyacını pakete göre değiştirebilir.  Bu dosyalar, marka etiketlerinin branding.xml dosyasından ilgili içeriği alması için kendi marka paketine başvurur.

|**Dosya**|**Kullanım**|**Görünen Içerik kaynağı**|
|-|-|-|
|homepage.htm|Bu, şu anda yüklü olan içeriği görüntüleyen ve kullanıcıya içerik hakkında sunmanız gereken diğer tüm iletileri gösteren bir sayfasıdır.  Bu dosya, "Microsoft.Help.Id" content = "-1" ek meta veri özniteliğine sahiptir ve bu içeriği TOC yerel içeriğinin üst kısmına koyar.||
||<META_HOME_PAGE_TITLE_ADD/>|Branding.xml, etiket \<HomePageTitle>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD/>|Branding.xml, etiket \<HomePageIntroduction>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD/>|Branding.xml, etiket \<HomePageContentInstallText>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD/>|Başlık bölümü Branding.xml etiket \<HomePageInstalledBooks> , hiçbir kitap yüklü olmadığında uygulamadan oluşturulan veriler  \<HomePageNoBooksInstalled> .|
||<HOME_PAGE_SETTINGS_SECTION_ADD/>|Başlık bölümü Branding.xml etiketi \<HomePageHelpSettings> , Bölüm metni \<HomePageHelpSettingsText> .|
|topiccorrupted.htm|Yerel küme içinde bir konu mevcut olduğunda, ancak bazı nedenlerle görüntülenemiyor (bozuk içerik).||
||<META_TOPIC_CORRUPTED_TITLE_ADD/>|Branding.xml, etiket \<TopicCorruptedTitle>|
||<TOPIC_CORRUPTED_SECTION_ADD/>|Branding.xml, etiket \<TopicCorruptedViewOnlineText>|
|topicnotfound.htm|Bir konu, yerel içerik kümesinde bulunamadığında veya çevrimiçi olarak kullanılabilir||
||<META_TOPIC_NOT_FOUND_TITLE_ADD/>|Branding.xml, etiket \<TopicNotFoundTitle>|
||<META_TOPIC_NOT_FOUND_ID_ADD/>|Branding.xml, etiket \<TopicNotFoundViewOnlineText> + \<TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD/>|Branding.xml, etiket \<TopicNotFoundText>|
|contentnotinstalled.htm|Ürün için yerel içerik yüklü olmadığında.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD/>|Branding.xml, etiket \<ContentNotInstalledTitle>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD/>|Branding.xml, etiket \<ContentNotInstalledDownloadContentText>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD/>|Branding.xml, etiket \<ContentNotInstalledText>|

**CSS dosyaları**

Visual Studio Yardım Görüntüleyicisi markalama paketi, tutarlı Visual Studio yardım içeriği sunumunu desteklemeye yönelik iki CSS dosyası içerir:

- Marka. css-kendini Selfmarkalı = false olarak işlemek için CSS öğelerini içerir

- Printer. css-kendini Selfmarkalı = false olarak işlemek için CSS öğelerini içerir

Marka. css dosyaları Visual Studio konu sunumu için tanımları içerir (desteklenmediği uyarısıyla, paket hizmetinden Branding_. mshc içinde bulunan marka. css 'nin \<locale> değişebilir).

**Grafik dosyaları**

Visual Studio içeriği, Visual Studio logosunu ve diğer grafikleri görüntüler.  Visual Studio Yardım Görüntüleyicisi markalama paketinde yer alan grafik dosyalarının tam listesi aşağıda gösterilmiştir.

|**Dosya**|**Kullanım**|**Örnekler**|
|-|-|-|
|clear.gif|Daraltılabilir Alanı işlemek için kullanılır||
|footer_slice.gif|Alt bilgi sunusu||
|info_icon.gif|Bilgi görüntülenirken kullanılır|Disclaimer|
|online_icon.gif|Bu simge çevrimiçi bağlantılarla ilişkilendirilen simgedir||
|tabLeftBD.gif|Kod parçacığı kapsayıcısı işlemek için kullanılır||
|tabRightBD.gif|Kod parçacığı kapsayıcısı işlemek için kullanılır||
|vs_logo_bk.gif|normal karşıtlık logo başvuruları için, Branding.xml \<LogoFileName> kullanılır.  Diğer Visual Studio logo adı vs_logo_bk.gif.||
|vs_logo_wh.gif|etiketinde tanımlandığı gibi yüksek karşıtlıklı logo Branding.xml \<LogoFileNameHC> kullanılır.  Diğer Visual Studio logo adı vs_logo_wh.gif.||
|ccOff.png|Açıklamalı alt yazı grafiği||
|ccOn.png|Açıklamalı alt yazı grafiği||
|ImageSprite.png|Daraltılabilir Alanı işlemek için kullanılır|genişletilmiş veya daraltılmış grafik|

## <a name="deploy-a-set-of-topics"></a>Bir dizi konu dağıtma

Bu, bir MSHA dosyasından ve konuları içeren cabs veya MSHC'lerden oluşan bir Yardım Görüntüleyicisi içerik dağıtım kümesi oluşturmaya yönelik basit ve hızlı bir öğreticidir. MSHA, bir dizi cabs veya MSHC dosyasını tanımlayan bir XML dosyasıdır. Yardım Görüntüleyicisi MSHA'yı okuyarak içerik listesini (.CAB. MSHC dosyaları) yerel yükleme için kullanılabilir.

Bu yalnızca Yardım Görüntüleyicisi MSHA için çok temel XML şemasını açıklayan bir temel bilgidir.  Bu kısa genel bakışın ve örnek HelpContentSetup.msha'nın altında örnek bir uygulama vardır.

Bu temel bilgi için MSHA'nın adı HelpContentSetup.msha'dır (dosyanın adı uzantısıyla herhangi bir şey olabilir). MSHA). HelpContentSetup.msha (aşağıdaki örnekte) kullanılabilir cab'lerin veya MSHC'lerin bir listesini içerebilir.  Dosya türü MSHA içinde tutarlı olmalıdır (MSHA ve CAB dosya türlerinin birleşimini desteklemez). Her CAB veya MSHC için bir \<div class="package"> ... (aşağıdaki \</div> örneğine bakın) olması gerekir.

Not: Aşağıdaki uygulama örneğinde markalama paketini dahil edildik. Bu, içerik işleme öğelerinin ve içerik davranışlarının gerekli Visual Studio için dahil etmek açısından kritik öneme sahiptir.

Örnek HelpContentSetup.msha dosyası: ("content set name 1" ve "content set name 2" gibi dosyaları dosya adlarla değiştirin.)

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
</div>.
```

1. "C:\SampleContent" gibi bir yerel klasör oluşturun

2. Bu örnekte, mshc dosyalarını kullanarak konuları içeririz.  MSHC, dosya uzantısının dosya uzantısı olarak değiştirilmiş bir zip .zip. MSHC.

3. Aşağıdaki HelpContentSetup.msha dosyasını bir metin dosyası olarak oluşturun (dosyayı oluşturmak için not defteri kullanılmıştır) ve yukarıdaki belirtilen klasöre kaydedin (bkz. 1. adım).

"Markalama" sınıfı vardır ve benzersizdir. Branding mshc, yüklü içeriğin markaya sahip olması ve MSHC'lerde yer alan içerik davranışlarının markalama paketinde yer alan uygun destek öğelerine sahip olması için bu temel bilgide yer almaktadır. Bu olmadan, sistem parçalanmış (yüklü) içeriğin parçası olmayan destek öğelerine bakarak hatalara neden olur.

Visual Studio marka paketini almak için C:\Program Files (x86)\Microsoft Yardım Görüntüleyicisi\v2.3\ konumundaki Branding_en-US.mshc dosyasını çalışma klasörünüze kopyalayın.

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

Yukarıdaki adımları kullanmak ve genişletmek, VSP'lerin yardım görüntüleyicisi için içerik kümelerini Visual Studio sağlar.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Visual Studio Shell'e yardım ekleme (Tümleşik ve Yalıtılmış)

**Giriş**

Bu kılavuzda Yardım içeriğinin bir Visual Studio Shell uygulamasına nasıl dahil olduğu ve ardından dağıtın.

**Gereksinimler**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Visual Studio 2013 Yalıtılmış Kabuk Redist](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**Genel Bakış**

Kabuk, [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] IDE'nin bir uygulamayı temel alan bir sürümüdür. Bu tür uygulamalar, Yalıtılmış Kabuğu ve sizin oluşturdukları uzantıları içerir. Uzantıları derlemek için SDK'ya dahil edilen Yalıtılmış [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Kabuk proje şablonlarını kullanın.

Yalıtılmış Kabuk tabanlı bir uygulama ve onun Yardımı oluşturmak için temel adımlar:

1. ISO [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell yeniden dağıtılabilir 'i alın (Bir Microsoft indirmesi).

2. Bu Visual Studio, yalıtılmış Kabuğu temel alan bir Yardım uzantısı oluşturun; örneğin, bu kılavuzda daha sonra açıklanan Contoso Yardımı uzantısı.

3. Uzantıyı ve ISO Kabuğu yeniden dağıtılabilir'i dağıtım MSI'sine (uygulama kurulumu) sarman. Bu Kılavuz bir kurulum adımına dahil değildir.

Yeni bir Visual Studio deposu oluşturun. Tümleşik Kabuk senaryosu için Visual Studio12'i ürün kataloğu adıyla aşağıdaki gibi değiştirin:

- C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15 klasörünü oluşturun.

- CatalogType.xml adlı bir dosya oluşturun ve klasöre ekleyin. Dosya aşağıdaki kod satırlarını içermeli:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Kayıt defterindeki içerik depolarını tanımlayın. Tümleşik Kabuk için VisualStudio15'i ürün kataloğu adıyla değiştirebilirsiniz:

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

   Anahtar: LocationPath Dizesi değeri: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US

   Anahtar: CatalogName Dizesi değeri: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Belgeler

**Projeyi Oluşturma**

Yalıtılmış Kabuk uzantısı oluşturmak için:

1. Yeni Visual Studio altında Yeni **Proje'yi** **seçin,** Diğer Proje Türleri altında  Genişletilebilirlik'i seçin ve ardından **Visual Studio Kabuğu Yalıtılmış'ı seçin.**  Yalıtılmış `ContosoHelpShell` Kabuk şablonunu temel alan bir genişletilebilirlik projesi oluşturmak Visual Studio ) adını verir.

2. Bu Çözüm Gezgini ContosoHelpShellUI projesinde, Kaynak Dosyaları klasöründe ApplicationCommands.vsct'yi açın. Bu satırın açıklama satırı olduğundan emin olun ("No_Help" ifadesini arayın): `<!-- <define name="No_HelpMenuCommands"/> -->`

3. Hata ayıklamayı derlemek ve çalıştırmak için F5 **anahtarını seçin.** Yalıtılmış Kabuk IDE'nin deneysel örneğinde Yardım **menüsünü** seçin. Yardım Görüntüle, Yardım **İçeriğini** **Ekle ve Kaldır ve Yardım Tercihini** Ayarla **komutlarının görüntüden emin** olun.

4. Bu Çözüm Gezgini ContosHelpShell projesinde, Kabuk Özelleştirme klasöründe ContosoHelpShell.pkgdef'i açın. Contoso Yardım kataloğunu tanımlamak için aşağıdaki satırları ekleyin:

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. Bu Çözüm Gezgini ContosHelpShell projesinde, Kabuk Özelleştirme klasöründe ContosoHelpShell.Application.pkgdef'i açın. F1 Yardım'a etkinleştirmek için aşağıdaki satırları ekleyin:

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

6. Bu Çözüm Gezgini ContosoHelpShell çözümünün bağlam menüsünde Özellikler menü **öğesini** seçin. Yapılandırma **Özellikleri'nin** **altında,** Yapılandırma Yöneticisi. Yapılandırma **sütunundaki** her "Hata Ayıklama" değerini "Yayın" olarak değiştirebilirsiniz.

7. Çözümü derleyin. Bu, sonraki bölümde kullanılacak bir yayın klasöründe bir dosya kümesi oluşturur.

Bunu dağıtılmış gibi test etmek için:

1. Contoso'ya dağıtın makinede indirilen (yukarıdan) ISO Kabuğunu yükleyin.

2. \Program Files \\ (x86) içinde bir klasör oluşturun \\ ve buna adını `Contoso` girin.

3. ContosoHelpShell yayın klasöründeki içeriği \\ \Program Files (x86)\Contoso\ klasörüne kopyalayın.

4. Başlat menüsünde Çalıştır'ın **seçerek** ve **girerek Kayıt Defteri** Düzenleyicisi'ni başlatabilirsiniz. `Regedit` Kayıt defteri düzenleyicisinde Dosya'ya **ve ardından** İçeri Aktar'ı **seçin.** ContosoHelpShell proje klasörüne gidin. ContosoHelpShell alt klasörlerinden ContosoHelpShell.reg dosyasını seçin.

5. İçerik deposu oluşturma:

    ISO Kabuğu için - C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12 adlı bir Contoso içerik deposu oluşturun

    Tümleşik [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Kabuk için C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15 klasörünü oluşturun

6. İçerik CatalogType.xml oluşturun ve şunları içeren içerik deposuna ekleyin (önceki adım):

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Aşağıdaki kayıt defteri anahtarlarını ekleyin:

    HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: LocationPath Dizesi değeri:

    ISO Kabuğu için:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Tümleşik Kabuk:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    Anahtar: CatalogName Dizesi değeri: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Belgeler. ISO Shell için bu, kataloğun adıdır.

8. İçeriğinizi (cabs veya MSHC ve MSHA) yerel bir klasöre kopyalayın.

9. İçerik depolarını test etmek için örnek Tümleşik Kabuk komut satırı. ISO Shell için kataloğu ve Uygulama değerlerini ürünle eşleşmesi için uygun şekilde başlatmayı seçin.

     "C:\Program Files (x86)\Microsoft Help Viewer\v2.3\HlpViewer.exe" /catalogName VisualStudio15 /helpQuery method="page&id=ContosoTopic0" /launchingApp Microsoft,VisualStudio,12.0

10. Contoso uygulamasını başlatma (Contoso uygulama kökünden). ISO Kabuğu içinde Yardım menü **öğesini seçin** ve Yardım Tercihini Yerel Yardımı **Kullan** **olarak Ayarlayın.**

11. Kabuk içinde Yardım menü öğesini **ve ardından** Yardımı **Görüntüle'yi seçin.** Yerel Yardım görüntüleyicinin başlatılması gerekir. İçeriği Yönet **sekmesini** seçin. Yükleme **Kaynağı'nın** altında **Disk seçeneği** düğmesini seçin. ... **düğmesini** seçin ve Contoso içeriğini içeren yerel klasöre gidin (yukarıdaki adımda yerel klasöre kopyalanır). HelpContentSetup.msha'yı seçin. Contoso şimdi kitap seçimlerini kitap olarak göstersin. **Ekle'yi** ve ardından Güncelleştir **düğmesini (sağ** alt köşede) seçin.

12. Contoso IDE içinde F1 işlevselliğini test etmek için F1 anahtarını seçin.

## <a name="additional-resources"></a>Ek kaynaklar

Çalışma Zamanı API'si için [bkz. Windows Yardım API'si.](/previous-versions/windows/desktop/helpapi/helpapi-portal)

Yardım API'sini kullanma hakkında daha fazla bilgi için bkz. [Yardım Görüntüleyicisi kod örnekleri.](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples)

özellik önerilerini [Geliştirici Topluluğu.](https://aka.ms/feedback/suggest?space=8)
