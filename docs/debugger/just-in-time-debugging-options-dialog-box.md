---
title: Tam zamanında, hata ayıklama, Seçenekler Iletişim kutusu | Microsoft Docs
description: Tam zamanında hata ayıklama, Visual Studio dışında başlayan programlarda hata ayıklamanıza olanak tanır. Çeşitli program türleri için tam zamanında hata ayıklamayı nasıl etkinleştirebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9179b67d5a7418cfc16900b28f51e3b0984135aa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043901"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Tam Zamanında, Hata Ayıklama, Seçenekler İletişim Kutusu
**Tam zamanında** sayfasına erişmek için **Araçlar** menüsüne gidin ve **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **hata ayıklama** düğümünü genişletin ve **tam zamanında**' ı seçin. Bu sayfa, yönetilen kod, yerel kod ve komut dosyası için tam zamanında hata ayıklamayı etkinleştirmenizi sağlar. Daha fazla bilgi için bkz. [tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md).

 Bu program türleri için tam zamanında hata ayıklamayı etkinleştirebilirsiniz:

- Yönetilen

- Yerel

- Komut Dosyası

  Tam zamanında hata ayıklama, dışında başlatılan bir programda hata ayıklama için bir tekniktir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Ortam dışında oluşturulmuş bir programı çalıştırabilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Tam zamanında hata ayıklamayı etkinleştirdiyseniz, kilitlenme hata ayıklamak isteyip istemediğinizi soran bir iletişim kutusu görüntüler.

## <a name="associated-warnings"></a>İlişkili uyarılar
 **Seçenekler** iletişim kutusunun bu sayfasını ziyaret ettiğinizde şöyle bir uyarı iletisi görebilirsiniz:

 **Başka bir hata ayıklayıcı kendisini tam zamanında hata ayıklayıcı olarak kaydettirdi. onarmak için tam zamanında hata ayıklamayı etkinleştirin veya Visual Studio onarma işlemini çalıştırın.**

 Bu ileti, hata ayıklayıcı 'nın daha eski bir sürümü olan başka bir hata ayıklayıcı varsa ve [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tam zamanında hata ayıklayıcı olarak ayarlandıysanız oluşur.

 Görebileceğiniz başka bir ileti şu şekildedir:

 **Tam zamanında hata ayıklama kayıt hataları algılandı. onarmak için tam zamanında hata ayıklamayı etkinleştirin veya Visual Studio onarma işlemini çalıştırın.**

 Bu uyarılardan birini görürseniz, tam zamanında hata ayıklama, [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] sorunu düzeltene kadar yönetici ayrıcalıklarına sahip olmasını gerektirir. Bu koşullarda yönetici olmayan tek olarak etkinleştirmeyi denerseniz, aşağıdaki hata iletisini görürsünüz:

 **Erişim reddedildi. Bir yöneticiye tam zamanında hata ayıklamayı etkinleştirme veya Visual Studio yüklemenizi onarma.**

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama, Seçenekler Iletişim kutusu](../debugger/debugging-options-dialog-box.md)
- [nasıl yapılır: hata ayıklayıcı belirtme Ayarlar](../debugger/how-to-specify-debugger-settings.md)