---
title: R için paket yöneticisi
description: R paketlerini yüklemek ve Visual Studio R paket yöneticisini kullanma.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 8f89f7750cdaddcb2d12fe6384042cff2dcc2ce0
ms.sourcegitcommit: dcecc0ed37b5e976b5dc83c5128ba5ecc8bc04b1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2022
ms.locfileid: "135750810"
---
# <a name="package-manager"></a>Paket yöneticisi

Visual Studio için R Araçları (RTVS) paket yöneticisi, R paketlerini yönetmek için bir kullanıcı arabirimidir. Açmak için R Araçları'Windows'ni  >    >  **seçin** veya **Ctrl** + **7 tuşlarına basın.**

Paket yöneticisinin üç sekmesi vardır. Her sekme sol tarafta ilgili paketlerin listesini ve seçilen paketle ilgili ayrıntıları sağ tarafta görüntüler. Paketin sürümü, açıklaması, lisansı, yükleme konumu ve diğer ilgili bilgilerin bağlantıları da buna dahil olur. Sağ üstteki arama kutusu listeyi filtrelemenizi sağlar.

> [!Tip]
> Sekmeler arasında geçiş yapın ve arama kutusunda terimin etkisi devam ediyor.

- **Kullanılabilir,** yüklemek için paketlere göz atmanıza olanak sağlar. Paket zaten yüklüyse, sağ üstte **yer alan** Yükle düğmesi Kaldır olarak **değişir.**

    ![Visual Studio için R Araçları paket yöneticisinde kullanılabilir paketler sekmesi](media/package-manager-available.png)

- **Yüklü olan** tüm yüklü ve yüklü paketler gösterir. Paketin yanındaki yeşil nokta, paketin R oturumuna yükleniyor olduğunu gösterir. Paketi kaldırmak için sol listede yer  alan kırmızı X simgesi veya sağ tarafta bulunan Kaldır düğmesi kullanılabilir. Yüklü bir paketin daha yeni bir sürümü varsa, güncelleştirmeyi paketin sağ tarafından mavi yukarı ok gerçekleştirir.

    ![Visual Studio için R Araçları paket yöneticisinde yüklü paketler sekmesi](media/package-manager-installed.png)

- **Yüklendi,** yalnızca R oturumuna yüklenen paketleri görüntüler ve bunların hepsi yeşil noktayla görünür. Paketleri buradan da kaldırabilirsiniz ve güncelleştirebilirsiniz.

    ![Visual Studio için R Araçları paket yöneticisinde yüklü paketler sekmesi](media/package-manager-loaded.png)

## <a name="package-locations"></a>Paket konumları

Paketler aşağıdaki konumlara yüklenir:

- RTVS'ye dahil edilen çekirdek paketler *C:\Program Files\Microsoft\R Client\R_SERVER\library dizinine yüklenir*
- *%userprofile%\Documents\R\win-library\3.3* klasörüne ek paketler yüklenir
