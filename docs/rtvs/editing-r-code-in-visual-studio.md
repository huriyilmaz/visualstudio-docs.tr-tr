---
title: R kodunu düzenleme
description: Visual Studio, tüm özellikleri ve uzantıları kullanma becerisini korurken R için özel bir düzenleme deneyimi sağlar.
ms.date: 11/05/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 27db2b3b5edfe5fbaed9899927f7e9e866bd7d7a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076106"
---
# <a name="edit-r-code-in-visual-studio"></a>R kodunu Visual Studio

Visual Studio için R Araçları (RTVS), tüm özellikleri ve uzantıları Visual Studio korurken özel olarak R için düzenleme deneyimini uyarlar. (Örneğin, VIM anahtar bağlamalarını tercih ediyorsanız, ücretsiz [VsVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim) uzantısını Market'Visual Studio yükleyebilirsiniz.)

Bu makaledeki özelliklere ek olarak bkz. [IntelliSense,](r-intellisense.md) [linting,](linting-r-code.md)kod parçacıkları [ve](code-snippets-for-r.md) [R Markdown.](rmarkdown-with-r-in-visual-studio.md)

## <a name="syntax-highlighting"></a>Söz dizimi vurgulama

RtVS, kodunuzun dizeler, açıklamalar ve anahtar sözcükler gibi farklı bölümlerini renklendirmeye ek olarak açıklamalarda bağlantıları da vurgular ve sağlar:

![R kodu için söz dizimi renklendirmesi](media/editing-syntax-colors.png)

Yazı tiplerini ve belirli vurgulama renklerini özelleştirmek için Araçlar Seçenekleri komutunu seçin, Ortam Yazı Tipleri ve Renkler'e gidin, ardından Öğeleri görüntüle kutusunda R ile ilgili  >     >   **öğelerin ayarlarını** değiştirin:

![R kodu için yazı tipleri ve renk seçenekleri](media/editing-syntax-colors-options.png)

Visual Studio söz dizimi hatalarının da alt çizgilerini çizin:

![R kodunda söz dizimi hatası vurgulama](media/editing-syntax-error.png)

Bu davranışı değiştirmek için düzenleyici **seçeneklerinin altındaki**  >  **Gelişmiş Söz Dizimi** denetimi [ayarına bakın.](#editor-options)

## <a name="edit-and-organize-code"></a>Kodu düzenleme ve düzenleme

Siz kod yazarak RTVS, [IntelliSense](r-intellisense.md) sayfasında açıklandığı gibi otomatik tamamlama sağlar. Ayraçların ve parantezlerin tamamlanması gibi otomatik biçimlendirme de yapar:

![Satır içi biçimlendirme animasyonu](media/editing-inline-formatting.gif)

Birçok parametreye sahip işlevlere çağrılar yazarken, genellikle kodun okunmalarını kolaylaştırmak için parametreleri sıraya almak istersiniz. RTVS, parametreler için kümenizin girintisini hatırlar ve sonraki satırlar için bu girintiyi otomatik olarak uygular:

![Otomatik girintileme animasyonu](media/editing-auto-indentation.gif)

Bu davranışı değiştirmek için [Bkz. Sekmeler](#editor-options) grubu için **düzenleyici** seçenekleri.

Daraltılabilir kod bölgeleri, düzenleyicide kodun bir bölümünü geçici olarak gizlemeye izin sağlar. Visual Studio satırlı deyimler için olduğu gibi, Gelişmiş Satır Çizgisi Kodu açıklama satırı seçeneği Kapalı olarak ayarlanmadıkça sizin için otomatik olarak çeşitli  >    >   bölgeler oluşturur.

Kendi bölgenizi oluşturmak için, istenen kodu ile sona eren açıklamalarla `---` çevreler. Kodun sol tarafından yapılan küçük +/- denetimleri bölgeleri genişletmenizi ve daraltmayı sağlar:

![Açıklamalarla daraltılabilir bölge oluşturma](media/editing-collapsible-regions.gif)

Varsayılan olarak, Visual Studio tuşuna basarak **boşluklar ekler.** Seçenekler, Metin Düzenleyici, Sekmeler'de açıklandığı [gibi bu davranışı değiştirebilirsiniz.](../ide/reference/options-text-editor-all-languages.md)

## <a name="code-navigation"></a>Kod gezintisi

Kod gezintisi, R program ve kitaplıklarının kaynak koduna hızlı erişim sağlar. Bu özellikler, kodunuzu el ile aramak zorunda kalmadan çalışma akışında kalmanızı sağlar.

**Tanıma Git** işlevi hızla bir işlev tanımına atlar veya bir kitaplık işlevinin kaynak kodunu okumak için satır içi bir mini düzenleyici açılır. İstediğiniz işleve sağ tıklayın ve Tanıma Git'i **seçin** veya imleci işleve yerleştirerek **F12 tuşuna basın.**

Bu komut, işlevin kaynak kodunu içeren yeni bir düzenleyici penceresi açar. İmleç, işlev tanımının başında rahatça konumlandı.

**Sağ tıklama** menüsünden veya **Alt** + **F12'den** çağrılan Tanıma Göz At işlevi, işlev çağrısının altına işlevin kaynak kodunu içeren salt okunur, kaydırılabilir bir bölge ekler:

![Tanıma göz atma animasyonu](media/editing-peek-definition.gif)

## <a name="send-code-to-the-interactive-window"></a>Etkileşimli pencereye kod gönderme

Birçok geliştirici, düzenleyicide kod yazmak ve ardından bu [](interactive-repl-for-r-in-visual-studio.md) kodu hemen test etmek üzere etkileşimli pencereye (Read-Evaluate-Print-Loop veya REPL olarak da bilinir) göndermek ister. R **düzenleyicisinde Ctrl** Enter tuşlarına basılarak geçerli kod satırı etkileşimli +  pencereye gönderildi ve imleci sonraki satıra yerleştirildi. **Ctrl** + **Enter** tuşunu basılı tutarak düzenleyiciden kodunuzu etkili bir şekilde adım adım atabilirsiniz.

Ayrıca kodu seçerek **Ctrl** + **Enter tuşuna basarak** seçimin tamamını uygulayabilirsiniz. Alternatif olarak, seçime sağ tıklayın ve Etkileşimli'de **Yürüt'u seçin.**

## <a name="format-code"></a>Kodu biçimlendirme

Visual Studio otomatik biçimlendirme özelliği, hem sizin hem de düzenleyiciye yapıştıran kodun tercihlerinize göre biçimlendirilmiş şekilde biçimlendirilmiş şekilde tutar. Ayrıca, bu tercihleri uygulamak için bir seçim, sağ tıklar ve Biçim Seçimi **(** **Ctrl** + **K**,**F**) öğesini seçebilirsiniz. Örneğin, tek satırda bir işlev tanımına sahip olursanız:

```R
f<-function  (a){  return(a + 1) }
```

Biçimlendirme uygulanarak şu şekilde temizlenir:

```R
f <- function(a) { return(a + 1) }
```

Kod dosyasının tamamını yeniden biçimlendirmek için Gelişmiş Biçim **Belgesini Düzenle**  >    >   (**Ctrl** + **E**, D )**öğesini seçin.**

Otomatik biçimlendirme, geri alınamaz ayrı bir işlemdir. Örneğin, düzenleyiciye kod yapıştırıyorsanız ve biçimlendirme geçerli ise, Geri Al'ı Düzenle'yi seçmek veya Ctrl Z tuşlarına basıldıktan sonra biçimlendirme tersine çevrilir; ikinci bir Geri Al,  >    +  yapıştırma işleminin kendisini tersine çevirer. 

Biçimlendirme seçenekleri (biçimlendirmeyi kapatma da dahil) Metin **Düzenleyici**  >  R **Gelişmiş** **sekmesindeki Araçlar Seçenekler**  >    >  **aracılığıyla** ayarlanır. **R** Araçları Düzenleyicisi seçenekler komutunu kullanarak veya düzenleyiciye sağ tıklar ve Biçimlendirme seçenekleri'ni seçerek  >   doğrudan bu sayfaya **gidebilirsiniz.** Ayrıntılar için [düzenleyici seçenekleri](#editor-options) bölümüne bakın.

## <a name="inserting-roxygen-comments"></a>Gen açıklamalarını ekleme

RTVS, bir işlevin parametre adlarını kullanarak [Nedenygen](https://cran.r-project.org/web/packages/roxygen2/index.html) yorumları oluşturmak için bir kısayol sağlar. İşlev `###` tanımının üzerindeki boş bir satıra yazmanız gerekir:

![Bir Zamanygen açıklaması ekleme animasyonu](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Düzenleyici seçenekleri

Düzenleyiciye özgü seçenekler Araçlar Seçenekleri **komutu aracılığıyla** ayarlanır, Metin Düzenleyici R'ye giderek veya R Araçları Düzenleyici  >   Seçenekleri kısayol   >   **komutunu**  >  **kullanın.**

Genel, Kaydırma **çubukları** ve  Sekmeler sekmeleri seçenekleri R'ye özgü değildir, ancak tüm diller için Visual Studio ancak dil bazında uygulanan genel ayarlardır. Ayrıntılar için aşağıdaki makalelere bakın:

- [Seçenekler, Metin Düzenleyici, Tüm Diller](../ide/reference/options-text-editor-all-languages.md)
- [Kaydırma çubuğunu özelleştirerek kodunuzu izleme](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Seçenekler, Metin Düzenleyici, Sekmeler](../ide/reference/options-text-editor-all-languages-tabs.md)

**R** Gelişmiş  >  **sekmesindeki seçenekler** RTVS'ye özeldir:

| Grup | Seçenek | Varsayılan | Açıklama |
| --- | --- | --- | --- |
| Biçimlendirme | Otomatik biçimlendirme | Açık | Siz yazarken kodu yeniden biçimlendirin. Seçimi Biçimlendir veya **Belgeyi Biçimlendir** **komutlarını** etkilemez. |
| | Genişletilmiş ayraçlar | Kapalı | Yeni bir satıra açık { yer. |
| | Yapıştırmada biçimlendirme | Açık | Yapıştırmak için biçimlendirme uygular. |
| | } üzerinde kapsamı biçimlendirme | Açık | Kapanış } yazarak kapsamı biçimlendirme. |
| | Virgülden sonra boşluk | Açık | Virgülden sonra boşluk yer. |
| | Anahtar sözcüğün ardından boşluk | Açık | , ve gibi anahtar sözcüklerden `if` sonra `while` boşluklar `repeat` yer. |
| | { öncesinde boşluk | Açık | {. |
| | Çevresinde boşluklar = | Açık | Eşittir işareti çevresinde boşluklar yer. |
| IntelliSense | Enter tuşuna basın | Kapalı | Enter tuşuna basıldığında otomatik **tamamlama** seçimini işler. |
| | Boşluk anahtarında Yürüt | Kapalı | **Boşluk** basıldığında otomatik tamamlama seçimini kaydeder.|
| | İlk karakter için tamamlanma listesi | Açık | İlk karakter türlerindeki tamamlanma listesini gösterir. Kapalı olduğunda,   >  **IntelliSense**  >  **Liste üyelerini** Düzenle (**CTRL** + **J**) ile bir tamamlanma listesi görüntülenir. |
| | **Sekme** anahtarındaki tamamlanma listesi | Kapalı | Bir veya daha fazla karakter yazıp **Tab** tuşuna basarak tamamlanma listesini çağırır. |
| | Kısmi türlerin bağımsız değişken adlarını Eşleştir | Kapalı | Bir işlev çağrısında bağımsız değişken adları yazarken, imza yardımı en iyi eşleşme olan bağımsız değişken için bir açıklama gösterir. |
| Etkileşimli Pencere | R konsolundaki sözdizimi denetimi | Kapalı | Etkileşimli pencerede söz dizimi denetimi uygular. Sözdizimi denetimi, çok satırlı deyimlerle düzgün çalışmayabilir. |
| Anahat Oluşturma | Kod anahat oluşturma | Açık | , Çok satırlı deyimler gibi alanlarda otomatik olarak daraltılabilir bölgeler oluşturur. |
| Söz dizimi denetimi | Sözdizimi hatalarını göster | Açık | Kodun otomatik sözdizimi denetimini sunar. |
