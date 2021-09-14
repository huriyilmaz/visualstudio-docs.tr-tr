---
title: Emulator Azure bulut hizmetini yerel olarak çalıştırmak/hata ayıklamak için Express
ms.custom: SEO-VS-2020
description: Yerel Emulator bulut hizmetini çalıştırmak ve hata ayıklamak için Emulator Express kullanma
author: mikejo5000
manager: jmartens
ms.technology: vs-azure
ms.topic: how-to
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.openlocfilehash: be382d80aea5a8f44001dc453741a1685fb644bc
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633137"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Emulator Express kullanarak Azure bulut hizmetini yerel makinede çalıştırma ve hatalarını ayıklama
Emulator Express kullanarak bir bulut hizmetini yönetici olarak çalıştırmadan test Visual Studio hataları ayıkabilirsiniz. Bulut hizmetinizin gereksinimlerine bağlı olarak proje ayarlarınızı Emulator Express veya tam öykünücü olarak kullanabilirsiniz. Tam öykünücü hakkında daha fazla bilgi için [bkz. İşlem](/azure/storage/common/storage-use-emulator)ve Emulator.

## <a name="using-emulator-express-in-visual-studio"></a>Emulator Express'i Visual Studio
Azure SDK 2.3 veya sonraki bir sürümüyle bir Azure projesi 2.3 Emulator Express otomatik olarak kullanılır. Azure SDK'nın önceki bir sürümüyle oluşturulmuş mevcut projeler için, Azure Express'i seçmek için Emulator kullanın:

1. Azure bulut hizmeti projesi oluşturma veya açma Visual Studio.

1. Bu Çözüm Gezgini projeye sağ tıklayın ve bağlam menüsünden Özellikler'i **seçin.**

1. Proje özellikleri sayfalarında **Web** sekmesini seçin.

    ![Azure bulut hizmeti projesinin özellikleri](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. Yerel **Geliştirme Sunucusu altında,** Kaynak **kullan seçeneğini IIS Express seçin.**

1. Altında **Emulator** **Express'i kullan'Emulator seçin.**

1. Emulator Express'i başlatmak için komut isteminde aşağıdaki komutu çalıştırın:

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Emulator Hızlı sınırlamalar
Aşağıdaki sorunlar, Express'in bilinen Emulator dır:

- Emulator Express, IIS Web Sunucusu ile uyumlu değildir.
- Bulut hizmetiniz birden çok rol içerebilir, ancak her rol bir örnekle sınırlıdır.
- 1000'in altındaki bağlantı noktası numaralarına erişesiniz. Normalde 1000'in altındaki bir bağlantı noktasını kullanan bir kimlik doğrulama sağlayıcısı kullanıyorsanız, bu değeri 1000'den büyük bir bağlantı noktası numarasıyla değiştirmeniz gerekebilir.
- Azure İşlem Emulator Express için Emulator geçerlidir. Örneğin, dağıtım başına 50'den fazla rol örneğiniz olabilir. Uygulama hakkında daha fazla bilgi Azure İşlem Emulator bilgi için bkz. İşlem [Emulator.](vs-azure-tools-performance-profiling-cloud-services.md)

## <a name="next-steps"></a>Sonraki adımlar
[Azure bulut hizmetlerde hata ayıklama](vs-azure-tools-debugging-cloud-services-overview.md)
