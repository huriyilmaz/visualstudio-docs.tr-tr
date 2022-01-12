---
title: Güncelleştirici, bilgileri alırken hatalarla karşılaşıyor
description: "' Güncelleştirme bilgilerini alma hatası ' hatasını gördüğünüzde nasıl düzeltileceğini gösteren yönergeler. Mac için Visual Studio 2019"
ms.topic: troubleshooting
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 2ea9e2bdbbde5691c20d7063732b042253690b22
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135805279"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Sorun Giderme: Güncelleştirici, bilgileri alırken hatalarla karşılaşıyor

nadir bir gün içinde, [Mac için Visual Studio güncelleştirmeyi](update.md)denediğinizde "güncelleştirme bilgileri alınırken hata oluştu" hata iletisini görebilirsiniz. Bu durumda, çözümü onarmak için aşağıdaki adımları deneyin:

- İnternet bağlantınızı kontrol edin. Bu hatanın en yaygın nedeni bağlantıda yer açdır.
  - Bir bileşen indirilemezse, indirmeyi yeniden denemek için bileşen adının yanındaki yeniden dene düğmesine tıklayabilirsiniz.
- IDE 'yi yeniden başlatın.
- Bu hata iletisini görmeye devam ederseniz, **. dmg** hala makinenizde ise yükleyiciyi kullanarak güncelleştirmeyi deneyebilir ya da [VisualStudio.com](https://visualstudio.microsoft.com/vs/mac/) adresinden indirebilirsiniz.
  - Yükleyici, makinenizde yüklü olan tüm bileşenleri güncelleştirecek.
  - Yükleyiciyi yeniden çalıştırarak, daha önce yüklemediyseniz eksik olan bileşenleri de yükleyebilirsiniz.
- Ayrıca, konumunda bulunan dosyayı silerek önbelleğe alınmış indirilerinizi temizlemeyi deneyebilirsiniz `~/Library/Caches/VisualStudio/8.0/TempDownload/index.xml` .
- Mac için Visual Studio eski bir sürümüyle çalışıyorsanız, dizin altında başka sürüm numaralarına sahip olabilirsiniz `VisualStudio` . `index.xml`Bu yollardaki dosyayı da silin.
