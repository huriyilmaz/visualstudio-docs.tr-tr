---
title: Profil oluşturma ve Windows Vista güvenliği | Microsoft Docs
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2a74862d59fe402cbfd9e6bfa804d62ca4c8310b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778381"
---
# <a name="profiling-and-windows-vista-security"></a>Profil oluşturma ve Windows Vista güvenliği

[!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)]Bir bilgisayar yöneticisinin kullanılabilir hale getirildiğine yönelik kullanıcı erişim izinleri ayarlarına bağlı olarak, bireysel bir kullanıcı o bilgisayardaki bir işlemi profil için güvenlik iznine sahip olabilir. Aşağıdaki örneklerde kullanıcılar arasındaki olası farklılıklar gösterilmektedir:

- Yönetici, sürücüyü ve hizmeti başlatmaya ayarladıktan sonra bazı kullanıcılar Gelişmiş profil oluşturma özelliklerine erişebilir.

- Etki alanı kullanıcıları yalnızca örnek profil oluşturma erişimi sağlayabilir.

- Bazı kullanıcılar, diğer tüm kullanıcılar için profil oluşturmaya erişimi reddedebilir.

  Daha fazla bilgi için bkz. [VSPerfCmd](../profiling/vsperfcmd.md)içindeki yönetici seçenekleri.

## <a name="cross-session-profiling"></a>Çapraz oturum profili oluşturma

*Çapraz oturum profili oluşturma* , farklı bir kullanıcı oturumunda çalışan bir işlemi profil oluşturma olanağıdır. Örneğin, çoğu hizmet oturum 0 ' da çalışır ve kullanıcılar 0 oturumunda doğrudan çalıştırılamaz. Performans Gezgini araç çubuğundaki **Işleme İliştir** düğmesini veya `/attach` VSPerfCmd komut satırı aracının seçeneğini kullanarak, farklı kullanıcı oturumlarında birçok işlemi de profile olabilirsiniz.

İşlemler arası profil oluşturma görünürlüğü seçeneklerini ayarlayarak kullanılabilir işlemlerin bir listesini görebilirsiniz. Bu seçenekler, **işleme**İliştir ' i seçtiğinizde görüntülenen **İşleme İliştir** penceresinde kullanılabilir:

- **Tüm kullanıcılardan işlem göster**

  Bu seçenek seçilmezse, listede yalnızca geçerli kullanıcıya ait olan süreçler görüntülenir. Aksi takdirde, listede tüm kullanıcıların süreçler görüntülenir.

- **Tüm oturumlarda işlem göster**

  Bu seçenek seçilmezse, listede geçerli oturumdaki süreçler görüntülenir. Aksi takdirde, listede tüm oturumlardaki süreçler görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- ['a Genel Bakış](../profiling/overviews-performance-tools.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Nasıl yapılır: çalışan bir işleme Iliştirme](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z\(v\=vs.100\))
