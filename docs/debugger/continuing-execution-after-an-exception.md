---
title: Özel Durum Sonrasında Yürütmeye Devam | Microsoft Docs
description: Hata ayıklayıcı işlanmamış bir özel durum nedeniyle yürütmeyi sonlara ayırsa ne olacağını öğrenin. Aynı iş parçacığında yürütmeye devam etmek mümkün olabilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: baed5da414077ee5d81482f092e697ddb608e420
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121732"
---
# <a name="continuing-execution-after-an-exception"></a>Özel Durumdan Sonra Yürütmeye Devam Etme
Hata ayıklayıcısı bir özel durum nedeniyle yürütmeyi bozarsa, varsayılan olarak **Özel Durum Yardımcı'sını** göreceğiz. Seçenekler iletişim kutusunda Özel Durum  **Yardımcısı'nın** devre dışı bırakılmıştır, Özel Durum Yardımcısı **(C#** veya Visual Basic) veya Özel Durum iletişim kutusunu (C++) alırsınız. 

 Özel **Durum Yardımcı'sı** göründüğünde, özel durumla ilgili sorunu düzeltmeyi denemeyi edebilirim.

## <a name="managed-and-native-code"></a>Yönetilen ve Yerel Kod
 Yönetilen ve yerel kodda, iş parçacıklı bir özel durum sonrasında aynı iş parçacığında yürütmeye devam edersiniz. Özel **Durum Yardımcı,** çağrı yığınını özel durumun atılmış olduğu noktaya doğru geriye doğru geriye doğru takip eder.

## <a name="mixed-code"></a>Karma Kod
 Karma yerel ve yönetilen kodda hata ayıklarken işlenebilir olmayan bir özel durumla karşılaşırsanız, işletim sistemi kısıtlamaları çağrı yığınının geriye doğru izlemesini önler. Kısayol menüsünü kullanarak çağrı yığınını geri sarmayı denersanız, hata ayıklayıcının karma kod hata ayıklaması dışında işlanmamış bir öğeden geriye doğru geri alamayğını açıklayan bir hata iletisi görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumları Hata Ayıklayıcısı ile Yönetme](../debugger/managing-exceptions-with-the-debugger.md)