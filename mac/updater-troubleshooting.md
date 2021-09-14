---
title: Güncelleştirici, bilgileri alırken hatalarla karşılaşıyor
description: "'Güncelleştirme bilgileri alınırken hata oluştu' hatasını gördüğünüzde düzeltme yönergeleri. Mac için Visual Studio 2019'da"
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 2ccef07a2889f66df3e7f217ea292b61ffc0008f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725956"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Sorun Giderme: Güncelleştirici, bilgileri alırken hatalarla karşılaşıyor

Nadiren de olsa, 'i güncelleştirmeye çalışsanız "Güncelleştirme bilgileri alınırken hata oluştu" hata [iletisini Mac için Visual Studio.](update.md) Bu durumda, düzeltmek için aşağıdaki adımları deneyin:

- İnternet bağlantınızı kontrol edin. Bağlantıda bir düşüş, bu hatanın en yaygın nedenidir.
  - Bir bileşen indiremezse, bileşenin adının yanındaki yeniden dene düğmesine tıklayarak indirmeyi yeniden indirebilirsiniz.
- IDE'i yeniden başlatın.
- Bu hata iletisini görmeye devam edersiniz, **.dmg** hala makineniz üzerinde ise Yükleyiciyi kullanarak güncelleştirmeyi deneyebilir veya bu iletiyi yükleyiciden [visualstudio.com](https://visualstudio.microsoft.com/vs/mac/)
  - Yükleyici, makinenize yüklenmiş bileşenleri güncelleştirecek.
  - Yükleyiciyi yeniden çalıştırarak, daha önce yüklememiş olduğu tüm eksik bileşenleri de yükleyebilirsiniz.
- Ayrıca, 'de bulunan dosyayı silerek önbelleğe alınmış indirmelerinizi temizlemeyi de denemeniz `~/Library/Caches/VisualStudio/8.0/TempDownload/index.xml` gerekir.
- Mac için Visual Studio'nin eski bir sürümüyle çalışıyorsanız dizinin altında başka sürüm numaraları da `VisualStudio` olabilir. Bu `index.xml` yollarda dosyayı da silin.
