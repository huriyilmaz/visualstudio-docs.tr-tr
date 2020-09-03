---
title: Tam zamanında, hata ayıklama, Seçenekler Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b3bd6c6ee32145a94dbc4b751834ecc003f2bdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201113"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Tam Zamanında, Hata Ayıklama, Seçenekler İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Tam zamanında** sayfasına erişmek için **Araçlar** menüsüne gidin ve **Seçenekler**' e tıklayın. **Seçenekler** iletişim kutusunda, **hata ayıklama** düğümünü genişletin ve **tam zamanında**' ı seçin. Bu sayfa, yönetilen kod, yerel kod ve komut dosyası için tam zamanında hata ayıklamayı etkinleştirmenizi sağlar. Daha fazla bilgi için bkz. [tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Bu program türleri için tam zamanında hata ayıklamayı etkinleştirebilirsiniz:  
  
- Yönetilen  
  
- Yerel  
  
- Komut Dosyası  
  
  Tam zamanında hata ayıklama, dışında başlatılan bir programda hata ayıklama için bir tekniktir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Ortam dışında oluşturulmuş bir programı çalıştırabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Tam zamanında hata ayıklamayı etkinleştirdiyseniz, kilitlenme hata ayıklamak isteyip istemediğinizi soran bir iletişim kutusu görüntüler.  
  
## <a name="associated-warnings"></a>İlişkili uyarılar  
 **Seçenekler** iletişim kutusunun bu sayfasını ziyaret ettiğinizde şöyle bir uyarı iletisi görebilirsiniz:  
  
 **Başka bir hata ayıklayıcı kendisini tam zamanında hata ayıklayıcı olarak kaydettirdi. Onarmak için, tam zamanında hata ayıklamayı etkinleştirin veya Visual Studio onarımı 'nı çalıştırın.**  
  
 Bu ileti, hata ayıklayıcı 'nın daha eski bir sürümü olan başka bir hata ayıklayıcı varsa ve [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tam zamanında hata ayıklayıcı olarak ayarlandıysanız oluşur.  
  
 Görebileceğiniz başka bir ileti şu şekildedir:  
  
 **Tam zamanında hata ayıklama kayıt hataları algılandı. Onarmak için, tam zamanında hata ayıklamayı etkinleştirin veya Visual Studio onarımı 'nı çalıştırın.**  
  
 Bu uyarılardan birini görürseniz, tam zamanında hata ayıklama, [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] sorunu düzeltene kadar yönetici ayrıcalıklarına sahip olmasını gerektirir. Bu koşullarda yönetici olmayan tek olarak etkinleştirmeyi denerseniz, aşağıdaki hata iletisini görürsünüz:  
  
 **Erişim reddedildi. Bir yöneticiye tam zamanında hata ayıklamayı etkinleştirme veya Visual Studio yüklemenizi onarma.**  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama, Seçenekler Iletişim kutusu](../debugger/debugging-options-dialog-box.md)   
 [Nasıl yapılır: hata ayıklayıcı ayarlarını belirtme](../debugger/how-to-specify-debugger-settings.md)
