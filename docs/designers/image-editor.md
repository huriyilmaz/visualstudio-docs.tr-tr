---
title: Görüntü Düzenleyici
ms.date: 08/10/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.imageeditor
- vs.graphics.imageeditor
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd7d9aed75876b47a6574d46b226f5baec336883
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589324"
---
# <a name="image-editor"></a>Görüntü düzenleyicisi

Bu makalede doku ve resim kaynaklarını görüntülemek ve değiştirmek için Visual Studio **Görüntü Düzenleyicisi** ile nasıl çalışılacağı açıklanır.

DirectX uygulama geliştirmede kullanılan zengin doku ve görüntü biçimleri türleriyle çalışmak için **görüntü düzenleyicisini** kullanabilirsiniz. Bu, popüler görüntü dosyası biçimleri ve renk kodlamaları, alfa kanalları ve MıP eşleme gibi özellikler ve DirectX 'in desteklediği yüksek oranda sıkıştırılmış, donanım hızlandırmalı doku biçimlerinin çoğunu destekler.

## <a name="supported-formats"></a>Desteklenen biçimler

**Görüntü Düzenleyicisi** aşağıdaki görüntü biçimlerini destekler:

|Biçim adı|Dosya Adı Uzantısı|
|-----------------| - |
|Taşınabilir Ağ Grafikleri|*. png*|
|JPEG|*. jpg*, *. jpeg*, *. jpe*, *. JI*|
|Doğrudan çizim yüzeyi|*. DDS*|
|Grafik Değişim Biçimi|*Resimler*|
|Biteş|*. bmp*, *. dib*|
|Etiketli resim dosyası biçimi|*. tif*, *. tiff*|
|TGA (Targa)|*. tga*|

## <a name="get-started"></a>Kullanmaya başlayın

Bu bölümde, Visual Studio projenize bir görüntü ekleme ve gereksinimlerinize göre yapılandırma açıklanmaktadır.

### <a name="add-an-image-to-your-project"></a>Projenize resim ekleme

1. **Çözüm Gezgini**, görüntüsünü eklemek istediğiniz projenin kısayol menüsünü açın ve ardından > **Yeni öğe** **Ekle** ' yi seçin.

2. **Yeni öğe Ekle** iletişim kutusunda, **yüklü**altında **grafikler**' i seçin ve ardından görüntü için uygun bir dosya biçimi seçin.

   > [!NOTE]
   > **Yeni öğe Ekle** Iletişim kutusunda **grafik** kategorisini görmüyorsanız, **görüntü ve 3B model düzenleyicileri** bileşenini yüklemeniz gerekebilir. İletişim kutusunu kapatın ve **Visual Studio yükleyicisi**açmak için menü çubuğundan **Araçlar ve Özellikler al** > **Araçlar** ' ı seçin. **Ayrı bileşenler** sekmesini seçin ve ardından **Oyunlar ve grafikler** kategorisi altındaki **görüntü ve 3B model düzenleyicileri** bileşenini seçin. **Değiştir**'i seçin.
   >
   > ![Görüntü ve 3B model düzenleyicileri bileşeni](media/image-3d-model-editors-component.png)

   Gereksinimlerinize göre bir dosya biçimi seçme hakkında daha fazla bilgi için bkz. [görüntü biçimini seçme](#choose-the-image-format).

3. Görüntü dosyasının **adını** ve oluşturulmasını istediğiniz **konumu** belirtin.

4. Seçin **Ekle** düğmesi.

### <a name="choose-the-image-format"></a>Görüntü biçimini seçin

Görüntüyü nasıl kullanacağınızı planladığınıza bağlı olarak, bazı dosya biçimleri diğerlerinden daha uygun olabilir. Örneğin, bazı biçimler ihtiyacınız olan bir özelliği (örneğin, saydamlık veya belirli bir renk biçimi) desteklemeyebilir. Bazı biçimler, planladığınız görüntü içeriği türü için uygun sıkıştırmayı sağlamayabilir.

Aşağıdaki bilgiler, gereksinimlerinizi karşılayan bir görüntü biçimi seçmenize yardımcı olabilir:

**Bit eşlem resmi (. bmp)**

Bit eşlem resmi biçimi. 24 bit rengi destekleyen sıkıştırılmamış bir görüntü biçimi. Bit eşlem biçimi saydamlığı desteklemez.

**GIF resmi (. gif)**

Grafik Değişim Biçimi (GIF) resim biçimi. En fazla 256 rengi destekleyen, LZW ile sıkıştırılmış, kayıpsız bir görüntü biçimi. Önemli miktarda renk ayrıntısı olan fotoğraflar ve görüntüler için uygun olmayan ancak yüksek düzeyde renk uyumluluğu olan düşük renkli görüntüler için iyi sıkıştırma oranları sağlar.

**JPG resmi (. jpg)**

Birleşik Fotoğraf Uzmanları Grubu (JPEG) resim biçimi. 24 bit rengi destekleyen ve yüksek düzeyde renk uyumluluğu olan görüntülerin genel amaçlı sıkıştırmaya uygun olan, yüksek oranda sıkıştırılmış, kayıplı bir görüntü biçimi.

**PNG resmi (. png)**

Taşınabilir Ağ Grafikleri (PNG) resim biçimi. 24 bit rengi ve alfa saydamlığını destekleyen, orta düzeyde sıkıştırılmış, kayıpsız bir görüntü biçimi. Doğal ve yapay görüntüler için uygundur, ancak JPG veya GIF gibi kayıplı biçimler kadar iyi sıkıştırma oranları sağlamaz.

**TIFF resmi (. tif)**

Etiketli resim dosyası biçimi (TIFF veya TıF) resim biçimi. Birkaç sıkıştırma şemasını destekleyen esnek bir görüntü biçimi.

**DDS dokusu (. DDS)**

DirectDraw yüzeyi (DDS) doku biçimi. 24 bit renk ve alfa saydamlığını destekleyen, yüksek oranda sıkıştırılmış, kayıplı bir doku biçimi. Sıkıştırma oranları 8:1 kadar yüksek olabilir. Grafik donanımında açılan S3 doku sıkıştırmasını temel alır.

**TGA resmi (. TGA)**

Truevision grafik bağdaştırıcısı (TGA) görüntü biçimi (Targa olarak da bilinir). Hem renk eşlemeli (renk paleti), hem de 24 bit renge ve Alfa saydamlığına sahip doğrudan renk görüntülerini destekleyen, RLE sıkıştırılmış, kayıpsız bir resim biçimi. Önemli miktarda renk ayrıntısı olan fotoğraflar ve görüntüler için uygun değil, ancak aynı renklerin uzun yayılmasına sahip görüntüler için iyi sıkıştırma oranları sağlar.

### <a name="configure-the-image"></a>Görüntüyü yapılandırma

Oluşturduğunuz görüntüyle çalışmaya başlamadan önce, varsayılan yapılandırmasını değiştirebilirsiniz. Örneğin boyutlarını veya kullandığı renk biçimini değiştirebilirsiniz. Görüntünün bu ve diğer özelliklerinin nasıl yapılandırılacağı hakkında bilgi için bkz. [görüntü özellikleri](#image-properties).

> [!NOTE]
> Çalışmanızı kaydetmeden önce, belirli bir renk biçimini kullanmak istiyorsanız **renk biçimi** özelliğini ayarladığınızdan emin olun. Dosya biçimi sıkıştırmayı destekliyorsa, dosyayı ilk kez kaydettiğinizde veya **farklı kaydet**' i seçtiğinizde sıkıştırma ayarlarını yapabilirsiniz.

## <a name="work-with-the-image-editor"></a>Görüntü Düzenleyicisi ile çalışma

Bu bölümde, doku ve görüntüleri değiştirmek için **Görüntü Düzenleyicisi** 'nin nasıl kullanılacağı açıklanmaktadır.

**Görüntü düzenleyicisinin** durumunu etkileyen komutlar, **Görüntü Düzenleyicisi Modu** araç çubuğunda gelişmiş komutlarla birlikte bulunur. Araç çubuğu, **Görüntü Düzenleyicisi** tasarım yüzeyinin en üst kenarı üzerinde bulunur. Çizim araçları **, görüntü Düzenleyicisi tasarım yüzeyinin** en sol kenarında bulunan **görüntü düzenleyici** araç çubuğunda bulunur.

### <a name="image-editor-mode-toolbar"></a>Görüntü düzenleyici modu araç çubuğu

![Visual Studio 'da görüntü düzenleyici modu araç çubuğu](../designers/media/digit-tre-modal-toolbar.png)

Aşağıdaki tabloda, **Görüntü Düzenleyicisi Modu** araç çubuğunda, soldan sağa göründükleri sırada listelenen öğeler açıklanmaktadır:

|Araç Çubuğu Öğesi|Açıklama|
|------------------|-----------------|
|**Seçin**|Bir görüntünün dikdörtgen bölgesini seçmeye izin vermez. Bir bölge seçtikten sonra, onu kesebilir, kopyalayabilir, taşıyabilir, ölçeklendirebilir, döndürebilir, çevirebilir veya silebilirsiniz. Etkin bir seçim olduğunda, çizim araçları yalnızca seçili bölgeyi etkiler.|
|**Düzensiz seçim**|Görüntüde düzensiz bir bölgenin seçilmesine izin vermez. Bir bölge seçtikten sonra, onu kesebilir, kopyalayabilir, taşıyabilir, ölçeklendirebilir, döndürebilir, çevirebilir veya silebilirsiniz. Etkin bir seçim olduğunda, çizim araçları yalnızca seçili bölgeyi etkiler.|
|**Değnek seçimi**|Bir görüntünün benzer renkli bir bölgesini seçmeye izin vermez. *Tolerans*— diğer bir deyişle, benzer olarak kabul ettikleri bitişik renkler arasındaki en büyük fark — daha küçük veya daha geniş bir benzer renk aralığı içerecek şekilde yapılandırılabilir. Bir bölge seçtikten sonra, onu kesebilir, kopyalayabilir, taşıyabilir, ölçeklendirebilir, döndürebilir, çevirebilir veya silebilirsiniz. Etkin bir seçim olduğunda, çizim araçları yalnızca seçili bölgeyi etkiler.|
|**Pan**|Görüntünün pencere çerçevesine göre taşınmasını sağlar. **Kaydırma** modu ' nda görüntüde bir nokta seçin ve sonra taşıyın.<br /><br /> **CTRL** tuşuna basarak ve basılı tutarak, **kaydırma** modunu geçici olarak etkinleştirebilirsiniz.|
|**Yakınlaştırma**|Pencere çerçevesine göre daha fazla veya daha az görüntü ayrıntısı görüntülenmesini sağlar. **Yakınlaştırma** modu ' nda görüntüde bir nokta seçin ve yakınlaştırmak için sağa veya aşağı taşıyın ya da uzaklaştırmak için sola ya da yukarı kaydırın.<br /><br /> Fare tekerleğini kullanırken veya artı işaretine ( **+** ) veya eksi işaretine ( **-** ) basarak, **CTRL** tuşunu basılı tutarak yakınlaştırıp uzaklaştırabilirsiniz.|
|**Gerçek boyuta Yakınlaştır**|Görüntünün pikselleri ve ekranın pikselleri arasında bir 1:1 ilişkisi kullanarak görüntüyü görüntüler.|
|**Sığacak kadar Yakınlaştır**|Pencere çerçevesindeki tam görüntüyü görüntüler.|
|**Genişliği Yakınlaştır**|Pencere çerçevesindeki görüntünün tam genişliğini görüntüler.|
|**Kılavuz**|Piksel sınırlarını gösteren kılavuzu etkinleştirilir veya devre dışı bırakır. Görüntüye yakınlaştırana kadar ızgara görünmeyebilir.|
|**Sonraki MıP düzeyini görüntüle**|Bir MIP eşleme zincirindeki bir sonraki daha büyük MıP düzeyini etkinleştirir. Etkin MıP düzeyi tasarım yüzeyinde görüntülenir. Bu öğe yalnızca MıP düzeylerine sahip dokularla kullanılabilir.|
|**Önceki MıP düzeyini görüntüle**|Bir MIP eşleme zincirindeki bir sonraki küçük MıP düzeyini etkinleştirir. Etkin MıP düzeyi tasarım yüzeyinde görüntülenir. Bu öğe yalnızca MıP düzeylerine sahip dokularla kullanılabilir.|
|**Kırmızı kanal**<br /><br /> **Yeşil kanal**<br /><br /> **Mavi kanal**<br /><br /> **Alfa kanalı**|Belirli renk kanalını etkinleştirilir veya devre dışı bırakır. **Note:**  Renk kanallarını sistematik olarak etkinleştirerek veya devre dışı bırakarak, bir veya daha fazla sorunla ilgili sorunları yalıtabilirsiniz. Örneğin, yanlış alfa saydamlığı belirleyebilirsiniz.|
|**Arka plan**|Görüntünün saydam kısımları aracılığıyla arka planın görüntülenmesini mümkün veya devre dışı bırakır. Aşağıdaki seçeneklerden birini belirleyerek arka planın nasıl görüntüleneceğini yapılandırabilirsiniz:<br /><br /> **Tahtası**<br /> Arka planı bir dama tahtası stili olarak göstermek için belirtilen arka plan rengiyle birlikte yeşil bir renk kullanır. Bu seçeneği, görüntünün saydam parçalarını daha belirgin hale getirmenize yardımcı olması için kullanabilirsiniz.<br /><br /> Beyaz arka plan<br /> Arka planı göstermek için beyaz rengi kullanır.<br /><br /> Siyah arka plan<br /> Arka planı göstermek için siyahın rengini kullanır.<br /><br /> Arka plana animasyon ekle<br /> Dama tahtası deseninin yavaş olması. Bu seçeneği, görüntünün saydam parçalarını daha belirgin hale getirmenize yardımcı olması için kullanabilirsiniz.|
|**Veri Erişimi**|Alternatif olarak **Özellikler** penceresini açar veya kapatır.|
|**Gelişmiş**|Ek komutlar ve seçenekler içerir.<br /><br /> **Filtreler**<br /><br /> Birkaç ortak görüntü filtresi sağlar: **siyah ve beyaz**, **bulanıklaştırma**, **parlak on**, **koyulaştırma**, **kenar algılama**, **kabarık**, **renkleri ters çevir**, **Ripple**, **sepıa tonu**ve **keskinleştirme**.<br /><br /> **Grafik altyapıları**<br /><br /> **D3D11 ile işleme**<br /> **Görüntü Düzenleyicisi** tasarım yüzeyini Işlemek için Direct3D 11 ' i kullanır.<br /><br /> **D3D11WARP ile işleme**<br /> , **Resim Düzenleyicisi** tasarım yüzeyini Işlemek için Direct3D 11 Windows Gelişmiş Tarama Platformu (warp) kullanır.<br /><br /> **Araçlar**<br /><br /> **Yatay Çevir**<br /> Görüntüyü yatay veya x, eksenin etrafında yerleştir.<br /><br /> **Dikey Çevir**<br /> Görüntüyü dikey veya y ekseni etrafında dönüştürün.<br /><br /> **MIPS oluştur**<br /> Bir görüntü için MıP düzeyleri oluşturur. MıP düzeyleri zaten mevcutsa, en büyük MıP düzeyinden yeniden oluşturulur. Daha küçük MıP düzeylerinde yapılan tüm değişiklikler kaybolur. Oluşturmuş olduğunuz MıP düzeylerini kaydetmek için, görüntüyü kaydetmek üzere *. DDS* biçimini kullanmanız gerekir.<br /><br /> **Görünümü**<br /><br /> **Kare hızı**<br /> Etkinleştirildiğinde, tasarım yüzeyinin sağ üst köşesindeki kare hızını görüntüler. Kare hızı, saniye başına çizilen çerçeve sayısıdır. **İpucu:** Son komutu yeniden çalıştırmak için **Gelişmiş** düğmesini seçebilirsiniz.|

### <a name="image-editor-toolbar"></a>Görüntü Düzenleyicisi araç çubuğu

![Görüntü Düzenleyicisi araç çubuğu](../designers/media/digit-tre-toolbar.png)

Aşağıdaki tabloda, en üstten alta göründükleri sırada listelenen **Görüntü Düzenleyicisi** araç çubuğundaki öğeler açıklanmaktadır:

|Araç Çubuğu Öğesi|Açıklama|
|------------------|-----------------|
|**Düğmede**|Diğer adı olan bir vuruş çizmek için etkin renk seçimini kullanır. **Özellikler** penceresinde konturun rengini ve kalınlığını ayarlayabilirsiniz.|
|**Fırça**|, İzin verilen bir kenar yumuşatma çizmek için etkin renk seçimini kullanır. **Özellikler** penceresinde konturun rengini ve kalınlığını ayarlayabilirsiniz.|
|**Boya tabancası**|, Görüntüyle birlikte karışan ve zaman içerisinde daha fazla doygun bir kenar yumuşatma içeren bir vuruş çizmek için etkin renk seçimini kullanır. **Özellikler** penceresinde konturun rengini ve kalınlığını ayarlayabilirsiniz.|
|**Damlalığı**|Etkin renk seçimini seçili pikselin rengine ayarlar.|
|**Doldurması**|Görüntünün bir bölgesini dolduracak etkin renk seçimini kullanır. Etkilenen bölge, her pikselde aynı renkteki ve aynı rengin kendisi olan piksellerle bağlantılı olan her pikselle birlikte, dolgunun uygulandığı piksel olarak tanımlanır. Dolguyu etkin bir seçim içinde uygulanırsa, etkilenen bölge seçim tarafından sınırlandırılır.<br /><br /> Varsayılan olarak, etkin renk seçimi, Alfa bileşenine göre görüntünün etkilenen bölgesiyle birlikte karıştırılırdı. Etkilenen bölgenin üzerine yazmak üzere etkin renk seçimini kullanmak için, Fill aracını kullanırken **SHIFT** tuşuna basın ve basılı tutun.|
|**Silgi**|Resim bir alfa kanalını destekliyorsa, pikselleri tamamen saydam renge ayarlar. Aksi takdirde, pikselleri etkin arka plan rengine ayarlar.|
|**Çizgi**, **dikdörtgen**, **yuvarlatılmış dikdörtgen**, **elips**|Görüntüde bir şekil çizer. Ana hattın rengini ve kalınlığını **Özellikler** penceresinde ayarlayabilirsiniz.<br /><br /> Eşit genişliğe ve yüksekliğe sahip bir temel öğe çizmek için, çizerken **SHIFT** tuşuna basın ve basılı tutun.|
|**Metin**|Metin çizmek için ön plan rengi seçimini kullanır. Arka plan rengi, arka plan rengi seçimine göre belirlenir. Saydam bir arka plan için, arka plan rengi seçiminin alfa değeri 0 olmalıdır. Metin bölgesi etkin olsa da, metnin bir kenar yumuşatma ile çizilip çizilmeyeceğini ayarlayabilir ve **Özellikler** penceresinde metin **değeri**, **yazı tipi**, **Boyut**ve stil —**kalın**, **italik**veya **altı çizili**) ayarlayabilirsiniz. Metin bölgesi artık etkin olmadığında metnin içeriği ve görünümü sonlandırılır.|
|**Boyut**|Görüntüyü saat yönünde 90 derece döndürür.|
|**Kırpma**|Görüntüyü etkin seçime kırpar.|

### <a name="work-with-mip-levels"></a>MıP düzeyleriyle çalışma

Bazı görüntü biçimleri (örneğin, DirectDraw yüzeyi ( *. DDS*), doku alanı ayrıntı düzeyi (Lod) IÇIN MIP düzeylerini destekler. MıP düzeyleri oluşturma ve bunlarla çalışma hakkında daha fazla bilgi için bkz [. nasıl yapılır: MıP düzeyleri oluşturma ve değiştirme](../designers/how-to-create-and-modify-mip-levels.md)

### <a name="work-with-transparency"></a>Saydamlıkla çalışma

Bazı görüntü biçimleri, örneğin, DirectDraw yüzeyi ( *. DDS*), saydamlığı destekler. Kullanmakta olduğunuz araca bağlı olarak saydamlık kullanmanın birkaç yolu vardır. Bir renk seçimine ait saydamlık düzeyini belirtmek için, **Özellikler** penceresinde, renk seçiminin **a** (Alpha) bileşenini ayarlayın.

Aşağıdaki tabloda, saydamlığın nasıl uygulandığını kontrol eden farklı araç türlerinin nasıl bulunduğu açıklanmaktadır:

|Aracı|Açıklama|
|----------|-----------------|
|**Kurşun kalem**, **fırça**, **püskürtme**, **çizgi**, **dikdörtgen**, **yuvarlatılmış dikdörtgen**, **elips**, **metin**|Etkin renk seçimini görüntüyle birlikte Blend için, **Özellikler** penceresinde **Kanallar** özellik grubu ' nu genişletin ve **Alfa** kanalında **Çiz** onay kutusunu ayarlayın ve normal şekilde çizin.<br /><br /> Etkin renk seçimini kullanarak çizim yapmak ve görüntünün Alfa değerini yerinde bırakmak için, **Alfa** kanalının **Çizim** onay kutusunu temizleyin ve normal şekilde çizin.|
|**Doldurması**|Etkin renk seçimini görüntüyle birlikte karıştırmak için, doldurmanız gereken alanı seçmeniz yeterlidir.<br /><br /> Alfa kanalının değeri de dahil olmak üzere etkin renk seçimini kullanmak için, resmin üzerine yazmak için **SHIFT** tuşuna basın ve basılı tutun ve ardından doldurulacak alanı seçin.|

### <a name="image-properties"></a>Görüntü özellikleri

Görüntünün çeşitli özelliklerini belirtmek için **Özellikler** penceresini kullanabilirsiniz. Örneğin, genişliği ve yüksekliği özelliklerini görüntüyü yeniden boyutlandırmak için ayarlayabilirsiniz.

Aşağıdaki tabloda görüntü özellikleri açıklanmaktadır:

|Özellik|Açıklama|
|--------------|-----------------|
|Genişlik|Resmin genişliği.|
|Yükseklik|Resmin yüksekliği.|
|Bit/piksel|Her pikseli temsil eden bit sayısı. Bu özelliğin değeri görüntünün **renk biçimine** bağlıdır.|
|Saydam seçim|Seçim katmanının Alfa değerine bağlı olarak, seçim katmanını ana görüntüyle birlikte karıştırmak için **true** ; Aksi takdirde, **false**. Bu öğe yalnızca Alpha destekleyen görüntülerde kullanılabilir.|
|Biçimi|Görüntünün renk biçimi. Görüntü biçimine bağlı olarak çeşitli renk biçimleri belirtebilirsiniz. Renk biçimi, görüntüde yer alan renk kanalların sayısını ve türünü ve ayrıca çeşitli kanalların boyut ve kodlamasını tanımlar.|
|MIP düzeyi|Etkin MıP düzeyi. Bu öğe yalnızca MıP düzeylerine sahip dokularla kullanılabilir.|
|MİP düzeyi sayısı|Görüntüdeki MıP düzeylerinin toplam sayısı. Bu öğe yalnızca MıP düzeylerine sahip dokularla kullanılabilir.|
|Çerçeve sayısı|Görüntüdeki çerçevelerin toplam sayısı. Bu öğe yalnızca doku dizilerini destekleyen görüntülerde kullanılabilir.|
|Çerçeve|Geçerli çerçeve. Yalnızca ilk çerçeve görüntülenebilir; görüntü kaydedildiğinde diğer tüm çerçeveler kaybolur.|
|Derinlik dilimi sayısı|Görüntüdeki derinlik dilimlerinin toplam sayısı. Bu öğe yalnızca birim dokularını destekleyen görüntülerde kullanılabilir.|
|Derinlik dilimi|Geçerli derinlik dilimi. Yalnızca ilk dilim görüntülenebilir; görüntüyü kaydettiğinizde diğer tüm dilimler kaybedilir.|

> [!NOTE]
> **Döndürme** özelliği tüm araçlar ve seçili bölgeler için geçerli olduğundan, her zaman **Özellikler** penceresinin alt kısmında diğer araç özellikleriyle birlikte görüntülenir. Başka bir seçim veya etkin araç olmadığında tüm görüntü örtük olarak seçildiğinden, **Döndürme ölçütü** her zaman görüntülenir. **Döndürme** özelliği hakkında daha fazla bilgi için bkz. [araç özellikleri](#tool -properties).

### <a name="resize-images"></a>Görüntüleri yeniden boyutlandırma

Bir görüntüyü yeniden boyutlandırmanın iki yolu vardır. Her iki durumda da, **Görüntü Düzenleyicisi** görüntüyü yeniden örneklemek için Bilinear ilişkilendirmeyi kullanır.

- **Özellikler** penceresinde **Genişlik** ve **Yükseklik** özellikleri için yeni değerler belirtin.

- Görüntüyü yeniden boyutlandırmak için görüntünün tamamını seçin ve kenarlık işaretçilerini kullanın.

### <a name="selected-regions"></a>Seçili bölgeler

**Görüntü düzenleyicisinde** seçimler etkin olan görüntünün bölgelerini tanımlar. Etkin bölgeler araçlar ve dönüşümlerinden etkilenir. Etkin bir seçim olduğunda, seçilen bölgenin dışındaki bölgeler çoğu araç ve dönüşümden etkilenmez. Etkin bir seçim yoksa görüntünün tamamı etkin olur.

Çoğu araç (**kurşun kalem**, **fırça**, **püskürtme**, **Fill**, **silgi**ve 2B temel elemanlar) ve dönüşümler (**döndürme**, **kesme**, **renkleri ters**çevirme, **Yatay Çevir**ve **Dikey Çevir**), etkin seçim tarafından kısıtlı veya tanımlı. Ancak bazı araçlar (**damlalık** ve **metin**) ve dönüşümler (**MIPS oluştur**), herhangi bir etkin seçimden etkilenmez. Bu araçlar her zaman tüm görüntünün etkin seçim olduğu gibi davranır.

Bir bölge seçerken, orantılı (kare) seçim yapmak için **SHIFT** tuşuna basılı tutabilirsiniz. Aksi takdirde, seçim kısıtlı değildir.

#### <a name="resize-selections"></a>Seçimleri yeniden boyutlandır

Bir bölge seçtikten sonra seçim işaretçisinin boyutunu değiştirerek onu veya görüntü içeriğini yeniden boyutlandırabilirsiniz. Seçili bölgeyi yeniden boyutlandırırken, seçilen bölgenin yeniden boyutlandırılırken davranışını değiştirmek için aşağıdaki değiştirici tuşları kullanabilirsiniz:

**CTRL** -seçili bölgenin içeriğini yeniden boyutlandırmadan önce kopyalar. Bu, kopya yeniden boyutlandırılırken orijinal görüntüyü bozulmadan bırakır.

**Shift** -Seçili bölgeyi özgün boyutuna göre orantılı olarak yeniden boyutlandırır.

**Alt** -seçim bölgesinin boyutunu değiştirir. Bu, görüntüyü değiştirilmemiş olarak bırakır.

Aşağıdaki tabloda geçerli değiştirici tuş bileşimleri açıklanmaktadır:

|Ctrl|Shift|Alt|Açıklama|
|----------|-----------|---------|-----------------|
||||Seçili bölgenin içeriğini yeniden boyutlandırır.|
||**Karakter**||Seçili bölgenin içeriğini orantılı olarak yeniden boyutlandırır.|
|||**Alternatif**|Seçili bölgeyi yeniden boyutlandırır. Bu, yeni bir seçim bölgesi tanımlar.|
||**Karakter**|**Alternatif**|Seçili bölgeyi orantılı olarak yeniden boyutlandırır. Bu, yeni bir seçim bölgesi tanımlar.|
|**T**|||Seçili bölgenin içeriğini kopyalar ve sonra yeniden boyutlandırır.|
|**T**|**Karakter**||Seçili bölgenin içeriğini kopyalar ve daha sonra orantılı olarak yeniden boyutlandırır.|

### <a name="tool-properties"></a>Araç özellikleri

Bir araç seçiliyken, görüntü nasıl etkilediği hakkındaki ayrıntıları belirtmek için **Özellikler** penceresini kullanabilirsiniz. Örneğin, **kurşun kalem** aracının kalınlığını veya **fırça** aracının rengini ayarlayabilirsiniz.

Hem ön plan rengi hem de arka plan rengi ayarlayabilirsiniz. Her ikisi de Kullanıcı tanımlı opaklık sağlamak için bir alfa kanalını destekler. Ayarlar tüm araçlara uygulanır. Fare kullanıyorsanız sol fare düğmesi ön plan rengine karşılık gelir ve sağ fare düğmesi arka plan rengine karşılık gelir.

Aşağıdaki tabloda araç özellikleri açıklanmaktadır:

|Aracı|Özellikler|
|----------|----------------|
|Tüm araçlar ve seçimler|**Döndürme ölçütü**<br /> Seçim ya da araç efektinin saatin saat yönünde döndürüldüğü miktarı derece cinsinden tanımlar.|
|**Kurşun kalem**, **fırça**, **püskürtme**, **silgi**|**Kalınlığı**<br /> Araçtan etkilenen alanın boyutunu tanımlar.|
|**Metin**|**Kenar yumuşatma**<br /> Daha fazla kenar yumuşatma uygulanmış kenarları olan metni çizer. Bu metin daha yumuşak bir görünüm sağlar.<br /><br /> **Değer**<br /> Çizilecek metin.<br /><br /> **Yazı tipi**<br /> Metni çizmek için kullanılan yazı tipi.<br /><br /> **Boyut**<br /> Metnin boyutu.<br /><br /> **Kalın**<br /> Yazı tipini kalın yapar.<br /><br /> **İtalik**<br /> Yazı tipini italik yapar.<br /><br /> **Çiz**<br /> Yazı tipi altı çizili hale gelir.|
|**2B temel**|**Kenar yumuşatma**<br /> Kenar yumuşatma uygulanmış kenarları olan temel türleri çizer. Böylece daha yumuşak bir görünüm elde edin.<br /><br /> **Kalınlığı**<br /> Temel öğesinin sınırını oluşturan çizginin kalınlığını tanımlar.<br /><br /> **Yarıçap X**<br /> (Yalnızca yuvarlatılmış dikdörtgen) Temel öğesinin üst ve alt kenarları için yuvarlama yarıçapını tanımlar.<br /><br /> **Yarıçap Y**<br /> (Yalnızca yuvarlatılmış dikdörtgen) Temel öğesinin sol ve sağ kenarları için yuvarlama yarıçapını tanımlar.|
|**Kurşun kalem**, **fırça**, **püskürtme**, **2B temel**|**Kanallar**<br /> Görüntüleme ve çizim için belirli renk kanallarını etkinleştirip devre dışı bırakır. Belirli bir renk kanalı için **Görünüm** ayarlandıysa, bu kanal görüntüde görünür; Aksi takdirde, görünür değildir. Belirli bir renk kanalı için **Çizim** ayarlandıysa, bu kanal çizim işlemleri tarafından etkilenir; Aksi takdirde, değildir.|
|**Değnek seçimi**, **dolgusu**|**Payı**<br /> Etkilenen veya seçilen bölgenin bir parçası olarak daha az veya daha fazla benzer renge sahip olduğu için, benzer olarak kabul edildiği bitişik renkler arasındaki en büyük farkı tanımlar. Varsayılan olarak, değer 32 ' dir. Bu, orijinal rengin 32 gölgeler (daha açık veya daha koyu) içindeki bitişik piksellerin bölgenin parçası olarak kabul edildiği anlamına gelir.|

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

|Komut|Klavye kısayolları|
|-------------| - |
|**Seçme** moduna geçiş yap|**S**|
|**Yakınlaştırma** moduna geç|**Z**|
|**Pan** moduna geç|**K**|
|Tümünü seç|**Ctrl**+**A**|
|Geçerli seçimi sil|**Delete**|
|Geçerli seçimi iptal et|**ESC** (kaçış)|
|Yakınlaştır|**Fare tekerleği ileri**+**CTRL**<br /><br /> **Ctrl**+**PageUp**<br /><br /> Artı Işareti ( **+** )|
|Uzaklaştır|**-** **fare tekerleği geriye doğru**<br /><br /> **Ctrl**-**pageaşağı**<br /><br /> Eksi Işareti ( **-** )|
|Görüntüyü yukarı kaydır|**Fare tekerleği geriye doğru**<br /><br /> **Seç**|
|Görüntüyü aşağı kaydır|**Fare tekerleği ileri**<br /><br /> **Seç**|
|Görüntüyü sola kaydır|+**fare tekerleğini geriye doğru** **Kaydır**<br /><br /> **Fare tekerleği sol**<br /><br /> +**Pageaşağı** **Kaydır**|
|Görüntüyü sağa kaydır|+**fare tekerleğini Ileri** **Kaydır**<br /><br /> **Fare tekerleği sağ**<br /><br /> +**PageUp** **Kaydır**|
|Gerçek boyuta Yakınlaştır|**Ctrl**+**0** (sıfır)|
|Görüntüyü pencereye sığdır|**Ctrl**+**G**, **CTRL**+**F**|
|Görüntüyü pencere genişliğine Sığdır|**Ctrl**+**g**, **CTRL**+**ı**|
|Kılavuza geç|**Ctrl**+**g**, **CTRL**+**g**|
|Görüntüyü geçerli seçime Kırp|**Ctrl**+**G**, **CTRL**+**C**|
|Sonrakini görüntüle (daha yüksek ayrıntı) MıP düzeyi|**Ctrl**+**G**, **CTRL**+**6**|
|Öncekini görüntüle (düşük ayrıntı) MıP düzeyi|**Ctrl**+**G**, **CTRL**+**7**|
|Kırmızı renk kanalını değiştirme|**Ctrl**+**G**, **CTRL**+**1**|
|Yeşil renk kanalını aç|**Ctrl**+**G**, **CTRL**+**2**|
|Mavi renk kanalını aç|**Ctrl**+**G**, **CTRL**+**3**|
|Alfa (saydam) kanalını değiştirme|**Ctrl**+**G**, **CTRL**+**4**|
|Alfa dama tahtası düzenine geç|**Ctrl**+**G**, **CTRL**+**B**|
|Düzensiz seçim aracına geç|**L**|
|Değnek seçim aracına geç|**M**|
|Kurşun Kalem aracına geç|**P**|
|Fırça aracına geç|**B**|
|Fill aracına geç|**F**|
|Silgi aracına geç|**E**|
|Metin aracına geç|**T**|
|Renk seç (damlalık) aracına geç|**I**|
|Etkin seçimi ve içeriğini taşıyın.|**Ok** tuşları.|
|Etkin seçimi ve içeriğini yeniden boyutlandırın.|**Ctrl**+**ok** tuşları|
|Etkin seçimi taşıyın, ancak içeriğini değil.|**Shıft**+**ok** tuşları|
|Etkin seçimi yeniden boyutlandırın, ancak içeriğini değil.|**Shıft**+**CTRL**+**ok** tuşları|
|Geçerli katmanı Yürüt|**Döndürülmesini**|
|Araç kalınlığını azalt|**[**|
|Araç kalınlığını artır|**]**|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Oyunlar ve uygulamalar için 3B varlıklarla çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|Dokular ve görüntüler, 3B modeller ve gölgelendirici efektleri gibi grafik varlıklarıyla çalışmak için Visual Studio 'da kullanabileceğiniz araçlara genel bir bakış sağlar.|
|[Model düzenleyicisi](../designers/model-editor.md)|3D modellerle çalışmak için Visual Studio Model Düzenleyicisi ' nin nasıl kullanılacağını açıklar.|
|[Gölgelendirici tasarımcısı](../designers/shader-designer.md)|Gölgelendiricilerle çalışmak için Visual Studio gölgelendirici Tasarımcısı 'nın nasıl kullanılacağını açıklar.|
