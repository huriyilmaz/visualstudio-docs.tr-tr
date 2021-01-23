---
title: .NET Framework çalışma zamanını belirtin | Microsoft Docs
description: Uygulamaların .NET Framework çalışma zamanının farklı sürümleri kullanılarak oluşturulmuş modüllerden nasıl oluşabileceğinden öğrenin.
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: e825b456a4524653df4e8c40793f16f3d8887665
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721833"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Nasıl yapılır: .NET Framework çalışma zamanını belirtin

.NET Framework 4 sürümünde, uygulamalar .NET Framework çalışma zamanının farklı sürümleri kullanılarak oluşturulmuş modüllerden oluşabilir. Varsayılan olarak, Visual Studio Profil Oluşturma Araçları uygulama tarafından yüklenen ilk çalışma zamanını profili. Profil Oluşturucu ile bir uygulama başlattığınızda ve zaten çalışan bir uygulamaya profil oluşturucu iliştirçalıştığınızda, profil oluşturma zamanını belirtebilirsiniz.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Profil Oluşturucu ile bir uygulama başlatılırken .NET Framework çalışma zamanını belirlemek için

1. **Performans Gezgini**, performans oturumuna sağ tıklayın, **Özellikler**' e ve ardından **Gelişmiş**' e tıklayın.

     **Hedef CLR sürümü** liste kutusu, bilgisayarda yüklü olan .NET Framework çalışma zamanının **Otomatik** ve sürümlerini görüntüler.

2. Aşağıdaki adımlardan birini uygulayın:

    - Profil eklemek istediğiniz CLR sürümüne tıklayın.

    - Uygulama tarafından yüklenen ilk sürümü profil için **Otomatik** ' e tıklayın.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Profil oluşturucuyu bir uygulamaya eklerken kullanılacak .NET Framework çalışma zamanını belirtmek için

1. **Çözümle** menüsünde **Profil Oluşturucu**' nın üzerine gelin ve **Ekle/ayır**' a tıklayın.

2. **Işleme profil oluşturucu Ekle** iletişim kutusunda, profil eklemek istediğiniz işleme tıklayın.

     **Hedef CLR sürümü** liste kutusu **Otomatik** ve bilgisayarda yüklü olan .NET Framework çalışma zamanının sürümleri.

3. Aşağıdaki adımlardan birini uygulayın:

    - Profil eklemek istediğiniz CLR sürümüne tıklayın.

    - Profil Oluşturucu uygulamaya iliştirayarlandığında yüklenen sürümü profil için **Otomatik** ' e tıklayın.
