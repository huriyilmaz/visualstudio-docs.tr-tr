---
title: ActiveX Control | Microsoft Docs
description: Bir denetimde hata ayıklamayı ActiveX öğrenin. İçeren bir yürütülebilir dosya belirtmeniz gerekir. Bunu özellik Project hata ayıklamaya başlarken de kullanabilirsiniz.
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
ms.openlocfilehash: e3d47b749813fe4d60fde4086e5b4eeb66cff651
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161303"
---
# <a name="how-to-debug-an-activex-control"></a>Nasıl Yapılır: ActiveX Denetiminde Hata Ayıklama

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünde İçeri ve Dışarı Ayarlar'yi seçin. Daha fazla bilgi için [bkz. Ayarları sıfırlama.](../ide/environment-settings.md#reset-settings)

Uygulama denetiminizin ActiveX ayıklamak için, denetimin içinde çalışması için bir kapsayıcı (yürütülebilir) belirtmeniz gerekir.

## <a name="to-specify-a-container-for-the-debug-session"></a>Hata ayıklama oturumu için bir kapsayıcı belirtmek için

1. Bu Çözüm Gezgini projesini seçin.

2. Görünüm **menüsünden** Özellik **Sayfaları'ı seçin.**

3. Project **Sayfaları iletişim kutusunda** Yapılandırma Özellikleri klasörünü **açın ve Hata** Ayıklama'ya **tıklayın.**

4. Hata **ayıklama kategorisi** altında **Command özelliğini** bulun.

5. Kapsayıcının yol adını belirtin. Örneğin, C:\Program Files\Internet Explorer\IEXPLORE.EXE.

6. Kapsayıcı olarak Internet Explorer ve kapsayıcıyı kullanıyorsanız Active Desktop Bağımsız Değişkenler `/new` **kutusuna** yazın.

7. **Tamam**'a tıklayın.

     Project Özellik Sayfaları iletişim kutusunda **bir** kapsayıcı belirtmezseniz, hata ayıklamaya başlarken kapsayıcıyı belirtebilirsiniz. Hata ayıklamaya başlamak için bir yürütme komutu seçerek Hata Ayıklama için [Yürütülebilir Oturum İletişim Kutusu](../debugger/executable-for-debugging-session-dialog-box.md) görüntülenir. İletişim kutusunda kapsayıcının yol adını belirtin.

## <a name="see-also"></a>Ayrıca bkz.

- [ActiveX Denetim](/cpp/mfc/activex-controls)
- [Test Kapsayıcısı ile Özellikleri ve Olayları Test Etme](/cpp/mfc/testing-properties-and-events-with-test-container)
- [COM ve ActiveX Hata Ayıklama](../debugger/com-and-activex-debugging.md)
- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
