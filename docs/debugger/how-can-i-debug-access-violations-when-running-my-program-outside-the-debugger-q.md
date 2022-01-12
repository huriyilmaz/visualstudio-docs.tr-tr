---
title: Uygulamayı uygulamanın dışında çalıştırarak erişim ihlallerinin Visual Studio
titleSuffix: ''
description: Uygulama ortamının dışında oluşan erişim ihlalinde hata ayıklamak için Tam Zamanında Hata Ayıklayıcı'Visual Studio kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: ef9b645c22296aeaa9af3c08e3767e6c821c954b
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135804148"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Kendi Programımı Hata Ayıklayıcı Dışında Çalıştırırken Erişim İhlallerinde Nasıl Hata Ayıklayabilirim?

## <a name="problem-description"></a>Sorun Açıklaması
 Programım Visual Studio iyi çalışıyor, ancak bunu işletim sistemiyle tek başına Windows erişim ihlaline neden oluyor. Bu sorunda nasıl hata ayık bilmiyorum?

## <a name="solution"></a>Çözüm
 Tam [zamanında hata ayıklama seçeneğini ayarlayın ve](../debugger/just-in-time-debugging-in-visual-studio.md) erişim ihlali oluşana kadar programınızı tek başına çalıştırın. Ardından, Erişim **İhlali** iletişim kutusunda İptal'e **tıklar ve** hata ayıklayıcıyı başlatabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kodda Hata Ayıklama hakkında SSS](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)