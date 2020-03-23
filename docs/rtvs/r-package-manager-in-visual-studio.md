---
title: R için paket yöneticisi
description: Visual Studio'da R paket yöneticisinin nasıl kullanılacağı, R paketlerini yüklemek ve yöneticilik yapmak.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: d35bfd45e862912ff78ae600eed01ce8dc002493
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62998874"
---
# <a name="package-manager"></a>Paket yöneticisi

R Tools for Visual Studio (RTVS) paket yöneticisi, R paketlerini yönetmek için kullanılan bir ui'dir. Açmak için **R Tools** > **Windows** > **Paketleri'ni** seçin veya **Ctrl**+**7**tuşuna basın.

Paket yöneticisinin üç sekmesi vardır. Her sekme, paketin sürümü, açıklaması, lisansı, yükleme konumu ve diğer ilgili bilgilere bağlantılar da dahil olmak üzere, solda ilgili paketlerin bir listesini ve sağda seçili paket için belirli ayrıntıları görüntüler. Sağ üstteki arama kutusu listeyi filtrelemenizi sağlar.

> [!Tip]
> Sekmeler arasında geçiş yaptığınızda arama kutusundaki terim geçerli liğini korur.

- **Kullanılabilir,** yüklemek için paketlere göz atmanızı sağlar. Paket zaten yüklüyse, sağdaki **Yükle** düğmesi **Kaldır**'a dönüşür.

    ![Visual Studio paket yöneticisi için R Tools'ta kullanılabilir paketler sekmesi](media/package-manager-available.png)

- **Yüklenen** tüm yüklü ve yüklenen paketleri gösterir. Paketin yanındaki yeşil nokta, paketin R oturumuna yüklendiğini gösterir. Sol listedeki kırmızı X simgesi veya sağdaki **Kaldır** düğmesi paketi kaldırmak için kullanılabilir. Yüklü bir paketin daha yeni bir sürümü varsa, paketin sağındaki mavi yukarı ok güncelleştirmeyi gerçekleştirir.

    ![Visual Studio paket yöneticisi için R Tools'a yüklenen paketler sekmesi](media/package-manager-installed.png)

- **Yüklenen** paketler yalnızca R oturumuna yüklenen ve tümü yeşil bir noktayla görünen paketleri görüntüler. Paketleri buradan da kaldırabilir ve güncelleyebilirsiniz.

    ![Visual Studio paket yöneticisi için R Tools'ta yüklenen paketler sekmesi](media/package-manager-loaded.png)

## <a name="package-locations"></a>Paket konumları

Paketler aşağıdaki konumlara yüklenir:

- RTVS ile birlikte verilen çekirdek paketler *C:\Program Files\Microsoft\R Client\R_SERVER\library'de* yüklenir
- Ek paketler *%userprofile%\\Documents\R\win-library\3.3'e* yüklenir
