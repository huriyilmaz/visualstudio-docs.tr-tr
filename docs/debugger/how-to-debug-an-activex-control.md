---
title: ActiveX denetiminde hata ayıklama | Microsoft Docs
description: ActiveX denetiminde hata ayıklamayı öğrenin. Project özellik sayfalarında yapabileceğiniz veya hata ayıklamaya başladığınızda kullanabileceğiniz bir içeren yürütülebilir dosya belirtmeniz gerekir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 12eec4742fb4c420e10637b212a1fa6bbc578b0d07d058296b931f4ce60a7015
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121362334"
---
# <a name="how-to-debug-an-activex-control"></a>Nasıl Yapılır: ActiveX Denetiminde Hata Ayıklama

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. ayarlarınızı değiştirmek için araçlar menüsünden içeri aktar ve dışarı aktar Ayarlar seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

ActiveX denetibir denetimin hatalarını ayıklamak için, denetimin içinde çalışacağı bir kapsayıcı (yürütülebilir) belirtmeniz gerekir.

## <a name="to-specify-a-container-for-the-debug-session"></a>Hata ayıklama oturumu için bir kapsayıcı belirtmek için

1. Çözüm Gezgini, projeyi seçin.

2. **Görünüm** menüsünde **Özellik sayfaları**' nı seçin.

3. **Project özellik sayfaları** iletişim kutusunda, **yapılandırma özellikleri** klasörünü açın ve **hata ayıklama**' yı seçin.

4. **Hata ayıklama** kategorisi altında, **komut** özelliğini bulun.

5. Kapsayıcının yol adını belirtin. Örneğin, C:\Program Files\ınternet Explorer\IEXPLORE.EXE.

6. Kapsayıcı olarak Internet Explorer 'ı belirtirseniz ve etkin masaüstü kullanıyorsanız, `/new` **komut bağımsız değişkenleri** kutusuna yazın.

7. **Tamam**'a tıklayın.

     **Project özellik sayfaları** iletişim kutusunda bir kapsayıcı belirtmezseniz, hata ayıklamaya başladığınızda kapsayıcıyı belirtebilirsiniz. Hata ayıklamayı başlatmak için bir yürütme komutu seçtiğinizde, [hata ayıklama oturumu Için yürütülebilir Iletişim kutusu](../debugger/executable-for-debugging-session-dialog-box.md) görüntülenir. İletişim kutusunda kapsayıcının yol adını belirtin.

## <a name="see-also"></a>Ayrıca bkz.

- [ActiveX Kontrollerini](/cpp/mfc/activex-controls)
- [Test kapsayıcısı ile özellikleri ve olayları test etme](/cpp/mfc/testing-properties-and-events-with-test-container)
- [COM ve ActiveX hata ayıklama](../debugger/com-and-activex-debugging.md)
- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
