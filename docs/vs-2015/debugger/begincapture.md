---
title: BeginCapture | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b16fdc4d0a12d7082400e697ca44a7ca4c549f9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431803"
---
# <a name="begincapture"></a>BeginCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İle biten bir yakalama aralığı başlatır `EndCapture` .  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void BeginCapture();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Yakalama aralığı genellikle yalnızca belirli bir çizim çağrısı türü hakkında grafik bilgilerini yakalamak istediğinizde olduğu gibi, bir çerçevenin alt kümesini kapsar. Yakalama aralığı, var olan bir çağrıya yayılırsa, grafik bilgilerinin iki çerçevesi yakalanır. İlk çerçeve, çağrısı ve var olan çağrı arasındaki aralığı kapsar `BeginCapture` ; ikinci kare, çağrısı ve çağrısı sonrasında Ilk Direct3D olayı arasındaki aralığı kapsar `EndCapture` .  
  
 Bir aralığı yakalamak için, uygulamanızı grafik bilgilerini yakalamak ve kaydetmek üzere hazırlamanız gerekir — diğer bir deyişle, [Init](../debugger/init.md) `VsgDbg` veya çağrısından önce sınıfının bir örneğini kullanarak Init olarak adlandırmanız gerekir `BeginCapture` `EndCapture` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [EndCapture](../debugger/endcapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)
