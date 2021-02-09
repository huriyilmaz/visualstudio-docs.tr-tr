---
title: Çıktı Penceresi
description: Çıkış penceresi ve IDE 'deki çeşitli özellikler için durum iletilerini görüntüleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.build.output
- vs.debug.output
- vs.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0bdbaf79a3700a1ba1c0574e345093af25608e39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932052"
---
# <a name="output-window"></a>Çıktı penceresi

**Çıkış** penceresinde, tümleşik geliştirme ORTAMıNDAKI (IDE) çeşitli özellikler için durum iletileri görüntülenir. **Çıkış** penceresini açmak için, menü çubuğunda çıktıyı görüntüle ' yi seçin   >  veya **CTRL** + **alt** + **O** tuşlarına basın.

## <a name="toolbar"></a>Araç Çubuğu

Aşağıdaki denetimler **Çıkış** penceresinin araç çubuğunda gösterilir.

### <a name="show-output-from"></a>Çıktıyı göster

Görüntülenecek bir veya daha fazla çıkış bölmesi görüntüler. IDE 'deki hangi araçların kullanıcıya ileti teslim etmek için **Çıkış** penceresini kullandığına bağlı olarak çeşitli bilgi bölmeleri kullanılabilir olabilir.

### <a name="find-message-in-code"></a>Kodda Ileti bul

Kod düzenleyicisinde ekleme noktasını, seçilen derleme hatasını içeren satıra kaydırır.

### <a name="go-to-previous-message"></a>Önceki Iletiye git

**Çıkış** penceresindeki odağı önceki derleme hatasına dönüştürür ve kod düzenleyicisinde ekleme noktasını, bu derleme hatasını içeren satıra taşımaktadır.

### <a name="go-to-next-message"></a>Sonraki Iletiye git

**Çıkış** penceresindeki odağı sonraki derleme hatasına dönüştürür ve kod düzenleyicisinde ekleme noktasını, bu derleme hatasını içeren satıra taşımaktadır.

### <a name="clear-all"></a>Tümünü temizle

**Çıkış** bölmesinden tüm metni temizler.

### <a name="toggle-word-wrap"></a>Sözcük kaydırmayı aç

**Çıktı** bölmesinde sözcük kaydır özelliğini açar ve kapatır. Sözcük kaydırması açık olduğunda, görüntüleme alanının ötesine geçen daha uzun girdilerde bulunan metinler aşağıdaki satırda görüntülenir.

## <a name="output-pane"></a>Çıkış bölmesi

**Çıktıyı göster** listesinden seçilen **Çıkış** bölmesi, belirtilen kaynaktaki çıktıyı görüntüler.

## <a name="route-messages-to-the-output-window"></a>İletileri çıkış penceresine yönlendir

Her proje oluşturduğunuzda **Çıkış** penceresini görüntülemek için, **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**  >  **genel** sayfasında, **derleme başladığında çıkış penceresini göster**' i seçin. Daha sonra, bir kod dosyası düzenlenmek üzere açıkken **sonraki Iletiye git** ' i seçin **ve çıkış penceresinde** girişler ' i seçmek için **Çıkış** penceresi araç çubuğunda **önceki iletiye gidin** . Bunu yaparken, kod düzenleyicisinde ekleme noktası, seçilen sorunun gerçekleştiği kod satırına atlar.

[Komut penceresi](../../ide/reference/command-window.md) ÇAĞRıLAN belirli IDE özellikleri ve komutları çıktısını **Çıkış** penceresine teslim edin. Genellikle komut penceresinde görünen *. bat* ve *. com* dosyaları gibi dış araçların çıktıları, [dış araçları yönetme](../../ide/managing-external-tools.md)bölümünde **Çıkış penceresi kullan** seçeneğini belirlediğinizde bir **Çıkış** bölmesine yönlendirilir. Diğer birçok ileti, **Çıkış** bölmelerinde de görüntülenebilir. Örneğin, saklı yordamdaki Transact-SQL sözdizimi hedef veritabanına karşı denetlendiğinde, sonuçlar **Çıkış** penceresinde görüntülenir.

Ayrıca, çalışma zamanında bir **Çıkış** bölmesine tanılama iletileri yazmak için kendi uygulamalarınızı programlayabilirsiniz. Bunu yapmak için, <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> <xref:System.Diagnostics> .NET API 'sinin ad alanındaki sınıfının veya sınıfın üyelerini kullanın. Sınıf üyeleri, <xref:System.Diagnostics.Debug> çözümünüzün veya projenizin hata ayıklama yapılandırmalarının derlenmesi sırasında çıktıyı görüntüler; <xref:System.Diagnostics.Trace> sınıf üyeleri hata ayıklama veya sürüm yapılandırması oluştururken çıktıyı görüntüler. Daha fazla bilgi için bkz. [Çıkış penceresindeki tanılama iletileri](../../debugger/diagnostic-messages-in-the-output-window.md).

C++ ' da, uyarıları ve hataları **Çıkış** bölmesinde görüntülenen ve sayılan özel yapı adımları ve derleme olayları oluşturabilirsiniz. Bir çıktı satırında **F1** tuşuna basarak uygun bir yardım konusu görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [özel derleme adımının çıkışını biçimlendirme](/cpp/build/formatting-the-output-of-a-custom-build-step-or-build-event).

## <a name="scroll-behavior"></a>Kaydırma davranışı

**Çıkış** penceresinde bir oto kaydırma kullanır ve sonra fare veya ok tuşlarını kullanarak gezinirseniz, oto kaydırma duraklar. Oto kaydırmayı yeniden başlatmak için **CTRL** tuşuna basın + .

## <a name="see-also"></a>Ayrıca bkz.

- [Çıkış penceresindeki tanılama iletileri](../../debugger/diagnostic-messages-in-the-output-window.md)
- [Nasıl yapılır: çıkış penceresini denetleme](/previous-versions/ht6z4e28(v=vs.140))
- [Derleme ve oluşturma](../../ide/compiling-and-building-in-visual-studio.md)
- [Derleme yapılandırmalarını anlama](../../ide/understanding-build-configurations.md)
- [Sınıf kitaplığına genel bakış](/dotnet/standard/class-library-overview)