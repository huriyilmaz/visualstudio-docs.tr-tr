---
title: Model Düzenleyicisi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.3dscene
- vs.graphics.modelviewer
ms.assetid: 5edf1a30-9307-43c3-9b8b-831217be0104
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1ede47ea89030aed0298961599f09df6444ed968
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664213"
---
# <a name="model-editor"></a>Model Düzenleyicisi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belgede [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , 3B modelleri görüntülemek, oluşturmak ve değiştirmek için Model Düzenleyicisi ile nasıl çalışılacağı açıklanmaktadır.

 Sıfırdan 3B modeller oluşturmak veya tam özellikli 3B modelleme araçları kullanılarak oluşturulmuş daha karmaşık 3B modelleri görüntülemek veya değiştirmek için Model Düzenleyicisi'ni kullanabilirsiniz. Model Düzenleyicisi, DirectX uygulaması geliştirmede kullanılan çeşitli 3B model biçimlerini destekler.

## <a name="supported-formats"></a>Desteklenen biçimler
 Model Düzenleyicisi şu model biçimlerini destekler:

|Biçim Adı|Dosya Uzantısı|Desteklenen İşlemler (Görüntüleme, Düzenleme, Oluşturma)|
|-----------------|--------------------|-------------------------------------------------|
|AutoDesk FBX Değişim Dosyası|.fbx|Görüntüleme, Düzenleme, Oluşturma|
|Collada DAE Dosyası|.dae|Görüntüleme, Düzenleme (Collada DAE dosyalarında yapılan değişiklikler FBX biçimi kullanılarak kaydedilir.)|
|OBJ|.obj|Görüntüleme, Düzenleme (OBJ dosyalarında yapılan değişiklikler FBX biçimi kullanılarak kaydedilir.)|

## <a name="getting-started"></a>Başlarken
 Bu bölümde, projenize 3-b modelinin nasıl ekleneceği [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve başlamak için ihtiyacınız olan temel bilgilerin nasıl sağlanacağı açıklanmaktadır.

#### <a name="to-add-a-3-d-model-to-your-project"></a>Projenize 3B model eklemek için

1. **Çözüm Gezgini**' de, görüntüsünü eklemek istediğiniz projenin kısayol menüsünü açın ve **Ekle**, **Yeni öğe**' yi seçin.

2. **Yeni öğe Ekle** iletişim kutusunda, **yüklü**altında **grafikler**' i seçin ve ardından **3B sahne (. fbx)** öğesini seçin.

3. Model dosyasının **adını** ve oluşturulmasını istediğiniz **konumu** belirtin.

4. **Ekle** düğmesini seçin.

### <a name="axis-orientation"></a>Eksen yönlendirme
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , 3-b eksenin her yönünü destekler ve onu destekleyen model dosya biçimlerinden eksen yönlendirme bilgilerini yükler. Hiçbir eksen yönü belirtilmemişse, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Varsayılan olarak sağ elli koordinat sistemini kullanır. **Eksen göstergesi** , tasarım yüzeyinin sağ alt köşesindeki geçerli eksen yönünü gösterir. **Eksen göstergesinde**, kırmızı x eksenini, yeşil ise y eksenini temsil eder ve mavi, z eksenini temsil eder.

### <a name="beginning-your-3-d-model"></a>3B modelinize başlama
 Model düzenleyicisinde her yeni nesne her zaman, model düzenleyicide yerleşik olan temel 3-b şekillerinde veya temel *elemanların*biri olarak başlar. Yeni ve benzersiz nesneler oluşturmak için, görünüme bir temel öğe ekler ve sonra da köşeleriyle oynayarak şeklini değiştirirsiniz. Karmaşık şekiller için, kalıp veya alt bölüm kullanarak ek köşeler ekler ve sonra bunlarda değişiklik yaparsınız. Sahneye temel bir nesne ekleme hakkında daha fazla bilgi için bkz. [3-b nesneler oluşturma ve içeri aktarma](#Adding3DObjects). Bir nesneye daha fazla köşe ekleme hakkında daha fazla bilgi için bkz. [nesneleri değiştirme](#ModifyingObjects).

## <a name="working-with-the-model-editor"></a>Model Düzenleyicisi ile çalışma
 Aşağıdaki bölümlerde, 3B modellerle çalışmak için Model Düzenleyicisi'nin nasıl kullanılacağı açıklanmaktadır.

### <a name="model-editor-toolbars"></a>Model Düzenleyicisi araç çubukları
 Model Düzenleyicisi araç çubukları, 3B modellerle çalışmanıza yardımcı olan komutlar içerir.

 Model Düzenleyicisi 'nin durumunu etkileyen komutlar, ana penceredeki **Model Düzenleyicisi Modu** araç çubuğunda bulunur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Modelleme araçları ve komut dosyalı komutlar, Model Düzenleyicisi tasarım yüzeyinde **Model Düzenleyicisi** araç çubuğunda bulunur.

 **Model Düzenleyicisi Modu** araç çubuğu şöyledir:

 ![Model görüntüleyici kalıcı araç çubuğu.](../designers/media/digit-mre-modal-toolbar.png "Digit-MRE-Modal-araç çubuğu")

 Bu tabloda, **Model Düzenleyicisi Modu** araç çubuğunda, soldan sağa göründükleri sırada listelenen öğeler açıklanmaktadır.

|Araç Çubuğu Öğesi|Description|
|------------------|-----------------|
|**Seç**|Etkin seçim moduna bağlı olarak görünümdeki noktaların, kenarların, yüzeylerin ya da nesnelerin seçimini etkinleştirir.|
|**Kaydır**|Pencere çerçevesine göre 3B görünümün hareketini sağlar. Kaydırmak için görünümde bir nokta seçip dolaştırın.<br /><br /> **Seçim** modunda, **Dikey Çevir** modunu geçici olarak etkinleştirmek için CTRL tuşuna basılı tutabilirsiniz.|
|**Zoom**|Pencere çerçevesine göre daha az ya da daha fazla görünüm ayrıntısının görüntülenmesini sağlar. **Yakınlaştırma** modu ' nda sahnede bir nokta seçin ve yakınlaştırmak için sağa veya aşağı taşıyın ya da uzaklaştırmak için sola veya yukarı kaydırın.<br /><br /> **Seç** modunda, CTRL tuşunu basılı tutarken fare tekerleğini kullanarak yakınlaştırıp uzaklaştırabilirsiniz.|
|**Yörünge**|Görünümü seçili nesnenin çevresinde dairesel bir yola yerleştirir. Hiçbir nesne seçili değilse, yol görünüm başlangıcında ortalanır. **Note:**  **Orgraphic** projeksiyonu etkinleştirildiğinde bu modun etkisi yoktur.|
|**Dünya Yerel**|Bu öğe etkin olduğunda, seçili nesne üzerindeki dönüştürmeler dünya uzayında oluşur. Aksi takdirde, seçilen nesne üzerinde dönüştürmeler yerel uzayda oluşur.|
|**Özet mod**|Bu öğe etkinleştirildiğinde, dönüşümler seçili nesnenin *pivot noktasının* konumunu ve yönünü etkiler (pivot noktası, çeviri, ölçeklendirme ve döndürme işlemlerinin merkezini tanımlar.) Aksi takdirde dönüşümler, nesnenin geometrisinin konumunu ve yönünü, pivot noktasına göre etkiler.|
|**X eksenini kilitle**|Nesne düzenlemesini x ekseni ile sınırlar. Yalnızca işleyici pencere öğesinin orta bölümünü kullandığınızda uygulanır.|
|**Y eksenini kilitle**|Nesne düzenlemesini y ekseni ile sınırlar. Yalnızca işleyici pencere öğesinin orta bölümünü kullandığınızda uygulanır.|
|**Z eksenini kilitle**|Nesne düzenlemesini z ekseni ile sınırlar. Yalnızca işleyici pencere öğesinin orta bölümünü kullandığınızda uygulanır.|
|**Çerçeve nesnesi**|Seçili nesneyi, görünümün ortasında yer alacak şekilde çerçeveler.|
|**Görünüm**|Görünüm yönlendirmesini ayarlar. Kullanılabilir yönlendirmeler şunlardır:<br /><br /> **Front**<br /> Görünümü sahnenin önüne yerleştirir.<br /><br /> **Geri**<br /> Görünümü sahnenin arkasına yerleştirir.<br /><br /> **Tarafta**<br /> Görünümü sahnenin soluna yerleştirir.<br /><br /> **Right**<br /> Görünümü sahnenin sağına yerleştirir.<br /><br /> **Sayfanın Üstü**<br /> Görünümü sahnenin yukarısına yerleştirir.<br /><br /> **Aşağıya**<br /> Görünümü sahnenin aşağısına yerleştirir. **Note:**  Bu, **Dikçizgisel** projeksiyon etkinken görünüm yönünü değiştirmek için tek yoldur.|
|**Projeksiyon**|Sahneyi çizmek için kullanılan projeksiyonun türünü ayarlar. Kullanılabilir projeksiyonlar şunlardır:<br /><br /> **Perspektif**<br /> Perspektif projeksiyonunda, bakış açısından uzakta olan nesneler boyut olarak daha küçük görünür ve en sonunda uzaktaki bir noktaya doğru birleşir.<br /><br /> **Ortografik**<br /> Ortografik projeksiyonda, bakış açısına olan uzaklıklarına bakılmaksızın nesneler aynı boyutta görünür. Bir yakınlaşma görüntüsü olmaz. **Dikçizgisel** projeksiyon etkinleştirildiğinde, görünümü konumlandırmak Için **Orbit** modunu kullanamazsınız.|
|**Stil çiz**|Sahnedeki nesnelerin işlenme yöntemini ayarlar. Kullanılabilir stiller şunlardır:<br /><br /> **Tel çerçeve**<br /> Etkin olduğunda, nesneler tel çerçeve şeklinde işlenir.<br /><br /> **Hesabı aşma**<br /> Etkin olduğunda, nesneler ek karıştırma kullanılarak işlenir. Görünümde, fazla çekme işleminin ne kadar yapıldığını görselleştirmek için bunu kullanabilirsiniz.<br /><br /> **Düz gölgeli**<br /> Etkin olduğunda, nesneler temel ve düz gölgeli bir aydınlatma modeli kullanılarak işlenir. Bir nesnenin yüzeylerini daha kolay görmek için bunu kullanabilirsiniz.<br /><br /> Bu seçeneklerden hiçbiri etkin değilse, her nesne kendisine uygulanan malzeme kullanılarak işlenir.|
|**Gerçek zamanlı Işleme modu**|Gerçek zamanlı işleme etkinleştirildiğinde, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] herhangi bir kullanıcı eylemi gerçekleştirilmediğinde bile tasarım yüzeyini yeniden çizer. Bu mod, zamanla değişen gölgelendiriciler ile çalıştığınızda kullanışlıdır.|
|**Kılavuzu Aç/Kapat**|Bu öğe etkinleştirildiğinde bir kılavuz görüntülenir. Aksi takdirde kılavuz görüntülenmez.|
|**Araç Kutusu**|Ayrıca **araç kutusunu**gösterir veya gizler.|
|**Belge Anahattı**|Alternatif olarak **Belge Anahattı** penceresini gösterir veya gizler.|
|**Özellikler**|Alternatif olarak **Özellikler** penceresini gösterir veya gizler.|
|**Gelişmiş**|Gelişmiş komutları ve seçenekleri içerir.<br /><br /> **Grafik altyapıları**<br /><br /> **D3D11 ile işleme**<br /> Model Düzenleyicisi tasarım yüzeyini işlemek için Direct3D 11 kullanır.<br /><br /> **D3D11WARP ile işleme**<br /> Model Düzenleyicisi tasarım yüzeyini işlemek için Direct3D 11 Windows Gelişmiş Pikselleştirme Platformu'nu (WARP) kullanır.<br /><br /> **Sahne yönetimi**<br /><br /> **İçeri Aktar**<br /> Başka bir 3B model dosyasındaki nesneleri geçerli görünüme içeri aktarır.<br /><br /> **Üst öğeye Ekle**<br /> Çoklu seçilen nesnelerin ilkini, kalan seçili nesnelerin üst öğesi olarak ayarlar.<br /><br /> **Üst öğeden ayır**<br /> Seçili nesneyi üst öğesinden ayırır. Seçili nesne, sahnede bir *kök nesne* olur. Kök nesnenin bir üst nesnesi olmaz.<br /><br /> **Grup Oluşturma**<br /> Seçili nesneleri eşdüzey nesneler olarak gruplandırır.<br /><br /> **Nesneleri Birleştir**<br /> Seçili nesneleri tek bir nesne halinde birleştirir.<br /><br /> **Çokgen seçiminden yeni nesne oluştur**<br /> Seçilen yüzeyleri geçerli nesneden kaldırır ve bu yüzeyleri içeren yeni bir nesneyi sahneye ekler.<br /><br /> **Araçlar**<br /><br /> **Çokgen dikey sargı**<br /> Seçili çokgenleri çevirir ve böylece sargı sırasını ve yüzey normalini tersine çevirir.<br /><br /> **Tüm animasyonu kaldır**<br /> Nesnelerden animasyon verilerini kaldırır.<br /><br /> **Üçgenlere ayır**<br /> Seçili nesneyi üçgenlere dönüştürür.<br /><br /> **Görünüm**<br /><br /> Arkayüz Ayrılması<br /> Arka yüz ayırmayı etkinleştirir veya devre dışı bırakır.<br /><br /> **Kare hızı**<br /> Tasarım yüzeyinin sağ üst köşesinde kare hızını görüntüler. Kare hızı, saniye başına çizilen çerçeve sayısıdır.<br /><br /> Bu seçenek, **gerçek zamanlı Işleme modu** seçeneğini etkinleştirdiğinizde yararlıdır.<br /><br /> **Tümünü göster**<br /> Sahnedeki tüm nesneleri gösterir. Bu, her nesnenin **Hidden** özelliğini **false**olarak sıfırlar.<br /><br /> **Yüz normalleri göster**<br /> Her bir yüzeyin normalini gösterir.<br /><br /> **Eksik malzemeleri göster**<br /> Atanmış malzemeleri olmayan nesneler üzerinde özel bir doku gösterir.<br /><br /> **Özeti göster**<br /> Etkin seçimin pivot noktasında 3B eksen işaretçisi görüntülenmesini etkinleştirir veya devre dışı bırakır.<br /><br /> **Yer tutucu düğümlerini göster**<br /> Yer tutucu düğümlerini gösterir. Nesneleri gruplandırdığınızda bir yer tutucu düğümü oluşturulur.<br /><br /> **Köşe normalleri göster**<br /> Her köşenin normalini gösterir. **İpucu:**  Son betiği yeniden çalıştırmak için **betikler** düğmesini seçebilirsiniz.|

 **Model Düzenleyicisi** araç çubuğu şöyledir:

 ![Model Görüntüleyicisi araç çubuğu](../designers/media/digit-mre-toolbar.png "Basamak-MRE-araç çubuğu")

 Sonraki tabloda, **Model Düzenleyicisi** araç çubuğunda yukarıdan aşağıya göründükleri sırada listelenen öğeler açıklanmaktadır.

|Araç Çubuğu Öğesi|Description|
|------------------|-----------------|
|**Çevir**|Seçimi taşır.|
|**Ölçeklendirme**|Seçimin boyutunu değiştirir.|
|**Döndür**|Seçimi döndürür.|
|**Noktayı seçin**|Bir nesnedeki noktaları tek tek seçmek için **seçim modunu** ayarlar.|
|**Kenar seçin**|Bir nesne üzerinde bir kenar (iki köşe arasında bir çizgi) seçmek için **seçim modunu** ayarlar.|
|**Yüz seçin**|Nesne üzerinde bir yüz seçmek için **seçim modunu** ayarlar.|
|**Nesne Seç**|**Seçim modunu** , tüm nesneyi seçmek için ayarlar.|
|**Kalıptan geçirir**|Ek bir yüzey oluşturur ve bunu seçili yüze bağlar.|
|**Bölümlere**|Seçilen her yüzeyi birden fazla yüzeye böler. Yeni yüzler oluşturmak için, biri özgün yüzün ortasına ve biri de her bir kenarın ortasına olmak üzere yeni köşeler eklenir ve sonra bunlar orijinal köşelerle birleştirilir. Eklenen yüzlerin sayısı, orijinal yüzdeki köşelerin sayısına eşittir.|

### <a name="controlling-the-view"></a>Görünümü denetleme
 3B sahne görünüme göre işlenir; bu bir konumu ve yönü olan sanal bir kamera olarak düşünülebilir. Konumu ve yönü değiştirmek için, **Model Düzenleyicisi Modu** araç çubuğundaki görünüm denetimlerini kullanın.

 Aşağıdaki tabloda birincil görünüm denetimleri açıklanmaktadır.

|Görünüm Denetimi|Description|
|------------------|-----------------|
|**Kaydır**|Pencere çerçevesine göre 3B görünümün hareketini sağlar. Kaydırmak için görünümde bir nokta seçip dolaştırın.<br /><br /> **Seçim** modunda, **Dikey Çevir** modunu geçici olarak etkinleştirmek için CTRL tuşuna basılı tutabilirsiniz.|
|**Zoom**|Pencere çerçevesine göre daha az ya da daha fazla görünüm ayrıntısının görüntülenmesini sağlar. **Yakınlaştırma** modu ' nda sahnede bir nokta seçin ve yakınlaştırmak için sağa veya aşağı taşıyın ya da uzaklaştırmak için sola veya yukarı kaydırın.<br /><br /> **Seç** modunda, CTRL tuşunu basılı tutarken fare tekerleğini kullanarak yakınlaştırıp uzaklaştırabilirsiniz.|
|**Yörünge**|Görünümü seçili nesnenin çevresinde dairesel bir yola yerleştirir. Hiçbir nesne seçili değilse, yol görünüm başlangıcında ortalanır. **Note:**  **Orgraphic** projeksiyonu etkinleştirildiğinde bu modun etkisi yoktur.|
|**Çerçeve nesnesi**|Seçili nesneyi, görünümün ortasında yer alacak şekilde çerçeveler.|

 Görünüm sanal kamera ile belirlenir, ancak aynı zamanda bir projeksiyon ile de tanımlanır. Projeksiyon, görünümdeki şekillerin ve nesnelerin tasarım yüzeyinde piksellere nasıl dönüştürüldüğünü tanımlar. **Model Düzenleyicisi** araç çubuğunda, **perspektif** veya **diksel** projeksiyon seçeneklerinden birini belirleyebilirsiniz.

|Projeksiyon|Description|
|----------------|-----------------|
|**Perspektif**|Perspektif projeksiyonunda, bakış açısından uzakta olan nesneler boyut olarak daha küçük görünür ve en sonunda uzaktaki bir noktaya doğru birleşir.|
|**Ortografik**|Ortografik projeksiyonda, bakış açısına olan uzaklıklarına bakılmaksızın nesneler aynı boyutta görünür. Bir yakınlaşma görüntüsü olmaz. **Dikçizgisel** projeksiyon etkinleştirildiğinde, görünümü rastgele konumlandırmak Için **yörünge** modunu kullanamazsınız.|

 3 boyutlu bir görünümü bilinen bir konum ve açıdan görüntülemeyi (örneğin, iki benzer görünümü karşılaştırmak istediğinizde) kullanışlı bulabilirsiniz. Bu senaryo için, Model Düzenleyicisi önceden tanımlı çeşitli görünümler sağlar. Önceden tanımlanmış bir görünüm kullanmak için, **Model Düzenleyicisi Modu** araç çubuğunda **görüntüle**' yi seçin ve ardından istediğiniz önceden tanımlanmış görünümü (ön, arka, sol, sağ, üst veya alt) seçin. Bu görünümlerde, sanal kamera doğrudan sahnenin başlangıç noktasına doğru bakar. Örneğin, **en üstte görüntüle**' yi seçerseniz, sanal kamera doğrudan üzerinde sahnenin başlangıcına bakar.

### <a name="viewing-additional-geometry-details"></a>Ek geometri ayrıntılarını görüntüleme
 Bir 3B nesneyi veya sahneyi daha iyi anlamak için, her köşe için normal değerler, her yüz için normal değerler, etkin seçimin pivot noktaları ve diğer ayrıntılar gibi ek geometri ayrıntılarını görüntüleyebilirsiniz. Bunları etkinleştirmek veya devre dışı bırakmak için, **Model Düzenleyicisi** araç çubuğunda **betikler**, **Görünüm**' ü seçin ve istediğiniz birini seçin.

### <a name="creating-and-importing-3-d-objects"></a><a name="Adding3DObjects"></a> 3-b nesneler oluşturma ve içeri aktarma
 Sahneye önceden tanımlı bir 3B şekil eklemek için, **araç kutusunda**istediğiniz birini seçin ve tasarım yüzeyine taşıyın. Yeni şekiller sahnenin başlangıcına yerleştirilir. Model Düzenleyicisi yedi şekil sağlar: **koni**, **küp**, **silindir**, **disk**, **düzlem**, **küre**ve **ekip**.

 Bir dosyadan 3B nesne içeri aktarmak için, **Model Düzenleyicisi** araç çubuğunda **Gelişmiş**, **sahne yönetimi**, **içeri aktar**' ı seçin ve ardından içeri aktarmak istediğiniz dosyayı belirtin.

### <a name="transforming-objects"></a>Nesneleri dönüştürme
 Bir nesneyi, **döndürme**, **Ölçek**ve **çeviri** özelliklerini değiştirerek *dönüştürebilirsiniz* . *Döndürme* , x ekseni, y ekseni ve onun Özet noktası tarafından tanımlanan z ekseni etrafında ardışık döndürmeler uygulayarak bir nesneyi yönlendirir. Her döndürme belirtiminin sırasıyla x, y ve z olmak üzere üç bileşeni vardır ve bu bileşenler derece olarak belirtilir. **Ölçeklendirme** , bir nesneyi, Özet noktasında ortalanan bir veya daha fazla eksende belirtilen faktörle uzatarak yeniden boyutlandırır. *Çeviri* , bir nesneyi Özet noktası yerine üst öğesine göre 3 boyutlu boşluk olarak konumlandırır.

 Modelleme araçlarını kullanarak veya özellikleri ayarlayarak bir nesneyi dönüştürebilirsiniz.

##### <a name="to-transform-an-object-by-using-modeling-tools"></a>Modelleme araçlarını kullanarak bir nesneyi dönüştürmek için

1. **Seç** modunda, dönüştürmek istediğiniz nesneyi seçin. Tel çerçeve yer paylaşımı nesnenin seçili olduğunu gösterir.

2. **Model Düzenleyicisi** araç çubuğunda **çevir**, **Ölçek**veya **döndürme** aracını seçin. Seçili nesne için bir çeviri, ölçeklendirme veya döndürme işleyicisi görüntülenir.

3. Dönüştürmeyi gerçekleştirmek için işleyiciyi kullanın. Çeviri ve ölçeklendirme dönüşümlerinde işleyici bir eksen göstergesidir. Bir kerede bir eksen değiştirebilir veya göstergenin ortasındaki beyaz küpü kullanarak aynı anda tüm eksenleri değiştirebilirsiniz. Döndürme için işleyici x eksenine (kırmızı), y eksenine (yeşil) ve z eksenine (mavi) karşılık gelen renk kodlu dairelerden oluşan bir küredir. İstediğiniz döndürmeyi oluşturmak için her ekseni tek tek değiştirmeniz gerekir.

##### <a name="to-transform-an-object-by-setting-its-properties"></a>Özelliklerini ayarlayarak bir nesneyi dönüştürmek için

1. **Seç** modunda, dönüştürmek istediğiniz nesneyi seçin. Tel çerçeve yer paylaşımı nesnenin seçili olduğunu gösterir.

2. **Özellikler** penceresinde, **döndürme**, **Ölçek**ve **çeviri** özellikleri için değerler belirtin.

   > [!IMPORTANT]
   > **Döndürme** özelliği için, üç eksenin her biri etrafında döndürme derecesini belirtin. Döndürmeler sırayla uygulandığından önce x ekseni, sonra y ekseni ve sonra da z ekseni açısından bir döndürme planladığınızdan emin olun.

   Modelleme araçlarını kullanarak, dönüştürmeleri hızlı ancak kesin olmayan bir şekilde oluşturabilirsiniz. Nesne özelliklerini ayarlayarak, dönüştürmeleri kesin ancak hızlı olmayan bir şekilde belirtebilirsiniz. İstediğiniz dönüştürmelere "yeteri kadar" yaklaşmak için modelleme araçlarını kullanmanızı ve ardından özellik değerlerinde ince ayar yapmanızı öneririz.

   İşleyicileri kullanmayı istemiyorsanız, serbest biçim modunu etkinleştirebilirsiniz. **Model Düzenleyicisi** araç çubuğunda, serbest biçim modunu etkinleştirmek (veya devre dışı bırakmak) için **betikler**, **Araçlar**, **serbest biçimli düzenleme** ' yi seçin. Serbest biçim modunda, işleyici üzerindeki bir nokta yerine herhangi bir tasarım yüzeyi noktasında düzenleme yapmaya başlayabilirsiniz. Serbest biçim modunda, değiştirmek istemediklerinizi kilitleyerek bazı eksenlerde yapılacak değişiklikleri kısıtlayabilirsiniz. **Model Düzenleyicisi Modu** araç çubuğunda **Lock X**, **Lock Y**ve **Z** Lock düğmelerinin herhangi bir birleşimini seçin.

   Kılavuza uydur işlevini kullanarak nesnelerle çalışmayı daha kullanışlı bulabilirsiniz. Kılavuza Yaslama özelliğini etkinleştirmek (veya devre dışı bırakmak) için, **Model Düzenleyicisi Modu** araç çubuğunda **yasla** ' yı seçin. Kılavuza uydur etkinleştirildiğinde, çeviri, döndürme ve ölçeklendirme dönüştürmeleri önceden tanımlı aralıklarla sınırlandırılır.

### <a name="working-with-the-pivot-point"></a>Pivot noktası ile çalışma
 Pivot noktası nesnenin döndürme ve ölçeklendirme merkezini tanımlar. Döndürme ve ölçeklendirme dönüşümlerinden nasıl etkilendiğini değiştirmek için bir nesnenin özet noktasını değiştirebilirsiniz. Özet modunu etkinleştirmek (veya devre dışı bırakmak) için, **Model Düzenleyicisi Modu** araç çubuğunda **Özet modu** ' nu seçin. Pivot modu etkin olduğunda, seçili nesnenin pivot noktasında küçük bir eksen göstergesi görünür. Ardından, Özet noktasını düzenlemek için **çeviri** ve **döndürme** araçlarını kullanabilirsiniz.

 Özet noktasının nasıl kullanılacağını gösteren bir gösterim için bkz. [nasıl yapılır: 3B modelin pivot noktasını değiştirme](../designers/how-to-modify-the-pivot-point-of-a-3-d-model.md).

### <a name="world-and-local-modes"></a>Dünya ve yerel modları
 Çeviri ve döndürme, nesnenin yerel koordinat sisteminde (veya *Yerel başvuru çerçevesi*) ya da dünyanın koordinat sisteminde (ya da *Dünya başvuru çerçevesi*) oluşabilir. Dünya başvuru çerçevesi nesnenin dönüşünden bağımsızdır. Yerel mod varsayılandır. Dünya modunu etkinleştirmek (veya devre dışı bırakmak) için, **Model Düzenleyicisi Modu** araç çubuğunda, **worldlocal** düğmesini seçin.

### <a name="modifying-objects"></a><a name="ModifyingObjects"></a> Nesneleri değiştirme
 Köşelerini, kenarlarını ve yüzeylerini taşıyarak veya silerek bir 3B nesnenin şeklini değiştirebilirsiniz. Varsayılan olarak, Model Düzenleyicisi *nesne modundadır*ve tüm nesneleri seçip dönüştürebilmenizi sağlayabilirsiniz. Noktaları, kenarları veya yüzeyleri seçmek için uygun seçim modunu seçin. **Model Düzenleyicisi Modu** araç çubuğunda **seçim modları**' nı seçin ve istediğiniz modu seçin.

 Çıkarmayla veya alt bölümlere ayırmayla ek köşeler oluşturabilirsiniz. Çıkarma bir yüzün köşelerini (aynı düzlemli bir yüzler kümesi) çoğaltır ve yüz çoğaltılmış köşelerle bağlı kalır. Alt bölümlere ayırma, önceden bir tane olan yüzeyden birçok yüzey oluşturmak için köşeler ekler. Yeni yüzler oluşturmak için, biri özgün yüzün ortasına ve biri de her bir kenarın ortasına olmak üzere yeni köşeler eklenir ve sonra bunlar orijinal köşelerle birleştirilir. Eklenen yüzlerin sayısı, orijinal yüzdeki köşelerin sayısına eşittir. Her iki durumda da, nesnenin geometrisini değiştirmek için yeni köşeleri çevirebilir, döndürebilir ve ölçeklendirebilirsiniz.

##### <a name="to-extrude-a-face-from-an-object"></a>Bir nesneden bir yüzü çıkarmak için

1. Yüz seçimi modunda, çıkarmak istediğiniz yüzü seçin.

2. **Model Düzenleyicisi** araç çubuğunda **betikler**, **Araçlar**, **Yükselt**' i seçin.

##### <a name="to-subdivide-faces"></a>Yüzleri alt bölümlere ayırmak için

1. Yüz seçimi modunda, alt bölümlere ayırmak istediğiniz yüzleri seçin. Alt bölüm yeni kenar verileri oluşturduğundan, tüm yüzeyleri aynı anda alt bölümlere ayırmak yüzler bitişik olduğunda daha tutarlı sonuçlar verir.

2. **Model Düzenleyicisi** araç çubuğunda betikler, **Araçlar**, alt **kod**öğesini **seçin.**

   Ayrıca yüzeyleri üçgenlere bölebilir, nesneleri birleştirebilir ve çokgen seçimlerini yeni nesnelere dönüştürebilirsiniz. Üçgenlere bölme, üçgen olmayan bir yüz, en uygun sayıda üçgene dönüştürülecek şekilde ek kenarlar oluşturur; ancak ek geometrik ayrıntı sağlamaz. Birleştirme işlemi, seçili nesneleri tek bir nesne halinde birleştirir. Yeni nesneler bir çokgen seçiminden oluşturulabilir.

##### <a name="to-triangulate-a-face"></a>Bir yüzü üçgenlere bölmek için

1. Yüz seçimi modunda, üçgenlere bölmek istediğiniz yüzü seçin.

2. **Model Düzenleyicisi** araç çubuğunda **betikler**, **Araçlar**, **üçgenlere ayır**öğesini seçin.

##### <a name="to-merge-objects"></a>Nesneleri birleştirmek için

1. Nesne seçimi modunda, birleştirmek istediğiniz nesneleri seçin.

2. **Model Düzenleyicisi** araç çubuğunda **betikler**, **Araçlar**ve **birleştirme nesneleri**' ni seçin.

##### <a name="to-create-an-object-from-a-polygon-selection"></a>Çokgen seçiminden bir nesne oluşturmak için

1. Yüz seçimi modunda yeni bir nesne oluşturmak istediğiniz yüzleri seçin.

2. **Model Düzenleyicisi** araç çubuğunda, **betikler**, **Araçlar**, **Çokgen seçiminden yeni nesne oluştur**' u seçin.

### <a name="working-with-materials-and-shaders"></a>Malzemeler ve gölgelendiriciler ile çalışma
 Bir nesnenin görünümü, sahnedeki aydınlatma etkileşimi ve nesnenin malzemesi ile belirlenir. Malzemeler, yüzeyin farklı ışık türlerine nasıl tepki verdiğini açıklayan özelliklerle ve nesne yüzeyindeki her pikselin son rengini ışıklandırma bilgisine, doku eşlemelerine, normal eşlemelere ve diğer verilere göre hesaplayan bir gölgelendirici programla tanımlanır.

 Model Düzenleyicisi şu varsayılan malzemeleri sağlar:

|Malzeme|Description|
|--------------|-----------------|
|Işıklandırılmamış|Benzetimli aydınlatma olmadan bir yüzeyi işler.|
|Lambert|Benzetimli ortam aydınlatması ve yayınık aydınlatma ile bir yüzey işler.|
|Phong|Benzetimli ortam aydınlatması, yayınık aydınlatma ve yansımalı vurgular ile bir yüzeyi işler.|

 Bu malzemelerin her biri nesnenin yüzeyine tek bir doku uygular. Malzemeyi kullanan her nesne için farklı bir doku ayarlayabilirsiniz.

 Belirli bir nesnenin sahnedeki farklı ışık kaynaklarına verdiği tepkiyi değiştirmek için, malzemeyi kullanan diğer nesnelerden bağımsız olarak malzemenin aydınlatma özelliklerini değiştirebilirsiniz. Bu tabloda genel aydınlatma özellikleri açıklanmaktadır:

|Aydınlatma Özelliği|Description|
|-----------------------|-----------------|
|Ortam|Yüzeyin ortam aydınlatmasından nasıl etkilendiğini açıklar.|
|Yayınık|Yüzeyin yönlü ve nokta ışıklardan nasıl etkilendiğini açıklar.|
|Yayımlatıcı|Yüzeyin, diğer aydınlatmalardan bağımsız olarak ışığı nasıl yaydığını açıklar.|
|Yansımalı|Yüzeyin yönlü ve nokta ışıkları nasıl yansıttığını açıklar.|
|Yansımalı Güç|Yansımalı vurguların genişliğini ve yoğunluğunu açıklar.|

 Bir malzemenin neyi desteklediğine bağlı olarak aydınlatma özelliklerini, dokuları ve diğer verileri değiştirebilirsiniz. **Seç** modunda, malzemesini değiştirmek istediğiniz nesneyi seçin ve ardından **Özellikler** penceresinde, **materialambtıcı**, **materialdağıt**, **materialeunalsel**, **materialspecsel**, **MaterialSpecularPower**veya diğer kullanılabilir özelliğini değiştirin. Bir malzeme, özellikleri **Doku1** ile **Texture8**arasında ardışık olarak adlandırılan sekiz dokuya kadar ortaya bulunabilir.

 Bir nesneden tüm malzemeleri kaldırmak için, **Model Düzenleyicisi** araç çubuğunda **betikler**, **malzemeler**, **malzemeleri kaldır**' ı seçin.

 3-b sahnedeki nesnelere uygulayabileceğiniz özel gölgelendirici malzemeleri oluşturmak için **gölgelendirici tasarımcısını** kullanabilirsiniz. Özel gölgelendirici malzemeleri oluşturma hakkında daha fazla bilgi için bkz. [Gölgelendirici Tasarımcısı](../designers/shader-designer.md). Bir nesneye özel gölgelendirici malzemesini uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir gölgelendiriciyi 3-b modele uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

### <a name="scene-management"></a>Sahne yönetimi
 Sahneleri nesnelerin bir hiyerarşisi olarak yönetebilirsiniz. Birden fazla nesne hiyerarşik bir şekilde düzenlendiğinde, üst öğe düğümünün herhangi bir çeviri, ölçek veya döndürme işlemi alt öğelerini de etkiler. Bu, temel nesnelerden karmaşık nesneler veya sahneler oluşturmak istediğinizde kullanışlıdır.

 Sahne hiyerarşisini görüntülemek ve sahne düğümlerini seçmek için **Belge Anahattı** penceresini kullanabilirsiniz. Anahatta bir düğüm seçtiğinizde özelliklerini değiştirmek için **Özellikler** penceresini kullanabilirsiniz.

 Gerek birini diğerlerinin üst öğesi yaparak, gerekse üst öğe gibi davranan bir yer tutucu düğümünün altında eşdüzeyler olarak birlikte gruplandırarak nesnelerin bir hiyerarşisini oluşturabilirsiniz.

##### <a name="to-create-a-hierarchy-that-has-a-parent-object"></a>Üst nesnesi olan bir hiyerarşi oluşturmak için

1. **Seç** modunda iki veya daha fazla nesne seçin. İlk seçtiğiniz öğe üst nesne olur.

2. **Model Düzenleyicisi** araç çubuğunda **betikler**, **sahne yönetimi**, **üst öğeye Ekle**seçeneklerini belirleyin.

##### <a name="to-create-a-hierarchy-of-sibling-objects"></a>Eşdüzeyli nesnelerin hiyerarşisini oluşturmak için

1. **Seç** modunda iki veya daha fazla nesne seçin. Bir yer tutucu nesne oluşturulur ve onların üst nesnesi haline gelir.

2. **Model Düzenleyicisi** araç çubuğunda **betikler**, **sahne yönetimi**, **Grup Oluştur**' u seçin.

   Model Düzenleyicisi, ilk seçilen nesneyi (üst öğe haline gelen) tanımlamak için beyaz tel çerçeve kullanır. Seçimdeki diğer nesneler mavi bir tel çerçeveye sahiptir. Varsayılan olarak, yer tutucu düğümleri görüntülenmez. Yer tutucu düğümlerini görüntülemek için, **Model Düzenleyicisi** araç çubuğunda **betikler**, **sahne yönetimi**, **yer tutucu düğümlerini göster**' i seçin. Yer tutucu düğümleriyle, yer tutucu olmayan nesnelerle çalıştığınız gibi çalışabilirsiniz.

   İki nesne arasındaki üst-alt öğe ilişkilendirmesini kaldırmak için, alt nesneyi seçin ve ardından **Model Düzenleyicisi** araç çubuğunda **komut dosyaları**, **sahne yönetimi**, **üst öğeden ayır**' ı seçin. Üst nesne ile alt nesneyi ayırdığınızda, alt nesne sahnede bir kök nesne olur.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

|Komut|Klavye kısayolları|
|-------------|------------------------|
|**Seçme** moduna geçiş yap|Ctrl+G, Gtrl+Q<br /><br /> S|
|**Yakınlaştırma** moduna geç|Ctrl+G, Ctrl+Z<br /><br /> Z|
|**Pan** moduna geç|Ctrl+G, Ctrl+P<br /><br /> K|
|Tümünü seç|Ctrl+A|
|Geçerli seçimi sil|Sil|
|Geçerli seçimi iptal et|Esc|
|Yakınlaştır|Fare tekerleği ileriye doğru<br /><br /> Ctrl+Fare tekerleği ileriye doğru<br /><br /> Shift+Fare tekerleği ileriye doğru<br /><br /> Ctrl+PageUp<br /><br /> Artı İşareti (+)|
|Uzaklaştır|Fare tekerleği geriye doğru<br /><br /> Ctrl+Fare tekerleği geriye doğru<br /><br /> Shift+Fare tekerleği geriye doğru<br /><br /> Ctrl+PageDown<br /><br /> Eksi İşareti (-)|
|Kamerayı yukarı kaydır|PageDown|
|Kamerayı aşağı kaydır|PageUp|
|Kamerayı sola kaydır|Fare tekerleği sol<br /><br /> Ctrl+PageDown|
|Kamerayı sağa kaydır|Fare tekerleği sağ<br /><br /> Ctrl+PageDown|
|Modelin üst kısmını görüntüle|Ctrl+L, Ctrl+T<br /><br /> T|
|Modelin alt kısmını görüntüle|Ctrl+L, Ctrl+U|
|Modelin sol tarafını görüntüle|Ctrl+L, Ctrl+L|
|Modelin sağ tarafını görüntüle|Ctrl+L, Ctrl+R|
|Modelin önünü görüntüle|Ctrl+L, Ctrl+F|
|Modelin arkasını görüntüle|Ctrl+L, Ctrl+B|
|Nesneyi pencere içinde çerçevele|F|
|Tel çerçeve modunu aç/kapat|Ctrl+L, Ctrl+W|
|Kılavuza uydurmayı aç/kapat|Ctrl+G, Ctrl+N|
|Pivot modunu aç/kapat|Ctrl+G, Ctrl+V|
|X ekseni kısıtlamasını aç/kapat|Ctrl+L, Ctrl+X|
|Y ekseni kısıtlamasını aç/kapat|Ctrl+L, Ctrl+Y|
|Z ekseni kısıtlamasını aç/kapat|Ctrl+L, Ctrl+Z|
|Çeviri moduna geçiş yap|Ctrl+G, Ctrl+W<br /><br /> W|
|Ölçek moduna geçiş yap|Ctrl+G, Ctrl+E<br /><br /> E|
|Döndürme moduna geçiş yap|Ctrl+G, Ctrl+R<br /><br /> R|
|Nokta seçme moduna geçiş yap|Ctrl+L, Ctrl+1|
|Kenar seçme moduna geçiş yap|Ctrl+L, Ctrl+2|
|Yüz seçme moduna geçiş yap|Ctrl+L, Ctrl+3|
|Nesne seçme moduna geçiş yap|Ctrl+L, Ctrl+4|
|Yörünge (kamera) moduna geçiş yap|Ctrl+G, Ctrl+O|
|Sahnede sonraki nesneyi seç|Tab|
|Sahnede önceki nesneyi seç|Shift+Sekme Tuşu|
|Geçerli araca bağlı olarak seçili nesneyi düzenle.|Ok tuşları|
|Geçerli işleyiciyi devre dışı bırak|Q|
|Kamerayı döndür|Alt + Farenin sol düğmesiyle sürükleme|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Oyunlar ve Uygulamalar için 3B Varlıklarla Çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Dokular ve görüntüler, 3-b modeller ve gölgelendirici efektleri gibi grafik varlıklarıyla çalışmak için kullanabileceğiniz araçlara genel bir bakış sağlar.|
|[Görüntü Düzenleyicisi](../designers/image-editor.md)|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Dokularla ve görüntülerle çalışmak için görüntü düzenleyicisinin nasıl kullanılacağını açıklar.|
|[Gölgelendirici Tasarımcısı](../designers/shader-designer.md)|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Gölgelendiricilerle çalışmak için Gölgelendirici Tasarımcısının nasıl kullanılacağını açıklar.|
