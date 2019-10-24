---
title: 'Nasıl yapılır: ActiveX denetiminde hata ayıklama | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75abf76516d3827a748e1b896d4c2e8c93bb34da
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733877"
---
# <a name="how-to-debug-an-activex-control"></a>Nasıl Yapılır: ActiveX Denetiminde Hata Ayıklama

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünden Içeri ve dışarı aktarma ayarları ' nı seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

ActiveX denetimi hata ayıklaması yapmak için denetimin içinde çalışacağı bir kapsayıcı (yürütülebilir) belirtmeniz gerekir.

## <a name="to-specify-a-container-for-the-debug-session"></a>Hata ayıklama oturumu için bir kapsayıcı belirtmek için

1. Çözüm Gezgini, projeyi seçin.

2. **Görünüm** menüsünde **Özellik sayfaları**' nı seçin.

3. **Proje özellik sayfaları** iletişim kutusunda, **yapılandırma özellikleri** klasörünü açın ve **hata ayıklama**öğesini seçin.

4. **Hata ayıklama** kategorisi altında, **komut** özelliğini bulun.

5. Kapsayıcının yol adını belirtin. Örneğin, C:\Program Files\Explorer\IEXPLORE. EXE.

6. Kapsayıcı olarak Internet Explorer 'ı belirtirseniz ve etkin masaüstü kullanıyorsanız, **komut bağımsız değişkenleri** kutusuna `/new` yazın.

7. **Tamam**'a tıklayın.

     **Proje özellik sayfaları** iletişim kutusunda bir kapsayıcı belirtmezseniz, hata ayıklamaya başladığınızda kapsayıcıyı belirtebilirsiniz. Hata ayıklamayı başlatmak için bir yürütme komutu seçtiğinizde, [hata ayıklama oturumu Için yürütülebilir Iletişim kutusu](../debugger/executable-for-debugging-session-dialog-box.md) görüntülenir. İletişim kutusunda kapsayıcının yol adını belirtin.

## <a name="see-also"></a>Ayrıca bkz.

- [ActiveX Denetimleri](/cpp/mfc/activex-controls)
- [Test Kapsayıcısı ile Özellikleri ve Olayları Test Etme](/cpp/mfc/testing-properties-and-events-with-test-container)
- [COM ve ActiveX Hata Ayıklaması](../debugger/com-and-activex-debugging.md)
- [Visual Studio’da hata ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)