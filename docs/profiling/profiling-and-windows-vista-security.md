---
title: Vista güvenlik Windows profil oluşturma ve | Microsoft Docs
description: Kullanılabilir Kullanıcı Erişim İzinleri ayarlarına bağlı olarak, tek bir kullanıcı o bilgisayarda bir işlem profili oluşturmak için güvenlik iznine sahip olabilir.
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 381cffa54c1dc0446b3e0e2cbc9fa897643e5058
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060810"
---
# <a name="profiling-and-windows-vista-security"></a>Profil oluşturma ve Windows Vista güvenliği

Bir bilgisayar yöneticisinin kullanılabilir duruma yaptığı Kullanıcı Erişim İzinleri ayarlarına bağlı olarak, tek bir kullanıcının o bilgisayarda bir işlem profili oluşturmak için [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] güvenlik izni olabilir. Aşağıdaki örnekler kullanıcılar arasındaki olası farkları göstermektedir:

- Yönetici, sürücüyü ve hizmeti başlatıyorken bazı kullanıcılar gelişmiş profil oluşturma özelliklerine erişebilirsiniz.

- Etki alanı kullanıcıları yalnızca örnek profil oluşturma erişimine sahip olabilir.

- Bazı kullanıcılar diğer tüm kullanıcılar için profil oluşturma erişimini reddeder.

  Daha fazla bilgi için [VSPerfCmd'de YÖNETİCI seçeneklerine bakın.](../profiling/vsperfcmd.md)

## <a name="cross-session-profiling"></a>Oturumlar arası profil oluşturma

*Oturumlar arası profil oluşturma,* farklı bir kullanıcı oturumunda çalışan bir sürecin profilini oluşturma özelliğidir. Örneğin, çoğu hizmet oturum 0'da çalıştırı ve kullanıcılar doğrudan oturum 0'da çalıştıramayabilirsiniz. Performans Gezgini araç  çubuğundaki İşleme Ekle düğmesini veya VSPerfCmd komut satırı aracının seçeneğini kullanarak, farklı kullanıcı oturumlarında işlemlerin çoğunun profilini `/attach` ekleyebilirsiniz.

İşlemler arası profil oluşturma görünürlük seçeneklerini ayarerek kullanılabilir işlemlerin listesini görüntüebilirsiniz. Bu seçenekler İşleme ekle **penceresinde İşleme Ekle'yi** seçerek **görüntüleniyor:**

- **Tüm kullanıcıların işlemlerini gösterme**

  Bu seçenek seçili değilse, listede yalnızca geçerli kullanıcının sahip olduğu işlemler görüntülenir. Aksi takdirde, listede tüm kullanıcılardan işlemler görüntülenir.

- **Tüm oturumlarda işlemleri gösterme**

  Bu seçenek seçili değilse, listede geçerli oturumda işlemler görüntülenir. Aksi takdirde, listede tüm oturumlarda işlemler görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- ['a Genel Bakış](../profiling/overviews-performance-tools.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Nasıl olur: Çalışan bir işleme ekleme](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z\(v\=vs.100\))
