---
title: R kodunu edit
description: Visual Studio, tüm özellikleri ve uzantıları kullanma yeteneğini korurken R için özel bir düzenleme deneyimi sağlar.
ms.date: 11/05/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 7ecfd8f1cf50e94991ce2fd94ad94ac9815c92ca
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302716"
---
# <a name="edit-r-code-in-visual-studio"></a>Visual Studio'da R kodunu edit

R Tools for Visual Studio (RTVS), Visual Studio düzenleme deneyimini özellikle R için uyarlarken, tüm özellikleri ve uzantıları kullanma yeteneğini korur. (Örneğin, VIM anahtar bağlamalarını tercih ederseniz, Visual Studio Marketplace'ten ücretsiz [VsVim uzantısını](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim) yükleyebilirsiniz.)

Bu makaledeki özelliklere ek olarak, ayrıca [IntelliSense](r-intellisense.md), [linting](linting-r-code.md), [kod parçacıkları](code-snippets-for-r.md)ve [R Markdown](rmarkdown-with-r-in-visual-studio.md)bakın.

## <a name="syntax-highlighting"></a>Sözdizimi vurgulama

Parolanızın dizeleri, yorumlar ve anahtar kelimeler gibi farklı bölümlerini boyamanın yanı sıra, RTVS yorumlardaki bağlantıları da vurgular ve etkinleştirirken:

![R kodu için sözdizimi boyama](media/editing-syntax-colors.png)

Yazı tiplerini ve belirli vurgurenklerini özelleştirmek için **Araçlar** > **Seçenekleri** komutunu seçin, **Çevre** > **Yazı Tipleri ve Renkler'e**gidin ve ardından **Ekran öğeleri** kutusundaKi R ile ilgili öğelerin ayarlarını değiştirin:

![R kodu için yazı tipleri ve renk seçenekleri](media/editing-syntax-colors-options.png)

Visual Studio ayrıca editördeki sözdizimi hatalarının altını çizer:

![R kodunda sözdizimi hatası vurgulama](media/editing-syntax-error.png)

Bu davranışı değiştirmek [için, düzenleyici seçenekleri](#editor-options)altında **Gelişmiş** > **Sözdizimi denetim** ayarı bakın.

## <a name="edit-and-organize-code"></a>Kodu düzenleme ve düzenleme

Kod yazarken, RTVS [IntelliSense](r-intellisense.md) sayfasında açıklandığı gibi otomatik tamamlama sağlar. Ayraçların tamamlanması ve parantez gibi otomatik biçimlendirme de yapar:

![Satır altı biçimlendirmeanimasyonu](media/editing-inline-formatting.gif)

Birçok parametreye sahip işlevlere çağrı yazarken, çoğu zaman kodun okunmasını kolaylaştırmak için parametreleri hizalamak istersiniz. RTVS parametreler için ayarladığınız girintiyi hatırlar ve sonraki satırlar için bu girintiyi otomatik olarak uygular:

![Otomatik girintinin animasyonu](media/editing-auto-indentation.gif)

Bu davranışı değiştirmek için **Sekmeler** grubunun [düzenleyici seçeneklerine](#editor-options) bakın.

Katlanabilir kod bölgeleri, kodun bir bölümünü geçici olarak düzenleyicide gizlemenize izin verebiliyor. Visual Studio, **Gelişmiş** > **Anahat** > **Kodu anahatlama** seçeneği Kapalı olarak ayarlanmadığı sürece, çok satırlı ifadelerde olduğu gibi sizin için otomatik olarak çeşitli bölgeler oluşturur.

Kendi bölgenizi oluşturmak için, istenilen kodu ' yla `---`biten yorumlarla çevreleyin. Kodun solundaki küçük +/- denetimleri, bölgeleri genişletmenize ve daraltmanıza olanak tanır:

![Yorumlarla birlikte katlanabilir bir bölge oluşturma](media/editing-collapsible-regions.gif)

Varsayılan olarak, Visual Studio **Sekme** tuşuna bastığınızda boşluk ekler. Seçenekler, [Metin Düzenleyicisi, Sekmeler'de](../ide/reference/options-text-editor-all-languages.md)açıklandığı gibi bu davranışı yine değiştirebilirsiniz.

## <a name="code-navigation"></a>Kod gezintisi

Kod gezintisi, R programınızın ve kitaplıklarının kaynak koduna hızlı erişim sağlar. Bu özellikler, kodunuzu el ile aramak zorunda kalmaktansa çalışmanızın akışında kalmanızı sağlar.

**Go To Definition** hızlı bir şekilde işlev tanımına atlar veya kitaplık işlevinin kaynak kodunu okumak için satır içi bir mini düzenleyici açılır. İlgi alanının işlevini sağ tıklatın ve **Tanıya Git'i**seçin veya imleci fonksiyona yerleştirin ve **F12**tuşuna basın.

Bu komut, işlevin kaynak kodunu içeren yeni bir düzenleyici penceresi açar. İmleç, işlev tanımının başında uygun bir şekilde konumlandırılır.

Sağ tıklama menüsünden veya **Alt**+**F12'den**çağrılan **Peek Definition,** işlev çağrısının altındaki işlevin kaynak kodunu içeren salt okunur, kaydırılabilir bir bölge ekler:

![Peek tanımı için animasyon](media/editing-peek-definition.gif)

## <a name="send-code-to-the-interactive-window"></a>Etkileşimli pencereye kod gönderme

Birçok geliştirici düzenleyiciye bazı kodlar yazmayı ve bu kodu hemen sınama için [etkileşimli pencereye](interactive-repl-for-r-in-visual-studio.md) göndermeyi (Oku-Değerlendir-Yazdır-Döngü veya REPL olarak da bilinir) ister. **Ctrl**+**Enter'a** basıldığında R düzenleyicisi geçerli kod satırını etkileşimli pencereye gönderir ve imleci bir sonraki satıra yerleştirir. **Ctrl**+**Enter**ile, daha sonra, etkili bir şekilde düzenleyiciden kod unuzu adım atabilirsiniz.

Ayrıca kodu seçebilir ve tüm seçimi uygulamak için **Ctrl**+**Enter** tuşuna basabilirsiniz. Alternatif olarak, seçimi sağ tıklatın ve **Etkileşimli yürüt'ün'de yürüt'ünü**seçin.

## <a name="format-code"></a>Kodu biçimlendirme

Visual Studio'nun otomatik biçimlendirmesi, yazdığınız kodun yanı sıra, tercihlerinize göre ayarlanan olarak biçimlendirilmiş olarak editöre yapıştırdığınız kodu da tutar. Ayrıca bir seçim yapabilir, sağ tıklatabilir ve bu tercihleri uygulamak için **Biçim Seçimi** **(Ctrl**+**K**,**F)** seçeneğini belirleyebilirsiniz. Örneğin, tek bir satırda bir işlev tanımı varsa:

```R
f<-function  (a){  return(a + 1) }
```

Biçimlendirme uygulamak onu şu şekilde temizler:

```R
f <- function(a) { return(a + 1) }
```

Tüm kod dosyasında yeniden biçimlendirmek için**Gelişmiş** > **Biçim Belgesini** **(Ctrl**+E ,**D)** **düzelt'i** > seçin.**E**

Otomatik biçimlendirme geri alınabilir ayrı bir işlemdir. Örneğin, kodu düzenleyiciye yapıştırıp biçimlendiriyorsanız,**Geri Al'ı** **Edit'i** > seçerek veya biçimlendirmeyi tersine çevirdikten sonra **Ctrl**+**Z** tuşuna basmak geçerlidir; ikinci bir **Geri Alma** yapıştırın kendisini tersine çevirir.

Biçimlendirme seçenekleri (biçimlendirmeyi kapatma dahil) **Metin Düzenleyicisi** > **R** > **Advanced** sekmesindeki **Araçlar** > **Seçenekleri** aracılığıyla ayarlanır. **R Tools** > **Editor seçenekleri** komutunu kullanarak veya düzenleyicide sağ tıklayarak ve **Biçimlendirme seçeneklerini**seçerek doğrudan bu sayfaya gidebilirsiniz. Ayrıntılar için [editör seçenekleri](#editor-options) bölümüne bakın.

## <a name="inserting-roxygen-comments"></a>Roxygen yorumekleme

RTVS, bir işlevin parametre adlarını kullanarak [Roxygen](https://cran.r-project.org/web/packages/roxygen2/index.html) yorumları oluşturmak için bir kısayol sağlar. İşlev `###` tanımının üzerindeki boş bir satıra yazman için:

![Roxygen yorum ekleme animasyonu](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Editör seçenekleri

Düzenleyiciye özgü **seçenekler, Text** >  **Editor** > **R'ye**yönlendirilerek Araçlar**Seçenekleri** komutu aracılığıyla ayarlanır veya kısayol komutu **R Tools** > **Editor Options'ı**kullanır.

**Genel,** Kaydırma **çubukları**ve **Sekmeler** sekmeleri üzerindeki seçenekler R'ye özgü değildir, ancak tüm diller için genel Visual Studio ayarları dır, ancak dil başına uygulanır. Ayrıntılar için aşağıdaki makalelere bakın:

- [Seçenekler, Metin Düzenleyici, Tüm Diller](../ide/reference/options-text-editor-all-languages.md)
- [Kaydırma çubuğunu özelleştirerek kodizleme](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Seçenekler, Metin Düzenleyicisi, Sekmeler](../ide/reference/options-text-editor-all-languages-tabs.md)

**R** > **Advanced** sekmesindeki seçenekler RTVS'e özgüdir:

| Grup | Seçenek | Varsayılan | Açıklama |
| --- | --- | --- | --- |
| Biçimlendirme | Otomatik biçimlendirme | Açık | Yazdığınız gibi yeniden biçimler kodu. **Belgeyi Biçimle'yi** veya **Biçimlendirme** komutlarını etkilemez. |
| | Genişletilmiş ayraçlar | Kapalı | Yeni bir satıra açık { yerleştirir. |
| | Yapıştır'da biçimlendirme | Açık | Yapıştırma üzerinde biçimlendirme uygular. |
| | Kapsamı } üzerinde biçimlendirme | Açık | Kapanış }yazdıktan sonra kapsamı biçimlendirin. |
| | Virgülden sonra boşluk | Açık | Virgülden sonra boşluk yerleştirir. |
| | Anahtar kelimeden sonra boşluk | Açık | , , `while`ve `repeat` `if`. gibi anahtar kelimelerden sonra boşluk yerleştirir. |
| | { önce boşluk | Açık | Önce bir boşluk yerleştirir ve {. |
| | Etrafındaki boşluklar = | Açık | Boşlukları eşit bir işaretin etrafına yerleştirir. |
| IntelliSense | Enter tuşuna gir'de commit | Kapalı | **Enter** tuşuna basıldığında otomatik tamamlama seçimini yapar. |
| | Boşluk tuşu üzerinde commit | Kapalı | **Boşluk** tuşuna basıldığında otomatik tamamlama seçimini yapar.|
| | İlk karakterdeki tamamlanma listesi | Açık | İlk karakter türlerinde tamamlanma listesini gösterir. Kapalı yken, > **IntelliSense** > List**Members** **(Ctrl**+**J)** ile bir tamamlama listesi **görüntülenir.** |
| | **Sekme** anahtarındaki tamamlanma listesi | Kapalı | Bir veya daha fazla karakter yazarak ve **Sekme'ye**basarak tamamlanma listesini çağırır. |
| | Kısmen türde bağımsız değişken adlarını eşleştir | Kapalı | WHen bir işlev çağrısında argüman adları yazarak, imza yardımı en iyi eşleşme bağımsız değişken için bir açıklama gösterir. |
| Etkileşimli Pencere | R Konsolunda sözdizimi denetimi | Kapalı | Etkileşimli pencerede sözdizimi denetimi uygular. Sözdizimi denetimi çok satırlı deyimlerde doğru çalışmayabilir. |
| Anahat Oluşturma | Kod anahat | Açık | Çok satırlı ifadeler gibi alanlar için otomatik olarak katlanabilir bölgeler oluşturur. |
| Sözdizimi denetimi | Sözdizimi hatalarını göster | Açık | Kodun otomatik sözdizimi denetimini sağlar. |
