---
title: Çoklu başlangıç projeleri ayarlama
description: Bu makalede, birden çok projenin çalıştırıldığında veya hata ayıklamada başlatılacak şekilde nasıl ayarlanacağı açıklanır.
author: sayedihashimi
ms.author: sayedha
ms.date: 02/21/2019
ms.topic: how-to
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: 1b015d9009dc813c50ef891a4a523ba497c254c2
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "121382238"
---
# <a name="set-multiple-startup-projects"></a>Çoklu başlangıç projeleri ayarlama

Mac için Visual Studio, çözümünüzü hata ayıkladığınızda veya çalıştırdığınızda birden çok projenin başlatılmasını belirtmenizi sağlar.

## <a name="to-set-multiple-startup-projects"></a>Birden çok başlangıç projesi ayarlamak için

1. Çözüm Bölmesi, çözümü (en üstteki düğüm) seçin.

2. Çözüm düğümüne sağ tıklayın ve ardından **Başlangıç projelerini ayarla**' yı seçin:

   ![Başlangıç Projelerini Ayarlama seçeneğini belirleyin](media/startup-proj-ctx-menu.png)

3. **Çözüm çalıştırma yapılandırması oluştur** iletişim kutusu açılır. Bu iletişim kutusu, çözümünüz için yeni bir adlandırılmış çözüm çalıştırma yapılandırması oluşturmanıza olanak sağlar. Dilediğiniz adı kullanabilirsiniz. Varsayılan ad `Multiple Projects` .

   ![Çözüm çalıştırma yapılandırması oluştur iletişim kutusu](media/create-sln-run-config.png)

4. **Çalıştırma yapılandırması oluştur**' u seçin. **Çözüm seçenekleri** iletişim kutusu yeni çözüm Çalıştır Yapılandırması seçiliyken açılır:

   ![Çözüm seçenekleri iletişim kutusu](media/sln-options-run-config-multi-projects.png)

5. Mac için Visual Studio ' den uygulamanızı hata ayıkladığınızda veya çalıştırırken başlatmak istediğiniz projeleri seçin:

   ![Seçili projeler içeren çözüm seçenekleri iletişim kutusu](media/sln-options-run-config-multi-projects-configured.png)

6. **Tamam**’ı seçin. Yeni çözüm çalıştırma yapılandırması etkin çalıştırma yapılandırması olarak ayarlanır:

   ![Hata ayıklamada veya çalıştırmada başlatılacak şekilde yapılandırılmış birden çok projeyle sahip çözüm](media/startup-project-configured.png)

   İki projenin de başlamak üzere yapılandırıldığını görebilirsiniz çünkü her iki proje de Çözüm Bölmesi **kalın** . Araç çubuğunda, yeni çalıştırma yapılandırması geçerli çözüm çalıştırma yapılandırması olarak ayarlanır.

## <a name="next-steps"></a>Sonraki adımlar

- [Mac için Visual Studio derleme ve oluşturma](compiling-and-building.md)
- [Yapı yapılandırmalarını anlama](configurations.md)
