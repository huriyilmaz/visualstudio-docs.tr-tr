---
title: Tam zamanında, hata ayıklama, Seçenekler Iletişim kutusu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c27ec66c8165995c6877b9a9e65802813140c7f2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731603"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Tam Zamanında, Hata Ayıklama, Seçenekler İletişim Kutusu
**Tam zamanında** sayfasına erişmek için **Araçlar** menüsüne gidin ve **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **hata ayıklama** düğümünü genişletin ve **tam zamanında**' ı seçin. Bu sayfa, yönetilen kod, yerel kod ve komut dosyası için tam zamanında hata ayıklamayı etkinleştirmenizi sağlar. Daha fazla bilgi için bkz. [tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md).

 Bu program türleri için tam zamanında hata ayıklamayı etkinleştirebilirsiniz:

- lebilmesi

- Yerel

- Komut Dosyası

  Tam zamanında hata ayıklama, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dışında başlatılan bir programda hata ayıklamaya yönelik bir tekniktir. @No__t_1 ortamının dışında [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oluşturulan bir programı çalıştırabilirsiniz. Tam zamanında hata ayıklamayı etkinleştirdiyseniz, kilitlenme hata ayıklamak isteyip istemediğinizi soran bir iletişim kutusu görüntüler.

## <a name="associated-warnings"></a>İlişkili uyarılar
 **Seçenekler** iletişim kutusunun bu sayfasını ziyaret ettiğinizde şöyle bir uyarı iletisi görebilirsiniz:

 **Başka bir hata ayıklayıcı kendisini tam zamanında hata ayıklayıcı olarak kaydettirdi. Onarmak için, tam zamanında hata ayıklamayı etkinleştirin veya Visual Studio onarımı 'nı çalıştırın.**

 Bu ileti, büyük olasılıkla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hata ayıklayıcı daha eski bir sürümü olan, tam zamanında hata ayıklayıcı olarak ayarlanan başka bir hata ayıklayıcıya sahipseniz oluşur.

 Görebileceğiniz başka bir ileti şu şekildedir:

 **Tam zamanında hata ayıklama kayıt hataları algılandı. Onarmak için, tam zamanında hata ayıklamayı etkinleştirin veya Visual Studio onarımı 'nı çalıştırın.**

 Bu uyarılardan birini görürseniz, [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] ile tam zamanında hata ayıklama, sorunu düzeltene kadar yönetici ayrıcalıklarına sahip olmasını gerektirir. Bu koşullarda yönetici olmayan tek olarak etkinleştirmeyi denerseniz, aşağıdaki hata iletisini görürsünüz:

 **Erişim reddedildi. Bir yöneticiye tam zamanında hata ayıklamayı etkinleştirme veya Visual Studio yüklemenizi onarma.**

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama, Seçenekler İletişim Kutusu](../debugger/debugging-options-dialog-box.md)
- [Nasıl Yapılır: Hata Ayıklayıcısı Ayarlarını Belirtme](../debugger/how-to-specify-debugger-settings.md)