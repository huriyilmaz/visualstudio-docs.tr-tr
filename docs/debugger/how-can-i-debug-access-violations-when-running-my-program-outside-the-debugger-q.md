---
title: Uygulama hata ayıklayıcı dışında çalıştırılırken erişim ihlallerine hata ayıkla
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: f5009bae2d7679081e29ae8f46d72455beac7e11
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734578"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Kendi Programımı Hata Ayıklayıcı Dışında Çalıştırırken Erişim İhlallerinde Nasıl Hata Ayıklayabilirim?

## <a name="problem-description"></a>Sorun açıklaması
 Programımı Visual Studio ortamında sorunsuz çalışıyor, ancak Windows işletim sistemiyle tek başına çalıştırıldığında bir erişim ihlali oluşturur. Bu sorunu nasıl ayıklayabilirim?

## <a name="solution"></a>Çözüm
 [Tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md) seçeneğini ayarlayın ve erişim ihlali gerçekleşene kadar programınızı tek başına çalıştırın. Ardından, **erişim ihlali** iletişim kutusunda, hata ayıklayıcıyı başlatmak için **iptal** ' e tıklayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kodda Hata Ayıklama SSS](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)