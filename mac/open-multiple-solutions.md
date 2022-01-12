---
title: 'Nasıllı: Birden çok çözüm açma'
description: Birden fazla çözümü Mac için Visual Studio açmayı ve uygulamanın birden fazla örneğini açmayı öğrenin.
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 11/09/2020
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: d6458340df167a45a088e5975627832e1c9ccdb8
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135805539"
---
# <a name="open-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Birden çok çözüm veya örnek Mac için Visual Studio

Varsayılan olarak, Mac'te Mac için Visual Studio uygulamalar tek _örnekli uygulamalardır._ Bu, kullanmak istediğiniz uygulama zaten açıksa (dock'ta simgenin altında bir noktayla gösterilir) simgeyi yeniden seçmek yeni bir örnek yerine çalışan örneği açar. Uygulamanın ek örneklerine ihtiyaç ediyorsanız, sonraki bölümde açıklandığı gibi sistemden uygulamayı sizin için açması [istenebilir.](#open-a-second-instance-of-visual-studio-for-mac)

Ayrıca, bir çözümü asanız varsayılan davranış çözümü yeni bir çalışma alanında açmak ve geçerli çalışma alanını kapatmaktır (gerekirse). İkinci bir çözüm aç bölümünde açıklandığı gibi geçerli çalışma alanını açık tutarak bu varsayılan [davranışı geçersiz kılabilirsiniz.](#open-a-second-solution-inside-a-single-instance)

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>dosyanın ikinci bir örneğini Mac için Visual Studio

Tümleşik geliştirme ortamının (IDE) ikinci bir örneğini açmak için, dock veya **Applications** klasörünüzdeki Visual Studio simgesine sağ tıklayın ve Yeni Örnek'i **seçin.**

![Sağ tık tıklama simgesinde Yeni Örnek menü seçeneğinin Visual Studio görüntüsü](media/open-new-instance.png)

## <a name="open-a-second-solution-inside-a-single-instance"></a>Tek bir örneğin içinde ikinci bir çözüm açma

İlk çözümünüzle birlikte ikinci bir çözüm açmak için aşağıdaki adımları kullanın:

1. İlk çözümünüz zaten açıkken Dosya **Aç'ı**  >  **seçin.**
2. Mevcut çözümü bulmak için dosya sistemine göz atma.
3. **.sln dosyasını seçin** ve Seçenekler'i **seçin:**

    ![.sln Mac için Visual Studio ve Seçenekler vurgulanmış şekilde ekran görüntüsü](media/open-multiple-solutions-image3.png)

4. Geçerli çalışma **alanını kapat kutusunu** temizleyin:

    ![Seçenekler iletişim kutusunun ekran görüntüsü, Geçerli çalışma alanını kapat kutusu temiz](media/open-multiple-solutions-image1.png)

5. Çözüm **Penceresinde** ikinci çözümü açmak için Aç'ı seçin.

Alternatif olarak, çözümü yakın zamanda açtıysanız aşağıdaki adımları kullanabilirsiniz:

1. Dosya Son  >  **Çözümler'e gidin.**

    ![Son Çözümler menüsünün ekran görüntüsü](media/open-multiple-solutions-image2.png)

1. **Ctrl tuşunu basılı** tutun ve çözümü seçin. Bu birleşim, çözüm penceresinde ikinci çözümü açar.

## <a name="related-video"></a>İlgili Video

> [!Video https://docs.microsoft.com/shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Work-With-Multiple-Solutions/player]
