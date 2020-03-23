---
title: Profil oluşturma ve Windows Vista güvenliği | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778381"
---
# <a name="profiling-and-windows-vista-security"></a>Profil oluşturma ve Windows Vista güvenliği

Bir bilgisayar [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] yöneticisinin kullanıma sunmuş kullanıcı erişim izinleri ayarlarına bağlı olarak, tek bir kullanıcı nın söz sahibi bilgisayardaki bir işlemi profillemek için güvenlik iznine sahip olabileceği nden. Aşağıdaki örnekler, kullanıcılar arasındaki olası farklılıkları göstermektedir:

- Yönetici sürücüyü ve hizmeti başlatmak üzere ayarladığında bazı kullanıcılar gelişmiş profil oluşturma özelliklerine erişebilir.

- Etki alanı kullanıcıları yalnızca örnek profil oluşturma erişebilir.

- Bazı kullanıcılar diğer tüm kullanıcılara profil oluşturma erişimini reddedebilir.

  Daha fazla bilgi için [VSPerfCmd'deki](../profiling/vsperfcmd.md)ADMIN seçeneklerine bakın.

## <a name="cross-session-profiling"></a>Oturumlar arası profil oluşturma

*Oturumlar arası profil oluşturma,* farklı bir kullanıcı oturumunda çalışan bir işlemin profilini çıkarma yeteneğidir. Örneğin, çoğu hizmet oturum 0'da çalışır ve kullanıcılar doğrudan oturum 0'da çalıştıramaz. Performans Gezgini araç çubuğundaki **İşleme Ekle** düğmesini veya `/attach` VSPerfCmd komut satırı aracıseçeneğini kullanarak, çoğu işlemin profilini farklı kullanıcı oturumlarında kullanabilirsiniz.

Çapraz işlem profil oluşturma görünürlük seçeneklerini ayarlayarak kullanılabilen işlemlerin listesini görebilirsiniz. Bu seçenekler, **İşleme Ekle'yi**seçtiğinizde görüntülenen **işleme ekle** penceresinde kullanılabilir:

- **Tüm kullanıcıların süreçlerini göster**

  Bu seçenek seçilmediğinde, liste yalnızca geçerli kullanıcıya ait olan işlemleri görüntüler. Aksi takdirde, liste tüm kullanıcıların işlemlerini görüntüler.

- **Tüm oturumlarda süreçleri göster**

  Bu seçenek seçilmediğinde, liste geçerli oturumdaki işlemleri görüntüler. Aksi takdirde, liste tüm oturumlarda işlemleri görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel bakış](../profiling/overviews-performance-tools.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Nasıl yapılır: Çalışan bir işleme bağlanma](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z\(v\=vs.100\))
