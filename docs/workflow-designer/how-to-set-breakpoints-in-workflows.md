---
title: İş Akışlarında Kesme Noktası Ayarlama
description: İş Akışı Tasarımcısı veya C# kodunda olduğu gibi grafik iş akışlarınıza kesme noktaları ayarlamak için Visual Basic kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 5a40b357c71fffd1ef44be4e904cd52b583fb956
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135355"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Nasıl kullanılır: İş akışlarında kesme noktaları ayarlama

İş Akışı Tasarımcısı C# kodunda olduğu gibi grafik iş akışlarınız üzerinde kesme Visual Basic oluşturabilirsiniz. Beklendiği gibi, iş akışı yürütme ayar her kesme noktası durdurulur.

Kesme noktası üç eyalete sahip: *Beklemede,* *Bağlandı* ve *Hata.* Kesme noktası ayar değişiklikleri Beklemede olur ve düz kırmızı bir simgeyle gösterilir. Çalışma zamanı iş akışı türünü yüklemişse Bound olur. Kesme noktası için geçerli olmayan etkinlik adı gibi yanlış bir biçim belirtirsiniz, bir hata penceresi görüntülenir. Kesme noktası yine de kesme noktası penceresine eklenir, ancak küçük bir "x" ile işaretlenir.

> [!NOTE]
> Çağrılan iş akışlarda kesme noktası ayarlama desteklenmiyor.

> [!NOTE]
> Hata ayıklamadan önce Araçlar Seçenekler **Hata Yalnızca kendi kodum'dan Etkinleştir (Yalnızca Yönetilen)** seçeneğini   >    >   belirleyin. Seçenek seçili değilse ve başka bir dizi içinde iç içe geçmiş iki diziye sahipseniz ve ilk iç dizide bir kesme noktası ayarıyorsanız, **F11** tuşuna basmak ikinci iç dizide hata ayıklamaz.

> [!NOTE]
> XAML dosya özelliğinin tam yolu doğru değilse iş akışında kesme noktalarına isabet olmaz. Projeyi veya çözümü başka bir klasöre veya başka bir makineye taşımanın ardından XAML dosyasının tam yolu doğru değil. Tam yol özelliğini kaydetmek ve güncelleştirmek için **Ctrl** + **S'yi** seçin.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Tasarım Görünümünde bir etkinlikte kesme noktası ayarlamak için

1. Hata ayıklayıcının kesmesi istediğiniz etkinliği seçin.

2. Hata **Ayıkla menüsünde Kesme** Noktası'nın **geçişini seçin.** Etkinliğin sol üst kenarında kırmızı bir simge görünür.

   Alternatif olarak, etkinliği seçdikten sonra **F9** tuşuna basabilirsiniz veya sağ tıklama menüsünden etkinliği sağ tıklayarak Kesme Noktası  >  **Ekle Kesme** Noktası'yı seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısı ile İş Akışlarında Hata Ayıklama](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Nasıl Yapılır: İş Akışı Tasarımcısı ile XAML Hatalarını Ayıklama](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)
