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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589324"
---
# <a name="image-editor"></a>Görüntü düzenleyicisi

Bu makalede, doku ve görüntü kaynaklarını görüntülemek ve değiştirmek için Visual Studio **Image Editor** ile nasıl çalışılalış ları açıklanmaktadır.

**DirectX** uygulama geliştirmede kullanılan zengin doku ve görüntü biçimleri yle çalışmak için Görüntü Düzenleyicisi'ni kullanabilirsiniz. Bu, popüler görüntü dosyası biçimleri ve renk kodlamaları, alfa kanalları ve MIP eşleme gibi özellikler ve DirectX'in desteklediği yüksek oranda sıkıştırılmış, donanım hızlandırılmış doku biçimlerinin çoğunu destekler.

## <a name="supported-formats"></a>Desteklenen biçimler

**Görüntü Düzenleyicisi** aşağıdaki görüntü biçimlerini destekler:

|Biçim lendirme adı|Dosya Adı Uzantısı|
|-----------------| - |
|Taşınabilir Ağ Grafikleri|*Png*|
|JPEG|*.jpg*, *.jpeg*, *.jpe*, *.jfif*|
|Doğrudan Çekme Yüzeyi|*.dds*|
|Grafik Değişim Biçimi|*Gif*|
|Bitmap|*.bmp*, *.dib*|
|Tagged Resim Dosya Biçimi|*.tif*, *.tiff*|
|TGA (Targa)|*.tga*|

## <a name="get-started"></a>Kullanmaya başlayın

Bu bölümde, Visual Studio projenize nasıl bir görüntü ekleyeceğiniz ve gereksinimlerinize göre nasıl yapılandırılabildiğini açıklanmaktadır.

### <a name="add-an-image-to-your-project"></a>Projenize resim ekleme

1. **Çözüm Gezgini'nde,** görüntüyü eklemek istediğiniz proje için kısayol menüsünü açın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.

2. **Yüklü**, **Grafik**seçin ve ardından görüntü için uygun bir dosya biçimi seçin, Yeni **Öğe Ekle** iletişim kutusunda.

   > [!NOTE]
   > **Yeni Öğe Ekle** iletişim kutusunda **Grafik** kategorisini görmüyorsanız, Resim ve **3B model düzenleyicileri** bileşenini yüklemeniz gerekebilir. İletişim kutusunu kapatın ve **ardından Visual Studio Installer'ı**açmak için menü çubuğundan **Araçlar** > **Alın Araçları ve Özellikleri** seçin. Bireysel **bileşenler** sekmesini seçin ve ardından **Oyunlar ve Grafikler** kategorisi altında Resim ve **3B model düzenleyiciler** bileşenini seçin. **Değiştir'i**seçin.
   >
   > ![Resim ve 3B model editörleri bileşeni](media/image-3d-model-editors-component.png)

   Gereksinimlerinize göre dosya biçimini nasıl seçeceğiniz hakkında bilgi [için](#choose-the-image-format)bkz.

3. Resim dosyasının **Adını** ve oluşturulmasını istediğiniz **Konumu** belirtin.

4. **Ekle** düğmesini seçin.

### <a name="choose-the-image-format"></a>Resim biçimini seçin

Görüntüyü nasıl kullanmayı planladığınız bağlı olarak, belirli dosya biçimleri diğerlerinden daha uygun olabilir. Örneğin, bazı biçimler saydamlık veya belirli bir renk biçimi gibi gereksinim duyduğunuz bir özelliği desteklemeyebilir. Bazı biçimler, planladığınız görüntü içeriği türü için uygun sıkıştırma sağlamayabilir.

Aşağıdaki bilgiler, gereksinimlerinizi karşılayan bir resim biçimi seçmenize yardımcı olabilir:

**Bitmap Görüntü (.bmp)**

Bitmap görüntü biçimi. 24 bit rengi destekleyen sıkıştırılmamış görüntü biçimi. Bitmap biçimi saydamlığı desteklemez.

**GIF Görüntü (.gif)**

Grafik Değişim Biçimi (GIF) görüntü biçimi. 256 renge kadar destekleyen LZW sıkıştırılmış, kayıpsız görüntü biçimi. Önemli miktarda renk ayrıntısına sahip fotoğraflar ve görüntüler için uygun olmayan, ancak yüksek renk tutarlılığına sahip düşük renkli görüntüler için iyi sıkıştırma oranları sağlar.

**JPG Görüntü (.jpg)**

Ortak Fotoğraf Uzmanları Grubu (JPEG) görüntü biçimi. 24 bit rengi destekleyen ve yüksek renk tutarlılığına sahip görüntülerin genel amaçlı sıkıştırması için son derece sıkıştırılmış, kayıplı görüntü biçimi.

**PNG Görüntü (.png)**

Taşınabilir Ağ Grafikleri (PNG) görüntü biçimi. 24 bit renk ve alfa saydamlığı destekleyen orta düzeyde sıkıştırılmış, kayıpsız görüntü biçimi. Hem doğal hem de yapay görüntüler için uygundur, ancak JPG veya GIF gibi kayıplı biçimler kadar iyi sıkıştırma oranları sağlamaz.

**TIFF Görüntü (.tif)**

Etiketli Resim Dosyası Biçimi (TIFF veya TIF) görüntü biçimi. Birkaç sıkıştırma düzenini destekleyen esnek bir görüntü biçimi.

**DDS Doku (.dds)**

DirectDraw Surface (DDS) doku biçimi. 24 bit renk ve alfa saydamlığı destekleyen son derece sıkıştırılmış, kayıplı doku biçimi. Sıkıştırma oranları 8:1'e kadar çıkabilir. Grafik donanımında sıkıştırılabilen S3 Doku sıkıştırmaya dayanır.

**TGA Görüntü (.tga)**

Truevision Grafik Bağdaştırıcısı (TGA) görüntü biçimi (Targa olarak da bilinir). RLE sıkıştırılmış, kayıpsız görüntü biçimi, hem renk eşlenmiş (renk paleti) hem de 24 bit'e kadar renk ve alfa saydamlığı yla doğrudan renkli görüntüleri destekler. Önemli miktarda renk ayrıntısına sahip fotoğraflar ve görüntüler için uygun değildir, ancak aynı renklerde uzun aralıklara sahip görüntüler için iyi sıkıştırma oranları sağlar.

### <a name="configure-the-image"></a>Görüntüyü yapılandırma

Oluşturduğunuz resimle çalışmaya başlamadan önce varsayılan yapılandırmasını değiştirebilirsiniz. Örneğin, boyutlarını veya kullandığı renk biçimini değiştirebilirsiniz. Görüntünün bu ve diğer özelliklerinin nasıl yapılandırılabildiğini öğrenmek için [Resim özelliklerine](#image-properties)bakın.

> [!NOTE]
> Çalışmanızı kaydetmeden önce, belirli bir renk biçimi kullanmak istiyorsanız **Renk Biçimi** özelliğini ayarladığınızdan emin olun. Dosya biçimi sıkıştırmayı destekliyorsa, dosyayı ilk kez kaydettiğinizde veya Farklı **Kaydet'i**seçtiğinizde sıkıştırma ayarlarını ayarlayabilirsiniz.

## <a name="work-with-the-image-editor"></a>Görüntü Düzenleyicisi ile çalışma

Bu bölümde, dokuları ve görüntüleri değiştirmek için **Görüntü Düzenleyicisi** nasıl kullanılacağı açıklanmaktadır.

**Görüntü** Düzenleyicisi'nin durumunu etkileyen komutlar, gelişmiş komutlarla birlikte **Görüntü Düzenleyicisi Modu** araç çubuğunda bulunur. Araç çubuğu, **Görüntü Düzenleyicisi** tasarım yüzeyinin en üst kenarı boyunca yer alır. Çizim araçları, **Görüntü Düzenleyicisi** tasarım yüzeyinin en sol kenarı boyunca **Görüntü Düzenleyicisi** araç çubuğunda bulunur.

### <a name="image-editor-mode-toolbar"></a>Görüntü Düzenleyici modu araç çubuğu

![Visual Studio'da Görüntü Düzenleyicisi modu araç çubuğu](../designers/media/digit-tre-modal-toolbar.png)

Aşağıdaki tabloda, Resim **Düzenleyicisi Modu** araç çubuğundaki soldan sağa doğru göründükleri sırada listelenen öğeler açıklanmaktadır:

|Araç Çubuğu Öğesi|Açıklama|
|------------------|-----------------|
|**Seç**|Görüntünün dikdörtgen bir bölgesinin seçilmesini sağlar. Bir bölgeyi seçtikten sonra, bölgeyi kesebilir, kopyalayabilir, taşıyabilir, ölçeklendirebilir, döndürebilir, çevirebilir veya silebilirsiniz. Etkin bir seçim olduğunda, çizim araçları yalnızca seçili bölgeyi etkiler.|
|**Düzensiz Seçim**|Görüntünün düzensiz bir bölgesinin seçilmesini sağlar. Bir bölgeyi seçtikten sonra, bölgeyi kesebilir, kopyalayabilir, taşıyabilir, ölçeklendirebilir, döndürebilir, çevirebilir veya silebilirsiniz. Etkin bir seçim olduğunda, çizim araçları yalnızca seçili bölgeyi etkiler.|
|**Değnek Seçimi**|Görüntünün benzer şekilde renkli bir bölgesinin seçilmesini sağlar. *Tolerans*(diğer bir şekilde, benzer olarak kabul edildikleri bitişik renkler arasındaki maksimum fark) daha küçük veya daha geniş bir benzer renk aralığı içerecek şekilde yapılandırılabilir. Bir bölgeyi seçtikten sonra, bölgeyi kesebilir, kopyalayabilir, taşıyabilir, ölçeklendirebilir, döndürebilir, çevirebilir veya silebilirsiniz. Etkin bir seçim olduğunda, çizim araçları yalnızca seçili bölgeyi etkiler.|
|**Pan**|Görüntünün pencere çerçevesine göre hareketini sağlar. **Kaydırma** modunda, görüntüüzerinde bir nokta seçin ve sonra hareket ettirin.<br /><br /> **Ctrl** **tuşuna** basıp basılı tutarak Pan modunu geçici olarak etkinleştirebilirsiniz.|
|**Zoom**|Pencere çerçevesine göre az ya da çok görüntü ayrıntısının görüntülenmesini sağlar. **Yakınlaştırma** modunda, görüntüüzerinde bir nokta seçin ve yakınlaştırmak için sağa veya aşağı veya uzaklaştırmak için sağa veya aşağı taşıyın.<br /><br /> Fare tekerleğini kullanırken **Ctrl** tuşuna basarak veya artı işaretine (**+**) veya**-** eksi işaretine () basarak yakınlaştırabilir veya uzaklaştırabilirsiniz.|
|**Gerçek Boyuta Yakınlaştırma**|Görüntünün pikselleri ile ekranın pikselleri arasında 1:1 ilişkisi kullanarak görüntüyü görüntüler.|
|**Sığdırmak Için Yakınlaştırma**|Pencere çerçevesinde tam görüntüyü görüntüler.|
|**Genişliğe Yakınlaştırma**|Pencere çerçevesinde görüntünün tam genişliğini görüntüler.|
|**Kılavuz**|Piksel sınırlarını gösteren ızgarayı etkinleştirir veya devre dışı kılabilir. Görüntüye yakınlaştırana kadar ızgara görünmeyebilir.|
|**Sonraki MIP Seviyesini Görüntüle**|MIP harita zincirindeki bir sonraki büyük MIP düzeyini etkinleştirir. Etkin MIP düzeyi tasarım yüzeyinde görüntülenir. Bu öğe yalnızca MIP düzeylerine sahip dokular için kullanılabilir.|
|**Önceki MIP Düzeyini Görüntüle**|Bir MIP harita zincirindeki bir sonraki küçük MIP düzeyini etkinleştirir. Etkin MIP düzeyi tasarım yüzeyinde görüntülenir. Bu öğe yalnızca MIP düzeylerine sahip dokular için kullanılabilir.|
|**Kırmızı Kanal**<br /><br /> **Yeşil Kanal**<br /><br /> **Mavi Kanal**<br /><br /> **Alfa Kanalı**|Belirli renk kanalını etkinleştirer veya devre dışı kılabilir. **Not:**  Renk kanallarını sistematik olarak etkinleştirerek veya devre dışı bırakarak, bunlardan biriyle veya daha fazlası ile ilgili sorunları yalıtabilirsiniz. Örneğin, yanlış alfa saydamlığı tanımlayabilirsiniz.|
|**Arka plan**|Görüntünün saydam bölümleri aracılığıyla arka planın görüntülenmesini sağlar veya devre dışı eder. Bu seçeneklerden birini seçerek arka planın nasıl görüntüleneceğini yapılandırabilirsiniz:<br /><br /> **Dama**<br /> Arka planı dama tahtası deseni olarak görüntülemek için belirtilen arka plan rengiyle birlikte yeşil renk kullanır. Görüntünün saydam bölümlerini daha belirgin hale getirmeye yardımcı olmak için bu seçeneği kullanabilirsiniz.<br /><br /> Beyaz Arka Plan<br /> Arka planı görüntülemek için beyaz rengi kullanır.<br /><br /> Siyah Arka Plan<br /> Arka planı görüntülemek için siyah rengi kullanır.<br /><br /> Arka Plana Animasyon<br /> Pans dama tahtası deseni yavaş yavaş. Görüntünün saydam bölümlerini daha belirgin hale getirmeye yardımcı olmak için bu seçeneği kullanabilirsiniz.|
|**Özellikler**|Özellikler **penceresini** dönüşümlü olarak açar veya kapatır.|
|**Gelişmiş**|Ek komutlar ve seçenekler içerir.<br /><br /> **Filtreler**<br /><br /> Birkaç yaygın görüntü filtreleri sağlar: **Siyah ve Beyaz,** **Bulanıklaştırma,** **Parlaklık**, **Koy,** **Kenar Algılama**, **Kabartma**, Renkleri **Ters ,** **Dalgalanma**, **Sepya Sesi**, ve **Keskinleştirmek**.<br /><br /> **Grafik Motorları**<br /><br /> **D3D11 ile işleme**<br /> **Görüntü Düzenleyicisi** tasarım yüzeyini işlemek için Direct3D 11 kullanır.<br /><br /> **D3D11WARP ile işleme**<br /> **Görüntü Düzenleyicisi** tasarım yüzeyini işlemek için Direct3D 11 Windows Advanced Rasterization Platform (WARP) kullanır.<br /><br /> **Araçlar**<br /><br /> **Yatay Çevirme**<br /> Görüntüyü yatay veya x ekseni etrafında aktarır.<br /><br /> **Dikey Çevirme**<br /> Görüntüyü dikey veya y ekseni etrafında aktarır.<br /><br /> **Mips oluşturun**<br /> Görüntü için MIP düzeyleri oluşturur. MIP düzeyleri zaten varsa, bunlar en büyük MIP düzeyinden yeniden oluşturulur. Daha küçük MIP düzeylerinde yapılan tüm değişiklikler kaybolur. Oluşturduğunuz MIP düzeylerini kaydetmek için görüntüyü kaydetmek için *.dds* biçimini kullanmanız gerekir.<br /><br /> **Görünüm**<br /><br /> **Kare Hızı**<br /> Etkinleştirildiğinde, tasarım yüzeyinin sağ üst köşesinde ki kare hızını görüntüler. Kare hızı, saniye başına çizilen çerçeve sayısıdır. **İpucu:** Son komutu yeniden çalıştırmak için **Gelişmiş** düğmesini seçebilirsiniz.|

### <a name="image-editor-toolbar"></a>Görüntü Düzenleyiciaraç Çubuğu

![Görüntü Düzenleyiciaraç Çubuğu](../designers/media/digit-tre-toolbar.png)

Aşağıdaki tabloda, Resim **Düzenleyicisi** araç çubuğundaki yukarıdan aşağıya doğru göründükleri sırada listelenen öğeler açıklanmaktadır:

|Araç Çubuğu Öğesi|Açıklama|
|------------------|-----------------|
|**Kalem**|Takma bir kontur çizmek için etkin renk seçimini kullanır. **Konturun** rengini ve kalınlığını Özellikler penceresinde ayarlayabilirsiniz.|
|**Fırça**|Takma adla karşılanmış bir kontur çizmek için etkin renk seçimini kullanır. **Konturun** rengini ve kalınlığını Özellikler penceresinde ayarlayabilirsiniz.|
|**Airbrush**|Görüntüyle biraraya gelen ve zamanın bir işlevi olarak daha doygun hale gelen bir takma adla yapılan bir kontur çizmek için etkin renk seçimini kullanır. **Konturun** rengini ve kalınlığını Özellikler penceresinde ayarlayabilirsiniz.|
|**Damlalık**|Etkin renk seçimini seçili pikselin rengine ayarlar.|
|**Doldurmak**|Görüntünün bir bölgesini doldurmak için etkin renk seçimini kullanır. Etkilenen bölge, dolgunun uygulandığı piksel olarak tanımlanır ve aynı renkteki piksellerle ona bağlanan ve aynı rengin kendisi olan her pikselle birlikte. Dolgu etkin bir seçim içinde uygulanırsa, etkilenen bölge seçimle sınırlandırılır.<br /><br /> Varsayılan olarak, etkin renk seçimi alfa bileşenine göre görüntünün etkilenen bölgesiyle karıştırılır. Etkilenen bölgenin üzerine yazmak için etkin renk seçimini kullanmak için, dolgu aracını kullanırken **Shift** tuşuna basın ve basılı tutun.|
|**Silgi**|Görüntü bir alfa kanalını destekliyorsa pikselleri tam saydam renge ayarlar. Aksi takdirde, pikselleri etkin arka plan rengine ayarlar.|
|**Çizgi**, **Dikdörtgen**, **Yuvarlak Dikdörtgen**, **Elips**|Görüntüüzerinde bir şekil çizer. **Özellikler** penceresinde anahattın rengini ve kalınlığını ayarlayabilirsiniz.<br /><br /> Eşit genişlik ve yüksekliğe sahip bir ilkel çizmek için, çizerken **Shift** tuşuna basın ve basılı tutun.|
|**Metin**|Metin çizmek için ön plan renk seçimini kullanır. Arka plan rengi, arka plan renk seçimi ile belirlenir. Saydam bir arka plan için, arka plan renk seçiminin alfa değeri 0 olmalıdır. Metin bölgesi etkin olsa da, metnin diğer adı olmayan bir konturla çizilip çizilmediğini ayarlayabilir ve **Özellikler** penceresinde **Değer,** **Yazı Tipi**, **Boyut**ve stil-**Kalın,** **Italik**ler veya **Altı Çizili**metin ayarlayabilirsiniz. Metin bölgesi artık etkin olmadığında metnin içeriği ve görünümü tamamlanır.|
|**Döndür**|Görüntüyü saat yönünde 90 derece döndürür.|
|**Döşeme**|Görüntüyü etkin seçime kırpıyor.|

### <a name="work-with-mip-levels"></a>MIP düzeyleriyle çalışma

Bazı görüntü biçimleri, örneğin, DirectDraw Surface (*.dds*), doku-boşluk Düzey-of-Detail (LOD) için MIP düzeylerini destekler. MIP düzeylerini oluşturma ve onlarla nasıl çalışacağı hakkında bilgi için [bkz: MIP düzeylerini oluşturma ve değiştirme](../designers/how-to-create-and-modify-mip-levels.md)

### <a name="work-with-transparency"></a>Saydamlıkla çalışma

Bazı görüntü biçimleri, örneğin, DirectDraw Surface (*.dds*), saydamlığı destekler. Kullandığınız araca bağlı olarak saydamlığı kullanabileceğiniz çeşitli yöntemler vardır. **Özellikler** penceresinde, renk seçimi için saydamlık düzeyini belirtmek için renk seçiminin **A** (alfa) bileşenini ayarlayın.

Aşağıdaki tabloda, farklı araç türlerinin saydamlığın nasıl uygulandığını nasıl denetlenen açıklanmaktadır:

|Araç|Açıklama|
|----------|-----------------|
|**Kalem**, **Fırça**, **Airbrush**, **Çizgi**, **Dikdörtgen**, **Yuvarlak Dikdörtgen**, **Elips**, **Metin**|Etkin renk seçimini görüntüyle birleştirmek için **Özellikler** penceresinde, **Kanallar** özellik grubunu genişletin ve **Alfa** kanalındaki **Draw** onay kutusunu ayarlayın ve normal çizin.<br /><br /> Etkin renk seçimini kullanarak çizmek ve görüntünün alfa değerini yerinde bırakmak için **Alfa** kanalının **Beraberlik** onay kutusunu temizleyin ve normal çizin.|
|**Doldurmak**|Etkin renk seçimini görüntüyle birleştirmek için doldurulacak alanı seçmeniz.<br /><br /> Görüntünün üzerine yazmak için alfa kanalının değeri de dahil olmak üzere etkin renk seçimini kullanmak için **Shift** tuşuna basın ve basılı tutun ve ardından doldurulacak alanı seçin.|

### <a name="image-properties"></a>Görüntü özellikleri

Görüntünün çeşitli özelliklerini belirtmek için **Özellikler** penceresini kullanabilirsiniz. Örneğin, görüntüyü yeniden boyutlandırmak için genişlik ve yükseklik özelliklerini ayarlayabilirsiniz.

Aşağıdaki tabloda görüntü özellikleri açıklanmaktadır:

|Özellik|Açıklama|
|--------------|-----------------|
|Genişlik|Görüntünün genişliği.|
|Height|Görüntünün yüksekliği.|
|Piksel Başına Bit|Her pikseli temsil eden bit sayısı. Bu özelliğin değeri görüntünün **Renk Biçimine** bağlıdır.|
|Saydam Seçim|**True** Seçim katmanının alfa değerine bağlı olarak seçim katmanını ana görüntüyle karıştırmak doğru; aksi takdirde, **False**. Bu öğe yalnızca alfayı destekleyen görüntüler için kullanılabilir.|
|Biçimlendir|Görüntünün renk biçimi. Görüntü biçimine bağlı olarak çeşitli renk biçimleri belirtebilirsiniz. Renk biçimi, görüntüde bulunan renk kanallarının sayısını ve türünü ve ayrıca çeşitli kanalların boyutunu ve kodlayıcısını tanımlar.|
|Mip Seviyesi|Etkin MIP düzeyi. Bu öğe yalnızca MIP düzeylerine sahip dokular için kullanılabilir.|
|Mip Seviye Sayısı|Görüntüdeki toplam MIP düzeyi sayısı. Bu öğe yalnızca MIP düzeylerine sahip dokular için kullanılabilir.|
|Çerçeve Sayısı|Görüntüdeki toplam kare sayısı. Bu öğe yalnızca doku dizilerini destekleyen görüntüler için kullanılabilir.|
|Çerçeve|Geçerli çerçeve. Yalnızca ilk kare görüntülenebilir; görüntü kaydedildiğinde diğer tüm kareler kaybolur.|
|Derinlik Dilim Sayısı|Görüntüdeki toplam derinlik dilimi sayısı. Bu öğe yalnızca birim dokularını destekleyen görüntüler için kullanılabilir.|
|Derinlik Dilimi|Geçerli derinlik dilimi. Yalnızca ilk dilim görüntülenebilir; görüntüyü kaydettiğinizde diğer tüm dilimler kaybolur.|

> [!NOTE]
> **Özelliğine Göre Döndürme** tüm araçlar ve seçili bölgeler için geçerli olduğundan, her zaman diğer araç özellikleriyle birlikte **Özellikler** penceresinin alt kısmında görünür. Başka bir seçim veya etkin araç olmadığında görüntünün tamamı örtülü olarak **seçildiğinden, döndürülme** her zaman görüntülenir. Özelliğine Göre **Döndürme** hakkında daha fazla bilgi [için, Bkz. Araç özellikleri.](#tool -properties)

### <a name="resize-images"></a>Görüntüleri yeniden boyutlandırma

Görüntüyü yeniden boyutlandırmanın iki yolu vardır. Her iki durumda da, **Görüntü Düzenleyicisi** görüntüyü yeniden örneklemek için çift doğrusal enterpolasyon kullanır.

- **Özellikler** penceresinde, **Genişlik** ve **Yükseklik** özellikleri için yeni değerler belirtin.

- Resmin tamamını seçin ve görüntüyü yeniden boyutlandırmak için kenarlık işaretçilerini kullanın.

### <a name="selected-regions"></a>Seçili bölgeler

**Görüntü** Düzenleyicisi'ndeki seçimler, görüntünün etkin olan bölgelerini tanımlar. Etkin bölgeler araçlardan ve dönüşümlerden etkilenir. Etkin bir seçim olduğunda, seçili bölgenin dışındaki alanlar çoğu araç ve dönüşümden etkilenmez. Etkin bir seçim yoksa, görüntünün tamamı etkindir.

Çoğu araç **(Kalem,** **Fırça,** **Airbrush**, **Dolgu**, **Silgi**, ve 2D primitives) ve dönüşümler **(Döndürme**, **Kırpma**, **Renkleri Ters Çevir**, Yatay **Çevir**ve **Dikey Çevir**) sınırlı veya aktif seçim tarafından tanımlanır. Ancak, bazı araçlar **(Eyedropr** ve **Text)** ve dönüşümler **(Mips oluştur)** herhangi bir etkin seçim etkilenmez. Bu araçlar her zaman görüntünün tamamı etkin seçimmiş gibi olur.

Bir bölge seçerken, orantılı (kare) seçim yapmak için **Shift** tuşuna basıp basılı tutabilirsiniz. Aksi takdirde, seçim kısıtlanmış değildir.

#### <a name="resize-selections"></a>Seçimleri yeniden boyutlandırma

Bir bölge seçtikten sonra, seçim işaretçisinin boyutunu değiştirerek onu veya görüntü içeriğini yeniden boyutlandırabilirsiniz. Seçili bölgeyi yeniden boyutlandırma yaparken, seçili bölgenin davranışını değiştirmek için aşağıdaki değiştirici anahtarlarını kullanabilirsiniz:

**Ctrl** - Seçili bölgenin içeriğini yeniden boyutlandırilmeden önce kopyalar. Bu, kopya yeniden boyutlandırılırken orijinal görüntüyü bozulmadan bırakır.

**Shift** - Seçili bölgeyi özgün boyutuyla orantılı olarak yeniden boyutlandırıyor.

**Alt** - Seçim bölgesinin boyutunu değiştirir. Bu, görüntüyü değiştirilmemiş bırakır.

Aşağıdaki tabloda geçerli değiştirici anahtar kombinasyonları açıklanmaktadır:

|Ctrl|Shift|Alt|Açıklama|
|----------|-----------|---------|-----------------|
||||Seçili bölgenin içeriğini yeniden boyutlandırıyor.|
||**Shift**||Seçili bölgenin içeriğini orantılı olarak yeniden boyutlandırıyor.|
|||**Alt**|Seçili bölgeyi yeniden boyutlandırıyor. Bu, yeni bir seçim bölgesi tanımlar.|
||**Shift**|**Alt**|Seçili bölgeyi orantılı olarak yeniden boyutlandırıyor. Bu, yeni bir seçim bölgesi tanımlar.|
|**Ctrl**|||Seçili bölgenin içeriğini kopyalar ve yeniden boyutlandırır.|
|**Ctrl**|**Shift**||Seçili bölgenin içeriğini kopyalar ve orantılı olarak yeniden boyutlandırır.|

### <a name="tool-properties"></a>Takım özellikleri

Bir araç seçiliyken, görüntüyü nasıl etkilediğine ilişkin ayrıntıları belirtmek için **Özellikler** penceresini kullanabilirsiniz. Örneğin, **Kalem** aracının kalınlığını veya **Fırça** aracının rengini ayarlayabilirsiniz.

Hem ön plan rengini hem de arka plan rengini ayarlayabilirsiniz. Her ikisi de kullanıcı tanımlı opaklık sağlamak için bir alfa kanal desteği. Ayarlar tüm araçlar için geçerlidir. Fare kullanıyorsanız, sol fare düğmesi ön plan rengine, sağ fare düğmesi ise arka plan rengine karşılık gelir.

Aşağıdaki tabloda araç özellikleri açıklanmaktadır:

|Araç|Özellikler|
|----------|----------------|
|Tüm araçlar ve seçimler|**Tarafından döndür**<br /> Seçim veya takım efektinin saat yönünde döndürüldürün derece olarak miktarını tanımlar.|
|**Kalem**, **Fırça**, **Airbrush**, **Silgi**|**Kalınlık**<br /> Araçtan etkilenen alanın boyutunu tanımlar.|
|**Metin**|**Kenar yumuşatma**<br /> Takma ad karşıtı kenarları olan metin çizer. Bu metin daha düzgün bir görünüm verir.<br /><br /> **Değer**<br /> Çizilecek metin.<br /><br /> **Yazı tipi**<br /> Metni çizmek için kullanılan yazı tipi.<br /><br /> **Boyut**<br /> Metnin boyutu.<br /><br /> **Kalın**<br /> Yazı tipini kalın laştırır.<br /><br /> **Italik**<br /> Yazı tipiitalik yapar.<br /><br /> **Altı çizili**<br /> Yazı tipini altı çizili yapar.|
|**2D İlkel**|**Kenar yumuşatma**<br /> Takma ad karşıtı kenarları olan ilkelleri çizer. Bu onlara daha yumuşak bir görünüm verir.<br /><br /> **Kalınlık**<br /> İlkel sınırı oluşturan çizginin kalınlığını tanımlar.<br /><br /> **Yarıçap X**<br /> (Yalnızca yuvarlatılmış dikdörtgen) İlkel in üst ve alt kenarları için yuvarlama yarıçapını tanımlar.<br /><br /> **Yarıçap Y**<br /> (Yalnızca yuvarlatılmış dikdörtgen) İlkel in sol ve sağ kenarlarıiçin yuvarlama yarıçapını tanımlar.|
|**Kalem**, **Fırça**, **Airbrush**, **2D Primitive**|**Kanallar**<br /> Görüntüleme ve çizim için belirli renk kanallarını etkinleştirir veya devre dışı kılabilir. **Görünüm** belirli bir renk kanalı için ayarlanmışsa, bu kanal görüntüde görünür; aksi takdirde, görünmez. **Beraberlik** belirli bir renk kanalı için ayarlanmışsa, bu kanal çizim işlemlerini etkiler; aksi takdirde, öyle değildir.|
|**Değnek Seçimi**, **Dolgu**|**Tolerans**<br /> Daha az veya daha fazla benzer renk etkilenen veya seçili bölgenin bir parçası yapılır, böylece içinde benzer olarak kabul edilir bitişik renkler arasındaki maksimum farkı tanımlar. Varsayılan olarak, değer 32'dir, bu da orijinal rengin 32 tonundaki (daha açık veya koyu) bitişik piksellerin bölgenin bir parçası olarak kabul edildiği anlamına gelir.|

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

|Komut|Klavye kısayolları|
|-------------| - |
|**Select** moduna geç|**S**|
|**Yakınlaştırma** moduna geçme|**Z**|
|**Pan** moduna geçme|**Kahraman**|
|Tümünü seç|**Ctrl**+**A**|
|Geçerli seçimi sil|**Sil**|
|Geçerli seçimi iptal et|**Esc** (kaçış)|
|Yakınlaştır|**Ctrl**+**Mouse tekerleği ileri**<br /><br /> **Ctrl**+**PageUp**<br /><br /> Artı İşaret**+**( )|
|Uzaklaştır|**Ctrl**-**Fare tekerleği geriye**<br /><br /> **Ctrl**-**PageDown**<br /><br /> Eksi İşareti (**-**)|
|Görüntüyü yukarı kaydırma|**Fare tekerleği geriye doğru**<br /><br /> **PageDown**|
|Görüntüyü aşağı kaydırma|**Fare tekerleği ileriye doğru**<br /><br /> **PageUp**|
|Görüntüyü sola kaydırma|**Shift**+**Mouse tekerleği geriye**<br /><br /> **Fare tekerleği sol**<br /><br /> **PageDown'ı Kaydır**+**PageDown**|
|Görüntüyü sağa kaydırma|**Shift**+**Mouse tekerleği ileri**<br /><br /> **Fare tekerleği sağ**<br /><br /> **Shift**+**PageUp**|
|Gerçek boyuta yakınlaştırma|**Ctrl**+**0** (sıfır)|
|Görüntüyü pencereye sığdır|**Ctrl**+**G**, **Ctrl**+**F**|
|Görüntüyü pencere genişliğine sığdır|**Ctrl**+**G**, **Ctrl**+**I**|
|Geçiş ızgarası|**Ctrl**+**G**, **Ctrl**+**G**|
|Görüntüyü geçerli seçime kırpma|**Ctrl**+**G**, **Ctrl**+**C**|
|Sonraki (daha yüksek ayrıntı) MIP düzeyini görüntüleme|**Ctrl**+**G**, **Ctrl**+**6**|
|Önceki (daha düşük ayrıntı) MIP düzeyini görüntüleme|**Ctrl**+**G**, **Ctrl**+**7**|
|Kırmızı renk kanalLarını değiştirme|**Ctrl**+**G**, **Ctrl**+**1**|
|Yeşil renk kanalInı değiştirme|**Ctrl**+**G**, **Ctrl**+**2**|
|Mavi renk kanalını değişt|**Ctrl**+**G**, **Ctrl**+**3**|
|Alfa (saydamlık) kanalına geçiş|**Ctrl**+**G**, **Ctrl**+**4**|
|Alfa dama tahtası deseni geçiş|**Ctrl**+**G**, **Ctrl**+**B**|
|Düzensiz seçim aracına geçme|**L**|
|Değnek seçim aracına geçme|**M**|
|Kalem aletine geçme|**P**|
|Fırça aracına geçme|**B**|
|Doldurma aracını çevirme|**F**|
|Silgi aracına geçiş|**E**|
|Metin aracına geçiş|**T**|
|Renk seç (dropr) aracına geçiş|**Ⅰ**|
|Etkin seçimi ve içeriğini taşıyın.|**Ok** tuşları.|
|Etkin seçimi ve içeriğini yeniden boyutlandırın.|**Ctrl**+**Ok** tuşları|
|Etkin seçimi taşıyın, ancak içeriğini taşımayın.|**Shift**+**Arrow** tuşları|
|Etkin seçimi yeniden boyutlandırın, ancak içeriğini yeniden boyutlandırmayın.|**Shift**++**Ctrl****Arrow** tuşlarını kaydır|
|Geçerli katmanı işleme|**Dönüş**|
|Takım kalınlığını azaltın|**[**|
|Takım kalınlığını artırın|**]**|

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Oyunlar ve uygulamalar için 3B varlıklarla çalışma](../designers/working-with-3-d-assets-for-games-and-apps.md)|Dokular ve görüntüler, 3B modeller ve gölgeefektleri gibi grafik varlıklarıyla çalışmak için Visual Studio'da kullanabileceğiniz araçlara genel bir bakış sağlar.|
|[Model düzenleyici](../designers/model-editor.md)|Visual Studio Model Editor'un 3B modellerle çalışmak için nasıl kullanılacağını açıklar.|
|[Gölgelendirici tasarımcısı](../designers/shader-designer.md)|Gölgelilerle çalışmak için Visual Studio Shader Designer'ın nasıl kullanılacağını açıklar.|
