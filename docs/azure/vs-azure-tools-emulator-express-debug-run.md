---
title: Yerel kutuda Azure Cloud Service 'i çalıştırmak/hata ayıklamak için öykünücü Express
description: Öykünücü Express kullanarak yerel bir makinede bir bulut hizmetini çalıştırma ve hata ayıklama
author: mikejo5000
manager: jillfra
ms.assetid: 73108f98-a552-4817-b7a1-551367b71906
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.openlocfilehash: 2c9c4470d51718f5c7d4fa3f903fdcc063aa8d80
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911825"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Emulator Express kullanarak Azure bulut hizmetini yerel makinede çalıştırma ve hatalarını ayıklama
Öykünücü Express 'i kullanarak, Visual Studio 'Yu yönetici olarak çalıştırmadan bir bulut hizmetini test edebilir ve hatalarını ayıklayabilirsiniz. Bulut hizmetinizin gereksinimlerine bağlı olarak, proje ayarlarınızı öykünücü Express ya da tam öykünücü kullanacak şekilde ayarlayabilirsiniz. Tam öykünücü hakkında daha fazla bilgi için bkz. [Işlem öykünücüsünde Azure uygulaması çalıştırma](/azure/storage/common/storage-use-emulator).

## <a name="using-emulator-express-in-visual-studio"></a>Visual Studio 'da öykünücü Express 'ı kullanma
Azure SDK 2,3 veya sonraki sürümlerde bir Azure projesi oluşturduğunuzda, öykünücü Express otomatik olarak kullanılır. Azure SDK 'sının önceki bir sürümüyle oluşturulmuş mevcut projeler için, öykünücü Express ' i seçmek için aşağıdaki adımları kullanın:

1. Visual Studio 'da bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini**, projeye sağ tıklayın ve bağlam menüsünden **Özellikler**' i seçin.

1. Projeler Özellikler sayfasında, **Web** sekmesini seçin.

    ![Azure bulut hizmeti projesi özellikleri](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. **Yerel geliştirme sunucusu**altında **IIS Express seçeneğini kullan**' ı seçin.

1. **Öykünücü**bölümünde **öykünücü hızlı kullan**' ı seçin.

1. Öykünücü Express 'i başlatmak için komut isteminde aşağıdaki komutu çalıştırın:

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Öykünücü hızlı sınırlamaları
Aşağıdaki sorunlar öykünücü Express 'in bilinen sınırlamalarıdır:

- Öykünücü Express IIS Web sunucusuyla uyumlu değil.
- Bulut hizmetiniz birden çok rol içerebilir, ancak her rol bir örnekle sınırlıdır.
- 1000 numaralı bağlantı noktası numaralarına erişemezsiniz. Normalde 1000 altında bir bağlantı noktası kullanan bir kimlik doğrulama sağlayıcısı kullanırsanız, bu değeri 1000 ' nin üzerindeki bir bağlantı noktası numarasıyla değiştirmeniz gerekebilir.
- Azure Işlem öykünücüsü için uygulanan sınırlamalar, öykünücü Express için de geçerlidir. Örneğin, dağıtım başına en fazla 50 rol örneğine sahip olabilirsiniz. Azure Işlem öykünücüsü hakkında daha fazla bilgi için bkz. [Işlem öykünücüsünde Azure uygulaması çalıştırma](vs-azure-tools-performance-profiling-cloud-services.md).

## <a name="next-steps"></a>Sonraki adımlar
[Azure bulut hizmetlerinde hata ayıklama](vs-azure-tools-debugging-cloud-services-overview.md)
