---
title: Model Düzenleyicisi
ms.date: 04/12/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.3dscene
- vs.graphics.modelviewer
ms.assetid: 5edf1a30-9307-43c3-9b8b-831217be0104
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7adee409ff6bb5721724b9acc2e76a11d32a4f54
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589857"
---
# <a name="model-editor"></a>Model düzenleyicisi

Bu belge, 3B modelleri görüntülemek, oluşturmak ve değiştirmek için Visual Studio **Model Editor** ile nasıl çalışacağını açıklar.

**Model** Düzenleyicisi'ni sıfırdan temel 3B modeller oluşturmak veya tam özellikli 3B modelleme araçları kullanılarak oluşturulan daha karmaşık 3B modelleri görüntülemek ve değiştirmek için kullanabilirsiniz.

## <a name="supported-formats"></a>Desteklenen biçimler

**Model** Düzenleyicisi, DirectX uygulama geliştirmede kullanılan birkaç 3B model biçimini destekler:

|Biçim Adı|Dosya Uzantısı|Desteklenen İşlemler (Görüntüleme, Düzenleme, Oluşturma)|
|-----------------| - | - |
|AutoDesk FBX Değişim Dosyası|*.fbx*|Görüntüleme, Düzenleme, Oluşturma|
|Collada DAE Dosyası|*.dae*|Görüntüleme, Düzenleme (Collada DAE dosyalarında yapılan değişiklikler FBX biçimi kullanılarak kaydedilir.)|
|OBJ|*Obj*|Görüntüleme, Düzenleme (OBJ dosyalarında yapılan değişiklikler FBX biçimi kullanılarak kaydedilir.)|

## <a name="get-started"></a>Kullanmaya başlayın

Bu bölümde Visual Studio C++ projenize nasıl bir 3B model ekleyeceğiniz ve başlamanıza yardımcı olacak diğer temel bilgiler açıklanmaktadır.

> [!NOTE]
> 3B sahneler (.fbx dosyaları) gibi grafik öğelerinin otomatik yapı tümleştirmesi yalnızca C++ projeleri için desteklenir.

### <a name="to-add-a-3d-model-to-your-project"></a>Projenize bir 3B model eklemek için

1. Grafiklerle çalışmanız için gerekli Visual Studio bileşeninin yüklü olduğundan emin olun. Bileşenin adı **Image ve 3D model editörleri.**

   Yüklemek için, **Araçlar** > **Araçlar Al Araçları ve Özellikleri** menü çubuğundan seçerek Visual Studio Installer'ı açın ve ardından Bireysel **bileşenler** sekmesini seçin. Oyunlar **ve Grafikler** kategorisi altında Resim ve **3D model düzenleyicileri** bileşenini seçin ve sonra **Değiştir'i**seçin.

   ![Resim ve 3B model editörleri bileşeni](media/image-3d-model-editors-component.png)

   Bileşen yüklemeye başlar.

2. **Çözüm Gezgini'nde,** görüntüyü eklemek istediğiniz C++ projesinin kısayol menüsünü açın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.

3. Yeni **Öğe Ekle** iletişim kutusunda, **Grafik** kategorisi **altında, 3B Sahne (.fbx) seçeneğini belirleyin.**

   ![Seçili 3B sahneile Yeni Öğe iletişim kutusu ekleme](media/add-new-3d-scene.png)

   > [!NOTE]
   > **Yeni Öğe Ekle** iletişim kutusunda **Grafik** kategorisini görmüyorsanız ve Resim **ve 3B model düzenleyicileri** bileşeni yüklüyse, grafik öğeleri proje türünüz için desteklenmez.

4. Model dosyasının **Adını** girin ve sonra **Ekle'yi**seçin.

### <a name="axis-orientation"></a>Eksen yönlendirme

Visual Studio, 3B ekseninin her yönünü destekler ve eksen yönlendirme bilgilerini destekleyen model dosya biçimlerinden yükler. Eksen yönlendirmesi belirtilmemişse, Visual Studio varsayılan olarak sağ elini kullanan koordinat sistemini kullanır. **Eksen göstergesi,** tasarım yüzeyinin sağ alt köşesindeki geçerli eksen yönünü gösterir. Eksen **göstergesinde**kırmızı x eksenini, yeşil y eksenini temsil eder ve mavi z eksenini temsil eder.

### <a name="begin-your-3d-model"></a>3B modelinizi başlatın

Model Düzenleyicisi'nde, her yeni nesne her zaman Model Düzenleyicisi'nde yerleşik olan temel 3B şekillerden veya *ilkel*şekillerden biri olarak başlar. Yeni ve benzersiz nesneler oluşturmak için, görünüme bir temel öğe ekler ve sonra da köşeleriyle oynayarak şeklini değiştirirsiniz. Karmaşık şekiller için, kalıp veya alt bölüm kullanarak ek köşeler ekler ve sonra bunlarda değişiklik yaparsınız. Sahnenize ilkel bir nesne ekleme hakkında bilgi için [bkz.](#Adding3DObjects) Bir nesneye nasıl daha fazla vertices ekleyeceğiniz hakkında bilgi [için](#ModifyingObjects)bkz.

## <a name="work-with-the-model-editor"></a>Model Düzenleyicisi ile çalışma

Aşağıdaki bölümlerde Model Düzenleyicisi'nin 3B modellerle nasıl çalışacağı açıklanmıştır.

### <a name="model-editor-toolbars"></a>Model Düzenleyicisi araç çubukları

Model Düzenleyicisi araç çubukları, 3B modeller ile çalışmanıza yardımcı olan komutlar içerir.

Model Düzenleyicisi'nin durumunu etkileyen komutlar, ana Visual Studio penceresindeki **Model Düzenleyicisi Modu** araç çubuğunda bulunur. Modelleme araçları ve komut dosyası komutları Model Düzenleyicisi tasarım yüzeyindeki **Model Düzenleyiciaraç** çubuğunda bulunur.

İşte Model **Düzenleyici Modu** araç çubuğu:

![Model Görüntüleyici modal araç çubuğu.](../designers/media/digit-mre-modal-toolbar.png)

Bu tablo, Model **Düzenleyici Modu** araç çubuğundaki soldan sağa doğru göründükleri sırada listelenen öğeleri açıklar.

|Araç Çubuğu Öğesi|Açıklama|
|------------------|-----------------|
|**Seç**|Etkin seçim moduna bağlı olarak görünümdeki noktaların, kenarların, yüzeylerin ya da nesnelerin seçimini etkinleştirir.|
|**Pan**|Pencere çerçevesine göre bir 3B sahnenin hareketini sağlar. Kaydırmak için görünümde bir nokta seçip dolaştırın.<br /><br /> **Select** modunda, **Kaydırma** modunu geçici olarak etkinleştirmek için **Ctrl** tuşuna basıp basılı tutabilirsiniz.|
|**Zoom**|Pencere çerçevesine göre daha az ya da daha fazla görünüm ayrıntısının görüntülenmesini sağlar. **Yakınlaştırma** modunda, sahnede bir nokta seçin ve sonra yakınlaştırmak için sağa veya aşağı veya uzaklaştırmak için sola veya yukarı taşıyın.<br /><br /> **Select** modunda, **Ctrl**tuşuna basıp basılı tutarken fare tekerleğini kullanarak yakınlaştırabilir veya uzaklaştırabilirsiniz.|
|**Yörünge**|Görünümü seçili nesnenin çevresinde dairesel bir yola yerleştirir. Hiçbir nesne seçili değilse, yol görünüm başlangıcında ortalanır. **Not:**  **Ortografik** projeksiyon etkinleştirildiğinde bu modun bir etkisi yoktur.|
|**Dünya Yerel**|Bu öğe etkin olduğunda, seçili nesne üzerindeki dönüştürmeler dünya uzayında oluşur. Aksi takdirde, seçilen nesne üzerinde dönüştürmeler yerel uzayda oluşur.|
|**Pivot Modu**|Bu öğe etkinleştirildiğinde, dönüşümler seçili nesnenin *pivot noktasının* konumunu ve yönünü etkiler (Pivot noktası çeviri, ölçekleme ve döndürme işlemlerinin merkezini tanımlar.) Aksi takdirde, dönüşümler nesnenin geometrisinin konumunu ve yönünü, pivot noktasına göre etkiler.|
|**X eksenini kilitle**|Nesne düzenlemesini x ekseni ile sınırlar. Yalnızca işleyici pencere öğesinin orta bölümünü kullandığınızda uygulanır.|
|**Y eksenini kilitle**|Nesne düzenlemesini y ekseni ile sınırlar. Yalnızca işleyici pencere öğesinin orta bölümünü kullandığınızda uygulanır.|
|**Kilit Z ekseni**|Nesne düzenlemesini z ekseni ile sınırlar. Yalnızca işleyici pencere öğesinin orta bölümünü kullandığınızda uygulanır.|
|**Çerçeve Nesnesi**|Seçili nesneyi, görünümün ortasında yer alacak şekilde çerçeveler.|
|**Görünüm**|Görünüm yönlendirmesini ayarlar. Kullanılabilir yönlendirmeler şunlardır:<br /><br /> **Front**<br /> Görünümü sahnenin önüne yerleştirir.<br /><br /> **Geri**<br /> Görünümü sahnenin arkasına yerleştirir.<br /><br /> **Sol**<br /> Görünümü sahnenin soluna yerleştirir.<br /><br /> **Doğru**<br /> Görünümü sahnenin sağına yerleştirir.<br /><br /> **Sayfanın Üstü**<br /> Görünümü sahnenin yukarısına yerleştirir.<br /><br /> **Alt**<br /> Görünümü sahnenin aşağısına yerleştirir. **Not:**  **Ortografik** projeksiyon etkinleştirildiğinde görüş yönünü değiştirmenin tek yolu budur.|
|**Yansıtma**|Sahneyi çizmek için kullanılan projeksiyonun türünü ayarlar. Kullanılabilir projeksiyonlar şunlardır:<br /><br /> **Perspektif**<br /> Perspektif projeksiyonunda, bakış açısından uzakta olan nesneler boyut olarak daha küçük görünür ve en sonunda uzaktaki bir noktaya doğru birleşir.<br /><br /> **Ortografik**<br /> Ortografik projeksiyonda, bakış açısına olan uzaklıklarına bakılmaksızın nesneler aynı boyutta görünür. Bir yakınlaşma görüntüsü olmaz. **Ortografik** projeksiyon etkinleştirildiğinde, görünümü konumlandırmak için **Orbit** modunu kullanamazsınız.|
|**Çizim Stili**|Sahnedeki nesnelerin işlenme yöntemini ayarlar. Kullanılabilir stiller şunlardır:<br /><br /> **Tel Çerçeve**<br /> Etkin olduğunda, nesneler tel çerçeve şeklinde işlenir.<br /><br /> **Fazla çekme**<br /> Etkin olduğunda, nesneler ek karıştırma kullanılarak işlenir. Görünümde, fazla çekme işleminin ne kadar yapıldığını görselleştirmek için bunu kullanabilirsiniz.<br /><br /> **Düz Gölgeli**<br /> Etkin olduğunda, nesneler temel ve düz gölgeli bir aydınlatma modeli kullanılarak işlenir. Bir nesnenin yüzeylerini daha kolay görmek için bunu kullanabilirsiniz.<br /><br /> Bu seçeneklerden hiçbiri etkin değilse, her nesne kendisine uygulanan malzeme kullanılarak işlenir.|
|**Gerçek Zamanlı Görüntüleme Modu**|Gerçek zamanlı görüntüleme etkinleştirildiğinde, Visual Studio hiçbir kullanıcı eylemi gerçekleştirilmese bile tasarım yüzeyini yeniden çizer. Bu mod, zamanla değişen gölgelendiriciler ile çalıştığınızda kullanışlıdır.|
|**Kılavuzu Aç/Kapat**|Bu öğe etkinleştirildiğinde bir kılavuz görüntülenir. Aksi takdirde kılavuz görüntülenmez.|
|**Araç Kutusu**|Araç **Kutusunu**dönüşümlü olarak gösterir veya gizler.|
|**Belge Anahattı**|Belge **Anahattı** penceresini dönüşümlü olarak gösterir veya gizler.|
|**Özellikler**|Özellikler **penceresini** dönüşümlü olarak gösterir veya gizler.|
|**Gelişmiş**|Gelişmiş komutları ve seçenekleri içerir.<br /><br /> **Grafik Motorları**<br /><br /> **D3D11 ile işleme**<br /> Model Düzenleyicisi tasarım yüzeyini işlemek için Direct3D 11 kullanır.<br /><br /> **D3D11WARP ile işleme**<br /> Model Düzenleyicisi tasarım yüzeyini işlemek için Direct3D 11 Windows Gelişmiş Pikselleştirme Platformu'nu (WARP) kullanır.<br /><br /> **Sahne Yönetimi**<br /><br /> **İçeri Aktarma**<br /> Nesneleri başka bir 3B model dosyasından geçerli sahneye aktarın.<br /><br /> **Ebeveyne Ekle**<br /> Çoklu seçilen nesnelerin ilkini, kalan seçili nesnelerin üst öğesi olarak ayarlar.<br /><br /> **Ebeveynden Ayırma**<br /> Seçili nesneyi üst öğesinden ayırır. Seçili nesne sahnede bir *kök nesne* olur. Kök nesnenin bir üst nesnesi olmaz.<br /><br /> **Grup Oluşturma**<br /> Seçili nesneleri eşdüzey nesneler olarak gruplandırır.<br /><br /> **Nesneleri Birleştirme**<br /> Seçili nesneleri tek bir nesne halinde birleştirir.<br /><br /> **Çokgen Seçiminden Yeni Nesne Oluşturma**<br /> Seçilen yüzeyleri geçerli nesneden kaldırır ve bu yüzeyleri içeren yeni bir nesneyi sahneye ekler.<br /><br /> **Araçlar**<br /><br /> **Çevirme Çokgen Sargı**<br /> Seçili çokgenleri çevirir ve böylece sargı sırasını ve yüzey normalini tersine çevirir.<br /><br /> **Tüm Animasyonları Kaldır**<br /> Nesnelerden animasyon verilerini kaldırır.<br /><br /> **Üçgen**<br /> Seçili nesneyi üçgenlere dönüştürür.<br /><br /> **Görünüm**<br /><br /> Arkayüz Ayrılması<br /> Arka yüz ayırmayı etkinleştirir veya devre dışı bırakır.<br /><br /> **Kare Hızı**<br /> Tasarım yüzeyinin sağ üst köşesinde kare hızını görüntüler. Kare hızı, saniye başına çizilen çerçeve sayısıdır.<br /><br /> Bu seçenek, **Gerçek Zamanlı Görüntüleme Modu** seçeneğini etkinleştirdiğinizde yararlıdır.<br /><br /> **Tümünü Göster**<br /> Sahnedeki tüm nesneleri gösterir. Bu, her nesnenin **Gizli** özelliğini **False'a**sıfırlar.<br /><br /> **Yüz Normallerini Göster**<br /> Her bir yüzeyin normalini gösterir.<br /><br /> **Eksik Malzemeleri Göster**<br /> Atanmış malzemeleri olmayan nesneler üzerinde özel bir doku gösterir.<br /><br /> **Pivot'u Göster**<br /> Etkin seçimin pivot noktasında bir 3B eksen işaretçisinin ekranını etkinleştirir veya devre dışı kılabilir.<br /><br /> **Yer Tutucu Düğümlerini Göster**<br /> Yer tutucu düğümlerini gösterir. Nesneleri gruplandırdığınızda bir yer tutucu düğümü oluşturulur.<br /><br /> **Vertex Normalleri Göster**<br /> Her köşenin normalini gösterir. **İpucu:**  Son komut **dosyasını** yeniden çalıştırmak için Komut Dosyaları düğmesini seçebilirsiniz.|

Model **Düzenleyiciaraç** çubuğu aşağıda veda edin:

![Model Görüntüleyici araç çubuğu](../designers/media/digit-mre-toolbar.png)

Sonraki tabloda, Model **Düzenleyicisi** araç çubuğundaki yukarıdan aşağıya doğru göründükleri sırada listelenen öğeler açıklanır.

|Araç Çubuğu Öğesi|Açıklama|
|------------------|-----------------|
|**Çevirme**|Seçimi taşır.|
|**Ölçeklendirme**|Seçimin boyutunu değiştirir.|
|**Döndür**|Seçimi döndürür.|
|**Nokta'yı Seçin**|Bir nesne üzerinde tek tek noktaları seçmek için **Seçim modunu** ayarlar.|
|**Kenar'ı Seçin**|Bir nesne üzerinde bir kenar (iki tepe arasında bir çizgi) seçmek için **Seçim modunu** ayarlar.|
|**Yüz'u Seçin**|Nesne üzerinde bir yüz seçmek için **Seçim modunu** ayarlar.|
|**Nesne'yi Seçin**|Tüm nesneyi seçmek için **Seçim modunu** ayarlar.|
|**Yükselt**|Ek bir yüzey oluşturur ve bunu seçili yüze bağlar.|
|**Alt bölme**|Seçilen her yüzeyi birden fazla yüzeye böler. Yeni yüzler oluşturmak için, biri özgün yüzün ortasına ve biri de her bir kenarın ortasına olmak üzere yeni köşeler eklenir ve sonra bunlar orijinal köşelerle birleştirilir. Eklenen yüzlerin sayısı, orijinal yüzdeki köşelerin sayısına eşittir.|

### <a name="control-the-view"></a>Görünümü denetleme

3D sahne bir konum ve bir yönelim eki olan bir sanal kamera olarak düşünülebilir görünümüne göre işlenir. Konumu ve yönlendirmeyi değiştirmek için Model **Düzenleyici Modu** araç çubuğundaki görünüm denetimlerini kullanın.

Aşağıdaki tabloda birincil görünüm denetimleri açıklanmaktadır.

|Görünüm Denetimi|Açıklama|
|------------------|-----------------|
|**Pan**|Pencere çerçevesine göre bir 3B sahnenin hareketini sağlar. Kaydırmak için görünümde bir nokta seçip dolaştırın.<br /><br /> **Select** modunda, **Kaydırma** modunu geçici olarak etkinleştirmek için **Ctrl** tuşuna basıp basılı tutabilirsiniz.|
|**Zoom**|Pencere çerçevesine göre daha az ya da daha fazla görünüm ayrıntısının görüntülenmesini sağlar. **Yakınlaştırma** modunda, sahnede bir nokta seçin ve sonra yakınlaştırmak için sağa veya aşağı veya uzaklaştırmak için sola veya yukarı taşıyın.<br /><br /> **Select** modunda, **Ctrl**tuşuna basıp basılı tutarken fare tekerleğini kullanarak yakınlaştırabilir veya uzaklaştırabilirsiniz.|
|**Yörünge**|Görünümü seçili nesnenin çevresinde dairesel bir yola yerleştirir. Hiçbir nesne seçili değilse, yol görünüm başlangıcında ortalanır. **Not:**  **Ortografik** projeksiyon etkinleştirildiğinde bu modun bir etkisi yoktur.|
|**Çerçeve Nesnesi**|Seçili nesneyi, görünümün ortasında yer alacak şekilde çerçeveler.|

Görünüm sanal kamera ile belirlenir, ancak aynı zamanda bir projeksiyon ile de tanımlanır. Projeksiyon, görünümdeki şekillerin ve nesnelerin tasarım yüzeyinde piksellere nasıl dönüştürüldüğünü tanımlar. Model **Düzenleyicisi** araç çubuğunda **Perspektif** veya **Ortografik** projeksiyonu seçebilirsiniz.

|Yansıtma|Açıklama|
|----------------|-----------------|
|**Perspektif**|Perspektif projeksiyonunda, bakış açısından uzakta olan nesneler boyut olarak daha küçük görünür ve en sonunda uzaktaki bir noktaya doğru birleşir.|
|**Ortografik**|Ortografik projeksiyonda, bakış açısına olan uzaklıklarına bakılmaksızın nesneler aynı boyutta görünür. Bir yakınlaşma görüntüsü olmaz. **Ortografik** projeksiyon etkinleştirildiğinde, görünümü rasgele konumlandırmak için **Orbit** modunu kullanamazsınız.|

Örneğin, benzer iki sahneyi karşılaştırmak istediğinizde, bir 3B sahneyi bilinen bir konumdan ve açıdan görüntülemeyi yararlı bulabilirsiniz. Bu senaryo için, Model Düzenleyicisi önceden tanımlı çeşitli görünümler sağlar. **Model Düzenleyici Modu** araç çubuğunda önceden tanımlanmış bir görünüm kullanmak için **Görünüm'i**seçin ve ardından ön, arka, sol, sağ, üst veya alt olmak üzere istediğiniz önceden tanımlanmış görünümü seçin. Bu görünümlerde, sanal kamera doğrudan sahnenin başlangıç noktasına doğru bakar. Örneğin, **Üstle Görüntüle'yi**seçerseniz, sanal kamera sahnenin kaynağına doğrudan üstünden bakar.

### <a name="view-additional-geometry-details"></a>Ek geometri ayrıntılarını görüntüleme

Bir 3B nesneyi veya sahneyi daha iyi anlamak için, tepe noktası başına normaller, yüz başına normaller, etkin seçimin pivot noktaları ve diğer ayrıntılar gibi ek geometri ayrıntılarını görüntüleyebilirsiniz. Bunları etkinleştirmek veya devre dışı kalmak için **Model Düzenleyiciaraç** çubuğunda **Komut Dosyası** > **Görünümü'ni**seçin ve ardından istediğinizi seçin.

### <a name="create-and-import-3d-objects"></a>3B nesneler oluşturma ve alma<a name="Adding3DObjects"></a>

Sahneye önceden tanımlanmış bir 3B şekil eklemek **için, Araç**Kutusu'nda, istediğinizi seçin ve ardından tasarım yüzeyine taşıyın. Yeni şekiller sahnenin başlangıcına yerleştirilir. Model Düzenleyici yedi şekil sağlar: **Koni**, **Küp**, **Silindir**, **Disk**, **Düzlem**, **Küre**, ve **Çaydanlık**.

Bir dosyadan bir 3B nesne almak için, **Model Düzenleyicisi** araç çubuğunda Gelişmiş**Sahne Yönetimi** > **Alma** **>'ni** > seçin ve sonra almak istediğiniz dosyayı belirtin.

### <a name="transform-objects"></a>Dönüşüm nesneleri

Bir nesneyi **Döndürme,** **Ölçek**ve **Çeviri** özelliklerini değiştirerek *dönüştürebilirsiniz.* *Döndürme,* bir nesneyi eksen, y ekseni ve z ekseni etrafında eksen noktası etrafında ardışık döndürmeler uygulayarak yönlendirir. Her döndürme belirtiminin sırasıyla x, y ve z olmak üzere üç bileşeni vardır ve bu bileşenler derece olarak belirtilir. **Ölçekleme,** bir nesneyi pivot noktası üzerinde ortalanmış bir veya daha fazla eksen boyunca belirli bir faktöre kadar uzatarak yeniden boyutlandırılır. *Çeviri,* bir nesneyi pivot noktası yerine üst öğesine göre 3 boyutlu uzayda bulur.

Modelleme araçlarını kullanarak veya özellikleri ayarlayarak bir nesneyi dönüştürebilirsiniz.

#### <a name="transform-an-object-by-using-modeling-tools"></a>Modelleme araçlarını kullanarak nesneyi dönüştürme

1. **Select** modunda, dönüştürmek istediğiniz nesneyi seçin. Tel çerçeve yer paylaşımı nesnenin seçili olduğunu gösterir.

2. Model **Düzenleyicisi** araç çubuğunda **Çevir,** **Ölçekle**veya **Döndür** aracını seçin. Seçili nesne için bir çeviri, ölçeklendirme veya döndürme işleyicisi görüntülenir.

3. Dönüştürmeyi gerçekleştirmek için işleyiciyi kullanın. Çeviri ve ölçeklendirme dönüşümlerinde işleyici bir eksen göstergesidir. Bir kerede bir eksen değiştirebilir veya göstergenin ortasındaki beyaz küpü kullanarak aynı anda tüm eksenleri değiştirebilirsiniz. Döndürme için işleyici x eksenine (kırmızı), y eksenine (yeşil) ve z eksenine (mavi) karşılık gelen renk kodlu dairelerden oluşan bir küredir. İstediğiniz döndürmeyi oluşturmak için her ekseni tek tek değiştirmeniz gerekir.

#### <a name="transform-an-object-by-setting-its-properties"></a>Özelliklerini ayarlayarak nesneyi dönüştürme

1. **Select** modunda, dönüştürmek istediğiniz nesneyi seçin. Tel çerçeve yer paylaşımı nesnenin seçili olduğunu gösterir.

2. **Özellikler** penceresinde, **Döndürme,** **Ölçek**ve **Çeviri** özellikleri için değerleri belirtin.

    > [!IMPORTANT]
    > **Döndürme** özelliği için, üç eksenin her birinin etrafındaki dönüş derecesini belirtin. Döndürmeler sırayla uygulandığından önce x ekseni, sonra y ekseni ve sonra da z ekseni açısından bir döndürme planladığınızdan emin olun.

Modelleme araçlarını kullanarak, dönüştürmeleri hızlı ancak kesin olmayan bir şekilde oluşturabilirsiniz. Nesne özelliklerini ayarlayarak, dönüştürmeleri kesin ancak hızlı olmayan bir şekilde belirtebilirsiniz. İstediğiniz dönüştürmelere "yeteri kadar" yaklaşmak için modelleme araçlarını kullanmanızı ve ardından özellik değerlerinde ince ayar yapmanızı öneririz.

İşleyicileri kullanmayı istemiyorsanız, serbest biçim modunu etkinleştirebilirsiniz. Model **Düzenleyicisi** araç çubuğunda, serbest biçim modunu etkinleştirmek (veya devre dışı etmek) için **Komut Dosyaları** > **Araçları** > **Serbest Biçimli Düzenleme'yi** seçin. Serbest biçim modunda, işleyici üzerindeki bir nokta yerine herhangi bir tasarım yüzeyi noktasında düzenleme yapmaya başlayabilirsiniz. Serbest biçim modunda, değiştirmek istemediklerinizi kilitleyerek bazı eksenlerde yapılacak değişiklikleri kısıtlayabilirsiniz. Model **Düzenleyici Modu** araç çubuğunda, **X Kilit, Y** **kilidi**ve **Kilit Z** düğmelerinin herhangi bir kombinasyonunu seçin.

Kılavuza uydur işlevini kullanarak nesnelerle çalışmayı daha kullanışlı bulabilirsiniz. Model **Düzenleyici Modu** araç çubuğunda, eşlemeyi etkinleştirmek (veya devre dışı kalmak) için **Tuttur'u** seçin. Kılavuza uydur etkinleştirildiğinde, çeviri, döndürme ve ölçeklendirme dönüştürmeleri önceden tanımlı aralıklarla sınırlandırılır.

### <a name="work-with-the-pivot-point"></a>Pivot noktasıyla çalışma

Pivot noktası nesnenin döndürme ve ölçeklendirme merkezini tanımlar. Döndürme ve ölçeklendirme dönüşümlerinden nasıl etkilendiğini değiştirmek için bir nesnenin özet noktasını değiştirebilirsiniz. Model **Düzenleyici Modu** araç çubuğunda, pivot modunu etkinleştirmek (veya devre dışı etmek) için **Pivot Modu'nu** seçin. Pivot modu etkin olduğunda, seçili nesnenin pivot noktasında küçük bir eksen göstergesi görünür. Daha sonra pivot noktasını işlemek için **Çeviri** ve **Döndürme** araçlarını kullanabilirsiniz.

Özet noktasının nasıl kullanılacağını gösteren bir gösteri için [bkz.](../designers/how-to-modify-the-pivot-point-of-a-3-d-model.md)

### <a name="world-and-local-modes"></a>Dünya ve yerel modları

Çeviri ve döndürme, nesnenin yerel koordinat sisteminde (veya *yerel referans çerçevesi)* veya dünyanın koordinat sisteminde (veya *dünya referans çerçevesi)* oluşabilir. Dünya başvuru çerçevesi nesnenin dönüşünden bağımsızdır. Yerel mod varsayılandır. Dünya modunu etkinleştirmek (veya devre dışı kalmak için) **Model Düzenleyici Modu** araç çubuğunda **WorldLocal** düğmesini seçin.

### <a name="modify-objects"></a>Nesneleri değiştirme<a name="ModifyingObjects"></a>

Bir 3B nesnenin şeklini, ön nesnelerini, kenarlarını ve yüzlerini hareket ettirerek veya silerek değiştirebilirsiniz. Varsayılan olarak, Model Düzenleyicisi *nesne modundadır,* böylece tüm nesneleri seçip dönüştürebilirsiniz. Noktaları, kenarları veya yüzeyleri seçmek için uygun seçim modunu seçin. Model **Düzenleyici Modu** araç çubuğunda **Seçim modlarını**seçin ve ardından istediğiniz modu seçin.

Çıkarmayla veya alt bölümlere ayırmayla ek köşeler oluşturabilirsiniz. Çıkarma bir yüzün köşelerini (aynı düzlemli bir yüzler kümesi) çoğaltır ve yüz çoğaltılmış köşelerle bağlı kalır. Alt bölümlere ayırma, önceden bir tane olan yüzeyden birçok yüzey oluşturmak için köşeler ekler. Yeni yüzler oluşturmak için, biri özgün yüzün ortasına ve biri de her bir kenarın ortasına olmak üzere yeni köşeler eklenir ve sonra bunlar orijinal köşelerle birleştirilir. Eklenen yüzlerin sayısı, orijinal yüzdeki köşelerin sayısına eşittir. Her iki durumda da, nesnenin geometrisini değiştirmek için yeni köşeleri çevirebilir, döndürebilir ve ölçeklendirebilirsiniz.

#### <a name="to-extrude-a-face-from-an-object"></a>Bir nesneden bir yüzü çıkarmak için

1. Yüz seçimi modunda, çıkarmak istediğiniz yüzü seçin.

2. Model **Düzenleyicisi** araç **çubuğunda, Komut Dosyası** > **Araçları** > **Ekstrüzyonu'nu**seçin.

#### <a name="to-subdivide-faces"></a>Yüzleri alt bölümlere ayırmak için

1. Yüz seçimi modunda, alt bölümlere ayırmak istediğiniz yüzleri seçin. Alt bölüm yeni kenar verileri oluşturduğundan, tüm yüzeyleri aynı anda alt bölümlere ayırmak yüzler bitişik olduğunda daha tutarlı sonuçlar verir.

2. Model **Düzenleyicisi** araç **çubuğunda, Komut Dosyası** > **Araçları** > **Alt Böl'ü**seçin.

Ayrıca yüzeyleri üçgenlere bölebilir, nesneleri birleştirebilir ve çokgen seçimlerini yeni nesnelere dönüştürebilirsiniz. Üçgenlere bölme, üçgen olmayan bir yüz, en uygun sayıda üçgene dönüştürülecek şekilde ek kenarlar oluşturur; ancak ek geometrik ayrıntı sağlamaz. Birleştirme işlemi, seçili nesneleri tek bir nesne halinde birleştirir. Yeni nesneler bir çokgen seçiminden oluşturulabilir.

#### <a name="triangulate-a-face"></a>Bir yüzü üçgen

1. Yüz seçimi modunda, üçgenlere bölmek istediğiniz yüzü seçin.

2. Model **Düzenleyicisi** araç çubuğunda, **Komut Dosyası** > **Araçları** > **Üçgeni'ni**seçin.

#### <a name="merge-objects"></a>Nesneleri birleştirme

1. Nesne seçimi modunda, birleştirmek istediğiniz nesneleri seçin.

2. Model **Düzenleyicisi** araç çubuğunda, **Komut Dosyası** > **Araçları** > **Birleştirme Nesneleri'ni**seçin.

#### <a name="create-an-object-from-a-polygon-selection"></a>Çokgen seçiminden nesne oluşturma

1. Yüz seçimi modunda yeni bir nesne oluşturmak istediğiniz yüzleri seçin.

2. Model **Düzenleyicisi** araç çubuğunda,**Çokgen Seçimi'nden** **Komut Dosyası** > **Araçları** > Oluşturma Yeni Nesne'yi seçin.

### <a name="work-with-materials-and-shaders"></a>Malzemeler ve gölgeleyicilerle çalışma

Bir nesnenin görünümü, sahnedeki aydınlatma etkileşimi ve nesnenin malzemesi ile belirlenir. Malzemeler, yüzeyin farklı ışık türlerine nasıl tepki verdiğini açıklayan özelliklerle ve nesne yüzeyindeki her pikselin son rengini ışıklandırma bilgisine, doku eşlemelerine, normal eşlemelere ve diğer verilere göre hesaplayan bir gölgelendirici programla tanımlanır.

Model Düzenleyicisi şu varsayılan malzemeleri sağlar:

|Malzeme|Açıklama|
|--------------|-----------------|
|**Işıklandırılmamış**|Benzetimli aydınlatma olmadan bir yüzeyi işler.|
|**Lambert**|Benzetimli ortam aydınlatması ve yayınık aydınlatma ile bir yüzey işler.|
|**Phong**|Benzetimli ortam aydınlatması, yayınık aydınlatma ve yansımalı vurgular ile bir yüzeyi işler.|

Bu malzemelerin her biri nesnenin yüzeyine tek bir doku uygular. Malzemeyi kullanan her nesne için farklı bir doku ayarlayabilirsiniz.

Belirli bir nesnenin sahnedeki farklı ışık kaynaklarına verdiği tepkiyi değiştirmek için, malzemeyi kullanan diğer nesnelerden bağımsız olarak malzemenin aydınlatma özelliklerini değiştirebilirsiniz. Bu tabloda genel aydınlatma özellikleri açıklanmaktadır:

|Aydınlatma Özelliği|Açıklama|
| - |-----------------|
|**Ortam**|Yüzeyin ortam aydınlatmasından nasıl etkilendiğini açıklar.|
|**Yayınık**|Yüzeyin yönlü ve nokta ışıklardan nasıl etkilendiğini açıklar.|
|**Yayımlatıcı**|Yüzeyin, diğer aydınlatmalardan bağımsız olarak ışığı nasıl yaydığını açıklar.|
|**Yansımalı**|Yüzeyin yönlü ve nokta ışıkları nasıl yansıttığını açıklar.|
|**Yansımalı Güç**|Yansımalı vurguların genişliğini ve yoğunluğunu açıklar.|

Bir malzemenin neyi desteklediğine bağlı olarak aydınlatma özelliklerini, dokuları ve diğer verileri değiştirebilirsiniz. **Select** modunda, malzemesini değiştirmek istediğiniz nesneyi seçin ve ardından **Özellikler** penceresinde **MaterialAmbient**, **MaterialDiffuse**, **MaterialEmissive**, **MaterialSpecular , MaterialSpecularPower**veya diğer kullanılabilir özelliği değiştirin. **MaterialSpecularPower** Bir malzeme, özellikleri **Texture1'den** **Texture8'e**sırayla adlandırılmış sekiz dokuya kadar ortaya çıkarabilir.

Bir nesnedeki tüm malzemeleri kaldırmak için, **Model Düzenleyicisi** araç çubuğunda, **Komut Dosyası** > **Malzemeleri** > **Kaldırma Materyalleri'ni**seçin.

3B sahnenizdeki nesnelere uygulayabileceğiniz özel gölgeli malzemeler oluşturmak için **Shader Designer'ı** kullanabilirsiniz. Özel gölgeli malzemelerin nasıl oluşturulabildiğini öğrenmek için Bkz. [Shader Designer.](../designers/shader-designer.md) Bir nesneye özel bir gölgeleyici malzemenin nasıl uygulanacağı hakkında bilgi için [bkz.](../designers/how-to-apply-a-shader-to-a-3-d-model.md)

### <a name="scene-management"></a>Sahne yönetimi

Sahneleri nesnelerin bir hiyerarşisi olarak yönetebilirsiniz. Birden fazla nesne hiyerarşik bir şekilde düzenlendiğinde, üst öğe düğümünün herhangi bir çeviri, ölçek veya döndürme işlemi alt öğelerini de etkiler. Bu, temel nesnelerden karmaşık nesneler veya sahneler oluşturmak istediğinizde kullanışlıdır.

Olay yeri hiyerarşisini görüntülemek ve sahne düğümlerini seçmek için **Belge Anahattı** penceresini kullanabilirsiniz. Anasatırda bir düğüm seçtiğinizde, özelliklerini değiştirmek için **Özellikler** penceresini kullanabilirsiniz.

Gerek birini diğerlerinin üst öğesi yaparak, gerekse üst öğe gibi davranan bir yer tutucu düğümünün altında eşdüzeyler olarak birlikte gruplandırarak nesnelerin bir hiyerarşisini oluşturabilirsiniz.

#### <a name="create-a-hierarchy-that-has-a-parent-object"></a>Üst nesnesi olan bir hiyerarşi oluşturma

1. **Select** modunda iki veya daha fazla nesne seçin. İlk seçtiğiniz öğe üst nesne olur.

2. Model **Düzenleyicisi** araç çubuğunda, **Komut Dosyası** > **Sahne Yönetimi** > **Üst Öğeye Ekle'yi**seçin.

#### <a name="create-a-hierarchy-of-sibling-objects"></a>Kardeş nesnelerhiyerarşisi oluşturma

1. **Select** modunda iki veya daha fazla nesne seçin. Bir yer tutucu nesne oluşturulur ve onların üst nesnesi haline gelir.

2. Model **Düzenleyicisi** araç çubuğunda, **Komut Dosyası** > **Sahne Yönetimi** > **Oluşturma Grubu'nu**seçin.

Model Düzenleyicisi, ilk seçilen nesneyi (üst öğe haline gelen) tanımlamak için beyaz tel çerçeve kullanır. Seçimdeki diğer nesneler mavi bir tel çerçeveye sahiptir. Varsayılan olarak, yer tutucu düğümleri görüntülenmez. Yer tutucu düğümlerini görüntülemek **için, Model Düzenleyiciaraç** çubuğunda, **Komut Dosyası** > **Sahne Yönetimi** > **Yer Tutucu Düğümlerini Göster'i**seçin. Yer tutucu düğümleriyle, yer tutucu olmayan nesnelerle çalıştığınız gibi çalışabilirsiniz.

İki nesne arasındaki üst-alt ilişkilendirmeyi kaldırmak için alt nesneyi seçin ve ardından **Model Düzenleyiciaraç** çubuğunda Üst Öğe'den **Komut Dosyaları** > **Sahne Yönetimi** > **Ayrıştır'ı**seçin. Üst nesne ile alt nesneyi ayırdığınızda, alt nesne sahnede bir kök nesne olur.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

|Komut|Klavye kısayolları|
|-------------| - |
|**Select** moduna geç|**Ctrl**+**G**, **Ctrl**+**Q**<br /><br /> **S**|
|**Yakınlaştırma** moduna geçme|**Ctrl**+**G**, **Ctrl**+**Z**<br /><br /> **Z**|
|**Pan** moduna geçme|**Ctrl**+**G**, **Ctrl**+**P**<br /><br /> **Kahraman**|
|Tümünü seç|**Ctrl**+**A**|
|Geçerli seçimi sil|**Sil**|
|Geçerli seçimi iptal et|**Kaçış** (**Esc**)|
|Yakınlaştır|**Fare tekerleği ileriye doğru**<br /><br /> **Ctrl**+**Mouse tekerleği ileri**<br /><br /> **Shift**+**Mouse tekerleği ileri**<br /><br /> **Ctrl**+**PageUp**<br /><br /> Artı İşaret**+**( )|
|Uzaklaştır|**Fare tekerleği geriye doğru**<br /><br /> **Ctrl**+**Fare tekerleği geriye**<br /><br /> **Shift**+**Mouse tekerleği geriye**<br /><br /> **Ctrl**+**PageDown**<br /><br /> Eksi İşareti (**-**)|
|Kamerayı yukarı kaydır|**PageDown**|
|Kamerayı aşağı kaydır|**PageUp**|
|Kamerayı sola kaydır|**Fare tekerleği sol**<br /><br /> **Ctrl**+**PageDown**|
|Kamerayı sağa kaydır|**Fare tekerleği sağ**<br /><br /> **Ctrl**+**PageDown**|
|Modelin üst kısmını görüntüle|**Ctrl**+**L**, **Ctrl**+**T**<br /><br /> **T**|
|Modelin alt kısmını görüntüle|**Ctrl**+**L**, **Ctrl**+**U**|
|Modelin sol tarafını görüntüle|**Ctrl**+**L**, **Ctrl**+**L**|
|Modelin sağ tarafını görüntüle|**Ctrl**+**L**, **Ctrl**+**R**|
|Modelin önünü görüntüle|**Ctrl**+**L**, **Ctrl**+**F**|
|Modelin arkasını görüntüle|**Ctrl**+**L**, **Ctrl**+**B**|
|Nesneyi pencere içinde çerçevele|**F**|
|Tel çerçeve modunu aç/kapat|**Ctrl**+**L**, **Ctrl**+**W**|
|Kılavuza uydurmayı aç/kapat|**Ctrl**+**G**, **Ctrl**+**N**|
|Pivot modunu aç/kapat|**Ctrl**+**G**, **Ctrl**+**V**|
|X ekseni kısıtlamasını aç/kapat|**Ctrl**+**L**, **Ctrl**+**X**|
|Y ekseni kısıtlamasını aç/kapat|**Ctrl**+**L**, **Ctrl**+**Y**|
|Z ekseni kısıtlamasını aç/kapat|**Ctrl**+**L**, **Ctrl**+**Z**|
|Çeviri moduna geçiş yap|**Ctrl**+**G**, **Ctrl**+**W**<br /><br /> **W**|
|Ölçek moduna geçiş yap|**Ctrl**+**G**, **Ctrl**+**E**<br /><br /> **E**|
|Döndürme moduna geçiş yap|**Ctrl**+**G**, **Ctrl**+**R**<br /><br /> **R**|
|Nokta seçme moduna geçiş yap|**Ctrl**+**L**, **Ctrl**+**1**|
|Kenar seçme moduna geçiş yap|**Ctrl**+**L**, **Ctrl**+**2**|
|Yüz seçme moduna geçiş yap|**Ctrl**+**L**, **Ctrl**+**3**|
|Nesne seçme moduna geçiş yap|**Ctrl**+**L**, **Ctrl**+**4**|
|Yörünge (kamera) moduna geçiş yap|**Ctrl**+**G**, **Ctrl**+**O**|
|Sahnede sonraki nesneyi seç|**Sekme**|
|Sahnede önceki nesneyi seç|**Shift**+**Sekmesi**|
|Geçerli araca bağlı olarak seçili nesneyi düzenle.|**Ok** tuşları|
|Geçerli işleyiciyi devre dışı bırak|**S**|
|Kamerayı döndür|**Sol**+fare tuşu ile Alt**Sürükley**|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Oyunlar ve uygulamalar için 3B varlıklarla çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|Dokular ve görüntüler, 3B modeller ve gölgeli efektler gibi grafik varlıklarıyla çalışmak için kullanabileceğiniz Visual Studio araçlarına genel bir bakış sağlar.|
|[Görüntü Düzenleyici](../designers/image-editor.md)|Dokular ve görüntülerle çalışmak için Visual Studio Image Editor'un nasıl kullanılacağını açıklar.|
|[Shader Tasarımcısı](../designers/shader-designer.md)|Gölgelilerle çalışmak için Visual Studio Shader Designer'ın nasıl kullanılacağını açıklar.|
