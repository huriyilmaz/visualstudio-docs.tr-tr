---
title: ActiveX denetiminde hata ayıklama | Microsoft Docs
description: ActiveX denetiminde hata ayıklamayı öğrenin. Proje özellik sayfalarında yapabileceğiniz veya hata ayıklamaya başladığınızda kullanabileceğiniz bir içeren yürütülebilir dosya belirtmeniz gerekir.
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
ms.workload:
- multiple
ms.openlocfilehash: 6728b498da91f540d92182ad60f23e490d614948
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160401"
---
# <a name="how-to-debug-an-activex-control"></a>Nasıl Yapılır: ActiveX Denetiminde Hata Ayıklama

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünden Içeri ve dışarı aktarma ayarları ' nı seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

ActiveX denetimi hata ayıklaması yapmak için denetimin içinde çalışacağı bir kapsayıcı (yürütülebilir) belirtmeniz gerekir.

## <a name="to-specify-a-container-for-the-debug-session"></a>Hata ayıklama oturumu için bir kapsayıcı belirtmek için

1. Çözüm Gezgini, projeyi seçin.

2. **Görünüm** menüsünde **Özellik sayfaları**' nı seçin.

3. **Proje özellik sayfaları** iletişim kutusunda, **yapılandırma özellikleri** klasörünü açın ve **hata ayıklama** öğesini seçin.

4. **Hata ayıklama** kategorisi altında, **komut** özelliğini bulun.

5. Kapsayıcının yol adını belirtin. Örneğin, C:\Program Files\ınternet Explorer\IEXPLORE.EXE.

6. Kapsayıcı olarak Internet Explorer 'ı belirtirseniz ve etkin masaüstü kullanıyorsanız, `/new` **komut bağımsız değişkenleri** kutusuna yazın.

7. **Tamam**'a tıklayın.

     **Proje özellik sayfaları** iletişim kutusunda bir kapsayıcı belirtmezseniz, hata ayıklamaya başladığınızda kapsayıcıyı belirtebilirsiniz. Hata ayıklamayı başlatmak için bir yürütme komutu seçtiğinizde, [hata ayıklama oturumu Için yürütülebilir Iletişim kutusu](../debugger/executable-for-debugging-session-dialog-box.md) görüntülenir. İletişim kutusunda kapsayıcının yol adını belirtin.

## <a name="see-also"></a>Ayrıca bkz.

- [ActiveX denetimleri](/cpp/mfc/activex-controls)
- [Test kapsayıcısı ile özellikleri ve olayları test etme](/cpp/mfc/testing-properties-and-events-with-test-container)
- [COM ve ActiveX hata ayıklaması](../debugger/com-and-activex-debugging.md)
- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
