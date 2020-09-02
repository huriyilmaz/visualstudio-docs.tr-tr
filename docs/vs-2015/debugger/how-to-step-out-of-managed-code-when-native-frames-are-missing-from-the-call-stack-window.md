---
title: 'Nasıl yapılır: yerel çerçeveler çağrı yığını penceresinde olmadığında yönetilen koddan adımla | Microsoft Docs'
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
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 63bd55fd254dd263540a9161e8579ea6600e97f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690094"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Nasıl Yapılır: Yerel Çerçeveler Çağrı Yığını Penceresinde Olmadığında Yönetilen Kodların Dışına Adımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodunuzun **çağrı yığını** penceresinde görünmez yerel çerçeveleri varsa, yönetilen koddan dışarı adım beklenmedik sonuçlara neden olabilir. Geçici bir çözüm olarak, **Step Out**yerine bir kesme noktası kullanabilirsiniz.  
  
> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Çağrı yığını görüntüsüne yerel çerçeveler olmadığında yönetilen koddan geçmek için  
  
1. Yerel kodda, yönetilen koda çağrıdan sonra bir konum kesme noktası ayarlayın.  
  
2. **Hata Ayıkla** menüsünde **devam**' ı seçin.  
  
     Yönetilen çağrı tamamlandığında, yürütme yerel koddaki kesme noktasında durur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır: Çağrı Yığını Penceresini Kullanma](../debugger/how-to-use-the-call-stack-window.md)
