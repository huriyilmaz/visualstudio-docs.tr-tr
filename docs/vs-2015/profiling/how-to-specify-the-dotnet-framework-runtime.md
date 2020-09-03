---
title: 'Nasıl yapılır: .NET Framework çalışma zamanını belirtme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f631e8639c1004fa2cb005da3b6c8bcb27f1a9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203404"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Nasıl yapılır: .NET Framework çalışma zamanını belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sürümü ile [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] , uygulamalar çalışma zamanının farklı sürümleri kullanılarak oluşturulmuş modüllerden oluşabilir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Varsayılan olarak, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uygulama tarafından yüklenen ilk çalışma zamanının profilini profil oluşturma araçları. Profil Oluşturucu ile bir uygulama başlattığınızda ve zaten çalışan bir uygulamaya profil oluşturucu iliştirçalıştığınızda, profil oluşturma zamanını belirtebilirsiniz.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Profil Oluşturucu ile bir uygulama başlatılırken .NET Framework çalışma zamanını belirlemek için  
  
1. **Performans Gezgini**, performans oturumuna sağ tıklayın, **Özellikler**' e ve ardından **Gelişmiş**' e tıklayın.  
  
     **Hedef CLR sürümü** liste kutusu, **Automatic** [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] bilgisayarda yüklü olan çalışma zamanının otomatik ve sürümlerini görüntüler.  
  
2. Aşağıdaki adımlardan birini uygulayın:  
  
    - Profil eklemek istediğiniz CLR sürümüne tıklayın.  
  
    - Uygulama tarafından yüklenen ilk sürümü profil için **Otomatik** ' e tıklayın.  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Profil oluşturucuyu bir uygulamaya eklerken kullanılacak .NET Framework çalışma zamanını belirtmek için  
  
1. Çözümle menüsünde Profil Oluşturucu ' nın üzerine gelin ve Ekle/ayır ' a tıklayın.  
  
2. Işleme profil oluşturucu Ekle iletişim kutusunda, profil eklemek istediğiniz işleme tıklayın.  
  
     **Hedef CLR sürümü** liste kutusu **Otomatik** ve [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] bilgisayarda yüklü olan çalışma zamanının sürümleri.  
  
3. Aşağıdaki adımlardan birini uygulayın:  
  
    - Profil eklemek istediğiniz CLR sürümüne tıklayın.  
  
    - Profil Oluşturucu uygulamaya iliştirayarlandığında yüklenen sürümü profil için **Otomatik** ' e tıklayın.
