---
title: Çıktı Penceresi
description: Çıkış penceresi ve IDE'de çeşitli özellikler için durum iletilerini nasıl görüntüley olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.build.output
- vs.debug.output
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
ms.openlocfilehash: bbc6f33c439a812d7153f48d7f20d7e1d9dd3cb1
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112925169"
---
# <a name="output-window"></a>Çıktı penceresi

Çıkış **penceresi** tümleşik geliştirme ortamındaki (IDE) çeşitli özellikler için durum iletilerini görüntüler. Çıkış penceresini açmak **için** menü çubuğunda Çıkışı Görüntüle'yi seçin  >  veya Ctrl Alt O  + **tuşlarına** + **basın.**

## <a name="toolbar"></a>Araç Çubuğu

Aşağıdaki denetimler Çıkış penceresinin araç **çubuğunda** gösterilir.

### <a name="show-output-from"></a>çıktısını göster

Görüntülemek için bir veya daha fazla çıkış bölmesi görüntüler. IDE'de kullanıcıya ileti teslim etmek için Çıkış penceresini hangi araçların kullandığına bağlı olarak **çeşitli** bilgi bölmeleri kullanılabilir.

### <a name="find-message-in-code"></a>Kodda İleti Bulma

Kod düzenleyicisinde ekleme noktasını seçili derleme hatasını içeren satıra taşır.

### <a name="go-to-previous-message"></a>Önceki İletiye Git

Çıkış penceresindeki **odağı önceki** derleme hatasına değiştirir ve kod düzenleyicisinde ekleme noktasını bu derleme hatasını içeren satıra taşır.

### <a name="go-to-next-message"></a>Sonraki İletiye Git

Çıkış penceresinde odağı **bir** sonraki derleme hatasına değiştirir ve kod düzenleyicisinde ekleme noktasını bu derleme hatasını içeren satıra taşır.

### <a name="clear-all"></a>Tümünü temizle

Çıkış bölmesindeki tüm **metni** temizler.

### <a name="toggle-word-wrap"></a>Sözcük Kaydırmayı Değiştir

Çıkış bölmesinde Sözcük Kaydırma özelliğini açma **ve** kapatma. Sözcük Kaydırma açık olduğunda, görüntüleme alanı ötesine genişleten daha uzun girişlerde yer alan metinler aşağıdaki satırda görüntülenir.

## <a name="output-pane"></a>Çıkış bölmesi

Çıktıyı göster listesinde **seçilen Çıkış bölmesi,** belirtilen kaynaktan çıktıyı görüntüler. 

## <a name="route-messages-to-the-output-window"></a>İletileri Çıkış penceresine yönlendirme

Her proje **derlemeniz** için Çıkış  penceresini görüntülemek için, Seçenekler iletişim kutusundaki Projeler **ve** Çözümler Genel sayfasında, derleme başlatıldığında Çıkışı Göster  >   **penceresini seçin.** Ardından, düzenleme için açık bir kod dosyasıyla  Çıkış **penceresindeki** araç  çubuğunda Sonraki İletiye Git ve Önceki İletiye Git'i seçerek Çıkış **bölmesindeki girişleri** seçin. Bunu yapmak için kod düzenleyicisinde ekleme noktası, seçilen sorunun oluştuğu kod satırına atlar.

Belirli IDE özellikleri ve komutları Komut penceresi [çıkışlarını](../../ide/reference/command-window.md) Çıkış penceresine **teslim** etmek için kullanılır. genellikle komut penceresinde görüntülenen *.bat* *ve .com* dosyaları gibi dış araçlardan gelen çıkış,  Dış araçları yönet'te Çıkış Penceresi kullan seçeneğinin seçili olduğu bir Çıkış bölmesine [yönlendirildi.](../../ide/managing-external-tools.md)  Diğer birçok ileti türü Çıkış **bölmeleri içinde** de görüntülenebilir. Örneğin, saklı yordamda Transact-SQL söz dizimi hedef veritabanına karşı denetlenirse, sonuçlar Çıkış **penceresinde** görüntülenir.

Ayrıca çalışma zamanında bir Çıkış bölmesine tanılama iletileri yazmak için kendi uygulamalarınızı **programleyebilirsiniz.** Bunu yapmak için <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> .NET API'sinde ad alanı içinde <xref:System.Diagnostics> sınıf veya sınıfın üyelerini kullanın. Sınıf üyeleri, çözüm veya projenizin Hata ayıklama yapılandırmalarını derlemek için çıkışı görüntüler; sınıf üyeleri, Hata Ayıklama veya Yayın yapılandırmalarını <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> derlemek için çıkışı görüntüler. Daha fazla bilgi için Çıktı [penceresindeki Tanılama iletileri'ne bakın.](../../debugger/diagnostic-messages-in-the-output-window.md)

C++ içinde, uyarıları ve hataları Çıkış bölmesinde görüntülenen ve sayılan özel derleme adımları ve derleme **olayları oluşturabilirsiniz.** Bir çıkış **satırına F1** tuşuna basarak uygun bir yardım konusu görüntüebilirsiniz. Daha fazla bilgi için [bkz. Özel derleme adımının çıkışını biçimlendirme.](/cpp/build/formatting-the-output-of-a-custom-build-step-or-build-event)

## <a name="scroll-behavior"></a>Kaydırma davranışı

Çıkış penceresinde otomatik olarak kaydı kullanırsanız **ve ardından** fare veya ok tuşlarını kullanarak gezinilse otomatik kayıt durur. Otomatik olarak kaydı sürdürmeye devam etmek için **Ctrl End tuşlarına** + **basın.**

## <a name="see-also"></a>Ayrıca bkz.

- [Çıkış penceresindeki tanılama iletileri](../../debugger/diagnostic-messages-in-the-output-window.md)
- [Nasıl: Çıkış penceresini denetleme](/previous-versions/ht6z4e28(v=vs.140))
- [Derleme ve oluşturma](../../ide/compiling-and-building-in-visual-studio.md)
- [Derleme yapılandırmalarını anlama](../../ide/understanding-build-configurations.md)
- [Sınıf kitaplığına genel bakış](/dotnet/standard/class-library-overview)