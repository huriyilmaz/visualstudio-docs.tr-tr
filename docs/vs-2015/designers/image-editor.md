---
title: Görüntü Düzenleyicisi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics.designer.imageeditor
- vs.graphics.imageeditor
ms.assetid: fc71d502-c548-4863-8afc-12a1d3ec90d4
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0c30e6f1be9daf07f3685c06b21ed9d507b86a07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664384"
---
# <a name="image-editor"></a>Görüntü Düzenleyici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belge, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] doku ve resim kaynaklarını görüntülemek ve değiştirmek için görüntü Düzenleyicisi ile nasıl çalışabileceğinizi açıklar.

 DirectX uygulama geliştirmede kullanılan zengin doku ve görüntü biçimleri türleriyle çalışmak için görüntü düzenleyicisini kullanabilirsiniz. Bu, popüler görüntü dosyası biçimleri ve renk kodlamaları, alfa kanalları ve MıP eşleme gibi özellikler ve DirectX 'in desteklediği yüksek oranda sıkıştırılmış, donanım hızlandırmalı doku biçimlerinin birçoğu için destek içerir.

## <a name="supported-formats"></a>Desteklenen biçimler
 Görüntü Düzenleyicisi şu görüntü biçimlerini destekler:

|Biçim adı|Dosya Adı Uzantısı|
|-----------------|-------------------------|
|Taşınabilir Ağ Grafikleri|.png|
|JPEG|. jpg,. jpeg,. jpe,. JI|
|Doğrudan çizim yüzeyi|. DDS|
|Grafik Değişim Biçimi|.gif|
|Biteş|. bmp,. dib|
|Etiketli resim dosyası biçimi|. tif,. tiff|
|TGA (Targa)|. tga|

## <a name="getting-started"></a>Başlarken
 Bu bölümde, projenize bir görüntü ekleme [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve gereksinimlerinize göre yapılandırma açıklanmaktadır.

#### <a name="to-add-an-image-to-your-project"></a>Projenize bir görüntü eklemek için

1. **Çözüm Gezgini**' de, görüntüsünü eklemek istediğiniz projenin kısayol menüsünü açın ve **Ekle**, **Yeni öğe**' yi seçin.

2. **Yeni öğe Ekle** iletişim kutusunda, **yüklü**altında **grafikler**' i seçin ve ardından görüntü için uygun bir dosya biçimi seçin. Gereksinimlerinize göre bir dosya biçimi seçme hakkında daha fazla bilgi için aşağıdaki bölüme bakın.

3. Görüntü dosyasının **adını** ve oluşturulmasını istediğiniz **konumu** belirtin.

4. **Ekle** düğmesini seçin.

### <a name="choosing-the-image-format"></a>Görüntü biçimini seçme
 Görüntüyü nasıl kullanacağınızı planladığınıza bağlı olarak, bazı dosya biçimleri diğerlerinden daha uygun olabilir. Örneğin, bazı biçimler, ihtiyacınız olan bir özelliği (saydamlık veya belirli bir renk biçimi gibi) desteklemeyebilir veya planladığınız görüntü içeriği türü için uygun sıkıştırmayı sağlamayabilir.

 Aşağıdaki bilgiler, gereksinimlerinizi karşılayan bir görüntü biçimi seçmenize yardımcı olabilir.

 **Bit eşlem resmi (. bmp)** Bit eşlem resmi biçimi. 24 bit rengi destekleyen sıkıştırılmamış bir görüntü biçimi. Bit eşlem biçimi saydamlığı desteklemez.

 **GIF resmi (. GIF)** Grafik Değişim Biçimi (GIF) resim biçimi. En fazla 256 rengi destekleyen, LZW ile sıkıştırılmış, kayıpsız bir görüntü biçimi. Önemli miktarda renk ayrıntısı olan fotoğraflar ve görüntüler için uygun olmayan ancak yüksek düzeyde renk uyumluluğu olan düşük renkli görüntüler için iyi sıkıştırma oranları sağlar.

 **Jpg resmi (. jpg)** Birleşik Fotoğraf Uzmanları Grubu (JPEG) resim biçimi. 24 bit rengi destekleyen ve yüksek düzeyde renk uyumluluğu olan görüntülerin genel amaçlı sıkıştırmaya uygun olan, yüksek oranda sıkıştırılmış, kayıplı bir görüntü biçimi.

 **PNG resmi (. png)** Taşınabilir Ağ Grafikleri (PNG) resim biçimi. 24 bit renk ve alfa saydamlığı destekleyen, orta düzeyde sıkıştırılmış, kayıpsız bir görüntü biçimi. Doğal ve yapay görüntüler için uygundur, ancak JPG veya GIF gibi kayıplı biçimler kadar iyi sıkıştırma oranları sağlamaz.

 **TIFF resmi (. tif)** Etiketli resim dosyası biçimi (TIFF veya TıF) resim biçimi. Birkaç sıkıştırma şemasını destekleyen esnek bir görüntü biçimi.

 **DDS dokusu (. DDS)** DirectDraw yüzeyi (DDS) doku biçimi. 24 bit renk ve alfa saydamlığını destekleyen, yüksek oranda sıkıştırılmış, kayıplı bir doku biçimi. Sıkıştırma oranları 8:1 kadar yüksek olabilir. Grafik donanımında açılan S3 doku sıkıştırmasını temel alır.

 **TGA resmi (. TGA)** Truevision grafik bağdaştırıcısı (TGA) görüntü biçimi (Targa olarak da bilinir). Hem renk eşlemeli (renk paleti), hem de 24 bit renge ve Alfa saydamlığına sahip doğrudan renk görüntülerini destekleyen, RLE sıkıştırılmış, kayıpsız bir resim biçimi. Önemli miktarda renk ayrıntısı olan fotoğraflar ve görüntüler için uygun değil, ancak aynı renklerin uzun yayılmasına sahip görüntüler için iyi sıkıştırma oranları sağlar.

### <a name="configuring-the-image"></a>Görüntüyü yapılandırma
 Yeni oluşturduğunuz görüntüyle çalışmaya başlamadan önce varsayılan yapılandırmasını değiştirebilirsiniz. Örneğin boyutlarını veya kullandığı renk biçimini değiştirebilirsiniz. Görüntünün bu ve diğer özelliklerinin nasıl yapılandırılacağı hakkında bilgi için bkz. [görüntü özellikleri](#ImageProperties).

> [!NOTE]
> Çalışmanızı kaydetmeden önce, belirli bir renk biçimini kullanmak istiyorsanız **renk biçimi** özelliğini ayarladığınızdan emin olun. Dosya biçimi sıkıştırmayı destekliyorsa, dosyayı ilk kez kaydettiğinizde veya **farklı kaydet**' i seçtiğinizde sıkıştırma ayarlarını yapabilirsiniz.

## <a name="working-with-the-image-editor"></a>Görüntü Düzenleyicisi ile çalışma
 Bu bölümde, doku ve görüntüleri değiştirmek için görüntü Düzenleyicisi 'nin nasıl kullanılacağı açıklanmaktadır.

### <a name="image-editor-toolbars"></a>Görüntü Düzenleyicisi araç çubukları
 Görüntü Düzenleyicisi araç çubukları görüntülerle çalışmanıza yardımcı olan komutlar içerir.

 Görüntü düzenleyicisinin durumunu etkileyen komutlar, **Görüntü Düzenleyicisi Modu** araç çubuğunda gelişmiş komutlarla birlikte bulunur. Araç çubuğu, görüntü Düzenleyicisi tasarım yüzeyinin en üst kenarı üzerinde bulunur. Çizim araçları, görüntü Düzenleyicisi tasarım yüzeyinin en sol kenarında bulunan **görüntü düzenleyici** araç çubuğunda bulunur.

 **Görüntü Düzenleyicisi Modu** araç çubuğu şöyledir:

 ![Görüntü düzenleyici kalıcı araç çubuğu.](../designers/media/digit-tre-modal-toolbar.png "Digit-TRE-Modal-araç çubuğu")

 Bu tabloda, **Görüntü Düzenleyicisi Modu** araç çubuğunda, soldan sağa göründükleri sırada listelenen öğeler açıklanmaktadır.

|Araç Çubuğu Öğesi|Description|
|------------------|-----------------|
|**Seç**|Bir görüntünün dikdörtgen bölgesini seçmeye izin vermez. Bir bölge seçtikten sonra, onu kesebilir, kopyalayabilir, taşıyabilir, ölçeklendirebilir, döndürebilir, çevirebilir veya silebilirsiniz. Etkin bir seçim olduğunda, çizim araçları yalnızca seçili bölgeyi etkiler.|
|**Düzensiz seçim**|Görüntüde düzensiz bir bölgenin seçilmesine izin vermez. Bir bölge seçtikten sonra, onu kesebilir, kopyalayabilir, taşıyabilir, ölçeklendirebilir, döndürebilir, çevirebilir veya silebilirsiniz. Etkin bir seçim olduğunda, çizim araçları yalnızca seçili bölgeyi etkiler.|
|**Değnek seçimi**|Bir görüntünün benzer renkli bir bölgesini seçmeye izin vermez. *Tolerans*— diğer bir deyişle, benzer olarak kabul ettikleri bitişik renkler arasındaki en büyük fark — daha küçük veya daha geniş bir benzer renk aralığı içerecek şekilde yapılandırılabilir. Bir bölge seçtikten sonra, onu kesebilir, kopyalayabilir, taşıyabilir, ölçeklendirebilir, döndürebilir, çevirebilir veya silebilirsiniz. Etkin bir seçim olduğunda, çizim araçları yalnızca seçili bölgeyi etkiler.|
|**Kaydır**|Görüntünün pencere çerçevesine göre taşınmasını sağlar. **Kaydırma** modu ' nda görüntüde bir nokta seçin ve sonra taşıyın.<br /><br /> CTRL tuşuna basarak ve basılı tutarak, **kaydırma** modunu geçici olarak etkinleştirebilirsiniz.|
|**Zoom**|Pencere çerçevesine göre daha fazla veya daha az görüntü ayrıntısı görüntülenmesini sağlar. **Yakınlaştırma** modu ' nda görüntüde bir nokta seçin ve yakınlaştırmak için sağa veya aşağı taşıyın ya da uzaklaştırmak için sola ya da yukarı kaydırın.<br /><br /> Fare tekerleğini kullanırken veya artı işaretine (+) ya da eksi Işaretine (-) basarak CTRL tuşunu basılı tutarak yakınlaştırıp uzaklaştırabilirsiniz.|
|**Gerçek boyuta Yakınlaştır**|Görüntünün pikselleri ve ekranın pikselleri arasında bir 1:1 ilişkisi kullanarak görüntüyü görüntüler.|
|**Sığacak kadar Yakınlaştır**|Pencere çerçevesindeki tam görüntüyü görüntüler.|
|**Genişliği Yakınlaştır**|Pencere çerçevesindeki görüntünün tam genişliğini görüntüler.|
|**Kılavuz**|Piksel sınırlarını gösteren kılavuzu etkinleştirilir veya devre dışı bırakır. Görüntüye yakınlaştırana kadar ızgara görünmeyebilir.|
|**Sonraki MıP düzeyini görüntüle**|Bir MIP eşleme zincirindeki bir sonraki daha büyük MıP düzeyini etkinleştirir. Etkin MıP düzeyi tasarım yüzeyinde görüntülenir. Bu öğe yalnızca MıP düzeylerine sahip dokularla kullanılabilir.|
|**Önceki MıP düzeyini görüntüle**|Bir MIP eşleme zincirindeki bir sonraki küçük MıP düzeyini etkinleştirir. Etkin MıP düzeyi tasarım yüzeyinde görüntülenir. Bu öğe yalnızca MıP düzeylerine sahip dokularla kullanılabilir.|
|**Kırmızı kanal**<br /><br /> **Yeşil kanal**<br /><br /> **Mavi kanal**<br /><br /> **Alfa kanalı**|Belirli renk kanalını etkinleştirilir veya devre dışı bırakır. **Note:**  Renk kanallarını sistematik olarak etkinleştirerek veya devre dışı bırakarak, bir veya daha fazla sorunla ilgili sorunları yalıtabilirsiniz. Örneğin, yanlış alfa saydamlığı belirleyebilirsiniz.|
|**Arka plan**|Görüntünün saydam kısımları aracılığıyla arka planın görüntülenmesini mümkün veya devre dışı bırakır. Aşağıdaki seçeneklerden birini belirleyerek arka planın nasıl görüntüleneceğini yapılandırabilirsiniz:<br /><br /> **Tahtası**<br /> Arka planı bir dama tahtası stili olarak göstermek için belirtilen arka plan rengiyle birlikte yeşil bir renk kullanır. Bu seçeneği, görüntünün saydam parçalarını daha belirgin hale getirmenize yardımcı olması için kullanabilirsiniz.<br /><br /> Beyaz arka plan<br /> Arka planı göstermek için beyaz rengi kullanır.<br /><br /> Siyah arka plan<br /> Arka planı göstermek için siyahın rengini kullanır.<br /><br /> Arka plana animasyon ekle<br /> Dama tahtası deseninin yavaş olması. Bu seçeneği, görüntünün saydam parçalarını daha belirgin hale getirmenize yardımcı olması için kullanabilirsiniz.|
|**Özellikler**|Alternatif olarak **Özellikler** penceresini açar veya kapatır.|
|**Gelişmiş**|Ek komutlar ve seçenekler içerir.<br /><br /> **Filtreler**<br /><br /> Birkaç ortak görüntü filtresi sağlar: **siyah ve beyaz**, **bulanıklaştırma**, **parlak on**, **koyulaştırma**, **kenar algılama**, **kabarık**, **renkleri ters çevir**, **Ripple**, **sepıa tonu**ve **keskinleştirme**.<br /><br /> **Grafik altyapıları**<br /><br /> **D3D11 ile işleme**<br /> Görüntü Düzenleyicisi tasarım yüzeyini işlemek için Direct3D 11 ' i kullanır.<br /><br /> **D3D11WARP ile işleme**<br /> , Resim Düzenleyicisi tasarım yüzeyini işlemek için Direct3D 11 Windows Gelişmiş Tarama Platformu (WARP) kullanır.<br /><br /> **Araçlar**<br /><br /> **Yatay Çevir**<br /> Görüntüyü yatay veya x, eksenin etrafında yerleştir.<br /><br /> **Dikey Çevir**<br /> Görüntüyü dikey veya y ekseni etrafında dönüştürün.<br /><br /> **MIPS oluştur**<br /> Bir görüntü için MıP düzeyleri oluşturur. MıP düzeyleri zaten mevcutsa, en büyük MıP düzeyinden yeniden oluşturulur. Daha küçük MıP düzeylerinde yapılan tüm değişiklikler kaybolur. Oluşturmuş olduğunuz MıP düzeylerini kaydetmek için, görüntüyü kaydetmek üzere. DDS biçimini kullanmanız gerekir.<br /><br /> **Görünüm**<br /><br /> **Kare hızı**<br /> Etkinleştirildiğinde, tasarım yüzeyinin sağ üst köşesindeki kare hızını görüntüler. Kare hızı, saniye başına çizilen çerçeve sayısıdır. **İpucu:**  Son komutu yeniden çalıştırmak için **Gelişmiş** düğmesini seçebilirsiniz.|

 **Görüntü Düzenleyicisi** araç çubuğu aşağıda verilmiştir.

 ![Görüntü Düzenleyicisi araç çubuğu](../designers/media/digit-tre-toolbar.png "Basamak-TRE-araç çubuğu")

 Aşağıdaki tabloda, en üstten alta göründükleri sırada listelenen **Görüntü Düzenleyicisi** araç çubuğundaki öğeler açıklanmaktadır.

|Araç Çubuğu Öğesi|Description|
|------------------|-----------------|
|**Düğmede**|Diğer adı olan bir vuruş çizmek için etkin renk seçimini kullanır. **Özellikler** penceresinde konturun rengini ve kalınlığını ayarlayabilirsiniz.|
|**Fırçanın**|, İzin verilen bir kenar yumuşatma çizmek için etkin renk seçimini kullanır. **Özellikler** penceresinde konturun rengini ve kalınlığını ayarlayabilirsiniz.|
|**Boya tabancası**|, Görüntüyle birlikte karışan ve zaman içerisinde daha fazla doygun bir kenar yumuşatma içeren bir vuruş çizmek için etkin renk seçimini kullanır. **Özellikler** penceresinde konturun rengini ve kalınlığını ayarlayabilirsiniz.|
|**Damlalığı**|Etkin renk seçimini seçili pikselin rengine ayarlar.|
|**Doldur**|Görüntünün bir bölgesini dolduracak etkin renk seçimini kullanır. Etkilenen bölge, her pikselde aynı renkteki ve aynı rengin kendisi olan piksellerle bağlantılı olan her pikselle birlikte, dolgunun uygulandığı piksel olarak tanımlanır. Dolguyu etkin bir seçim içinde uygulanırsa, etkilenen bölge seçim tarafından sınırlandırılır.<br /><br /> Varsayılan olarak, etkin renk seçimi, Alfa bileşenine göre görüntünün etkilenen bölgesiyle birlikte karıştırılırdı. Etkilenen bölgenin üzerine yazmak üzere etkin renk seçimini kullanmak için, Fill aracını kullanırken SHIFT tuşuna basın ve basılı tutun.|
|**Silgi**|Resim bir alfa kanalını destekliyorsa, pikselleri tamamen saydam renge ayarlar. Aksi takdirde, pikselleri etkin arka plan rengine ayarlar.|
|**Çizgi**, **dikdörtgen**, **yuvarlatılmış dikdörtgen**, **elips**|Görüntüde bir şekil çizer. Ana hattın rengini ve kalınlığını **Özellikler** penceresinde ayarlayabilirsiniz.<br /><br /> Eşit genişliğe ve yüksekliğe sahip bir temel öğe çizmek için, çizerken SHIFT tuşuna basın ve basılı tutun.|
|**Metin**|Metin çizmek için ön plan rengi seçimini kullanır. Arka plan rengi, arka plan rengi seçimine göre belirlenir. Saydam bir arka plan için, arka plan rengi seçiminin alfa değeri 0 olmalıdır. Metin bölgesi etkin olsa da, metnin bir kenar yumuşatma ile çizilip çizilmeyeceğini ayarlayabilir ve **Özellikler** penceresinde metin **değeri**, **yazı tipi**, **Boyut**ve stil —**kalın**, **italik**veya **altı çizili**) ayarlayabilirsiniz. Metin bölgesi artık etkin olmadığında metnin içeriği ve görünümü sonlandırılır.|
|**Döndür**|Görüntüyü saat yönünde 90 derece döndürür.|
|**Kırpma**|Görüntüyü etkin seçime kırpar.|

### <a name="working-with-mip-levels"></a>MıP düzeyleriyle çalışma
 Bazı görüntü biçimleri — Örneğin, DirectDraw yüzeyi (. DDS) — doku alanı ayrıntı düzeyi (LOD) için MıP düzeylerini destekler. MıP düzeyleri oluşturma ve bunlarla çalışma hakkında daha fazla bilgi için bkz [. nasıl yapılır: MıP düzeyleri oluşturma ve değiştirme](../designers/how-to-create-and-modify-mip-levels.md)

### <a name="working-with-transparency"></a>Saydamlıkla çalışma
 Bazı görüntü biçimleri — Örneğin, DirectDraw yüzeyi (. DDS) — saydamlığı destekler. Kullandığınız araca bağlı olarak, saydamlığın kullanılabileceği birçok yol vardır. Bir renk seçimine ait saydamlık düzeyini belirtmek için, **Özellikler** penceresinde, renk seçiminin **a** (Alpha) bileşenini ayarlayın. Saydamlığın nasıl uygulandığını kontrol eden farklı araç türleri aşağıda verilmiştir:

|Araç|Açıklama|
|----------|-----------------|
|**Kurşun kalem**, **fırça**, **püskürtme**, **çizgi**, **dikdörtgen**, **yuvarlatılmış dikdörtgen**, **elips**, **metin**|Etkin renk seçimini görüntüyle birlikte Blend için, **Özellikler** penceresinde **Kanallar** özellik grubu ' nu genişletin ve **Alfa** kanalında **Çiz** onay kutusunu ayarlayın ve normal şekilde çizin.<br /><br /> Etkin renk seçimini kullanarak çizim yapmak ve görüntünün Alfa değerini yerinde bırakmak için, **Alfa** kanalının **Çizim** onay kutusunu temizleyin ve normal şekilde çizin.|
|**Doldur**|Etkin renk seçimini görüntüyle birlikte karıştırmak için, doldurmanız gereken alanı seçmeniz yeterlidir.<br /><br /> Alfa kanalının değeri de dahil olmak üzere etkin renk seçimini kullanmak için, resmin üzerine yazmak için SHIFT tuşuna basın ve basılı tutun ve ardından doldurulacak alanı seçin.|

### <a name="image-properties"></a><a name="ImageProperties"></a> Görüntü özellikleri
 Görüntünün çeşitli özelliklerini belirtmek için **Özellikler** penceresini kullanabilirsiniz. Örneğin, genişliği ve yüksekliği özelliklerini görüntüyü yeniden boyutlandırmak için ayarlayabilirsiniz.

 Aşağıdaki tabloda görüntü özellikleri açıklanmaktadır.

|Özellik|Açıklama|
|--------------|-----------------|
|Width|Resmin genişliği.|
|Height|Resmin yüksekliği.|
|Bit/piksel|Her pikseli temsil eden bit sayısı. Bu özelliğin değeri görüntünün **renk biçimine** bağlıdır.|
|Saydam seçim|Seçim katmanının Alfa değerine bağlı olarak, seçim katmanını ana görüntüyle birlikte karıştırmak için **true** ; Aksi takdirde, **false**. Bu öğe yalnızca Alpha destekleyen görüntülerde kullanılabilir.|
|Biçimlendir|Görüntünün renk biçimi. Görüntü biçimine bağlı olarak çeşitli renk biçimleri belirtilebilir. Renk biçimi, görüntüde yer alan renk kanalların sayısını ve türünü ve ayrıca çeşitli kanalların boyut ve kodlamasını tanımlar.|
|MIP düzeyi|Etkin MıP düzeyi. Bu öğe yalnızca MıP düzeylerine sahip dokularla kullanılabilir.|
|MİP düzeyi sayısı|Görüntüdeki MıP düzeylerinin toplam sayısı. Bu öğe yalnızca MıP düzeylerine sahip dokularla kullanılabilir.|
|Çerçeve sayısı|Görüntüdeki çerçevelerin toplam sayısı. Bu öğe yalnızca doku dizilerini destekleyen görüntülerde kullanılabilir.|
|Çerçeve|Geçerli çerçeve. Yalnızca ilk çerçeve görüntülenebilir; görüntü kaydedildiğinde diğer tüm çerçeveler kaybolur.|
|Derinlik dilimi sayısı|Görüntüdeki derinlik dilimlerinin toplam sayısı. Bu öğe yalnızca birim dokularını destekleyen görüntülerde kullanılabilir.|
|Derinlik dilimi|Geçerli derinlik dilimi. Yalnızca ilk dilim görüntülenebilir; görüntü kaydedildiğinde diğer tüm dilimler kaybedilir.|

> [!NOTE]
> **Döndürme** özelliği tüm araçlar ve seçili bölgeler için geçerli olduğundan, her zaman **Özellikler** penceresinin alt kısmında diğer araç özellikleriyle birlikte görüntülenir. Başka bir seçim veya etkin araç olmadığında tüm görüntü örtük olarak seçildiğinden, **Döndürme ölçütü** her zaman görüntülenir. **Döndürme** özelliği hakkında daha fazla bilgi için bkz. [araç özellikleri](#ToolProperties).

#### <a name="resizing-images"></a>Görüntüleri yeniden boyutlandırma
 Görüntüyü yeniden boyutlandırmanın iki yolu vardır. Her iki durumda da, görüntü Düzenleyicisi görüntüyü yeniden örneklemek için bı doğrusal ilişkilendirmeyi kullanır.

- **Özellikler** penceresinde **Genişlik** ve **Yükseklik** özellikleri için yeni değerler belirtin.

- Görüntüyü yeniden boyutlandırmak için görüntünün tamamını seçin ve kenarlık işaretçilerini kullanın.

### <a name="working-with-tools"></a>Araçlarla çalışma

#### <a name="selected-regions"></a>Seçili bölgeler
 Görüntü düzenleyicisinde seçimler etkin olan görüntünün bölgelerini tanımlar; diğer bir deyişle, bölge araçlar ve dönüşümlerden etkilenir. Etkin bir seçim olduğunda, seçilen bölgenin dışındaki bölgeler çoğu araç ve dönüşümden etkilenmez. Etkin bir seçim yoksa görüntünün tamamı etkin olur.

 Çoğu araç —**kurşun kalem**, **fırça**, **püskürtme**, **Fill**, **silgi**ve 2-b temel elemanlar — ve dönüşümler —**döndürme**, **kesme**, **renkleri ters**çevirme, **Yatay Çevir**ve **Dikey Çevir**—, etkin seçim tarafından sınırlandırılır veya tanımlanır. Ancak, bazı araçlar (**damlalık** ve **metin**ve dönüşümler —**MIPS oluştur**), herhangi bir etkin seçimden etkilenmez; Bu araçlar her zaman tüm görüntünün etkin seçim olduğu gibi davranır.

 Bir bölge seçerken, orantılı (kare) seçim yapmak için SHIFT tuşuna basabilir ve basılı tutabilirsiniz. Aksi takdirde, seçim kısıtlı değildir.

##### <a name="resizing-selections"></a>Seçimleri yeniden boyutlandırma
 Bir bölge seçtikten sonra seçim işaretçisinin boyutunu değiştirerek onu veya görüntü içeriğini yeniden boyutlandırabilirsiniz. Seçili bölgeyi yeniden boyutlandırırken, seçilen bölgenin yeniden boyutlandırılırken davranışını değiştirmek için aşağıdaki değiştirici tuşları kullanabilirsiniz (yeniden boyutlandırılırken tuşu basılı tutun).

 CTRL seçili bölgenin içeriğini yeniden boyutlandırmadan önce kopyalar. Bu, kopya yeniden boyutlandırılırken orijinal görüntüyü bozulmadan bırakır.

 SHIFT Seçili bölgeyi özgün boyutuna göre orantılı olarak yeniden boyutlandırır.

 Alt, seçim bölgesinin boyutunu değiştirir. Bu, görüntüyü değiştirilmemiş olarak bırakır.

 Geçerli değiştirici tuş bileşimleri şunlardır:

|Ctrl|Shift|Alt|Description|
|----------|-----------|---------|-----------------|
||||Seçili bölgenin içeriğini yeniden boyutlandırır.|
||Shift||Seçili bölgenin içeriğini orantılı olarak yeniden boyutlandırır.|
|||Alt|Seçili bölgeyi yeniden boyutlandırır. Bu, yeni bir seçim bölgesi tanımlar.|
||Shift|Alt|Seçili bölgeyi orantılı olarak yeniden boyutlandırır. Bu, yeni bir seçim bölgesi tanımlar.|
|Ctrl|||Seçili bölgenin içeriğini kopyalar ve sonra yeniden boyutlandırır.|
|Ctrl|Shift||Seçili bölgenin içeriğini kopyalar ve daha sonra orantılı olarak yeniden boyutlandırır.|

#### <a name="tool-properties"></a><a name="ToolProperties"></a> Araç özellikleri
 Bir araç seçiliyken, görüntü nasıl etkilediği hakkındaki ayrıntıları belirtmek için **Özellikler** penceresini kullanabilirsiniz. Örneğin, **kurşun kalem** aracının kalınlığını veya **fırça** aracının rengini ayarlayabilirsiniz.

 Hem ön plan rengi hem de arka plan rengi ayarlayabilirsiniz. Her ikisi de Kullanıcı tanımlı opaklık sağlamak için bir alfa kanalını destekler. Ayarlar tüm araçlara uygulanır. Fare kullanıyorsanız sol fare düğmesi ön plan rengine karşılık gelir ve sağ fare düğmesi arka plan rengine karşılık gelir.

 Aşağıdaki tabloda araç özellikleri açıklanmaktadır.

|Araç|Özellikler|
|----------|----------------|
|Tüm araçlar ve seçimler|**Döndürme ölçütü**<br /> Seçim ya da araç efektinin saatin saat yönünde döndürüldüğü miktarı derece cinsinden tanımlar.|
|**Kurşun kalem**, **fırça**, **püskürtme**, **silgi**|**Kalınlık**<br /> Araçtan etkilenen alanın boyutunu tanımlar.|
|**Metin**|**Kenar yumuşatma**<br /> Daha fazla kenar yumuşatma uygulanmış kenarları olan metni çizer. Bu metin daha yumuşak bir görünüm sağlar.<br /><br /> **Değer**<br /> Çizilecek metin.<br /><br /> **Yazı tipi**<br /> Metni çizmek için kullanılan yazı tipi.<br /><br /> **Boyut**<br /> Metnin boyutu.<br /><br /> **Kalın**<br /> Yazı tipini kalın yapar.<br /><br /> **İtalik**<br /> Yazı tipini italik yapar.<br /><br /> **Çiz**<br /> Yazı tipi altı çizili hale gelir.|
|**2-b temel**|**Kenar yumuşatma**<br /> Kenar yumuşatma uygulanmış kenarları olan temel türleri çizer. Böylece daha yumuşak bir görünüm elde edin.<br /><br /> **Kalınlık**<br /> Temel öğesinin sınırını oluşturan çizginin kalınlığını tanımlar.<br /><br /> **Yarıçap X**<br /> (Yalnızca yuvarlatılmış dikdörtgen) Temel öğesinin üst ve alt kenarları için yuvarlama yarıçapını tanımlar.<br /><br /> **Yarıçap Y**<br /> (Yalnızca yuvarlatılmış dikdörtgen) Temel öğesinin sol ve sağ kenarları için yuvarlama yarıçapını tanımlar.|
|**Kurşun kalem**, **fırça**, **püskürtme**, **2-b temel**|**Kanallar**<br /> Görüntüleme ve çizim için belirli renk kanallarını etkinleştirip devre dışı bırakır. Belirli bir renk kanalı için **Görünüm** ayarlandıysa, bu kanal görüntüde görünür; Aksi takdirde, görünür değildir. Belirli bir renk kanalı için **Çizim** ayarlandıysa, bu kanal çizim işlemleri tarafından etkilenir; Aksi takdirde, değildir.|
|**Değnek seçimi**, **dolgusu**|**Payı**<br /> Etkilenen veya seçilen bölgenin bir parçası olarak daha az veya daha fazla benzer renge sahip olduğu için, benzer olarak kabul edildiği bitişik renkler arasındaki en büyük farkı tanımlar. Varsayılan olarak, değer 32 ' dir. Bu, orijinal rengin 32 gölgeler (daha açık veya daha koyu) içindeki bitişik piksellerin bölgenin parçası olarak kabul edildiği anlamına gelir.|

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

|Komut|Klavye kısayolları|
|-------------|------------------------|
|**Seçme** moduna geçiş yap|S|
|**Yakınlaştırma** moduna geç|Z|
|**Pan** moduna geç|K|
|Tümünü seç|Ctrl+A|
|Geçerli seçimi sil|Sil|
|Geçerli seçimi iptal et|Esc|
|Yakınlaştır|Ctrl+Fare tekerleği ileriye doğru<br /><br /> Ctrl+PageUp<br /><br /> Artı İşareti (+)|
|Uzaklaştır|Ctrl-fare tekerleği geriye doğru<br /><br /> CTRL-Pageaşağı<br /><br /> Eksi İşareti (-)|
|Görüntüyü yukarı kaydır|Fare tekerleği geriye doğru<br /><br /> PageDown|
|Görüntüyü aşağı kaydır|Fare tekerleği ileriye doğru<br /><br /> PageUp|
|Görüntüyü sola kaydır|Shift+Fare tekerleği geriye doğru<br /><br /> Fare tekerleği sol<br /><br /> SHIFT + Pageaşağı|
|Görüntüyü sağa kaydır|Shift+Fare tekerleği ileriye doğru<br /><br /> Fare tekerleği sağ<br /><br /> SHIFT + PageUp|
|Gerçek boyuta Yakınlaştır|CTRL + 0 (sıfır)|
|Görüntüyü pencereye sığdır|CTRL + G, CTRL + F|
|Görüntüyü pencere genişliğine Sığdır|CTRL + G, CTRL + ı|
|Kılavuza geç|CTRL + G, CTRL + G|
|Görüntüyü geçerli seçime Kırp|CTRL + G, CTRL + C|
|Sonrakini görüntüle (daha yüksek ayrıntı) MıP düzeyi|CTRL + G, CTRL + 6|
|Öncekini görüntüle (düşük ayrıntı) MıP düzeyi|CTRL + G, CTRL + 7|
|Kırmızı renk kanalını değiştirme|CTRL + G, CTRL + 1|
|Yeşil renk kanalını aç|CTRL + G, CTRL + 2|
|Mavi renk kanalını aç|CTRL + G, CTRL + 3|
|Alfa (saydam) kanalını değiştirme|CTRL + G, Ctrl + 4|
|Alfa dama tahtası düzenine geç|CTRL + G, CTRL + B|
|Düzensiz seçim aracına geç|L|
|Değnek seçim aracına geç|M|
|Kurşun Kalem aracına geç|P|
|Fırça aracına geç|B|
|Fill aracına geç|F|
|Silgi aracına geç|E|
|Metin aracına geç|T|
|Renk seç (damlalık) aracına geç|I|
|Etkin seçimi ve içeriğini taşıyın.|Ok tuşları.|
|Etkin seçimi ve içeriğini yeniden boyutlandırın.|CTRL + ok tuşları|
|Etkin seçimi taşıyın, ancak içeriğini değil.|SHIFT + ok tuşları|
|Etkin seçimi yeniden boyutlandırın, ancak içeriğini değil.|SHIFT + CTRL + ok tuşları|
|Geçerli katmanı Yürüt|Döndürülmesini|
|Araç kalınlığını azalt|[|
|Araç kalınlığını artır|]|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Oyunlar ve Uygulamalar için 3B Varlıklarla Çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Dokular ve görüntüler, 3-b modeller ve gölgelendirici efektleri gibi grafik varlıklarıyla çalışmak için kullanabileceğiniz araçlara genel bir bakış sağlar.|
|[Model Düzenleyicisi](../designers/model-editor.md)|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]3B modellerle çalışmak için model düzenleyicisinin nasıl kullanılacağını açıklar.|
|[Gölgelendirici Tasarımcısı](../designers/shader-designer.md)|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Gölgelendiricilerle çalışmak için Gölgelendirici Tasarımcısının nasıl kullanılacağını açıklar.|
