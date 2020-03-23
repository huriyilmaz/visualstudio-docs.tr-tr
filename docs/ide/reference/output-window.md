---
title: Çıktı Penceresi
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be028af8ab9f458c1fadad6f8b2fcbd6aaa49a04
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567989"
---
# <a name="output-window"></a>Çıktı penceresi

**Çıktı** penceresi, tümleşik geliştirme ortamındaki (IDE) çeşitli özellikler için durum iletilerini görüntüler. **Çıktı** penceresini açmak için menü çubuğunda**Çıktıyı** **Görüntüle'yi** > seçin veya **Ctrl**+**Alt**+**O**tuşuna basın.

## <a name="toolbar"></a>Araç Çubuğu

Aşağıdaki denetimler **Çıktı** penceresinin araç çubuğunda gösterilir.

### <a name="show-output-from"></a>Çıktıyı göster

Görüntülenebilmek için bir veya daha fazla çıkış bölmesini görüntüler. IDE'deki hangi araçların kullanıcıya ileti ler iletmek için **Çıktı** penceresini kullandığına bağlı olarak, çeşitli bilgi bölmeleri kullanılabilir.

### <a name="find-message-in-code"></a>Kodda İleti bul

Kod düzenleyicisindeki ekleme noktasını seçili yapı hatasını içeren satıra taşır.

### <a name="go-to-previous-message"></a>Önceki İletiye Git

**Çıktı** penceresindeki odağı önceki yapı hatasıyla değiştirir ve kod düzenleyicisindeki ekleme noktasını bu yapı hatasını içeren satıra taşır.

### <a name="go-to-next-message"></a>Sonraki İletiye Git

**Çıktı** penceresindeki odağı bir sonraki yapı hatasına değiştirir ve kod düzenleyicisindeki ekleme noktasını bu yapı hatasını içeren satıra taşır.

### <a name="clear-all"></a>Tümünü temizle

**Çıktı** bölmesinden tüm metni temizler.

### <a name="toggle-word-wrap"></a>Sözcük Kaydırma'yı Geçiş

**Çıktı** bölmesinde Word Wrap özelliğini açar ve kapatır. Word Wrap açıkken, görüntüleme alanının ötesine uzanan daha uzun girişlerde metin aşağıdaki satırda görüntülenir.

## <a name="output-pane"></a>Çıkış bölmesi

**Liste çıktısını Göster'de** seçilen **Çıktı** bölmesi belirtilen kaynaktan çıktı görüntüler.

## <a name="route-messages-to-the-output-window"></a>İletileri Çıkış penceresine yönlendirme

Bir proje oluşturduğunuzda **Çıktı** penceresini görüntülemek için, **Projeler ve Çözümler** > **Genel** **sayfasındaki Seçenekler** iletişim kutusunda, yapı başladığında **Çıktıyı Göster penceresini**seçin. Ardından, düzenleme için açık bir kod dosyasıyla, **Çıktı** bölmesinde girişleri seçmek için Çıkış penceresinde Sonraki **İletiye Git** ve **Önceki** **İletiye Git'i** seçin. Bunu yaptığınızda, kod düzenleyicisindeki ekleme noktası, seçili sorunun oluştuğu kod satırına atlar.

[Komut penceresinde](../../ide/reference/command-window.md) çağrılan belirli IDE özellikleri ve komutları çıktılarını **Çıkış** penceresine teslim eder. Genellikle komut penceresinde görüntülenen *.bat* ve *.com* dosyaları gibi dış araçlardan elde edilen çıktı, [dış araçları Yönet'te](../../ide/managing-external-tools.md)Kullanım **Çıktı penceresi** seçeneğini seçtiğinizde **Çıktı** bölmesine yönlendirilir. Diğer birçok ileti türü de **Çıktı** bölmelerinde görüntülenebilir. Örneğin, depolanan bir yordamdaki Transact-SQL sözdizimi hedef veritabanına karşı denetlendiğinde, sonuçlar **Çıkış** penceresinde görüntülenir.

Ayrıca, bir **Çıktı** bölmesine çalışma zamanında tanılama iletileri yazmak için kendi uygulamalarınızı programlayabilirsiniz. Bunu yapmak için,.NET <xref:System.Diagnostics.Debug> API'nin <xref:System.Diagnostics> ad alanında sınıf veya <xref:System.Diagnostics.Trace> sınıf üyelerini kullanın. Çözümünüzün <xref:System.Diagnostics.Debug> veya projenizin Hata Ayıklama yapılandırmalarını oluşturduğunuzda sınıf üyeleri çıktıyı görüntüler; Hata Ayıklama veya Sürüm yapılandırmaları oluşturduğunuzda <xref:System.Diagnostics.Trace> sınıf üyeleri çıktıyı görüntüler. Daha fazla bilgi [için, Çıktı penceresindetanı iletileri](../../debugger/diagnostic-messages-in-the-output-window.md)bakın.

C++'da, özel yapı adımları oluşturabilir ve uyarılar ve hatalar **Çıktı** bölmesinde görüntülenen ve sayılan olaylar oluşturabilirsiniz. Çıktı satırında **F1** tuşuna basarak, uygun bir yardım konusunu görüntüleyebilirsiniz. Daha fazla bilgi için [bkz.](/cpp/build/formatting-the-output-of-a-custom-build-step-or-build-event)

## <a name="scroll-behavior"></a>Kaydırma davranışı

**Çıkış** penceresinde otomatik kaydırma kullanıyorsanız ve fare veya ok tuşlarını kullanarak geziniyorsanız, otomatik kaydırma durakları. Otomatik kaydırmaya devam etmek için **Ctrl**+**End**tuşuna basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Çıkış penceresindeki tanılama iletileri](../../debugger/diagnostic-messages-in-the-output-window.md)
- [Nasıl yapılsın: Çıkış penceresini denetleme](https://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858)
- [Derleme ve oluşturma](../../ide/compiling-and-building-in-visual-studio.md)
- [Derleme yapılandırmalarını anlama](../../ide/understanding-build-configurations.md)
- [Sınıf kitaplığına genel bakış](/dotnet/standard/class-library-overview)
