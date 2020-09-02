---
title: R için Paket Yöneticisi
description: R paketlerini yüklemek ve Manager için Visual Studio 'da R Package Manager 'ı kullanma.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: d35bfd45e862912ff78ae600eed01ce8dc002493
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62998874"
---
# <a name="package-manager"></a>Paket yöneticisi

Visual Studio için R Araçları (RTVS) Paket Yöneticisi, R paketlerini yönetmek için bir kullanıcı arabirimi. Açmak için **R araçları**  >  **Windows**  >  **paketleri** ' ni seçin veya **CTRL** + **7**tuşlarına basın.

Paket yöneticisinin üç sekmesi vardır. Her sekme, sol taraftaki ilgili paketlerin bir listesini, paketin sürüm, açıklama, lisans, yüklemesi konumu ve diğer ilgili bilgilere bağlantılar da dahil olmak üzere sağda görüntüler. Sağ üst köşedeki arama kutusu listeyi filtrelemenizi sağlar.

> [!Tip]
> Sekmeler arasında geçiş yaparken arama kutusundaki terim etkin kalır.

- **Kullanılabilir** , yüklenecek paketlere gözatmanızı sağlar. Paket zaten yüklüyse, doğru değişiklikleri **kaldırmak**için **yükleme** düğmesi.

    ![Visual Studio için R Araçları paket yöneticisinde kullanılabilir paketler sekmesi](media/package-manager-available.png)

- **Yüklü** tüm yüklü ve yüklenmiş paketleri gösterir. Bir paketin yanındaki yeşil nokta, R oturumuna yüklendiğini belirtir. Sol taraftaki listede kırmızı X simgesi veya sağdaki **Kaldır** düğmesi, paketi kaldırmak için kullanılabilir. Yüklü bir paketin daha yeni bir sürümü kullanılabiliyorsa, paketin sağında bir mavi yukarı ok güncelleştirmeyi gerçekleştirir.

    ![Visual Studio için R Araçları paket yöneticisinde yüklü paketler sekmesi](media/package-manager-installed.png)

- **Yüklü** , hepsi yeşil noktayla görüntülenen R oturumuna yüklenmiş olan paketleri görüntüler. Ayrıca, paketleri buradan kaldırabilir ve güncelleştirebilirsiniz.

    ![Visual Studio için R Araçları Paket Yöneticisi 'nde paketler sekmesi yüklendi](media/package-manager-loaded.png)

## <a name="package-locations"></a>Paket konumları

Paketler aşağıdaki konumlara yüklenir:

- RTVS 'ye dahil edilen temel paketler, *C:\Program Files\Microsoft\R Client \ R_SERVER \library* ' de yüklüdür
- Ek paketler *%userprofile%\documents\r\win-library\3.3* ' e yüklenir
