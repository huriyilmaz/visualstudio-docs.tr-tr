---
title: Uzak makine uzak bağlantılar iletişim kutusunda görünmüyor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: be39d733b2e5fe83fa9f7e2241c7de06980bb583
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871382"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Hata: Uzak Makine, Uzaktan Bağlantılar iletişim kutusunda görünmüyor
Uzak makine uzak bağlantılar iletişim kutusunda görünmüyorsa, aşağıdaki genel nedenleri kontrol edin.

 Yönetilen Uyumluluk modu kullanıyorsanız, lütfen Visual Studio 2010 belgelerini denetleyin: [Uzaktan hata ayıklama sorunlarını giderme-Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).

### <a name="common-causes-for-this-error"></a>Bu hatanın yaygın nedenleri

- Uzak makine, farklı bir alt ağda bulunan bir makinede çalışıyor. Bu hatayı gidermek için, niteleyici iletişim kutusunda makine adını veya IP adresini el ile yazın

- Uzak makinede uzaktan hata ayıklayıcı çalışmıyor. Bu hatayı düzeltemedi, uzaktan hata ayıklayıcıyı başlatın.

- Güvenlik Duvarı, Visual Studio ile uzak makine arasındaki iletişimi engelliyor. Bu hatayı onarmak için, güvenlik duvarınızı Visual Studio ve uzaktan hata ayıklayıcı 'nın (msvsmon) iletişim kurmasına izin verecek şekilde yapılandırın.

- Virüsten koruma yazılımı, Visual Studio ile uzak makine arasındaki iletişimi engelliyor. Bu hatayı onarmak için, virüsten koruma yazılımını Visual Studio ve uzaktan hata ayıklayıcı 'nın (msvsmon) iletişim kurmasına izin verecek şekilde yapılandırın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)