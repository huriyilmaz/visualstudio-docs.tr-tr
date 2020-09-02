---
title: 'Hata: uzak makine uzak bağlantılar iletişim kutusunda görünmüyor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5fd98a5b-2cf3-4438-8b0f-6f1a742a62ce
caps.latest.revision: 5
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a97211c1fa86123a2a7a65f2ff86b0cecac957dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697320"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Hata: Uzak Makine, Uzaktan Bağlantılar iletişim kutusunda görünmüyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uzak makine uzak bağlantılar iletişim kutusunda görünmüyorsa, aşağıdaki genel nedenleri kontrol edin.  
  
 Yönetilen Uyumluluk modu kullanıyorsanız, lütfen Visual Studio 2010 belgelerini denetleyin: [Uzaktan hata ayıklama sorunlarını giderme-Visual Studio 2010](https://msdn.microsoft.com/library/2ys11ead\(v=vs.100\).aspx) .  
  
### <a name="common-causes-for-this-error"></a>Bu hatanın yaygın nedenleri  
  
- Uzak makine, farklı bir alt ağda bulunan bir makinede çalışıyor. Bu hatayı gidermek için, niteleyici iletişim kutusunda makine adını veya IP adresini el ile yazın  
  
- Uzak makinede uzaktan hata ayıklayıcı çalışmıyor. Bu hatayı düzeltemedi, uzaktan hata ayıklayıcıyı başlatın.  
  
- Güvenlik Duvarı, Visual Studio ile uzak makine arasındaki iletişimi engelliyor. Bu hatayı onarmak için, güvenlik duvarınızı Visual Studio ve uzaktan hata ayıklayıcı 'nın (msvsmon) iletişim kurmasına izin verecek şekilde yapılandırın.  
  
- Virüsten koruma yazılımı, Visual Studio ile uzak makine arasındaki iletişimi engelliyor. Bu hatayı onarmak için, virüsten koruma yazılımını Visual Studio ve uzaktan hata ayıklayıcı 'nın (msvsmon) iletişim kurmasına izin verecek şekilde yapılandırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Cihazda uzak araçları ayarlama](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
