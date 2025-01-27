---
title: Özel durumdan sonra yürütmeye devam etme | Microsoft Docs
description: İşlenmeyen bir özel durum nedeniyle hata ayıklayıcı yürütmeyi kesintiye düğünde ne olacağını öğrenin. Aynı iş parçacığında yürütmeye devam edebilirsiniz.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630866"
---
# <a name="continuing-execution-after-an-exception"></a>Özel Durumdan Sonra Yürütmeye Devam Etme
Bir özel durum nedeniyle hata ayıklayıcı yürütmeyi bozarsa, varsayılan olarak **özel durum yardımcısını** görürsünüz. **seçenekler** iletişim kutusunda **özel durum yardımcısını** devre dışı bırakırsanız, **özel durum yardımcısı** (C# veya Visual Basic) veya **özel durum** iletişim kutusu (C++) görüntülenir.

 **Özel durum Yardımcısı** göründüğünde, özel duruma neden olan sorunu gidermeyi deneyebilirsiniz.

## <a name="managed-and-native-code"></a>Yönetilen ve yerel kod
 Yönetilen ve yerel kodda, işlenmeyen bir özel durumdan sonra aynı iş parçacığında yürütmeye devam edebilirsiniz. **Özel durum Yardımcısı** , çağrı yığınını özel durumun oluşturulduğu noktaya geri vermez.

## <a name="mixed-code"></a>Karışık kod
 Karma bir yerel ve yönetilen kodda hata ayıklarken işlenmeyen bir özel durumla karşılaşırsanız, işletim sistemi kısıtlamaları çağrı yığınını geriye doğru geri çağırmayı önler. Çağrı yığınını kısayol menüsünü kullanarak yeniden geri sarılıyorsanız, hata iletisi, karışık kod hata ayıklaması dışında işlenmeyen bir işlenmemiş öğesinden geriye doğru bir hata mesajı olduğunu açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumları Hata Ayıklayıcısı ile Yönetme](../debugger/managing-exceptions-with-the-debugger.md)