---
title: Microsoft Yardım Görüntüleyici SDK | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 721623edabcaf3b395a143dd193cae3fd71d93d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707148"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Yardım Görüntüleyicisi SDK’sı

Bu makalede, Visual Studio Yardım Görüntüleyenenler için aşağıdaki görevleri içerir:

- Konu oluşturma (F1 desteği)

- Yardım Görüntüleyicisi içerik markapaketi oluşturma

- Bir dizi makale dağıtma

- Visual Studio kabuğuna yardım ekleme (tümleşik veya yalıtılmış)

- Ek Kaynaklar

## <a name="create-a-topic-f1-support"></a>Konu oluşturma (F1 desteği)

Bu bölümde, sunulan bir konunun bileşenlerine genel bir bakış, konu gereksinimleri, bir konunun nasıl oluşturulabildiğini gösteren kısa bir açıklama (F1 destek gereksinimleri dahil) ve son olarak, işlenen sonucu içeren örnek bir konu sağlar.

**Görüntüleyici Konusuna Genel Bakış**

Bir konu oluşturma için çağrıldığında, Yardım Görüntüleyicisi yükleme veya son güncelleştirme sırasında konuyla ilişkili marka paketi öğelerini xHTML konusuyla birlikte alır ve bu ikisini sunulan içerik görünümüyle (marka verileri + konu verileri) sonuçlandırmak için birleştirir.  Marka paketi logolar, içerik davranışları desteği ve marka metni (telif hakkı, vb.) içerir.  Marka paketi öğeleri hakkında daha fazla bilgi için aşağıdaki "Marka Oluşturma Paketi" başlıklı bınız.  Konuyla ilişkili bir marka paketi olmaması durumunda, Yardım Görüntüleyicisi Yardım Görüntüleyicisi uygulama kökünde (Branding_en-US.mshc) bulunan geri dönüş markapaketini kullanır.

**Görüntüleyici Konu Gereksinimlerine Yardım Edin**

Yardım Görüntüleyicisi içinde doğru bir şekilde oluşturulabilmesi için ham konu içeriğinin W3C Basic 1.1 XHTML olması gerekir.

Bir konu genellikle iki bölümden oluşur:

- Meta veriler (bkz. İçerik Metaveri Başvurusu): konu yla ilgili veriler, örneğin, konu yla ilgili benzersiz kimlik, anahtar kelime değeri, konu TOC Kimliği, üst düğüm kimliği, vb.

- Gövde içeriği: desteklenen içerik davranışlarını (katlanabilir alan, kod parçacığı, vb.) içeren W3C Basic 1.1 XHTML ile uyumlu Tam bir liste aşağıda gösterilmiştir).

Visual Studio Marka Paketi destekli kontroller:

- Bağlantılar

- KodSnippet

- Katlanabilir Alan

- Devralınan Üye

- LanguageSpecificText

Desteklenen dil dizeleri (büyük/küçük harf duyarlı değil):

- javascript

- csharp veya c #

- cplusplus veya visualc++ veya c++

- Jscript

- visualbasic veya vb

- f# veya fsharp veya fs

- diğer - bir dil adını temsil eden bir dize

**Yardım Görüntüleyici konusu oluşturma**

ContosoTopic4.htm adında yeni bir XHTML belgesi oluşturun ve başlık etiketini (aşağıda) ekleyin.

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

Ardından, konunun nasıl sunulacağını (kendi markalı olsun veya olmasın), bu konunun TOC içinde bulunduğu F1 için nasıl başvurulacağını, kimliğini (diğer konulara göre bağlantı başvurusu için) vb. tanımlamak için veri ekleyin. Desteklenen meta verilerin tam listesi için aşağıdaki "İçerik Meta Verileri" tablosuna bakın.

- Bu durumda, Visual Studio Help Viewer marka paketinin bir varyantı olan kendi marka paketimizi kullanacağız.

- IDE özellik çantasında sağlanan F1 değeriyle eşleşen F1 meta adını ve değerini ("Microsoft.Help.F1" content=" ContosoTopic4") ekleyin. (Daha fazla bilgi için F1 Desteği bölümüne bakın.) Bu, F1 IDE seçildiğinde bu konuyu görüntülemek için IDE içinden F1 çağrısıyla eşleşen değerdir.

- Konu kimliğini ekleyin. Bu, bu konuya bağlantı vermek için diğer konular tarafından kullanılan dizedir. Bu konu için Yardım Görüntüleyici Kimliği'dir.

- TOC için, bu konu TOC düğümünün nerede görüneceğini tanımlamak için bu konunun üst düğümöğesini ekleyin.

- TOC için, bu konunun düğüm sırasını ekleyin. Üst düğümde alt `n` düğüm sayısı olduğunda, alt düğümsırasını bu konunun konumunu sırayla tanımlayın. Örneğin, bu konu 4 alt konunun 4 sayısıdır.

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

**Konu Gövdesi**

Konunun gövdesi (üstbilgi ve altbilgi dahil değildir) sayfa bağlantıları, not bölümü, katlanabilir bir alan, bir kod parçacığı ve dile özgü metnin bir bölümünü içerir.  Sunulan konunun bu alanları hakkında bilgi için markalandırma bölümüne bakın.

1. Konu başlığı etiketi ekleyin:`<div class="title">Contoso Topic 4</div>`

2. Not bölümü ekleyin:`<div class="alert"> add your table tag and text </div>`

3. Katlanabilir alan ekleyin:`<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Kod parçacığı ekleyin:`<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Kod diline özel `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` metin `devLangnu=` ekleyin: Diğer dilleri girmenizi sağlayan not. Örneğin, `devLangnu="Fortran"` kod snippet DisplayLanguage = Fortran olduğunda Fortran görüntüler

6. Sayfa bağlantıları ekle:`<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Not: Desteklenmeyen yeni "Görüntülü Dil" (örneğin, F#, Cobol, Fortran) kod snippet kod renklendirme için tek renkli olacaktır.

**Örnek Yardım Görüntüleyici Konu** Kod, meta verilerin, kod parçacığının, katlanabilir alanın ve dile özgü metnin nasıl tanımlandığını gösterir.

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

**F1 Desteği**

Visual Studio'da F1'i seçmek imlecin IDE'ye yerleştirilmesinden sağlanan değerleri oluşturur ve verilen değerlerle birlikte bir "özellik çantası" oluşturur (imleç konumuna göre. İmleç x özelliği nin üzerinde yken, x özelliği etkin/odakta dır ve özellik torbasını değerlerle doldurur.  F1 seçildiğinde özellik çantası doldurulur ve Visual Studio F1 kodu müşterilerin varsayılan Yardım kaynağının yerel veya çevrimiçi olup olmadığını görmek için bakar (çevrimiçi varsayılandır), ardından kullanıcılar ayarına göre uygun dize oluşturur (çevrimiçi varsayılandır) - shell execute (exe başlatma parametreleri için Yardım Yöneticisi Kılavuzu'na bakın) yerel yardım izleyicisi için parametrelerle birlikte + anahtar kelime(ler) yerel yardım varsayılan ise özellik çantasından veya parametre listesinde anahtar kelime bulunan MSDN URL'si.

Çok değerli dize olarak adlandırılan F1 için üç dize döndürülürse, ilk terimi alın, bir hit arayın ve bulunursa, işimiz biter; değilse, bir sonraki dizeye geçin.  Düzen önemlidir. Çok değerli anahtar kelimelerin sunumu en kısa dize için en uzun dize olmalıdır.  Çok değerli anahtar kelimeler için bunu doğrulamak için, seçilen anahtar kelimeyi içerecek çevrimiçi F1 URL dizesine bakın.

Visual Studio 2012'de, kasıtlı olarak çevrimiçi ve çevrimdışı arasında daha güçlü bir ayrım yaptık, böylece kullanıcının ayarı Çevrimiçi içinse, F1 isteğini Visual Studio 2010'da sahip olduğumuz Yardım Kitaplığı Aracısı aracılığıyla yönlendirmek yerine doğrudan MSDN'deki çevrimiçi sorgu hizmetimize aktardık. Daha sonra, bu bağlamda farklı bir şey yapıp yapmamayı belirlemek için "satıcı içeriği yüklü = true" durumuna güveniriz. Doğruysa, müşterileriniz için neleri desteklemek istediğinize bağlı olarak bu ayrıştırma ve yönlendirme mantığını gerçekleştiririz. Eğer yanlışsa, msdn'ye gideriz. Kullanıcının ayarı Yerel'e doğruysa, tüm aramalar yerel yardım motoruna gider.

F1 Akış Diyagramı:

![F1 akışı](../../extensibility/internals/media/f1flow.png "F1flow")

Yardım Görüntüleyicisi varsayılan yardım içerik kaynağı çevrimiçi olarak ayarlandığında (Tarayıcıda başlat):

- Visual Studio Partner (VSP) özellikleri f1 özellik çantası (özellik çantası öneki ve kayıt defterinde bulunan önek için çevrimiçi URL) için bir değer yontmak özellikleri: F1 tarayıcıya bir VSP URL+ parametreleri gönderir.

- Visual Studio özellikleri (dil editörü, Visual Studio özel menü öğeleri, vb): F1 tarayıcıya visual studio URL gönderir.

Yardım Görüntüleyicisi varsayılan yardım kaynağı yerel Yardım 'a ayarlandığında (Yardım Görüntüleyicide Başlat):

- VP özellikleri F1 özellik çantası ve yerel mağaza dizini (diğer bir deyişle, özellik çantası öneki.anahtar kelime = yerel mağaza dizini bulunan değer) arasında anahtar kelime eşleşir): F1 Yardım Görüntüleyici'de konuyu işler.

- Visual Studio özellikleri (VSP'nin Visual Studio özelliklerinden yayılan özellik çantasını geçersiz kılma seçeneği yoktur): F1, Yardım Görüntüleyicisi'nde Visual Studio konusunu işler.

Satıcı Yardım içeriği için F1 Fallback'i etkinleştirmek için aşağıdaki kayıt defteri değerlerini ayarlayın. F1 Fallback, Yardım Görüntüleyicisi'nin Çevrimiçi F1 Yardım içeriğini aramak üzere ayarlanmış olduğu ve satıcı içeriğinin kullanıcıların sabit diskine yerel olarak yüklenmiş olduğu anlamına gelir. Yardım Görüntüleyicisi, varsayılan ayar çevrimiçi yardım için olsa bile içerik için yerel Yardım'a bakmalıdır.

1. **Satıcıİçeriği** değerini Yardım 2.3 kayıt defteri anahtarı altında ayarlayın:

   - 32 bit işletim sistemleri için:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "Satıcıİçeriği"=dword:00000001

   - 64 bit işletim sistemleri için:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Düğüm\Microsoft\Help\v2.3\Kataloglar\VisualStudio15

        "Satıcıİçeriği"=dword:00000001

2. Ortak ad alanını Yardım 2.3 kayıt defteri anahtarının altına kaydedin:

   - 32 bit işletim sistemleri için:

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\İş<<em> \\ ad alanı\></em>

      "konum"="çevrimdışı"

   - 64 bit işletim sistemleri için:

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Düğüm\Microsoft\Help\v2.3\İş<em> \\ ortağı<ad alanı\></em>

      "konum"="çevrimdışı"

**Temel Yerel Ad Alanı Ayrıştırma**

Temel yerel ad alanı ayrıştırma açmak için, kayıt defterine adıyla yeni bir DWORD ekleyin: BaseNativeNamespaces ve değerini 1 olarak ayarlayın (desteklemek istedikleri katalog anahtarı altında).  Örneğin, Visual Studio kataloğunu kullanmak istiyorsanız, yolun anahtarını ekleyebilirsiniz:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Düğüm\Microsoft\Help\v2.3\Kataloglar\VisualStudio15

Başlık/YÖNTEM biçiminde ki bir F1 anahtar kelimesine rastlandığında, '/' karakteri ayrıştırılır ve bu da aşağıdaki yapıyla sonuçlanır:

- ÜSTBILGI: kayıt defterine kaydolmak için kullanılabilecek ad alanı olacaktır

- YÖNTEM: bu geçirilen alır anahtar kelime olacak.

Örneğin, CustomLibrary adlı özel bir kitaplık ve MyTestMethod adlı bir yöntem verildiğinde, bir `CustomLibrary/MyTestMethod`F1 isteği geldiğinde ' olarak biçimlendirilecek.

Bir kullanıcı daha sonra CustomLibrary'yi Ortaklar kovanının altında ad alanı olarak kaydedebilir ve istedikleri konum anahtarını sağlayabilir ve sorguya geçirilen anahtar kelime MyTestMethod olacaktır.

**IDE'de hata ayıklama aracını etkinleştir**

Aşağıdaki kayıt defteri anahtarını ve değerini ekleyin:

::: moniker range="vs-2017"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dinamik Yardım**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Dinamik Yardım**

::: moniker-end

Değer: Perakende Verilerinde Hata Ayıklama Çıktısını Görüntüleme: EVET

IDE'de, Yardım menüsü öğesinin altında **Hata Ayıklama Yardım Bağlamı'nı**seçin.

**İçerik Meta verileri**

Aşağıdaki tabloda, parantezler arasında görünen herhangi bir dize, tanınan bir değerle değiştirilmesi gereken bir yer tutucudur. Örneğin, \<meta adı="Microsoft.Help.Locale" content="[language code]" />, "[language code]" "en-us" gibi bir değerle değiştirilmelidir.

| Mülkiyet (HTML Gösterimi) | Açıklama |
| - | - |
| \<meta adı="Microsoft.Help.Locale" content="[language-code]" /> | Bu konu için bir yerel ayar ayarlar. Bu etiket bir konu da kullanılıyorsa, bir kez kullanılmalıdır ve diğer Microsoft Yardım etiketlerinin üzerine eklenmelidir. Bu etiket kullanılmazsa, konunun gövde metni, belirtilmişse, ürün yerelliğiyle ilişkili sözcük ayırıcısı kullanılarak dizine işlenir; aksi takdirde, en-us sözcük ayırıcısı kullanılır. Bu etiket ISOC RFC 4646 ile uyumludur. Microsoft Yardım'ın doğru çalıştığından emin olmak için, genel Dil özniteliği yerine bu özelliği kullanın. |
| \<meta adı="Microsoft.Help.TopicLocale" content="[language-code]" /> | Diğer yerel ayarlar da kullanıldığında bu konu için bir yer ayarlar. Bu etiket bir konuda kullanılıyorsa, sadece bir kez kullanılmalıdır. Katalog birden fazla dilde içerik içeriyorsa bu etiketi kullanın. Katalogdaki birden çok konu aynı kama sahip olabilir, ancak her biri benzersiz bir TopicLocale belirtmelidir. Kataloğun yerel le eşleşen bir TopicLocale belirten konu, içindekiler tablosunda görüntülenen konudur. Ancak, konunun tüm dil sürümleri Arama sonuçlarında görüntülenir. |
| \<başlık>[Başlık]\</başlık> | Bu konunun başlığını belirtir. Bu etiket gereklidir ve bir konu için sadece bir kez kullanılmalıdır. Konunun gövdesi başlık \<div> bölümü içermiyorsa, bu Başlık konu ve içindekiler tablosunda görüntülenir. |
| \<meta adı=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/> | Yardım Görüntüleyici'nin dizin bölmesinde görüntülenen bir bağlantının metnini belirtir. Bağlantı tıklandığında, konu görüntülenir. Bir konu için birden çok dizin anahtar sözcük belirtebilirsiniz veya bu konuya yönelik bağlantıların dizinde görünmesini istemiyorsanız bu etiketi atlayabilirsiniz. Yardım'ın önceki sürümlerinden "K" anahtar kelimeleri bu özelliğe dönüştürülebilir. |
| \<meta adı="Microsoft.Help.Id" content="[TopicID]"/> | Bu konu için tanımlayıcıyı ayarlar. Bu etiket gereklidir ve bir konu için sadece bir kez kullanılmalıdır. Kimlik, katalogda aynı yerel ayara sahip konular arasında benzersiz olmalıdır. Başka bir konu, bu kimliği kullanarak bu konuya bir bağlantı oluşturabilirsiniz. |
| \<meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | Bu konu için F1 anahtar sözcük belirtir. Bir konu için birden çok F1 anahtar sözcük belirtebilirsiniz veya bir uygulama kullanıcısı F1 tuşuna bastığında bu konunun görüntülenmesini istemiyorsanız bu etiketi atlayabilirsiniz. Genellikle, bir konu için yalnızca bir F1 anahtar kelimesi belirtilir. Yardım'ın önceki sürümlerinden "F" anahtar kelimeleri bu özelliğe dönüştürülebilir. |
| \<meta name="Açıklama" içerik="[konu açıklaması]" /> | Bu konudaki içeriğin kısa bir özetini sağlar. Bu etiket bir konuda kullanılıyorsa, sadece bir kez kullanılmalıdır. Bu özelliğe doğrudan sorgu kitaplığı tarafından erişilir; dizin dosyasında depolanmaz. |
| meta adı="Microsoft.Help.TocParent" content="[parent_Id]"/> | Bu konunun ana konusunu içindekiler tablosunda belirtir. Bu etiket gereklidir ve bir konu için sadece bir kez kullanılmalıdır. Değer, ebeveynin Microsoft.Help.Id. Bir konunun içindekiler tablosunda sadece bir konumu olabilir. "-1" TOC kökü için konu kimliği olarak kabul edilir. Bu [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]sayfada Yardım Görüntüleyici ana sayfası dır. Bu, özellikle en üst düzeyde göstermek sağlamak için bazı konulara TocParent = -1 eklemek aynı nedenle. Yardım Görüntüleyici giriş sayfası bir sistem sayfasıdır ve bu nedenle değiştirilemez. BIR VSP -1 kimliği olan bir sayfa eklemeye çalışırsa, içerik kümesine eklenebilir, ancak Yardım Görüntüleyen her zaman sistem sayfasını kullanır - İzleyici Ana Sayfasına Yardım Et |
| \<meta name="Microsoft.Help.TocOrder" content="[pozitif tamsayı]"/> | İçerik tablosunda bu konunun eş konularına göre nerede göründüğünü belirtir. Bu etiket gereklidir ve bir konu için sadece bir kez kullanılmalıdır. Değer bir karşıcıdır. Daha düşük değerli bir tamsayı belirten bir konu, daha yüksek değerli bir tamsayı belirten bir konunun üzerinde görünür. |
| \<meta adı="Microsoft.Help.Product" content="[ürün kodu]"/> | Bu konunun açıkladığı ürünü belirtir. Bu etiket bir konuda kullanılıyorsa, sadece bir kez kullanılmalıdır. Bu bilgiler, Yardım Dizinleyicisine geçirilen bir parametre olarak da sağlanabilir. |
| \<meta name="Microsoft.Help.ProductVersion" content="[sürüm numarası]"/> | Bu konunun açıkladığı ürünün sürümünü belirtir. Bu etiket bir konuda kullanılıyorsa, sadece bir kez kullanılmalıdır. Bu bilgiler, Yardım Dizinleyicisine geçirilen bir parametre olarak da sağlanabilir. |
| \<meta adı="Microsoft.Help.Category" content="[string]"/> | Ürünler tarafından içeriğin alt bölümlerini tanımlamak için kullanılır. Bir konu için birden çok alt bölüm tanımlayabilirsiniz veya bağlantıların herhangi bir alt bölümü tanımlamasını istemiyorsanız bu etiketi atlayabilirsiniz. Bu etiket, bir konu Yardım'ın önceki bir sürümünden dönüştürüldüğünde TargetOS ve TargetFrameworkMoniker özniteliklerini depolamak için kullanılır. İçeriğin biçimi AttributeName:AttributeValue'dır. |
| \<meta name="Microsoft.Help.TopicVersion content="[konu sürümü numarası]"/> | Bir katalogda birden çok sürüm olduğunda, konunun bu sürümünü belirtir. Microsoft.Help.Id benzersiz olduğu garanti olmadığından, bir konunun birden fazla sürümü bir katalogda varsa, örneğin, bir katalog .NET Framework 3.5 için bir konu ve .NET Framework 4 için bir konu içeriyorsa ve her ikisi de aynı Microsoft.Help.Id sahipse, bu etiket gereklidir. |
| \<meta name="SelfBranded" content="[DOĞRU veya YANLIŞ]"/> | Bu konunun Yardım Kitaplığı Yöneticisi başlangıç marka paketini mi yoksa konuya özgü bir marka paketini mi kullandığını belirtir. Bu etiket doğru veya YANLıŞ olmalıdır. Doğruysa, ilişkili konunun marka paketi, Yardım Kitaplığı Yöneticisi başlatıldığında ayarlanan marka paketini geçersiz kılar, böylece konu diğer içeriğin işlenmesinden farklı olsa bile amaçlandığı gibi işlenir. FALSE ise, geçerli konu, Yardım Kitaplığı Yöneticisi başlatıldığında ayarlanan marka paketine göre işlenir. Varsayılan olarak, SelfBranded değişkeni TRUE olarak beyan edilmedikçe, Yardım Kitaplığı Yöneticisi kendi kendini markalamanın yanlış olduğunu varsayar; bu nedenle, meta adı="SelfBranded" içerik="FALSE" /> beyan \<etmek zorunda kalmamanız gerekmez. |

## <a name="create-a-branding-package"></a>Marka paketi oluşturma

Visual Studio sürümü, Visual Studio Partners için İzole ve Entegre kabuklar da dahil olmak üzere bir dizi farklı Visual Studio ürününün bir kısmını kapsar.  Bu ürünlerin her biri, ürüne özgü bir dereceye kadar konu tabanlı Yardım içeriği markalama desteği gerektirir.  Örneğin, Visual Studio konularının tutarlı bir marka sunumuna sahip olması gerekirken, ISO Shell'i saran SQL Studio her konu için kendi benzersiz Yardım içeriği markasını gerektirir.  Entegre Shell İş Ortağı, Yardım konularının kendi konu markasını korurken ana Visual Studio ürün Yardım içeriğinde olmasını isteyebilir.

Marka paketleri, Yardım Görüntüleyicisi'ni içeren ürün tarafından yüklenir.  Visual Studio ürünleri için:

- Help Viewer 2.3\<uygulama köküne (örnek: C:\Program Files (x86)\Microsoft Help Viewer\v2.3) Tarafından Yardım Görüntüleyicisi dil paketi tarafından bir geri dönüş marka paketi (Branding_ localar>.mshc) yüklenir.  Bu, ürün markalama paketinin yüklenmediğinin (içerik yüklü olmadığı) veya yüklü marka paketinin bozuk olduğu durumlar için kullanılır.  Uygulama kökü geri dönüş marka paketi kullanıldığında Visual Studio öğeleri (logo ve Geri Bildirim) göz ardı edilir.

- Visual Studio içeriği içerik paketi hizmetinden yüklendiğinde, bir marka paketi de yüklenir (ilk kez içerik yükleme senaryosu).  Marka paketinde bir güncelleştirme varsa, bir sonraki içerik güncelleştirmesi veya ek paket yükleme eylemi gerçekleştiğinde güncelleştirme yüklenir.

Microsoft Yardım Görüntüleyicisi, konu meta verilerine dayalı konuların markalaşmalarını destekler.

- Konu meta veri kendini markalı = doğru tanımlar nerede, olduğu gibi konu işlemek, hiçbir şey (kadar markalama olarak).

- Konu meta verilerinin kendi markalı = false'u tanımladığı durumlarda, TopicVendor meta veri değeriyle ilişkili marka paketini kullanın.

- Konu meta verilerinin ad="Microsoft.Help.TopicVendor"\< content= msha> satıcıda markalama paketi adını tanımladığı durumlarda, içerik değerinde tanımlanan marka paketini kullanın.

- Visual Studio kataloğunda, Marka Paketlerinin öncelikli bir uygulaması bulunmaktadır.  İlk Visual Studio varsayılan markalama uygulanır ve daha sonra, konu meta verilerinde tanımlanır ve ilişkili marka paketi (kurulum msha tanımlandığı gibi) ile desteklenirse, marka tanımlanan satıcı geçersiz kılma olarak uygulanır.

Markaöğeleri genellikle üç ana kategoriye ayrılır:

- Üstbilgi öğeleri (örnekler geri bildirim bağlantısı, koşullu feragatname metni, logo) içerir

- İçerik davranışları (örnekler genişletme/daralt denetim metin öğeleri ve kod parçacıkları öğelerini içerir)

- Altbilgi öğeleri (örnek Telif Hakkı)

Markalı unsurlar olarak kabul edilen öğeler şunlardır (bu spec ayrıntılı):

- Katalog/ürün logosu (örnek, Visual Studio)

- Geri bildirim bağlantısı ve e-posta öğeleri

- Yasal Uyarı metni

- Telif hakkı metni

Visual Studio Help Viewer marka paketindeki destekleyici dosyalar şunlardır:

- Grafikler (logolar, simgeler, vb.)

- Branding.js - içerik davranışlarını destekleyen komut dosyası dosyaları

- Branding.xml - katalog içeriği nde sürekli olarak kullanılan dizeleri.  Not: Visual Studio yerelleştirme metin öğeleri için branding.xml, _locID="\<benzersiz değer>" içerir

- Branding.css - sunum tutarlılığı için stil tanımları

- Print.css - tutarlı yazdırılmış sunu için stil tanımları

Yukarıda belirtildiği gibi, Marka Paketleri konu ile ilişkilidir:

- SelfBranded = false meta verilerde tanımlandığında, konu katalog markalama paketini devralır

- Veya SelfBranded = yanlış ve benzersiz bir Marka Paketi MSHA tanımlanan ve içerik yüklü olduğunda kullanılabilir

Özel marka paketleri (VSP içeriği, SelfBranded=True) uygulayan VSP'ler için, devam etmenin bir yolu geri dönüş marka paketiyle (Yardım Görüntüleyicisi ile yüklü) başlamak ve dosyanın adını uygun şekilde değiştirmektir.  Branding_\<localo>.mshc dosyası, dosya uzantısı .mshc olarak değiştirilen bir zip dosyasıdır, bu nedenle uzantıyı .mshc'den .zip'e değiştirin ve içeriği ayıklayın.  Paket öğelerini markalamak ve uygun şekilde değiştirmek için aşağıya bakın (örneğin, logoyu VSP logosuna ve Branding.xml dosyasındaki logoya yapılan başvuruyu değiştirin, VSP özelliklerine göre Branding.xml'i güncelleyin, vb.).

Tüm değişiklikler yapıldığında, istenilen marka öğelerini içeren bir zip dosyası oluşturun ve uzantıyı .mshc olarak değiştirin.

Özel marka paketini ilişkilendirmek için, mshc içeriğiyle birlikte mshc dosyasına başvuruyu içeren MSHA'yı (konuları içeren) oluşturun.  Temel bir MSHA oluşturmak için nasıl "MSHA" aşağıya bakın.

Branding.xml dosyası, konu meta adı="Microsoft.Help.SelfBranded" content="false"/> içerdiğinde, \<bir konudaki belirli öğeleri sürekli olarak işlemek için kullanılan öğelerin listesini içerir.  Branding.xml dosyasındaki öğelerin Visual Studio listesi aşağıda listelenmiştir.  Bu liste, iso shell benimseyenler için bir şablon olarak kullanılmak üzere tasarlanmıştır ve burada bu öğeleri (örneğin logo, geri bildirim ve Telif Hakkı) kendi ürün markalama gereksinimlerini karşılamak için değiştirirler.

Not: "{n}" tarafından belirtilen değişkenlerin kod bağımlılıkları vardır - bu değerleri kaldırmak veya değiştirmek hatalara ve büyük olasılıkla uygulama çökmesine neden olur. Yerelleştirme tanımlayıcıları (örnek _locID="codesnippet.n") Visual Studio Marka Paketi'ne dahildir.

**Marka.xml**

| | |
| - | - |
| Özelliği: | **Katlanabilir Alan** |
| Kullanın: | Genişletme içeriği denetim metni daraltıyor |
| **Öğe** | **Değer** |
| Metni Genişletme | Genişlet |
| Daraltma Metni | Daralt |
| Özelliği: | **KodSnippet** |
| Kullanın: | Kod parçacığı denetim metni.  Not: "Kırılmayan" alanı olan kod snippet içeriği uzaya değiştirilir. |
| **Öğe** | **Değer** |
| CopyToClipboard | Panoya kopyala |
| ViewColorizedText | Renkli Görüntüle |
| CombinedVBTabDisplayLanguage | Visual Basic (Örnek) |
| VBBildirgesi | Bildirim |
| VBKullanım | Kullanım |
| Özelliği: | **Geri bildirim, Altbilgi ve Logo** |
| Kullanın: | Müşterinin geçerli konu hakkında e-posta yoluyla geri bildirim sağlaması için bir Geri Bildirim denetimi sağlayın.  İçerik için telif hakkı metni.  Logo tanımı. |
| **Öğe** | **Değer (Bu dizeleri içerik benimseyen ihtiyacını karşılamak için değiştirilebilir.)** |
| Telif hakkı | © 2013 Microsoft Corporation. Tüm hakları saklıdır. |
| SendFeedback | \<a{0}href=" {1} "\<>Microsoft'a bu konuda geri bildirim /bir> gönderin. |
| FeedbackLink | |
| LogoBaşlığı | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| Özelliği: | **Disclaimer** |
| Kullanın: | Makineye çevrilmiş içerik için servis talebine özel feragatnameler kümesi. |
| **Öğe** | **Değer** |
| MT_Editable | Bu makale makine tercüme edildi. Internet bağlantınız varsa, bu sayfayı aynı anda orijinal İngilizce içeriğiyle birlikte editable modunda görüntülemek için "Bu konuyu çevrimiçi görüntüle"yi seçin. |
| MT_NonEditable | Bu makale makine tercüme edildi. Internet bağlantınız varsa, bu sayfayı aynı anda orijinal İngilizce içeriğiyle birlikte editable modunda görüntülemek için "Bu konuyu çevrimiçi görüntüle"yi seçin. |
| MT_QualityEditable | Bu makale el ile çevrildi. Internet bağlantınız varsa, bu sayfayı aynı anda orijinal İngilizce içeriğiyle birlikte editable modunda görüntülemek için "Bu konuyu çevrimiçi görüntüle"yi seçin. |
| MT_QualityNonEditable | Bu makale el ile çevrildi. Internet bağlantınız varsa, bu sayfayı aynı anda orijinal İngilizce içeriğiyle birlikte editable modunda görüntülemek için "Bu konuyu çevrimiçi görüntüle"yi seçin. |
| MT_BetaContents | Bu makale, bir ön sürüm için çevrilmiş makine oldu. Internet bağlantınız varsa, bu sayfayı aynı anda orijinal İngilizce içeriğiyle birlikte editable modunda görüntülemek için "Bu konuyu çevrimiçi görüntüle"yi seçin. |
| MT_BetaRecycledContents | Bu makale, bir ön sürüm için el ile tercüme edilmiştir. Internet bağlantınız varsa, bu sayfayı aynı anda orijinal İngilizce içeriğiyle birlikte editable modunda görüntülemek için "Bu konuyu çevrimiçi görüntüle"yi seçin. |
| Özelliği: | **Bağlantı Tablosu** |
| Kullanın: | Çevrimiçi konu bağlantıları için destek |
| **Öğe** | **Değer** |
| LinkTableBaşlık | Bağlantı Tablosu |
| TopicEnuLinkText | Bilgisayarınızda bulunan\<bu konunun İngilizce sürümünü /bir> görüntüleyin. |
| KonuOnlineLinkText | Bu konuyu \<bir href="{0}" {1}>çevrimiçi\</a> |
| OnlineMetin | Çevrimiçi |
| Özelliği: | **Video Ses kontrolü** |
| Kullanın: | Video içeriği için öğeleri ve metni görüntüleme |
| **Öğe** | **Değer** |
| MultiMediaNotSupported | İçeriği desteklemek {0} için Internet Explorer 9 veya daha büyük bir yüklenmeniz gerekir. |
| VideoMetin | video görüntüleme |
| Sesli Metin | ses akışı |
| OnlineVideoLinkText | \<p>Bu konuyla ilişkili videoyu {0} \<görüntülemek için bir{1}href=" ">{2}burada\</bir>. \</p> |
| OnlineAudioLinkText | \<p>Bu konuyla ilişkili sesi dinlemek {0} \<için{1}href=" {2}\<">burada /bir>. \</p> |
| Özelliği: | **İçerik Yüklenmedi denetimi** |
| Kullanın: | Contentnotinstalled.htm'nin işlenmesi için kullanılan metin öğeleri (dizeleri) |
| **Öğe** | **Değer** |
| İçerikNotInstalledTitle | Bilgisayarınızda içerik bulunamadı. |
| İçerikNotInstalledDownloadContentText | \<p>Bilgisayarınıza içerik \<indirmek için,{0}bir {1} href="\<">Yönet sekmesine tıklayın /a>. \</p> |
| İçerikNotInstalledText | \<p>Bilgisayarınızda içerik yüklü değildir. Yerel Yardım içeriği yüklemesi için Yöneticinize görün. \</p> |
| Özelliği: | **Konu Bulunamadı denetimi** |
| Kullanın: | Topicnotfound.htm'nin işlenmesi için kullanılan metin öğeleri (dizeleri) |
| **Öğe** | **Değer** |
| TopicNotFoundTitle | İstenen konuyu bilgisayarınızda bulamıyor. |
| TopicNotFoundViewOnlineText | \<p>İstediğiniz konu bilgisayarınızda bulunamadı, ancak bir \<href="{0} {1} ">konuyu\<çevrimiçi /a> görüntüleyebilirsiniz. \</p> |
| TopicNotFoundDownloadContentText | \<p>Benzer konulara bağlantılar için gezinti \<bölmesine veya{0} {1} bir href=" ">bilgisayarınıza içerik indirmek için> Yönet sekmesine\<tıklayın. \</p> |
| TopicNotFoundText | \<p>İstediğiniz konu bilgisayarınızda bulunamadı. \</p> |
| Özelliği: | **Konu Bozuk Denetim** |
| Kullanın: | Topiccorrupted.htm'nin işlenmesi için kullanılan metin öğeleri (dizeleri) |
| **Öğe** | **Değer** |
| TopicCorruptedTitle | İstenen konu görüntülenemiyor. |
| TopicCorruptedViewOnlineText | \<p>Yardım Görüntüleyici istenen konuyu görüntüleyemiyor. Konunun içeriğinde veya altta yatan bir sistem bağımlılığında bir hata olabilir. \</p> |
| Özelliği: | **Ana Sayfa denetimi** |
| Kullanın: | Yardım Görüntüleyicisi üst düzey düğüm içeriğinin görüntülenmesini destekleyen metin. |
| **Öğe** | **Değer** |
| AnaSayfaBaşlığı | İzleyici Ana Sayfasına Yardım Et |
| AnaSayfaGiriş | \<p>Microsoft araçlarını, ürünlerini, teknolojilerini ve hizmetlerini kullanan herkes için önemli bir bilgi kaynağı olan Microsoft Yardım Görüntüleyicisi'ne hoş geldiniz. Yardım Görüntüleyicisi, nasıl yapılacağınız ve başvuru bilgilerine, örnek koda, teknik makalelere ve daha fazlasına erişmenizi sağlar. İhtiyacınız olan içeriği bulmak için, içindekiler tablosuna göz atın, tam metin araması kullanın veya anahtar kelime dizini kullanarak içerikte gezinin. \</p> |
| Ana SayfaİçerikYükleme Metni | \<p \<>br />\<Aşağıdakileri{0}yapmak {1} için\<bir href=" "\<>\<İçeriği Yönet /bir> sekmesini kullanın: ul>li>Bilgisayarınıza içerik ekleyin. \</li \<>li>Yerel içeriğinizin güncellemelerini kontrol edin. \</li \<>li>İçeriği bilgisayarınızdan kaldırın. \</li \<>/ul>\</p> |
| AnasayfaYüklü Kitaplar | Yüklü Kitaplar |
| AnasayfaNoBooksYüklü | Bilgisayarınızda içerik bulunamadı. |
| AnaSayfaYardım Ayarları | Yardım İçerik Ayarları |
| AnaSayfaYardım AyarlarıMetin | \<p>Geçerli ayarınız yerel yardımdır. Yardım Görüntüleyicisi, bilgisayarınıza yüklediğiniz içeriği görüntüler. \<br />Yardım içeriği kaynağınızı değiştirmek için Visual Studio \<menü çubuğunda açıklık{0}stili="\<">Help, Set Help Preference /span>. \<br />\</p> |
| Megabayt | MB |

**branding.js**

Branding.js dosyası, Visual Studio Help Viewer markalama öğeleri tarafından kullanılan JavaScript'i içerir.  Aşağıda marka öğeleri ve destekleyici JavaScript işlevinin bir listesi yer almaktadır.  Bu dosya için yerelleştirilecek tüm dizeleri bu dosyanın üst kısmındaki "Yerelleştirilebilir Dizeleri" bölümünde tanımlanır.  ICL dosyası, branding.js dosyasındaki dizeleri bulmak için oluşturulmuştur.

||||
|-|-|-|
|**Marka Özelliği**|**JavaScript Fonksiyonu**|**Açıklama**|
|Var ...||Değişkenleri tanımlama|
|Kullanıcı kodu dilini alma|setUserPreferenceLang|bir dizini # kod diline eşler|
|Çerez değerlerini ayarlama ve alma|getCookie, setCookie||
|Devralınan Üye|changeMembersLabel|Devralınan üyeyi genişletme/daraltma|
|Ne zaman SelfBranded=False|Onload|Yazdırma isteği olup olmadığını kontrol etmek için sorgu dizesini okuyun.  Kullanıcı tercih edilen sekmeye odaklanmak için tüm codesnippets ayarlayın.  Bir baskı isteği ise, o zaman doğru isPrinterFriendly ayarlayın. Yüksek kontrast modu olup olup yok.|
|Kod Snippet|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||Değişiklik Sekmesi||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|Katlanabilir Alan|addToCollapsibleControlSet|tüm katlanabilir kontrol nesnesini listeye yazın.|
||CA_Click|katlanabilir alanın durumuna göre, hangi görüntü ve metin sunmak için tanımlar|
|Logo için kontrast desteği|isBlackBackground()|Arka planın siyah olup olmadığını belirlemek için çağrıldı.  Yalnızca yüksek kontrast lı modda doğru.|
||isHighContrast()|yüksek kontrast lı modu algılamak için renkli bir yayılma alanı kullanın|
||onHighContrast(siyah)|Yüksek kontrast algılandığında çağrılır|
|LST işlevselliği|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|MultiMedia işlevselliği|resim yazısı(başlangıç, bitiş, metin, stil)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSeconds(t)||
||getAllComments(düğüm)||
||styleRectify(styleName, styleValue)||
||showCC(id)||
||altyazı(id)||

**HTM DOSYALARI**

Marka paketi, içerik kullanıcılarına önemli bilgilerin iletilmesi için senaryoları destekleyen bir dizi HTM dosyası içerir ( örneğin, hangi içerik kümelerinin yüklenmesini açıklayan bir ana sayfa ve yerel konular kümesinde konular bulunamadığı zaman kullanıcıya bildiren sayfalar gibi. Bu HTM dosyaları ürün başına değiştirilebilir.  ISO Shell satıcıları varsayılan marka paketini alabilir ve bu sayfaların davranışını ve içeriğini kendi ihtiyaçlarını karşılamak üzere değiştirebilirler.  Bu dosyalar, marka etiketlerinin branding.xml dosyasından ilgili içeriği alabilmesi için kendi marka paketine başvurur.

||||
|-|-|-|
|**Dosya**|**Kullanma**|**Görüntülenen İçerik Kaynağı**|
|ana sayfa.htm|Bu, şu anda yüklü içeriği görüntüleyen bir sayfadır ve kullanıcıya içeriği hakkında sunulması uygun başka bir iletidir.  Bu dosya, bu içeriği yerel içerik TOC'un en üstüne yerleştiren Microsoft.Help.Id ek meta veri özniteliğine sahiptir="-1"||
||<META_HOME_PAGE_TITLE_ADD />|Branding.xml, \<tag HomePageTitle>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD />|Branding.xml, \<tag HomePageIntroduction>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD />|Branding.xml, \<etiket Ana SayfaİçerikInstallText>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD />|Başlık bölümü Branding.xml etiketi\<AnaSayfaInstalledBooks>, \<uygulamadan oluşturulan veriler, HomePageNoBooksInstalled> zaman kitap yüklü.|
||<HOME_PAGE_SETTINGS_SECTION_ADD />|Başlık bölümü Branding.xml etiketi \<AnaSayfaYardım \<Ayarları>, bölüm metni AnaSayfaYardımAyarlarıMetin>.|
|topiccorrupted.htm|Yerel kümede bir konu varsa, ancak nedense görüntülenemiyorsa (bozuk içerik).||
||<META_TOPIC_CORRUPTED_TITLE_ADD />|Branding.xml, \<etiket TopicCorruptedTitle>|
||<TOPIC_CORRUPTED_SECTION_ADD />|Branding.xml, \<etiket TopicCorruptedViewOnlineText>|
|topicnotfound.htm|Bir konu yerel içerik kümesinde bulunmadığında veya çevrimiçi olarak kullanılamıyorsa||
||<META_TOPIC_NOT_FOUND_TITLE_ADD />|Branding.xml, \<etiket TopicNotFoundTitle>|
||<META_TOPIC_NOT_FOUND_ID_ADD />|Branding.xml, \<etiket TopicNotFoundViewOnlineText \<> + TopicNotFoundDownloadContentMetin>|
||<TOPIC_NOT_FOUND_SECTION_ADD />|Branding.xml, \<tag TopicNotFoundText>|
|contentnotinstalled.htm|Ürün için yerel içerik yüklü olmadığında.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD />|Branding.xml, \<etiket ContentNotInstalledTitle>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD />|Branding.xml, \<etiket İçerikNotInstalledDownloadContentMetin>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD />|Branding.xml, \<etiket İçerikNotInstalledMetin>|

**CSS Dosyaları**

Visual Studio Yardım Görüntüleyici MarkaPaketi tutarlı Visual Studio Yardım içerik sunum desteklemek için iki css dosyaları içerir:

- Branding.css - SelfBranded=false nerede render için css elemanları içerir

- Printer.css - SelfBranded=false nerede render için css elemanları içerir

Branding.css dosyaları Visual Studio konu sunumu için tanımlar içerir (uyarı, paket hizmetten\<>.mshc Branding_ yerel olarak yer alan branding.css değişebilir).

**Grafik Dosyaları**

Visual Studio içeriği, diğer grafiklerin yanı sıra Visual Studio logosunu da görüntüler.  Visual Studio Yardım Görüntüleyen marka paketindeki grafik dosyaların tam listesi aşağıda gösterilmiştir.

||||
|-|-|-|
|**Dosya**|**Kullanma**|**Örnekler**|
|clear.gif|Katlanabilir Alanı işlemek için kullanılır||
|footer_slice.gif|Altbilgi sunumu||
|info_icon.gif|Bilgileri görüntülerken kullanılır|Disclaimer|
|online_icon.gif|Bu simge çevrimiçi bağlantılarla ilişkilendirilmelidir||
|tabLeftBD.gif|Kod parçacık kapsayıcısını işlemek için kullanılır||
|sekmeRightBD.gif|Kod parçacık kapsayıcısını işlemek için kullanılır||
|vs_logo_bk.gif|Branding.xml etiketi \<LogoFileName>'da tanımlandığı şekilde normal kontrastlı logo başvuruları için kullanılır.  Visual Studio ürünleri için logo adı vs_logo_bk.gif'tir.||
|vs_logo_wh.gif|Branding.xml etiketi \<LogoFileNameHC> tanımlandığı gibi normal yüksek logo referansları için kullanılır.  Visual Studio ürünleri için logo adı vs_logo_wh.gif'tir.||
|ccOff.png|Grafik altyazı||
|ccOn.png|Grafik altyazı||
|GörüntüSprite.png|Katlanabilir Alanı işlemek için kullanılır|genişletilmiş veya grafik daraltma|

## <a name="deploy-a-set-of-topics"></a>Bir konu kümesi dağıtma

Bu, bir MSHA dosyası ve konuları içeren kabinler veya MSHC'lerden oluşan bir Yardım Görüntüleyicisi içerik dağıtım kümesi oluşturmak için basit ve hızlı bir öğreticidir. MSHA, bir dizi kabin veya MSHC dosyasını açıklayan bir XML dosyasıdır. Yardım Görüntüleyicisi bir içerik listesi elde etmek için MSHA'yı okuyabilir (. CAB veya . MSHC dosyaları) yerel kurulum için kullanılabilir.

Bu sadece Yardım İzleyici MSHA için çok temel XML şema açıklayan bir astar.  Bu kısa genel bakış ın altında örnek bir uygulama ve örnek HelpContentSetup.msha vardır.

MSHA adı, Bu astar amaçları için, HelpContentSetup.msha (dosyanın adı uzantısı ile, bir şey olabilir. MSHA). HelpContentSetup.msha (aşağıdaki örnek) mevcut kabinlerin veya MSHC'lerin listesini içermelidir.  Dosya türü MSHA içinde tutarlı olmalıdır (MSHA ve CAB dosya türlerinin bir birleşimini desteklemez). Her CAB veya MSHC için \<div sınıfı="paket">... \</div> (aşağıdaki örneğe bakın).

Not: Aşağıdaki uygulama örneğinde markalama paketini de dahil ettik. Bu, gerekli Visual Studio içerik oluşturma öğelerini ve içerik davranışlarını elde etmek için eklemek için önemlidir.

Örnek HelpContentSetup.msha dosyası: ("Içerik kümesi adı 1" ve "içerik kümesi adı 2" vb. dosya adlarınızı değiştirin.)

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

1. "C:\SampleContent" gibi yerel klasör oluşturma

2. Bu örnekte, konuları içerecek şekilde MSHC dosyalarını kullanırız.  MSHC, dosya uzantısı .zip'ten .zip'e değiştirilen bir zip'tir. MSHC.

3. Aşağıdaki HelpContentSetup.msha'yı metin dosyası olarak oluşturun (dosyayı oluşturmak için not defteri kullanıldı) ve yukarıdaki belirtilen klasöre kaydedin (bkz. adım 1).

Sınıf "Marka" var ve benzersizdir. Mshc markası bu astara dahildir, böylece yüklü içerik markalaşmaya sahip olur ve MSHC'lerde yer alan içerik davranışları markalama paketinde yer alan uygun destek öğelerine sahip olur. Bu olmadan, sistem yırtılmış (yüklü) içeriğin bir parçası olmayan destek öğelerini aradığında hatalar ortaya çıkacaktır.

Visual Studio marka paketini almak için Branding_en-US.mshc dosyasını C:\Program Files (x86)\Microsoft Help Viewer\v2.3\ adresinden çalışma klasörünüze kopyalayın.

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

Yukarıdaki adımları kullanmak ve genişletmek VSP'lerin Visual Studio Yardım Görüntüleyicisi için içerik kümelerini dağıtmalarını sağlar.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Visual Studio Shell'e yardım ekleme (Entegre ve İzole)

**Giriş**

Bu gözden geçirme, Yardım içeriğinin Visual Studio Shell uygulamasına nasıl dahil edilip sonra dağıtılayacağını gösterir.

**Gereksinimler**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Visual Studio 2013 İzole Shell Redist](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**Genel bakış**

[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell, [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] bir uygulamayı temel alabildiğiniz IDE'nin bir sürümüdür. Bu tür uygulamalar, oluşturduğunuz uzantılarla birlikte İzole Kabuk'u içerir. Uzantılar oluşturmak için [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] SDK'da bulunan İzole Shell proje şablonlarını kullanın.

Yalıtılmış Kabuk tabanlı bir uygulama ve Yardım oluşturmak için temel adımlar:

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] ISO Shell yeniden dağıtılabilir (Microsoft indir) edinin.

2. Visual Studio'da, İzole Shell'i temel alan bir Yardım uzantısı oluşturun, örneğin, bu izbin daha sonra açıklanan Contoso Yardım uzantısı.

3. Uzantıyı ve ISO Shell'i dağıtım MSI'ına (uygulama kurulumu) kaydırın. Bu Walkthrough bir kurulum adımı içermez.

Visual Studio içerik mağazası oluşturun. Tümleşik Shell senaryosu için Visual Studio12'yi ürün kataloğu adı aşağıdaki gibi değiştirin:

- C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15 klasörünü oluşturun.

- CatalogType.xml adlı bir dosya oluşturun ve klasöre ekleyin. Dosya aşağıdaki kod satırlarını içermelidir:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Kayıt defterindeki içerik deposunu tanımlayın. Entegre Shell için VisualStudio15'i ürün kataloğu adı ile değiştirin:

- HKLM\YAZILIM\Wow6432Düğüm\Microsoft\Yardım\v2.3\Kataloglar\VisualStudio15

   Anahtar: LocationPath String değeri: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\

- HKLM\SOFTWARE\Wow6432Düğüm\Microsoft\Help\v2.3\Kataloglar\VisualStudio15\tr-US

   Anahtar: CatalogName String [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] değeri: Dokümantasyon

**Proje oluşturma**

Yalıtılmış Kabuk uzantısı oluşturmak için:

1. Visual Studio, **Dosya**altında , **Yeni Proje**seçin , Diğer **Proje Türleri** altında **Genişletilebilirlik**seçin , ve sonra **Visual Studio Shell İzole**seçin . Visual Studio `ContosoHelpShell`İzole Shell şablonuna dayalı bir genişletilebilirlik projesi oluşturmak için projeyi adlandırın.

2. Solution Explorer'da, ContosoHelpShellUI projesinde, Kaynak Dosyaları klasöründe ApplicationCommands.vsct'i açın. Bu satırın yorumlanındığından emin olun ("No_Help" için arama yapın):`<!-- <define name="No_HelpMenuCommands"/> -->`

3. Hata Ayıklama'yı derlemek ve çalıştırmak için F5 **tuşunu**seçin. İzole Shell IDE'nin deneysel örneğinde **Yardım** menüsünü seçin. **Yardım İçeriğini Görüntüle,** **Ekle ve Kaldır**ve Yardım Tercihi komutlarını **ayarla** komutlarının göründüğünden emin olun.

4. Solution Explorer'da, ContosHelpShell projesinde, Shell Özelleştirme klasöründe ContosoHelpShell.pkgdef'i açın. Contoso Yardım kataloğunu tanımlamak için aşağıdaki satırları ekleyin:

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. Solution Explorer'da, ContosHelpShell projesinde, Shell Özelleştirme klasöründe ContosoHelpShell.Application.pkgdef'i açın. F1 Yardımı'nı etkinleştirmek için aşağıdaki satırları ekleyin:

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

6. Solution Explorer'da, ContosoHelpShell çözümünün bağlam menüsünde **Özellikler** menü öğesini seçin. **Yapılandırma Özellikleri**altında **Configuration Manager'ı**seçin. **Yapılandırma** sütununda, her "Hata Ayıklama" değerini "Sürüm" olarak değiştirin.

7. Çözümü derleyin. Bu, bir sonraki bölümde kullanılacak bir sürüm klasöründe bir dosya kümesi oluşturur.

Bunu dağıtılmış gibi sınamak için:

1. Contoso'yu yerleştirdiğiniz makinede indirilen (yukarıdan) ISO Shell'i yükleyin.

2. \Program Dosyaları \\(x86)\\içinde bir klasör `Contoso`oluşturun ve adlandırın.

3. İçeriği ContosoHelpShell sürüm klasöründen \\\Program Files (x86)\Contoso\ klasörüne kopyalayın.

4. **Başlat** menüsünde `Regedit` **Çalıştır'ı** seçip . Kayıt defteri düzenleyicisinde **Dosya'yı**seçin ve sonra **içeri aktar.** ContosoHelpShell proje klasörüne göz atın. ContosoHelpShell alt klasöründe ContosoHelpShell.reg'i seçin.

5. İçerik deposu oluşturun:

    ISO Shell için - Contoso içerik deposu C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12 oluşturun

    Tümleşik Kabuk için [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15 klasörünü oluşturun

6. CatalogType.xml oluşturun ve aşağıdakileri içeren içerik deposuna (önceki adım) ekleyin:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Aşağıdaki kayıt defteri anahtarlarını ekleyin:

    HKLM\SOFTWARE\Wow6432Düğüm\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: LocationPath String değeri:

    ISO Shell için:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]Entegre Kabuk:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    Anahtar: CatalogName String [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] değeri: Dokümantasyon. ISO Shell için kataloğunuzun adı budur.

8. İçeriğinizi (kabinler veya MSHC ve MSHA) yerel bir klasöre kopyalayın.

9. İçerik deposunu test etmek için Örnek Entegre Kabuk komut satırı. ISO Shell için, kataloğu ve uygulama uygulama değerlerini ürünle eşleşecek şekilde değiştirin.

     "C:\Program Files (x86)\Microsoft Help Viewer\v2.3\HlpViewer.exe" /catalogName VisualStudio15 /helpQuery method="page&id=ContosoTopic0" /launchingApp Microsoft,VisualStudio,12.0

10. Contoso uygulamasını başlatın (Contoso uygulama kökünden). ISO Shell'de **Yardım** menüsü öğesini seçin ve **Yerel Yardımı Kullanmak**Için **Yardım Tercihini** Ayarla'yı değiştirin.

11. Kabuk içinde, **Yardım** menüsü öğesini seçin ve ardından **Yardım'ı görüntüle.'yi görüntüleyin.** Yerel Yardım görüntüleyici başlatMalıdır. İçeriği **Yönet** sekmesini seçin. **Yükleme Kaynağı** **altında, Disk** seçeneği düğmesini seçin. **...** düğmesini seçin ve Contoso içeriği içeren yerel klasöre göz atın (yukarıdaki adımda yerel klasöre kopyalanır). HelpContentSetup.msha'yı seçin. Contoso şimdi kitap seçimlerinde bir kitap olarak görünmelidir. **Ekle'yi**seçin ve ardından **Güncelleştir** düğmesini (sağ alt köşe) seçin.

12. Contoso IDE içinde, F1 işlevselliğini test etmek için F1 tuşunu seçin.

## <a name="additional-resources"></a>Ek kaynaklar

Runtime API için [Windows Yardım API'si'ne](/previous-versions/windows/desktop/helpapi/helpapi-portal)bakın.

Yardım API'nden nasıl yararlanılabildiğini zedekçe daha fazla bilgi için [Görüntüleyicikoduna Yardım örneklerine](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples)bakın.

[Geliştirici Topluluğu'nda](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)özellik önerileri gönderebilirsiniz.
