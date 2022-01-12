---
title: 'Nasıl yapılır: birden çok çözüm açma'
description: Mac için Visual Studio ' de birden fazla çözüm açmayı ve uygulamanın birden fazla örneğini açmayı öğrenin.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: 59b5fbc07e2f19517e075cc9c4dde0b42c19f63c
ms.sourcegitcommit: fc874be3fe4637a23997b4ef2d99a2ee9a499581
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135516510"
---
# <a name="open-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>birden çok çözüm veya Mac için Visual Studio örnekleri açın

varsayılan olarak, Mac için Visual Studio dahil olmak üzere Mac üzerindeki tüm uygulamalar _tek örnekli_ uygulamalardır. Bu, kullanmak istediğiniz uygulama zaten açıksa (Dock 'taki simgenin altında bir nokta tarafından gösterilen), simgenin seçilmesi, yeni bir örnek yerine çalışan örneği açar. Uygulamanın ek örneklerine ihtiyacınız varsa, [sonraki bölümde](#open-a-second-instance-of-visual-studio-for-mac)açıklandığı gibi, sistemin sizin için onu açmasını isteyebilirsiniz.

Ayrıca, bir çözümü açtığınızda, varsayılan davranış çözümü yeni bir çalışma alanında açmak ve geçerli çalışma alanını (gerekliyse) kapatmak olur. [İkinci çözüm açma](#open-a-second-solution-inside-a-single-instance) bölümünde açıklandığı gibi geçerli çalışma alanını açık tutarak bu varsayılan davranışı geçersiz kılabilirsiniz.

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>ikinci bir Mac için Visual Studio örneğini açın

tümleşik geliştirme ortamının (ıde) ikinci bir örneğini açmak için yuva veya **uygulamalar** klasörünüzdeki Visual Studio simgesine sağ tıklayın ve **yeni örnek**' i seçin.

![sağ tıklatılan Visual Studio simgesindeki yeni örnek menü seçeneğinin ekran görüntüsü](media/open-new-instance.png)

## <a name="open-a-second-solution-inside-a-single-instance"></a>İkinci bir çözümü tek bir örnek içinde açın

İkinci bir çözümü ilk çözümünüzün yanında açmak için aşağıdaki adımları kullanın:

1. İlk çözümünüz zaten açık olduğunda **Dosya**  >  **Aç**' ı seçin.
2. Mevcut çözümü bulmak için dosya sistemine gidin.
3. **. Sln** dosyasını seçin ve **Seçenekler**' i seçin:

    ![. sln dosyası ve seçenekleri vurgulanmış Mac için Visual Studio ekran görüntüsü](media/open-multiple-solutions-image3.png)

4. **Geçerli çalışma alanını kapat** kutusunu temizleyin:

    ![Geçerli çalışma alanını kapat kutusunu işaretsiz Seçenekler iletişim kutusunun ekran görüntüsü](media/open-multiple-solutions-image1.png)

5. Çözüm penceresinde ikinci çözümü açmak için **Aç** ' ı seçin.

Alternatif olarak, çözümü son zamanlarda açtıysanız aşağıdaki adımları kullanabilirsiniz:

1.   >  **Son çözüm** dosyaları sayfasına gidin.

    ![Son çözümler menüsünün ekran görüntüsü](media/open-multiple-solutions-image2.png)

1. **CTRL** tuşunu basılı tutun ve çözümü seçin. Bu bileşim, çözüm penceresinde ikinci çözümü açar.

## <a name="related-video"></a>İlgili video

> [!Video https://docs.microsoft.com/shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Work-With-Multiple-Solutions/player]
