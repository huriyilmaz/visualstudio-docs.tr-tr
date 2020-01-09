---
title: Çoklu başlangıç projeleri ayarlama
description: Bu makalede, birden çok projenin çalıştırıldığında veya hata ayıklamada başlatılacak şekilde nasıl ayarlanacağı açıklanır.
author: sayedihashimi
ms.author: sayedha
ms.date: 12/13/2019
ms.topic: conceptual
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: 46e6447e07d2ee8439fcd86f5d1519beaa1e4609
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75406690"
---
# <a name="set-multiple-startup-projects"></a>Çoklu başlangıç projeleri ayarlama

Mac için Visual Studio, çözümünüzü hata ayıkladığınızda veya çalıştırdığınızda birden çok projenin başlatılmasını belirtmenizi sağlar.

## <a name="to-set-multiple-startup-projects"></a>Birden çok başlangıç projesi ayarlamak için

1. Çözüm Bölmesi, çözümü (en üstteki düğüm) seçin.

2. Çözüm düğümüne sağ tıklayın ve ardından **Başlangıç projelerini ayarla**' yı seçin:

   ![Başlangıç projelerini ayarla ' yı seçin](media/startup-proj-ctx-menu.png)

3. **Çözüm çalıştırma yapılandırması oluştur** iletişim kutusu açılır. Bu iletişim kutusu, çözümünüz için yeni bir adlandırılmış çözüm çalıştırma yapılandırması oluşturmanıza olanak sağlar. Dilediğiniz adı kullanabilirsiniz. Varsayılan ad `Multiple Projects`.

   ![Çözüm çalıştırma yapılandırması oluştur iletişim kutusu](media/create-sln-run-config.png)

4. **Çalıştırma yapılandırması oluştur**' u seçin. **Çözüm seçenekleri** iletişim kutusu yeni çözüm Çalıştır Yapılandırması seçiliyken açılır:

   ![Çözüm seçenekleri iletişim kutusu](media/sln-options-run-config-multi-projects.png)

5. Mac için Visual Studio ' den uygulamanızı hata ayıkladığınızda veya çalıştırırken başlatmak istediğiniz projeleri seçin:

   ![Seçili projeler içeren çözüm seçenekleri iletişim kutusu](media/sln-options-run-config-multi-projects-configured.png)

6. Seçin **Tamam**. Yeni çözüm çalıştırma yapılandırması etkin çalıştırma yapılandırması olarak ayarlanır:

   ![Hata ayıklamada veya çalıştırmada başlatılacak şekilde yapılandırılmış birden çok projeyle sahip çözüm](media/startup-project-configured.png)

   Her iki projenin de Çözüm Bölmesi **kalın** olduğu için, iki projenin de başlatılacak şekilde yapılandırıldığını görebilirsiniz. Araç çubuğunda, yeni çalıştırma yapılandırması geçerli çözüm çalıştırma yapılandırması olarak ayarlanır.

## <a name="next-steps"></a>Sonraki adımlar

- [Mac için Visual Studio derleme ve oluşturma](compiling-and-building.md)
- [Yapı yapılandırmalarını anlama](configurations.md)
