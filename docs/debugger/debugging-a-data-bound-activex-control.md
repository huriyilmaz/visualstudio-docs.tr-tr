---
title: Veri bağlantılı ActiveX denetiminde hata ayıklama | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ccca00387e701d62e47eee0a93adff44a4765fa2
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600069"
---
# <a name="debugging-a-data-bound-activex-control"></a>Veri Bağımlı ActiveX Denetiminde Hata Ayıklama
Bir veri kaynağı denetimine bağlanacak bir ActiveX denetimi geliştiriyorsanız, kendi kapsayıcı uygulamanızı oluşturabilir ve bu kapsayıcıyı ActiveX denetiminde hata ayıklamak için kullanabilirsiniz.

 Örneğin, iletişim kutusuna bir iletişim kutusu tabanlı MFC uygulaması oluşturabilir ve veri bağlantılı denetiminizi ve bir veri kaynağı denetimini yerleştirebilirsiniz. Bu MFC uygulamasını, çalışma zamanı testi için ve veri bağlantılı ActiveX denetiminizin hata ayıklaması için kapsayıcı yürütülebilir dosyası olarak kullanabilirsiniz.

## <a name="using-the-test-container"></a>Test kapsayıcısını kullanma
 Denetim ya da kapsayıcıda çeşitli arabirimleri desteklemek üzere kolayca değiştirebileceğiniz bir kapsayıcı isterseniz, hata ayıklama oturumu için yürütülebilir dosya olarak ActiveX test kapsayıcısını kullanın. Farklı arabirimleri etkinleştirmek için, ActiveX test kapsayıcısında **kapsayıcı** menüsünde **Seçenekler** ' e tıklayın. Daha fazla bilgi için bkz. [Test kapsayıcısı Ile özellikleri ve olayları test etme](/cpp/mfc/testing-properties-and-events-with-test-container).

 Hata ayıklarken kapsayıcının kodunu değiştirmeniz gerekiyorsa, kapsayıcının hata ayıklama sürümünü kullanın veya ActiveX test kapsayıcısının hata ayıklama sürümünü kullanın. Daha fazla bilgi için bkz. [tstcon örneği: ActiveX denetimi test kapsayıcısı](/previous-versions/f9adb5t5(v=vs.100)).

## <a name="see-also"></a>Ayrıca bkz.
- [COM ve ActiveX Hata Ayıklaması](../debugger/com-and-activex-debugging.md)
- [ActiveX denetimleri](/cpp/mfc/activex-controls)