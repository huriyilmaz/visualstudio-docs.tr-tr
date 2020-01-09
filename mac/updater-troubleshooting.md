---
title: Güncelleştirici, bilgileri alırken hatalara sahip
description: "' Güncelleştirme bilgilerini alma hatası ' hatasını gördüğünüzde nasıl düzeltileceğini gösteren yönergeler. Mac için Visual Studio 2019"
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 2ccef07a2889f66df3e7f217ea292b61ffc0008f
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75405474"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Sorun giderme: Güncelleştirici bilgileri alırken hatalara sahip

Nadir bir gün içinde, [Mac için Visual Studio güncelleştirmeyi](update.md)denediğinizde "güncelleştirme bilgileri alınırken hata oluştu" hata iletisini görebilirsiniz. Bu durumda, çözümü onarmak için aşağıdaki adımları deneyin:

- İnternet bağlantınızı denetleyin. Bu hatanın en yaygın nedeni bağlantıda yer açdır.
  - Bir bileşen indirilemezse, indirmeyi yeniden denemek için bileşen adının yanındaki yeniden dene düğmesine tıklayabilirsiniz.
- IDE 'yi yeniden başlatın.
- Bu hata iletisini görmeye devam ederseniz, **. dmg** hala makinenizde ise yükleyiciyi kullanarak güncelleştirmeyi deneyebilir ya da [VisualStudio.com](https://visualstudio.microsoft.com/vs/mac/) adresinden indirebilirsiniz.
  - Yükleyici, makinenizde yüklü olan tüm bileşenleri güncelleştirecek.
  - Yükleyiciyi yeniden çalıştırarak, daha önce yüklemediyseniz eksik olan bileşenleri de yükleyebilirsiniz.
- Ayrıca, `~/Library/Caches/VisualStudio/8.0/TempDownload/index.xml`konumunda bulunan dosyayı silerek önbelleğe alınmış indirilerinizi temizlemeyi de deneyebilirsiniz.
- Mac için Visual Studio daha eski bir sürümüyle çalışıyorsanız, `VisualStudio` dizin altında başka sürüm numaralarına sahip olabilirsiniz. Bu yollardaki `index.xml` dosyasını da silin.
