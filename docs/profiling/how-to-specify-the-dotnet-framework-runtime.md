---
title: .NET Framework Runtime | Microsoft Docs
description: Uygulamaların çalışma zamanlarının farklı sürümleri kullanılarak .NET Framework nasıl oluşturabilirsiniz?
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 96d2640410e2565452053f2ceb899a0c29d61c9d584aae72ba4385c7e0ad2000
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121426774"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Nasıl yapılır: .NET Framework çalışma zamanını belirtin

.NET Framework 4 sürümüyle, uygulamalar çalışma zamanlarının farklı sürümleri kullanılarak .NET Framework modüllerden biri olabilir. Varsayılan olarak, Visual Studio Profil Oluşturma Araçları tarafından yüklenen ilk çalışma zamanının profilini oluşturun. Profil oluşturma için çalışma zamanı belirtebilirsiniz. Bir uygulamayı profil işleyiciyle başlatacak ve profilleyiciyi zaten çalışan bir uygulamaya ekleyebilirsiniz.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Profil oluşturma .NET Framework bir uygulamayı başlatacak çalışma zamanı belirtmek için

1. Bu **Performans Gezgini,** performans oturumuna sağ tıklayın, **Özellikler'e ve** ardından Gelişmiş'e **tıklayın.**

     Hedef **CLR Sürümü** liste kutusu **Otomatik'i** ve bilgisayarda yüklü .NET Framework çalışma zamanının sürümlerini görüntüler.

2. Aşağıdaki adımlardan birini uygulayın:

    - Profili oluşturmak istediğiniz CLR sürümüne tıklayın.

    - Uygulama **tarafından** yüklenen ilk sürümün profilini oluşturmak için Otomatik'e tıklayın.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Profil oluşturma .NET Framework profil oluşturma çalışma zamanı belirtmek için

1. Çözümle **menüsünde ProfilLeyici'nin** üzerine gelin **ve** **Ekle/Ayır'a tıklayın.**

2. **profiler'ı İşleme Ekle** iletişim kutusunda, profil oluşturmak istediğiniz işleme tıklayın.

     Hedef **CLR Sürüm** listesi kutusunda **Otomatik** ve bilgisayarda yüklü .NET Framework çalışma zamanı sürümleri.

3. Aşağıdaki adımlardan birini uygulayın:

    - Profili oluşturmak istediğiniz CLR sürümüne tıklayın.

    - Profil **oluşturma,** uygulamaya ekli olduğunda yüklenen sürümün profilini oluşturmak için Otomatik'e tıklayın.
