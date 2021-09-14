---
title: Görüntü Düzenleyici
description: DirectX uygulama geliştirmede kullanılan doku ve resim kaynaklarını görüntülemek ve değiştirmek için Visual Studio görüntü düzenleyicisi ile nasıl çalışacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/10/2018
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.imageeditor
- vs.graphics.imageeditor
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 47bcc37f0fe000066f8e2585098601b71e606a12
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636497"
---
# <a name="image-editor"></a>Görüntü düzenleyicisi

bu makalede doku ve resim kaynaklarını görüntülemek ve değiştirmek için Visual Studio **görüntü düzenleyicisi** ile nasıl çalışılacağı açıklanır.

DirectX uygulama geliştirmede kullanılan zengin doku ve görüntü biçimleri türleriyle çalışmak için **görüntü düzenleyicisini** kullanabilirsiniz. Bu, popüler görüntü dosyası biçimleri ve renk kodlamaları, alfa kanalları ve MıP eşleme gibi özellikler ve DirectX 'in desteklediği yüksek oranda sıkıştırılmış, donanım hızlandırmalı doku biçimlerinin çoğunu destekler.

## <a name="supported-formats"></a>Desteklenen biçimler

**Görüntü Düzenleyicisi** aşağıdaki görüntü biçimlerini destekler:

|Biçim adı|Dosya Adı Uzantısı|
|-----------------| - |
|Taşınabilir Ağ Grafikleri|*.png*|
|JPEG|*.jpg*, *. jpeg*, *. jpe*, *. JI*|
|Doğrudan çizim yüzeyi|*. DDS*|
|Grafik Değişim Biçimi|*.gif*|
|Biteş|*.bmp*, *. dib*|
|Etiketli resim dosyası biçimi|*. tif*, *. tiff*|
|TGA (Targa)|*. tga*|

## <a name="get-started"></a>başlarken

bu bölümde, Visual Studio projenize bir görüntü ekleme ve gereksinimlerinize göre yapılandırma açıklanmaktadır.

### <a name="add-an-image-to-your-project"></a>Projenize resim ekleme

1. **Çözüm Gezgini** içinde, görüntüsünü eklemek istediğiniz projenin kısayol menüsünü açın ve ardından   >  **Yeni öğe** Ekle ' yi seçin.

2. **Yeni öğe Ekle** iletişim kutusunda, **yüklü** altında **grafikler**' i seçin ve ardından görüntü için uygun bir dosya biçimi seçin.

   > [!NOTE]
   > **Yeni öğe Ekle** Iletişim kutusunda **grafik** kategorisini görmüyorsanız, **görüntü ve 3B model düzenleyicileri** bileşenini yüklemeniz gerekebilir. iletişim kutusunu kapatın ve ardından   >  **Visual Studio Yükleyicisi** açmak için menü çubuğunda araçlar **ve özellikler al** ' ı seçin. **Ayrı bileşenler** sekmesini seçin ve ardından **Oyunlar ve grafikler** kategorisi altındaki **görüntü ve 3B model düzenleyicileri** bileşenini seçin. **Değiştir**'i seçin.
   >
   > ![Görüntü ve 3B model düzenleyicileri bileşeni](media/image-3d-model-editors-component.png)

   Gereksinimlerinize göre bir dosya biçimi seçme hakkında daha fazla bilgi için bkz. [görüntü biçimini seçme](#choose-the-image-format).

3. Görüntü dosyasının **adını** ve oluşturulmasını istediğiniz **konumu** belirtin.

4. **Ekle** düğmesini seçin.

### <a name="choose-the-image-format"></a>Görüntü biçimini seçin

Görüntüyü nasıl kullanacağınızı planladığınıza bağlı olarak, bazı dosya biçimleri diğerlerinden daha uygun olabilir. Örneğin, bazı biçimler ihtiyacınız olan bir özelliği (örneğin, saydamlık veya belirli bir renk biçimi) desteklemeyebilir. Bazı biçimler, planladığınız görüntü içeriği türü için uygun sıkıştırmayı sağlamayabilir.

Aşağıdaki bilgiler, gereksinimlerinizi karşılayan bir görüntü biçimi seçmenize yardımcı olabilir:

**Bit eşlem resmi (.bmp)**

Bit eşlem resmi biçimi. 24 bit rengi destekleyen sıkıştırılmamış bir görüntü biçimi. Bit eşlem biçimi saydamlığı desteklemez.

**GIF resmi (.gif)**

Grafik Değişim Biçimi (GIF) resim biçimi. En fazla 256 rengi destekleyen, LZW ile sıkıştırılmış, kayıpsız bir görüntü biçimi. Önemli miktarda renk ayrıntısı olan fotoğraflar ve görüntüler için uygun olmayan ancak yüksek düzeyde renk uyumluluğu olan düşük renkli görüntüler için iyi sıkıştırma oranları sağlar.

**JPG resmi (.jpg)**

Birleşik Fotoğraf Uzmanları Grubu (JPEG) resim biçimi. 24 bit rengi destekleyen ve yüksek düzeyde renk uyumluluğu olan görüntülerin genel amaçlı sıkıştırmaya uygun olan, yüksek oranda sıkıştırılmış, kayıplı bir görüntü biçimi.

**PNG resmi (.png)**

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

![Visual Studio resim Düzenleyicisi Modu araç çubuğu](../designers/media/digit-tre-modal-toolbar.png)

Aşağıdaki tabloda, **Görüntü Düzenleyicisi Modu** araç çubuğunda, soldan sağa göründükleri sırada listelenen öğeler açıklanmaktadır:

|Araç Çubuğu Öğesi|Description|
|------------------|-----------------|
|**Seç**|Bir görüntünün dikdörtgen bölgesini seçmeye izin vermez. Bir bölge seçtikten sonra, onu kesebilir, kopyalayabilir, taşıyabilir, ölçeklendirebilir, döndürebilir, çevirebilir veya silebilirsiniz. Etkin bir seçim olduğunda, çizim araçları yalnızca seçili bölgeyi etkiler.|
|**Düzensiz seçim**|Görüntüde düzensiz bir bölgenin seçilmesine izin vermez. Bir bölge seçtikten sonra, onu kesebilir, kopyalayabilir, taşıyabilir, ölçeklendirebilir, döndürebilir, çevirebilir veya silebilirsiniz. Etkin bir seçim olduğunda, çizim araçları yalnızca seçili bölgeyi etkiler.|
|**Değnek seçimi**|Bir görüntünün benzer renkli bir bölgesini seçmeye izin vermez. *Tolerans*— diğer bir deyişle, benzer olarak kabul ettikleri bitişik renkler arasındaki en büyük fark — daha küçük veya daha geniş bir benzer renk aralığı içerecek şekilde yapılandırılabilir. Bir bölge seçtikten sonra, onu kesebilir, kopyalayabilir, taşıyabilir, ölçeklendirebilir, döndürebilir, çevirebilir veya silebilirsiniz. Etkin bir seçim olduğunda, çizim araçları yalnızca seçili bölgeyi etkiler.|
|**Kaydır**|Görüntünün pencere çerçevesine göre taşınmasını sağlar. **Kaydırma** modu ' nda görüntüde bir nokta seçin ve sonra taşıyın.<br /><br /> **CTRL** tuşuna basarak ve basılı tutarak, **kaydırma** modunu geçici olarak etkinleştirebilirsiniz.|
|**Zoom**|Pencere çerçevesine göre daha fazla veya daha az görüntü ayrıntısı görüntülenmesini sağlar. **Yakınlaştırma** modu ' nda görüntüde bir nokta seçin ve yakınlaştırmak için sağa veya aşağı taşıyın ya da uzaklaştırmak için sola ya da yukarı kaydırın.<br /><br /> Fare tekerleğini kullanırken veya artı işaretine (  **+** ) ya da eksi işaretine () basarak, CTRL tuşunu basılı tutarak yakınlaştırıp uzaklaştırabilirsiniz **-** .|
|**Gerçek boyuta Yakınlaştır**|Görüntünün pikselleri ve ekranın pikselleri arasında bir 1:1 ilişkisi kullanarak görüntüyü görüntüler.|
|**Sığacak kadar Yakınlaştır**|Pencere çerçevesindeki tam görüntüyü görüntüler.|
|**Genişliği Yakınlaştır**|Pencere çerçevesindeki görüntünün tam genişliğini görüntüler.|
|**Çizgisi**|Piksel sınırlarını gösteren kılavuzu etkinleştirilir veya devre dışı bırakır. Görüntüye yakınlaştırana kadar ızgara görünmeyebilir.|
|**Sonraki MıP düzeyini görüntüle**|Bir MIP eşleme zincirindeki bir sonraki daha büyük MıP düzeyini etkinleştirir. Etkin MıP düzeyi tasarım yüzeyinde görüntülenir. Bu öğe yalnızca MıP düzeylerine sahip dokularla kullanılabilir.|
|**Önceki MıP düzeyini görüntüle**|Bir MIP eşleme zincirindeki bir sonraki küçük MıP düzeyini etkinleştirir. Etkin MıP düzeyi tasarım yüzeyinde görüntülenir. Bu öğe yalnızca MıP düzeylerine sahip dokularla kullanılabilir.|
|**Kırmızı kanal**<br /><br /> **Yeşil kanal**<br /><br /> **Mavi kanal**<br /><br /> **Alfa kanalı**|Belirli renk kanalını etkinleştirilir veya devre dışı bırakır. **Note:**  Renk kanallarını sistematik olarak etkinleştirerek veya devre dışı bırakarak, bir veya daha fazla sorunla ilgili sorunları yalıtabilirsiniz. Örneğin, yanlış alfa saydamlığı belirleyebilirsiniz.|
|**Arka Plan**|Görüntünün saydam kısımları aracılığıyla arka planın görüntülenmesini mümkün veya devre dışı bırakır. Aşağıdaki seçeneklerden birini belirleyerek arka planın nasıl görüntüleneceğini yapılandırabilirsiniz:<br /><br /> **Tahtası**<br /> Arka planı bir dama tahtası stili olarak göstermek için belirtilen arka plan rengiyle birlikte yeşil bir renk kullanır. Bu seçeneği, görüntünün saydam parçalarını daha belirgin hale getirmenize yardımcı olması için kullanabilirsiniz.<br /><br /> Beyaz arka plan<br /> Arka planı göstermek için beyaz rengi kullanır.<br /><br /> Siyah arka plan<br /> Arka planı göstermek için siyahın rengini kullanır.<br /><br /> Arka plana animasyon ekle<br /> Dama tahtası deseninin yavaş olması. Bu seçeneği, görüntünün saydam parçalarını daha belirgin hale getirmenize yardımcı olması için kullanabilirsiniz.|
|**Özellikler**|Alternatif olarak **Özellikler** penceresini açar veya kapatır.|
|**Gelişmiş**|Ek komutlar ve seçenekler içerir.<br /><br /> **Filtreler**<br /><br /> Birkaç ortak görüntü filtresi sağlar: **siyah ve beyaz**, **bulanıklaştırma**, **parlak on**, **koyulaştırma**, **kenar algılama**, **kabarık**, **renkleri ters çevir**, **Ripple**, **sepıa tonu** ve **keskinleştirme**.<br /><br /> **Grafik altyapıları**<br /><br /> **D3D11 ile işleme**<br /> **Görüntü Düzenleyicisi** tasarım yüzeyini Işlemek için Direct3D 11 ' i kullanır.<br /><br /> **D3D11WARP ile işleme**<br /> , **görüntü düzenleyicisi** tasarım yüzeyini işlemek için Direct3D 11 Windows gelişmiş tarama platformu (WARP) kullanır.<br /><br /> **Araçlar**<br /><br /> **Yatay Çevir**<br /> Görüntüyü yatay veya x, eksenin etrafında yerleştir.<br /><br /> **Dikey Çevir**<br /> Görüntüyü dikey veya y ekseni etrafında dönüştürün.<br /><br /> **MIPS oluştur**<br /> Bir görüntü için MıP düzeyleri oluşturur. MıP düzeyleri zaten mevcutsa, en büyük MıP düzeyinden yeniden oluşturulur. Daha küçük MıP düzeylerinde yapılan tüm değişiklikler kaybolur. Oluşturmuş olduğunuz MıP düzeylerini kaydetmek için, görüntüyü kaydetmek üzere *. DDS* biçimini kullanmanız gerekir.<br /><br /> **Görünüm**<br /><br /> **Kare hızı**<br /> Etkinleştirildiğinde, tasarım yüzeyinin sağ üst köşesindeki kare hızını görüntüler. Kare hızı, saniye başına çizilen çerçeve sayısıdır. **İpucu:** Son komutu yeniden çalıştırmak için **Gelişmiş** düğmesini seçebilirsiniz.|

### <a name="image-editor-toolbar"></a>Görüntü Düzenleyicisi araç çubuğu

![Görüntü Düzenleyicisi araç çubuğu](../designers/media/digit-tre-toolbar.png)

Aşağıdaki tabloda, en üstten alta göründükleri sırada listelenen **Görüntü Düzenleyicisi** araç çubuğundaki öğeler açıklanmaktadır:

|Araç Çubuğu Öğesi|Description|
|------------------|-----------------|
|**Düğmede**|Diğer adı olan bir vuruş çizmek için etkin renk seçimini kullanır. **Özellikler** penceresinde konturun rengini ve kalınlığını ayarlayabilirsiniz.|
|**Fırçanın**|, İzin verilen bir kenar yumuşatma çizmek için etkin renk seçimini kullanır. **Özellikler** penceresinde konturun rengini ve kalınlığını ayarlayabilirsiniz.|
|**Boya tabancası**|, Görüntüyle birlikte karışan ve zaman içerisinde daha fazla doygun bir kenar yumuşatma içeren bir vuruş çizmek için etkin renk seçimini kullanır. **Özellikler** penceresinde konturun rengini ve kalınlığını ayarlayabilirsiniz.|
|**Damlalığı**|Etkin renk seçimini seçili pikselin rengine ayarlar.|
|**Doldur**|Görüntünün bir bölgesini dolduracak etkin renk seçimini kullanır. Etkilenen bölge, her pikselde aynı renkteki ve aynı rengin kendisi olan piksellerle bağlantılı olan her pikselle birlikte, dolgunun uygulandığı piksel olarak tanımlanır. Dolguyu etkin bir seçim içinde uygulanırsa, etkilenen bölge seçim tarafından sınırlandırılır.<br /><br /> Varsayılan olarak, etkin renk seçimi, Alfa bileşenine göre görüntünün etkilenen bölgesiyle birlikte karıştırılırdı. Etkilenen bölgenin üzerine yazmak üzere etkin renk seçimini kullanmak için, Fill aracını kullanırken **SHIFT** tuşuna basın ve basılı tutun.|
|**Silgi**|Resim bir alfa kanalını destekliyorsa, pikselleri tamamen saydam renge ayarlar. Aksi takdirde, pikselleri etkin arka plan rengine ayarlar.|
|**Çizgi**, **dikdörtgen**, **yuvarlatılmış dikdörtgen**, **elips**|Görüntüde bir şekil çizer. Ana hattın rengini ve kalınlığını **Özellikler** penceresinde ayarlayabilirsiniz.<br /><br /> Eşit genişliğe ve yüksekliğe sahip bir temel öğe çizmek için, çizerken **SHIFT** tuşuna basın ve basılı tutun.|
|**Metin**|Metin çizmek için ön plan rengi seçimini kullanır. Arka plan rengi, arka plan rengi seçimi tarafından belirlenir. Saydam bir arka plan için arka plan renk seçiminin alfa değeri 0'dır. Metin bölgesi etkin durumdayken, Metnin diğer addan koruma ile çizip çizilmemeylerini ve Özellikler penceresinde Değer , Yazı Tipi,  Boyut **ve** stil(**Kalın**, **İtalik** veya Altı Çizili) metnini de **ayarabilirsiniz.**  Metin bölgesi artık etkin olmadığı zaman metnin içeriği ve görünümü son hale getirildi.|
|**Döndür**|Görüntüyü saat yönünde 90 derece döndürür.|
|**Döşeme**|Görüntüyü etkin seçime göre kırpıyor.|

### <a name="work-with-mip-levels"></a>MIP düzeyleriyle çalışma

DirectDraw Surface (*.dds)* gibi bazı görüntü biçimleri doku-alanı Ayrıntı Düzeyi (LOD) için MIP düzeylerini destekler. MIP düzeyleri oluşturma ve bu düzeylerle çalışma hakkında daha fazla bilgi için [bkz. Nasıl 2012: MIP düzeyleri oluşturma ve değiştirme](../designers/how-to-create-and-modify-mip-levels.md)

### <a name="work-with-transparency"></a>Saydamlık ile çalışma

DirectDraw Surface (*.dds)* gibi bazı görüntü biçimleri saydamlığı destekler. Kullandığınız araça bağlı olarak saydamlığı çeşitli yollarla kullanabilirsiniz. Renk seçiminin saydamlık düzeyini belirtmek için Özellikler **penceresinde** renk seçiminin **A** (alfa) bileşenini ayarlayın.

Aşağıdaki tabloda, farklı türlerde araçların saydamlığın nasıl uygulandığını denetlemesi açık almaktadır:

|Araç|Açıklama|
|----------|-----------------|
|**Kalem,** **Fırça,** **Airbrush,** **Çizgi,** **Dikdörtgen,** **Yuvarlanmış Dikdörtgen,** **Üç Nokta**, **Metin**|Etkin renk seçimini görüntüyle birlikte karıştırmak  için Özellikler  penceresinde Kanallar özellik grubunu genişletin, **Alfa** kanalında **Çiz** onay kutusunu ayarlayın ve ardından normal şekilde çizin.<br /><br /> Etkin renk seçimini kullanarak çizmek ve görüntünün alfa değerini olduğu gibi bırakmak için Alfa kanalının **Çiz** **onay** kutusunu temizleyin ve ardından normal şekilde çizin.|
|**Doldur**|Etkin renk seçimini görüntüyle birlikte karıştırmak için, doldurulacak alanı seçmeniz gerekir.<br /><br /> Görüntünün üzerine yazmak için etkin renk seçimini (alfa kanalının değeri dahil) kullanmak için **Shift** tuşuna basın ve ardından doldurulacak alanı seçin.|

### <a name="image-properties"></a>Görüntü özellikleri

Görüntünün çeşitli **özelliklerini** belirtmek için Özellikler penceresini kullanabilirsiniz. Örneğin, görüntüyü yeniden boyutlandırmak için genişlik ve yükseklik özelliklerini ayarlayın.

Aşağıdaki tabloda görüntü özellikleri açık almaktadır:

|Özellik|Açıklama|
|--------------|-----------------|
|Width|Görüntünün genişliği.|
|Height|Görüntünün yüksekliği.|
|Piksel Başına Bit|Her pikseli temsil eden bit sayısı. Bu özelliğin değeri görüntünün **Renk Biçimine** bağlıdır.|
|Saydam Seçim|Seçim katmanını ana görüntüyle birlikte, seçim katmanının alfa değerine göre karıştırmak için **True;** aksi takdirde **False olur.** Bu öğe yalnızca alfa desteği olan görüntüler için kullanılabilir.|
|Biçimlendir|Görüntünün renk biçimi. Görüntü biçimine bağlı olarak çeşitli renk biçimleri belirtebilirsiniz. Renk biçimi, görüntüye dahil edilen renk kanallarının sayısını ve türlerini ve çeşitli kanalların boyutunu ve kodlamasını tanımlar.|
|Mip Düzeyi|Etkin MIP düzeyi. Bu öğe yalnızca MIP düzeylerine sahip dokular için kullanılabilir.|
|Mip Düzeyi Sayısı|Görüntüde miP düzeylerinin toplam sayısı. Bu öğe yalnızca MIP düzeylerine sahip dokular için kullanılabilir.|
|Çerçeve Sayısı|Görüntüdeki toplam kare sayısı. Bu öğe yalnızca doku dizilerini destekleyen görüntüler için kullanılabilir.|
|Çerçeve|Geçerli çerçeve. Yalnızca ilk kare görünüme sahip olabilir; Görüntü kaydedilebilirken diğer tüm kareler kaybolur.|
|Derinlik Dilimi Sayısı|Görüntüde yer alan derinlik dilimlerinin toplam sayısı. Bu öğe yalnızca birim dokularını destekleyen görüntüler için kullanılabilir.|
|Derinlik Dilimi|Geçerli derinlik dilimi. Yalnızca ilk dilim görünüme sahip olabilir; Görüntüyü kaydeden diğer tüm dilimler kaybolur.|

> [!NOTE]
> Döndür **özelliği tüm** araçlara ve seçili bölgelere uygulandığı için özellikler penceresinin alt kısmında her **zaman** diğer araç özellikleriyle birlikte görünür. **Başka bir** seçim veya etkin araç yoksa görüntünün tamamı örtülü olarak seçildiğinden döndür seçeneği her zaman görüntülenir. Döndür özelliği hakkında daha **fazla bilgi için** bkz. Araç [özellikleri.](#tool -properties)

### <a name="resize-images"></a>Görüntüleri yeniden boyutlandırma

Bir görüntüyü yeniden boyutlandırmanın iki yolu vardır. Her iki durumda da Görüntü **Düzenleyicisi,** görüntüyü yeniden örneklemek için çift ilişkilendirme kullanır.

- Özellikler **penceresinde** Genişlik ve Yükseklik özellikleri için **yeni** **değerler** belirtin.

- Görüntünün tamamını seçin ve kenarlığı işaretleyicilerini kullanarak görüntüyü yeniden boyutlandırabilirsiniz.

### <a name="selected-regions"></a>Seçili bölgeler

Görüntü **Düzenleyicisi'nde yapılan seçimler** görüntünün etkin olan bölgelerini tanımlar. Etkin bölgeler araçlardan ve dönüşümlerden etkilenir. Etkin bir seçim olduğunda, seçilen bölgenin dışındaki alanlar çoğu araç ve dönüştürmeden etkilenmez. Etkin bir seçim yoksa görüntünün tamamı etkindir.

Çoğu araç **(Kalem,** **Fırça,** **Airbrush,** **Fill,** **Silgi** ve 2D temel öğeler) ve dönüştürmeler (**Döndürme,** **Kırpma,** Renkleri Ters **Çevirme,** Yatay Çevirme **ve** Dikey **Çevirme)** etkin seçimle kısıtlanmış veya tanımlanmıştır. Ancak, bazı araçlar **(Eyedropper** ve **Text**) ve dönüştürmeler (**Mips** Oluştur) herhangi bir etkin seçimden etkilenmez. Bu araçlar her zaman görüntünün tamamı etkin seçim gibi davranır.

Bir bölgeyi seçerken, orantılı (kare) seçim yapmak için **Shift** tuşuna basarak ve basılı tutarak. Aksi takdirde seçim kısıtlanmaz.

#### <a name="resize-selections"></a>Seçimleri yeniden boyutlandırma

Bir bölgeyi seçdikten sonra, seçim işaretçisi boyutunu değiştirerek bölgeyi veya görüntü içeriğini yeniden boyutlandırabilirsiniz. Seçilen bölgeyi yeniden boyutlandırırken, seçilen bölgenin davranışını yeniden boyutlandırırken değiştirmek için aşağıdaki değiştirici anahtarları kullanabilirsiniz:

**Ctrl** - Seçilen bölgenin içeriğini yeniden boyutlandırılmadan önce kopyalar. Bu, kopya yeniden boyutlandırılırken özgün görüntüyü olduğu gibi bırakır.

**Shift** - Seçilen bölgeyi özgün boyutuyla orantılı olarak yeniden boyutlandırılır.

**Alt** - Seçim bölgesi boyutunu değiştirir. Bu, görüntüyü değiştirilmeden bırakır.

Aşağıdaki tabloda geçerli değiştirici anahtar birleşimleri açık almaktadır:

|Ctrl|Shift|Alt|Description|
|----------|-----------|---------|-----------------|
||||Seçilen bölgenin içeriğini yeniden boyutlandırıyor.|
||**Shift**||Seçilen bölgenin içeriğini orantılı olarak yeniden boyutlandırıyor.|
|||**Alt**|Seçilen bölgeyi yeniden boyutlandırıyor. Bu, yeni bir seçim bölgesi tanımlar.|
||**Shift**|**Alternatif**|Seçili bölgeyi orantılı olarak yeniden boyutlandırır. Bu, yeni bir seçim bölgesi tanımlar.|
|**T**|||Seçili bölgenin içeriğini kopyalar ve sonra yeniden boyutlandırır.|
|**T**|**Shift**||Seçili bölgenin içeriğini kopyalar ve daha sonra orantılı olarak yeniden boyutlandırır.|

### <a name="tool-properties"></a>Araç özellikleri

Bir araç seçiliyken, görüntü nasıl etkilediği hakkındaki ayrıntıları belirtmek için **Özellikler** penceresini kullanabilirsiniz. Örneğin, **kurşun kalem** aracının kalınlığını veya **fırça** aracının rengini ayarlayabilirsiniz.

Hem ön plan rengi hem de arka plan rengi ayarlayabilirsiniz. Her ikisi de Kullanıcı tanımlı opaklık sağlamak için bir alfa kanalını destekler. Ayarlar tüm araçlara uygulanır. Fare kullanıyorsanız sol fare düğmesi ön plan rengine karşılık gelir ve sağ fare düğmesi arka plan rengine karşılık gelir.

Aşağıdaki tabloda araç özellikleri açıklanmaktadır:

|Araç|Özellikler|
|----------|----------------|
|Tüm araçlar ve seçimler|**Döndürme ölçütü**<br /> Seçim ya da araç efektinin saatin saat yönünde döndürüldüğü miktarı derece cinsinden tanımlar.|
|**Kurşun kalem**, **fırça**, **püskürtme**, **silgi**|**Kalınlık**<br /> Araçtan etkilenen alanın boyutunu tanımlar.|
|**Metin**|**Kenar yumuşatma**<br /> Daha fazla kenar yumuşatma uygulanmış kenarları olan metni çizer. Bu metin daha yumuşak bir görünüm sağlar.<br /><br /> **Değer**<br /> Çizilecek metin.<br /><br /> **Yazı tipi**<br /> Metni çizmek için kullanılan yazı tipi.<br /><br /> **Boyut**<br /> Metnin boyutu.<br /><br /> **Kalın**<br /> Yazı tipini kalın yapar.<br /><br /> **İtalik**<br /> Yazı tipini italik yapar.<br /><br /> **Çiz**<br /> Yazı tipi altı çizili hale gelir.|
|**2B temel**|**Kenar yumuşatma**<br /> Kenar yumuşatma uygulanmış kenarları olan temel türleri çizer. Böylece daha yumuşak bir görünüm elde edin.<br /><br /> **Kalınlık**<br /> Temel öğesinin sınırını oluşturan çizginin kalınlığını tanımlar.<br /><br /> **Yarıçap X**<br /> (Yalnızca yuvarlatılmış dikdörtgen) Temel öğesinin üst ve alt kenarları için yuvarlama yarıçapını tanımlar.<br /><br /> **Yarıçap Y**<br /> (Yalnızca yuvarlatılmış dikdörtgen) Temel öğesinin sol ve sağ kenarları için yuvarlama yarıçapını tanımlar.|
|**Kurşun kalem**, **fırça**, **püskürtme**, **2B temel**|**Kanallar**<br /> Görüntüleme ve çizim için belirli renk kanallarını etkinleştirip devre dışı bırakır. Belirli bir renk kanalı için **Görünüm** ayarlandıysa, bu kanal görüntüde görünür; Aksi takdirde, görünür değildir. Belirli bir renk kanalı için **Çizim** ayarlandıysa, bu kanal çizim işlemleri tarafından etkilenir; Aksi takdirde, değildir.|
|**Değnek seçimi**, **dolgusu**|**Payı**<br /> Etkilenen veya seçilen bölgenin bir parçası olarak daha az veya daha fazla benzer renge sahip olduğu için, benzer olarak kabul edildiği bitişik renkler arasındaki en büyük farkı tanımlar. Varsayılan olarak, değer 32 ' dir. Bu, orijinal rengin 32 gölgeler (daha açık veya daha koyu) içindeki bitişik piksellerin bölgenin parçası olarak kabul edildiği anlamına gelir.|

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

|Komut|Klavye kısayolları|
|-------------| - |
|**Seçme** moduna geçiş yap|**S**|
|**Yakınlaştırma** moduna geç|**Kadar**|
|**Pan** moduna geç|**K**|
|Tümünü seç|**CTRL** + **Bir**|
|Geçerli seçimi sil|**Silme**|
|Geçerli seçimi iptal et|**ESC** (kaçış)|
|Yakınlaştır|**CTRL** + **Fare tekerleği ileri**<br /><br /> **CTRL** + **PageUp**<br /><br /> Artı Işareti ( **+** )|
|Uzaklaştır|**CTRL** - **Fare tekerleği geriye doğru**<br /><br /> **CTRL** - **Pageaşağı**<br /><br /> Eksi Işareti ( **-** )|
|Görüntüyü yukarı kaydır|**Fare tekerleği geriye doğru**<br /><br /> **PageDown**|
|Görüntüyü aşağı kaydır|**Fare tekerleği ileriye doğru**<br /><br /> **PageUp**|
|Görüntüyü sola kaydır|**SHIFT** + **Fare tekerleği geriye doğru**<br /><br /> **Fare tekerleği sol**<br /><br /> **SHIFT** + **Pageaşağı**|
|Görüntüyü sağa kaydır|**SHIFT** + **Fare tekerleği ileri**<br /><br /> **Fare tekerleği sağ**<br /><br /> **SHIFT** + **PageUp**|
|Gerçek boyuta Yakınlaştır|**CTRL** + **0** (sıfır)|
|Görüntüyü pencereye sığdır|**CTRL** + **G**, **CTRL** + **F**|
|Görüntüyü pencere genişliğine sığdır|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **I**|
|Kılavuza geçiş|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **G**|
|Görüntüyü geçerli seçime kırpma|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **C**|
|Sonraki (daha yüksek ayrıntı) MIP düzeyini görüntüleme|**Ctrl tuşunu basılı tutarak** + **G**, **Ctrl** + **6**|
|Önceki (daha düşük ayrıntı) MIP düzeyini görüntüleme|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **7**|
|Kırmızı renk kanalını değiştirme|**Ctrl tuşunu basılı tutarak** + **G**, **Ctrl** + **1**|
|Yeşil renk kanalını değiştirme|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **2**|
|Mavi renk kanalını değiştirme|**Ctrl tuşunu basılı tutarak** + **G**, **Ctrl** + **3**|
|Alfa (saydamlık) kanalını iki durumlu düğme|**Ctrl tuşunu basılı tutarak** + **G**, **Ctrl** + **4**|
|Alfa denetleyici panosu desenini değiştir|**Ctrl tuşunu basılı tutarak** + **G,** **Ctrl** + **B**|
|Düzensiz seçim aracına geçme|**L**|
|Wand selection aracına geçme|**M**|
|Kalem aracına geçme|**P**|
|Fırça aracına geçiş|**B**|
|Dolgu aracına geçiş|**F**|
|Silgi aracına geçiş|**E**|
|Metin aracına geçiş|**T**|
|Renk seçme (gözdropper) aracına geçiş|**I**|
|Etkin seçimi ve içeriğini taşıma.|**Ok** tuşları.|
|Etkin seçimi ve içeriğini yeniden boyutlandırabilirsiniz.|**Ctrl tuşunu basılı tutarak** + **Ok** tuşları|
|Etkin seçimi hareket ettirin, ancak içeriğini taşımayın.|**Shift ile kaydırma** + **Ok** tuşları|
|Etkin seçimi yeniden boyutlandırabilirsiniz ancak içeriğini yeniden boyutlandıramaz.|**Shift ile kaydırma** + **Ctrl tuşunu basılı tutarak** + **Ok** tuşları|
|Geçerli katmanı işleme|**Dönüş**|
|Araç kalınlığını azaltma|**[**|
|Araç kalınlığını artırma|**]**|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Oyunlar ve uygulamalar için 3D varlıklarla çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|Dokular ve görüntüler, 3B modeller ve gölgelendirici Visual Studio grafik varlıklarıyla çalışmak için Visual Studio'da kullanabileceğiniz araçlara genel bir bakış sağlar.|
|[Model düzenleyicisi](../designers/model-editor.md)|3D modellerle çalışmak için Visual Studio Model Düzenleyicisi'nin nasıl kullanılası açıklandı.|
|[Gölgelendirici tasarımcısı](../designers/shader-designer.md)|Gölgelendiriciler ile çalışmak için Visual Studio Gölgelendirici Tasarımcısı'nın nasıl kullanacağız?|
