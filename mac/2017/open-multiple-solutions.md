---
title: 'Nasıllı: Birden çok çözüm açma'
description: Birden fazla çözümü Mac için Visual Studio açmayı ve uygulamanın birden fazla örneğini açmayı öğrenin.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/19/2018
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: ddf3d7fd3e07cdbbaad5c113c322de008562fae20b8785766d341db19b78ea1e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121422263"
---
# <a name="open-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Birden çok çözüm veya örnek Mac için Visual Studio

Varsayılan olarak, Mac'te Mac için Visual Studio uygulamalar tek _örnekli uygulamalardır._ Bu, kullanmak istediğiniz uygulama zaten açıksa (dock'ta simgenin altında bir noktayla gösterilir) simgeyi yeniden seçmek yeni bir örnek yerine çalışan örneği açar. Uygulamanın ek örneklerine ihtiyaç ediyorsanız, sonraki bölümde açıklandığı gibi sistemden uygulamayı sizin için açması [istenebilir.](#open-a-second-instance-of-visual-studio-for-mac)

Ayrıca, bir çözümü asanız varsayılan davranış çözümü yeni bir çalışma alanında açmak ve geçerli çalışma alanını kapatmaktır (gerekirse). İkinci bir çözüm aç bölümünde açıklandığı gibi geçerli çalışma alanını açık tutarak bu varsayılan [davranışı geçersiz kılabilirsiniz.](#open-a-second-solution-inside-a-single-instance)

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>İkinci bir örnek Mac için Visual Studio

Tümleşik geliştirme ortamının (IDE) ikinci bir örneğini açmak için **Terminal** uygulamasını açın ve aşağıdaki satırı girin:

```bash
open -n "/Applications/Visual Studio.app"
```

## <a name="open-a-second-solution-inside-a-single-instance"></a>Tek bir örneğin içinde ikinci bir çözüm açma

İlk çözümünüzle birlikte ikinci bir çözüm açmak için aşağıdaki adımları kullanın:

1. İlk çözümünüz zaten açıkken Dosya **Aç'ı**  >  **seçin.**
2. Mevcut çözümü bulmak için dosya sistemine göz atma.
3. **.sln dosyasını seçin** ve Seçenekler'i **seçin:**

    ![.sln Mac için Visual Studio ve Seçenekler vurgulanmış şekilde ekran görüntüsü](media/open-multiple-solutions-image3.png)

4. Geçerli çalışma **alanını kapat kutusunu** temizleyin:

    ![Seçenekler iletişim kutusunun ekran görüntüsü, Geçerli çalışma alanını kapat kutusu temiz](media/open-multiple-solutions-image1.png)

5. İkinci **çözümü** yeni çözümde açmak için Aç'ı Çözüm Bölmesi.

Alternatif olarak, çözümü yakın zamanda açtıysanız aşağıdaki adımları kullanabilirsiniz:

1. Dosya Son  >  **Çözümler'e gidin.**

    ![Son Çözümler menüsünün ekran görüntüsü](media/open-multiple-solutions-image2.png)

1. **Ctrl tuşunu basılı** tutun ve çözümü seçin. Bu birleşim, ikinci çözümü Çözüm Bölmesi.

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Work-With-Multiple-Solutions/player]
