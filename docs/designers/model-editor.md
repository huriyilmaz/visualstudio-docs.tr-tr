---
title: Model Düzenleyicisi
description: modelleme araçları tarafından oluşturulan sıfırdan veya daha karmaşık 3b modellerden 3b modelleri görüntülemek, oluşturmak ve değiştirmek için Visual Studio Model düzenleyicisi ile nasıl çalışacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 04/12/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.3dscene
- vs.graphics.modelviewer
ms.assetid: 5edf1a30-9307-43c3-9b8b-831217be0104
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 32c5a26a529318bfe2e828de8fdb5529152907b3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051488"
---
# <a name="model-editor"></a>Model düzenleyicisi

bu belgede, 3b modelleri görüntülemek, oluşturmak ve değiştirmek için Visual Studio **modeli düzenleyicisi** ile nasıl çalışılacağı açıklanmaktadır.

Sıfırdan temel 3B modeller oluşturmak veya tam özellikli 3D modelleme araçları kullanılarak oluşturulmuş daha karmaşık 3B modelleri görüntülemek ve değiştirmek için **model düzenleyicisini** kullanabilirsiniz.

## <a name="supported-formats"></a>Desteklenen biçimler

**Model Düzenleyicisi** , DirectX uygulama geliştirmede kullanılan çeşitli 3B model biçimlerini destekler:

|Biçim Adı|Dosya Uzantısı|Desteklenen İşlemler (Görüntüleme, Düzenleme, Oluşturma)|
|-----------------| - | - |
|AutoDesk FBX Değişim Dosyası|*.fbx*|Görüntüleme, Düzenleme, Oluşturma|
|Collada DAE Dosyası|*.dae*|Görüntüleme, Düzenleme (Collada DAE dosyalarında yapılan değişiklikler FBX biçimi kullanılarak kaydedilir.)|
|OBJ|*. obj*|Görüntüleme, Düzenleme (OBJ dosyalarında yapılan değişiklikler FBX biçimi kullanılarak kaydedilir.)|

## <a name="get-started"></a>başlarken

bu bölümde, Visual Studio C++ projenize ve başlamanıza yardımcı olacak diğer temel bilgilere nasıl 3b model ekleneceği açıklanmaktadır.

> [!NOTE]
> 3B sahneler (. fbx dosyaları) gibi grafik öğelerinin otomatik derleme tümleştirmesi yalnızca C++ projeleri için desteklenir.

### <a name="to-add-a-3d-model-to-your-project"></a>Projenize 3D model eklemek için

1. grafiklerle çalışmanız gereken Visual Studio bileşenin yüklü olduğundan emin olun. Bileşen, **görüntü ve 3B model düzenleyicileri** olarak adlandırılır.

   yüklemek için **araçlar**  >  menüsünü ve menü çubuğundan araçlar **al** ' ı seçerek Visual Studio Yükleyicisi açın ve ardından **ayrı bileşenler** sekmesini seçin. **oyunlar ve grafikler** kategorisi altındaki **görüntü ve 3b model düzenleyicileri** bileşenini seçin ve ardından **değiştir**' i seçin.

   ![Görüntü ve 3B model düzenleyicileri bileşeni](media/image-3d-model-editors-component.png)

   Bileşen yüklenmeye başlıyor.

2. **Çözüm Gezgini** içinde, görüntüsünü eklemek istediğiniz C++ projesinin kısayol menüsünü açın ve ardından   >  **Yeni öğe** Ekle ' yi seçin.

3. **Yeni öğe Ekle** Iletişim kutusundaki **grafik** kategorisi altında **3B sahne (. fbx)** öğesini seçin.

   ![3B sahneye yeni öğe Ekle iletişim kutusu seçili](media/add-new-3d-scene.png)

   > [!NOTE]
   > **Yeni öğe Ekle** Iletişim kutusunda **grafik** kategorisini görmüyorsanız ve **resim ve 3B model düzenleyicileri** bileşeni yüklüyse, grafik öğeleri proje türü için desteklenmez.

4. Model dosyasının **adını** girin ve ardından **Ekle**' yi seçin.

### <a name="axis-orientation"></a>Eksen yönlendirme

Visual Studio, 3b eksenin her yönünü destekler ve onu destekleyen model dosya biçimlerinden eksen yönlendirme bilgilerini yükler. eksen yönü belirtilmediyse Visual Studio, varsayılan olarak doğru el ile koordinat sistemini kullanır. **Eksen göstergesi** , tasarım yüzeyinin sağ alt köşesindeki geçerli eksen yönünü gösterir. **Eksen göstergesinde**, kırmızı x eksenini, yeşil ise y eksenini temsil eder ve mavi, z eksenini temsil eder.

### <a name="begin-your-3d-model"></a>3B modelinize başlayın

Model düzenleyicisinde, her yeni nesne her zaman, model düzenleyicide yerleşik olan temel 3B şekillerden (veya temel *elemanlar*) biri olarak başlar. Yeni ve benzersiz nesneler oluşturmak için, görünüme bir temel öğe ekler ve sonra da köşeleriyle oynayarak şeklini değiştirirsiniz. Karmaşık şekiller için, kalıp veya alt bölüm kullanarak ek köşeler ekler ve sonra bunlarda değişiklik yaparsınız. Sahneye temel bir nesne ekleme hakkında daha fazla bilgi için bkz. [3D nesneler oluşturma ve içeri aktarma](#Adding3DObjects). Bir nesneye daha fazla köşe ekleme hakkında daha fazla bilgi için bkz. [nesneleri değiştirme](#ModifyingObjects).

## <a name="work-with-the-model-editor"></a>Model Düzenleyicisi ile çalışma

Aşağıdaki bölümlerde, 3B modellerle çalışmak için Model Düzenleyicisi 'nin nasıl kullanılacağı açıklanır.

### <a name="model-editor-toolbars"></a>Model Düzenleyicisi araç çubukları

Model Düzenleyicisi araç çubukları 3B modellerle çalışmanıza yardımcı olan komutlar içerir.

model düzenleyicisi 'nin durumunu etkileyen komutlar, ana Visual Studio penceresindeki **model düzenleyicisi modu** araç çubuğunda bulunur. Modelleme araçları ve komut dosyalı komutlar, Model Düzenleyicisi tasarım yüzeyinde **Model Düzenleyicisi** araç çubuğunda bulunur.

**Model Düzenleyicisi Modu** araç çubuğu şöyledir:

![Model görüntüleyici kalıcı araç çubuğu.](../designers/media/digit-mre-modal-toolbar.png)

Bu tabloda, **Model Düzenleyicisi Modu** araç çubuğunda, soldan sağa göründükleri sırada listelenen öğeler açıklanmaktadır.

|Araç Çubuğu Öğesi|Açıklama|
|------------------|-----------------|
|**Seç**|Etkin seçim moduna bağlı olarak görünümdeki noktaların, kenarların, yüzeylerin ya da nesnelerin seçimini etkinleştirir.|
|**Kaydır**|3B sahnenin pencere çerçevesine göre taşınmasını sağlar. Kaydırmak için görünümde bir nokta seçip dolaştırın.<br /><br /> **Seçim** modunda, **Dikey Çevir** modunu geçici olarak etkinleştirmek için **CTRL** tuşuna basılı tutabilirsiniz.|
|**Zoom**|Pencere çerçevesine göre daha az ya da daha fazla görünüm ayrıntısının görüntülenmesini sağlar. **Yakınlaştırma** modu ' nda sahnede bir nokta seçin ve yakınlaştırmak için sağa veya aşağı taşıyın ya da uzaklaştırmak için sola veya yukarı kaydırın.<br /><br /> **Seç** modunda, **CTRL** tuşunu basılı tutarken fare tekerleğini kullanarak yakınlaştırıp uzaklaştırabilirsiniz.|
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
|**Gerçek zamanlı Işleme modu**|gerçek zamanlı işleme etkinleştirildiğinde, kullanıcı eylemi gerçekleştirilmediğinde bile tasarım yüzeyini yeniden çizer Visual Studio. Bu mod, zamanla değişen gölgelendiriciler ile çalıştığınızda kullanışlıdır.|
|**Kılavuzu Aç/Kapat**|Bu öğe etkinleştirildiğinde bir kılavuz görüntülenir. Aksi takdirde kılavuz görüntülenmez.|
|**Araç Kutusu**|Ayrıca **araç kutusunu** gösterir veya gizler.|
|**Belge Anahattı**|Alternatif olarak **Belge Anahattı** penceresini gösterir veya gizler.|
|**Özellikler**|Alternatif olarak **Özellikler** penceresini gösterir veya gizler.|
|**Gelişmiş**|Gelişmiş komutları ve seçenekleri içerir.<br /><br /> **Grafik altyapıları**<br /><br /> **D3D11 ile işleme**<br /> Model Düzenleyicisi tasarım yüzeyini işlemek için Direct3D 11 kullanır.<br /><br /> **D3D11WARP ile işleme**<br /> Model Düzenleyicisi tasarım yüzeyini işlemek için Direct3D 11 Windows Gelişmiş Pikselleştirme Platformu'nu (WARP) kullanır.<br /><br /> **Sahne yönetimi**<br /><br /> **İçeri Aktar**<br /> Başka bir 3B model dosyasındaki nesneleri geçerli sahneye aktarır.<br /><br /> **Üst öğeye Ekle**<br /> Çoklu seçilen nesnelerin ilkini, kalan seçili nesnelerin üst öğesi olarak ayarlar.<br /><br /> **Üst öğeden ayır**<br /> Seçili nesneyi üst öğesinden ayırır. Seçili nesne, sahnede bir *kök nesne* olur. Kök nesnenin bir üst nesnesi olmaz.<br /><br /> **Grup Oluşturma**<br /> Seçili nesneleri eşdüzey nesneler olarak gruplandırır.<br /><br /> **Nesneleri Birleştir**<br /> Seçili nesneleri tek bir nesne halinde birleştirir.<br /><br /> **Çokgen seçiminden yeni nesne oluştur**<br /> Seçilen yüzeyleri geçerli nesneden kaldırır ve bu yüzeyleri içeren yeni bir nesneyi sahneye ekler.<br /><br /> **Araçlar**<br /><br /> **Çokgen dikey sargı**<br /> Seçili çokgenleri çevirir ve böylece sargı sırasını ve yüzey normalini tersine çevirir.<br /><br /> **Tüm animasyonu kaldır**<br /> Nesnelerden animasyon verilerini kaldırır.<br /><br /> **Üçgenlere ayır**<br /> Seçili nesneyi üçgenlere dönüştürür.<br /><br /> **Görünüm**<br /><br /> Arkayüz Ayrılması<br /> Arka yüz ayırmayı etkinleştirir veya devre dışı bırakır.<br /><br /> **Kare hızı**<br /> Tasarım yüzeyinin sağ üst köşesinde kare hızını görüntüler. Kare hızı, saniye başına çizilen çerçeve sayısıdır.<br /><br /> Bu seçenek, **gerçek zamanlı Işleme modu** seçeneğini etkinleştirdiğinizde yararlıdır.<br /><br /> **Tümünü göster**<br /> Sahnedeki tüm nesneleri gösterir. Bu, her nesnenin **Hidden** özelliğini **false** olarak sıfırlar.<br /><br /> **Yüz normalleri göster**<br /> Her bir yüzeyin normalini gösterir.<br /><br /> **Eksik malzemeleri göster**<br /> Atanmış malzemeleri olmayan nesneler üzerinde özel bir doku gösterir.<br /><br /> **Özeti göster**<br /> Etkin seçimin Özet noktasında 3B Eksen işaretinin görüntülenmesini etkinleştirilir veya devre dışı bırakır.<br /><br /> **Yer tutucu düğümlerini göster**<br /> Yer tutucu düğümlerini gösterir. Nesneleri gruplandırdığınızda bir yer tutucu düğümü oluşturulur.<br /><br /> **Köşe normalleri göster**<br /> Her köşenin normalini gösterir. **İpucu:**  Son betiği yeniden çalıştırmak için **betikler** düğmesini seçebilirsiniz.|

**Model Düzenleyicisi** araç çubuğu şöyledir:

![Model Görüntüleyicisi araç çubuğu](../designers/media/digit-mre-toolbar.png)

Sonraki tabloda, **Model Düzenleyicisi** araç çubuğunda yukarıdan aşağıya göründükleri sırada listelenen öğeler açıklanmaktadır.

|Araç Çubuğu Öğesi|Açıklama|
|------------------|-----------------|
|**Çevir**|Seçimi taşır.|
|**Ölçeklendirme**|Seçimin boyutunu değiştirir.|
|**Boyut**|Seçimi döndürür.|
|**Noktayı seçin**|Bir nesnedeki noktaları tek tek seçmek için **seçim modunu** ayarlar.|
|**Kenar seçin**|Bir nesne üzerinde bir kenar (iki köşe arasında bir çizgi) seçmek için **seçim modunu** ayarlar.|
|**Yüz Seçme**|Bir **nesnede yüz** seçmek için Seçim modunu ayarlar.|
|**Nesne Seçme**|Bir nesnenin **tamamını seçmek** için Seçim modunu ayarlar.|
|**Yükselt**|Ek bir yüzey oluşturur ve bunu seçili yüze bağlar.|
|**Alt canlı**|Seçilen her yüzeyi birden fazla yüzeye böler. Yeni yüzler oluşturmak için, biri özgün yüzün ortasına ve biri de her bir kenarın ortasına olmak üzere yeni köşeler eklenir ve sonra bunlar orijinal köşelerle birleştirilir. Eklenen yüzlerin sayısı, orijinal yüzdeki köşelerin sayısına eşittir.|

### <a name="control-the-view"></a>Görünümü denetleme

3D sahne, konuma ve yönlendirmeye sahip bir sanal kamera olarak düşünilen görünüme göre işlenir. Konumu ve yönü değiştirmek için Model Düzenleyicisi Modu araç çubuğundaki **görünüm denetimlerini** kullanın.

Aşağıdaki tabloda birincil görünüm denetimleri açıklanmaktadır.

|Görünüm Denetimi|Açıklama|
|------------------|-----------------|
|**Kaydır**|Pencere çerçevesine göre 3D sahnenin hareketini sağlar. Kaydırmak için görünümde bir nokta seçip dolaştırın.<br /><br /> Seçim **modunda,** Pan modunu geçici olarak etkinleştirmek için **Ctrl tuşuna** **basabilirsiniz.**|
|**Zoom**|Pencere çerçevesine göre daha az ya da daha fazla görünüm ayrıntısının görüntülenmesini sağlar. Yakınlaştırma **modunda,** sahnenin bir noktasını seçin ve sonra yakınlaştırmak için sağ veya aşağı hareket ettirin ya da uzaklaştırın ya da sola ya da yukarıya gelin.<br /><br /> Seç **modunda** fare tekerleğini kullanarak Ctrl tuşunu basılı tutarak yakınlaştırabilir veya **uzaklaştırabilirsiniz.**|
|**Yörünge**|Görünümü seçili nesnenin çevresinde dairesel bir yola yerleştirir. Hiçbir nesne seçili değilse, yol görünüm başlangıcında ortalanır. **Not:**  Bu modun, Ortografik **projeksiyon etkinleştirildiğinde** hiçbir etkisi olmaz.|
|**Çerçeve Nesnesi**|Seçili nesneyi, görünümün ortasında yer alacak şekilde çerçeveler.|

Görünüm sanal kamera ile belirlenir, ancak aynı zamanda bir projeksiyon ile de tanımlanır. Projeksiyon, görünümdeki şekillerin ve nesnelerin tasarım yüzeyinde piksellere nasıl dönüştürüldüğünü tanımlar. Model Düzenleyicisi **araç çubuğunda** Perspektif  veya Görsel **projeksiyon'ı seçebilirsiniz.**

|Projeksiyon|Açıklama|
|----------------|-----------------|
|**Perspektif**|Perspektif projeksiyonunda, bakış açısından uzakta olan nesneler boyut olarak daha küçük görünür ve en sonunda uzaktaki bir noktaya doğru birleşir.|
|**Ortografik**|Ortografik projeksiyonda, bakış açısına olan uzaklıklarına bakılmaksızın nesneler aynı boyutta görünür. Bir yakınlaşma görüntüsü olmaz. Görsel **projeksiyon etkinleştirildiğinde,** görünümü rastgele konumlandırmak **için Orbit** modunu kullanasınız.|

3D sahneyi bilinen bir konumdan ve açıdan görüntülemeyi yararlı bulabilirsiniz. Örneğin, iki benzer sahneyi karşılaştırmak istediğiniz zaman. Bu senaryo için, Model Düzenleyicisi önceden tanımlı çeşitli görünümler sağlar. Önceden tanımlanmış bir görünüm kullanmak için **Model** Düzenleyicisi Modu araç çubuğunda Görünüm'e tıklayın ve ardından istediğiniz önceden tanımlanmış görünümü (ön, geri, sol, sağ, üst veya alt) seçin. Bu görünümlerde, sanal kamera doğrudan sahnenin başlangıç noktasına doğru bakar. Örneğin, Üst Görünümü **seçerseniz,** sanal kamera sahnenin kökenine doğrudan yukarıdan bakabilirsiniz.

### <a name="view-additional-geometry-details"></a>Ek geometri ayrıntılarını görüntüleme

Bir 3B nesneyi veya sahneyi daha iyi anlamak için köşe başına normaller, yüz başına normaller, etkin seçimin pivot noktaları ve diğer ayrıntılar gibi ek geometri ayrıntılarını görüntüebilirsiniz. Bunları etkinleştirmek veya devre dışı bırakmak için **Model Düzenleyicisi araç** çubuğunda Betikler Görünümü'ni ve ardından istediğiniz seçeneği   >  seçin.

### <a name="create-and-import-3d-objects"></a>3D nesne oluşturma ve içeri aktarma <a name="Adding3DObjects"></a>

Görünüme önceden tanımlanmış bir 3B şekil eklemek için Araç Kutusunda istediğiniz şekli seçin ve tasarım yüzeyine taşıma. Yeni şekiller sahnenin başlangıcına yerleştirilir. Model Düzenleyicisi yedi şekil sağlar: **Külah,** **Küp,** **Silindir,** **Disk,** **Düzlem,** **Sphere** ve **Çaydanlık.**

Bir dosyadan 3D nesnesini içeri aktarın, **Model** Düzenleyicisi araç çubuğunda Gelişmiş Sahne Yönetimi İçeri Aktarma >'ı seçin ve ardından içeri   >    >   aktarmayı istediğiniz dosyayı belirtin.

### <a name="transform-objects"></a>Dönüşüm nesneleri

Bir nesneyi *Dönüştürme,* Ölçeklendirme ve **Çeviri** **özelliklerini** değiştirerek **dönüştürebilirsiniz.** *Döndürme,* bir nesneyi, pivot noktası tarafından tanımlanan x ekseni, y ekseni ve z ekseni çevresinde başarılı döndürmeler uygulayarak yönlendirer. Her döndürme belirtiminin sırasıyla x, y ve z olmak üzere üç bileşeni vardır ve bu bileşenler derece olarak belirtilir. **Ölçeklendirme,** nesneyi belirli bir faktöre göre esneterek pivot noktasının ortası olan bir veya daha fazla eksen üzerinde yeniden boyutlandırılır. *Çeviri,* bir nesneyi pivot noktası yerine üst öğeye göre 3 boyutlu bir alanda bularak elde eder.

Modelleme araçlarını kullanarak veya özellikleri ayarlayarak bir nesneyi dönüştürebilirsiniz.

#### <a name="transform-an-object-by-using-modeling-tools"></a>Modelleme araçlarını kullanarak nesneyi dönüştürme

1. Seç  modunda dönüştürmek istediğiniz nesneyi seçin. Tel çerçeve yer paylaşımı nesnenin seçili olduğunu gösterir.

2. Model Düzenleyicisi **araç çubuğunda** Çevir, **Ölçeklendir** veya **Döndür** **aracını** seçin. Seçili nesne için bir çeviri, ölçeklendirme veya döndürme işleyicisi görüntülenir.

3. Dönüştürmeyi gerçekleştirmek için işleyiciyi kullanın. Çeviri ve ölçeklendirme dönüşümlerinde işleyici bir eksen göstergesidir. Bir kerede bir eksen değiştirebilir veya göstergenin ortasındaki beyaz küpü kullanarak aynı anda tüm eksenleri değiştirebilirsiniz. Döndürme için işleyici x eksenine (kırmızı), y eksenine (yeşil) ve z eksenine (mavi) karşılık gelen renk kodlu dairelerden oluşan bir küredir. İstediğiniz döndürmeyi oluşturmak için her ekseni tek tek değiştirmeniz gerekir.

#### <a name="transform-an-object-by-setting-its-properties"></a>Özelliklerini ayarerek nesneyi dönüştürme

1. Seç  modunda dönüştürmek istediğiniz nesneyi seçin. Tel çerçeve yer paylaşımı nesnenin seçili olduğunu gösterir.

2. Özellikler **penceresinde** Döndürme, Ölçeklendirme ve **Çeviri** **özellikleri** için **değerleri** belirtin.

    > [!IMPORTANT]
    > Rotation **özelliği** için üç eksenin her biri için döndürme derecesini belirtin. Döndürmeler sırayla uygulandığından önce x ekseni, sonra y ekseni ve sonra da z ekseni açısından bir döndürme planladığınızdan emin olun.

Modelleme araçlarını kullanarak, dönüştürmeleri hızlı ancak kesin olmayan bir şekilde oluşturabilirsiniz. Nesne özelliklerini ayarlayarak, dönüştürmeleri kesin ancak hızlı olmayan bir şekilde belirtebilirsiniz. İstediğiniz dönüştürmelere "yeteri kadar" yaklaşmak için modelleme araçlarını kullanmanızı ve ardından özellik değerlerinde ince ayar yapmanızı öneririz.

İşleyicileri kullanmayı istemiyorsanız, serbest biçim modunu etkinleştirebilirsiniz. Serbest biçim **modunu etkinleştirmek (veya** **devre** dışı bırakmak) için Model Düzenleyicisi araç çubuğunda Betik Araçları Serbest Biçimli  >    >   Düzenleme'yi seçin. Serbest biçim modunda, işleyici üzerindeki bir nokta yerine herhangi bir tasarım yüzeyi noktasında düzenleme yapmaya başlayabilirsiniz. Serbest biçim modunda, değiştirmek istemediklerinizi kilitleyerek bazı eksenlerde yapılacak değişiklikleri kısıtlayabilirsiniz. Model Düzenleyicisi **Modu araç çubuğunda** X'i Kilitle, **Y'yi** Kilitle ve **Z'yi** Kilitle **düğmelerinin herhangi bir bileşimini** seçin.

Kılavuza uydur işlevini kullanarak nesnelerle çalışmayı daha kullanışlı bulabilirsiniz. Kılavuza **yasla özelliğini** etkinleştirmek **(veya devre dışı** bırakmak) için Model Düzenleyicisi Modu araç çubuğunda Yasla'ya tıklayın. Kılavuza uydur etkinleştirildiğinde, çeviri, döndürme ve ölçeklendirme dönüştürmeleri önceden tanımlı aralıklarla sınırlandırılır.

### <a name="work-with-the-pivot-point"></a>Pivot noktasıyla çalışma

Pivot noktası nesnenin döndürme ve ölçeklendirme merkezini tanımlar. Döndürme ve ölçeklendirme dönüşümlerinden nasıl etkilendiğini değiştirmek için bir nesnenin özet noktasını değiştirebilirsiniz. Model Düzenleyicisi **Modu araç çubuğunda,** özet modunu **etkinleştirmek (veya** devre dışı) için Özet Modu'nu seçin. Pivot modu etkin olduğunda, seçili nesnenin pivot noktasında küçük bir eksen göstergesi görünür. Daha sonra Çeviri ve **Döndürme araçlarını** **kullanarak** özet noktasını işebilirsiniz.

Özet noktasını kullanmayı gösteren bir tanıtım için bkz. [Nasıl 3D](../designers/how-to-modify-the-pivot-point-of-a-3-d-model.md)modelin pivot noktasını değiştirme.

### <a name="world-and-local-modes"></a>Dünya ve yerel modları

Çeviri ve döndürme, nesnenin yerel koordinat sisteminde (veya yerel başvuru *çerçevesinde)* veya dünyanın koordinat sisteminde (veya dünya başvuru *çerçevesi) oluşabilir.* Dünya başvuru çerçevesi nesnenin dönüşünden bağımsızdır. Yerel mod varsayılandır. Dünya modunu etkinleştirmek (veya devre dışı bırakmak) için **Model Düzenleyicisi Modu** araç çubuğunda **WorldLocal düğmesini** seçin.

### <a name="modify-objects"></a>Nesneleri değiştirme <a name="ModifyingObjects"></a>

Köşelerini, kenarlarını ve yüzlerini hareket ettirerek veya silerek 3D nesnesinin şeklini değiştirebilirsiniz. Varsayılan olarak Model Düzenleyicisi nesne *modundadır,* böylece tüm nesneleri seçebilirsiniz ve dönüştürebilirsiniz. Noktaları, kenarları veya yüzeyleri seçmek için uygun seçim modunu seçin. Model **Düzenleyicisi Modu araç çubuğunda** Seçim **modları'nu** ve ardından istediğiniz modu seçin.

Çıkarmayla veya alt bölümlere ayırmayla ek köşeler oluşturabilirsiniz. Çıkarma bir yüzün köşelerini (aynı düzlemli bir yüzler kümesi) çoğaltır ve yüz çoğaltılmış köşelerle bağlı kalır. Alt bölümlere ayırma, önceden bir tane olan yüzeyden birçok yüzey oluşturmak için köşeler ekler. Yeni yüzler oluşturmak için, biri özgün yüzün ortasına ve biri de her bir kenarın ortasına olmak üzere yeni köşeler eklenir ve sonra bunlar orijinal köşelerle birleştirilir. Eklenen yüzlerin sayısı, orijinal yüzdeki köşelerin sayısına eşittir. Her iki durumda da, nesnenin geometrisini değiştirmek için yeni köşeleri çevirebilir, döndürebilir ve ölçeklendirebilirsiniz.

#### <a name="to-extrude-a-face-from-an-object"></a>Bir nesneden bir yüzü çıkarmak için

1. Yüz seçimi modunda, çıkarmak istediğiniz yüzü seçin.

2. Model Düzenleyicisi **araç çubuğunda Betik** Araçları **Ekstrude'yi**  >    >  **seçin.**

#### <a name="to-subdivide-faces"></a>Yüzleri alt bölümlere ayırmak için

1. Yüz seçimi modunda, alt bölümlere ayırmak istediğiniz yüzleri seçin. Alt bölüm yeni kenar verileri oluşturduğundan, tüm yüzeyleri aynı anda alt bölümlere ayırmak yüzler bitişik olduğunda daha tutarlı sonuçlar verir.

2. Model Düzenleyicisi **araç çubuğunda** Betik Araçları   >    >  **AltDivide'yi seçin.**

Ayrıca yüzeyleri üçgenlere bölebilir, nesneleri birleştirebilir ve çokgen seçimlerini yeni nesnelere dönüştürebilirsiniz. Üçgenlere bölme, üçgen olmayan bir yüz, en uygun sayıda üçgene dönüştürülecek şekilde ek kenarlar oluşturur; ancak ek geometrik ayrıntı sağlamaz. Birleştirme işlemi, seçili nesneleri tek bir nesne halinde birleştirir. Yeni nesneler bir çokgen seçiminden oluşturulabilir.

#### <a name="triangulate-a-face"></a>Bir yüzü üçgene alıtma

1. Yüz seçimi modunda, üçgenlere bölmek istediğiniz yüzü seçin.

2. Model Düzenleyicisi **araç çubuğunda Betik** Araçları **Üçgene**  >    >  **Alın'ı seçin.**

#### <a name="merge-objects"></a>Nesneleri birleştirme

1. Nesne seçimi modunda, birleştirmek istediğiniz nesneleri seçin.

2. Model Düzenleyicisi **araç çubuğunda Betik** Araçları Nesneleri   >  **Birleştir'i**  >  **seçin.**

#### <a name="create-an-object-from-a-polygon-selection"></a>Çokgen seçiminden nesne oluşturma

1. Yüz seçimi modunda yeni bir nesne oluşturmak istediğiniz yüzleri seçin.

2. Model Düzenleyicisi **araç çubuğunda Betik** Araçları ÇokGen   >    >  **Seçiminden Yeni Nesne Oluştur'a tıklayın.**

### <a name="work-with-materials-and-shaders"></a>Malzemeler ve gölgelendiricilerle çalışma

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

Bir malzemenin neyi desteklediğine bağlı olarak aydınlatma özelliklerini, dokuları ve diğer verileri değiştirebilirsiniz. Seç **modunda,** malzemesini değiştirmek istediğiniz nesneyi seçin ve  ardından Özellikler penceresinde **MaterialAmbient**, **MaterialDiffuse**, **MaterialEmissive**, **MaterialSpecular**, **MaterialSpecularPower** veya diğer kullanılabilir özelliği değiştirin. Bir malzeme, özellikleri **Texture1'den** Texture8'e sıralı olarak adlandırılmış sekiz dokuyu **ortaya çıkarır.**

Bir nesneden tüm malzemeleri kaldırmak için Model Düzenleyicisi araç çubuğunda **Betik** Malzemeleri **Malzemelerini**  >    >  **Kaldır'ı seçin.**

Gölgelendirici **Tasarımcısını kullanarak** 3D sahnenizin nesnelerine uygulayabilecek özel gölgelendirici malzemeleri oluşturabilirsiniz. Özel gölgelendirici malzemeleri oluşturma hakkında bilgi için bkz. [Gölgelendirici Tasarımcısı.](../designers/shader-designer.md) Bir nesneye özel gölgelendirici malzeme uygulama hakkında bilgi için bkz. Nasıl [yapılır: 3D modele](../designers/how-to-apply-a-shader-to-a-3-d-model.md)gölgelendirici uygulama.

### <a name="scene-management"></a>Sahne yönetimi

Sahneleri nesnelerin bir hiyerarşisi olarak yönetebilirsiniz. Birden fazla nesne hiyerarşik bir şekilde düzenlendiğinde, üst öğe düğümünün herhangi bir çeviri, ölçek veya döndürme işlemi alt öğelerini de etkiler. Bu, temel nesnelerden karmaşık nesneler veya sahneler oluşturmak istediğinizde kullanışlıdır.

Sahne hiyerarşisini görüntülemek **ve sahne** düğümlerini seçmek için Belge Ana Hat penceresini kullanabilirsiniz. Ana hatta bir düğüm seçin, özelliklerini değiştirmek **için Özellikler** penceresini kullanabilirsiniz.

Gerek birini diğerlerinin üst öğesi yaparak, gerekse üst öğe gibi davranan bir yer tutucu düğümünün altında eşdüzeyler olarak birlikte gruplandırarak nesnelerin bir hiyerarşisini oluşturabilirsiniz.

#### <a name="create-a-hierarchy-that-has-a-parent-object"></a>Üst nesnesi olan bir hiyerarşi oluşturma

1. Seç **modunda** iki veya daha fazla nesne seçin. İlk seçtiğiniz öğe üst nesne olur.

2. Model Düzenleyicisi **araç çubuğunda Betikler** Sahne Yönetimi **Üst**  >  **Öğeye**  >  **Ekle'yi seçin.**

#### <a name="create-a-hierarchy-of-sibling-objects"></a>Ibling nesnelerinin hiyerarşisini oluşturma

1. Seç **modunda** iki veya daha fazla nesne seçin. Bir yer tutucu nesne oluşturulur ve onların üst nesnesi haline gelir.

2. Model Düzenleyicisi **araç çubuğunda Betikler** **Sahne** Yönetimi  >  **Grup**  >  **Oluştur'a tıklayın.**

Model Düzenleyicisi, ilk seçilen nesneyi (üst öğe haline gelen) tanımlamak için beyaz tel çerçeve kullanır. Seçimdeki diğer nesneler mavi bir tel çerçeveye sahiptir. Varsayılan olarak, yer tutucu düğümleri görüntülenmez. Yer tutucu düğümlerini görüntülemek için Model Düzenleyicisi araç **çubuğunda Betikler** Sahne **Yönetimi** Yer Tutucu  >    >  **Düğümlerini Göster'i seçin.** Yer tutucu düğümleriyle, yer tutucu olmayan nesnelerle çalıştığınız gibi çalışabilirsiniz.

İki nesne arasındaki üst-alt ilişkilendirmeyi kaldırmak için, alt nesneyi seçin ve  **ardından Model** Düzenleyicisi araç çubuğunda Betikler Sahne Yönetimi Üst nesneden  >    >  **ayır'ı seçin.** Üst nesne ile alt nesneyi ayırdığınızda, alt nesne sahnede bir kök nesne olur.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

|Komut|Klavye kısayolları|
|-------------| - |
|Seçim **moduna** geçme|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **Q**<br /><br /> **S**|
|Yakınlaştırma **moduna** geçme|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **Z**<br /><br /> **Z**|
|Kaydırma **moduna** geçme|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **P**<br /><br /> **K**|
|Tümünü seç|**Ctrl tuşunu basılı tutarak** + **A**|
|Geçerli seçimi sil|**Silme**|
|Geçerli seçimi iptal et|**Kaçış** (**Esc**)|
|Yakınlaştır|**Fare tekerleği ileriye doğru**<br /><br /> **Ctrl tuşunu basılı tutarak** + **Fare tekerleği ileri**<br /><br /> **Shift ile kaydırma** + **Fare tekerleği ileri**<br /><br /> **Ctrl tuşunu basılı tutarak** + **PageUp**<br /><br /> Artı İşareti ( **+** )|
|Uzaklaştır|**Fare tekerleği geriye doğru**<br /><br /> **Ctrl tuşunu basılı tutarak** + **Fare tekerleği geriye doğru**<br /><br /> **Shift ile kaydırma** + **Fare tekerleği geriye doğru**<br /><br /> **Ctrl tuşunu basılı tutarak** + **PageDown**<br /><br /> Eksi İşareti ( **-** )|
|Kamerayı yukarı kaydır|**PageDown**|
|Kamerayı aşağı kaydır|**PageUp**|
|Kamerayı sola kaydır|**Fare tekerleği sol**<br /><br /> **Ctrl tuşunu basılı tutarak** + **PageDown**|
|Kamerayı sağa kaydır|**Fare tekerleği sağ**<br /><br /> **Ctrl tuşunu basılı tutarak** + **PageDown**|
|Modelin üst kısmını görüntüle|**Ctrl tuşunu basılı tutarak** + **L,** **Ctrl** + **T**<br /><br /> **T**|
|Modelin alt kısmını görüntüle|**Ctrl tuşunu basılı tutarak** + **L,** **Ctrl** + **U**|
|Modelin sol tarafını görüntüle|**Ctrl tuşunu basılı tutarak** + **L,** **Ctrl** + **L**|
|Modelin sağ tarafını görüntüle|**Ctrl tuşunu basılı tutarak** + **L,** **Ctrl** + **R**|
|Modelin önünü görüntüle|**Ctrl tuşunu basılı tutarak** + **L,** **Ctrl** + **F**|
|Modelin arkasını görüntüle|**Ctrl tuşunu basılı tutarak** + **L,** **Ctrl** + **B**|
|Nesneyi pencere içinde çerçevele|**F**|
|Tel çerçeve modunu aç/kapat|**Ctrl tuşunu basılı tutarak** + **L,** **Ctrl** + **W**|
|Kılavuza uydurmayı aç/kapat|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **N**|
|Pivot modunu aç/kapat|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **V**|
|X ekseni kısıtlamasını aç/kapat|**Ctrl tuşunu basılı tutarak** + **L,** **Ctrl** + **X**|
|Y ekseni kısıtlamasını aç/kapat|**Ctrl tuşunu basılı tutarak** + **L,** **Ctrl** + **Y**|
|Z ekseni kısıtlamasını aç/kapat|**Ctrl tuşunu basılı tutarak** + **L,** **Ctrl** + **Z**|
|Çeviri moduna geçiş yap|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **W**<br /><br /> **W**|
|Ölçek moduna geçiş yap|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **E**<br /><br /> **E**|
|Döndürme moduna geçiş yap|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **R**<br /><br /> **R**|
|Nokta seçme moduna geçiş yap|**Ctrl tuşunu basılı tutarak** + **L**, **Ctrl** + **1**|
|Kenar seçme moduna geçiş yap|**Ctrl tuşunu basılı tutarak** + **L**, **Ctrl** + **2**|
|Yüz seçme moduna geçiş yap|**Ctrl tuşunu basılı tutarak** + **L**, **Ctrl** + **3**|
|Nesne seçme moduna geçiş yap|**Ctrl tuşunu basılı tutarak** + **L**, **Ctrl** + **4**|
|Yörünge (kamera) moduna geçiş yap|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **O**|
|Sahnede sonraki nesneyi seç|**Sekme**|
|Sahnede önceki nesneyi seç|**Shift ile kaydırma** + **Sekme**|
|Geçerli araca bağlı olarak seçili nesneyi düzenle.|Ok  tuşları|
|Geçerli işleyiciyi devre dışı bırak|**S**|
|Kamerayı döndür|**Alt** + **Farenin** sol düğmesiyle sürükleme|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Oyunlar ve uygulamalar için 3D varlıklarla çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|Dokular ve görüntüler, 3B modeller ve gölgelendirici etkileri gibi grafik varlıklarıyla çalışmak için kullanabileceğiniz Visual Studio araçlarına genel bir bakış sağlar.|
|[Görüntü Düzenleyicisi](../designers/image-editor.md)|Dokular ve görüntülerle çalışmak Visual Studio Görüntü Düzenleyicisi'nin nasıl kullanılabını açıklar.|
|[Gölgelendirici Tasarımcısı](../designers/shader-designer.md)|Gölgelendiriciler ile çalışmak için Visual Studio Gölgelendirici Tasarımcısı'nın nasıl kullanılacı açık bir şekilde açık bir şekilde anlattır.|
