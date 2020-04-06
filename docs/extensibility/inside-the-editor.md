---
title: Düzenleyicinin İçinde
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bba0b5192df53b6ec837b0030c7b236bf8e08dea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710323"
---
# <a name="inside-the-editor"></a>Editörün içinde

Düzenleyici, düzenleyici metin modelini metin görünümünden ve kullanıcı arabiriminden ayrı tutmak için tasarlanmış birkaç farklı alt sistemden oluşur.

Bu bölümlerde editör farklı yönlerini açıklar:

- [Alt sistemlere genel bakış](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [Metin modeli](../extensibility/inside-the-editor.md#the-text-model)

- [Metin görünümü](../extensibility/inside-the-editor.md#the-text-view)

Bu bölümlerde editörün özellikleri açıklayınız:

- [Etiketler ve sınıflandırıcılar](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Süsleme -leri](../extensibility/inside-the-editor.md#adornments)

- [Yansıtma](../extensibility/inside-the-editor.md#projection)

- [Anahat Oluşturma](../extensibility/inside-the-editor.md#outlining)

- [Fare bağlamaları](../extensibility/inside-the-editor.md#mouse-bindings)

- [Editör işlemleri](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Alt sistemlere genel bakış

### <a name="text-model-subsystem"></a>Metin modeli alt sistemi

Metin modeli alt sistemi, metni temsil eden ve işlemesini etkinleştiren sorumludur. Metin modeli alt sistemi, düzenleyici tarafından görüntülenecek karakter dizisini açıklayan <xref:Microsoft.VisualStudio.Text.ITextBuffer> arabirimi içerir. Bu metin değiştirilebilir, izlenebilir ve başka bir şekilde değiştirilebilir. Metin modeli de aşağıdaki yönleri için türleri sağlar:

- Metni dosyalarla ilişkilendiren ve bunları dosya sisteminde okuma yı ve yazmayı yöneten bir hizmettir.

- İki nesne dizisi arasındaki en az farkları bulan bir farklılık hizmeti.

- Diğer arabellekteki metnin alt kümeleri açısından arabellekteki metni açıklayan bir sistem.

Metin modeli alt sistemi kullanıcı arabirimi (UI) kavramları içermez. Örneğin, metin biçimlendirme veya metin düzeni nden sorumlu değildir ve metinle ilişkili olabilecek görsel süslemeler hakkında hiçbir bilgisi yoktur.

Metin modeli alt sisteminin genel türleri *Microsoft.VisualStudio.Text.Data.dll* ve *Microsoft.VisualStudio.CoreUtility.dll*, yalnızca .NET Framework taban sınıf kitaplığı ve Yönetilen Genişletilebilirlik Çerçevesi (MEF) bağlıdır bulunur.

### <a name="text-view-subsystem"></a>Metin görünümü alt sistemi

Metin görünümü alt sistemi metni biçimlendirmekten ve görüntülemekten sorumludur. Bu alt sistemdeki türler, türlerin Windows Sunu Temeli'ne (WPF) güvenip dayanmadığına bağlı olarak iki katmana ayrılır. En önemli türleri <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>ve , hangi görüntülenecek metin satırları kümesini kontrol ve aynı zamanda caret, seçim ve WPF UI öğeleri kullanarak metin süslemek için tesisler. Bu alt sistem, metin görüntüleme alanının etrafında kenar boşlukları da sağlar. Bu kenar boşlukları genişletilebilir ve farklı içerik türleri ve görsel efektler içerebilir. Kenar boşluklarına örnek olarak satır numarası görüntüler ve kaydırma çubukları verilebilir.

Metin görünümü alt sisteminin ortak türleri *Microsoft.VisualStudio.Text.UI.dll* ve *Microsoft.VisualStudio.Text.UI.Wpf.dll*bulunur. İlk derleme platformdan bağımsız öğeleri içerir ve ikinci WPF özgül öğeleri içerir.

### <a name="classification-subsystem"></a>Sınıflandırma alt sistemi

Sınıflandırma alt sistemi metin için yazı tipi özelliklerini belirlemekten sorumludur. Bir sınıflandırıcı metni farklı sınıflara ayırır, örneğin, "anahtar kelime" veya "yorum". Sınıflandırma biçimi eşlemi, bu sınıfları gerçek yazı tipi özellikleriyle (örneğin, "Mavi Teselli10 pt" ile ilişkilendirer. Bu bilgiler, metni biçimlendirdiğinde ve işlerken metin görünümü tarafından kullanılır. Bu konunun ilerleyen saatlerinde daha ayrıntılı olarak açıklanan etiketleme, verilerin metin yayılmalarıyla ilişkilendirilmesini sağlar.

Sınıflandırma alt sisteminin genel türleri Microsoft.VisualStudio.Text.Logic.dll'de bulunur ve Microsoft.VisualStudio.Text.UI.Wpf.dll'de bulunan sınıflandırmanın görsel yönleriyle etkileşime girmelidir.

### <a name="operations-subsystem"></a>İşlemler alt sistemi

İşlemler alt sistemi düzenleyici davranışını tanımlar. Visual Studio düzenleyici komutları ve geri alma sistemi için uygulama sağlar.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Metin modeline ve metin görünümüne daha yakından bakmak

### <a name="the-text-model"></a>Metin modeli

Metin modeli alt sistemi, metin türlerinin farklı gruplandırmalarından oluşur. Bunlar metin arabelleği, metin anlık görüntüleri ve metin açıklıklarını içerir.

#### <a name="text-buffers-and-text-snapshots"></a>Metin arabellekleri ve metin anlık görüntüleri

Arabirim, <xref:Microsoft.VisualStudio.Text.ITextBuffer> .NET Framework'deki `String` tür tarafından kullanılan kodlama olan UTF-16 kullanılarak kodlanan Unicode karakter sırasını temsil eder. Metin arabelleği dosya sistemi belgesi olarak kalıcı olabilir, ancak bu gerekli değildir.

Boş <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> bir metin arabelleği veya bir dize den veya <xref:System.IO.TextReader>. Metin arabelleği dosya sistemine '' <xref:Microsoft.VisualStudio.Text.ITextDocument>olarak kalıcı olarak

Herhangi bir iş parçacığı, bir iş parçacığı arayarak <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>metin arabelleği sahipliğini alana kadar metin arabelleği'ni düzenleme yapabilir. Bundan sonra, yalnızca bu iş parçacığı, edinimi gerçekleştirebilir.

Metin arabelleği, kullanım ömrü boyunca birçok sürümden geçebilir. Arabellek her düzenlenilen yeni bir sürüm oluşturulur <xref:Microsoft.VisualStudio.Text.ITextSnapshot> ve değişmez bir arabellek bu sürümün içeriğini temsil eder. Metin anlık görüntüleri değişmez olduğundan, temsil ettiği metin arabelleği değişmeye devam etse bile, herhangi bir iş parçacığıüzerinde kısıtlama olmaksızın bir metin anlık görüntüsüne erişebilirsiniz.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Metin anlık görüntüleri ve metin anlık çizgileri

Metin anlık görüntüsünün içeriğini bir karakter dizisi veya satır dizisi olarak görüntüleyebilirsiniz. Karakterler ve çizgiler indekslenir. Boş bir metin anlık görüntüsü sıfır karakter ve bir boş satır içerir. Bir satır, geçerli unicode satır sonu karakter dizisi yle veya arabelleğenin başı veya sonuyla sınırlandırılır. Satır sonu karakterleri metin anlık görüntüsünde açıkça temsil edilir ve metin anlık görüntüsündeki satır sonları hepsinin aynı olması gerekmez.

> [!NOTE]
> Visual Studio düzenleyicisindeki satır sonu karakterleri hakkında daha fazla bilgi için [Kodlamalar ve satır sonları'na](../ide/encodings-and-line-breaks.md)bakın.

Metin satırı, belirli bir <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> satır numarası için metin anlık görüntüsünden veya belirli bir karakter konumu için elde edilebilen bir nesne tarafından temsil edilir.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints, SnapshotSpans ve Normalize SnapshotSpanCollections

A <xref:Microsoft.VisualStudio.Text.SnapshotPoint> anlık görüntüdeki karakter konumunu temsil eder. Konumun sıfır ile anlık görüntünün uzunluğu arasında olması garanti edilir. A <xref:Microsoft.VisualStudio.Text.SnapshotSpan> anlık görüntüdeki bir metin aralığını temsil eder. Bitiş konumunun sıfır ile anlık görüntünün uzunluğu arasında olması garanti edilir. Aynı <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> anlık görüntüden <xref:Microsoft.VisualStudio.Text.SnapshotSpan> bir nesne kümesi oluşur.

#### <a name="spans-and-normalizedspancollections"></a>Yayılma Süreleri ve Normalize Yayılma Koleksiyonları

A, <xref:Microsoft.VisualStudio.Text.Span> metin anlık görüntüsündeki bir metin aralığına uygulanabilecek bir aralığı temsil eder. Anlık görüntü konumları sıfır tabanlıdır, bu nedenle açıklıklar sıfır da dahil olmak üzere herhangi bir konumda başlayabilir. Bir `End` aralığın özelliği, `Start` mülkiyetinin ve `Length` mülkiyetinin toplamına eşittir. A `Span` `End` özelliği tarafından dizine eklenen karakter içermez. Örneğin, Başlangıç=5 ve Uzunluk=3 olan bir açıklık End=8'e sahiptir ve 5, 6 ve 7 konumlarındaki karakterleri içerir. Bu açıklık için gösterim [5..8).

Bitiş konumu da dahil olmak üzere ortak konumları varsa iki açıklık kesişiyor. Bu nedenle, [3, 5) ve [2, 7) kesişim [3, 5) ve [3, 5) ve [5, 7) kesişim [5, 5) olduğunu. ([5, 5) boş bir açıklık olduğuna dikkat edin.)

Bitiş konumu dışında ortak konumları varsa iki açıklık çakışıyor. Boş bir açıklık hiçbir zaman başka bir açıklıkla örtüşmez ve iki açıklığımın çakışması hiçbir zaman boş olmaz.

A, <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> yayılma açıklıklarının Başlangıç özellikleri sırasına göre bir yayılma listesidir. Listede, çakışan veya bitişik yayılma süreleri birleştirilir. Örneğin, [5..9), [0..1), [3..6) ve [9..10) açıklıklar kümesi göz önüne alındığında, normalleştirilmiş yayılma listesi [0..1), [3..10).

#### <a name="itextedit-textversion-and-text-change-notifications"></a>iTextedit, TextVersion ve metin değişikliği bildirimleri

Metin arabelleği içeriği bir <xref:Microsoft.VisualStudio.Text.ITextEdit> nesne kullanılarak değiştirilebilir. Böyle bir nesne oluşturma `CreateEdit()` (yöntemlerinden <xref:Microsoft.VisualStudio.Text.ITextBuffer>birini kullanarak) metin düzenlemelerinden oluşan bir metin hareketi başlatır. Her düzenleme, arabellekteki bazı metin açıklarının bir dize ile değiştirilmesidir. Her bir edinimin koordinatları ve içeriği, hareket başlatıldığında arabelleğe göre ifade edilir. Nesne, <xref:Microsoft.VisualStudio.Text.ITextEdit> aynı işlemdeki diğer düzenlemelerden etkilenen düzenlemekoordinatlarını ayarlar.

Örneğin, bu dize içeren bir metin arabellek düşünün:

```
abcdefghij
```

İki düzenleme içeren bir işlem uygulayın, bir düzenleme [2..4) de açıklığı değiştirir karakteri `X` kullanarak ve karakteri `Y`kullanarak [6..9) de açıklığı değiştiren ikinci bir düzenleme. Sonuç şu arabellektir:

```
abXefYj
```

İkinci edinimin koordinatları, ilk düzen uygulanmadan önce, işlemin başındaki arabelleğe ilişkin olarak hesaplandı.

<xref:Microsoft.VisualStudio.Text.ITextEdit> Arabellek değişiklikleri nesne yöntemini `Apply()` çağırarak işlenir zaman etkili olur. En az bir boş olmayan edit varsa, yeni <xref:Microsoft.VisualStudio.Text.ITextVersion> bir <xref:Microsoft.VisualStudio.Text.ITextSnapshot> yeni oluşturulur, `Changed` yeni bir yeni oluşturulur ve bir olay yükseltilir. Her metin sürümünde farklı bir metin anlık görüntüsü vardır. Metin anlık görüntüsü, bir edit işleminden sonra metin arabelleği'nin tam durumunu temsil eder, ancak metin sürümü yalnızca bir anlık görüntüden diğerine yapılan değişiklikleri açıklar. Genel olarak, metin anlık görüntüleri bir kez kullanılmak ve sonra atılır, metin sürümleri bir süre canlı kalır iken içindir.

Metin sürümü nde <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>bir . Bu koleksiyon, anlık görüntüye uygulandığında sonraki anlık görüntü üreten değişiklikleri açıklar. Koleksiyondaki her <xref:Microsoft.VisualStudio.Text.ITextChange> değişiklik karakter konumunu, değiştirilen dize ve değiştirme dizesini içerir. Değiştirilen dize temel ekleme için boş ve değiştirme dizesi temel bir silme için boş. Normalleştirilmiş koleksiyon her `null` zaman metin arabelleği en son sürümü içindir.

Metin <xref:Microsoft.VisualStudio.Text.ITextEdit> arabelleği için herhangi bir zamanda yalnızca bir nesne anında kullanılabilir ve tüm metin edinişleri metin arabelleği sahibi olan iş parçacığı üzerinde gerçekleştirilmesi gerekir (sahiplik iddia edildiyse). Metin düzenleme, yöntemini `Cancel` veya yöntemini `Dispose` çağırarak terk edilebilir.

<xref:Microsoft.VisualStudio.Text.ITextBuffer>ayrıca, `Insert()` `Delete()`arabirimde bulunanlara benzeyen , ve `Replace()` yöntemler sağlar. <xref:Microsoft.VisualStudio.Text.ITextEdit> Bunları çağırmak, bir <xref:Microsoft.VisualStudio.Text.ITextEdit> nesne oluşturma, benzer arama yapma ve ardından editi uygulama yla aynı etkiye sahiptir.

#### <a name="tracking-points-and-tracking-spans"></a>İzleme noktaları ve izleme süreleri

Bir <xref:Microsoft.VisualStudio.Text.ITrackingPoint> metin arabelleği bir karakter konumunu temsil eder. Arabellek, karakterin konumunun değişmesine neden olacak şekilde düzenlenirse, izleme noktası da onunla birlikte değişir. Örneğin, bir izleme noktası arabellekteki 10 konumuna başvuruyorsa ve arabelleğin başına beş karakter eklenirse, izleme noktası sonra 15 konumuna başvurur. Bir ekleme tam olarak izleme noktası tarafından belirtilen konumda gerçekleşirse, davranışı <xref:Microsoft.VisualStudio.Text.PointTrackingMode>onun tarafından belirlenir `Positive` `Negative`, ya da olabilir . İzleme modu pozitifse, izleme noktası eklemenin sonunda bulunan aynı karaktere başvurur. İzleme modu negatifse, izleme noktası özgün konumdaki ilk eklenen karaktere başvurur. İzleme noktası tarafından temsil edilen konumdaki karakter silinirse, izleme noktası silinen aralığı izleyen ilk karaktere geçer. Örneğin, bir izleme noktası 5.

An, <xref:Microsoft.VisualStudio.Text.ITrackingSpan> tek bir konum yerine karakter aralığını temsil eder. Davranışı onun <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>tarafından belirlenir. Yayılma izleme modu [SpanTrackingMode.EdgeInclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive)ise, izleme süresi kenarlarına eklenen metni eklemek için büyür. Yayılma izleme modu [SpanTrackingMode.EdgeExclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive)ise, izleme süresi kenarlarına eklenen metni içermez. Ancak, yayılma izleme modu [SpanTrackingMode.EdgePositive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive)ise, ekleme geçerli konumu starta doğru iter ve yayılma izleme modu [SpanTrackingMode.EdgeNegative](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative)ise, ekleme geçerli konumu sona doğru iter.

Ait oldukları metin arabelleği herhangi bir anlık görüntü için bir izleme noktası veya izleme açıklığı konumunu alabilirsiniz. İzleme noktaları ve izleme süreleri herhangi bir iş parçacığından güvenle başvurulabilir.

#### <a name="content-types"></a>İçerik türleri

İçerik türleri, farklı içerik türlerini tanımlamak için bir mekanizmadır. İçerik türü "metin", "kod", "ikili" veya "xml", "vb" veya "c#" gibi bir teknoloji türü gibi bir dosya türü olabilir. Örneğin, "kullanmak" sözcüğü hem C# hem de Visual Basic'te kullanılan bir anahtar kelimedir, ancak diğer programlama dillerinde değildir. Bu nedenle, bu anahtar kelimenin tanımı "c#" ve "vb" içerik türleri ile sınırlı olacaktır.

İçerik türleri, editörün diğer öğeleri ve süslemeleri için bir filtre olarak kullanılır. İçerik türüne göre birçok düzenleyici özelliği ve uzantı noktası tanımlanır. Örneğin, metin boyama düz metin dosyaları, XML dosyaları ve Visual Basic kaynak kodu dosyaları için farklıdır. Metin arabelleklerine genellikle oluşturulduklarında bir içerik türü atanır ve metin arabelleği içerik türü değiştirilebilir.

İçerik türleri diğer içerik türlerinden birden çok devralınabilir. Belirli <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> bir içerik türünün ebeveynleri olarak birden çok temel türü belirtmenizi sağlar.

Geliştiriciler kendi içerik türlerini tanımlayabilir ve <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>bunları kullanarak kaydedebilir. Birçok düzenleyici özelliği, belirli bir içerik türüne <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>göre tanımlanabilir. Örneğin, düzenleyici kenar boşlukları, süslemeler ve fare işleyicileri tanımlanabilir, böylece yalnızca belirli içerik türlerini görüntüleyen düzenleyiciler için geçerlidir.

### <a name="the-text-view"></a>Metin görünümü

Model görünümü denetleyicisinin (MVC) görünüm bölümü metin görünümünü, görünümübiçimlendirmeyi, kaydırma çubuğu gibi grafik öğelerini ve özeni tanımlar. Visual Studio editörünün tüm sunum öğeleri WPF'ye dayanmaktadır.

#### <a name="text-views"></a>Metin görünümleri

Arabirim, <xref:Microsoft.VisualStudio.Text.Editor.ITextView> metin görünümünün platformdan bağımsız bir temsilidir. Öncelikle metin belgelerini bir pencerede görüntülemek için kullanılır, ancak başka amaçlar için de kullanılabilir, örneğin, bir araç ipucu.

Metin görünümü farklı türde metin arabellekleri başvurur. Özellik, <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> bu <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> üç farklı metin arabelleğine işaret eden bir nesneyi ifade eder: en üst veri düzeyi arabelleği olan veri arabelleği, düzenlemenin gerçekleştiği düzenleme arabelleği ve metin görünümünde görüntülenen arabellek olan görsel arabellek.

Metin, temel metin arabelleğine eklenen sınıflandırıcılara göre biçimlendirilir ve metin görünümüne eklenen süs sağlayıcıları kullanılarak süslenir.

#### <a name="the-text-view-coordinate-system"></a>Metin görünümü koordinat sistemi

Metin görünümü koordinat sistemi metin görünümünde konumları belirtir. Bu koordinat sisteminde, x değeri 0.0 görüntülenen metnin sol kenarına, y değeri ise görüntülenen metnin üst kenarına karşılık gelir. X koordinatı soldan sağa, y koordinatı yukarıdan aşağıya doğru artar.

Bir görünüm portu (metin penceresinde görünen metin bölümü) dikey olarak kaydırılırken yatay olarak kaydırılamaz. Bir viewport, çizim yüzeyine göre hareket edebilmek için sol koordinatını değiştirerek yatay olarak kaydırılır. Ancak, bir görünüm portu yalnızca işlenen metni değiştirerek dikey olarak <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> kaydırılabilir ve bu da bir olayın yükseltilmesine neden olur.

Koordinat sistemindeki mesafeler mantıksal piksellere karşılık gelir. Metin oluşturma yüzeyi ölçekleme dönüşümü olmadan görüntülenirse, metin oluşturma koordinat sistemindeki bir birim ekranda bir piksele karşılık gelir.

#### <a name="margins"></a>Kenar boşlukları

Arabirim <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> bir kenar boşluğu temsil eder ve kenar boşluğunun görünürlüğünü n ve boyutunun denetimini sağlar. "Üst", "Sol", "Sağ" ve "Alt" olarak adlandırılan ve görünümün üst, alt, sol veya sağ kenarına iliştirilmiş olan önceden tanımlanmış dört kenar boşluğu vardır. Bu kenar boşlukları, diğer kenar boşluklarının yerleştirilebileceği kapsayıcılardır. Arabirim, kenar boşluğunun boyutunu ve bir kenar boşluğunun görünürlüğünü döndüren yöntemleri tanımlar. Kenar boşlukları, iliştirildikleri metin görünümü hakkında ek bilgi sağlayan görsel öğelerdir. Örneğin, satır sayısı kenar boşluğu metin görünümü için satır numaralarını görüntüler. Glyph kenar boşluğu, UI öğelerini görüntüler.

Arabirim, <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> kenar boşluklarının oluşturulmasını ve yerleşimini işler. Kenar boşlukları diğer kenar boşluklarına göre sıralanabilir. Daha yüksek öncelikli kenar boşlukları metin görünümüne daha yakın bulunur. Örneğin, iki sol kenar boşluğu varsa, a ve kenar boşluğu B ve B marjı A marjından daha düşük bir önceliğe sahipse, B marjı A marjının solunda görünür.

#### <a name="the-text-view-host"></a>Metin görünümü ana bilgisayarı

Arabirim, <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> metin görünümünü ve görünüme eşlik eden bitişik süslemeleri (örneğin, kaydırma çubukları) içerir. Metin görünümü ana bilgisayarı, görünümün kenarlıklarına eklenen kenar boşluklarını da içerir.

#### <a name="formatted-text"></a>Biçimlendirilmiş metin

Metin görünümünde görüntülenen metin nesnelerden <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> oluşur. Her metin görünümü satırı, metin görünümündeki bir metin satırına karşılık gelir. Temel metin arabelleğindeki uzun satırlar kısmen gizlenmiş (sözcük kaydırma etkin değilse) veya birden çok metin görünümü satırına bölünebilir. Arabirim, <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> koordinatlar ve karakterler arasında eşleme ve çizgiyle ilişkili olabilecek süslemeler için yöntemler ve özellikler içerir.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>nesneler bir <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> arayüz kullanılarak oluşturulur. Yalnızca görünümde görüntülenen metinle ilgili endişeleriniz varsa, biçimlendirme kaynağını yoksayabilirsiniz. Görünümde görüntülenmeyen metin biçimiyle ilgileniyorsanız (örneğin, zengin metin kesimi ni ve yapıştırmayı desteklemek <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> için), metni metin arabelleğinde biçimlendirmek için kullanabilirsiniz.

Metin görünümü birer <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> birer biçimlendirin.

## <a name="editor-features"></a>Editör özellikleri

Düzenleyicinin özellikleri, özelliğin tanımının uygulanmasından ayrı olacak şekilde tasarlanmıştır. Editör şu özellikleri içerir:

- Etiketler ve sınıflandırıcılar

- Süsleme -leri

- Yansıtma

- Anahat Oluşturma

- Fare ve anahtar bağlamaları

- Operasyonlar ve ilkel

- IntelliSense

### <a name="tags-and-classifiers"></a>Etiketler ve sınıflandırıcılar

Etiketler, bir metin aralığıyla ilişkili işaretçilerdir. Metin boyama, altı çizili grafikler, grafikler veya açılır pencereler kullanılarak farklı şekillerde sunulabilir. Sınıflandırıcılar bir tür etikettir.

Diğer etiket türleri <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> metin vurgulama, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> anahat oluşturma <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> ve hataları derlemek içindir.

#### <a name="classification-types"></a>Sınıflandırma türleri

Arabirim, <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> soyut bir metin kategorisi olan eşdeğerlik sınıfını temsil eder. Sınıflandırma türleri diğer sınıflandırma türlerinden birden fazla kalıtsal olabilir. Örneğin, programlama dili sınıflandırmaları "anahtar kelime", "yorum" ve "tanımlayıcı" içerebilir ve bunların tümü "kod"dan devralır. Doğal dil sınıflandırma türleri "isim", "fiil" ve "sıfat" içerebilir ve bunların tümü "doğal dil"den miras kalır.

#### <a name="classifications"></a>Sınıflandırmalar

Sınıflandırma, genellikle bir metin aralığı üzerinde belirli bir sınıflandırma türüne örnektir. A <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> bir sınıflandırmayı temsil etmek için kullanılır. Sınıflandırma aralığı, belirli bir metin aralığını kapsayan ve sisteme bu metin aralığının belirli bir sınıflandırma türünde olduğunu söyleyen bir etiket olarak düşünülebilir.

#### <a name="classifiers"></a>Sınıflandırıcı

An, <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> metni bir sınıflandırma kümesine ayıran bir mekanizmadır. Sınıflandırıcılar belirli içerik türleri için tanımlanmalı ve belirli metin arabellekleri için anında hazırlanmalıdır. İstemciler <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> metin sınıflandırmasına katılmak için uygulamalıdır.

#### <a name="classifier-aggregators"></a>Sınıflandırıcı toplayıcıları

Sınıflandırıcı toplayıcı, bir metin arabelleği için tüm sınıflandırıcıları yalnızca bir sınıflandırma kümesinde birleştiren bir mekanizmadır. Örneğin, hem C# sınıflandırıcısı hem de İngilizce dil sınıflandırıcısı, C# dosyasındaki bir yorum üzerinde sınıflandırmalar oluşturabilir. Bu yorumu göz önünde bulundurun:

```
// This method produces a classifier
```

C# sınıflandırıcısı tüm yayılma alanını bir açıklama olarak etiketleyebilir ve İngilizce dil sınıflandırıcısı "üretir"i "fiil" ve "yöntem"i "isim" olarak sınıflandırabilir. Toplayıcı çakışmayan sınıflandırmalar kümesi üretir ve kümenin türü tüm katkıları temel ayarır.

Bir sınıflandırıcı toplayıcı, metni bir sınıflandırma kümesine ayırdığından da sınıflayıcıdır. Sınıflandırıcı toplayıcı, çakışan sınıflandırmalar olmamasını ve sınıflandırmaların sıralanmış olmasını da sağlar. Tek tek sınıflandırıcılar, herhangi bir sırada ve herhangi bir şekilde çakışan herhangi bir sınıflandırma kümesini döndürmekte serbesttir.

#### <a name="classification-formatting-and-text-coloring"></a>Sınıflandırma biçimlendirme ve metin boyama

Metin biçimlendirme, metin sınıflandırması üzerine oluşturulmuş bir özellik örneğidir. Bir uygulamadaki metnin görünümünü belirlemek için metin görünümü katmanı tarafından kullanılır. Metin biçimlendirme alanı WPF'ye bağlıdır, ancak sınıflandırmaların mantıksal tanımı değildir.

Sınıflandırma biçimi, belirli bir sınıflandırma türü için biçimlendirme özellikleri kümesidir. Bu biçimler, sınıflandırma türünün üst biçiminin biçiminden devralır.

An, <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> sınıflandırma türünden metin biçimlendirme özellikleri kümesine kadar olan bir haritadır. Düzenleyicide biçim haritasının uygulanması, sınıflandırma biçimlerinin tüm dışa tüm dışa aktarma işlemlerini işler.

### <a name="adornments"></a>Süsleme -leri

Süslemeler, metin görünümündeki karakterlerin yazı tipi ve rengiyle doğrudan ilişkili olmayan grafik efektlerdir. Örneğin, birçok programlama dilinde derleme olmayan kodu işaretlemek için kullanılan kırmızı dalgalı alt çizgi gömülü bir süslemedir ve araç uçları açılır süslemelerdir. Süslemeler türetilmiştir <xref:System.Windows.UIElement> ve <xref:Microsoft.VisualStudio.Text.Tagging.ITag>uygulamak. Süsleme etiketi iki özel türleri <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, bir görünümde metin olarak aynı alanı işgal süslemeleri <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>için, ve , dalgalı altı çizili için.

Katıştırılmış süslemeler, biçimlendirilmiş metin görünümünün bir parçasını oluşturan grafiklerdir. Farklı Z-sıra katmanlarında düzenlenirler. Metin, caret ve seçim: aşağıdaki gibi üç yerleşik katmanları vardır. Ancak, geliştiriciler daha fazla katman tanımlayabilir ve bunları birbirlerine göre sıraya koyabilir. Üç tür katıştırılmış süslememetin göreli süslemeleri (metin hareket ettiğinde hareket eden ve metin silindiğinde silinir), görünüm göreli süslemelerdir (görünümün metin olmayan bölümleriyle ilgili olan) ve sahip kontrollü süslemelerdir (geliştirici yerleşimlerini yönetmelidir).

Açılır pencereler, metin görünümünün üzerindeki küçük bir pencerede görünen grafiklerdir, örneğin, araç ipuçları.

### <a name="projection"></a><a name="projection"></a>Projeksiyon

Projeksiyon, metni gerçekte depolamayan, ancak bunun yerine diğer metin arabelleklerinden gelen metni birleştiren farklı bir tür metin arabelleği oluşturmak için kullanılan bir tekniktir. Örneğin, bir projeksiyon arabelleği metni diğer iki arabellekten ayırmak ve sonucu yalnızca bir arabellekte yatmaktadır gibi sunmak veya metnin bazı bölümlerini bir arabellekte gizlemek için kullanılabilir. Bir projeksiyon arabelleği başka bir projeksiyon arabelleği için bir kaynak arabellek olarak hareket edebilir. Projeksiyonla ilişkili bir arabellek kümesi, metni çok farklı şekillerde yeniden düzenlemek için oluşturulabilir. (Böyle bir küme *arabellek grafiği*olarak da bilinir.) Visual Studio metin anahat özelliği, daraltılmış metni gizlemek için bir projeksiyon arabelleği kullanılarak uygulanır ve ASP.NET sayfalar için Visual Studio düzenleyicisi Visual Basic ve C# gibi gömülü dilleri desteklemek için projeksiyon kullanır.

Bir <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> kullanılarak <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>oluşturulur. Projeksiyon arabelleği, *kaynak yayılma*alanı <xref:Microsoft.VisualStudio.Text.ITrackingSpan> olarak bilinen nesnelerin sıralı bir dizisi yle temsil edilir. Bu yayılma ların içeriği bir karakter dizisi olarak sunulur. Kaynak yayılma alanının çizildiği metin arabelleklerine *kaynak arabellekleri*adı verilir. Bir projeksiyon arabelleği istemcileri, sıradan bir metin arabelleği farklı olduğunu farkında olmak zorunda değildir.

Projeksiyon arabelleği kaynak arabellekteki metin değiştirme olaylarını dinler. Kaynak açıktaki metin değiştiğinde, projeksiyon arabelleği değiştirilen metin koordinatlarını kendi koordinatlarına göre eşler ve uygun metin değiştirme olaylarını yükseltir. Örneğin, bu içeriği içeren Kaynak arabellekleri A ve B'yi göz önünde bulundurun:

```
A: ABCDE
B: vwxyz
```

Projeksiyon arabelleği P, biri Tüm Arabellek A'ya sahip, diğeri b arabelleği olan iki metin aralığından oluşursa, P aşağıdaki içeriğe sahiptir:

```
P: ABCDEvwxyz
```

Alt dize `xy` b arabelleği nden silinirse, arabellek P, 7 ve 8 pozisyonlarındaki karakterlerin silindiğini gösteren bir olay ortaya çıkarır.

Projeksiyon arabelleği de doğrudan düzenlenebilir. Bu uygun kaynak arabellekleri için ediniciler yayılır. Örneğin, bir dize 6 numaralı konumdaki arabellek P'ye eklenirse ("v" karakterinin orijinal konumu) ekleme, 1 numaralı konumda B arabelleğine yayılır.

Kaynak açıklıklarında, projeksiyon arabelleğine katkıda bulunan kısıtlamalar vardır. Kaynak yayılma ları çakışmayabilir; Projeksiyon arabelleğindeki bir konum, herhangi bir kaynak arabellekte birden fazla konuma eşlenemez ve kaynak arabelleğindeki bir konum, projeksiyon arabelleğinde birden fazla konuma eşlenemez. Kaynak arabellek ilişkisinde herhangi bir döngüye izin verilmez.

Projeksiyon arabelleği için kaynak arabellek kümesi değiştiğinde ve kaynak yayılma kümesi değiştiğinde olaylar yükselir.
Bir elision tampon projeksiyon arabelleği özel bir türüdür. Öncelikle anahat ve metin blokları genişletmek ve daraltma işlemleri için kullanılır. Bir elision arabelleği tek bir kaynak arabelleği temel alınmaktadır ve elision arabelleğindeki yayılma açıklıkları, kaynak arabelleği'nde sıralandığı gibi sıralanmalıdır.

#### <a name="the-buffer-graph"></a>Arabellek grafiği

Arabirim, <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> projeksiyon arabelleklerinin grafiğinde eşleme yapılmasını sağlar. Tüm metin arabellekleri ve projeksiyon arabellekleri, bir dil derleyicisi tarafından üretilen soyut sözdizimi ağacı gibi yönlendirilmiş bir asiklik grafikte toplanır. Grafik, herhangi bir metin arabelleği olabilir üst arabellek tarafından tanımlanır. Arabellek grafiği, üst arabellekteki bir noktadan kaynak arabellekteki bir noktaya veya üst arabellekteki bir açıklıktan kaynak arabelleğindeki bir yayılma kümesine eşlenebilir. Benzer şekilde, bir noktayı veya yayılmayı kaynak arabellekten üst arabellekteki bir noktaya eşleyebilir. Arabellek grafikleri kullanılarak <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>oluşturulur.

#### <a name="events-and-projection-buffers"></a>Olaylar ve projeksiyon arabellekleri

Bir projeksiyon arabelleği değiştirildiğinde, değişiklikler projeksiyon arabelleğinden ona bağlı arabelleklere gönderilir. Tüm arabellek değiştirildikten sonra, en derin arabellekten başlayarak arabellek değişikliği olayları yükseltilir.

### <a name="outlining"></a>Anahat Oluşturma

Anahat oluşturma, metin görünümünde farklı metin bloklarını genişletme veya daraltma yeteneğidir. Anahat, süsler olarak <xref:Microsoft.VisualStudio.Text.Tagging.ITag>tanımlanan aynı şekilde, bir tür olarak tanımlanır. A, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> genişletilebilen veya daraltılmış bir metin bölgesini tanımlayan bir etikettir. Anahat kullanmak <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> için, bir <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>almak için almanız gerekir. Anahat yöneticisi, nesne olarak <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> temsil edilen farklı blokları sıralar, daraltır ve genişletir ve olayları buna göre yükseltir.

### <a name="mouse-bindings"></a>Fare bağlamaları

Fare bağlamaları fare hareketlerini farklı komutlara bağlar. Fare bağlamaları bir <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>kullanılarak tanımlanır ve anahtar bağlamaları <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>bir . Otomatik <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> olarak tüm bağlamaları anında ve görünümdeki fare olaylarına bağlar.

Arabirim, <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> farklı fare olayları için işlem öncesi ve işlem sonrası olay işleyicileri içerir. Olaylardan birini işlemek için, bazı yöntemleri <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>geçersiz kılabilirsiniz.

### <a name="editor-operations"></a>Editör işlemleri

Düzenleyici işlemleri, komut dosyası veya başka amaçlarla düzenleyiciyle etkileşimi otomatikleştirmek için kullanılabilir. Belirli <xref:Microsoft.VisualStudio.Text.Editor.ITextView>bir <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> işlemüzerinde erişim işlemleri için içe aktarabilirsiniz. Daha sonra seçimi değiştirmek, görünümü kaydırmak veya bakımı görünümün farklı bölümlerine taşımak için bu nesneleri kullanabilirsiniz.

### <a name="intellisense"></a>IntelliSense

IntelliSense deyimi tamamlama, imza yardımı (parametre bilgisi olarak da bilinir), Hızlı Bilgi ve ampulleri destekler.

Ekstre tamamlama yöntem adları, XML öğeleri ve diğer kodlama veya biçimlendirme öğeleri için olası tamamlamaların açılır listeleri sağlar. Genel olarak, bir kullanıcı hareketi bir tamamlama oturumu çağırır. Oturum olası tamamlanma listesini görüntüler ve kullanıcı birini seçebilir veya listeyi kapatabilir. Oluşturmak <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> ve tetiklemekten <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>sorumludur. Oturum <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> için tamamlama <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> maddelerinin hesaplaması.

## <a name="see-also"></a>Ayrıca bkz.

- [Dil hizmeti ve editör uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
- [Düzenleyici alma](../extensibility/editor-imports.md)
