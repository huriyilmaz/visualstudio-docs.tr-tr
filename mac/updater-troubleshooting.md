---
title: Güncelleştirici, bilgileri alırken hatalarla karşılaşıyor
description: "'Hata alma güncelleştirme bilgileri' hatasını gördüğünüzde nasıl düzeltileceklerine ilişkin yönergeler. Mac için Visual Studio 2019'da"
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 2ccef07a2889f66df3e7f217ea292b61ffc0008f
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75405474"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Sorun giderme: Updater'ın bilgi alma hataları var

Nadir durumlarda, [Mac için Visual Studio'yu güncelleştirmeye](update.md)çalıştığınızda görüntülenen hata iletisi "Hata alma güncelleştirme bilgileri" görebilirsiniz. Bu durumda, düzeltmek için aşağıdaki adımları deneyin:

- İnternet bağlantınızı kontrol edin. Bağlantıdaki bir düşüş, bu hatanın en yaygın nedenidir.
  - Bir bileşen karşıdan yükleme yapamazsa, indirmeyi yeniden denemek için bileşen adının yanındaki yeniden deneme düğmesini tıklatabilirsiniz.
- IDE'yi yeniden başlatın.
- Bu hata iletisini görmeye devam ederseniz, **.dmg** hala makinenizdeyse veya [visualstudio.com'dan](https://visualstudio.microsoft.com/vs/mac/) indirebilirsiniz.
  - Yükleyici, makinenizdeki yüklü bileşenleri güncelleştirecektir.
  - Yükleyiciyi yeniden çalıştırarak, daha önce yüklemediğiniz eksik bileşenleri de yükleyebilirsiniz.
- Önbelleğe alınmış indirmelerinizi de ' de `~/Library/Caches/VisualStudio/8.0/TempDownload/index.xml`bulunan dosyayı silerek temizlemeyi deneyebilirsiniz.
- Mac için Visual Studio'nun eski bir sürümüyle çalışıyorsanız, `VisualStudio` dizinin altında başka sürüm numaraları olabilir. Bu `index.xml` yollardaki dosyayı da silin.
