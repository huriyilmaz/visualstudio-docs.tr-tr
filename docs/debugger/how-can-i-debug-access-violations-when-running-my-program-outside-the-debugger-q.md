---
title: Uygulama hata ayıklayıcı dışında çalıştırılırken erişim ihlallerine hata ayıkla
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88dde869e6e9e1551459ce1171364709baf6403e
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350439"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Kendi Programımı Hata Ayıklayıcı Dışında Çalıştırırken Erişim İhlallerinde Nasıl Hata Ayıklayabilirim?

## <a name="problem-description"></a>Sorun Açıklaması
 Programımı Visual Studio ortamında sorunsuz çalışıyor, ancak Windows işletim sistemiyle tek başına çalıştırıldığında bir erişim ihlali oluşturur. Bu sorunu nasıl ayıklayabilirim?

## <a name="solution"></a>Çözüm
 [Tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md) seçeneğini ayarlayın ve erişim ihlali gerçekleşene kadar programınızı tek başına çalıştırın. Ardından, **erişim ihlali** iletişim kutusunda, hata ayıklayıcıyı başlatmak için **iptal** ' e tıklayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kod Hata Ayıklaması SSS](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)