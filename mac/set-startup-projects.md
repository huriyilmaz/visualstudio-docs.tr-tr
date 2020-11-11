---
title: Çoklu başlangıç projeleri ayarlama
description: Bu makalede, birden çok projenin çalıştırıldığında veya hata ayıklamada başlatılacak şekilde nasıl ayarlanacağı açıklanır.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.topic: how-to
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: df1e088a5e2d0f65d8b72dad0895f1edb1740f1f
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493575"
---
# <a name="set-multiple-startup-projects"></a>Çoklu başlangıç projeleri ayarlama

Mac için Visual Studio, çözümünüzü hata ayıkladığınızda veya çalıştırdığınızda birden çok projenin başlatılmasını belirtmenizi sağlar.

## <a name="to-set-multiple-startup-projects"></a>Birden çok başlangıç projesi ayarlamak için

1. Çözüm penceresinde çözümü (üstteki düğüm) seçin.

2. Çözüm düğümüne sağ tıklayın ve ardından **Başlangıç projelerini ayarla** ' yı seçin:

   ![Başlangıç Projelerini Ayarlama seçeneğini belirleyin](media/startup-proj-ctx-menu.png)

3. **Çözüm çalıştırma yapılandırması oluştur** iletişim kutusu açılır. Bu iletişim kutusu, çözümünüz için yeni bir adlandırılmış çözüm çalıştırma yapılandırması oluşturmanıza olanak sağlar. Dilediğiniz adı kullanabilirsiniz. Varsayılan ad `Multiple Projects` .

   ![Çözüm çalıştırma yapılandırması oluştur iletişim kutusu](media/create-sln-run-config.png)

4. **Çalıştırma yapılandırması oluştur** ' u seçin. **Çözüm seçenekleri** iletişim kutusu yeni çözüm Çalıştır Yapılandırması seçiliyken açılır:

   ![Çözüm seçenekleri iletişim kutusu](media/sln-options-run-config-multi-projects.png)

5. Mac için Visual Studio ' den uygulamanızı hata ayıkladığınızda veya çalıştırırken başlatmak istediğiniz projeleri seçin:

   ![Seçili projeler içeren çözüm seçenekleri iletişim kutusu](media/sln-options-run-config-multi-projects-configured.png)

6. **Tamam** ’ı seçin. Yeni çözüm çalıştırma yapılandırması etkin çalıştırma yapılandırması olarak ayarlanır:

   ![Hata ayıklamada veya çalıştırmada başlatılacak şekilde yapılandırılmış birden çok projeyle sahip çözüm](media/startup-project-configured.png)

   Artık iki proje başlatılacak şekilde yapılandırılmıştır. Bu, çözüm penceresinde **kalın** görüntülenen her iki proje tarafından temsil edilir. Araç çubuğunda, yeni çalıştırma yapılandırması geçerli çözüm çalıştırma yapılandırması olarak ayarlanır.

## <a name="next-steps"></a>Sonraki adımlar

- [Mac için Visual Studio derleme ve oluşturma](compiling-and-building.md)
- [Yapı yapılandırmalarını anlama](configurations.md)
