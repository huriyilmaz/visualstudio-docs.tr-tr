---
title: Çoklu başlangıç projeleri ayarlama
description: Bu makalede, birden çok proje yi çalıştırmaya veya hata ayıklamaya başlamak üzere nasıl ayarlanır.
author: sayedihashimi
ms.author: sayedha
ms.date: 12/13/2019
ms.topic: conceptual
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: 46e6447e07d2ee8439fcd86f5d1519beaa1e4609
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75406690"
---
# <a name="set-multiple-startup-projects"></a>Çoklu başlangıç projeleri ayarlama

Mac için Visual Studio, hata ayıklama veya çözümünüzü çalıştırdığınızda birden fazla projenin başlatılması gerektiğini belirtmenizi sağlar.

## <a name="to-set-multiple-startup-projects"></a>Birden çok başlangıç projesi ayarlamak için

1. Çözüm Defteri'nde, çözümü (üst düğüm) seçin.

2. Çözüm düğümüne sağ tıklayın ve ardından **Başlangıç Projeleri Ayarla'yı**seçin:

   ![Başlangıç Projelerini Seç](media/startup-proj-ctx-menu.png)

3. **Çözüm Çalıştır Yapılandırması Oluştur** iletişim kutusu açılır. Bu iletişim kutusu, çözümünüz için yeni bir çözüm çalıştırma yapılandırması oluşturmanıza olanak tanır. İstediğin ismi kullanabilirsin. Varsayılan ad. `Multiple Projects`

   ![Çözüm Çalıştır Yapılandırması oluştur iletişim kutusu](media/create-sln-run-config.png)

4. **Çalıştır Yapılandırması Oluştur'u**seçin. **Çözüm Seçenekleri** iletişim kutusu seçilen yeni Çözüm Çalıştır Yapılandırması ile açılır:

   ![Çözüm Seçenekleri iletişim kutusu](media/sln-options-run-config-multi-projects.png)

5. Mac için Visual Studio'dan uygulamanızı hata ayıklarken veya çalıştırdığınızda başlatmak istediğiniz projeleri seçin:

   ![Seçili projelerle Çözüm Seçenekleri iletişim kutusu](media/sln-options-run-config-multi-projects-configured.png)

6. **Tamam'ı**seçin. Yeni Solution Run Yapılandırması etkin çalıştırma yapılandırması olarak ayarlanır:

   ![Hata ayıklamaya veya çalıştırmaya başlamak üzere yapılandırılan birden çok projeiçeren çözüm](media/startup-project-configured.png)

   Her iki proje de Çözüm Defteri'nde **kalın** olduğundan, iki projenin başlatılacak şekilde yapılandırıldığı görebilirsiniz. Araç çubuğunda, yeni çalıştır yapılandırması geçerli Çözüm Çalıştır Yapılandırması olarak ayarlanır.

## <a name="next-steps"></a>Sonraki adımlar

- [Mac için Visual Studio'da derleme ve oluşturma](compiling-and-building.md)
- [Yapı yapılandırmalarını anlama](configurations.md)
