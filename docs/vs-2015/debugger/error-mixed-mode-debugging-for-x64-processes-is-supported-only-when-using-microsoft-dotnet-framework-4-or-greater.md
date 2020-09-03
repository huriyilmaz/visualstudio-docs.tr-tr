---
title: 'Hata: x64 işlemlerine yönelik karışık modda hata ayıklama yalnızca Microsoft .NET Framework 4 veya daha yenisi kullanılırken desteklenir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 190a6e890ce31ce2aa66ff474bb9e4b1976a6c46
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67824004"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Hata: x64 işlemleri için karışık modda hata ayıklama yalnızca Microsoft .NET Framework 4 veya daha yenisi kullanılırken desteklenir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

64 bitlik bir işlemde karışık yerel ve yönetilen kodda hata ayıklamak için sürüm 4 ' e sahip olmanız gerekir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . 4 ' ten önceki sürümlere sahip 64 bit işlemlerdeki karışık modda hata ayıklama [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] desteklenmez.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Aşağıdaki adımlardan birini uygulayın:  
  
  - Sürümünüzü [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sürüm 4 ' e yükseltin.  

  - Hata ayıklama için uygulamanızın 32 bitlik bir sürümünü oluşturun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Cihazda uzak araçları ayarlama](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
