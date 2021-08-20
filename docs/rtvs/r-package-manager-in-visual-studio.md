---
title: R için Paket Yöneticisi
description: r paketlerini yüklemek için Visual Studio 'de r package manager 'ı kullanma.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 70423ab665c9fe07d41ad7c8fe9a0653909d440a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060641"
---
# <a name="package-manager"></a>Paket yöneticisi

Visual Studio için R Araçları (rtvs) paket yöneticisi, R paketlerini yönetmek için bir kullanıcı arabirimi. açmak için **R araçları**  >  **Windows**  >  **paketler** ' i seçin veya **Ctrl** + **+ 7** tuşlarına basın.

Paket yöneticisinin üç sekmesi vardır. Her sekme, sol taraftaki ilgili paketlerin bir listesini, paketin sürüm, açıklama, lisans, yüklemesi konumu ve diğer ilgili bilgilere bağlantılar da dahil olmak üzere sağda görüntüler. Sağ üst köşedeki arama kutusu listeyi filtrelemenizi sağlar.

> [!Tip]
> Sekmeler arasında geçiş yaparken arama kutusundaki terim etkin kalır.

- **Kullanılabilir** , yüklenecek paketlere gözatmanızı sağlar. Paket zaten yüklüyse, doğru değişiklikleri **kaldırmak** için **yükleme** düğmesi.

    ![Visual Studio için R Araçları paket yöneticisinde kullanılabilir paketler sekmesi](media/package-manager-available.png)

- **Yüklü** tüm yüklü ve yüklenmiş paketleri gösterir. Bir paketin yanındaki yeşil nokta, R oturumuna yüklendiğini belirtir. Sol taraftaki listede kırmızı X simgesi veya sağdaki **Kaldır** düğmesi, paketi kaldırmak için kullanılabilir. Yüklü bir paketin daha yeni bir sürümü kullanılabiliyorsa, paketin sağında bir mavi yukarı ok güncelleştirmeyi gerçekleştirir.

    ![Visual Studio için R Araçları paket yöneticisinde yüklü paketler sekmesi](media/package-manager-installed.png)

- **Yüklü** , hepsi yeşil noktayla görüntülenen R oturumuna yüklenmiş olan paketleri görüntüler. Ayrıca, paketleri buradan kaldırabilir ve güncelleştirebilirsiniz.

    ![Visual Studio için R Araçları paket yöneticisi 'nde paketler sekmesi yüklendi](media/package-manager-loaded.png)

## <a name="package-locations"></a>Paket konumları

Paketler aşağıdaki konumlara yüklenir:

- RTVS 'ye dahil edilen temel paketler, *C:\Program Files\Microsoft\R Client \ R_SERVER \library* ' de yüklüdür
- Ek paketler *%userprofile%\documents\r\win-library\3.3* ' e yüklenir
