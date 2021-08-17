---
description: Uzak makine Uzak Bağlantılar iletişim kutusunda görünmüyorsa, aşağıdaki yaygın nedenleri kontrol edin.
title: Uzak makine, Uzak Bağlantılar iletişim kutusunda | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 28d4086185a99ede835f2e2a05520732fbb9e2fe43f61c34188462a971371ba0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420189"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Hata: Uzak Makine, Uzaktan Bağlantılar iletişim kutusunda görünmüyor
Uzak makine Uzak Bağlantılar iletişim kutusunda görünmüyorsa, aşağıdaki yaygın nedenleri kontrol edin.

 Yönetilen uyumluluk modunu kullanıyorsanız lütfen Visual Studio 2010 belgelerini inceleyin: Uzaktan Hata Ayıklama Sorunlarını Giderme [- Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).

### <a name="common-causes-for-this-error"></a>Bu hatanın yaygın nedenleri

- Uzak makine farklı bir alt ağda yer alan bir makinede çalışıyor. Bunu düzeltmek için, Niteleyici iletişim kutusuna makine adını veya IP adresini el ile yazın

- Uzak hata ayıklayıcı uzak makinede çalışmıyor. Bunu düzeltmek için uzak hata ayıklayıcısını başlat.

- Güvenlik duvarı, uzak makineyle Visual Studio arasındaki iletişimi engelliyor. Bunu düzeltmek için güvenlik duvarınızı, uzaktan Visual Studio (msvsmon) ile iletişim kurmasına izin verecek şekilde yapılandırabilirsiniz.

- Virüsten koruma yazılımı, Visual Studio makine arasındaki iletişimi engelliyor. Bunu düzeltmek için, uzaktan hata ayıklayıcısının (msvsmon Visual Studio iletişim kurmasına izin vermek için virüsten koruma yazılımını yapılandırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)
