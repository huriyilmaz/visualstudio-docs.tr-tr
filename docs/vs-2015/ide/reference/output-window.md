---
title: Çıkış Penceresi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f17b91cc462b6f628100ffbf370fcdec2eb9888d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662191"
---
# <a name="output-window"></a>Çıktı Penceresi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Çıkış** penceresi, tümleşik geliştirme ORTAMıNDAKI (IDE) çeşitli özelliklerin durum iletilerini görüntüleyebilir. **Çıkış** penceresini açmak için, menü çubuğunda **Görünüm/çıkış** ' ı seçin (veya Ctrl + Alt + O tuşlarına basın).

> [!WARNING]
> Çıkış penceresi Visual Studio Express sürümlerindeki Görünüm menüsünde görünmez. Bunu getirmek için CTRL + ALT + O tuşlarına basarak kısayol tuşunu kullanın.

## <a name="toolbar"></a>Araç Çubuğu
 **Çıktıyı göster** Görüntülenecek bir veya daha fazla çıkış bölmesi görüntüler. IDE 'deki hangi araçların kullanıcıya ileti teslim etmek için **Çıkış** penceresini kullandığına bağlı olarak çeşitli bilgi bölmeleri kullanılabilir olabilir.

 **Kodda Ileti bul** Kod düzenleyicisinde ekleme noktasını, seçilen derleme hatasını içeren satıra kaydırır.

 **Önceki Iletiye git** **Çıkış** penceresindeki odağı önceki derleme hatasına dönüştürür ve kod düzenleyicisinde ekleme noktasını, bu derleme hatasını içeren satıra taşımaktadır.

 **Sonraki Iletiye git** **Çıkış** penceresindeki odağı sonraki derleme hatasına dönüştürür ve kod düzenleyicisinde ekleme noktasını, bu derleme hatasını içeren satıra taşımaktadır.

 **Tümünü Temizle** **Çıkış** bölmesinden tüm metni temizler.

 **Sözcük kaydırmayı aç** **Çıktı** bölmesinde sözcük kaydır özelliğini açar ve kapatır. Sözcük kaydırması açık olduğunda, görüntüleme alanının ötesine geçen daha uzun girdilerde bulunan metinler aşağıdaki satırda görüntülenir.

## <a name="output-pane"></a>Çıkış bölmesi
 **Çıktıyı göster** listesinden seçilen **Çıkış** bölmesi, belirtilen kaynaktaki çıktıyı görüntüler.

## <a name="routing-messages-to-the-output-window"></a>Iletileri Çıkış Penceresi yönlendirme
 Her proje oluşturduğunuzda **Çıkış** penceresini görüntülemek için **Genel, projeler ve çözümler, Seçenekler** iletişim kutusunda, **derleme başladığında çıkış penceresini göster**' i seçin. Daha sonra, bir kod dosyası düzenlenmek üzere açıkken, **Çıkış bölmesinde girişler** ' i seçmek için **Çıkış** penceresi araç çubuğunda bir **sonraki iletiye git** ve **önceki ileti düğmelerine git** ' i seçin. Bunu yaparken, kod düzenleyicisinde ekleme noktası, seçilen sorunun gerçekleştiği kod satırına atlar.

 [Komut penceresinde](../../ide/reference/command-window.md) ÇAĞRıLAN bazı IDE özellikleri ve komutları çıktısını **Çıkış** penceresine teslim edin. Genellikle komut Istemi penceresinde görünen. bat ve. com dosyaları gibi dış araçlardan alınan çıkış, [dış araçların yönetilmesi](../../ide/managing-external-tools.md) **Çıkış penceresi** seçeneğini belirlediğinizde bir **Çıkış** bölmesine yönlendirilir. Diğer birçok ileti, **Çıkış** bölmelerinde de görüntülenebilir. Örneğin, saklı yordamdaki Transact-SQL sözdizimi hedef veritabanına karşı denetlendiğinde, sonuçlar **Çıkış** penceresinde görüntülenir.

 Ayrıca, çalışma zamanında bir **Çıkış** bölmesine tanılama iletileri yazmak için kendi uygulamalarınızı programlayabilirsiniz. Bunu yapmak için, <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> <xref:System.Diagnostics> .NET Framework sınıf kitaplığının ad alanındaki sınıfının veya sınıfın üyelerini kullanın. Sınıf üyeleri, <xref:System.Diagnostics.Debug> çözümünüzün veya projenizin hata ayıklama yapılandırmalarının derlenmesi sırasında çıktıyı görüntüler; <xref:System.Diagnostics.Trace> sınıf üyeleri hata ayıklama veya sürüm yapılandırması oluştururken çıktıyı görüntüler. Daha fazla bilgi için [Çıkış penceresi tanılama iletileri](../../debugger/diagnostic-messages-in-the-output-window.md)bölümüne bakın.

 İçinde [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] , **Çıkış** bölmesinde uyarıları ve hataları görüntülenen ve sayılan özel yapı adımları ve derleme olayları oluşturabilirsiniz. Bir çıktı satırında F1 tuşuna basarak uygun bir yardım konusu görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [özel derleme adımının veya derleme olayının çıktısını biçimlendirme](https://msdn.microsoft.com/library/92ad3e38-24d7-4b89-90e6-5a16f5f998da).

## <a name="scrolling-behavior"></a>Kaydırma davranışı
 Çıkış penceresinde bir oto kaydırma kullanır ve sonra fare veya ok tuşlarını kullanarak gezinirseniz, oto kaydırma duraklar. Oto kaydırmayı yeniden başlatmak için CTRL + END tuşlarına basın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Çıkış penceresi](../../debugger/diagnostic-messages-in-the-output-window.md) [nasıl yapılır: çıkış penceresi derlemeyi denetleme](https://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858) [ve](../../ide/compiling-and-building-in-visual-studio.md) [derlemeyi anlama derleme konfigürasyonları](../../ide/understanding-build-configurations.md) [sınıf kitaplığı genel bakış](https://msdn.microsoft.com/library/7e4c5921-955d-4b06-8709-101873acf157)
