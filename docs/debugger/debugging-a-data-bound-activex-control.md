---
title: Data-Bound ActiveX Control | Hata Ayıklama Microsoft Docs
description: Hata ayıklama için bir kapsayıcı ActiveX bir veri kaynağı denetimine bağlı bir uygulamanın hata ayıklamasını öğrenin.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 75339365340c7133a5faf9573cf65dab1bb171b91c33c3b89917c0d213e58d9e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121344118"
---
# <a name="debugging-a-data-bound-activex-control"></a>Veri Bağımlı ActiveX Denetiminde Hata Ayıklama
Veri kaynağı denetimine ActiveX bir kapsayıcı denetimi geliştiriyorsanız, kendi kapsayıcı uygulamanızı oluşturabilir ve bu kapsayıcıyı kullanarak veri kaynağı denetimi hata ActiveX kullanabilirsiniz.

 Örneğin, iletişim kutusu tabanlı bir MFC uygulaması oluşturabilir ve veriye bağlı denetiminizi ve bir veri kaynağı denetiminizi iletişim kutusuna yer değiştirebilirsiniz. Bu MFC uygulamasını çalışma zamanı testi için ve veriye bağlı uygulama denetiminizin hata ayıklaması için kapsayıcı yürütülebilir dosyası ActiveX kullanabilirsiniz.

## <a name="using-the-test-container"></a>Test Kapsayıcısı Kullanma
 Denetimde veya kapsayıcıda çeşitli arabirimleri destekleyecek şekilde kolayca değiştirebiliyorsanız, hata ayıklama oturumunun yürütülebilir dosyası olarak ActiveX Test Kapsayıcısı'nın kullanın. Test Kapsayıcısı ActiveX çeşitli **arabirimleri** etkinleştirmek **için Kapsayıcı** menüsünden Seçenekler'e tıklayın. Daha fazla bilgi için [bkz. Test Kapsayıcısı ile Özellikleri ve Olayları Test Etme.](/cpp/mfc/testing-properties-and-events-with-test-container)

 Hata ayıklama sırasında kapsayıcının koduna adımlamanız gerekirse, kapsayıcının hata ayıklama sürümünü veya Test Kapsayıcısı'nın ActiveX sürümünü kullanın. Daha fazla bilgi için bkz. [TSTCON Örneği: ActiveX Test Kapsayıcısı.](/previous-versions/f9adb5t5(v=vs.100))

## <a name="see-also"></a>Ayrıca bkz.
- [COM ve ActiveX Hata Ayıklama](../debugger/com-and-activex-debugging.md)
- [ActiveX Denetim](/cpp/mfc/activex-controls)