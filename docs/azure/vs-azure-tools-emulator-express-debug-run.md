---
title: Emulator Azure Cloud Service 'i yerel olarak çalıştırma/hata ayıklama
ms.custom: SEO-VS-2020
description: yerel makinede bir bulut hizmetini çalıştırmak ve hata ayıklamak için Emulator Express kullanma
author: mikejo5000
manager: jmartens
ms.technology: vs-azure
ms.topic: how-to
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.openlocfilehash: be382d80aea5a8f44001dc453741a1685fb644bc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037479"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Emulator Express kullanarak Azure bulut hizmetini yerel makinede çalıştırma ve hatalarını ayıklama
Emulator Express kullanarak, bir bulut hizmetini yönetici olarak Visual Studio çalıştırmadan test edebilir ve hatalarını ayıklayabilirsiniz. bulut hizmetinizin gereksinimlerine bağlı olarak, proje ayarlarınızı Emulator Express veya tam öykünücü kullanacak şekilde ayarlayabilirsiniz. Tam öykünücü hakkında daha fazla bilgi için bkz. [işlem Emulator Azure uygulaması çalıştırma](/azure/storage/common/storage-use-emulator).

## <a name="using-emulator-express-in-visual-studio"></a>Visual Studio Emulator Express kullanma
azure SDK 2,3 veya sonraki sürümlerde bir azure projesi oluşturduğunuzda Emulator Express otomatik olarak kullanılır. Azure SDK 'sının önceki bir sürümüyle oluşturulmuş mevcut projeler için Emulator Express ' i seçmek için aşağıdaki adımları kullanın:

1. Visual Studio bir Azure bulut hizmeti projesi oluşturun veya açın.

1. Çözüm Gezgini, projeye sağ tıklayın ve bağlam menüsünden **Özellikler**' i seçin.

1. Projeler Özellikler sayfasında, **Web** sekmesini seçin.

    ![Azure bulut hizmeti projesi özellikleri](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. **yerel geliştirme sunucusu** altında **IIS Express seçeneğini kullan**' ı seçin.

1. **Emulator** altında **Emulator Express kullan**' ı seçin.

1. Emulator Express 'i başlatmak için komut isteminde aşağıdaki komutu çalıştırın:

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Emulator Hızlı sınırlamalar
aşağıdaki sorunlar Emulator Express 'in bilinen sınırlamalarıdır:

- Emulator Express IIS Web sunucusuyla uyumlu değil.
- Bulut hizmetiniz birden çok rol içerebilir, ancak her rol bir örnekle sınırlıdır.
- 1000 numaralı bağlantı noktası numaralarına erişemezsiniz. Normalde 1000 altında bir bağlantı noktası kullanan bir kimlik doğrulama sağlayıcısı kullanırsanız, bu değeri 1000 ' nin üzerindeki bir bağlantı noktası numarasıyla değiştirmeniz gerekebilir.
- Azure işlem Emulator uygulanan tüm sınırlamalar Emulator Express için de geçerlidir. Örneğin, dağıtım başına en fazla 50 rol örneğine sahip olabilirsiniz. azure işlem Emulator hakkında daha fazla bilgi için bkz. [işlem Emulator azure uygulaması çalıştırma](vs-azure-tools-performance-profiling-cloud-services.md).

## <a name="next-steps"></a>Sonraki adımlar
[Azure bulut hizmetlerinde hata ayıklama](vs-azure-tools-debugging-cloud-services-overview.md)
