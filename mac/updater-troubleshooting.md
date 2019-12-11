---
title: Güncelleştirici, bilgileri alırken hatalara sahip
description: "' Güncelleştirme bilgilerini alma hatası ' hatasını gördüğünüzde nasıl düzeltileceğini gösteren yönergeler. Mac için Visual Studio 2019"
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: b25285ff3060734ee18085d7a9e89cd0d0c43439
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984409"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Sorun giderme: Güncelleştirici bilgileri alırken hatalara sahip

Nadir bir gün içinde, [Mac için Visual Studio güncelleştirmeyi](update.md)denediğinizde "güncelleştirme bilgileri alınırken hata oluştu" hata iletisini görebilirsiniz. Bu durumda, çözümü onarmak için aşağıdaki adımları deneyin:

- İnternet bağlantınızı denetleyin. Bu hatanın en yaygın nedeni bağlantıda yer açdır.
  - Bir bileşen indirilemezse, indirmeyi yeniden denemek için bileşen adının yanındaki yeniden dene düğmesine tıklayabilirsiniz.
- IDE 'yi yeniden başlatın.
- Bu hata iletisini görmeye devam ederseniz, **. dmg** hala makinenizde ise yükleyiciyi kullanarak güncelleştirmeyi deneyebilir ya da [VisualStudio.com](https://visualstudio.microsoft.com/vs/mac/) adresinden indirebilirsiniz.
  - Yükleyici, makinenizde yüklü olan tüm bileşenleri güncelleştirecek.
  - Yükleyiciyi yeniden çalıştırarak, daha önce yüklemediyseniz eksik olan bileşenleri de yükleyebilirsiniz.
- Ayrıca, `~/Library/Caches/VisualStudio/7.0/TempDownload/index.xml`konumunda bulunan dosyayı silerek önbelleğe alınmış indirilerinizi temizlemeyi de deneyebilirsiniz.
