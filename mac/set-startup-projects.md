---
title: Çoklu başlangıç projeleri ayarlama
description: Bu makalede, çalıştırma veya hata ayıklama için birden çok proje ayarlama açıklanmıştır.
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 11/09/2020
ms.topic: how-to
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: d219d8aca5c9af49ff8f4f0e0490f0bd794b56d9
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135805513"
---
# <a name="set-multiple-startup-projects"></a>Çoklu başlangıç projeleri ayarlama

Mac için Visual Studio, çözümde hata ayıklarken veya çözümde hata ayıklarken birden fazla projenin başlat gerektiğini belirtmenize olanak sağlar.

## <a name="to-set-multiple-startup-projects"></a>Birden çok başlangıç projesi ayarlamak için

1. Çözüm Penceresinde çözümü (üst düğüm) seçin.

2. Çözüm düğümüne sağ tıklayın ve Başlangıç Projelerini **Ayarla'yı seçin:**

   ![Başlangıç Projelerini Ayarlama seçeneğini belirleyin](media/startup-proj-ctx-menu.png)

3. Çözüm **Çalıştırma Yapılandırması Oluştur** iletişim kutusu açılır. Bu iletişim kutusu, çözümünüz için Çözüm Çalıştırma Yapılandırması adlı yeni bir oluşturmanızı sağlar. Istediğiniz adı kullanabilirsiniz. Varsayılan ad: `Multiple Projects` .

   ![Çözüm Çalıştırma Yapılandırması Oluştur iletişim kutusu](media/create-sln-run-config.png)

4. Çalıştırma **Yapılandırması Oluştur'a seçin.** Çözüm **Seçenekleri iletişim** kutusu yeni Çözüm Çalıştırma Yapılandırması seçili olarak açılır:

   ![Çözüm Seçenekleri iletişim kutusu](media/sln-options-run-config-multi-projects.png)

5. Uygulamanıza hata ayıklarken veya bu projelerden uygulamalarınızı çalıştırarak başlatmak Mac için Visual Studio:

   ![Seçili projelerin yer alan Çözüm Seçenekleri iletişim kutusu](media/sln-options-run-config-multi-projects-configured.png)

6. **Tamam**’ı seçin. Yeni Çözüm Çalıştırma Yapılandırması etkin çalıştırma yapılandırması olarak ayarlanır:

   ![Hata ayıklama veya çalıştırma için birden çok proje yapılandırılan çözüm](media/startup-project-configured.png)

   Şimdi iki proje başlatacak şekilde yapılandırıldı. Bu, Çözüm Penceresinde kalın görünen her iki **projeyle** de gösterilir. Araç çubuğunda, yeni çalıştırma yapılandırması geçerli Çözüm Çalıştırma Yapılandırması olarak ayarlanır.

## <a name="next-steps"></a>Sonraki adımlar

- [Derleme ve derleme Mac için Visual Studio](compiling-and-building.md)
- [Yapı yapılandırmalarını anlama](configurations.md)
