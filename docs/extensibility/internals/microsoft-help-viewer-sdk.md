---
title: Microsoft Yardım Görüntüleyicisi SDK | Microsoft Docs
description: Makale Visual Studio, Yardım Görüntüleyicisi içerik marka paketi oluşturma ve bir makale kümesi dağıtma gibi Yardım Görüntüleyicisi görevleri hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5ea294f29359e60764b2d6b3f2237bdc1f72cfdc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102606"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Yardım Görüntüleyicisi SDK’sı

Bu makale, Yardım Görüntüleyicisi tümleştiricileri Visual Studio aşağıdaki görevleri içerir:

- Konu oluşturma (F1 desteği)

- Yardım Görüntüleyicisi içerik markalama paketi oluşturma

- Bir makale kümesi dağıtma

- Visual Studio kabuğuna yardım ekleme (tümleşik veya yalıtılmış)

- Ek Kaynaklar

## <a name="create-a-topic-f1-support"></a>Konu oluşturma (F1 desteği)

Bu bölümde, sunulan bir konunun bileşenlerine genel bakış, konu gereksinimleri, konu başlığı oluşturma hakkında kısa bir açıklama (F1 destek gereksinimleri dahil) ve son olarak, işlenmiş sonucu içeren örnek bir konu sunulmaktadır.

**Yardım Görüntüleyicisi Konu Başlığına Genel Bakış**

İşleme için bir konu çağrıldı olduğunda, Yardım Görüntüleyicisi, yükleme veya son güncelleştirme sırasında konu başlığıyla ilişkilendirilmiş markalama paketi öğelerini XHTML konusuyla birlikte alır ve bu ikisi bir araya gelir ve sunulan içerik görünümüne (marka verileri + konu verileri) neden olur.  Marka paketi logolar, içerik davranışları için destek ve marka metni (telif hakkı vb.) içerir.  Markalama paketi öğeleri hakkında daha fazla bilgi için aşağıdaki "Marka Paketi Oluşturma" belgesine bakın.  Konu başlığıyla ilişkilendirilmiş bir marka paketi olması durumunda, Yardım Görüntüleyicisi Yardım Görüntüleyicisi uygulama kökünde bulunan geri dönüş markalama paketini (Branding_en-US.mshc) kullanır.

**Yardım Görüntüleyicisi Konu Gereksinimleri**

Yardım Görüntüleyicisi'nde doğru şekilde işlenecek ham konu içeriğinin W3C Basic 1.1 XHTML olması gerekir.

Bir konu genellikle iki bölüm içerir:

- Meta veriler (bkz. İçerik Meta Verileri Başvurusu): konu hakkında veriler; örneğin konu benzersiz kimliği, anahtar sözcük değeri, konu toc kimliği, üst düğüm kimliği vb.

- Gövde içeriği: Desteklenen içerik davranışlarını (daraltılabilir alan, kod parçacığı vb.) içeren W3C Basic 1.1 XHTML ile uyumludur. Aşağıda tam liste gösterilmiştir).

Visual Studio Marka Paketi desteklenen denetimler:

- Bağlantılar

- CodeSnippet

- Daraltılabilir Alan

- Devralınan Üye

- LanguageSpecificText

Desteklenen dil dizeleri (büyük/büyük harfe duyarlı değildir):

- javascript

- csharp veya c #

- cplusplus veya visualc++ veya c++

- Jscript

- visualbasic veya vb

- f# veya fsharp veya fs

- diğer - dil adını temsil eden bir dize

**Yardım Görüntüleyicisi konu başlığı oluşturma**

ContosoTopic4.htm adlı yeni bir XHTML belgesi oluşturun ve başlık etiketini ekleyin (aşağıda).

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

Ardından, konunun nasıl sun olacağını (markalı veya markalı değil), F1 için bu konuya nasıl başvuracaklarını, bu konunun toc içinde nerede olduğunu, kimliğini (diğer konuların bağlantı başvurusu için) vb. tanımlamak için veri ekleyin. Desteklenen meta verilerin tam listesi için aşağıdaki "İçerik Meta Verileri" tablosuna bakın.

- Bu durumda, Visual Studio Help Viewer markalama paketinin bir çeşitlesi olan kendi marka paketimizi kullan kullanırsınız.

- IDE özellik çantasında sağlanan F1 değeriyle eş olacak F1 meta adını ve değerini ("Microsoft.Help.F1" content=" ContosoTopic4") ekleyin. (Daha fazla bilgi için F1 Desteği bölümüne bakın.) Bu, IDE'de F1 seçilirken bu konuyu görüntülemek için IDE'nin içindeki F1 çağrısıyla eş değerdir.

- Konu kimliğini ekleyin. Bu, diğer konular tarafından bu konuya bağlantı için kullanılan dizedir. Bu konu için Yardım Görüntüleyicisi Kimliğidir.

- ToC için, bu konunun toC düğümünün nerede görünekleçlerini tanımlamak üzere bu konunun üst düğümünü ekleyin.

- ToC için bu konunun düğüm sırasına ekleyin. Üst düğümde `n` alt düğüm sayısı olduğunda, bu konunun konumu alt düğüm sırasına göre tanımlayın. Örneğin, bu konu 4-4 alt konu başlığıdır.

Örnek meta veriler bölümü:

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

Konunun gövdesi (üst bilgi ve alt bilgi dahil değil) sayfa bağlantıları, not bölümü, daraltılabilir alan, kod parçacığı ve dile özgü bir metin bölümü içerir.  Sunulan konunun bu alanları hakkında bilgi için markalama bölümüne bakın.

1. Konu başlığı etiketi ekleyin:  `<div class="title">Contoso Topic 4</div>`

2. Not bölümü ekleyin: `<div class="alert"> add your table tag and text </div>`

3. Daraltılabilir bir alan ekleyin:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Kod parçacığı ekleme:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Kod diline özgü metin ekleme:  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` Diğer `devLangnu=` dilleri girmenize olanak sağlayan bir not. Örneğin, Kod `devLangnu="Fortran"` parçacığı DisplayLanguage = Fortran olduğunda Fortran'ı görüntüler

6. Sayfa bağlantıları ekleme: `<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Not: Kod parçacığında desteklenmeyen yeni "Görüntüleme Dili" (örneğin, F#, Cobol, Fortran) kod renklendirmesi çok güzel olur.

**Örnek Yardım Görüntüleyicisi Konusu** Kod meta verileri, kod parçacığını, daraltılabilir alanı ve dile özgü metni tanımlamayı göstermektedir.

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

Bu Visual Studio F1'i seçmek, IDE içinde imlecin yerleşimi tarafından sağlanan değerleri üretir ve sağlanan değerlerle (imleç konumunu temel alarak) bir "özellik çantası" ekler. İmleç x özelliğinin üzerine geldiğinde x özelliği etkin/odakta olur ve özellik çantasına değer ekler.  F1 seçildiğinde özellik çantası doldurulur ve Visual Studio F1 kodu müşterilerin varsayılan Yardım kaynağının yerel mi yoksa çevrimiçi mi (çevrimiçi varsayılandır) olduğunu görmek için görünür, ardından kullanıcılar ayarına göre uygun dizeyi oluşturur (varsayılandır) - kabuk yürütme (exe başlatma parametreleri için Yardım Yöneticisi Kılavuzu'na bakın) ve özellik çantasındaki yerel yardım görüntüleyici + anahtar sözcük parametreleriyle yerel yardım çantasından veya parametre listesinde anahtar sözcüğüyle MSDN URL'sini oluşturur.

F1 için çok değerli dize olarak adlandırılan üç dize döndürülürse ilk terimini kullanın, bir isabet bulun ve bulunursa, bitti; yoksa, sonraki dizeye inin.  Sipariş önemlidir. Çok değerli anahtar sözcüklerin sunumu en uzun dizeden en kısa dizeye olmalıdır.  Çok değerli anahtar sözcüklerde bunu doğrulamak için, seçilen anahtar sözcüğü içerecek olan çevrimiçi F1 URL dizesine bakın.

Visual Studio 2012'de kasıtlı olarak çevrimiçi ve çevrimdışı arasında daha güçlü bir bölme yaptık. Bu nedenle, kullanıcının ayarı Çevrimiçi ise, 2010'da sahip olduğu Yardım Kitaplığı Aracısı üzerinden yönlendirme yapmak yerine F1 isteğini doğrudan MSDN'de çevrimiçi sorgu hizmetimize Visual Studio. Ardından bu bağlamda farklı bir şey yapıp çalışmay olmadığını belirlemek için "satıcı içeriği yüklü = true" durumuna güvenebilirsiniz. Doğruysa, müşterileriniz için desteklemek istediğinize bağlı olarak bu ayrıştırma ve yönlendirme mantığını gerçekleştirin. False ise MSDN'ye gideriz. Kullanıcının ayarı Yerel ise, tüm çağrılar yerel yardım altyapısına gider.

F1 Flow Diyagramı:

![F1 akışı](../../extensibility/internals/media/f1flow.png "F1flow")

Yardım Görüntüleyicisi varsayılan yardım içerik kaynağı çevrimiçi olarak ayarlanırken (Tarayıcıda başlat):

- Visual Studio İş ortağı (VSP) özellikleri F1 özellik çantasına bir değer yayır (özellik çantası ön eki.anahtar sözcüğü ve kayıt defterinde bulunan ön ek için çevrimiçi URL): F1, tarayıcıya bir VSP URL+ parametresi gönderir.

- Visual Studio özellikleri (dil düzenleyicisi, Visual Studio menü öğeleri vb.): F1, tarayıcıya Visual Studio URL'si gönderir.

Yardım Görüntüleyicisi varsayılan yardım içerik kaynağı yerel Yardım (Yardım Görüntüleyicisi'nde Başlat) olarak ayarlanırken:

- Anahtar sözcüğün F1 özellik çantası ile yerel mağaza dizini (yani, paket ön eki.anahtar sözcüğü = yerel mağaza dizininde bulunan değer) arasında eş olduğu VSP özellikleri: F1, konuyu Yardım Görüntüleyicisi'nde işler.

- Visual Studio özellikleri (VSP'nin Visual Studio özelliklerinden yayılan özellik çantasını geçersiz kılacak seçeneği yoktur): F1, Yardım Görüntüleyicisi'nde Visual Studio bir konu başlığı işler.

Satıcı Yardımı içeriği için F1 Geri Dönüş'lerini etkinleştirmek için aşağıdaki kayıt defteri değerlerini ayarlayın. F1 Geri Dönüş, Yardım Görüntüleyicisi'nin F1 Yardım içeriğini çevrimiçi olarak araması için ayarlandı ve satıcı içeriği kullanıcıların sabit sürücüsüne yerel olarak yüklenir. Varsayılan ayar çevrimiçi yardım için olsa bile, Yardım Görüntüleyicisi içerik için yerel Yardım'a bakmalı.

1. Yardım 2.3 kayıt defteri anahtarı altında **VendorContent** değerini ayarlayın:

   - 32 bit işletim sistemleri için:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent"=dword:00000001

   - 64 bit işletim sistemleri için:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent"=dword:00000001

2. İş ortağı ad alanını Yardım 2.3 kayıt defteri anahtarı altına kaydetme:

   - 32 bit işletim sistemleri için:

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner<<em> \\ alanı \> </em>

      "location"="offline"

   - 64 bit işletim sistemleri için:

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner<<em> \\ alanı \> </em>

      "location"="offline"

**Temel Yerel Ad Alanı Ayrıştırma**

Temel yerel ad alanı ayrıştırmayı açmak için, kayıt defterinde şu ada sahip yeni bir DWORD ekleyin: BaseNativeNamespaces ve değerini 1 olarak ayarlayın (desteklemek istedikleri Katalog anahtarı altında).  örneğin, Visual Studio kataloğunu kullanmak istiyorsanız, anahtarı yola ekleyebilirsiniz:

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

Visual Studio sürümü, Visual Studio iş ortakları için yalıtılmış ve tümleşik kabuklar da dahil olmak üzere birçok farklı Visual Studio ürünü kapsar.  Bu ürünlerin her biri, ürüne özel olarak bazı konu tabanlı yardım içeriği marka desteği gerektirir.  örneğin, Visual Studio konuların tutarlı marka sunumuna sahip olması gerekir, ancak ıso kabuğunu sarmalayan SQL Studio, her konu için kendi benzersiz yardım içeriği markalamasını gerektirir.  tümleşik bir kabuk iş ortağı, kendi konu markalarını koruyarak yardım konularının üst Visual Studio ürün yardım içerikleri dahilinde olmasını isteyebilir.

Marka paketleri, Yardım Görüntüleyicisi 'Ni içeren ürün tarafından yüklenir.  Visual Studio ürünleri için:

- Yardım Görüntüleyicisi \<locale> 2,3 uygulama kökünde (örnek: C:\Program Files (x86) \Microsoft yardım Viewer\v2.3) Yardım Görüntüleyici dil paketi 'ne bir geri dönüş marka paketi (Branding_. mshc) yüklenir.  Bu, ürün markası paketinin yüklü olmadığı (içerik yüklenmemiş) veya yüklü marka paketinin bozuk olduğu durumlarda kullanılır.  uygulama kök geri dönüş markalama paketi kullanıldığında Visual Studio öğeleri (logo ve geri bildirim) yok sayılır.

- içerik paketi hizmetinden Visual Studio içerik yüklendiğinde, bir marka paketi de yüklenir (ilk kez içerik yükleme senaryosu için).  Marka paketine yönelik bir güncelleştirme varsa, güncelleştirme sonraki içerik güncelleştirmesi veya ek paket yükleme eylemi gerçekleştiğinde yüklenir.

Microsoft Yardım Görüntüleyicisi konu meta verilerine dayalı olarak konuların markalamasını destekler.

- Konu meta verileri kendi kendine markalı = doğru tanımlar, konuyu olduğu gibi işler, hiçbir şey yapmaz (marka olarak en fazla).

- Konu meta verileri kendi kendine markalı = false tanımlıyor, TopicVendor meta veri değeriyle ilişkili marka paketini kullanın.

- Konu meta verileri name = "Microsoft. help. TopicVendor" Content = tanımlar \< branding package name in vendor MSHA> , içerik değerinde tanımlanan marka paketini kullanın.

- Visual Studio kataloğunda, marka paketlerinin öncelikli bir uygulaması vardır.  ilk Visual Studio varsayılan marka uygulanır ve ardından konu meta verilerinde tanımlandıysa ve ilişkili marka paketiyle (yükleme msha bölümünde tanımlandığı gibi) destekleniyorsa, satıcı tanımlı marka bir geçersiz kılma olarak uygulanır.

Marka öğeleri genellikle üç ana kategoriye ayrılır:

- Üstbilgi öğeleri (örnek geri bildirim bağlantısı, koşullu vazgeçme metni, logo)

- İçerik davranışları (örnek, genişletme/daraltma denetim metni öğeleri ve kod parçacığı öğeleri)

- Footer öğeleri (örnek telif hakkı)

Markalı öğeler olarak kabul edilen öğeler (bu belirtimde ayrıntılı) şunları içerir:

- Katalog/ürün logosu (örnek, Visual Studio)

- Geri bildirim bağlantısı ve e-posta öğeleri

- Vazgeçme Metni

- Telif hakkı metni

Visual Studio yardım görüntüleyicisi markalama paketindeki destek dosyaları şunlardır:

- Grafikler (logolar, simgeler vb.)

- Branding.js-içerik davranışlarını destekleyen betik dosyaları

- Branding.xml-Katalog içeriklerine sürekli olarak kullanılan dizeler.  Note: branding.xml Visual Studio yerelleştirme metin öğeleri için _locID = " \<unique value> " ekleyin

- Sunum tutarlılığı için marka. CSS stili tanımları

- Tutarlı yazdırılmış sunum için. CSS stili tanımları yazdırılıyor

Yukarıda belirtildiği gibi, marka paketleri konusuyla ilişkilendirilir:

- Meta verilerde Selfmarkalı = false tanımlandığında konu, Katalog markalama paketini devralır

- Ya da Selfmarkalı = false olduğunda ve MSHA 'da tanımlanmış benzersiz bir marka paketi varsa ve içerik yüklendiğinde kullanılabilir

Özel marka paketleri uygulayan VSPs 'ler için (VSP içeriği, Selfmarkalı = true), devam etmenin bir yolu, geri dönüş markalama paketiyle (yardım görüntüleyiciyle yüklenir) başlamamaya ve dosyanın adını uygun şekilde değiştirecek.  Branding_ \<locale> . mshc dosyası,. mshc olarak değiştirilen dosya uzantısına sahip bir zip dosyasıdır. bu nedenle, uzantıyı. mshc 'den .zip olarak değiştirmeniz ve içeriği ayıklamanız yeterlidir.  Bkz. marka paketi öğeleri için aşağıya bakın ve uygun şekilde değiştirin (örneğin, logoyu VSP logosu ve Branding.xml dosyasındaki logo başvurusu olarak değiştirin, VSP özellikleri başına Branding.xml güncelleştirin vb.).

Tüm değişiklikler tamamlandığında, istenen marka öğelerini içeren bir ZIP dosyası oluşturun ve uzantıyı. mshc olarak değiştirin.

Özel marka paketini ilişkilendirmek için, markalama mshc dosyasına yönelik başvuruyu içeren MSHA 'yı oluşturun (konuları içeren).  Temel bir MSHA oluşturmak için aşağıdaki "MSHA" başlığına bakın.

Branding.xml dosyası, konu başlığı içerdiğinde bir konudaki belirli öğeleri tutarlı bir şekilde işlemek için kullanılan öğelerin bir listesini içerir \<meta name="Microsoft.Help.SelfBranded" content="false"/> .  Branding.xml dosyasındaki öğelerin Visual Studio listesi aşağıda listelenmiştir.  Bu liste, kendi ürün marka ihtiyaçlarını karşılamak üzere bu öğeleri (örneğin logo, geri bildirim ve telif hakkı) değiştiren ISO kabuğu benimseme şablonu olarak kullanılmak üzere tasarlanmıştır.

Not: "{n}" tarafından belirtilen değişkenlerin kod bağımlılıkları vardır-bu değerlerin kaldırılması veya değiştirilmesi hatalara neden olur ve büyük olasılıkla uygulama kilitlenmesiyle karşılaşabilirsiniz. yerelleştirme tanımlayıcıları (örnek _locID = "codeparçacığının. n") Visual Studio marka paketine dahildir.

**Branding.xml**

| Öğe | Açıklama |
| - | - |
| Özellik | **CollapsibleArea** |
| Kullanırsınız | Genişlet içerik denetimi metnini Genişlet |
| **Öğe** | **Değer** |
| ExpandText | Genişlet |
| CollapseText | Daralt |
| Özellik | **CodeSnippet** |
| Kullanırsınız | Kod parçacığı denetim metni.  Note: "bölünmez" boşluk ile kod parçacığı içeriği, boşluk olarak değiştirilecek. |
| **Öğe** | **Değer** |
| CopyToClipboard | Panoya kopyala |
| ViewColorizedText | Renklendirilmiş görüntüleme |
| CombinedVBTabDisplayLanguage | Visual Basic (örnek) |
| VBDeclaration | Bildirim |
| VBUsage | Kullanım |
| Özellik | **Geri bildirim, altbilgi ve logo** |
| Kullanırsınız | Müşterinin, e-posta ile geçerli konu hakkında geri bildirim sağlaması için bir geri bildirim denetimi sağlayın.  İçerik için telif hakkı metni.  Logo tanımı. |
| **Öğe** | **Değer (Bu dizeler, içerik benimseme gereksinimini karşılayacak şekilde değiştirilebilir.)** |
| Yaptırımlar | © 2013 Microsoft Corporation. All rights reserved. |
| SendFeedback | \<a href="{0}" {1}>\</a>Bu konuda Microsoft 'A geri bildirim gönderin. |
| FeedbackLink | |
| Logo başlığı | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| Özellik | **Bildirim** |
| Kullanırsınız | Makine çevirisi içeriği için büyük/küçük harfe özgü bildirimler kümesi. |
| **Öğe** | **Değer** |
| MT_Editable | Bu makale makine çevirisi yapıldı. Bir Internet bağlantınız varsa, bu sayfayı orijinal Ingilizce içeriğiyle aynı anda düzenlenebilir modda görüntülemek için "Bu konuyu çevrimiçi görüntüle" seçeneğini belirleyin. |
| MT_NonEditable | Bu makale makine çevirisi yapıldı. Bir Internet bağlantınız varsa, bu sayfayı orijinal Ingilizce içeriğiyle aynı anda düzenlenebilir modda görüntülemek için "Bu konuyu çevrimiçi görüntüle" seçeneğini belirleyin. |
| MT_QualityEditable | Bu makale el ile çevrilmiştir. Bir Internet bağlantınız varsa, bu sayfayı orijinal Ingilizce içeriğiyle aynı anda düzenlenebilir modda görüntülemek için "Bu konuyu çevrimiçi görüntüle" seçeneğini belirleyin. |
| MT_QualityNonEditable | Bu makale el ile çevrilmiştir. Bir Internet bağlantınız varsa, bu sayfayı orijinal Ingilizce içeriğiyle aynı anda düzenlenebilir modda görüntülemek için "Bu konuyu çevrimiçi görüntüle" seçeneğini belirleyin. |
| MT_BetaContents | Bu makale, bir ön sürüm için makine çevirisi yapıldı. Bir Internet bağlantınız varsa, bu sayfayı orijinal Ingilizce içeriğiyle aynı anda düzenlenebilir modda görüntülemek için "Bu konuyu çevrimiçi görüntüle" seçeneğini belirleyin. |
| MT_BetaRecycledContents | Bu makale, ön sürüm için el ile çevrilmiştir. Bir Internet bağlantınız varsa, bu sayfayı orijinal Ingilizce içeriğiyle aynı anda düzenlenebilir modda görüntülemek için "Bu konuyu çevrimiçi görüntüle" seçeneğini belirleyin. |
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
| HomePageHelpSettings | yardım içeriği Ayarlar |
| HomePageHelpSettingsText | \<p>Geçerli ayarınız yerel yardımdır. Yardım Görüntüleyicisi bilgisayarınıza yüklediğiniz içeriği görüntüler. \<br /> yardım içeriği kaynağınızı değiştirmek için, Visual Studio menü çubuğunda \<span style="{0}"> yardım, yardım tercihi ayarla ' yı seçin \</span> .\<br />\</p> |
| Karşılık | MB |

**branding.js**

branding.js dosyası, Visual Studio yardım görüntüleyicisi markalama öğeleri tarafından kullanılan JavaScript içerir.  Aşağıda, marka öğelerinin ve destekleyici JavaScript işlevinin bir listesi verilmiştir.  Bu dosya için Yerelleştirilecek tüm dizeler, bu dosyanın en üstündeki "yerelleştirilebilir dizeler" bölümünde tanımlanmıştır.  ITıL dosyası branding.js dosyası içindeki Loc dizeleri için oluşturulmuştur.

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

Visual Studio yardım görüntüleyicisi markalama paketi, tutarlı Visual Studio yardım içerik sunumunu desteklemeye yönelik iki css dosyası içerir:

- Marka. css-kendini Selfmarkalı = false olarak işlemek için CSS öğelerini içerir

- Printer. css-kendini Selfmarkalı = false olarak işlemek için CSS öğelerini içerir

marka. css dosyaları Visual Studio konu sunumu için tanımlar içerir (desteklenmediği uyarısıyla, paket hizmetinden Branding_. mshc içinde bulunan marka. css 'nin \<locale> değişebilir).

**Grafik dosyaları**

Visual Studio içeriği, Visual Studio logosunu ve diğer grafikleri görüntüler.  Visual Studio Yardım Görüntüleyicisi markalama paketinde grafik dosyalarının tam listesi aşağıda gösterilmiştir.

|**Dosya**|**Kullanım**|**Örnekler**|
|-|-|-|
|clear.gif|Daraltılabilir Alanı işlemek için kullanılır||
|footer_slice.gif|Alt bilgi sunusu||
|info_icon.gif|Bilgi görüntülenirken kullanılır|Disclaimer|
|online_icon.gif|Bu simge çevrimiçi bağlantılarla ilişkilendirilen simgedir||
|tabLeftBD.gif|Kod parçacığı kapsayıcısı işlemek için kullanılır||
|tabRightBD.gif|Kod parçacığı kapsayıcısı işlemek için kullanılır||
|vs_logo_bk.gif|normal karşıtlık logo başvuruları için, etiketinde Branding.xml \<LogoFileName> kullanılır.  Diğer Visual Studio logo adı vs_logo_bk.gif.||
|vs_logo_wh.gif|etiketinde tanımlandığı gibi yüksek karşıtlıklı logo Branding.xml \<LogoFileNameHC> kullanılır.  Diğer Visual Studio logo adı vs_logo_wh.gif.||
|ccOff.png|Açıklamalı alt yazı grafiği||
|ccOn.png|Açıklamalı alt yazı grafiği||
|ImageSprite.png|Daraltılabilir Alanı işlemek için kullanılır|genişletilmiş veya daraltılmış grafik|

## <a name="deploy-a-set-of-topics"></a>Bir dizi konu dağıtma

Bu, bir MSHA dosyasından ve konuları içeren cabs veya MSHC'lerden oluşan bir Yardım Görüntüleyicisi içerik dağıtım kümesi oluşturmaya yönelik basit ve hızlı bir öğreticidir. MSHA, bir dizi cabs veya MSHC dosyasını tanımlayan bir XML dosyasıdır. Yardım Görüntüleyicisi MSHA'yı okuyarak içerik listesini (.CAB. MSHC dosyaları) yerel yükleme için kullanılabilir.

Bu yalnızca Yardım Görüntüleyicisi MSHA için çok temel XML şemasını açıklayan bir temel bilgidir.  Bu kısa genel bakışın ve örnek HelpContentSetup.msha'nın altında örnek bir uygulama vardır.

Bu temel bilgi için MSHA'nın adı HelpContentSetup.msha'dır (dosyanın adı uzantısıyla herhangi bir şey olabilir). MSHA). HelpContentSetup.msha (aşağıdaki örnekte) kullanılabilir cab'lerin veya MSHC'lerin bir listesini içerebilir.  Dosya türü MSHA içinde tutarlı olmalıdır (MSHA ve CAB dosya türlerinin birleşimini desteklemez). Her CAB veya MSHC için bir \<div class="package"> ... (aşağıdaki \</div> örneğine bakın) olması gerekir.

Not: Aşağıdaki uygulama örneğinde markalama paketini dahil edildik. Bu, gerekli içeriği işleme öğelerini ve içerik davranışlarını Visual Studio için dahil etmek açısından kritik öneme sahiptir.

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

Bu kılavuzda, Yardım içeriğinin bir Visual Studio Shell uygulamasına nasıl dahil olduğu ve ardından nasıl dağıtın?

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

1. Dosya Visual Studio altında Yeni  Project'ı seçin, Diğer  Project Türleri altında Genişletilebilirlik'i seçin ve ardından Visual Studio **Kabuk Yalıtılmış'ı seçin.**  Yalıtılmış `ContosoHelpShell` Kabuk şablonunu temel alan bir genişletilebilirlik projesi oluşturmak Visual Studio ) adını verir.

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

3. ContosoHelpShell sürüm klasöründeki içerikleri \\ \Program Files (x86) \Contoso\ klasörüne kopyalayın.

4. **Başlat** menüsünde **Çalıştır** ' i seçerek ve girerek kayıt defteri düzenleyicisini başlatın `Regedit` . Kayıt Defteri Düzenleyicisi 'nde **Dosya**' yı ve ardından **içeri aktar**' ı seçin. ContosoHelpShell proje klasörüne gidin. ContosoHelpShell alt klasöründe ContosoHelpShell. reg ' yi seçin.

5. Bir içerik deposu oluşturun:

    ISO kabuğu için-Contoso içerik deposu oluşturma C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]Tümleşik Kabuk için C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15 klasörünü oluşturun

6. CatalogType.xml oluşturun ve içeren içerik deposuna (önceki adım) ekleyin:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Aşağıdaki kayıt defteri anahtarlarını ekleyin:

    HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: LocationPath dize değeri:

    ISO kabuğu için:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Tümleşik Kabuk:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    Anahtar: katalogadı dize değeri: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] belgeler. ISO kabuğu için bu, kataloğunuzun adıdır.

8. İçeriğinizi (Cabs veya MSHC ve MSHA) yerel bir klasöre kopyalayın.

9. İçerik deposunu test etmek için örnek tümleşik kabuk komut satırı. ISO kabuğu için, Katalog ve launchingApp değerlerini ürünle eşleşmesi için uygun şekilde değiştirin.

     "C:\Program Files (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe"/katalogadı VisualStudio15/helpQuery method = "Page&ID = ContosoTopic0"/launchingApp Microsoft, VisualStudio, 12.0

10. Contoso uygulamasını başlatın (contoso uygulama kökünden). ISO kabuğu 'nda **Yardım** menü öğesini seçin ve **yerel yardım 'ı kullanmak** için **Yardım tercihini ayarla** ' yı değiştirin.

11. Kabuk içinde **Yardım** menü öğesini seçin ve ardından **Yardım 'ı görüntüleyin**. Yerel Yardım Görüntüleyicisi başlatması gerekir. **Içeriği Yönet** sekmesini seçin. **Yükleme kaynağı** altında **disk** seçenek düğmesini seçin. **...** Düğmesini seçin ve contoso içeriğini içeren yerel klasöre (Yukarıdaki adımda yerel klasöre kopyalanmış) gidin. HelpContentSetup. msha ' ı seçin. Contoso artık kitap seçimlerinde kitap olarak görünür olmalıdır. **Ekle**' yi seçin ve ardından **Güncelleştir** düğmesini (sağ alt köşedeki) seçin.

12. Contoso IDE içinde F1 işlevini test etmek için F1 tuşunu seçin.

## <a name="additional-resources"></a>Ek kaynaklar

çalışma zamanı apı 'si için bkz. [Windows yardım apı 'si](/previous-versions/windows/desktop/helpapi/helpapi-portal).

Yardım API 'sinin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Yardım Görüntüleyicisi kod örnekleri](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples).

[Geliştirici Community](https://aka.ms/feedback/suggest?space=8)özellik önerileri gönderebilirsiniz.
