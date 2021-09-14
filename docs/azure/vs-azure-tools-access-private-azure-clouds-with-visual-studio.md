---
title: Özel Azure bulutlara erişme
description: Visual Studio kullanarak özel bulut kaynaklarına erişmeyi Visual Studio.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: 04ce2657fa5b7e5aa8e829c161a1739d23920ab9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633230"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>Visual Studio ile özel Azure bulutlara erişme

Varsayılan olarak, Visual Studio Azure bulut REST uç noktalarını destekler. Bu makalede, özel bulut sertifikanızı kullanarak buluttan özel buluta erişmeyi ve bu bulutla etkileşime geçmeyi Visual Studio.

1. Özel Azure portal için yayımlama ayarları dosyanızı indirin veya yayımlama ayarları dosyası için yöneticinize başvurun. (Dosya uzantısına `.publishsettings` sahip.)

1. Bu Visual Studio **Sunucu Gezgini** Azure düğümüne sağ tıklayın ve **Abonelikleri** Yönet ve **Filtrele'yi seçin.**

    ![Abonelikleri yönet komutu](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790778.png)

1. Abonelikleri **Microsoft Azure iletişim kutusunda** Sertifikalar sekmesini ve ardından **İçeri** Aktar'ı **seçin.**

    ![Azure sertifikalarını içeri aktarma](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790779.png)

1. Abonelikleri **İçeri Aktar iletişim Microsoft Azure Gözat'ı** **seçin.**

    ![Abonelikleri İçeri Aktar iletişim kutusundaki Microsoft Azure düğmesi](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/browse-button.png)

1. Aç **iletişim** kutusunda publish-settings dosyasını kaydeden dizine göz atarak dosyayı seçin ve ardından Aç'ı **seçin.**

    ![Yayımlama ayarları dosyasını seçin](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/select-publish-settings-file.png)

1. Abonelikleri İçeri Aktar **iletişim Microsoft Azure İçeri** Aktar'ı **seçin.**

    ![Yayımlama ayarları dosyasını içeri aktarma](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790780.png)

    Sertifikalar yayımlama ayarları dosyasından Visual Studio içine aktarılır ve artık özel bulut kaynaklarıyla etkileşim kurabilirsiniz.
