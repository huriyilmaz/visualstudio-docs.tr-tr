---
title: Azure Bulut Hizmetleri hizmet hizmetlerde hata ayıklama | Microsoft Docs
description: Azure bulut hizmetlerde hata ayıklama
author: mikejo5000
manager: jmartens
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/18/2017
ms.author: mikejo
ms.technology: vs-ide-debug
ms.openlocfilehash: 12b327c65b83acde09eeac748d614ca560f3e012
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633142"
---
# <a name="learn-the-various-ways-to-debug-an-azure-cloud-service"></a>Azure bulut hizmetinde hata ayıklamanın çeşitli yöntemlerini öğrenme
Bu makalede, Azure bulut hizmetlerinde hata ayıklamak için çeşitli yöntemlere bağlantılar yer alır.

## <a name="debugging-an-azure-cloud-service-in-visual-studio"></a>Azure bulut hizmetinde hata ayıklama Visual Studio
Yerel makinede bulut hizmetinizin hata ayıklaması için Azure İşlem Emulator kullanarak zamandan ve paradan tasarruf edin. Bir hizmeti dağıtmadan önce yerel olarak hata ayıklarken, işlem süresi için ödeme yapmadan güvenilirliği ve performansı geliştirebilirsiniz. Ancak bazı hatalar yalnızca Azure'da bir bulut hizmeti çalıştırarak ortaya çıkabilir. Yalnızca Azure'da bir bulut hizmetini çalıştırmanız sırasında oluşan hatalar, hizmetinizi yayımlarken uzaktan hata ayıklama etkinleştirerek ve ardından hata ayıklayıcıyı bir rol örneğine ekerek hata ayıklaması olabilir. Daha fazla bilgi için [bkz. Yerel bilgisayarınızda bulut hizmetinizin hata ayıklaması.](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-your-cloud-service-on-your-local-computer)

## <a name="using-intellitrace"></a>IntelliTrace’i kullanma
.NET Framework 4.5'i hedef alan roller yazmak için Visual Studio Enterprise kullanıyorsanız, Azure bulut hizmetini dağıtarak IntelliTrace'i Visual Studio. IntelliTrace, uygulama hata ayıklamak için Visual Studio Azure'da çalışıyor gibi kullanabileceğiniz bir günlük sağlar. Daha fazla bilgi için bkz. [IntelliTrace ve Visual Studio ile](vs-azure-tools-intellitrace-debug-published-cloud-services.md)yayımlanmış bir bulut hizmetinde hata ayıklama.

## <a name="remote-debugging"></a>Uzaktan hata ayıklama
Bulut hizmetini bulut hizmetinden dağıtırken bulut hizmetleriniz üzerinde uzaktan hata ayıklamayı Visual Studio. Bir dağıtım için uzaktan hata ayıklamayı etkinleştirmeyi seçerseniz, her rol örneğini çalıştıran sanal makinelere uzaktan hata ayıklama hizmetleri yüklenir. Bu hizmetler ( `msvsmon.exe` gibi) performansı etkilemez veya ek maliyetlere neden olmaz. Daha fazla bilgi için [bkz. Azure'da bir bulut hizmetinin hata ayıklaması.](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-a-cloud-service-in-azure)

## <a name="next-steps"></a>Sonraki adımlar
- [Visual Studio'da Bir Azure](./vs-azure-tools-debug-cloud-services-virtual-machines.md) bulut hizmetinde veya VM'de hata ayıklama - Azure bulut hizmetlerde hata ayıklama hakkında ayrıntılı bilgi edinin.
