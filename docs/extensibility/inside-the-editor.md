---
title: Düzenleyicinin İçinde
description: Düzenleyicinin alt sistemleri ve özellikleri hakkında bilgi edinin. Visual Studio düzenleyicisinin özelliklerini genişletebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4b7fbf671b20cd923e8adc181179ce3d042ed9326f69638eaee3d5e57d7c1ffa
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359799"
---
# <a name="inside-the-editor"></a>Düzenleyicinin içinde

Düzenleyici, düzenleyici metin modelini metin görünümünden ve kullanıcı arabiriminden ayrı tutmak için tasarlanan birkaç farklı alt sistemden oluşur.

Bu bölümler düzenleyicinin farklı yönlerini anlatmaktadır:

- [Alt sistemlere genel bakış](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [Metin modeli](../extensibility/inside-the-editor.md#the-text-model)

- [Metin görünümü](../extensibility/inside-the-editor.md#the-text-view)

Bu bölümler düzenleyicinin özelliklerini anlatmaktadır:

- [Etiketler ve sınıflandırıcılar](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Satırdaki kenarlıkları](../extensibility/inside-the-editor.md#adornments)

- [Projeksiyon](../extensibility/inside-the-editor.md#projection)

- [Anahat Oluşturma](../extensibility/inside-the-editor.md#outlining)

- [Fare bağlamaları](../extensibility/inside-the-editor.md#mouse-bindings)

- [Düzenleyici işlemleri](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Alt sistemlere genel bakış

### <a name="text-model-subsystem"></a>Metin modeli alt sistemi

Metin modeli alt sistemi, metni temsil eden ve işlemesini etkinleştirmeye sorumludur. Metin modeli alt sistemi, <xref:Microsoft.VisualStudio.Text.ITextBuffer> Düzenleyici tarafından gösterilecek karakterlerin dizisini açıklayan arabirimini içerir. Bu metin, birçok şekilde değiştirilebilir, izlenebilir ve başka yollarla yönetilebilir. Metin modeli aşağıdaki durumlar için de türler sağlar:

- Metni dosyalarla ilişkilendiren ve dosya sisteminde okumayı ve yazmayı yöneten bir hizmet.

- İki nesne dizisi arasındaki en az farkları bulan bir fark kayıt hizmeti.

- Bir arabellekteki metni, diğer arabelleklerindeki metnin alt kümeleri bakımından açıklayan bir sistem.

Metin modeli alt sistemi, Kullanıcı arabirimi (UI) kavramlarından muaf değildir. Örneğin, metin biçimlendirme veya metin düzeninden sorumlu değildir ve metinle ilişkili olabilecek görsel donatılarla ilgili bir bilgi içermez.

metin modeli alt sisteminin ortak türleri *Microsoft.VisualStudio.Text.Data.dll* ve *Microsoft.VisualStudio.CoreUtility.dll* bulunur ve yalnızca .NET Framework temel sınıf kitaplığına ve Managed Extensibility Framework (MEF) bağımlıdır.

### <a name="text-view-subsystem"></a>Metin görünümü alt sistemi

Metin görünümü alt sistemi, metin biçimlendirme ve görüntüleme sorumludur. bu alt sistemdeki türler, türlerin Windows Presentation Foundation (WPF) bağımlı olmasına bağlı olarak iki katmana bölünür. En önemli türler, <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> görüntülenecek metin satırları kümesini ve ayrıca giriş işaretini, SEÇIMI ve WPF Kullanıcı arabirimi öğelerini kullanarak metni donatma özelliklerini denetleyen ve ' dir. Bu alt sistem ayrıca metin görüntüleme alanı etrafında kenar boşlukları sağlar. Bu kenar boşlukları genişletilebilir ve farklı türde içerik ve görsel etkiler içerebilir. Kenar boşluklarının örnekleri satır numarası ekranları ve kaydırma çubuklardır.

Metin görünümü alt sisteminin ortak türleri *Microsoft.VisualStudio.Text.UI.dll* ve *Microsoft.VisualStudio.Text.UI.Wpf.dll* içindedir. İlk derleme, platformdan bağımsız öğeleri içerir ve ikincisi WPF 'e özgü öğeleri içerir.

### <a name="classification-subsystem"></a>Sınıflandırma alt sistemi

Sınıflandırma alt sistemi, metnin yazı tipi özelliklerini belirlemekten sorumludur. Sınıflandırıcı, metni farklı sınıflara ayırır, örneğin "anahtar sözcüğü" veya "Açıklama". Sınıflandırma biçim eşlemesi bu sınıfları gerçek yazı tipi özellikleriyle ilişkilendirir (örneğin, "Blue Consolas 10 pt"). Bu bilgiler metin görünümü tarafından metni biçimlendirir ve işler tarafından kullanılır. Bu konunun ilerleyen bölümlerinde daha ayrıntılı olarak açıklanan etiketleme, verilerin yayılmaları ile ilişkilendirilmesine olanak sağlar.

Sınıflandırma alt sisteminin ortak türleri Microsoft.VisualStudio.Text.Logic.dll içindedir ve Microsoft.VisualStudio.Text.UI.Wpf.dll bulunan sınıflandırmanın görsel yönleri ile etkileşime geçebilir.

### <a name="operations-subsystem"></a>İşlemler alt sistemi

İşlemler alt sistemi düzenleyici davranışını tanımlar. Visual Studio düzenleyicisi komutları ve geri alma sistemi için uygulama sağlar.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Metin modeline ve metin görünümüne daha yakından bakış

### <a name="the-text-model"></a>Metin modeli

Metin modeli alt sistemi, farklı metin türü gruplamalardan oluşur. Bunlar metin arabelleğini, metin anlık görüntülerini ve metin yayılmalarını içerir.

#### <a name="text-buffers-and-text-snapshots"></a>Metin arabellekleri ve metin anlık görüntüleri

<xref:Microsoft.VisualStudio.Text.ITextBuffer>Arabirim, .NET Framework türü tarafından kullanılan kodlama olan UTF-16 kullanılarak kodlanmış bir Unicode karakter dizisini temsil eder `String` . Bir metin arabelleği bir dosya sistemi belgesi olarak kalıcı olabilir, ancak bu gerekli değildir.

<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>Boş bir metin arabelleği veya bir dizeden ya da öğesinden başlatılan bir metin arabelleği oluşturmak için kullanılır <xref:System.IO.TextReader> . Metin arabelleği dosya sisteminde olarak kalıcı olabilir <xref:Microsoft.VisualStudio.Text.ITextDocument> .

Herhangi bir iş parçacığı, çağırarak, bir iş parçacığı metin arabelleğinin sahipliğini yapana kadar metin arabelleğini düzenleyebilir <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A> . Bundan sonra yalnızca bu iş parçacığı düzenleme yapabilir.

Bir metin arabelleği, ömrü boyunca pek çok sürümü geçebilir. Arabellek her düzenlendiğinde yeni bir sürüm oluşturulur ve sabit, <xref:Microsoft.VisualStudio.Text.ITextSnapshot> Bu arabellek sürümünün içeriğini temsil eder. Metin anlık görüntüleri sabit olduğu için, gösterdiği metin arabelleği değişmeye devam ediyorsa bile, herhangi bir iş parçacığında bir metin anlık görüntüsüne kısıtlama olmadan erişebilirsiniz.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Metin anlık görüntüleri ve metin anlık görüntü çizgileri

Metin anlık görüntüsünün içeriğini bir karakter dizisi veya satır dizisi olarak görüntüleyebilirsiniz. Hem karakterler hem de satırlar sıfırdan başlayarak dizinlenir. Boş bir metin anlık görüntüsü sıfır karakter ve bir boş satır içerir. Bir çizgi, geçerli bir Unicode satır sonu karakter dizisiyle veya arabelleğin başına ya da sonuna göre sınırlandırılır. Satır sonu karakterleri metin anlık görüntüsünde açıkça temsil edilir ve bir metin anlık görüntüsüne ait satır sonlarının hepsi aynı olmamalıdır.

> [!NOTE]
> Visual Studio düzenleyicisinde satır sonu karakterleri hakkında daha fazla bilgi için bkz. [kodlamalar ve satır sonları](../ide/encodings-and-line-breaks.md).

Bir metin satırı <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> , belirli bir satır numarası veya belirli bir karakter konumu için bir metin anlık görüntüsünden elde edilebilir bir nesne tarafından temsil edilir.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints, Snapshotyayılmalar ve NormalizedSnapshotSpanCollections

Bir <xref:Microsoft.VisualStudio.Text.SnapshotPoint> anlık görüntüdeki karakter konumunu temsil eder. Konum, anlık görüntünün uzunluğu sıfır ile arasında olacak şekilde garanti edilir. Bir <xref:Microsoft.VisualStudio.Text.SnapshotSpan> anlık görüntüdeki metnin bir aralığını temsil eder. Bitiş konumu, anlık görüntünün uzunluğu sıfır ile arasında olacak şekilde garanti edilir. , <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> <xref:Microsoft.VisualStudio.Text.SnapshotSpan> Aynı anlık görüntüdeki bir nesne kümesinden oluşur.

#### <a name="spans-and-normalizedspancollections"></a>Yayılmalar ve NormalizedSpanCollections

Bir <xref:Microsoft.VisualStudio.Text.Span> metin anlık görüntüsünde bir metin aralığına uygulanabilen bir aralığı temsil eder. Anlık görüntü konumları sıfır tabanlıdır, bu nedenle yayılmalar sıfır dahil herhangi bir konumda başlayabilir. `End`Bir yayılımın özelliği, `Start` özelliği ve özelliği toplamına eşittir `Length` . `Span`, Özelliği tarafından dizine eklenen karakteri içermez `End` . Örneğin, Start = 5 ve length = 3 olan bir yayılımın sonu = 8 ve 5, 6 ve 7 konumlarındaki karakterleri içerir. Bu yayılımın gösterimi [5.. 8).

Son konum da dahil olmak üzere ortak konumlarda varsa iki yayılma kesişirler. Bu nedenle, [3, 5) ve [2, 7) kesişimi [3, 5) ve [5, 7) kesişimi [5, 5). ([5, 5) ' in boş bir yayılma olduğunu unutmayın.)

İkinci yayılma, son konum haricinde ortak konumlarda yer alıyorsa çakışırlar. Boş bir yayılım hiçbir şekilde başka bir yayılma ile çakışamaz ve iki yayılma alanının çakışması hiçbir şekilde boş değildir.

, <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> Yayılmalar 'ın başlangıç özelliklerinin sırasıyla yer aldığı yayılmalar listesidir. Listede, çakışan veya bitişik yayılma birleştirilir. Örneğin, [5.. 9), [0.. 1), [3.. 6) ve [9.. 10) yayılma kümesi verildiğinde, Normalleştirilmemiş liste [0.. 1), [3.. 10).

#### <a name="itextedit-textversion-and-text-change-notifications"></a>Ixtedıt, TextVersion ve metin değişikliği bildirimleri

Bir metin arabelleğinin içeriği bir nesnesi kullanılarak değiştirilebilir <xref:Microsoft.VisualStudio.Text.ITextEdit> . Böyle bir nesne oluşturmak (yöntemlerinden birini kullanarak `CreateEdit()` <xref:Microsoft.VisualStudio.Text.ITextBuffer> ) metin düzenlemelerinden oluşan bir metin işlemi başlatır. Her düzenleme, arabellekteki bazı metin yayılımının bir dizeye göre yerini alır. Her düzenlemenin koordinatları ve içeriği, işlem başlatıldığında arabelleğin anlık görüntüsüne göre ifade edilir. <xref:Microsoft.VisualStudio.Text.ITextEdit>Nesnesi, aynı işlem içindeki diğer düzenlemelerle etkilenen düzenlemelerin koordinatlarını ayarlar.

Örneğin, bu dizeyi içeren bir metin arabelleğini göz önünde bulundurun:

```
abcdefghij
```

İki düzenleme içeren bir işlem uygulayın; karakteri kullanarak [2.. 4), karakteri `X` ve [6.. 9) ' de yer alan yayılımın yerini alan ikinci bir düzenleme `Y` . Bu arabellekte sonuç elde edilir:

```
abXefYj
```

İkinci düzenlemenin koordinatları, ilk düzenleme uygulanmadan önce, işlem başındaki arabellek içeriğine göre hesaplandı.

Arabelleğe yapılan değişiklikler, nesnesi yöntemi <xref:Microsoft.VisualStudio.Text.ITextEdit> çağrılarak işlendiklerine göre `Apply()` etkili olur. En az bir boş olmayan düzenleme varsa, yeni <xref:Microsoft.VisualStudio.Text.ITextVersion> bir oluşturulur, yeni <xref:Microsoft.VisualStudio.Text.ITextSnapshot> bir oluşturulur ve bir olay `Changed` oluşturulur. Her metin sürümü farklı bir metin anlık görüntüsüne sahip. Metin anlık görüntüsü, düzenleme işlemi sonrasında metin arabelleğinin tam durumunu temsil eder, ancak metin sürümü yalnızca bir anlık görüntüden bir sonrakine yapılan değişiklikleri açıklar. Genel olarak, metin anlık görüntülerinin bir kez kullanılmaya ve sonra atılırken, metin sürümlerinin bir süre canlı kalması gerekir.

Metin sürümü bir <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection> içerir. Bu koleksiyon, anlık görüntüye uygulandığında sonraki anlık görüntüyü üreten değişiklikleri açıklar. Koleksiyonda her değişiklik karakter konumunu, değiştirilen <xref:Microsoft.VisualStudio.Text.ITextChange> dizeyi ve değiştirme dizesini içerir. Değiştirilen dize, temel ekleme için boştur ve değiştirme dizesi de temel silme işlemi için boştur. Normalleştirilmiş koleksiyon her zaman `null` metin arabelleğinin en son sürümüne göredir.

Herhangi bir zamanda bir metin arabelleği için yalnızca bir nesne örneği gerçekleştirilir ve metin arabelleğinin sahibi olan iş parçacığında tüm metin düzenlemeleri yapılmalıdır (sahiplik talep <xref:Microsoft.VisualStudio.Text.ITextEdit> edildi ise). Metin düzenlemesi, yöntemi veya yöntemi `Cancel` çağrılarak terk `Dispose` edilir.

<xref:Microsoft.VisualStudio.Text.ITextBuffer> ayrıca, `Insert()` `Delete()` `Replace()` arabirimde bulunanlara benzer , ve yöntemleri <xref:Microsoft.VisualStudio.Text.ITextEdit> sağlar. Bunları çağırma, nesne oluşturma, benzer çağrı yapma ve <xref:Microsoft.VisualStudio.Text.ITextEdit> sonra düzenlemeyi uygulama ile aynı etkiye sahiptir.

#### <a name="tracking-points-and-tracking-spans"></a>İzleme noktaları ve izleme aralıkları

, <xref:Microsoft.VisualStudio.Text.ITrackingPoint> metin arabelleğinde bir karakter konumunu temsil eder. Arabellek, karakterin konumunun kaymasını neden olacak şekilde düzenlenmişse, izleme noktası da bu karakterle birlikte kaydırıldı. Örneğin, bir izleme noktası bir arabellekte 10 konumunu ifade eder ve arabelleğin başına beş karakter eklenirse, izleme noktası 15 konumunu ifade eder. Ekleme izleme noktası tarafından tam olarak ifade edilen konumda gerçekleşirse, davranışı veya olabilir , tarafından <xref:Microsoft.VisualStudio.Text.PointTrackingMode> `Positive` `Negative` belirlenir. İzleme modu pozitifse, izleme noktası eklemenin sonunda olan aynı karaktere başvurur. İzleme modu negatifse, izleme noktası özgün konumdaki ilk eklenen karaktere başvurur. İzleme noktası tarafından temsil edilen konumdaki karakter silinirse, izleme noktası silinen aralığı izleyen ilk karaktere kaydırr. Örneğin, bir izleme noktası 5 konumundaki karaktere başvurursa ve 3 ile 6 arasında konumlarda yer alan karakterler silinirse, izleme noktası 3 konumundaki karaktere başvurur.

, <xref:Microsoft.VisualStudio.Text.ITrackingSpan> yalnızca bir konum yerine bir karakter aralığını temsil eder. Davranışı, tarafından <xref:Microsoft.VisualStudio.Text.SpanTrackingMode> belirlenir. Yayma izleme modu [SpanTrackingMode.EdgeInclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive)ise izleme aralığı, kenarlarına eklenen metinleri birleştirmek için büyür. Yayma izleme modu [SpanTrackingMode.EdgeExclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive)ise, izleme aralığı kenarlarına eklenen metinleri eklemez. Ancak, span izleme modu [SpanTrackingMode.EdgePositive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive)ise, ekleme geçerli konumu başlanıcıya iter ve span izleme modu [SpanTrackingMode.EdgeNegative](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative)ise ekleme geçerli konumu sona doğru iletir.

Ait olduğu metin arabelleğinin herhangi bir anlık görüntüsü için bir izleme noktasının konumunu veya izleme aralığına ait olan aralığı eldeebilirsiniz. İzleme noktalarına ve izleme aralıklara herhangi bir iş parçacığından güvenli bir şekilde başvurul olabilir.

#### <a name="content-types"></a>İçerik türleri

İçerik türleri, farklı içerik türlerini tanımlamak için bir mekanizmadır. İçerik türü "text", "code" veya "binary" gibi bir dosya türü ya da "xml", "vb" veya "c#" gibi bir teknoloji türü olabilir. Örneğin, "using" sözcüğü hem C# hem de Visual Basic anahtar sözcük olur, ancak diğer programlama dillerinde değildir. Bu nedenle, bu anahtar sözcüğün tanımı "c#" ve "vb" içerik türleriyle sınırlı olacaktır.

İçerik türleri, düzenleyicinin diğer öğeleri ve donatma için bir filtre olarak kullanılır. Birçok düzenleyici özelliği ve uzantı noktası içerik türüne göre tanımlanır. Örneğin, metin renklendirme düz metin dosyaları, XML dosyaları ve kaynak kod Visual Basic için farklıdır. Metin arabellekleri oluşturulduğunda genellikle bir içerik türü atanır ve metin arabelleğinin içerik türü değiştirilebilir.

İçerik türleri diğer içerik türlerinden birden çok devralabilir. , <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> belirli bir içerik türünün alt verileri olarak birden çok temel tür belirtmenize olanak sağlar.

Geliştiriciler kendi içerik türlerini tanımlayabilir ve kullanarak bunları <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> kaydedebilirsiniz. Birçok düzenleyici özelliği, kullanılarak belirli bir içerik türüne göre <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> tanımlanabilir. Örneğin, düzenleyici kenar boşlukları, donatma ve fare işleyicileri yalnızca belirli içerik türlerini görüntüleyen düzenleyiciler için geçerli olacak şekilde tanımlanabilir.

### <a name="the-text-view"></a>Metin görünümü

Model görünümü denetleyicisi (MVC) deseninin görünüm bölümü metin görünümünü, görünümün biçimlendirmesini, kaydırma çubuğu gibi grafik öğelerini ve caret'i tanımlar. Bu düzenleyicinin tüm Visual Studio WPF'ye dayalıdır.

#### <a name="text-views"></a>Metin görünümleri

Arabirim, <xref:Microsoft.VisualStudio.Text.Editor.ITextView> metin görünümünün platformdan bağımsız bir gösterimidir. Öncelikle metin belgelerini bir pencerede görüntülemek için kullanılır, ancak bir araç ipucu gibi başka amaçlarla da kullanılabilir.

Metin görünümü, farklı türlerde metin arabelleklerine başvurur. özelliği, şu üç farklı metin arabelleğine sahip bir nesneye başvurur: veri arabelleği, en üst veri düzeyi arabelleği, düzenlemenin oluştuğu düzenleme arabelleği ve metin görünümünde görüntülenen arabellek olan görsel <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> arabellek.

Metin, temel alınan metin arabelleğine eklenen sınıflandırıcılara göre biçimlendirildi ve metin görünümüne eklenen donatma sağlayıcıları kullanılarak donatıldı.

#### <a name="the-text-view-coordinate-system"></a>Metin görünümü koordinat sistemi

Metin görünümü koordinat sistemi, metin görünümündeki konumlarını belirtir. Bu koordinat sisteminde, 0,0 x değeri görüntülenen metnin sol kenarına karşılık, y değeri 0,0 ise görüntülenen metnin üst kenarına karşılık gelen değerdir. x koordinatı soldan sağa, y koordinatı ise üstten aşağıya doğru artar.

Görünüm penceresi (metin penceresinde görünen metnin parçası) dikey olarak kaydırıldıklarında olduğu gibi yatay olarak kaydıramaz. Görünüm çubuğu, çizim yüzeyine göre hareket edecek şekilde sol koordinatı değiştirerek yatay olarak kaydırıldı. Ancak, bir görünüm kutusu yalnızca işlenmiş metin değiştirerek dikey olarak kaydırılabilir ve bu da bir olayın ortaya <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> çıkarılana neden olur.

Koordinat sistemi uzaklıkları mantıksal piksellere karşılık geliyor. Metin işleme yüzeyi ölçeklendirme dönüşümü olmadan görüntülenirse, metin işleme koordinat sistemi içinde bir birim, ekranda bir piksele karşılık geliyor olur.

#### <a name="margins"></a>Kenar boşlukları

Arabirim <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> bir dış boşluğu temsil eder ve kenar boşluğu ile boyutunun görünürlüğünün denetimine olanak sağlar. "Üst", "Sol", "Sağ" ve "Alt" olarak adlandırılmış ve bir görünümün üst, alt, sol veya sağ kenarına eklenmiş dört önceden tanımlanmış kenar boşluğu vardır. Bu dış boşluklar, diğer dış boşlukların yerleştiril olduğu kapsayıcılardır. arabirimi, dış boşluğun boyutunu ve bir dış boşluğun görünürlüğünü sağlayan yöntemleri tanımlar. Kenar boşlukları, ekli olduğu metin görünümü hakkında ek bilgi sağlayan görsel öğelerdir. Örneğin, satır-sayı kenar boşluğu metin görünümü için satır numaralarını görüntüler. Glyph kenar boşluğunda kullanıcı arabirimi öğeleri görüntülenir.

Arabirim, <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> kenar boşluklarının oluşturulmasını ve yerleştirilmesini sağlar. Kenar boşlukları diğer kenar boşluklarına göre sıra edilebilir. Daha yüksek öncelikli kenar boşlukları metin görünümüne daha yakın bulunur. Örneğin, A kenar boşluğu ve B kenar boşluğu olmak için iki sol kenar boşluğu varsa ve B kenar boşluğu A kenar boşluğundan daha düşük önceliğe sahipse, A kenar boşluğunda sol kenar boşluğu B görünür.

#### <a name="the-text-view-host"></a>Metin görünümü ana bilgisayarı

Arabirim, metin görünümünü ve görünüme eşlik eden kaydırma çubuklarını <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> içerir. Metin görünümü ana bilgisayarı, görünümün bir kenarlığına eklenmiş kenar boşluklarını da içerir.

#### <a name="formatted-text"></a>Biçimlendirilmiş metin

Metin görünümünde görüntülenen metin nesnelerden <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> oluşur. Her metin görünümü satırı, metin görünümündeki bir metin satırına karşılık gelen bir satırdır. Temel alınan metin arabelleğinde uzun satırlar kısmen belirsiz olabilir (sözcük kaydırma etkinleştirilmediyse) veya birden çok metin görünümü satırına ayrılarak. Arabirimi, koordinatlar ve karakterler arasında eşleme için yöntemler ve özellikler ve satırla ilişkilendirilen <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> donatma için içerir.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> nesneleri bir arabirim kullanılarak <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> oluşturulur. Yalnızca görünümde görüntülenen metinle ilgili endişeleriz varsa biçimlendirme kaynağını yoksayabilirsiniz. Görünümde görüntülenmeen metnin biçimiyle ilgileniyorsanız (örneğin, zengin metin kesme ve yapıştırmayı desteklemek için), metin arabelleğinde metin biçimlendirmek için <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> kullanabilirsiniz.

Metin görünümü tek tek <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> biçimlendirmeler.

## <a name="editor-features"></a>Düzenleyici özellikleri

Düzenleyicinin özellikleri, özelliğin tanımının uygulamasından ayrı olacak şekilde tasarlanmıştır. Düzenleyici şu özellikleri içerir:

- Etiketler ve sınıflandırıcılar

- Süsleme -leri

- Projeksiyon

- Anahat Oluşturma

- Fare ve tuş bağlamaları

- İşlemler ve temel öğeler

- IntelliSense

### <a name="tags-and-classifiers"></a>Etiketler ve sınıflandırıcılar

Etiketler, bir metin aralığıyla ilişkili işaretçilerdir. Bunlar, örneğin metin renklendirme, alt çizgiler, grafikler veya açılır pencere kullanılarak farklı şekillerde sunabilirsiniz. Sınıflandırıcılar bir tür etikettir.

Diğer etiket türleri metin <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> vurgulama, açıklama <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ve derleme hataları <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> için kullanılır.

#### <a name="classification-types"></a>Sınıflandırma türleri

Arabirim, <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> soyut metin kategorisi olan bir denklik sınıfını temsil eder. Sınıflandırma türleri diğer sınıflandırma türlerinden birden çok devralabilir. Örneğin, programlama dili sınıflandırmaları "anahtar sözcük", "açıklama" ve "tanımlayıcı" içerebilir ve bunların hepsi "koddan" devralabilir. Doğal dil sınıflandırma türleri "ad", "fiil" ve "sıfat" içerebilir ve bunların hepsi "doğal dilden" devralınabilir.

#### <a name="classifications"></a>Sınıflandırmalar

Sınıflandırma, genellikle bir metin aralığı üzerinden belirli bir sınıflandırma türünün örneğidir. Bir <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> sınıflandırmayı temsil etmek için kullanılır. Sınıflandırma aralığı, belirli bir metin aralığı kapsayan ve sisteme bu metin aralığına belirli bir sınıflandırma türü olduğunu söyleyen bir etiket olarak düşünebilirsiniz.

#### <a name="classifiers"></a>Sınıflandırıcı

, <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> metni bir sınıflandırma kümesine dönüştüren bir mekanizmadır. Sınıflandırıcılar belirli içerik türleri için tanımlanmalıdır ve belirli metin arabellekleri için örneklenmiş olmalıdır. İstemcilerin metin <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> sınıflandırmaya katılmak için uygulaması gerekir.

#### <a name="classifier-aggregators"></a>Sınıflandırıcı toplamaları

Sınıflandırıcı toplayıcısı, bir metin arabelleği için tüm sınıflandırıcıları tek bir sınıflandırma kümesi içinde birleştiren bir mekanizmadır. Örneğin, hem C# sınıflandırıcısı hem de İngilizce dil sınıflandırıcısı, C# dosyasındaki bir açıklama üzerinde sınıflandırmalar oluşturabilir. Şu açıklamayı göz önünde bulundurarak:

```
// This method produces a classifier
```

C# sınıflandırıcısı, aralığın tamamını açıklama olarak etiketleyebildi ve İngilizce dil sınıflandırıcısı "üretir"i "fiil" ve "yöntem" olarak "isim" olarak sınıflandır olabilir. Toplayıcı, çakışmayan bir sınıflandırma kümesi üretir ve kümenin türü tüm katkıları temel almaktadır.

Sınıflandırıcı toplayıcısı aynı zamanda bir sınıflandırıcıdır çünkü metni bir sınıflandırma kümesine parçalar. Sınıflandırıcı toplayıcısı, çakışan sınıflandırmalar olmadığını ve sınıflandırmaların sıralanmış olduğunu da sağlar. Tek tek sınıflandırıcılar herhangi bir sınıflandırma kümesi, herhangi bir sırayla ve herhangi bir şekilde örtüşürken ücretsizdir.

#### <a name="classification-formatting-and-text-coloring"></a>Sınıflandırma biçimlendirmesi ve metin renklendirme

Metin biçimlendirme, metin sınıflandırması üzerine kurulu bir özelliğin örneğidir. Metin görünümü katmanı tarafından bir uygulamada metnin görünümünü belirlemek için kullanılır. Metin biçimlendirme alanı WPF'ye bağlıdır, ancak sınıflandırmaların mantıksal tanımına bağlı değildir.

Sınıflandırma biçimi, belirli bir sınıflandırma türü için biçimlendirme özellikleri kümesidir. Bu biçimler sınıflandırma türünün üst öğesinden devralır.

<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>, sınıflandırma türünden metin biçimlendirme özellikleri kümesine bir eşlemedir. Düzenleyicide biçim haritasının uygulanması, sınıflandırma biçimlerinin tüm dışarı aktarmalarını işlemektedir.

### <a name="adornments"></a>Süsleme -leri

Donatma, metin görünümündeki karakterlerin yazı tipi ve rengiyle doğrudan ilgili olan grafik etkileridir. Örneğin, birçok programlama dilinde kod derlemeyenleri işaretlemek için kullanılan kırmızı iki durumlu çizgi ekli bir donatmadır ve araç ipucu açılır donatmadır. Donatma türetilen <xref:System.Windows.UIElement> ve <xref:Microsoft.VisualStudio.Text.Tagging.ITag> uygulanır. İki özel donatma etiketi türü, görünümde metinle aynı alanı kaplayacak olan donatma için ve alt çizgiye göre , <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> vardır.

Ekli donatma, biçimlendirilmiş metin görünümünün bir parçası olan grafiklerdir. Farklı Z düzeni katmanlarında düzenlenmiştir. Aşağıdaki gibi üç yerleşik katman vardır: metin, caret ve seçim. Ancak geliştiriciler daha fazla katman tanımlayarak bunları bir diğerine göre sıralayarak tanımlayabilir. Üç ekli donatma türü, metin göreli donatma (metin hareket ettiğinde hareket eder ve metin silindiğinde silinir), görünüm göreli donatmaları (görünümün metin olmayan bölümleriyle ilgili olması gerekir) ve sahip denetimli donatmalardır (geliştiricinin yerleştirmesini yönetmesi gerekir).

Açılır pencere donatma, metin görünümünün üzerindeki küçük bir pencerede görünen grafiklerdir, örneğin araç ipucu.

### <a name="projection"></a><a name="projection"></a> Projeksiyon

Projeksiyon, aslında metin depolamadan diğer metin arabelleklerinden metinleri birleştiren farklı bir tür metin arabelleği oluşturmak için kullanılan bir tekniktir. Örneğin, bir projeksiyon arabelleği diğer iki arabellekten metni biriktir ve sonucu yalnızca bir arabellekte gibi sunmak veya metnin bir arabellekte bölümlerini gizlemek için kullanılabilir. Projeksiyon arabelleği, başka bir projeksiyon arabelleği için kaynak arabellek görevi görür. Projeksiyonla ilgili bir dizi arabellek, metni birçok farklı şekilde yeniden düzenlemek için oluşturulmuş olabilir. (Bu tür bir küme, arabellek grafı *olarak da bilinir.)* Visual Studio metin açıklama özelliği daraltılmış metni gizlemek için bir projeksiyon arabelleği kullanılarak uygulanır ve ASP.NET sayfaları için Visual Studio düzenleyicisi, Visual Basic ve C# gibi ekli dilleri desteklemek için projeksiyon kullanır.

kullanılarak <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService> oluşturulur. Projeksiyon arabelleği, kaynak yayma olarak bilinen <xref:Microsoft.VisualStudio.Text.ITrackingSpan> sıralı bir nesne *dizisiyle temsil eder.* Bu aralıkların içeriği bir karakter dizisi olarak sunulmuştur. Kaynak aralıklarının çekilecek metin arabellekleri kaynak *arabellekleri olarak adlandırılmıştır.* Projeksiyon arabelleğinin istemcileri bunun sıradan bir metin arabelleğinden farklı olduğunu fark etmek zorunda değildir.

Projeksiyon arabelleği, kaynak arabelleklerde metin değiştirme olaylarını dinler. Bir kaynak yayma süresinde metin değişse projeksiyon arabelleği, değiştirilen metin koordinatlarını kendi koordinatlarıyla eşler ve uygun metin değişikliği olaylarını ortaya kaldırır. Örneğin, şu içeriklere sahip A ve B kaynak arabelleklerini göz önünde bulundurabilirsiniz:

```
A: ABCDE
B: vwxyz
```

Projeksiyon arabelleği P, biri A arabelleğinin tamama ve diğeri de tüm arabelleğe sahip olan iki metinden oluşuyorsa P aşağıdaki içeriğe sahip olur:

```
P: ABCDEvwxyz
```

Alt dize B arabellekten silinirse, arabellek P 7 ve 8 konumlarında karakterlerin silindi olduğunu belirten `xy` bir olay gösterir.

Projeksiyon arabelleği doğrudan da düzenlenebilir. Düzenlemeleri uygun kaynak arabelleklere yalıtır. Örneğin, 6 konumundaki P arabelleğine bir dize eklenirse ("v" karakterinin özgün konumu), ekleme işlemi 1 konumundaki B arabelleğine yalıtır.

Kaynak aralıklarda projeksiyon arabelleğine katkıda bulunan kısıtlamalar vardır. Kaynak aralıklar çakışmaz; Projeksiyon arabelleğinde bir konum, herhangi bir kaynak arabellekte birden fazla konuma eş olamaz ve kaynak arabellekte bir konum projeksiyon arabelleğinde birden fazla konuma eş olamaz. Kaynak arabellek ilişkisinde döngüselliklere izin verilmez.

Olaylar, projeksiyon arabelleği için kaynak arabellek kümesi değişirken ve kaynak kümesi değişikliklere yayma zamanlarında ortaya çıkar.
Elision arabelleği, özel bir projeksiyon arabelleği t'dır. Öncelikle ana satıra yönelik ve metin bloklarını genişleten ve daraltan işlemler için kullanılır. Bir elision arabelleği yalnızca bir kaynak arabelleğine dayalıdır ve elision arabelleğinde yer alan aralıklar, kaynak arabellekte sıra edilenle aynı şekilde sıralamalıdır.

#### <a name="the-buffer-graph"></a>Arabellek grafiği

Arabirimi, <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> projeksiyon arabelleklerinin grafı üzerinde eşlemeyi sağlar. Tüm metin arabellekleri ve projeksiyon arabellekleri, bir dil derleyicisi tarafından üretilen soyut söz dizimi ağacına benzer şekilde, yönlendiren bir zamansız grafikte toplanır. Grafik, herhangi bir metin arabelleği olan üst arabellek tarafından tanımlanır. Arabellek grafiği, en üst arabellekte yer alan bir noktadan kaynak arabellekte bir noktaya veya üst arabellekte yer alan bir aralıktan kaynak arabellekte bir dizi yayılma kümesine eş olabilir. Benzer şekilde, bir nokta eşler veya bir kaynak arabelleğinden üst arabellekte bir noktaya yayma. Arabellek grafikleri kullanılarak <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService> oluşturulur.

#### <a name="events-and-projection-buffers"></a>Olaylar ve projeksiyon arabellekleri

Bir projeksiyon arabelleği değiştirildiğinde, değişiklikler yansıtma arabelleğinden buna bağımlı arabelleklere gönderilir. Tüm arabellekler değiştirildikten sonra, en derin arabellekle başlayarak arabellek değişikliği olayları ortaya çıkar.

### <a name="outlining"></a>Anahat Oluşturma

Açıklama, metin görünümündeki farklı metin bloklarını genişletme veya daraltma özelliğidir. Outlining, donatma tanımlandığı <xref:Microsoft.VisualStudio.Text.Tagging.ITag> şekilde bir tür olarak tanımlanır. , <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> genişletilebilir veya daraltılmış bir metin bölgesi tanımlayan bir etikettir. Bir almak için, outlining kullanmak için <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> içeri aktarma <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> gerekir. İlke yöneticisi nesne olarak temsil edilen farklı blokları numaralandırarak daraltıyor ve genişleterek olayları buna <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> göre oluşturur.

### <a name="mouse-bindings"></a>Fare bağlamaları

Fare bağlamaları, fare hareketlerini farklı komutlara bağlar. Fare bağlamaları bir kullanılarak tanımlanır <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> ve anahtar bağlamaları bir kullanılarak <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider> tanımlanır. , <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> tüm bağlamaların otomatik olarak örneğini sağlar ve bunları görünümde fare olaylarına bağlar.

Arabirimi, <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> farklı fare olayları için ön işlem ve işlem sonrası olay işleyicileri içerir. Olaylardan birini işlemek için, 'de bazı yöntemleri geçersiz <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> kılebilirsiniz.

### <a name="editor-operations"></a>Düzenleyici işlemleri

Düzenleyici işlemleri, betik veya başka amaçlarla düzenleyiciyle etkileşimi otomatikleştirmek için kullanılabilir. Verilen bir üzerinde <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> erişim işlemlerine erişmek için 'i içeri aktarın. <xref:Microsoft.VisualStudio.Text.Editor.ITextView> Daha sonra seçimi değiştirmek, görünümü kaydırmak veya caret'i görünümün farklı bölümlerine taşımak için bu nesneleri kullanabilirsiniz.

### <a name="intellisense"></a>IntelliSense

IntelliSense deyim tamamlama, imza yardımı (parametre bilgisi olarak da bilinir), Hızlı Bilgi ve ampulleri destekler.

Deyim tamamlama yöntem adları, XML öğeleri ve diğer kodlama veya işaretleme öğeleri için olası tamamlamaların açılır listelerini sağlar. Genel olarak, bir kullanıcı hareketi bir tamamlama oturumu çağırır. Oturum olası tamamlamaların listesini görüntüler ve kullanıcı bir tane seçerek listeyi sildi. , Öğesini <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> oluşturmaktan ve tetiklemeden sorumludur <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession> . , <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> Oturum için tamamlanma öğelerinin sayısını hesaplar.

## <a name="see-also"></a>Ayrıca bkz.

- [Dil hizmeti ve Düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
- [Düzenleyici içeri aktarmaları](../extensibility/editor-imports.md)
