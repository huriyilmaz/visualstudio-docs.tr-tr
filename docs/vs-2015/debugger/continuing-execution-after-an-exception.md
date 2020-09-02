---
title: Özel durumdan sonra yürütmeye devam etme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
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
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6ae74c51f0f738bc596fbe5c789011630927707c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702261"
---
# <a name="continuing-execution-after-an-exception"></a>Özel Durumdan Sonra Yürütmeye Devam Etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir özel durum nedeniyle hata ayıklayıcı yürütmeyi kaparsa bir iletişim kutusu görünür. Visual Basic veya C# için, varsayılan olarak [özel durum Yardımcısı](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb) iletişim kutusu görüntülenir. C++ için eski **özel durum** iletişim kutusunu görürsünüz. Visual Basic veya C# kullanıyorsanız ancak **Seçenekler** Iletişim kutusunda **özel durum yardımcısını** devre dışı bırakırsanız, **özel durum** iletişim kutusunu görürsünüz.  
  
 Özel durum **Yardımcısı** veya **özel durum** iletişim kutusu göründüğünde, özel duruma neden olan sorunu gidermeyi deneyebilirsiniz.  
  
## <a name="managed-code"></a>Yönetilen kod  
 Yönetilen kodda, işlenmeyen bir özel durumdan sonra aynı iş parçacığında yürütmeye devam edebilirsiniz. **Özel durum Yardımcısı** , çağrı yığınını özel durumun oluşturulduğu noktaya geri vermez.  
  
## <a name="native-code"></a>Yerel kod  
 Yerel C/C++ ' da iki seçeneğiniz vardır:  
  
- **Kes** ' e tıklayabilir ve sorunu gidermeye çalışırsınız. Kesme modundayken çağrı yığınını, **çağrı yığını** penceresinde bir çerçeveye sağ tıklayıp kısayol menüsünde **Bu çerçeveye geri dön** seçeneğini belirleyerek aşağı doğru taşıyabilirsiniz. Hata ayıklamaya devam ettiğinizde, sorunu düzeltmediyse **özel durum** iletişim kutusu tekrar görünür. Aksi takdirde, **özel durum** iletişim kutusu yeniden görüntülenir.  
  
- Sorunu gidermeye çalışmamadan yürütmeye devam etmek için **devam** ' a tıklayabilirsiniz. **Özel durum** iletişim kutusu yeniden görüntülenir.  
  
## <a name="mixed-code"></a>Karışık kod  
 Karma bir yerel ve yönetilen kodda hata ayıklarken işlenmeyen bir özel durumla karşılaşırsanız, işletim sistemi kısıtlamaları çağrı yığınını geriye doğru geri çağırmayı önler. Çağrı yığınını kısayol menüsünü kullanarak yeniden geri sarılıyorsanız, hata iletisi, karışık kod hata ayıklaması dışında işlenmeyen bir işlenmemiş öğesinden geriye doğru bir hata mesajı olduğunu açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Durumları Hata Ayıklayıcısı ile Yönetme](../debugger/managing-exceptions-with-the-debugger.md)
