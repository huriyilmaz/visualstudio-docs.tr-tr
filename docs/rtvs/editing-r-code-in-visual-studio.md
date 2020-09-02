---
title: R kodunu Düzenle
description: Visual Studio, tüm özellikleri korurken ve uzantıları kullanma özelliği ile R için uyarlanmış bir düzen deneyimi sağlar.
ms.date: 11/05/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 7ecfd8f1cf50e94991ce2fd94ad94ac9815c92ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315102"
---
# <a name="edit-r-code-in-visual-studio"></a>Visual Studio 'da R kodunu Düzenle

Visual Studio için R Araçları (RTVS), tüm özellikleri korurken ve uzantıları kullanma olanağı sağlarken, Visual Studio düzenleme deneyimini özel olarak R için uyarlar. (Örneğin, VıM anahtar bağlamalarını tercih ediyorsanız, Visual Studio Market ücretsiz [Vsvım uzantısını](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim) yükleyebilirsiniz.)

Bu makaledeki özelliklere ek olarak, bkz. [IntelliSense](r-intellisense.md), [linme](linting-r-code.md), [kod parçacıkları](code-snippets-for-r.md)ve [R Markdown](rmarkdown-with-r-in-visual-studio.md).

## <a name="syntax-highlighting"></a>Söz dizimi vurgulama

Kodunuzun, dizeler, açıklamalar ve anahtar sözcükler gibi farklı parçalarını renklendirme yanı sıra, RTVS de vurgular ve açıklamalarda bağlantıları sağlar:

![R kodu için sözdizimi renklendirme](media/editing-syntax-colors.png)

Yazı tiplerini ve belirli vurgu renklerini özelleştirmek için, **Araçlar**  >  **Seçenekler** komutunu seçin, **ortam**  >  **yazı tipleri ve renkler**' e gidin, ardından **görüntüleme öğeleri** kutusunda R ile ilgili öğelerin ayarlarını değiştirin:

![R kodu için yazı tipleri ve renk seçenekleri](media/editing-syntax-colors-options.png)

Visual Studio Ayrıca düzenleyicideki sözdizimi hatalarının altını çizer:

![R kodunda sözdizimi hatası vurgulama](media/editing-syntax-error.png)

Bu davranışı değiştirmek için, **Advanced**  >  [Düzenleyici seçenekleri](#editor-options)altındaki Gelişmiş**sözdizimi denetimi** ayarı bölümüne bakın.

## <a name="edit-and-organize-code"></a>Kodu düzenleme ve düzenleme

Kodu yazarken, RTVS, [IntelliSense](r-intellisense.md) sayfasında açıklandığı şekilde otomatik tamamlama sağlar. Ayrıca, küme ayraçlarının ve ayracın tamamlanmasından sonra otomatik biçimlendirme yapar:

![Satır içi biçimlendirme animasyonu](media/editing-inline-formatting.gif)

Çok sayıda parametreye sahip işlevlere çağrı yazarken, kodu daha kolay okunabilir hale getirmek için parametreleri hizalamak istediğiniz zaman. RTVS, parametreleri için ayarladığınız Girintiyi anımsar ve sonraki satırlar için otomatik olarak bu girintileme uygular:

![Otomatik girintileme animasyonu](media/editing-auto-indentation.gif)

Bu davranışı değiştirmek için, **Sekmeler** grubu için [Düzenleyici seçenekleri](#editor-options) bölümüne bakın.

Daraltılabilir kod bölgeleri, düzenleyicideki kodun bir parçasını geçici olarak gizlemenizi sağlar. Visual Studio, **Gelişmiş**ana hat kod ana hattı  >  **Outlining**  >  **Code outlining** seçeneği kapalı olarak ayarlanmadığı sürece, çok satırlı deyimler için otomatik olarak çeşitli bölgeler oluşturur.

Kendi bölgesini oluşturmak için, istenen kodu ile biten açıklamalarla çevreleyin `---` . Kodun solundaki küçük +/-denetimleri, daha sonra bölgeleri genişletmenize ve daraltmanıza imkan tanır:

![Açıklamalarla daraltılabilir bölge oluşturma](media/editing-collapsible-regions.gif)

Varsayılan olarak, **sekme** tuşuna bastığınızda Visual Studio boşluk ekler. [Seçenekler, metin düzenleyici, sekmeler](../ide/reference/options-text-editor-all-languages.md)bölümünde açıklandığı gibi bu davranışı yeniden değiştirebilirsiniz.

## <a name="code-navigation"></a>Kod gezintisi

Kod gezintisi, R programınızın ve kitaplıklarının kaynak koduna hızlı erişim sağlar. Bu özellikler, kodunuzu el ile aramak yerine çalışmalarınızın akışında tutar.

**Tanıma Git** bir işlev tanımına hızlı bir şekilde atlar veya bir kitaplık işlevinin kaynak kodunu okumak için bir satır içi mini-düzenleyiciyi açılır. İlgilendiğiniz işleve sağ tıklayıp **Tanıma Git**' i seçin ya da imleci Işleve yerleştirip **F12**tuşuna basın.

Bu komut, işlevin kaynak kodunu içeren yeni bir düzenleyici penceresi açar. İmleç, işlev tanımının başlangıcında kolay bir şekilde konumlandırılmış.

Sağ tıklama menüsünden veya **alt**F12 'tan çağrılan **Açıklama tanımı**, + **F12**işlev çağrısının altındaki işlevin kaynak kodunu içeren salt okunurdur, kaydırılabilir bir bölge ekler:

![Göz atma tanımı için animasyon](media/editing-peek-definition.gif)

## <a name="send-code-to-the-interactive-window"></a>Etkileşimli pencereye kod gönder

Birçok geliştirici düzenleyicide kod yazmak ve ardından anında test için bu kodu [etkileşimli pencereye](interactive-repl-for-r-in-visual-studio.md) göndermek (Ayrıca Read-değerlendir-PRINT-Loop veya REPL olarak da bilinir). R düzenleyicisinde **CTRL** + **ENTER** tuşlarına basmak, geçerli kod satırını etkileşimli pencereye gönderir ve ardından imleci bir sonraki satıra koyar. **CTRL** + **ENTER**ile, düzenleyiciden kodunuzda kodlarda etkin bir şekilde geçiş yapabilirsiniz.

Ayrıca, **Ctrl** + tüm seçimi uygulamak için kod seçip CTRL**ENTER** tuşuna basabilirsiniz. Alternatif olarak, seçime sağ tıklayıp **etkileşimli olarak çalıştır**' ı seçin.

## <a name="format-code"></a>Kodu biçimlendirme

Visual Studio 'nun otomatik biçimlendirmesi yazdığınız kodu ve düzenleyicinize göre ayarlanmış şekilde, düzenleyiciye yapıştırdığınız kodu korur. Ayrıca, bu tercihleri uygulamak için bir seçim yapabilir, sağ tıklayıp **Biçim Seçimi** (**CTRL** + **K**,**F**) seçeneğini belirleyebilirsiniz. Örneğin, tek bir satırda bir işlev tanımınız varsa:

```R
f<-function  (a){  return(a + 1) }
```

Biçimlendirme uygulandığında şu kadar temizler:

```R
f <- function(a) { return(a + 1) }
```

Tüm kod dosyasını yeniden biçimlendirmek için, **Edit**  >  **Gelişmiş**  >  **Biçim belgesini** Düzenle (**CTRL** + **E**,**D**) seçeneğini belirleyin.

Otomatik biçimlendirme, geri alınabilecek ayrı bir işlemdir. Örneğin, düzenleyiciye kod yapıştırdıysanız ve bu biçim geçerliyse, **Düzenle**  >  **geri al** ' ı veya **CTRL** + **Z** tuşlarına basıldığında biçimlendirmeyi tersine çevirir; ikinci bir **geri alma** , yapıştırmayı kendisini tersine çevirir.

Biçimlendirme seçenekleri (biçimlendirmeyi kapatma dahil) **Tools**  >  , **metin düzenleyici****Options**  >  **R**  >  **Gelişmiş** sekmesindeki Araçlar seçenekleri aracılığıyla ayarlanır. **R araçları**  >  **Düzenleyicisi seçenekler** komutunu kullanarak veya düzenleyiciye sağ tıklayıp **biçimlendirme seçenekleri**' ni seçerek doğrudan bu sayfaya gidebilirsiniz. Ayrıntılar için [Düzenleyici seçenekleri](#editor-options) bölümüne bakın.

## <a name="inserting-roxygen-comments"></a>Roxygen açıklamaları ekleme

RTVS, bir işlevin parametre adlarını kullanarak [Roxygen](https://cran.r-project.org/web/packages/roxygen2/index.html) açıklamaları oluşturmaya yönelik bir kısayol sağlar. Yalnızca `###` işlev tanımının üzerine boş bir satır yazın:

![Roxygen yorumu ekleme animasyonu](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Düzenleyici seçenekleri

Düzenleyiciye özgü seçenekler, **Araçlar**  >  **Seçenekler** komutuyla, **metin Düzenleyicisi**  >  **R**'ye gidilerek ve **r araçları**  >  **Düzenleyicisi seçenekleri**kısayol komutu kullanılarak ayarlanır.

**Genel**, **kaydırma çubukları**ve **Sekmeler** sekmelerinde bulunan seçenekler R 'ye özgü değildir, ancak genel Visual Studio ayarları tüm diller için kullanılabilir ancak dile göre ayrı olarak uygulanır. Ayrıntılar için aşağıdaki makalelere bakın:

- [Seçenekler, Metin Düzenleyici, Tüm Diller](../ide/reference/options-text-editor-all-languages.md)
- [Kaydırma çubuğunu özelleştirerek kodunuzu izleyin](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Seçenekler, metin düzenleyici, sekmeler](../ide/reference/options-text-editor-all-languages-tabs.md)

**R**  >  **Gelişmiş** sekmesindeki seçenekler rtvs 'ye özgüdür:

| Gruplama | Seçenek | Varsayılan | Description |
| --- | --- | --- | --- |
| Biçimlendirme | Otomatik biçimlendirme | Açık | Yazdığınız şekilde kodu yeniden biçimlendirir. **Biçim Seçimi** veya **Biçim belgesi** komutlarını etkilemez. |
| | Genişletilmiş küme ayraçları | Kapalı | Açık bir {yeni satıra koyar. |
| | Yapıştırırken Biçimlendir | Açık | Yapıştırma sırasında biçimlendirme uygular. |
| | } Üzerinde kapsam Biçimlendir | Açık | Bir Closing-yazdıktan sonra kapsam biçimlendirir. |
| | Virgülden sonra boşluk | Açık | Virgüllerden sonra boşluk koyar. |
| | Anahtar sözcüğünden sonra boşluk | Açık | , Ve gibi anahtar sözcüklerden sonra boşluk koyar `if` `while` `repeat` . |
| | Önceki boşluk { | Açık | {' Dan önce bir boşluk koyar. |
| | Etrafındaki boşluklar = | Açık | Eşittir işaretinin etrafına boşluk koyar. |
| IntelliSense | ENTER tuşuna bir Kaydet | Kapalı | **ENTER** tuşuna basıldığında otomatik tamamlama seçimini kaydeder. |
| | Boşluk anahtarında Yürüt | Kapalı | **Boşluk** basıldığında otomatik tamamlama seçimini kaydeder.|
| | İlk karakter için tamamlanma listesi | Açık | İlk karakter türlerindeki tamamlanma listesini gösterir. Kapalı olduğunda, **Edit**  >  **IntelliSense**  >  **Liste üyelerini** Düzenle (**CTRL** + **J**) ile bir tamamlanma listesi görüntülenir. |
| | **Sekme** anahtarındaki tamamlanma listesi | Kapalı | Bir veya daha fazla karakter yazıp **Tab**tuşuna basarak tamamlanma listesini çağırır. |
| | Kısmi türlerin bağımsız değişken adlarını Eşleştir | Kapalı | Bir işlev çağrısında bağımsız değişken adları yazarken, imza yardımı en iyi eşleşme olan bağımsız değişken için bir açıklama gösterir. |
| Etkileşimli Pencere | R konsolundaki sözdizimi denetimi | Kapalı | Etkileşimli pencerede söz dizimi denetimi uygular. Sözdizimi denetimi, çok satırlı deyimlerle düzgün çalışmayabilir. |
| Anahat Oluşturma | Kod anahat oluşturma | Açık | , Çok satırlı deyimler gibi alanlarda otomatik olarak daraltılabilir bölgeler oluşturur. |
| Söz dizimi denetimi | Sözdizimi hatalarını göster | Açık | Kodun otomatik sözdizimi denetimini sunar. |
