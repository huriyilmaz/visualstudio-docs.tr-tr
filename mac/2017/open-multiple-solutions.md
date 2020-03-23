---
title: 'Nasıl kullanılır: Birden çok çözüm açın'
description: Mac için Visual Studio'da birden fazla çözümü nasıl açacağınızı ve uygulamanın birden fazla örneğini nasıl açacağınızı öğrenin.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/19/2018
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.custom: video
ms.openlocfilehash: 3568ab8dd68deb83d668c6e46f556516e29a81ae
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985006"
---
# <a name="open-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Mac için birden fazla çözüm veya Visual Studio örneği açın

Varsayılan olarak, Mac için Visual Studio da dahil olmak üzere Mac'teki tüm uygulamalar _tek örnek_ uygulamalardır. Bu, kullanmak istediğiniz uygulama zaten açıksa (dock simgesinin altındaki noktayla gösterilmiştir), simgeyi seçmek yeni bir simge yerine çalışan örneği yeniden açar. Uygulamanın ek örneklerine ihtiyaç duyarsanız, bir [sonraki bölümde](#open-a-second-instance-of-visual-studio-for-mac)açıklandığı gibi sistemi sizin için açmasını isteyebilirsiniz.

Ayrıca, bir çözüm açtığınızda, varsayılan davranış çözümü yeni bir çalışma alanında açmak ve geçerli çalışma alanını (gerekirse) kapatmaktır. [İkinci bir çözüm aç](#open-a-second-solution-inside-a-single-instance) bölümünde açıklandığı gibi, geçerli çalışma alanını açık tutarak bu varsayılan davranışı geçersiz kılabilirsiniz.

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Mac için Visual Studio'nun ikinci bir örneğini açın

Tümleşik geliştirme ortamının (IDE) ikinci bir örneğini açmak için **Terminal** uygulamasını açın ve aşağıdaki satırı girin:

```bash
open -n "/Applications/Visual Studio.app"
```

## <a name="open-a-second-solution-inside-a-single-instance"></a>Tek bir örnek içinde ikinci bir çözüm açma

İlk çözümünüzle birlikte ikinci bir çözüm açmak için aşağıdaki adımları kullanın:

1. İlk çözümünüz zaten açıkken **Dosya** > **Aç'ı**seçin.
2. Varolan çözümü bulmak için dosya sistemine göz atın.
3. **.sln** dosyasını seçin ve **Seçenekler'i**seçin:

    ![.sln dosyası ve Seçenekler vurgulanmış Olan Mac için Visual Studio ekran görüntüsü](media/open-multiple-solutions-image3.png)

4. Geçerli **çalışma alanını kapat** kutusunu temizle:

    ![Seçenekler iletişim kutusunun ekran görüntüsü, geçerli çalışma alanını kapat kutusu temizlenir](media/open-multiple-solutions-image1.png)

5. Çözüm Defteri'ndeki ikinci çözümü açmak için **Aç'ı** seçin.

Alternatif olarak, çözümü yakın zamanda açtıysanız, aşağıdaki adımları kullanabilirsiniz:

1. **Dosya** > **Son Çözümleri**gidin.

    ![Son Çözümler menüsünün ekran görüntüsü](media/open-multiple-solutions-image2.png)

1. **Ctrl** tuşunu basılı tutun ve çözümü seçin. Bu kombinasyon Çözüm Pedi'ndeki ikinci çözümü açar.

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Work-With-Multiple-Solutions/player]
