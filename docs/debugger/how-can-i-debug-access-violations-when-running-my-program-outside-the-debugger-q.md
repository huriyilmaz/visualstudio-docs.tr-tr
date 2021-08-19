---
title: Uygulama Visual Studio dışında çalıştırırken erişim ihlallerinde hata ayıkla
titleSuffix: ''
description: Visual Studio ortamının dışında oluşan bir erişim ihlaline hata ayıklaması yapmak için tam zamanında hata ayıklayıcıyı kullanın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ec9b41f45211294f0587d4e78fc879394e677e7f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080825"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Kendi Programımı Hata Ayıklayıcı Dışında Çalıştırırken Erişim İhlallerinde Nasıl Hata Ayıklayabilirim?

## <a name="problem-description"></a>Sorun Açıklaması
 programımı Visual Studio ortamda ince çalışır, ancak Windows işletim sistemiyle tek başına çalıştırıldığımda, bir erişim ihlali üretir. Bu sorunu nasıl ayıklayabilirim?

## <a name="solution"></a>Çözüm
 [Tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md) seçeneğini ayarlayın ve erişim ihlali gerçekleşene kadar programınızı tek başına çalıştırın. Ardından, **erişim ihlali** iletişim kutusunda, hata ayıklayıcıyı başlatmak için **iptal** ' e tıklayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel kod SSS hatalarını ayıklama](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)