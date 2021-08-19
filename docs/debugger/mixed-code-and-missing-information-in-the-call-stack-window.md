---
title: Çağrı Yığını & eksik bilgiler için karışık kod
description: Karma modlu programlarda (yerel ve yönetilen) hata ayıklayıcı her zaman tam çağrı yığınını gösterelemez. Yerel kod yönetilen kodu çağıran olası tutarsızlıkları öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 125eabe8e41b0ed63a8c5e4b942150d2b17d9be5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153933"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Çağrı Yığını Penceresinde Karışık Kod ve Eksik Bilgiler
Yönetilen ve yerel kod için çağrı yığınları arasındaki farklar nedeniyle, kod türleri karma olduğunda hata ayıklayıcı her zaman tam çağrı yığınını gösteramaz. Yerel kod yönetilen kodu çağırsa, Çağrı Yığını penceresinde aşağıdaki **tutarsızlıkları görebilirsiniz:**

- Yönetilen kodun hemen üzerindeki yerel çerçeve Çağrı Yığını penceresinde **eksik** olabilir. Daha fazla bilgi için, [bkz. How to: Step out out Managed Code when Native Frames are Missing from the Call Stack Window](how-to-use-the-call-stack-window.md).

- Hata ayıklayıcı dışında başlatılan karma modlu uygulamalar için Çağrı Yığını penceresi yalnızca yönetilen kodu görüntüler ve yerel karelerin hiçbiri görünmez. 

  Her iki durum da oldukça nadirdir. Yönetilen koda yapılan çoğu yerel çağrıda çağrı yığınları doğru görünür.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Yapılır: Çağrı Yığını Penceresini Kullanma](../debugger/how-to-use-the-call-stack-window.md)