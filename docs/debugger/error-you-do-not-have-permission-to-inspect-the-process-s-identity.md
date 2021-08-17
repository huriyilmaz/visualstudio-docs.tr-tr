---
description: İşlem kimliğini inceleme izniniz yok.
title: İşlem kimliğini denetleme izniniz &apos; | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d66baa88369583c1b8bbda124e95125d6c9f2b7d209c543de4b8254185be2718
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121436075"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Hata: İşlem kimliğini inceleme izniniz&#39;yok
İşlem kimliğini inceleme izniniz yok. Bunun nedeni, sistem yapılandırmanız olabilir.

 Hata ayıklayıcı, hata ayıklama için gerekli bilgiler olan işlem kimliğini inceleyemdi. Bunun en olası nedeni Terminal Hizmetlerinin devre dışı olmasıdır. Terminal Hizmetleri hizmeti varsayılan olarak etkindir. Yeniden etkinleştirmek için bu adımları izleyin.

### <a name="to-enable-terminal-services"></a>Terminal Hizmetlerini etkinleştirmek için

1. **Başlat'a** tıklayın ve **ardından** Denetim Masası.

2. Bu Denetim Masası, Gerekirse **Klasik Görünüme Geç'i** seçin ve ardından Yönetimsel **Araçlar'a çift tıklayın.**

3. Yönetimsel **Araçlar penceresinde** Bilgisayar Yönetimi'ne çift **tıklayın.**

4. Bilgisayar Yönetimi penceresinde Hizmetler ve Uygulamalar **düğümünü** genişletin.

5. Hizmetler ve **Uygulamalar altında Hizmetler'e** **tıklayın.**

     Sağ bölmede bir hizmet listesi görüntülenir.

6. Hizmetler listesinde **Terminal** Hizmetleri'ne sağ tıklayın **ve ardından Özellikler'i** **seçin.**

7. Terminal **Hizmetleri Özellikleri penceresinde** Genel sekmesine gidin **ve** Başlangıç türü'ni El **ile olarak** **ayarlayın.**

8. **Tamam**'a tıklayın.

9. Bilgisayarı yeniden başlatın.

     Bu yordam, Uzak Masaüstü'leri otomatik olarak etkinleştirmez. Bilgisayarınızda Uzak Masaüstü'leri etkinleştirmek için aşağıdaki ek yordamı gerçekleştirin.

### <a name="to-enable-remote-desktop"></a>Uzak Masaüstü'leri etkinleştirmek için

1. **Başlat'a** tıklayın ve ardından Bilgisayarım'a **sağ tıklayın.**

2. **Özellikler**'i seçin.

     Sistem **Özellikleri** penceresi görüntülenir.

3. **Uzak'a tıklayın.**

4. Uzak **Masaüstü altında Kullanıcıların** bu bilgisayara uzaktan **bağlanmasına izin ver'i seçin.**

5. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
