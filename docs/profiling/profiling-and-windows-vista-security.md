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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778381"
---
# <a name="profiling-and-windows-vista-security"></a>Profil oluşturma ve Windows Vista güvenliği

Bir bilgisayar yöneticisinin kullanılabilir hale yaptığı [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] Kullanıcı erişim Izinleri ayarlarına bağlı olarak, bireysel bir kullanıcı o bilgisayardaki bir işlemi profile yönelik güvenlik iznine sahip olabilir. Aşağıdaki örneklerde kullanıcılar arasındaki olası farklılıklar gösterilmektedir:

- Yönetici, sürücüyü ve hizmeti başlatmaya ayarladıktan sonra bazı kullanıcılar Gelişmiş profil oluşturma özelliklerine erişebilir.

- Etki alanı kullanıcıları yalnızca örnek profil oluşturma erişimi sağlayabilir.

- Bazı kullanıcılar, diğer tüm kullanıcılar için profil oluşturmaya erişimi reddedebilir.

  Daha fazla bilgi için bkz. [VSPerfCmd](../profiling/vsperfcmd.md)içindeki yönetici seçenekleri.

## <a name="cross-session-profiling"></a>Çapraz oturum profili oluşturma

*Çapraz oturum profili oluşturma* , farklı bir kullanıcı oturumunda çalışan bir işlemi profil oluşturma olanağıdır. Örneğin, çoğu hizmet oturum 0 ' da çalışır ve kullanıcılar 0 oturumunda doğrudan çalıştırılamaz. Performans Gezgini araç çubuğundaki **Işleme İliştir** düğmesini veya VSPerfCmd komut satırı aracının `/attach` seçeneğini kullanarak, birçok işlemi farklı kullanıcı oturumlarında profil oluşturabilirsiniz.

İşlemler arası profil oluşturma görünürlüğü seçeneklerini ayarlayarak kullanılabilir işlemlerin bir listesini görebilirsiniz. Bu seçenekler, **işleme**İliştir ' i seçtiğinizde görüntülenen **İşleme İliştir** penceresinde kullanılabilir:

- **Tüm kullanıcılardan işlem göster**

  Bu seçenek seçilmezse, listede yalnızca geçerli kullanıcıya ait olan süreçler görüntülenir. Aksi takdirde, listede tüm kullanıcıların süreçler görüntülenir.

- **Tüm oturumlarda işlem göster**

  Bu seçenek seçilmezse, listede geçerli oturumdaki süreçler görüntülenir. Aksi takdirde, listede tüm oturumlardaki süreçler görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel Bakışlar](../profiling/overviews-performance-tools.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Nasıl yapılır: çalışan bir işleme Iliştirme](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z\(v\=vs.100\))
