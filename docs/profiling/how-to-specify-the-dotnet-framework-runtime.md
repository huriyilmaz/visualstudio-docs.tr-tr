---
title: .NET Framework çalışma zamanını belirtin | Microsoft Docs
description: uygulamaların .NET Framework çalışma zamanının farklı sürümleri kullanılarak oluşturulmuş modüllerden nasıl oluşabileceğinden öğrenin.
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
ms.openlocfilehash: 3c4a102e7d18f7a580cb012f46e9a5c737106d2a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150046"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Nasıl yapılır: .NET Framework çalışma zamanını belirtin

.NET Framework 4 sürümünde, uygulamalar .NET Framework çalışma zamanının farklı sürümleri kullanılarak oluşturulmuş modüllerden oluşabilir. varsayılan olarak, Visual Studio Profil Oluşturma Araçları profili uygulama tarafından yüklenen ilk çalışma zamanına göre yapılır. Profil Oluşturucu ile bir uygulama başlattığınızda ve zaten çalışan bir uygulamaya profil oluşturucu iliştirçalıştığınızda, profil oluşturma zamanını belirtebilirsiniz.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>profil oluşturucu ile bir uygulama başlatılırken .NET Framework çalışma zamanını belirlemek için

1. **Performans Gezgini**, performans oturumuna sağ tıklayın, **Özellikler**' e ve ardından **Gelişmiş**' e tıklayın.

     **hedef CLR sürümü** liste kutusu, bilgisayarda yüklü olan .NET Framework çalışma zamanının **otomatik** ve sürümlerini görüntüler.

2. Aşağıdaki adımlardan birini uygulayın:

    - Profil eklemek istediğiniz CLR sürümüne tıklayın.

    - Uygulama tarafından yüklenen ilk sürümü profil için **Otomatik** ' e tıklayın.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>profil oluşturucuyu bir uygulamaya eklerken kullanılacak .NET Framework çalışma zamanını belirtmek için

1. **Çözümle** menüsünde **Profil Oluşturucu**' nın üzerine gelin ve **Ekle/ayır**' a tıklayın.

2. **Işleme profil oluşturucu Ekle** iletişim kutusunda, profil eklemek istediğiniz işleme tıklayın.

     **hedef CLR sürümü** liste kutusu **otomatik** ve bilgisayarda yüklü olan .NET Framework çalışma zamanının sürümleri.

3. Aşağıdaki adımlardan birini uygulayın:

    - Profil eklemek istediğiniz CLR sürümüne tıklayın.

    - Profil Oluşturucu uygulamaya iliştirayarlandığında yüklenen sürümü profil için **Otomatik** ' e tıklayın.
