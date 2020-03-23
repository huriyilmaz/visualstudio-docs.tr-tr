---
title: 'Nasıl yapılsın: .NET Framework Runtime | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 4ab53a6cf265b36ee423a2df176014187860f635
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778680"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Nasıl yapılır: .NET Framework çalışma zamanını belirtin

.NET Framework 4 sürümüyle, uygulamalar .NET Framework çalışma zamanının farklı sürümleri kullanılarak oluşturulmuş modüllerden oluşabilir. Varsayılan olarak, Visual Studio Profil Oluşturma Araçları, uygulama tarafından yüklenen ilk çalışma süresini profiller. Profil oluşturucuyla bir uygulamayı başlattığınızda ve profil oluşturucuyu zaten çalışan bir uygulamaya taktığınız zaman profil için çalışma süresini belirtebilirsiniz.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Profil oluşturucuile bir uygulama başlatırken .NET Framework'ün profil için çalışma süresini belirtmek için

1. **Performans Gezgini'nde,** performans oturumuna sağ tıklayın, **Özellikler'i**tıklatın ve sonra **Gelişmiş'i**tıklatın.

     **Hedef CLR Sürüm** liste kutusu **Otomatik** ve bilgisayarda yüklü .NET Framework çalışma zamanı sürümlerini görüntüler.

2. Aşağıdaki adımlardan birini uygulayın:

    - Profilini çıkarmak istediğiniz CLR sürümünü tıklatın.

    - Uygulama tarafından yüklenen ilk sürümün profilini çıkarmak için **Otomatik'i** tıklatın.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Bir uygulamaya profil oluşturucuyu takarken .NET Framework çalışma süresini profile belirtmek için

1. **Analiz** menüsünde **Profiler'ı**işaret edin, ardından **Ekle/Ayır'ı**tıklatın.

2. Profil **oluştur'u İşleme** iletişim kutusuna ekle iletişim kutusunda, profilini çıkarmak istediğiniz işlemi tıklatın.

     **Hedef CLR Sürüm** liste kutusu otomatik ve bilgisayarda yüklü olan .NET Framework çalışma zamanı sürümleri. **Automatic**

3. Aşağıdaki adımlardan birini uygulayın:

    - Profilini çıkarmak istediğiniz CLR sürümünü tıklatın.

    - Profil oluşturucu uygulamaya bağlandığında yüklenen sürümü profillemek için **Otomatik'i** tıklatın.
