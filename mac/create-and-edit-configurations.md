---
title: Derleme yapılandırması oluşturma ve bunları Düzenle
description: Bu makalede Mac için Visual Studio yapı yapılandırmalarının oluşturulması açıklanmaktadır
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: CC1B72D6-12FF-4CCC-A9D4-00F2DC14589F
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: eb3ceed624e3bbba67564bb8f7c359841c0e496d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85939178"
---
# <a name="creating-and-editing-build-configurations"></a>Derleme yapılandırması oluşturma ve bunları Düzenle

Yapı konfigürasyonları, farklı test ve dağıtım durumlarına karşı bir yapılandırma oluşturmanıza olanak sağlayan bir yapı üzerinde tam denetim sağlar. Tek tek projeler için veya çözüm genelinde derleme yapılandırması oluşturabilirsiniz.

Proje seçenekleri iletişim kutusunu kullanarak hem projeler hem de çözümler için yeni konfigürasyonlar oluşturabilir ve varolanları düzenleyebilirsiniz.

>[!NOTE]
>Bu konu Mac için Visual Studio için geçerlidir. Windows üzerinde Visual Studio için bkz. [nasıl yapılır: yapılandırma oluşturma ve düzenleme](/visualstudio/ide/how-to-create-and-edit-configurations).

## <a name="creating-a-project-build-configuration"></a>Proje Derleme yapılandırması oluşturma

Proje yapı yapılandırması oluşturmak için aşağıdaki adımları izleyin:

1. Proje düğümüne sağ tıklayın ve **Seçenekler**' i seçin. Proje seçenekleri iletişim kutusunu açmak için proje düğümüne çift tıklayabilirsiniz.

2. Proje seçenekleri iletişim kutusunda **> yapılandırma oluştur**' u seçin:

    ![Proje seçeneklerinde Yapılandırma Yöneticisi](media/create-and-edit-configurations-image2.png)

3. Yeni bir yapılandırma oluşturmak için **Ekle** ' yi seçin. Ayrıca, varolan yapılandırmaların herhangi birini kopyalayabilirsiniz.

Yapılandırmayı oluşturduktan sonra, yapılandırmanıza uygun özellikleri uyarlamak için proje seçeneklerinde **Build** bölümünü kullanabilirsiniz:

![Derleme seçeneklerini yapılandırma](media/create-and-edit-configurations-image3.png)

## <a name="creating-a-solution-build-configuration"></a>Çözüm derleme yapılandırması oluşturma

Bir çözüm yapı yapılandırması oluşturmak için aşağıdaki adımları izleyin:

1. Çözüm düğümüne sağ tıklayın ve **Seçenekler**' i seçin. Ayrıca çözüm düğümüne çift tıklayarak çözüm seçenekleri iletişim kutusunu getirebilirsiniz.

2. Çözüm seçenekleri iletişim kutusunda **derleme > yapılandırması**' nı seçin:

    ![Çözüm seçeneklerinde Yapılandırma Yöneticisi](media/create-and-edit-configurations-image1.png)

3. Yeni bir yapılandırma oluşturmak için **Ekle** ' yi seçin. Ayrıca, varolan yapılandırmaların herhangi birini kopyalayabilirsiniz.

Yapılandırmayı oluşturduktan sonra, yapılandırmanıza uygun özellikleri uyarlayabilmeniz için, projelerinizden her biri için proje seçenekleri iletişim kutusunun **derleme** bölümünü kullanabilirsiniz:

![Derleme seçeneklerini yapılandırma](media/create-and-edit-configurations-image3.png)

## <a name="renaming-a-build-configuration"></a>Derleme yapılandırmasını yeniden adlandırma

Bir yapılandırmayı yeniden adlandırmak için, proje veya çözüm seçeneklerinde **> yapılandırmalar** ' a giderek bu yapılandırmayı yapılandırma listesinden seçin:

![yapılandırma listesi](media/create-and-edit-configurations-image4.png)

**Yeniden Adlandır** düğmesini seçin.

![Yeniden Adlandır iletişim kutusu](media/create-and-edit-configurations-image5.png)

Onaylamak için **Tamam** ' ı tıklatın.

## <a name="related-video"></a>İlgili video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Launch-Multiple-Projects/player]

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme yapılandırması oluşturma ve düzenleme (Windows üzerinde Visual Studio)](/visualstudio/ide/how-to-create-and-edit-configurations)