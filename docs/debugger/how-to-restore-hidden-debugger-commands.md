---
title: Gizli Hata Ayıklayıcı Komutlarını Geri Yükleme | Microsoft Docs
description: Visual Studio'da gizli hata ayıklayıcı komutlarını geri Visual Studio. Bazı diller için varsayılan IDE ayarları, belirli hata ayıklayıcı komutlarını gizleyebiliyor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ebe873887ab74e5709afc2da347caa084e70990d0df256f408b45f3ccc7dd0a5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379105"
---
# <a name="how-to-restore-hidden-debugger-commands"></a>Nasıl Yapılır: Gizli Hata Ayıklayıcı Komutlarını Geri Yükleme
Bu ayarları Visual Studio, birincil programlama diliniz için bir dizi varsayılan IDE ayarı seçmeniz istenecek. Bazı diller için varsayılan IDE ayarları, belirli hata ayıklayıcı komutlarını gizleyebiliyor.

 Varsayılan IDE ayarlarınız tarafından gizlenen bir hata ayıklayıcı özelliği kullanmak için aşağıdaki yordamı kullanarak komutu menüye geri ekleyebilirsiniz.

### <a name="to-restore-hidden-debugger-commands"></a>Gizli hata ayıklayıcı komutlarını geri yüklemek için

1. Bir proje açıkken  Araçlar menüsünde **Özelleştir'e tıklayın.**

2. Özelleştir **iletişim** kutusunda Komutlar **sekmesine** tıklayın.

3. Menü **çubuğu:** açılan menüsünde geri yüklenen **komutu** içermek istediğiniz Hata Ayıklama menüsünü seçin.

4. Komut **Ekle... düğmesine** tıklayın.

5. Komut **Ekle kutusunda,** eklemek istediğiniz komutu seçin ve Tamam'a **tıklayın.**

6. Başka bir komut eklemek için önceki adımı tekrarlayın.

7. **Menüye** komut eklemeyi bitirdikten sonra Kapat'a tıklayın.

    > [!WARNING]
    > Bazı menü öğeleri yalnızca hata ayıklayıcı çalıştırma modu veya kesme modu gibi belirli modlarda olduğunda görünür. Bu nedenle, bu adımları tamamlarken, eklenen bir öğe hemen görünür durumda olmayacaktır.

## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>Özelleştir İletişim Kutusundan Komutları Geri Yükleme
 Özellikle hiyerarşik menülerde bulunan bazı komutlar Özelleştir iletişim kutusundan **geri yüklenebilir.** Bu komutları geri yüklemek için yeni bir IDE ayarları koleksiyonunu içeri aktarmalısınız.

#### <a name="to-import-new-ide-settings"></a>Yeni IDE ayarlarını içeri aktarma

1. Araçlar menüsünde **İçeri** ve Dışarı **Aktar'a tıklayın Ayarlar.**

2. İçeri ve **Dışarı Aktarma Sihirbazı'Ayarlar** Hoş Geldiniz sayfasında Seçili ortam ayarlarını içeri aktar'a ve **ardından** Sonraki 'ye **tıklayın.**

3. Geçerli Ayarları **Kaydet Ayarlar,** mevcut ayarlarınızı kaydedip kaydetmey karar verin ve ardından Sonraki 'ye **tıklayın.**

4. İçeri **aktarılamaz bir ayar** koleksiyonu seçin sayfasındaki **Varsayılan** Ayarlar klasörünün altında, kullanmak istediğiniz komutları içeren bir geliştirme ayarları koleksiyonu seçin. Hangi koleksiyonu seçeceklerini bilmiyorsanız, en fazla hata **ayıklayıcı komutu Ayarlar** genel Visual C++ **Geliştirme Ayarlar**' yi deneyin.

5. **İleri**’ye tıklayın.

6. İçeri **aktarilecek ayarları seçin sayfasının** Seçenekler'in **altında** Hata ayıklama'nın **seçili olduğundan** emin olun. Bu ayarları da içeri aktarmayı istemiyorsanız diğer onay kutularını temizleyin.

7. **Finish (Son)** düğmesine tıklayın.

8. İçeri Aktarma **Tamamlandı sayfasında,** Ayrıntılar altında ayarlarınızı sıfırlamayla ilişkili hataları gözden **geçirebilirsiniz.**

9. **Kapat**’a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcı Güvenliği](../debugger/debugger-security.md)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)