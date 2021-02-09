---
title: Data-Bound ActiveX denetiminde hata ayıklama | Microsoft Docs
description: Hata ayıklama için bir kapsayıcı uygulaması oluşturarak bir veri kaynağı denetimine yönelik bir ActiveX denetiminde hata ayıklamanın nasıl yapılacağını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 24de30887185ce4520817904ec6348ef6276b6d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872904"
---
# <a name="debugging-a-data-bound-activex-control"></a>Veri Bağımlı ActiveX Denetiminde Hata Ayıklama
Bir veri kaynağı denetimine bağlanacak bir ActiveX denetimi geliştiriyorsanız, kendi kapsayıcı uygulamanızı oluşturabilir ve bu kapsayıcıyı ActiveX denetiminde hata ayıklamak için kullanabilirsiniz.

 Örneğin, iletişim kutusuna bir iletişim kutusu tabanlı MFC uygulaması oluşturabilir ve veri bağlantılı denetiminizi ve bir veri kaynağı denetimini yerleştirebilirsiniz. Bu MFC uygulamasını, çalışma zamanı testi için ve veri bağlantılı ActiveX denetiminizin hata ayıklaması için kapsayıcı yürütülebilir dosyası olarak kullanabilirsiniz.

## <a name="using-the-test-container"></a>Test kapsayıcısını kullanma
 Denetim ya da kapsayıcıda çeşitli arabirimleri desteklemek üzere kolayca değiştirebileceğiniz bir kapsayıcı isterseniz, hata ayıklama oturumu için yürütülebilir dosya olarak ActiveX test kapsayıcısını kullanın. Farklı arabirimleri etkinleştirmek için, ActiveX test kapsayıcısında **kapsayıcı** menüsünde **Seçenekler** ' e tıklayın. Daha fazla bilgi için bkz. [Test kapsayıcısı Ile özellikleri ve olayları test etme](/cpp/mfc/testing-properties-and-events-with-test-container).

 Hata ayıklarken kapsayıcının kodunu değiştirmeniz gerekiyorsa, kapsayıcının hata ayıklama sürümünü kullanın veya ActiveX test kapsayıcısının hata ayıklama sürümünü kullanın. Daha fazla bilgi için bkz. [tstcon örneği: ActiveX denetimi test kapsayıcısı](/previous-versions/f9adb5t5(v=vs.100)).

## <a name="see-also"></a>Ayrıca bkz.
- [COM ve ActiveX hata ayıklaması](../debugger/com-and-activex-debugging.md)
- [ActiveX denetimleri](/cpp/mfc/activex-controls)