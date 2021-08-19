---
title: Düzenleyicinin İçinde
description: Düzenleyicinin alt sistemleri ve özellikleri hakkında bilgi edinmek. Yeni düzenleyicinin özelliklerini Visual Studio.
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
ms.openlocfilehash: bc258f8662d6ad44cb3e222ed130a79cfa7ce912
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159327"
---
# <a name="inside-the-editor"></a>Düzenleyicinin içinde

Düzenleyici, düzenleyici metin modelini metin görünümünden ve kullanıcı arabiriminden ayrı tutmak için tasarlanmış birkaç farklı alt sistemden oluşur.

Bu bölümlerde düzenleyicinin farklı yönleri açıklanmaktadır:

- [Alt sistemlere genel bakış](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [Metin modeli](../extensibility/inside-the-editor.md#the-text-model)

- [Metin görünümü](../extensibility/inside-the-editor.md#the-text-view)

Bu bölümlerde düzenleyicinin özellikleri açıklanmaktadır:

- [Etiketler ve sınıflandırıcılar](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Süsleme -leri](../extensibility/inside-the-editor.md#adornments)

- [Projeksiyon](../extensibility/inside-the-editor.md#projection)

- [Anahat Oluşturma](../extensibility/inside-the-editor.md#outlining)

- [Fare bağlamaları](../extensibility/inside-the-editor.md#mouse-bindings)

- [Düzenleyici işlemleri](../extensibility/inside-the-editor.md#editor-operations)

- [ıntellisense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Alt sistemlere genel bakış

### <a name="text-model-subsystem"></a>Metin modeli alt sistemi

Metin modeli alt sistemi, metni temsil eden ve işlemesini etkinleştirmekle sorumludur. Metin modeli alt <xref:Microsoft.VisualStudio.Text.ITextBuffer> sistemi, düzenleyici tarafından görüntülenecek karakter dizisini açıklayan arabirimini içerir. Bu metin birçok şekilde değiştirilebilir, izlenebilir ve başka şekilde değiştirilebilir. Metin modeli ayrıca aşağıdaki yönler için türler sağlar:

- Metinleri dosyalarla ilişkilendiren ve dosya sisteminde okuma ve yazmayı yöneten bir hizmet.

- İki nesne dizisi arasındaki en küçük farkları bulan fark hizmeti.

- Bir arabellekte metni diğer arabelleklerde metnin alt kümeleri açısından açıklamaya uygun bir sistem.

Metin modeli alt sistemi, kullanıcı arabirimi (UI) kavramlarına sahip değildir. Örneğin, metin biçimlendirmesi veya metin düzeninden sorumlu değildir ve metinle ilişkilendirilmiş görsel donatma bilgisi yoktur.

Metin modeli alt sisteminin ortak türleri *Microsoft.VisualStudio.Text.Data.dll* ve *Microsoft.VisualStudio.CoreUtility.dll* içinde yer alır. Bu, yalnızca .NET Framework temel sınıf kitaplığına ve Managed Extensibility Framework (MEF) bağımlıdır.

### <a name="text-view-subsystem"></a>Metin görünümü alt sistemi

Metin görünümü alt sistemi, metin biçimlendirme ve görüntülemeden sorumludur. Bu alt sistemdeki türler, türlerin Windows Presentation Foundation (WPF) bağlı olup Windows Presentation Foundation ayrılır. En önemli türler, görüntülenecek metin satırları dizisini ve ayrıca WPF UI öğelerini kullanarak metni donatma özellikleri, seçimi ve özellikleri de kontrol altına alan <xref:Microsoft.VisualStudio.Text.Editor.ITextView> ve <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> türleridir. Bu alt sistem ayrıca metin görüntüleme alanı çevresinde kenar boşlukları sağlar. Bu kenar boşlukları genişletilmiş olabilir ve farklı türlerde içerik ve görsel etkileri içerebilir. Kenar boşluklarının örnekleri, satır numarası ekranları ve kaydırma çubuklarıdır.

Metin görünümü alt sisteminin genel türleri,Microsoft.VisualStudio.Text.UI.dllve ** *Microsoft.VisualStudio.Text.UI.Wpf.dll.* İlk derleme platformdan bağımsız öğeleri, ikinci derleme ise WPF'ye özgü öğeleri içerir.

### <a name="classification-subsystem"></a>Sınıflandırma alt sistemi

Sınıflandırma alt sistemi, metin için yazı tipi özelliklerini belirlemekle sorumludur. Sınıflandırıcı, metni "anahtar sözcük" veya "açıklama" gibi farklı sınıflara kırar. Sınıflandırma biçimi eşlemesi, bu sınıfları gerçek yazı tipi özellikleriyle (örneğin, "Blue Consolas 10 pt" ) ilgilidir. Bu bilgiler metin görünümü tarafından metin biçimlerini ve işlemelerini sağlar. Bu konunun ilerleyenlarında daha ayrıntılı olarak açıklanan etiketleme, verilerin metin yayma aralığıyla ilişkilendirilmasını sağlar.

Sınıflandırma alt sisteminin genel türleri Microsoft.VisualStudio.Text.Logic.dll ve sınıflandırmanın görsel yönleriyle etkileşime Microsoft.VisualStudio.Text.UI.Wpf.dll.

### <a name="operations-subsystem"></a>İşlemler alt sistemi

İşlem alt sistemi düzenleyici davranışını tanımlar. Düzenleyici komutlarını ve Visual Studio için uygulama sağlar.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Metin modeline ve metin görünümüne daha yakından bakış

### <a name="the-text-model"></a>Metin modeli

Metin modeli alt sistemi, farklı metin türleri gruplamaları içerir. Bunlar metin arabelleği, metin anlık görüntüleri ve metin yayılmalarıdır.

#### <a name="text-buffers-and-text-snapshots"></a>Metin arabellekleri ve metin anlık görüntüleri

Arabirimi, UTF-16 kullanılarak kodlanan Unicode karakter dizisini temsil <xref:Microsoft.VisualStudio.Text.ITextBuffer> eder. Bu, UTF-16 kullanılarak kodlanmış olan, `String` .NET Framework. Metin arabelleği bir dosya sistemi belgesi olarak kalıcı olabilir, ancak bu gerekli değildir.

boş bir metin arabelleği veya bir dizeden veya 'den başlatılan bir metin <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> arabelleği oluşturmak için <xref:System.IO.TextReader> kullanılır. Metin arabelleği dosya sisteminde olarak kalıcı <xref:Microsoft.VisualStudio.Text.ITextDocument> olabilir.

Herhangi bir iş parçacığı, çağırarak metin arabelleğinin sahipliğini alana kadar metin arabelleği <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A> düzenleyebilir. Bundan sonra yalnızca bu iş parçacığı düzenleme gerçekleştirebilirsiniz.

Metin arabelleği, kullanım ömrü boyunca birçok sürümden geçebilirsiniz. Arabellek her düzende yeni bir sürüm oluşturulur ve sabit bir sürüm, arabelleğin bu <xref:Microsoft.VisualStudio.Text.ITextSnapshot> sürümünün içeriğini temsil eder. Metin anlık görüntüleri sabit olduğundan, temsil ettiği metin arabelleği değişmeye devam ediyor olsa bile kısıtlama olmadan herhangi bir iş parçacığında metin anlık görüntüsüne erişebilirsiniz.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Metin anlık görüntüleri ve metin anlık görüntü satırları

Metin anlık görüntüsünün içeriğini karakter dizisi veya satır dizisi olarak görüntüebilirsiniz. Karakterlerin ve satırların her ikisi de sıfırdan başlayarak dizine alındı. Boş metin anlık görüntüsü sıfır karakter ve bir boş satır içerir. Bir satır, geçerli bir Unicode satır sonu karakter dizisiyle veya arabelleğin başına veya sonuna göre ayrılmıştır. Satır sonu karakterleri metin anlık görüntüsünde açıkça temsil edilen ve bir metin anlık görüntüsünde satır sonları aynı olması gerekmez.

> [!NOTE]
> Düzenleyicideki satır sonu karakterleri hakkında daha fazla bilgi Visual Studio bkz. [Kodlamalar ve satır sonları.](../ide/encodings-and-line-breaks.md)

Metin satırı, belirli bir satır numarası için veya belirli bir karakter konumu için metin anlık görüntüsünden <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> alınarak elde edilen bir nesneyle temsil edilir.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints, SnapshotSpans ve NormalizedSnapshotSpanCollections

, <xref:Microsoft.VisualStudio.Text.SnapshotPoint> anlık görüntüdeki bir karakter konumunu temsil eder. Konumun sıfır ile anlık görüntü uzunluğu arasında olduğu garantidir. , <xref:Microsoft.VisualStudio.Text.SnapshotSpan> bir anlık görüntüde yer alan metin yayma durumunu temsil eder. Uç konumunun sıfır ile anlık görüntü uzunluğu arasında yer alma garantisine sahip olduğu garantidir. <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, aynı anlık görüntüden bir nesne <xref:Microsoft.VisualStudio.Text.SnapshotSpan> kümesinden oluşur.

#### <a name="spans-and-normalizedspancollections"></a>Spans ve NormalizedSpanCollections

, <xref:Microsoft.VisualStudio.Text.Span> metin anlık görüntüsünde bir metin aralığına uygulanacak aralığı temsil eder. Anlık görüntü konumu sıfır tabanlıdır, bu nedenle aralıklar sıfır dahil olmak üzere herhangi bir konumdan başlayabilir. Bir `End` aralığın özelliği, özelliğinin ve özelliğinin `Start` toplamına `Length` eşittir. , `Span` özelliği tarafından dizine alan karakteri `End` içermez. Örneğin, Start=5 ve Length=3 içeren bir aralık End=8'e sahip ve 5, 6 ve 7 konumlarında karakterleri içerir. Bu sürenin notası [5..8) olur.

Uç konum da dahil olmak üzere ortak konumlar varsa iki yayma kesiştir. Bu nedenle, [3, 5) ve [2, 7) kesişimi [3, 5) ve [3, 5) ile [5, 7) kesişimi [5, 5) 'dır. ([5, 5) boş bir süreye dikkat.)

Bitiş konumu dışında ortak konumlara sahipse iki yayma çakışması. Boş bir zaman aralığı hiçbir zaman diğer aralıklarla çakışmaz ve iki aralığın çakışması hiçbir zaman boştur.

<xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>, aralıkların Başlangıç özellikleri sırasına göre bir aralık listesidir. Listede çakışan veya çakışan aralıklar birleştirilir. Örneğin, aralık kümesi [5...9), [0..1), [3..6) ve [9..10), normalleştirilmiş aralık listesi [0..1), [3..10) olur.

#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit, TextVersion ve metin değişikliği bildirimleri

Metin arabelleğinin içeriği bir nesnesi kullanılarak <xref:Microsoft.VisualStudio.Text.ITextEdit> değiştirilebilir. Böyle bir nesne oluşturmak (yöntemlerinden `CreateEdit()` birini <xref:Microsoft.VisualStudio.Text.ITextBuffer> kullanarak) metin düzenlemelerinden oluşan bir metin işlemi başlatır. Her düzenleme, arabellekte yer alan metinlerin bir dizeye göre değiştirilmesidir. Her düzenlemenin koordinatları ve içeriği, işlem başlatan arabelleğin anlık görüntüsüne göre ifade edildi. nesnesi, <xref:Microsoft.VisualStudio.Text.ITextEdit> aynı işlemde yapılan diğer düzenlemelerden etkilenen düzenlemelerin koordinatlarını ayarlar.

Örneğin, şu dizeyi içeren bir metin arabelleği düşünün:

```
abcdefghij
```

karakterini kullanarak [2..4) aralığın yerini alan bir düzenleme ve `X` [6..9) karakterini kullanarak aralığın yerini alan ikinci bir düzenleme olmak için iki düzenleme içeren bir işlem `Y` uygulama. Sonuç şu arabellek olur:

```
abXefYj
```

İkinci düzenlemenin koordinatları, ilk düzenleme uygulanmadan önce, işlemin başındaki arabelleğin içeriğine göre hesaplanır.

Arabellekte yapılan değişiklikler nesne yöntemi çağırarak işlem tamamlandığında etkili olur <xref:Microsoft.VisualStudio.Text.ITextEdit> `Apply()` . Boş olmayan en az bir düzenleme varsa, yeni bir <xref:Microsoft.VisualStudio.Text.ITextVersion> oluşturulur, yeni bir oluşturulur <xref:Microsoft.VisualStudio.Text.ITextSnapshot> ve bir `Changed` olay tetiklenir. Her metin sürümünün farklı bir metin anlık görüntüsü vardır. Bir metin anlık görüntüsü, bir düzenleme işleminden sonra metin arabelleğinin bütün durumunu temsil eder, ancak bir metin sürümü yalnızca bir anlık görüntüden diğerine yapılan değişiklikleri açıklar. Genel olarak, metin anlık görüntülerinin bir kez kullanılması ve sonra atılması ve metin sürümlerinin bir süre etkin kalması gerekir.

Metin sürümü bir içerir <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection> . Bu koleksiyonda, anlık görüntüye uygulandığında sonraki anlık görüntüyü üreten değişiklikler açıklanmaktadır. <xref:Microsoft.VisualStudio.Text.ITextChange>Koleksiyonda her değişiklik, değişikliğin karakter konumunu, değiştirilen dizeyi ve değiştirme dizesini içerir. Değiştirilen dize temel bir ekleme için boş ve bir temel silme için değiştirme dizesi boş. Normalleştirilmiş koleksiyon, her zaman `null` Metin arabelleğinin en son sürümü içindir.

Herhangi bir <xref:Microsoft.VisualStudio.Text.ITextEdit> anda bir metin arabelleği için yalnızca bir nesne oluşturulabilir ve metin arabelleğinin sahip olduğu iş parçacığında tüm metin düzenlemeleri gerçekleştirilmelidir (sahiplik istenirse). Bir metin düzenlemesi, `Cancel` yöntemi veya metodu çağırarak bırakılmış olabilir `Dispose` .

<xref:Microsoft.VisualStudio.Text.ITextBuffer> Ayrıca `Insert()` ,, `Delete()` ve `Replace()` arayüzde bulunan yöntemlere benzeyen yöntemler de sağlar <xref:Microsoft.VisualStudio.Text.ITextEdit> . Bunların çağrılması <xref:Microsoft.VisualStudio.Text.ITextEdit> , nesne oluşturma, benzer çağrıyı yapma ve ardından düzenleme uygulama ile aynı etkiye sahiptir.

#### <a name="tracking-points-and-tracking-spans"></a>İzleme noktaları ve izleme yayılmaları

Bir <xref:Microsoft.VisualStudio.Text.ITrackingPoint> metin arabelleğindeki bir karakter konumunu temsil eder. Arabellek, karakterin konumunun kaydırmaya neden olacak şekilde düzenlenirse, izleme noktası onunla kaydırılır. Örneğin, bir izleme noktası bir arabellekte konum 10 ' a başvuruyorsa ve arabelleğin başına beş karakter eklenirse, izleme noktası daha sonra 15 konumuna başvurur. Bir ekleme işlemi, izleme noktası tarafından belirtilen konumda tam olarak gerçekleşiyorsa, davranışı tarafından belirlenir <xref:Microsoft.VisualStudio.Text.PointTrackingMode> , ya da olabilir `Positive` `Negative` . İzleme modu pozitifse, izleme noktası artık ekleme işlemi sonunda olan aynı karaktere başvurur. İzleme modu negatifse, izleme noktası orijinal konumdaki ilk ekli karakteri ifade eder. Bir izleme noktası tarafından temsil edilen konumdaki karakter silinirse, izleme noktası silinen aralığı izleyen ilk karaktere kayar. Örneğin, bir izleme noktası 5 konumundaki karakteri ifade eder ve konum 3 ile 6 arasındaki karakterler silinirse, izleme noktası 3 konumundaki karakteri gösterir.

<xref:Microsoft.VisualStudio.Text.ITrackingSpan>Yalnızca tek bir konum yerine bir karakter aralığını temsil eder. Davranışı, tarafından belirlenir <xref:Microsoft.VisualStudio.Text.SpanTrackingMode> . Span Tracking modu [SpanTrackingMode. Edgein](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive)ise, izleme yayılımı, kenarlarındaki metni eklemek için artar. Span Tracking modu [SpanTrackingMode. EdgeExclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive)ise, izleme yayılım, kenarlarına yerleştirilmiş metni içermez. Ancak, yayma izleme modu [SpanTrackingMode. Edgepozitif](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive)ise, bir ekleme geçerli konumu başlatmaya doğru bir şekilde gönderir ve yayılma Izleme modu [SpanTrackingMode. EdgeNegative](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative)ise, bir ekleme geçerli konumu sonuna doğru bir yere iter.

Bir izleme noktasının, ait oldukları metin arabelleğinin herhangi bir anlık görüntüsü için bir izleme yayılımının konumunu alabilirsiniz. İzleme noktaları ve izleme yayılmaları, herhangi bir iş parçacığından güvenle başvurulabilir.

#### <a name="content-types"></a>İçerik türleri

İçerik türleri, farklı türde içerik tanımlamaya yönelik bir mekanizmadır. İçerik türü "Text", "Code" veya "binary" gibi bir dosya türü veya "xml", "vb" veya "c#" gibi bir teknoloji türü olabilir. örneğin, "using" sözcüğü hem C# hem de Visual Basic, diğer programlama dillerinde olmayan bir anahtar sözcüktür. Bu nedenle, bu anahtar sözcüğünün tanımı "c#" ve "vb" içerik türleriyle sınırlı olacaktır.

İçerik türleri, donmanlar ve düzenleyicinin diğer öğeleri için bir filtre olarak kullanılır. Birçok Düzenleyici özelliği ve uzantı noktası, içerik türü başına tanımlanır. örneğin, metin renklendirme düz metin dosyaları, XML dosyaları ve Visual Basic kaynak kodu dosyaları için farklıdır. Metin arabelleklerine genellikle, oluşturulduklarında bir içerik türü atanır ve bir metin arabelleğinin içerik türü değiştirilebilir.

İçerik türleri, diğer içerik türlerinden birden çok devralınabilir. , <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> Belirli bir içerik türünün üst öğeleri olarak birden çok temel tür belirtmenizi sağlar.

Geliştiriciler kendi içerik türlerini tanımlayabilir ve kullanarak bunları kaydedebilir <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> . Birçok Düzenleyici özelliği, kullanarak belirli bir içerik türüne göre tanımlanabilir <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> . Örneğin, Düzenleyici kenar boşlukları, donnlar ve fare işleyicileri yalnızca belirli içerik türlerini görüntüleyen düzenleyicilerle uygulanabilmeleri için tanımlanabilir.

### <a name="the-text-view"></a>Metin görünümü

Model Görünüm denetleyicisi (MVC) deseninin görünüm kısmı metin görünümünü, görünümün biçimlendirmesini, kaydırma çubuğu gibi grafik öğelerini ve giriş işaretini tanımlar. Visual Studio düzenleyicisinin tüm sunum öğeleri WPF tabanlıdır.

#### <a name="text-views"></a>Metin görünümleri

<xref:Microsoft.VisualStudio.Text.Editor.ITextView>Arabirim, metin görünümünün platformdan bağımsız bir gösterimidir. Genellikle metin belgelerini bir pencerede göstermek için kullanılır, ancak örneğin bir araç ipucunda başka amaçlar için de kullanılabilir.

Metin görünümü farklı türlerde metin arabelleklerine başvurur. <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A>Özelliği, <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> Bu üç farklı metin arabelleğini işaret eden bir nesneyi ifade eder: en üst veri düzeyi arabelleği, düzenleme arabelleği ve metin görünümünde görüntülenen arabellek olan görsel arabellek olan veri arabelleği.

Metin, temel alınan metin arabelleğine eklenen sınıflandırıcılarına göre biçimlendirilir ve metin görünümüne eklenmiş olan kenarlığı sağlayıcıları kullanılarak donılır.

#### <a name="the-text-view-coordinate-system"></a>Metin görünümü koordinat sistemi

Metin görünümü koordinat sistemi, metin görünümündeki konumları belirtir. Bu koordinat sisteminde x değeri 0,0, görüntülenmekte olan metnin sol kenarına karşılık gelir ve 0,0 y değeri, görüntülenmekte olan metnin üst kenarına karşılık gelir. X koordinatı soldan sağa artar ve y koordinatı üstten alta kadar artar.

Bir görünüm penceresi (metnin metin penceresinde görünür olması) dikey kaydırıldığında yatay olarak aynı şekilde kaydırılamıyor. Bir görünüm penceresi, çizim yüzeyine göre taşınabilmesi için Sol koordinatı değiştirilerek yatay olarak kaydırıldı. Ancak, bir görünüm penceresi, yalnızca işlenen metnin değiştirilerek, bir olayın oluşturulmasına neden olacak şekilde dikey olarak kaydırılabilirler <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> .

Koordinat sistemindeki uzaklıklar mantıksal piksellere karşılık gelir. Metin işleme yüzeyi ölçeklendirme dönüştürmesi olmadan görüntüleniyorsa, metin işleme koordinat sistemindeki bir birim, ekranda bir piksele karşılık gelir.

#### <a name="margins"></a>Kenar boşlukları

<xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin>Arabirim bir kenar boşluğunu temsil eder ve kenar boşluğunun görünürlüğünü ve boyutunu denetim altına sunar. "Top", "left", "Right" ve "bottom" adlı dört önceden tanımlı kenar boşluğu vardır ve bir görünümün üst, alt, sol veya sağ kenarına iliştirilir. Bu kenar boşlukları, diğer kenar boşluklarının yerleştirilebileceği kapsayıcılardır. Arabirim, kenar boşluğunun boyutunu ve bir kenar boşluğunun görünürlüğünü döndüren yöntemleri tanımlar. Kenar boşlukları, eklendiği metin görünümü hakkında ek bilgiler sağlayan görsel öğelerdir. Örneğin, satır numarası kenar boşluğu metin görünümü için satır numaralarını görüntüler. Glif kenar boşluğu Kullanıcı arabirimi öğelerini görüntüler.

<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>Arabirim, kenar boşluklarının oluşturulmasını ve yerleşimini işler. Kenar boşlukları, diğer kenar boşluklarına göre sıralanır. Daha yüksek öncelikli kenar boşlukları metin görünümüne daha yakın bulunur. Örneğin, iki sol kenar boşluğu, kenar boşluğu A ve kenar boşluğu b ve kenar boşluğu B 'nin kenar boşluğu A 'dan daha düşük bir önceliği varsa, sol kenar boşluğunun sol tarafında B kenar boşluğu belirir.

#### <a name="the-text-view-host"></a>Metin görünümü Konağı

<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>Arabirim, metin görünümünü ve görünüme eşlik eden, örneğin, kaydırma çubuklarını içerir. Metin görünümü Konağı, görünümün bir kenarlığına eklenen kenar boşlukları da içerir.

#### <a name="formatted-text"></a>Biçimli metin

Metin görünümünde görüntülenen metin <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> nesnelerden oluşur. Her metin görünümü satırı metin görünümündeki bir satırlık metne karşılık gelir. Temel alınan metin arabelleğindeki uzun çizgiler kısmen görünmeyebilir (sözcük kaydırma etkinleştirilmemişse) veya birden çok metin görünümü satıra ayrılabilir. <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>Arabirim, koordinatlar ve karakterler arasında eşleme için yöntemler ve özellikler içerir ve satırla ilişkilendirilebilen donnments için.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> nesneler bir arabirim kullanılarak oluşturulur <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> . Şu anda görünümde görüntülenen metinle ilgili endişeleriniz varsa, biçimlendirme kaynağını yoksayabilirsiniz. Görünümde görüntülenmeyen metin biçimi ile ilgileniyorsanız (örneğin, zengin metin kesme ve yapıştırmayı desteklemek için), metin <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> arabelleğindeki metni biçimlendirmek için seçeneğini kullanabilirsiniz.

Metin görünümü tek seferde bir biçimlendirir <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> .

## <a name="editor-features"></a>Düzenleyici özellikleri

Düzenleyicinin özellikleri, özelliğin tanımının uygulamadan ayrı olması için tasarlanmıştır. Düzenleyici şu özellikleri içerir:

- Etiketler ve sınıflandırıcılar

- Satırdaki kenarlıkları

- Projeksiyon

- Anahat Oluşturma

- Fare ve tuş bağlamaları

- İşlemler ve temel elemanlar

- IntelliSense

### <a name="tags-and-classifiers"></a>Etiketler ve sınıflandırıcılar

Etiketler, metnin bir yayılımı ile ilişkili işaretçiler. Bunlar, örneğin metin renklendirme, alt çizgiler, grafikler veya açılır pencereler kullanılarak farklı yollarla sunulabilir. Sınıflandırıcılar tek bir etiket türüdür.

Diğer etiket türleri <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> metin vurgulaması, ana <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> hat ve <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> derleme hataları içindir.

#### <a name="classification-types"></a>Sınıflandırma türleri

Bir <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> arabirim, soyut bir metin kategorisi olan bir denklik sınıfını temsil eder. Sınıflandırma türleri, diğer sınıflandırma türlerinden birden çok devralma yapılabilir. Örneğin, programlama dili sınıflandırmaları, hepsi "Code" kaynağından devraldığı "anahtar sözcüğü", "Açıklama" ve "tanımlayıcı" içerebilir. Doğal dil sınıflandırması türleri "ad", "fiil" ve "sıfatıcı" içerebilir ve bunların hepsi "doğal dil" den devralınır.

#### <a name="classifications"></a>Sınıflandırmalar

Sınıflandırma, genellikle metin yayılımı üzerinde belirli bir sınıflandırma türünün bir örneğidir. Bir <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> Sınıflandırmayı temsil etmek için kullanılır. Bir sınıflandırma yayılımı, belirli bir metin yayılımını kapsayan bir etiket olarak düşünülebilir ve sisteme bu metin yayılma alanının belirli bir sınıflandırma türünde olduğunu söyler.

#### <a name="classifiers"></a>Sınıflandırıcılar

<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>, Metni bir sınıflandırma kümesine kesen bir mekanizmadır. Sınıflandırıcılar belirli içerik türleri için tanımlanmalıdır ve belirli metin arabellekleri için oluşturulur. İstemcilerin <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> metin sınıflandırmasına katılmak için uygulaması gerekir.

#### <a name="classifier-aggregators"></a>Sınıflandırıcı toplayıcısını değiştirme

Sınıflandırıcı toplayıcısı, bir metin arabelleğinin tüm sınıflandırmalarını yalnızca bir sınıflandırma kümesiyle birleştiren bir mekanizmadır. Örneğin, hem C# sınıflandırıcı hem de Ingilizce dil Sınıflandırıcısı, C# dosyasındaki bir yorum üzerinde sınıflandırmalar oluşturabilir. Şu yorumu göz önünde bulundurun:

```
// This method produces a classifier
```

Bir C# Sınıflandırıcısı, tüm yayılımı bir açıklama olarak etiketleyebilir ve Ingilizce dil Sınıflandırıcısı "fiil" ve "Yöntem" olarak "ad" olarak sınıflandırır. Toplayıcı çakışmayan sınıflandırmalar kümesi oluşturur ve küme türü tüm katkılara göre belirlenir.

Sınıflandırıcının bir sınıflandırıcıda metin kestiğinden bir sınıflandırıcı toplayıcısı da sınıflandırıcıdır. Sınıflandırıcı toplayıcısı, çakışan sınıflandırmalar olmamasını ve sınıflandırmaların sıralanacağını de sağlar. Tek tek sınıflandırıcılar, herhangi bir sırada herhangi bir sınıflandırmadan ve herhangi bir şekilde çakışarak herhangi bir sınıflandırma kümesini döndürmek için ücretsizdir.

#### <a name="classification-formatting-and-text-coloring"></a>Sınıflandırma biçimlendirme ve metin renklendirme

Metin biçimlendirme, metin sınıflandırması üzerinde oluşturulmuş bir özelliğin örneğidir. Bir uygulamadaki metnin görüntülenmesini sağlamak için metin görünümü katmanı tarafından kullanılır. Metin biçimlendirme alanı WPF 'e bağlıdır, ancak sınıflandırmaların mantıksal tanımı değildir.

Sınıflandırma biçimi, belirli bir sınıflandırma türü için biçimlendirme özellikleri kümesidir. Bu biçimler, Sınıflandırma türünün üst öğesinin biçiminden devralınır.

<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>, Bir sınıflandırma türünden metin biçimlendirme özellikleri kümesine yapılan bir haritadır. Düzenleyicide biçim eşlemesinin uygulanması, sınıflandırma biçimlerinin tüm dışarı aktarmaları işler.

### <a name="adornments"></a>Satırdaki kenarlıkları

Donnments, metin görünümündeki karakterlerin yazı tipiyle ve renkleriyle doğrudan ilgili olmayan grafik efektleridir. Örneğin, çok sayıda programlama dilinde derleme olmayan kodu işaretlemek için kullanılan kırmızı dalgalı çizgi alt çizgisi gömülü bir kenarlığı ve araç ipuçları açılır pencereler olur. Donmanlar, öğesinden türetilir <xref:System.Windows.UIElement> ve uygular <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . İki özel kenarlığı etiketi türü, <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> bir görünümdeki metinle aynı boşluğu kaplayan donmanlar için ve <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> dalgalı çizgi altı çizili için.

Gömülü donnlar, biçimli metin görünümünün bir parçasını oluşturan grafiklerdir. Bunlar farklı Z düzeni katmanlarında düzenlenirler. Aşağıdaki gibi üç yerleşik katman vardır: metin, giriş işareti ve seçim. Ancak, geliştiriciler daha fazla katman tanımlayabilir ve bunları bir diğerine göre sıraya alabilir. Üç tür katıştırılmış donatımı (metin taşındığında taşınır ve metin silindiğinde silinir), görünüm göreli donnments (görünümün metin olmayan bölümleri ile ilgili olması gerekir) ve sahip denetimli Donatılar (geliştiricinin yerleştirmesini yönetmesi gerekir). (geliştiricinin yerleşimini yönetmesi gerekir).

Açılır donatılanlar, metin görünümünün üzerinde küçük bir pencerede görünen grafiklerdir, örneğin araç ipuçları.

### <a name="projection"></a><a name="projection"></a> Yansıtma

Projeksiyon, aslında metin depolayamayan farklı bir tür metin arabelleği oluşturmak için kullanılan bir tekniktir, bunun yerine metni diğer metin arabelleğinden birleştirir. Örneğin, bir yansıtma arabelleği iki diğer arabellekten metin birleştirmek ve sonucu yalnızca bir arabellekte olduğu gibi sunmak ya da bir arabellekteki metnin parçalarını gizlemek için kullanılabilir. Projeksiyon arabelleği, başka bir yansıtma arabelleğine kaynak arabelleği olarak davranabilir. Projeksiyon ile ilişkili bir arabellek kümesi, metni birçok farklı şekilde yeniden düzenlemek için oluşturulabilir. (Böyle bir küme, *arabellek grafiği* olarak da bilinir.) Visual Studio metin anahat oluşturma özelliği, daraltılan metni gizlemek için bir yansıtma arabelleği kullanılarak uygulanır ve ASP.NET sayfaları için Visual Studio düzenleyicisi, Visual Basic ve C# gibi gömülü dilleri desteklemek için projeksiyonu kullanır.

<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>Kullanılarak oluşturulur <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService> . Projeksiyon arabelleği, <xref:Microsoft.VisualStudio.Text.ITrackingSpan> *kaynak yayılmaları* olarak bilinen sıralı nesne dizisiyle temsil edilir. Bu yayılmalar içeriği bir dizi karakter olarak sunulur. Kaynak yayılma alanlarının çizildiği metin arabelleklerinin adı *kaynak arabelleklerdir*. Bir yansıtma arabelleğinin istemcilerinin, sıradan bir metin arabelleğinden farklı olduğunu farkında olması gerekmez.

Projeksiyon arabelleği, kaynak arabelleklerindeki metin değiştirme olaylarını dinler. Bir kaynak yayılma alanındaki metin değiştiğinde, projeksiyon arabelleği değiştirilen metin koordinatlarını kendi koordinatlarına eşler ve uygun metin değişikliği olaylarını yükseltir. Örneğin, şu içeriğe sahip olan A ve B kaynak arabelleklerini göz önünde bulundurun:

```
A: ABCDE
B: vwxyz
```

Yansıtma arabelleği P, bir diğeri tüm arabelleği olan ve diğeri de B arabelleği olan iki metin yayılma alanından biçimlendirilmişse, P aşağıdaki içeriğe sahiptir:

```
P: ABCDEvwxyz
```

Alt dize, `xy` B arabelleğinden silinirse, buffer P, 7 ve 8 konumlarındaki karakterlerin silindiğini belirten bir olay oluşturur.

Projeksiyon arabelleği de doğrudan düzenlenebilir. Düzenlemeleri uygun kaynak arabelleklerine yayar. Örneğin, bir dize, 6 konumuna ("v" karakterinin özgün konumu) göre buffer P 'ye eklenirse, ekleme 1 konumundaki arabellek B 'ye yayılır.

Yansıtma arabelleğine katkıda bulunan kaynak yayılmalar üzerinde kısıtlamalar vardır. Kaynak yayılmaları çakışmayabilir; projeksiyon arabelleğindeki bir konum herhangi bir kaynak arabellekte birden fazla konuma eşlenemez ve Kaynak arabellekteki bir konum bir yansıtma arabelleğinde birden fazla konuma eşlenemez. Kaynak arabellek ilişkisinde hiçbir döngüye karşı izin verilmez.

Bir projeksiyon arabelleğinin kaynak arabelleklerinin kümesi değiştiğinde ve kaynak kümesi değiştiğinde olaylar tetiklenir.
Bir uyum arabelleği, özel bir yansıtma arabelleği türüdür. Ana hat ve metin bloklarını genişlettikten ve daraltma işlemlerinde öncelikli olarak kullanılır. Bir arabellek, tek bir kaynak arabelleğini temel alır ve tam arabellekteki yayılmalar, kaynak arabellekte sıralandığı gibi sıralanmalıdır.

#### <a name="the-buffer-graph"></a>Arabellek grafı

<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>Arabirim, projeksiyon arabelleklerinin bir grafiğinde eşlemeyi mümkün. Tüm metin arabellekleri ve İzdüşüm arabellekleri, bir dil derleyicisi tarafından üretilen soyut sözdizimi ağacına benzer şekilde, yönlendirilmiş bir Çevrimsiz grafiğinde toplanır. Grafik, herhangi bir metin arabelleği olabilen üst arabellek tarafından tanımlanır. Arabellek grafı, en üst arabellekteki bir noktadan kaynak arabellekteki bir noktaya veya en üstteki arabellekteki bir yayılma alanından bir kaynak arabelleğindeki bir dizi yayılmasına eşlenir. Benzer şekilde, bir kaynak arabelleğinden bir noktayı veya yayılımı, en üst arabellekteki bir noktaya eşleyebilir. Arabellek grafikleri kullanılarak oluşturulur <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService> .

#### <a name="events-and-projection-buffers"></a>Olaylar ve projeksiyon arabellekleri

Projeksiyon arabelleği değiştirildiğinde, değişiklikler yansıtma arabelleğinden buna bağlı olan arabelleklere gönderilir. Tüm arabellekler değiştirildikten sonra, arabellek değişiklik olayları, en derin arabellekten başlayarak oluşturulur.

### <a name="outlining"></a>Anahat Oluşturma

Ana hat oluşturma, metin görünümündeki farklı metin bloklarını genişletme veya daraltma olanağıdır. Ana hat, bir türü olarak tanımlanır <xref:Microsoft.VisualStudio.Text.Tagging.ITag> , donnments ile aynı şekilde tanımlanır. <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>, Genişletilebilen veya daraltılabilen bir metin bölgesini tanımlayan bir etikettir. Ana hattı kullanmak için, almak için öğesini içeri aktarmanız gerekir <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> . Ana hat Yöneticisi, nesneler olarak temsil edilen farklı blokları numaralandırır, daraltır ve genişletir <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> ve olayları uygun şekilde yükseltir.

### <a name="mouse-bindings"></a>Fare bağlamaları

Fare bağlamaları farklı komutlara fare hareketlerini bağlar. Fare bağlamaları bir kullanılarak tanımlanır <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> ve anahtar bağlamaları bir kullanılarak tanımlanır <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider> . , <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> Tüm bağlamaları otomatik olarak başlatır ve görünümdeki fare olaylarına bağlar.

<xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor>Arabirim, farklı fare olayları için işlem öncesi ve işlem sonrası olay işleyicilerini içerir. Olaylardan birini işlemek için içindeki yöntemlerin bazılarını geçersiz kılabilirsiniz <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> .

### <a name="editor-operations"></a>Düzenleyici işlemleri

Düzenleyici işlemleri, komut dosyası veya başka amaçlar için düzenleyiciyle etkileşimi otomatikleştirmek üzere kullanılabilir. <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>Belirli bir üzerinde erişim işlemlerine aktarabilirsiniz <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Daha sonra bu nesneleri kullanarak seçimi değiştirebilir, görünümü kaydıradırabilir veya giriş işaretini görünümün farklı bölümlerine taşıyabilirsiniz.

### <a name="intellisense"></a>IntelliSense

IntelliSense, deyimin tamamlanmasını, imza yardımını (parametre bilgisi olarak da bilinir), hızlı bilgi ve hafif bulbs 'leri destekler.

Deyimin tamamlanması, yöntem adları, XML öğeleri ve diğer kodlama veya biçimlendirme öğeleri için olası tamamların açılır listesini sağlar. Genel olarak, bir kullanıcı hareketi bir tamamlanma oturumu çağırır. Oturum, olası tamamlamaların listesini görüntüler ve Kullanıcı bir listeden seçim yapabilir veya kapatabilir. <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, oluşturmak ve tetiklemek için <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession> sorumludur. , <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> oturum için tamamlanma <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> öğelerinin hesaplaması.

## <a name="see-also"></a>Ayrıca bkz.

- [Dil hizmeti ve düzenleyici uzantısı noktaları](../extensibility/language-service-and-editor-extension-points.md)
- [Düzenleyici içeri aktarmaları](../extensibility/editor-imports.md)
